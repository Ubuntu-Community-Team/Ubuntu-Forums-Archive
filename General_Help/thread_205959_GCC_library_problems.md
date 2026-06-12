---
title: "GCC library problems"
date: 2006-06-29
forum: General Help
---

### Post by Lster on 2006-06-29
I can get gcc up, but can't compile:

#include <stdio.h>

int main(){
	printf("Hello world!");

	return 0;
}

I get the following error:

/tmp/ccZJFc0c.o:(.eh_frame+0x11): undefined reference to `__gxx_personality_v0'
collect2: ld returned 1 exit status

I don't know what to install or how... Plz help - I'm desperate!

---

### Post by Lster on 2006-06-29
Sry, computer added smiley! Here is the error:

/tmp/ccZJFc0c.o: (.eh_frame+0x11): undefined reference to `__gxx_personality_v0'
collect2: ld returned 1 exit status

---

### Post by lamego on 2006-06-29
First make sure you install all the required files:
```
sudo apt-get install build-essential
```
Could you please post the command you are using to compile the program ?

---

### Post by Lster on 2006-06-29
"sudo apt-get install build-essential" gives me the following:

	Password:
	Reading package lists... Done
	Building dependency tree... Done
	build-essential is already the newest version.
	0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

I am using the following command:

	gcc /home/lster/Desktop/p.c++

---

