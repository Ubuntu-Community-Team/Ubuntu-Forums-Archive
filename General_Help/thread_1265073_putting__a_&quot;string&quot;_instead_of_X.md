---
title: "putting  a &quot;string&quot; instead of X"
date: 2009-09-12
forum: General Help
---

### Post by dink123 on 2009-09-12
i want to put some string after the splash screen. so that after loading the kernal it will just show up the string and will hang up there without doing anything.

- in order to do this i may have to write a simple C program which prints a string and will have to configure its path in a way that the kernal will execute it instead of INIT

---

### Post by harrismh777 on 2009-09-13
> **dink123 said:**
> i want to put some string after the splash screen. so that after loading the kernal it will just show up the string and will hang up there without doing anything.

- in order to do this i may have to write a simple C program which prints a string and will have to configure its path in a way that the kernal will execute it instead of INIT


Init is process 1 on your system. Init *is* the kernel. Init keeps everything going, restarts processes, etc....   no init,.. no system.

Go ahead, open a terminal and try this...

sudo kill -9 1



:-({|=

---

### Post by akakingess on 2009-09-13
could you try it with a bash script that you add to init.d? Just a shot in the dark as I know you guys are way above my head, but 3 heads are better than 2 (in most cases).  Just a thought as to another approach to what you are trying to accomplish.

---

### Post by dink123 on 2009-09-13
> **harrismh777 said:**
> Init is process 1 on your system. Init *is* the kernel. Init keeps everything going, restarts processes, etc....   no init,.. no system.

Go ahead, open a terminal and try this...

sudo kill -9 1



i think GRUB will load the kernal and it will load the INIT(pid=1) and INIT will load all the other processes. anyway do you have any idea of doing that?

---

### Post by stderr on 2009-09-13
> **akakingess said:**
> could you try it with a bash script that you add to init.d? Just a shot in the dark as I know you guys are way above my head, but 3 heads are better than 2 (in most cases).  Just a thought as to another approach to what you are trying to accomplish.
May be worth trying something along these lines first before trying other solutions. Knock up a quick bash script, 

#!/bin/bash 
echo "If I see this it may be a possbility" && sleep 100

name it appropriately to where you want it in the boot order (probably last, so start the name with 99), chmod +x it, update-rc.d it, and see what happens on boot. If it pauses for a while, Ctrl+Alt+F1 and see if you've got some output.

---

### Post by dink123 on 2009-09-13
where to add those  changes? is it to the etc/passwd file

---

### Post by stderr on 2009-09-13
Uhm, don't touch that, whatever you do!!

No, you need to do some reading on update-rc.d. I doubt whether it will (easily) be able to achieve _exactly_ what you're looking for for a number of reasons, but then again I'm not sure exactly what you're trying to achieve. 

What we were proposing is method 3 on this howto: [https://help.ubuntu.com/community/UbuntuBootupHowto]("https://help.ubuntu.com/community/UbuntuBootupHowto"). Also, you should understand what the snippet of bash code I gave you does before trying to use it. 

```
man sleep
```

etc.

The process I outlined involved creating a blank file with a bash script in something like the example I gave & naming it appropriately, making it executable, giving it root ownership, placing it in the correct directory, executing a command to add links to it in the correct /etc/rc.d/ folders (i.e. making it run at startup) and in the correct order. This may not be enough though, as I can't think if it will **cause the boot process to pause** or not, and I can't think of a way to make the **text display by default** without the user having to switch to a text console manually. Lots of ifs and buts.

You can have the script execute your own crafted application, but I have no idea what the user will see, etc etc. Be prepared to do quite a bit of testing, coding, rebooting (and potentially booting from a live CD to undo the changes you made from a terminal so you have a bootable system, should you screw up the boot process!).

---

### Post by akakingess on 2009-09-13
Just keep in mind, I was not trying to cause you too much work, just thought that the idea of a script within init.d would be the easier route;)

---

### Post by dink123 on 2009-09-13
> **stderr said:**
> Uhm, don't touch that, whatever you do!!
......


what happens if i change the field for shell in the /etc/passwd file? since that is the process that is started after a user invokes the login command.

---

### Post by stderr on 2009-09-13
It doesn't just start an instance of, in my case, /bin/bash and let me get on with things... it starts GDM if requested and prompts for login info, or it starts a shell and prompts for login info. You say you want text to be displayed, but without a login prompt. Even if that method would work, you'd need to login to that account first, and without a valid shell I don't know if that would even be possible.

---

### Post by dink123 on 2009-09-13
thank you.
things are much clearer now.
but what does this /bin/bash field is supposed to do then?.

---

### Post by savagenator on 2009-09-13
the part with init=/bin/bash simply tells the kernel to launch bash, the shell (terminal, whatever you want to call it) and not load anything else

---

### Post by dink123 on 2009-09-14
> **savagenator said:**
> the part with init=/bin/bash simply tells the kernel to launch bash, the shell (terminal, whatever you want to call it) and not load anything else

no i mean /bin/bash field(for a paticular user) in the /etc/passwd file.

---

