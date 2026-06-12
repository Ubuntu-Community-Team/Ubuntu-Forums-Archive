---
title: "x server not loading"
date: 2006-05-02
forum: General Help
---

### Post by crash469_2u on 2006-05-02
I am new to ubuntu and know little about it I installed breazy on a new computer. It has an integrated ATI RADEON XSPRESS 200 chipset (for video) whean I turn on to boot it boots fine but whean I get past kernel load it comes up to a blue and grey screen simalar to the installation screen. It says x sever not able to load check wiki.x.org for more information. I go to that site and cant find anything that dose me any good I tried to reinstall linux but that didnt work either.  I have heard this is a rather common problem so I was hopeing I could get some advice.:confused:

---

### Post by nanotube on 2006-05-02
edit your /etc/X11/xorg.conf file, by entering command
```
sudo nano /etc/X11/xorg.conf
```
there, find the line that looks like
```
Device "ati"
```
and change it to 
```
Device "vesa"
```
save (hit control-X, press enter)
and reboot. see if that helps you.

---

### Post by crash469_2u on 2006-05-02
I tried that but it says that x11 is not a directory is that acessable by root acess only? if so can I set up a root account in recovery mode because this is a bare os I cant get the gnome interface working without xserver. I am at a total loss woth it at this point I hope you have some advice for me Thanx.

---

### Post by ecobuntu on 2006-05-02
did you use the 'sudo' command?

---

### Post by crash469_2u on 2006-05-02
yes I did and it is coming up command not found?

---

### Post by Jason_25 on 2006-05-02
Post the exact contents of the terminal showing the command you typed and the output.

---

### Post by crash469_2u on 2006-05-02
ok here it is 

/etc/x11/xorg.conf
 -bash /etc/x11/xorg.conf no sutch file or directory
 sudo /etc/x11/xorg.conf
password:*
 command not found

I also tried 
dpkg -reconfigure -phigh xserver-xorg
with it I get 
dpkg conflicting actions --control and --remove

---

### Post by nanotube on 2006-05-02
[QUOTE=crash469_2u]I tried that but it says that x11 is not a directory is that acessable by root acess only? if so can I set up a root account in recovery mode because this is a bare os I cant get the gnome interface working without xserver. I am at a total loss woth it at this point I hope you have some advice for me Thanx.[/QUOTE]
please, pay attention
it is not "x11" but "X11". the X is capitalized.
linux is case sensitive.
try it again, paste the command exactly as i posted it. then it will work. :)

---

### Post by crash469_2u on 2006-05-02
yes that was it I am under linux now. I keep forgetting that linux is case sensitive thank you for your help

---

### Post by nanotube on 2006-05-03
[QUOTE=crash469_2u]yes that was it I am under linux now. I keep forgetting that linux is case sensitive thank you for your help[/QUOTE]
hehe glad it worked. have fun. :)

---

