
UNIX下，共享库以so为后缀(shared object)。共享库与Windows下的DLL类似，是在程序运行时动态连接。多个进程可以连接同一个共享库。

**制作.so文件**
	
	//-c表示只编译(compile)，而不连接。-o选项用于说明输出(output)文件名。gcc将生成一个目标(object)文件mystack.o
	//注意-fPIC选项。PIC指Position Independent Code。共享库要求有此选项，以便实现动态连接(dynamic linking)。*/
	$gcc -c -fPIC mystack.c -o mystack.o 
	
	//生成共享库:
	//库文件以lib开始。共享库文件以.so为后缀。-shared表示生成一个共享库。
	$gcc -shared mystack.o -o libmystack.so 
	
这样，共享库就完成了。.so文件和.h文件都位于当前工作路径(.)。

**使用共享库**

	$gcc  test.c -lmystack  -o test -L.
	$./test