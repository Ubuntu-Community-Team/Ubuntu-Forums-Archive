---
title: "Interupt terminal sesion"
date: 2010-11-23
forum: General Help
---

### Post by dumbledor on 2010-11-23
I have simple c program.

```

#include <stdio.h>
#include <time.h>

void main(){
	int x = 5;
	int i = 0;
	
	do{
	    x++;
	    printf("%d\n",x);
	    sleep(1);	
	}while (i == 0);
}

```

I am running this in terminal 1. I want to send command from terminal window 2 to change int i to a different value. Is that possible? I am not interested in killing program, i just want to change variable to end loop and start another process. Thanks for answers.

---

### Post by blazemore on 2010-11-24
The only way to do this AFAIK is to put something in the C program that waits for a specific character on the input (as a string). IDK how to do this in C, but it must be possible.

Once this is working on the TTY the program is running on, you can use the "write" command to send messages to a specific tty:
```
write username pts/**x**
```

Type your message and press Enter.

Use EOF or Ctrl-C to end.

You can determine which value of **x** to use with the "who" command.

---

