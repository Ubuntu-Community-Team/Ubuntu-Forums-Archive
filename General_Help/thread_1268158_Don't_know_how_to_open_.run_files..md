---
title: "Don't know how to open .run files."
date: 2009-09-16
forum: General Help
---

### Post by Leo90 on 2009-09-16
okey I've looked threw some threads here and they are not helping me. I go to my terminal and put this inn

leo90@leo90-desktop:~$ chmod 777 NVIDIA-Linux-x86-190.32.pkg1.run
chmod: cannot access `NVIDIA-Linux-x86-190.32.pkg1.run': No such file or directory

I saw on the internet that 777 was a default executable permission.

leo90@leo90-desktop:~$ chmod u+x NVIDIA-Linux-x86-190.32.pkg1.run
chmod: cannot access `NVIDIA-Linux-x86-190.32.pkg1.run': No such file or directory

my .run file is on desktop so this should work right and you can see I'm trying to install a nvidia driver and there is no info on there site to install this.

can some one please help me

btw I'm a newb so don't be bad to me, don't know were this is supposed to go and don't know what a poll is :$

---

### Post by TeoBigusGeekus on 2009-09-16
Type 
```
cd ~/Desktop
``` 
and then you are on your Desktop.
By the way, why don't you install drivers for your g/card through 
System->Administration->Hardware Drivers?

---

### Post by Leo90 on 2009-09-16
cause I have GT9600 and I GNOME won't start when I boot so I get GUI, and I can't handle GUI. but how do you do this sign on your keyboard ? = 
~

