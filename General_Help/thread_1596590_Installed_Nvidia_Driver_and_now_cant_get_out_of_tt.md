---
title: "Installed Nvidia Driver and now cant get out of tty1"
date: 2010-10-14
forum: General Help
---

### Post by Akaedintov on 2010-10-14
Installed 10.10 Ubuntu for the first time and without problem problem.

At first i entered the ubuntu from grub with no problems. Ubuntu has found 2 drivers needs permission to install. One of them was wireless connection driver and the other one was for Nvidia. After i allowed them , it rebooted and since then i cant see my ubuntu desktop ever again. It always comes to a black screen like this;

Ubuntu 10.10 Akaedintov tty1

akaedintov login:
password:


i enter these informations and and prompt comes in;
aka@akaedintov: ~$ 


Any help ? 

Thanks.

---

### Post by dino99 on 2010-10-14
from the prompt:

sudo rm -f /etc/X11/xorg.conf
( if an error says: dont exist, then its ok)

sudo apt-get update
sudo apt-get install -f
sudo dpkg --configure -a

then reboot and check driver activation: system admin additional driver

---

### Post by Refalm on 2010-10-14
You should have read the sticky first.

Here is the solution:
[http://ubuntuforums.org/showpost.php?p=9965364&postcount=9](http://ubuntuforums.org/showpost.php?p=9965364&postcount=9)

---

### Post by Akaedintov on 2010-10-14
both solutions arent working. 

and about the solution refalm linked for;

"If X is still not starting, add this to /etc/xorg.cfg:"

how do i do that if i cant reach to desktop and else?

---

### Post by Akaedintov on 2010-10-14
/etc/xorg.cfg

no such file or directory

there is an error. what should i do ? i deleted windows for it and my computer is just useless. help me please.

---

### Post by dabl on 2010-10-14
Log in to the tty.

```
sudo service gdm stop
```

```
sudo service gdm start
```

What is the error message that you see?

---

### Post by Cole119 on 2010-10-14
I'm having this problem too. I've tried every suggestion so far, but none help. 
@dabl I tried that, but it didn't give an error it just said it was assigned to process 1000 something (can't remember exactly). 
OP, did you manage to figure it out?

---

### Post by Akaedintov on 2010-10-15
non of these solutions worked. There is still no desktop coming trough.
i logged in and used
"sudo apt-get remove nvidia-current"

and in recovery mode , used failsafe(use generic configurations).

now i'm using non updated versions. This driver is not active but it is really annoying since i cant use my HDMI or 3D or something. I'm waiting for a Nvidia ION 2 Driver ..nothing i can do for now.

---

### Post by Akaedintov on 2010-10-16
someone help please ? I'm stuc with prompt , whenever i use startx , it says;

Fatal Server Error;
No screen found

---

### Post by BLAD3_ on 2010-10-20
same here ..
i got the black screen with the tty1 
when i hit the user name and password i go back using terminal 

i did this 

> **Refalm said:**
> 
```
sudo add-apt-repository ppa:ubuntu-x-swat/x-updates
sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade
```



but still got the fatal error no screen found every time i try stratx

---

### Post by Cole119 on 2010-11-03
Has anyone figured this out yet?

---

### Post by dcompiled on 2010-11-06
same problem, 10.10 is crap...

---

### Post by Mecasickle on 2010-12-26
Wow I have exactly the same problem on my new Alienware computer...

I've been trying all the fixes on the web (mentioned on this trhead, and on others too). Nothing so far...

Could some1 give us a hand? 
Thanks!

---

### Post by cgroza on 2010-12-26
Try the nouveau driver.I can get 3d with it.

---

### Post by llawwehttam on 2010-12-26
can't you just do:

```
**nvidia-xconfig**
```

---

### Post by Mecasickle on 2010-12-26
I actually did :
sudo nvidia-xconfig

It gives me this message:

Using X configuration file: "/etc/X11/xorg.conf"
Backed up file '/etc/X11/xorg.conf' is '/etc/X11/xorg.conf.backup'
New X configuration file written to '/etc/X11/xorg.conf'

then, I read that I should just go with 
startx

but it fails to go to the desktop environment

Anyway, I just rebooted, and it stills gives me the tty1 black scrren as long as a I boot with nomodeset instead of quiet and splash.

Am I missing somthing?

---

### Post by Mecasickle on 2010-12-26
Bump.

Merry Christmas!

---

### Post by serlex on 2010-12-28
Same problem here. After grub I get left in tty1 login screen

```
startx
```

Gives 'No screens found'

Using nvidia graphics card on a laptop

---

### Post by newbie80 on 2011-03-20
I had the exact same issue yesterday when I was trying to install ubuntu 10.10 on my desktop. Earlier I had windows vista + ubuntu 9.1, rather than upgrade from 9.1 to 10.10 I decide to wipe out everything and do a fresh install of 10.10. Once I installed 10.10 and then the latest nvidia drivers I was unable to startx no matter what - stuck at tty1 login everytime. Tried all the solutions posted on this thread and some others but nothing worked. The real issue (at least when the log says Screen not found) is explained in this thread at nV forums [http://www.nvnews.net/vbulletin/showpost.php?p=2118873&postcount=22](http://www.nvnews.net/vbulletin/showpost.php?p=2118873&postcount=22). Luckily I had windows7 install cd with me. I did a windows 7 install (installed nvidia driver in windows) and then ubuntu 10.10. This time after installing the nvidia drivers in ubuntu 10.10 there was no problem. I didn't have to save the edid.bin file as posted there just installing windows solved the problem for me. Others may have to follow the instructions exactly. Hope this helps.

---

