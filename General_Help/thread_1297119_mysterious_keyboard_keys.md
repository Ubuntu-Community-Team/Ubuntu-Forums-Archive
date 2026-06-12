---
title: "mysterious keyboard keys"
date: 2009-10-21
forum: General Help
---

### Post by mocatz187 on 2009-10-21
I typed a simple C program to try and get the hang of the linux prompt, so I typed the hello world program. after a successful compile and run, I went to add more code but my quotation marks have turned into tiny pairs of dots. this has affected everything that I type in. I am using US keyboard and it worked fine until I compiled and ran hello world. """""""""""""" these are from my windows computer.I'll try and login with the notebook with linux and display the wierd qoutes I'm getting there.
Any ideas? Thanks.

---

### Post by mocatz187 on 2009-10-21
This what I´ve got now ¨¨¨¨¨¨¨¨¨¨¨¨¨¨¨¨¨¨¨¨¨¨¨¨¨¨¨¨¨on Kubuntu. 
Anyone have any Ideas? Thanks.
when running a live cd of DSL Linux I do not have this problem.

---

### Post by mocatz187 on 2009-10-21
this is the code I used:
 
#include <stdio.h>
int main () {
 
printf ("hello world");
 
return 0;
}
 
Then in command line:
gcc -Wall -o hello hello.c
 
I was in the appropriate directory.
When I removed the offending quotes in the new code the compiler and shell were happy.
But now it does something weird, it requires you to hit the key twice to get one output and if you hit it once and then hit the space bar it will make a qoute that is code compatable. 
it's almost as if I somehow toggled some sort of letter highlighter or punctuator or ???

---

### Post by Niko Johnson on 2009-10-21
are you sure you have g++ installed... it might not have anything to do with it or it might have everything to do with it give this command a try ```
 sudo apt-get install g++ 
```

---

### Post by mocatz187 on 2009-10-21
OK, g++ is a C++ compiler right? doesn't it come with Kubuntu. why would I need that for what I'm doing. 
I know that their are lots of Linux distros that don't come with g++ but they DO have gcc.
 
I have heard of something called a dead key mode and it sounded like that in a way but.....
 
And yes, I did reboot because I have run several live CD distros that I ran without this problem.

---

### Post by jtniehof on 2009-10-21
I don't use KDE so I can't tell you where to go specifically, but those look like umlauts you're typing, not quotes. ¨ instead of ". Go to your keyboard configuration and look for a setting named something like "dead keys" and make sure it's turned *off*. (Might also be a different keyboard layout...make sure you have one chosen without dead keys.)

You might also have a stuck modifier key (alt, one of the logo keys) that's set up as "compose." If you don't need to type accented characters, make sure no compose key is set up in your keyboard setup.

---

