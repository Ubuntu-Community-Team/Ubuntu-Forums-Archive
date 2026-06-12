---
title: "PC speaker programing"
date: 2012-01-19
forum: General Help
---

### Post by conradin on 2012-01-19
Hi all,
I want to do some low level programming in c for the PC speaker. All the tutorials I can find are more complex and try to point me to the sound card and more modern  methods. i want to use inb and outb to create port sounds.
Anyone know some good tutorials for this?

---

### Post by conradin on 2012-01-21
So Im on my merry way. With this C source code, compiled, and chomded to the permissions 4411
```
#include <stdio.h>
#include <sys/io.h>
#include <unistd.h>
#include <sys/types.h>
int main(int argc, char * argv[], char * env[])
{
	if(argc<2){printf("Usage is %s program [arguments]\n",argv[0]);return -1;}
	if(iopl(3)!=0) {perror("iopl");return -2;}
	setuid(getuid());
	if(argc >1)
	{
		execve(argv[1],&argv[1],env);
	}
}

```

Compiled as ioshell, all the programs I write now can be run in this shell, rather than having to set permissions each time.

```

/*Code from Bruce Seggi*/
/* To compile gcc -c sound.c  */
/* this will make sound.o    */

#include "sound.h"
#include <sys/io.h>
 
int read_timer(unsigned int channel)
{
if (channel >2) return(0xffff);
    outb(channel<<6,0x43); //latch
                           //bit shifting has to do with the sound chip.
    return inb(0x40+channel)+(inb(0x40+channel)<<8);
}
 
void sound(long freq)
{
 freq=DIVISOR(freq);
 
//assumes that the channel has been initialized with a 0xb6

 outb(0xb6,0x43);
 outb( (freq&0xff),0x42);
 outb( ((freq>>8)&0xff),0x42);
}
    
 
void soundoff(void)
{
//Turn Sound port off
 outb(inb(0x61) &~3,0x61);
}
 
void soundon(void)
{
//Turn Sound port on
 outb((inb(0x61)| 3), 0x61);
}

int main (){

soundon();
sound(5555);
sleep(3);
soundoff();
return 0;
};


```

From there I can tweak it, all necessary functions are defined to make obnoxious noises via the PC speaker!
I hope this helps others in the future.

---

