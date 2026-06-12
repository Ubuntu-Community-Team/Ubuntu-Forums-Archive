---
title: "where is the &quot;gnome-session&quot; folder located?"
date: 2010-10-28
forum: General Help
---

### Post by miesogeno on 2010-10-28
i need to check a file there, one that refers to the icon used for "restart" in the logout dialog box. the file i need is "gsm-logout-dialog.c".

i'm a bit tired of looking for it, both in my computer and on google.

thanks

---

### Post by Pollox on 2010-10-28
There are a few gnome-session folders. If you don't mind using terminal, may I suggest the "locate" command, i.e.
```
locate gsm-logout-dialog.c
```

By the way, I do not find that file on my computer, but I am assuming you have a reason to assume it exists on yours.

---

### Post by matt_symes on 2010-10-28
Hi 

I use locate as well. You might want to run

sudo updatedb

and enter you pasasword, to update locate's database.

BTW The file is also not on my machine.

Kind regards

---

### Post by miesogeno on 2010-10-28
thank you both!

but well, that didn't work (the tip worked but i didn't find the file). i probably do not have it in my computer either...

the thing is, i started by opening this thread [here]("http://ubuntuforums.org/showthread.php?t=1603220"), and nobody answered, so i refrased..

basically, i wanted to find the string responsible for the the "logout dialog" choosing the wrong icon (view-refresh...??) for the "reboot" option, and i found something on launchpad that pointed to that file.

i really dont know how to change that now.

any idea would be welcome.

---

### Post by Pollox on 2010-10-28
I don't have a specific answer to your original question, but I can tell you that gsm-logout-dialog.c is a file in the source code of gnome-session. You can view it here: [http://git.gnome.org/browse/gnome-session/tree/gnome-session/gsm-logout-dialog.c](http://git.gnome.org/browse/gnome-session/tree/gnome-session/gsm-logout-dialog.c).

---

### Post by miesogeno on 2010-10-28
yes, that's what i found when i went looking for the reboot icon.

but what do you mean by source code? does it mean that the file is not acessible in my computer? isn't that "source code" just the content of the file?
i thought that it would be installed somewhere and was just something you could tweak, carefully, of course, but easily.

thanks for your trouble.

---

### Post by matt_symes on 2010-10-28
Hi  

Source code is code that is written by some one who writes software. It is human readable. That then gets converted into something that the computer can understand by a process of compiling and linking. That file was a c source code file. You could update the source and rebuild, however if you cant write software..... It is not a configuration file

Kind regards

---

### Post by Pollox on 2010-10-28
The file is a .c file, which typically indicates that it is a file written in the C programming language. Looking at the file contents, you can confirm this.

Although some languages run programs directly from the source file (e.g. Python), C programs must be compiled. The .c file is run through a compiler (well, there's some other stuff that happens in this step too, and details about linking code from different files, but that's not important right here) and turned into machine code (0's and 1's that provide instructions for your processor to execute). It's the machine code that is installed on your computer.

If you want to make a change to gnome-session by editing that file, you would need to figure out how to compile and install gnome-session (there's probably directions included, usually something along the lines of ./configure, make, makeinstall). It might be better to look and see if what you want to accomplish can be done by editing some configuration file instead.

Edit: matt_symes types faster than me

---

### Post by miesogeno on 2010-10-28
thank you both, once again.

i'm obviously a long way from being able to compile system files without any risk, and this is my working computer, and i've formatted it too many times now, and wasted too much time on it. i've compiled some software before, 3th party, with instructions, of course. but i don't think it's worth the risk or the time waste for now.

[LEFT]it's a pitty, because that icon is definitely misused there, and it ruins my icon theme. from what i understand it has something to do with default icon theme availability, cross-distribution wise, but i think that argument is a bit out dated by now.

anyway, thanks a lot!
[/LEFT]

---

