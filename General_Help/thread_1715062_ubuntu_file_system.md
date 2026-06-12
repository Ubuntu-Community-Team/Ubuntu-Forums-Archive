---
title: "ubuntu file system"
date: 2011-03-26
forum: General Help
---

### Post by SShafa on 2011-03-26
Hi. I'm new at ubuntu. Just downloaded 10.10. While installing, I was confused which file system to use. I have a 250gb hard disk with 4 NTFS partition. C primary and d, e, f logical/extended. C and d has win7 and winXP installed. E stores my data. And now i want to install ubuntu on f drive. Currently it is in ntfs. So which file system should i use. If i just select f and click forward, then it is showing some 'root not mentioned' error. It is asking me to go to partition menu and choose the root. Please help me on this. I stuck here.

---

### Post by nothingspecial on 2011-03-26
Choose to use as an ext4 journaling file system.

Choose to format it

Choose a mount point of /

Don't pick the wrong partition or [COLOR="Red"][SIZE="3"]BANG![/SIZE][/COLOR]

---

### Post by jerome1232 on 2011-03-26
You will want to make a swap partition as well, doesn't need to be very big, usually = to your ram but you don't have to go over 1 GB imo.

---

### Post by SShafa on 2011-03-26
Thanks bros for you quick replies. I would like to add some info here.
First, I don't have any ups, and I'm not going to have one soon. So power failure is common. I read somewhere that ext4 are vulnerable to power failure and may cause data corruption?
In windows I never had any problem of data corruption due to power loss.
Secondly, Please tell me some more about swap. I have 4gb of ram.

---

### Post by nothingspecial on 2011-03-26
You can use ext3 if you feel more comfortable with that.

You need  swap if you have a laptop and want to hibernate.

A swap partition is not necessary, you can create a swap file after installing. Read this.

[https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq)

---

### Post by SShafa on 2011-03-29
Thanks bros, I've successfully installed ubuntu. I.ve used ext3 as file system. But now in system monitor, it is showing only 2.9gb of memory while I've 4gb. Does this 32bit ubuntu not support more than 3gb ram as windows? Should I use 64bit ubuntu or just be happy with that 2.9gb? I didn't creat any swap partition. Should I use 3gb swap file or not at all?
Will be waiting bro for your kind reply..

---

### Post by t0p on 2011-03-29
I think you should use 64-bit version of Ubuntu if you have a 64-bit computer; otherwise you're not going to be able to use all that RAM you've got.

If you decide to reinstall, I don't know of any reason why you shouldn't use ext4 file system.  As far as I know ext4 is just as capable (if not more capable) as ext3 at recovering from sudden power cut.  Both ext3 and ext4 are journalling file systems, which are designed to recover from unexpected power loss; and ext4 is a "newer, improved" file system.

---

### Post by nothingspecial on 2011-03-29
If you have the space, then yeah, create a swap file. It can't hurt.

---

### Post by SShafa on 2011-03-30
so I should use x64 with ext4 file system and a 4 gb swap partition/file.
thank you bros I'm gonna reinstall.
And one more question, I don't have internet for 24 hour. So how should i download/install all that codecs needed for playback of my media files after finishing my setup? (2 or 3 hours later) I had a look on software centre and synaptic. I saw a lot of them in the list. but I don't know which one to install.

---

### Post by NFblaze on 2011-03-30
No, you should just use the x64 bit version of Ubuntu if you want to use all 4gb of RAM.

It is not necessary for you to use teh ext4 file system or a 4gb sized swap space unless you want to.

For installing you multimedia codecs easiest method is to take a look at [http://medibuntu.org/](http://medibuntu.org/)

---

### Post by Pro_Wikileaks on 2011-03-30
im newbie  in ubuntu, is anybody can teach me how first time using ubuntu in my compiz,,,

---

