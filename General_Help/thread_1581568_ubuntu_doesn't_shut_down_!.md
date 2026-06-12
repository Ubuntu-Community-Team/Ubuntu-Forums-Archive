---
title: "ubuntu doesn't shut down !"
date: 2010-09-25
forum: General Help
---

### Post by reza1717s on 2010-09-25
Hi,
I have a dual boot vista/ubuntu 10.10.,everything runs very smoothly & i am really happy with it,just in the last 5-6 shut downs,after ubuntu closes all my file & app,i represent with  ubuntu logo screen,i wait each time for very long time(>10-15 min),but it doesn't turn off,& interesting thing is the each next time i can boot & log in without any problem too,any suggestion please ?
p.s.(i already used recovery mode-repair broken package too .)

---

### Post by 666f6f on 2010-09-25
Hi there,

Can you post your /etc/fstab & attach your /var/log/syslog?

Also, if you boot into recovery mode/root console and try to shutdown, does your system shutdown properly?

---

### Post by reza1717s on 2010-09-25
> **666f6f said:**
> Hi there,

Can you post your /etc/fstab & attach your /var/log/syslog?

Also, if you boot into recovery mode/root console and try to shutdown, does your system shutdown properly?
Hi,i don't know where to look for "/etc/fstab &  /var/log/syslog?",i am unfamiliar with Linux (i am trying  to learn!),
I went to recovery mode/root console &  i tried to shut down from there,i couldn't,but in the next boot,instead of regular GUI of ubuntu,i got a command line which asked for my user name & pass,but after i typed them correctly ,i didn't know how to activated my GUI,i tried to find some command for it with my phone browser like "Xstart" & few others but none of them worked,i had to turn computer off with power button,but next time i get normal ubuntu GUI & i login.
My computer seems to work without problem except it doesn't turn off or restart,i have to use power button each time,some more help please,

---

### Post by 666f6f on 2010-09-26
> **reza1717s said:**
> Hi,i don't know where to look for "/etc/fstab &  /var/log/syslog?",i am unfamiliar with Linux (i am trying  to learn!),

We will do this one step at the time. 

Also, welcome to the Linux world and remember to take backups. Since you just started playing with Linux, it's much easier to do something destructive.

> **reza1717s said:**
> I went to recovery mode/root console &  i tried to shut down from there,i couldn't,but in the next boot,instead of regular GUI of ubuntu,i got a command line.

Hmm, that's not very normal.. But since it works, let's not worry for the moment.

> **reza1717s said:**
> which asked for my user name & pass,but after i typed them correctly ,i didn't know how to activated my GUI,i tried to find some command for it with my phone browser like "Xstart" & few others but none of them worked,

You were very close. The correct command is ```
startx
```.

> **reza1717s said:**
> i had to turn computer off with power button,but next time i get normal ubuntu GUI & i login.
My computer seems to work without problem except it doesn't turn off or restart,i have to use power button each time,some more help please.

It seems that power management doesn't work. Is this a laptop? If yes, can you post the exact manufacturer/model? If it's a desktop, can you find out the exact motherboard model/manufacturer?

---

### Post by Soul-Sing on 2010-09-26
try acpi=force
in etc/default/grub
edit this line: > GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi=force"
```
sudo update-grub
```

---

### Post by 666f6f on 2010-09-26
> **leoquant said:**
> try acpi=force
in etc/default/grub
edit this line: 
```
sudo update grub
```

:bows:

---

### Post by reza1717s on 2010-09-26
Hi,first of all thanks a lot for your help & time.
 <remember to take backups>;i always save my valuable files in an external HDD,is it better to take backup even so?
<that's not very normal.. But since it works, let's not worry for the moment>. ; I had this problem with GUI several other times & that was the reason i had to install & reinstall ubuntu several times till now.i guess that i tried startx too.
My laptop is a sony vaio vgn-fw11m, Intel Core2 Duo Processor P8400,4 Gb ram.
shall i execute :  
<sudo update grub>
?

---

### Post by 666f6f on 2010-09-26
> **reza1717s said:**
> i always save my valuable files in an external HDD,is it better to take backup even so?

That's perfect.

> **reza1717s said:**
> <that's not very normal.. But since it works, let's not worry for the moment>. ; I had this problem with GUI several other times & that was the reason i had to install & reinstall ubuntu several times till now.i guess that i tried startx too.

Maybe you were dropped to some kind of a recovery console because of an unclean shutdown.

> **reza1717s said:**
> My laptop is a sony vaio vgn-fw11m, Intel Core2 Duo Processor P8400,4 Gb ram.

Weird, I did a quick search and don't see any real problems with this laptop.

> **reza1717s said:**
> shall i execute :  
<sudo update grub>
?

Boot into recovery console and type:

```
cp /etc/default/grub /etc/default/grub.bak && sed -i 's/GRUB_CMDLINE_LINUX_DEFAULT=.*/GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi=force"/gi' /etc/default/grub && update-grub && reboot
```

**Make sure you don't make a typo** and keep your fingers crossed!

---

