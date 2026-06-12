---
title: "need help compiling idea for 64bit"
date: 2011-08-01
forum: General Help
---

### Post by ottosykora on 2011-08-01
I have been using so far only 32bit ubuntu, but now for various reasons I have to change to 64bit

I need to compile a lib for gpg encryption for handling old keys, namely idea.

I have the idea.c file and had some instruction with which I was able to create the lib from it for the 32bit linux.

The intruction was:

gcc -Wall -02 -shared -fPIC -o idea idea.c


this seems not to work under 64bit and the old lib does not work under 64bit either obviously.

Can someone help me with the compilation of the source for the 64bit ubuntu pls


particularly the compiler tells me -02 option is unknown, does it matter? or what is -02 ?

---

### Post by blind2314 on 2011-08-01
> **ottosykora said:**
> I have been using so far only 32bit ubuntu, but now for various reasons I have to change to 64bit
 
I need to compile a lib for gpg encryption for handling old keys, namely idea.
 
I have the idea.c file and had some instruction with which I was able to create the lib from it for the 32bit linux.
 
The intruction was:
 
gcc -Wall -02 -shared -fPIC -o idea idea.c
 
 
this seems not to work under 64bit and the old lib does not work under 64bit either obviously.
 
Can someone help me with the compilation of the source for the 64bit ubuntu pls
 
 
particularly the compiler tells me -02 option is unknown, does it matter? or what is -02 ?
 
Formatting makes it hard to tell, but I suspect your problem is that you used a 'zero' instead of the letter 'o'. The flag should be ```
-O2
```

---

### Post by ottosykora on 2011-08-01
I have -02 , means dash zero two and the gcc complains

In my original instruction I have on a paper, it is dash zero two as I can see it, but ....well who knows exactly

what does the -02 or -O2 mean? I am not a programmer, so I do not know the options of compilers etc.

is it relevant at all?

Or can I do without ?

---

### Post by ottosykora on 2011-08-01
But bingo!

thanks for help, yes , with dash O two all works fine and the idea algo works in my gpg again.
Will try to note it for the future

---

