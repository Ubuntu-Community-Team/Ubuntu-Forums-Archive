---
title: "Need advice on Partition Setup"
date: 2010-11-15
forum: General Help
---

### Post by pheserus on 2010-11-15
I'm trying to make a partition setup with all my documents,
user settings, and applications all on a single separate partition.
Like this.

[Partition 1]
/

[Partition 2]
/data
   [COLOR=White]__[/COLOR]/data/home
[COLOR=White]__[/COLOR]/data/usr/local

[Partition 3]
Swap

So I'm asking, how would I go about doing this? And is /usr/local
where programs are installed? If so how would I put it and home on
this other partition? Symbolic link? If anyone could give me some
advise on this, or tell me how I could do it better, I would be
quite grateful.

---

### Post by viralmeme on 2010-11-15
> **pheserus said:**
> I'm trying to make a partition setup .. So I'm asking, how would I go about doing this?

[Choosing How Ubuntu Partitions the Harddisk]("http://www.easy-ubuntu-linux.com/ubuntu-installation-606-7.html")

---

### Post by pheserus on 2010-11-15
I'm sorry but I don't see anything in that link that helps me. Perhaps you could point
out what exactly on that page you are referring to. Maybe I should be more specific.
I know how to setup a partition table and how to format and mount directories.

But what I don't know is how to properly move directories like /usr/local and /home after an
installation, or if /usr/local is the correct directory for user installed application files.

---

### Post by srs5694 on 2010-11-15
You can't do precisely what you want to do in Linux, at least not easily. You *can*, however, put your /home directory on a separate partition, as described [here,](http://www.psychocats.net/ubuntu/separatehome) among other places.

The problem with your goal of isolating program files to their own partition is that Linux doesn't organize them in a way that makes this easy. Program files are scattered about in a variety of directories (/usr/bin, /usr/sbin, /bin, and /sbin being the major ones), and it's not easy to change where they reside, at least not when using standard Ubuntu packages. (In theory, you could create your own distribution that does things differently, but it would be a major undertaking, and the result would be a very non-standard Linux distribution.) For technical reasons, the contents of /bin and /sbin can never be split off from the root (/) directory. Further complicating this is the fact that programs rely on libraries, which also have their own locations, such as /usr/lib and /lib. Then there are documentation files, configuration files, etc. Thus, when you install a package, it'll drop files all over the place. You can split off certain directories, such as /usr, into their own partitions, and there are advantages to doing this; but reorganizing your program files so that everything from /usr/bin, /usr/sbin, and so on are all in some arbitrary new directory (whether it's on its own partition or not) is likely to result in a computer that won't boot.

To better understand the logic behind all this, first keep in mind that Linux doesn't treat partitions the way Windows does; in Linux, all files are accessible from a single unified filesystem. There are no drive letters in Linux; partitions are mounted at mount points, which grafts them into the unified filesystem. At a high enough level, it doesn't matter whether /usr is an ordinary directory off of the root (/) directory or if it's a separate partition. When placing files, only the directory matters. Second, consult the [Filesystem Hierarchy Standard (FHS)](http://www.pathname.com/fhs/) for information on what goes where. Although there is some "wiggle room" for deviation from the FHS, altering it in a significant way will create waves of consequences that will radically alter a Linux system.

---

### Post by viralmeme on 2010-11-15
> **pheserus said:**
> I'm sorry but I don't see anything in that link that helps me. Perhaps you could point
out what exactly on that page you are referring to. Maybe I should be more specific
[IMG]http://img593.imageshack.us/img593/2136/livecdbootmenuzoomed.png[/IMG]
Put the CD in the computer, switch it on and when you see the above image, click on the words "[SIZE="2"]**Start or install Ubuntu**[/SIZE]".

> **pheserus said:**
> I know how to setup a partition table and how to format and mount directories. But what I don't know is how to properly move directories like /usr/local and /home after an installation, or if /usr/local is the correct directory for user installed application files.

[IMG]http://img337.imageshack.us/img337/2388/installnewpartitionmoun.png[/IMG]

Working through the installation, you will come to a screen labeled "[SIZE="2"]**Prepare mount points**[/SIZE]", using the drop-down menus select root, home and swap, then continue with the installation.

---