### Post by reza1717s on 2010-09-26
Hi,
I boot to recovery menu/drop to root shell prompt & typed the command line carefully,
but i got something like :"directory or command <mv / etc/default/grub > doesn't exist."
then i turn off system (power button again),in next boot,i went to recovery console again & i chose <grub     update grub bootloader> from recovery menu,then i login & restart again,this time i got new screen about some errors in update,i took a picture from it with my phone (doesn't have a very good quality but it is read able,),i will attach it.

---

### Post by 666f6f on 2010-09-26
Before turning off the computer you should do a ```
sudo poweroff
``` or else your filesystem might be damaged.

From the attached picture I guess that the filesystem is pretty damaged. At this point I would suggest a reinstallation and then we can start over again :(

---

### Post by reza1717s on 2010-09-26
sudo poweroff turned my computer off,& i can turn it off each time with this command but i have the same problem for turning off with GUI,
in other hand it is not difficult for me to reinstall,as you know i have all my valuable on an external HDD,but there is a point here,if i damaged my system files in less then a week,is good to know to avoid what to prevent these damages !  & also if you have a little time maybe you let me to ask you few more questions & tips about two other problem i have,then maybe with better install i can avoid them too, 
my second monitor with hdmi connection gives me very weird colors,in the same time that it is allright with vista,& my microphone doesn't work neither,(that's ok too in vista), i guess these problem have their roots in installation too, because the first time i installed ubuntu,these two worked fine,thanks.

---

### Post by 666f6f on 2010-09-27
> **reza1717s said:**
> sudo poweroff turned my computer off,& i can turn it off each time with this command but i have the same problem for turning off with GUI,

We can come back to this problem after re-installation. I can see from the screenshot that the filesystem is seriously corrupt.

> **reza1717s said:**
> in other hand it is not difficult for me to reinstall,as you know i have all my valuable on an external HDD,but there is a point here,if i damaged my system files in less then a week,is good to know to avoid what to prevent these damages !

Wonderful question! So, here are the tips I can think of..:

1. Always shutdown properly your system (even from the command prompt/terminal). There are a series of things that need to be done before shutting down your system, like clearing software/hardware disk cache and gracefully spinning down the disks.

2. Avoid being root. root has superpowers to create, delete and change everything. A normal (non-privileged) user can only damage his home directory. root can bring chaos to your entire system.

3. Do one thing at the time and keep track of what you're doing as root. Whenever you have to run a command as root, note it down on a piece of paper.

4. Learn some basic stuff on how to use a [DVCS]("http://en.wikipedia.org/wiki/Distributed_Concurrent_Versions_System") like [Mercurial]("http://en.wikipedia.org/wiki/Mercurial_(software)"). This way you can [maintain your /etc in Mercurial]("http://michael-prokop.at/blog/2007/03/14/maintain-etc-with-mercurial-on-debian/"). This way, there's a good chance being able to revert your system to a given stable point, after having broke something.

5. Install VirtualBox and experiment with a virtual linux installation. Apply changes to your main system only when you've verified that they work well (that's not possible when trying to setup hardware).

6. Read some basic things about system administration. [This book]("http://books.google.com/books?id=F37gcHI6IbQC") might be a good start. [These lessons]("http://www.linux.org/lessons/") seem to provide useful information too.

> **reza1717s said:**
> & also if you have a little time maybe you let me to ask you few more questions & tips about two other problem i have,then maybe with better install i can avoid them too, 
my second monitor with hdmi connection gives me very weird colors,in the same time that it is allright with vista,

I'm sorry I can't help you with this issue, I don't even have an HDMI port, it's plain old VGA for me :) It's best to open another thread for this issue.

> **reza1717s said:**
> & my microphone doesn't work neither,(that's ok too in vista), i guess these problem have their roots in installation too, because the first time i installed ubuntu,these two worked fine,thanks.

Let's see if re-installation fixes them.

---

### Post by reza1717s on 2010-09-27
Hi,
Thanks a lot for your time,guidance & useful tips,i already start to brows "Linux for dummies" & hopefully can learn some basics knowledges to work with my new OS.
  <Avoid being root >  ;it isn't very clear to me what it means,but i guess i can find it in the book that i started,if i couldn't,i guess it will be subject of my next thread.
cheers

---

### Post by 666f6f on 2010-09-28
> **reza1717s said:**
> Hi,
Thanks a lot for your time,guidance & useful tips,

You're welcome. I wish I had more time to devote to the forums :)

> **reza1717s said:**
> i already start to brows "Linux for dummies" & hopefully can learn some basics knowledges to work with my new OS.

Great! Personally I think that the fun begins after you've learned the basics. Then you can enjoy a really beautiful OS :)

> **reza1717s said:**
> <Avoid being root >  ;it isn't very clear to me what it means,but i guess i can find it in the book that i started,if i couldn't,i guess it will be subject of my next thread.
cheers

[I]Linux is based on the idea that everyone using a system has their own username and password. Recent versions of Windows finally adopt this principle (sic).

Every file belongs to a user and a group, and has a set of given attributes (read, write and executable) for users, groups and all (everybody).

A file or folder can have permissions that only allows the user it belongs to to read and write to it, allowing the group it belongs to to read it and at the same time all other users can't even read the file.

Linux has one special user called root (this is the user name). Root is the "system administrator" and has access to all files and folders. This special user has the right to do anything.[/I]

You can read more [here]("http://linuxreviews.org/beginner/").

So, say you login with user "supermario". supermario owns all the files under /home/supermario. He can delete anything that's in there, but nothing else. **He can't delete /etc/fstab** for example (he can view it though).

supermario can damage/delete his personal files (photos, documents, e.t.c.) but **he can't damage the system**.

However **supermario can become root** or can run a command as root. If you run a command with the special prefix sudo (it's not really a prefix, it's a command), then this command runs with root priviledges; and can harm your system. For example ```
sudo rm /etc/fstab
``` is run with root privileges and **will damage your system**. supermario can become root if he runs the command ```
sudo -i
```.

You can find out more abou the sudo command by typing ```
man sudo
``` in any terminal. The man command (shortcut for manual) and Google is your friend! You can also use Google to search the ubuntuforums.org like [this.]("http://www.google.com/search?q=site:ubuntuforums.org")

Hope this helps!

---

