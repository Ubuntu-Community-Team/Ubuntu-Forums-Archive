---
title: "Partition Space"
date: 2011-04-19
forum: General Help
---

### Post by lelantus on 2011-04-19
I've been using Ubuntu for about two years now, and absolutely love it.

I installed via 64-bit Wubi on a Dell Studio running Vista and am now, as is typical for a year of use, running out of space on the root file, as is shown in the df -h output below:

```
/dev/loop0             17G   15G  808M  95% /
none                  2.0G  312K  2.0G   1% /dev
none                  2.0G  312K  2.0G   1% /dev/shm
none                  2.0G  316K  2.0G   1% /var/run
none                  2.0G     0  2.0G   0% /var/lock
none                  2.0G     0  2.0G   0% /lib/init/rw
/dev/sda3             284G  164G  120G  58% /host
/dev/loop1             14G  5.8G  7.3G  45% /home
```As you can see, I've still got plenty of space left on the hard drive as a whole (around 120G) and would really like to expand the Wubi partition into it.

I'd love to just scrap Windows completely, but I've definitely got to use some of the applications there and can't manage a way to do it without some serious emulation that my RAM just can't support.

LVPM doesn't support 10.04 distributions (which I'm currently using), and I'm looking for a viable workaround.

Any ideas?

---

### Post by lelantus on 2011-04-19
[UPDATE]

I've also attempted to use the wubi-add-virtual-disk approach described here in the past, but apparently it didn't work. Upon trying to run it again, I received the following error:

```
~$ sudo sh wubi-add-virtual-disk /home 25000
The target virtual disk /host/ubuntu/disks/home.disk already exists, aborting.

```I can usually figure this kind of stuff out on my own, but I'm pretty stumped here...

---

### Post by grahammechanical on 2011-04-19
I do not have the answer but I do not think that Wubi is installed in a partition of the hard disk. As I understand things Wubi is a Windows program that allows you to run Ubuntu inside Windows. It is my guess that you need to find a way to assign the Wubi program more disk space. When you installed Wubi and Ubuntu were you asked to assign a certain amount of disc space? Is there a Help document for Wubi that might give you this information? Is there any kind of menu item in Wubi that says Settings?

Regards

---

### Post by lelantus on 2011-04-19
Your understanding is correct, that' exactly how Wubi works.

There is a program (LVPM) that allows for the modification of the Wubi virtual partition and is recommended in Wubi help files, but as stated in the original post and on [the LVPM website]("http://lubi.sourceforge.net/lvpm.html"), it doesn't work with 10.04.

To clarify, I don't need more space alloted to my /home file, I need more space for /root.

Thanks for the input!

---

### Post by lmarmisa on 2011-04-19
I propose a very simple solution based on a symbolic Link suitable for storing data files (documents, photos, videos, etc). I do not recomend to store any program of Ubuntu there.

You could create a folder named MyData in the Wndows partition. I will create it on the root of the Windows unit but your could create it in any other place:

```

mkdir /host/MyData

```

Now you can create one (or even more) symbolic link(s) pointing to that folder /host/MyData. In this example I will create that link on the Desktop:

```

cd ~/Desktop
ln -s /host/MyData MyData

```

You can store now as files as you wish with the only limit of the size of the physical hard drive.

---

### Post by lmarmisa on 2011-04-19
Please, open a terminal, type this command and post here the results:

```

du -s ~/*

```

This command shows the space used by each directory of your home folder.

---

### Post by lelantus on 2011-04-19
A good solution if my /home directory was full, but sadly, it's /root.

I've linked this problem to the &#8216;/root/.Trash/&#8217; folder, in which the backup from my a virtual partition attempt lies. This backup takes up 5g, but there's also just about every other thing I've ever 'rm -rf'ed before. 

My solution was to do the following:

```
sudo rm -rf root/.local/share/Trash/files/home.2.2.backup/
```Where '/home.2.2.backup' was the obnoxiously large file in question, and presto! By running 'df -h' again, I found that /root was at 47% capacity, substantially less, and a much prettier number to look at.

```
/dev/loop0             17G  7.1G  8.3G  47% /
none                  2.0G  312K  2.0G   1% /dev
none                  2.0G  196K  2.0G   1% /dev/shm
none                  2.0G  328K  2.0G   1% /var/run
none                  2.0G     0  2.0G   0% /var/lock
none                  2.0G     0  2.0G   0% /lib/init/rw
/dev/sda3             284G  164G  120G  58% /host
/dev/loop1             14G  5.8G  7.3G  45% /home

```Thanks to those of you who helped jog my mind. Turns out it was a simple solution after all, haha.

---

