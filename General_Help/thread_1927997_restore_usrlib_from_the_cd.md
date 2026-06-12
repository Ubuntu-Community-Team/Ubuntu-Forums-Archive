---
title: "restore /usr/lib/ from the cd"
date: 2012-02-19
forum: General Help
---

### Post by ruigoncalves on 2012-02-19
Hi there!

I've accidentally deleted several files (including directories) from the /usr/lib/ directory. It is possible to restore them using an installation cd?

Thanks in advance for the help,
Best regards!

---

### Post by dragonfly41 on 2012-02-19
I can't help .. I've got the same problem ..  :confused:

[http://ubuntuforums.org/showthread.php?t=1927746](http://ubuntuforums.org/showthread.php?t=1927746)

so I'm interested in the answer.


[Later Edit]

Found this thread .. and tried the tip in post 1 in that thread

[http://ubuntuforums.org/showthread.php?t=157250](http://ubuntuforums.org/showthread.php?t=157250)

I tried to get into my /root partition from Live CD using this 

**[COLOR=Navy]chroot /mnt/sda7[/COLOR]**

but got this response ..

**[COLOR=Navy]chroot: cannot change root directory to /mnt/sda7: No such file or directory[/COLOR]**

I next tried this .. using the mount point found from GParted

**[COLOR=Navy]chroot /media/8eeb2f0d-92c7-463e-8961-3a1241fc148a[/COLOR]**

but got this

**[COLOR=Navy]chroot: cannot change root directory to /media/8eeb2f0d-92c7-463e-8961-3a1241fc148a: Operation not permitted[/COLOR]**


so I'm no nearer the solution.

---

### Post by dragonfly41 on 2012-02-19
I have finally tracked down how to get into the internal Ubuntu **[COLOR=Navy]root partition[/COLOR]** using Live CD

Here is the manual on **[COLOR=Navy]chrooting into the root partition[/COLOR]**

[http://ubuntuforums.org/showthread.php?t=1581099](http://ubuntuforums.org/showthread.php?t=1581099)


Read the section **[COLOR=Navy]Chroot[/COLOR]**

[COLOR=Blue]# If You Have a Normal Installation. No separate /boot partition, not a Windows/Wubi installation.
Code:

sudo mkdir /mnt/temp 
sudo mount /dev/sdXY /mnt/temp  # Example: sudo mount /dev/sda5 /mnt/temp
[/COLOR]

Here is a log of my terminal commands .. note that I have root partition as /dev/sda7 and /home partition as /dev/sda8

I made sure that these were[COLOR=Navy]** unmounted**[/COLOR] to start with


[COLOR=Blue]ubuntu@ubuntu:~$ sudo mkdir /mnt/temp
ubuntu@ubuntu:~$ sudo mount /dev/sda7  /mnt/temp
ubuntu@ubuntu:~$ for i in /dev /dev/pts /proc /sys; do sudo mount -B $i /mnt/temp$i;  done
ubuntu@ubuntu:~$ sudo cp /etc/resolv.conf /mnt/temp/etc/resolv.conf  # May be required to connect to the Internet.
ubuntu@ubuntu:~$ sudo chroot /mnt/temp

root@ubuntu:/# [/COLOR]


At this point i decided I'd better mount the /home partition as well


[COLOR=Blue]root@ubuntu:/# sudo mount /dev/sda8 /mnt/temp
sudo: error while loading shared libraries: libpam.so.0: cannot open shared object file: No such file or directory
root@ubuntu:/# [/COLOR]


This was the error I had when trying to boot up Ubuntu from cold.

Why libpam.so.0 is missing I don't know but I'm trying to replace it to try to boot up normally.


Making sure I had internet connection i next tried

[COLOR=Blue]apt-get update[/COLOR]

which worked o.k.


At this point .. as I understand it .. we should be able to download library files (from where though ?) and copy files into root partition .. /usr/lib/   ???

Anyone in forum to give more tips?


......

[EDIT]

I'm parking this next useful link here since I'm in Live CD mode and I can't bookmark links.

[http://ubuntuforums.org/showthread.php?t=801333&highlight=reinstall+libpam](http://ubuntuforums.org/showthread.php?t=801333&highlight=reinstall+libpam)

---

