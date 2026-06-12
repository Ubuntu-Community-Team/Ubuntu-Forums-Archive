---
title: "install 10.10 keeping old /home partition"
date: 2010-10-20
forum: General Help
---

### Post by andres-bracho on 2010-10-20
I'm sure this should be asked before but I just couldn't find it when searched.

I have a netbook (Acer Aspire One ZG5) with ubuntu only partitioned this way:
/
swap
/home

Since this ubuntu is 10.04 upgraded many times (since 8.04) I want to make a fresh install, and also want to take the oportunity to install and give a try to meego, so I want to...
/ ubuntu
/ meego
swap (need to expand)
/home (ubuntu)

My question is can I keep my current /home partition (which is encripted) and use it with my new 10.10? How?

Thanks in advance.

---

### Post by sgosnell on 2010-10-20
Just install it, and have the installer use your current /home as /home.  It's simple to do.

Why do you think you need to expand your swap area?  You only need about the size of your RAM in case you use hibernate, rarely more.  Having more OSs installed doesn't necessitate more swap, because only one can run at one time, so they can both use the same swap area, it's not persistent.

---

### Post by andres-bracho on 2010-10-20
Thank you for your quick answer... then tomorrow morning I'll install my brand new Ubuntu (NBR)   :P

I want to expand swap because I need more... let me explain... this netbokk have 1GB of RAM memory, I give it 1 GB of swap but I always hibernate almost never shutdown the computer and with 10.04 I the computer just freeze when I try to hibernate, I found that is a bug and that I need 2.5 GB of swap, that's why I'm going to expand it...

I don't know if 10.10 needs the same amount of swap than 10.04 but just in case...

Oh! and I was thinking that since Meego is still too new and in development (not a mature project) I will not install it, I don't want to find myself "hanging in the air" again like it happened with moblin when they just moved to the new project...  :(

---

### Post by oldfred on 2010-10-20
While /home will save all your user settings, if you have made any system settings they will be in /etc config files. You may want to save those just in case you need to add settings again.

Also if you have added a lot of programs and want to reinstall you can save a list. It will reinstall the newest versions of the same apps.

 dpkg --get-selections > ubuntu-files
from lovinglinux - use dpkg to list installed apps
[http://ubuntuforums.org/showpost.php?p=7157175&postcount=5](http://ubuntuforums.org/showpost.php?p=7157175&postcount=5)

You have to use manual install where you choose which partitions to use. Select your current Ubuntu install for / (root) and which format to use ext3 or ext4. You also select /home but DO NOT format it. Not sure what settings may be required for encryption.

You can use gparted to edit partitions.
GParted partitioning software - Full tutorial 
[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)
[http://www.ibm.com/developerworks/linux/library/l-resizing-partitions-1/index.html](http://www.ibm.com/developerworks/linux/library/l-resizing-partitions-1/index.html)
[https://help.ubuntu.com/community/HowtoPartition](https://help.ubuntu.com/community/HowtoPartition)

Some examples of installs:
[http://news.softpedia.com/news/Installing-Ubuntu-10-10-160966.shtml](http://news.softpedia.com/news/Installing-Ubuntu-10-10-160966.shtml)
Maverick partition by hand to use free space:
[http://sites.google.com/site/easylinuxtipsproject/partitioning](http://sites.google.com/site/easylinuxtipsproject/partitioning)
[http://www.dedoimedo.com/computers/ubuntu-maverick.html](http://www.dedoimedo.com/computers/ubuntu-maverick.html)

---

### Post by sgosnell on 2010-10-21
I found that 10.10 found the packages already installed and updated them for me, without having to do it manually.  A new install won't do that, of course, but it's a good argument for updating vs doing a new install.  

10.10 seems to have a problem with waking up from suspend/hibernation, so be prepared for trouble with that, regardless of the amount of swap.  There are lots of threads on this problem on the forum, and no firm solutions.  I suspect it's a video card problem, but I still can't say for sure.

---

### Post by andres-bracho on 2010-10-21
Thank you all.

I'll check those links and start installing.

---

