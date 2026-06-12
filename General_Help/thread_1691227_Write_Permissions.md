---
title: "Write Permissions"
date: 2011-02-19
forum: General Help
---

### Post by Briasaurus Rex on 2011-02-19
Greetings, people:

I've got what I feel is probably a fairly basic question. I'm trying to install a program from a bin file, but I'm getting a message saying I don't have write permissions to the directory that it wants to install to.

The directory in question is a new subdirectory of /opt

I was under the impression that sudo users have write permissions everywhere, but clearly that is not the case. How do I give myself write permissions for this directory? The owner is root, so I'm guessing I need to switch to that user? Or give my main user account root access?

I suppose I could just install it somewhere else, but this seemed like a good "better get to know your operating system" situation.

---

### Post by Bigtime_Scrub on 2011-02-19
If you know where this file is stored, you can navigate to it as a root user. If the owner of the program is root and you have sudo privileges Press Alt+F2. 

Type this in the box
```
 gksudo nautilus 
```and enter your password. 

This will let you navigate around directories as root and the permissions problem will be gone.

---

### Post by Briasaurus Rex on 2011-02-19
I still have to run the .bin file in the Terminal, no? If I just open the Terminal regular-style it starts me with the logged-in user, not root. Is there a way to launch Terminal as root?

---

### Post by ajgreeny on 2011-02-19
You should be able to install it by opening a root terminal with ```
sudo -i
```and then run the .bin file from that.  First **cd** to the folder where the bin file is, then make sure it is executable with ```
chmod a+x filename.bin
```then run the file with ```
./filename.bin
```

---

### Post by Briasaurus Rex on 2011-02-19
Welp, I successfully installed the program. Sort of.

Turns out it doesn't quite work on Ubuntu and is, in fact, meant for Red Hat. So I can't seem to actually LAUNCH the program. oopslolz.

Thanks for the help, anyway!

---

