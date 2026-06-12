---
title: "Apt-Get Broken!"
date: 2006-06-15
forum: General Help
---

### Post by david_e on 2006-06-15
Today when the update notifier finished its downloads, installing prompted an error message about some broken package. Now I can't use apt-get anymore!

When I try to open Adept I see this error message:

```
The APT Database could not be opened! 
This may be caused by incorrect APT configuration or some similar problem. 
Try running apt-setup and apt-get update in terminal and see if it helps to resolve the problem.
```
So I tried this apt-setup, but I found that this command does not exists... and apt-update didn't help too... 

When I issue an apt-get check:

```
davide@acer-ferrari:~$ sudo apt-get check
Password:
Reading package lists... Error!
E: Read error - read (5 Input/output error)
E: The package lists or status file could not be parsed or opened.
```
The only notable thing to say about my config is that I have installed the unofficial [kopete0.12 debian](http://www.ubuntuforums.org/showthread.php?t=190273) package I found on this forum and I have put it on hold as I said [here.](http://www.ubuntuforums.org/showthread.php?p=1107250#post1107250)

Windows style solutions like rebooting the computer didn't worked either... :D 

PS : Sorry for my English

---

### Post by eth on 2006-06-15
Non funziona nemmeno il synaptic, vero? ne tanto meno aptitude...?

---

### Post by severedspirit on 2006-06-15
I had some thing like this a while ago, the best thing to do is go to packages.ubuntu.com and download apt-get as a deb file then type

sudo dpkg -i *[deb-file]*

and "hopefully" this should fix it

---

### Post by briguy on 2006-06-15
Try this: sudo dpkg --configure -a

---

### Post by david_e on 2006-06-16
Thank you very much! I was able to solve this problem following your suggestions. I had to download apt.deb and dpkg it [COLOR="Red"]and[/COLOR] I had to dpkg --configure -a as doing only one of these things didn't worked...

---

