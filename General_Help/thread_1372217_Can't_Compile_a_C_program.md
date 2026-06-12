---
title: "Can't Compile a C program"
date: 2010-01-04
forum: General Help
---

### Post by Dark Sorrow on 2010-01-04
[SIZE=2]I can't compile a C program form terminal using gcc by Code Blocks 8.02 is able to do so. 
[/SIZE]```
[SIZE=2]#include<stdio.h>

int main(void)
{
     printf("Hello World\n");
     return 0;
}
[/SIZE]
```[SIZE=2]
To compile i type at the terminal
```

gcc HelloWorld.C 

```.C is the extension i gave while saving using text editor.
OR
```

gcc HelloWorld.C -o Hello

```Both the case give same error
> 
/tmp/cc0Wz6j5.o: (.eh_frame+0x11): undefined reference to `__gxx_personality_v0'
collect2: ld returned 1 exit status

I have installed build-essentials.
[/SIZE]

---

### Post by zine92 on 2010-01-04
where did you place your file. I tried to write my own and try compiling. I have no problem. Anyway this is what i did. 

```
patrick@patrick-laptop:~$ cd Desktop/
patrick@patrick-laptop:~/Desktop$ gcc hello\ world.c
patrick@patrick-laptop:~/Desktop$ '/home/patrick/Desktop/a.out' 
Hello,worldpatrick@patrick-laptop:~/Desktop$
``` 
Output from my terminal.

hope that helps.



```
#include <stdio.h>

int main(void)
{
	printf("Hello,world");
	return 0;
}
```

---

### Post by Dark Sorrow on 2010-01-04
> **zine92 said:**
> where did you place your file. I tried to write my own and try compiling. I have no problem. Anyway this is what i did. 

```
patrick@patrick-laptop:~$ cd Desktop/
patrick@patrick-laptop:~/Desktop$ gcc hello\ world.c
patrick@patrick-laptop:~/Desktop$ '/home/patrick/Desktop/a.out' 
Hello,worldpatrick@patrick-laptop:~/Desktop$
```Output from my terminal.

hope that helps.



```
#include <stdio.h>

int main(void)
{
    printf("Hello,world");
    return 0;
}
```

The program is in my home folder.

---

### Post by john newbuntu on 2010-01-04
File extension uppercase C is C++.  Change it to helloworld.c and try unless you are using a C++ program.

---

### Post by Dark Sorrow on 2010-01-04
> **john newbuntu said:**
> File extension uppercase C is C++.  Change it to helloworld.c and try unless you are using a C++ program.

Thank you, it worked. Now how to run it.
```

gcc HelloWorld.c -o Hello

```
I get an an:
> 
DarkSorrow@DarkSorrow-laptop:~$ Hello.out
bash: Hello.out: command not found
DarkSorrow@DarkSorrow-laptop:~$ Hello
bash: Hello: command not found
DarkSorrow@DarkSorrow-laptop:~$ Hello.exe
bash: Hello.exe: command not found


---

### Post by Seano911 on 2010-01-04
Try ./hello.out

---

### Post by Dark Sorrow on 2010-01-04
> **Seano911 said:**
> Try ./hello.out
DarkSorrow@DarkSorrow-laptop:~$ ./Hello.out
bash: ./Hello.out: No such file or directory

---

### Post by nothingspecial on 2010-01-04
```
chmod a+x Hello
```

```
./Hello
```

---

### Post by Dark Sorrow on 2010-01-04
> **nothingspecial said:**
> ```
chmod a+x Hello
``````
./Hello
```
Thank You, it worked.
Can you please explain what is chmod command what does it do.

---

### Post by nothingspecial on 2010-01-04
chmod a+x will make the program executable by anyone. It may not actually be necessary if everything is in your home directory.

The problem you were having was the syntax of the compiled binary

> DarkSorrow@DarkSorrow-laptop:~$ Hello.out
bash: Hello.out: command not found
DarkSorrow@DarkSorrow-laptop:~$ Hello
bash: Hello: command not found
DarkSorrow@DarkSorrow-laptop:~$ Hello.exe
bash: Hello.exe: command not found 

Each of these were wrong because you didn`t use ./

Then you tried ./hello.out

You got the ./ in there but the name of the binary wrong. You told g++ to output the file as Hello, with no file extension. It did exactly what you told it to do. Upper case H, no file extension. That`s what you had to run.

You could have called it bananas.jpg and it would still have run.
```

g++ hello.C -o bananas.jpg
./bananas.jpg
```

You`ve just got to get the syntax right.

---

### Post by pushkar_k on 2010-01-04
you typed at shell following to compile your program .
              gcc HelloWorld.c -o Hello

So here -o switch tells the name of your output file. As you gave  "-o Hello " , the name of your output file would be just "Hello" not "Hello.out". You can verify this using dir command.

So to run the program after compiling type 

          ./Hello
at the shell.

---

### Post by Dark Sorrow on 2010-01-04
> **pushkar_k said:**
> you typed at shell following to compile your program .
              gcc HelloWorld.c -o Hello

So here -o switch tells the name of your output file. As you gave  "-o Hello " , the name of your output file would be just "Hello" not "Hello.out". You can verify this using dir command.

So to run the program after compiling type 

          ./Hello
at the shell.

Thank You. You were write.

---

