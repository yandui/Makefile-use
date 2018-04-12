# Makefile-use

#Makefile较为通用的写法

```

    PROG = test
    SRC  = $(wildcard *.c)
    OBJ  = $(patsubst %.c ,%.o,${SRC})
    INCLUDE = hello.h
    DEFS= -DDEBUG
    CFLAGS  = -g  -c
    CC		= gcc
    
    all: ${PROG}
    
    ${PROG}:${OBJ} ${INCLUDE}
    	${CC} $^ -o $@
    	
    .PHONY:
    clean:
    	rm -rf *.o ${PROG}

'''


---------------
$(wildcard *.c)来获取工作目录下的所有的.c文件列表<br/>
$(patsubst %.c,%.o,$(wildcard *.c))，首先使用“wildcard”函数获取工作目录下的.c文件列表；之后将列表中所有文件名的后缀.c替换为.o。这样我们就可以得到在当前目录可生成的.o文件列表

--------------
