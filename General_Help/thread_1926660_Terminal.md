---
title: "Terminal"
date: 2012-02-16
forum: General Help
---

### Post by PadiSka on 2012-02-16
In terminal I am trying to access my music in my windows folder.

I type "cd C:\Documents and Settings\PadiSka\My Documents"
and I get told "bash: cd: C:Documents and Settings\PadiSka\My Documents.: No such file or directory"

Whats the problem?

---

### Post by ajgreeny on 2012-02-16
Is this a partitioned installation or one using wubi where you installed Ubuntu in a running windows system?

---

### Post by mcduck on 2012-02-16
The problem is that you are trying to type in a Windows path, while you are using Linux... ;)

Is it a normal or a Wubi install? Either way there isn't going to be such thing as "C:\", so you'll need to know where in the *Linux directory hierarchy* the Windows drive is mounted to.

(For a normal Ubuntu install, take a look inside /media. And for Wubi install, look into /host. And of course make sure the drive is actually mounted in the first place.)

---

### Post by drmrgd on 2012-02-16
The problem is due to the spaces in the folder names, as well as the path you're using.  

Linux doesn't like that so much.  You can tackle it in one of two ways:

1. Use quotation marks:

```
cd "Documents and Settings/PadiSka/My Documents"
```

2. Use the escape character '\' before the spaces:

```
cd Documents\ and\ Settings/PadiSka/My\ Documents
```

As far as the path goes, two things there, the use of '\' and 'C:\'.  Linux handles filesystems quite a bit differently than DOS.  Likely your windows partition or drive is mounted somewhere (not sure how you're setup), and you need to access that mount point first.  In Windows you would use the 'C:\' to point to the correct drive, which is quite a bit different.  For example, I have a second hard drive with windows on it, which (in Linux terms) is located at /dev/sda2 and mounted to /media/windows/.  I'm not sure how your system is set up, so it's hard to speculate where you Windows drive / partition is located.  We'll need a little more info.  

Secondly, Linux file systems use the '/' character (notice the difference '/' not '\'!) between directories.  As I said above, in the Linux shell '\' does not denote a different directory but an escape character.

So, to sum up, if you system is set up similar to mine, you would get to the folder like this:

```
cd "/media/windows/Documents and Settings/PadiSka/My Documents"
```

Hope that helps get you started.

---

### Post by PadiSka on 2012-02-16
I have dual boot system that I manually partitioned normally like not using wubi.

My windows seems to be mounted to the /media directory alright but the folder after this is not named windows but rather "06F8B445F8B434B1", why is the directory named this nonsense instead of being called "windows"?

Also what is the difference between the locations "/dev/sda2" and mount points "/media" etc. Like basically why do we not have to include /dev/sda2 in a directory path?

Thanks for all the help

---

### Post by 3rdalbum on 2012-02-16
> **PadiSka said:**
> I have dual boot system that I manually partitioned normally like not using wubi.

My windows seems to be mounted to the /media directory alright but the folder after this is not named windows but rather "06F8B445F8B434B1", why is the directory named this nonsense instead of being called "windows"?

Also what is the difference between the locations "/dev/sda2" and mount points "/media" etc. Like basically why do we not have to include /dev/sda2 in a directory path?

Thanks for all the help

/dev/sda2 is the raw device, but /media is where the drive's contents are mounted.

It's difficult to explain the difference, but mounting the device makes it easier for programs to access the contents. By an order of magnitude.

Also, note that if this device was a USB flash drive, then /dev/sda2 exists from the point of insertion up until you physically remove it from the computer. The entry in /media ceases to exist when you unmount the drive. If you could access the drive's contents through /dev/sda2 then you could either never safely remove the drive, or you could never safely repair filesystem damage.

---

