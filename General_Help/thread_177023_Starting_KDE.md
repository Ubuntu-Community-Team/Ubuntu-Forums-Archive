---
title: "Starting KDE"
date: 2006-05-15
forum: General Help
---

### Post by albox on 2006-05-15
Hello,

I have just installed KDE on breezy and I have some troubles. When I try to boot with my kernel 686-smp, the system freezes but if I start the recovery mode, then "startx", everything goes well...

I tried to changed the user (with login) but when I try "startx", I get :
"X : user not authorized to run X server, aborting"

I also tried to add my user with : "xhost + myuser:0.0" but it doesn't work since I get :
"xhost : unabble to open display '' "

Even if I set the DISPLAY variable, i get the same error :
"xhost : unabble to open display '127.0.0.1' "

Can you help me ? First, do you know how I can get the log about the system freeze ? Second, do you know why I can't start KDE except when I'm root ?

Thank you ;)

---

### Post by aysiu on 2006-05-15
[QUOTE=albox]
I tried to changed the user (with login) but when I try "startx", I get :
"X : user not authorized to run X server, aborting"[/QUOTE] I don't know what's going on. [This web search doesn't turn up much](http://www.google.com/search?num=100&hl=en&lr=lang_en&safe=off&q=X+%3A+user+not+authorized+to+run+X+server%2C+aborting+site%3Aubuntuforums.org&btnG=Search).

If X works for root but not for user, it sounds as if your user isn't in the right groups. Print this out: ```
root:x:0:
daemon:x:1:
bin:x:2:
sys:x:3:
adm:x:4:firstuser
tty:x:5:
disk:x:6:
lp:x:7:cupsys
mail:x:8:
news:x:9:
uucp:x:10:
man:x:12:
proxy:x:13:
kmem:x:15:
dialout:x:20:firstuser,cupsys
fax:x:21:
voice:x:22:
cdrom:x:24:firstuser,haldaemon
floppy:x:25:firstuser,haldaemon
tape:x:26:
sudo:x:27:
audio:x:29:firstuser
dip:x:30:firstuser
www-data:x:33:
backup:x:34:
operator:x:37:
list:x:38:
irc:x:39:
src:x:40:
gnats:x:41:
shadow:x:42:
utmp:x:43:
video:x:44:firstuser
sasl:x:45:
plugdev:x:46:firstuser,haldaemon
staff:x:50:
games:x:60:
users:x:100:
nogroup:x:65534:
dhcp:x:101:
syslog:x:102:
klog:x:103:
firstuser:x:1000:
lpadmin:x:104:firstuser
scanner:x:105:firstuser,cupsys
admin:x:106:firstuser
crontab:x:107:
ssh:x:108:
messagebus:x:109:
haldaemon:x:110:
slocate:x:111:
``` Then reboot into recovery mode and type ```
cp /etc/group /etc/group_old
nano /etc/group
``` and compare it to the printout. Substitute your actual username for *firstuser*. After you've made your changes, save (control-x). confirm (y), and exit (Enter). Then reboot again and see if you can *startx*.

---

### Post by albox on 2006-05-15
I just checked my group and I can startX. Indeed, I tried to run kdm and I can login with my usual user. I still don,t understand why I can't start KDE during the boot. Do you know how I can find the error ?

Thank you :D

---

### Post by aysiu on 2006-05-15
So your computer boots to the command prompt? Have you tried logging in and typing ```
sudo /etc/init.d/kdm restart
```?

---

### Post by albox on 2006-05-16
No, the system freezes before the prompt.

---

### Post by albox on 2006-05-16
Really amazing ! I can start KDE with my user if I start kdm after booting with the recovery console but if I try to boot using the "usual way", the system freezes.
Do you know how I can get an error message ?

Thank you ;)

---

### Post by albox on 2006-05-21
up !
Any advices or suggestions ?

---

