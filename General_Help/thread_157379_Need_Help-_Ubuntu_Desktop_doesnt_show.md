---
title: "Need Help- Ubuntu Desktop doesnt show"
date: 2006-04-09
forum: General Help
---

### Post by thelagoons on 2006-04-09
I have successfully installed Ubuntu linux for human beings into my pentium II, but couldnt get the Ubuntu desktop running. After booting up, it brings me to the command terminal. How do I switch to GUI?

---

### Post by aysiu on 2006-04-09
Did you do a server install? Try any one of these...

1. Control-Alt-F7
2. ```
startx
```
3. ```
sudo apt-get update
sudo apt-get install ubuntu-desktop
sudo /etc/init.d/gdm restart
```

---

### Post by thelagoons on 2006-04-09
thanks for the prompt reply, i have tried startx and xstart but it didnt work. I will try the other two options:D

---

### Post by Sef on 2006-04-09
How much memory (ram) do you have?

---

### Post by nanotube on 2006-04-09
here is what you do.
at the grub boot prompt, choose "recovery mode"
that will shoot you straight to a root shell.
in there, issue the command
```
nano /etc/X11/xorg.conf
```
this will bring up the nano text editor. scroll around in that file until you find the line that looks like 
```
Device "ati"
```
(it could have something else besides "ati", like "nv"). and edit it so that it looks like
```
Device "vesa"
```
save the file (by hitting <ctrl><x>, and pressing enter)
then reboot by command
```
shutdown -r now
```
and try booting as usual. chances are, your X will come up.

---

### Post by thelagoons on 2006-04-09
after I type the code sudo /etc/init.d/gdm restart, the following error message showed up:

IO: fatal error 104(connection reset by peer on X server "0.0" after 0 request(0 known process) with 0 events in remaining. 


     I dont understand any of these things, please help what to do next, thanks

---

### Post by thelagoons on 2006-04-09
I got 256mb of RAM

I tried what nanotube suggested and it did not bring up the nano text editor, there was nothing to edit, it only showed some menu like control x, control R, control C and etc.

---

### Post by nanotube on 2006-04-09
are you sure you typed the full path of xorg.conf, exactly?
note that X11 has a capital X. 
if you installed a regular, non-server install, there Must be an xorg.conf file, and it will contain some stuff. so the fact that nano brings up nothing leads me to suspect that you didnt enter the path correctly.
try 
```
ls -al /etc/X11
```
and see if xorg.conf is listed in that directory, just to check. :)

---

### Post by thelagoons on 2006-04-09
I am sure I type exactly what you told me in your code. But one thing I haven't told you is that I did a server install.

---

### Post by Sutekh on 2006-04-09
Then you need to follow option 3 in aysiu's post

A server installation does not install the desktop environment

---

### Post by thelagoons on 2006-04-09
I already did what aysiu's option 3 and there was a fatal server error: no screen found. 
It says please consult the The X.Org Foundation support at htt[://wiki.Org for help. Please also check the log file at "/var/log/Xorg.O.log" for additional information. 
XIO: fatal IO error 104(connection reset by peer) on X server "0.0" after 0 request(0 known processed with 0 events remaining.


What does all this mean?

---

### Post by aysiu on 2006-04-09
I Googled around for that error. Found the error.

But solutions? No joy. I don't know what that means.

One thread in a Mandriva forum seemed to suggest it might be a hardware failure, but it wasn't confirmed by the original post-er.

---

### Post by Sutekh on 2006-04-10
I couldn't find anything either.  I could only suggest the Xorg Wiki

[X.Org Wiki - FAQ](http://xorg.freedesktop.org/wiki/FAQ)

[X.Org Wiki - FAQ Error Message](http://xorg.freedesktop.org/wiki/FAQErrorMessages)

I'm sorry to say that at one point I was troubled by this kind of error.  I wish I could remember what resolved it.


A quick scan of the wiki makes me think you could try the reconfiguring advice given by **nanotube**.

You could also effect this change by reconfiguring the X server using its configuration text/GUI interface
```
sudo dpkg-reconfigure xserver-xorg
```
instead of hacking the xorg.conf.   Again set the video driver to be **vesa**

---