leo90@leo90-desktop:~$ cd ~/Desktop
leo90@leo90-desktop:~/Desktop$ 
leo90@leo90-desktop:~/Desktop$ chmod 777 nvidia-linux-x86-190.32-pkg1.run
chmod: cannot access `nvidia-linux-x86-190.32-pkg1.run': No such file or directory
leo90@leo90-desktop:~/Desktop$ chmod 777 NVIDIA-Linux-x86-190.32.pkg1.run
chmod: cannot access `NVIDIA-Linux-x86-190.32.pkg1.run': No such file or directory
leo90@leo90-desktop:~/Desktop$ sh NVIDIA-Linux-x86-190.32.pkg1.run
sh: Can't open NVIDIA-Linux-x86-190.32.pkg1.run
leo90@leo90-desktop:~/Desktop$ chmod u+x NVIDIA-Linux-x86-190.32.pkg1.run
chmod: cannot access `NVIDIA-Linux-x86-190.32.pkg1.run': No such file or directory

nothing of this worked, but I got onto my desktop.

---

### Post by TeoBigusGeekus on 2009-09-16
Right above the left TAB button.
EDIT
While on your Desktop, type 
```
ls
```
to see the existing files on it.

---

### Post by Leo90 on 2009-09-16
ok I did ls and they said this file NVIDIA-Linux-x86-190.32-pkg1.run was on it so i copy pasted it and then did 

leo90@leo90-desktop:~/Desktop$ sh NVIDIA-Linux-x86-190.32-pkg1.run
Verifying archive integrity... OK
Uncompressing NVIDIA Accelerated Graphics Driver for Linux-x86 190.32...........................................................................................................................................................................................................................................................................................................
nvidia-installer: Error opening log file '/var/log/nvidia-installer.log' for writing (Permission denied); disabling logging.
Received signal SIGINT; aborting.
Signal caught, cleaning up

So this file needs to be rooted, so what to do now ?

---

### Post by baseface on 2009-09-16
use sudo to run it.

---

### Post by Leo90 on 2009-09-16
So then we come to another thing what is and how do I use sudo ?

---

### Post by baseface on 2009-09-16
```
sudo sh whateveryouneedtorun
```

---

### Post by Leo90 on 2009-09-16
Now I get this :

ERROR: You appear to be running an X server; please exit X before installing. For further details, please see the section INSTALLING THE NVIDIA DRIVER in the README(Going to try to find this now) available on the Linux driver download page at [www.nvidia.com](www.nvidia.com)

---

### Post by marcopolo1981 on 2009-09-16
Leo90

Try this:

CTRL-ALT-F2

Enter username and password

Type "sudo su"

Enter Password

Type "killall gdm"

Type "sh NVIDIA-Linux-x86-190.32.pkg1.run"

Follow the instruction it gives you.

Once it has completed and returned to prompt, type "reboot -n"

When it reboots, there should be a NVIDIA logo on the screen before the desktop starts. This shows that the new drivers are installed correctly.

Mark

EDIT: This is assuming that you are using Gnome, if not, "killall gdm" will not work. I don't know how to kill other desktop environments, sorry.

Also, please save all open data before running these commands!

If it still fails to find the file, try copying it to your home directory and doing it again.

Also, SUDO is administrative priveledges. That means normal users can't screw up your system without jumping through hoops and the password. The password should be your username password if you were the first user registered/only user.

---

### Post by Leo90 on 2009-09-16
this ~ button ain't working for me don't know why :S ?! where is he supposed to be where this button is ° <--- at the left side up on tab, if it is him he aint working for me

and now I did this:

CTRL-ALT-F2

Enter username and password

Type "sudo su"

Enter Password

Type "killall gdm"

Type "sh NVIDIA-Linux-x86-190.32.pkg1.run"

and I get = bash: sd: command not found

---

### Post by oldos2er on 2009-09-16
Much easier to install nvidia drivers from a PPA, so you won't need to reinstall them after a kernel update: [http://webupd8.blogspot.com/2009/08/how-to-install-nvidia-190xx-drivers-in.html](http://webupd8.blogspot.com/2009/08/how-to-install-nvidia-190xx-drivers-in.html)

---

### Post by baseface on 2009-09-16
im guessing that you typed "sd" instead of "sh".
do it again.

---

### Post by Leo90 on 2009-09-16
Thank you baseface your method worked, I wrote ls then I wrote the file name and it worked. Didn't work if I freehand wrote it. but how do I now restart from this black screen (GUI I think)?

---

### Post by SuperSonic4 on 2009-09-16
You can either run (as root) ```
/etc/init.d/gdm start
``` or reboot the PC

---

### Post by Leo90 on 2009-09-16
I don't know how this /etc ( mainly this / <--) works cause I know how to go backwards inn dir (dc .. or dc - the seconed one i don't know completely). 

so how do I use this /etc/int.d/gdm start method ? It says when I but it into:

root@leo90-desktop:/home/leo90#  /etc/int.d/gdm start
bash:  /etc/int.d/gdm start: No such file or directory.

now that I rebooted (pushed the button on the computer cause I didn't get any awnsers) I can't get the displays up only the gui, the gnome won't go on now I need to reinstall everything or just open ubuntu 9.11 insted of 9.15 hope thats the case, then I can fix and overwrite..

---

### Post by Chronon on 2009-09-16
It seems you have some trouble with substituting characters.  You should try to directly copy and paste as much as possible as it will help you avoid this problem: Once again, you have misspelled the command that you want.  (You also managed to misspell the change directory command in your post -- it's "cd" not "dc".)

--
edit: How do you get a GUI up without a display?  I am having difficulty understanding what state your computer is in.

---

### Post by freackout on 2009-09-16
> **marcopolo1981 said:**
> Leo90

Try this:

CTRL-ALT-F2

Enter username and password

Type "sudo su"

Enter Password

Type "killall gdm"

Type "sh NVIDIA-Linux-x86-190.32.pkg1.run"

Follow the instruction it gives you.

Once it has completed and returned to prompt, type "reboot -n"

When it reboots, there should be a NVIDIA logo on the screen before the desktop starts. This shows that the new drivers are installed correctly.

Mark

EDIT: This is assuming that you are using Gnome, if not, "killall gdm" will not work. I don't know how to kill other desktop environments, sorry.

Also, please save all open data before running these commands!

If it still fails to find the file, try copying it to your home directory and doing it again.

Also, SUDO is administrative priveledges. That means normal users can't screw up your system without jumping through hoops and the password. The password should be your username password if you were the first user registered/only user.
ls (to see if upper/lowercase 
sh ./NV  or sh ./nv (then hit the tab button auto completes) or if you really stuggling with configuring your nvidia or ati card use envyng it will pick the recommended one for your system.

---

### Post by baseface on 2009-09-16
> **Leo90 said:**
> I don't know how this /etc ( mainly this / <--) works cause I know how to go backwards inn dir (dc .. or dc - the seconed one i don't know completely). 
 
so how do I use this /etc/int.d/gdm start method ? It says when I but it into:
 
root@leo90-desktop:/home/leo90# /etc/int.d/gdm start
bash: /etc/int.d/gdm start: No such file or directory.
 
now that I rebooted (pushed the button on the computer cause I didn't get any awnsers) I can't get the displays up only the gui, the gnome won't go on now I need to reinstall everything or just open ubuntu 9.11 insted of 9.15 hope thats the case, then I can fix and overwrite..
 
its /etc/in**i**t.d/gdm start
you forgot the 'i' in "init".

---

### Post by marcopolo1981 on 2009-09-17
An alternative way to switch back to GUI once the nVidia installer has completed;

Type "exit" to return back to normal user-mode

Type "startx"

This should put you back into the user-interface with the graphics card correctly configured.

Mark

---

