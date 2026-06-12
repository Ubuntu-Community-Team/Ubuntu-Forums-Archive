---
title: "Windows-readable /home"
date: 2010-10-04
forum: General Help
---

### Post by Vapourstreak on 2010-10-04
I just bought a new 16GB usb, which I'll run Ubuntu off.  But my few months at this boarding school made me realize the limits of the computer when using Windows without any of my personal data.  The point of having a bootable USB for me was so I could plug in and use my own Ubuntu installation in most computers I come across, but the school's computers have a BIOS password, so I'm unable to change the boot order.

So what I'm planning to do is install Ubuntu on a smaller partition, maybe 2-3GB, and have the rest, about 10GB, I think, used as the default /home folder.  The /home partition would need to be a filesystem that can be used by Ubuntu and Windows, though, is that possible?  The smaller ubuntu install partition would be Ext4, and i was planning to make the /home partition FAT16 or FAT32.  Would that work? 

And could someone tell me how to change the default /home location in the Ubuntu settings?

---

### Post by SaintDanBert on 2010-10-04
When each username does login, initial details from that user get read from /etc/passwd.  Two details there are (1) the path to their $HOME folder, and (2) the path and program name for their command line shell.
The typical and traditional behavior is to have a folder named **/home** in the root folder of your file system. That folder then contains a set of folders, each name matches the usernames for each of your users.

I would not stray from this traditional approach!!

If you want to integrate where your linux login and your windows login store files, linux is much more flexible and friendly with NTFS and FAT32 than win-doze is with anything else.

There are utilities for win-doze that let you open a "file explorer" looking application and then read the contents of many of your linux file systems. Also, there is a win-doze service that enables mounting of linux file systems using the drive-letter approach. I used to use both of these techniques, but have not done so for some time.

Bonne chance,
~~~ 0;-Dan

---

### Post by SaintDanBert on 2010-10-04
Let me be clear.  I would configure linux to access your minimal sized win-doze folders and files rather than try to teach win-doze to work with linux parts.

~~~ 0;-Dan

---

### Post by Vapourstreak on 2010-10-04
Yeah, I know Linux plays a lot better with Windows, than Windows with Linux, but the school only has Windows computers, and I need access to my files on the Ubuntu flash drive.  I can't install anything in the school's Windows. I was just hoping to have a common partition that both Ubuntu and Windows can access, and was hoping Ubuntu, being the dominant system that I use, could write it's data to that partition in default, so it saves me from copying files over every time.

---

### Post by Vapourstreak on 2010-10-04
Chewbacca choked on a chocolate?

Bump.

---

### Post by psusi on 2010-10-04
In a word: no.  /home needs to be on a unix fs with proper permissions.  You can store your documents on the windows partition though.

---

### Post by Simian Man on 2010-10-04
You can try [this]("http://www.fs-driver.org/").  I've never tried it before though.

---

### Post by Vapourstreak on 2010-10-04
Oh okay.  So the main problem is Windows not being able to read/write linux fs's.

**** windows.

EDIT:  So if I want to move /home onto another linux partition, it would work?  Can someone tell me how?

---

### Post by psusi on 2010-10-04
> **Vapourstreak said:**
> Oh okay.  So the main problem is Windows not being able to read/write linux fs's.

**** windows.

EDIT:  So if I want to move /home onto another linux partition, it would work?  Can someone tell me how?

These two statements contradict one another.  The first explains why the answer to the second is no.

---

### Post by Vapourstreak on 2010-10-04
> **psusi said:**
> These two statements contradict one another.  The first explains why the answer to the second is no.

No, the 'work' in edit didn't mean access through Windows, just that it was possible to have the /home on another partition, nothing to do with Windows.  Is that possible?

Sorry for the confusion.

---

### Post by psusi on 2010-10-04
Ohh, yes, though I advise against it.

---

### Post by Vapourstreak on 2010-10-04
Oh okay.  Why not?  Is there a lot of problems?

---

### Post by SeijiSensei on 2010-10-04
> **Vapourstreak said:**
> Yeah, I know Linux plays a lot better with Windows, than Windows with Linux, but the school only has Windows computers, and I need access to my files on the Ubuntu flash drive.  I can't install anything in the school's Windows. I was just hoping to have a common partition that both Ubuntu and Windows can access, and was hoping Ubuntu, being the dominant system that I use, could write it's data to that partition in default, so it saves me from copying files over every time.

Just create a partition with an NTFS file system.  Both operating systems will recognize it and be able to read and write to it.  You don't need to mount it as /home; it will show up in Nautilus or Dolphin by default.

---

### Post by Vapourstreak on 2010-10-04
> **SeijiSensei said:**
> Just create a partition with an NTFS file system.  Both operating systems will recognize it and be able to read and write to it.  You don't need to mount it as /home; it will show up in Nautilus or Dolphin by default.

It'll be a lot easier if Ubuntu writes directly to it, though.  Otherwise, I don't know how big the partition's should be.

---

### Post by psusi on 2010-10-04
> **Vapourstreak said:**
> Oh okay.  Why not?  Is there a lot of problems?

Because invariably you end up filling one up but still have plenty of space left on the other.

---

### Post by psusi on 2010-10-04
> **Vapourstreak said:**
> It'll be a lot easier if Ubuntu writes directly to it, though.  Otherwise, I don't know how big the partition's should be.

It should be as big as the files you want to store there.

---

### Post by srs5694 on 2010-10-04
Unless I misunderstand something, you've got more fundamental problems: You state that your school's computers are locked down such that you can't install your own software on them or redirect them to boot from a USB drive. If that's the case, I can't see how you're going to boot Linux on them, short of cracking them (a good way to get expelled, or even prosecuted). If I've misunderstood, please elaborate on how you intend to boot Linux. The answer may be critical to how you'll end up using your USB flash drive.

---

### Post by SaintDanBert on 2010-10-04
If you must move $HOME, edit /etc/passwd for that username and change the target path.  It must be a file system mounted within your running linux.

It seems that you boot from USB drive and need that running linux to (1) interact with windows file space, and (2) offer persisitent storage while in linux file space.  Is this correct?

I don't have a link handy, but I've read HOWTO for thumb drive boot with persistent storage.

Bonne Chance,
~~~ 0;-Dan

---

### Post by SaintDanBert on 2010-10-04
AGREED!!!  See my related post.

If you simply want linux commands and such, take a look at Cygwin.
It is a *nix "programmers workbench" -- bash, grep, less, and friends
-- that runs on top of win-doze.  Some have even made X11 work.
You could install that to your thumb drive and then use its features
from your windows login.

~~~ 0;-Dan

---

### Post by cariboo on 2010-10-04
We really aren't here to help the op circumvent IT policies at his school. 

If he wants to run Unbuntu on the computers at his school, he should talk to the IT department.

This thread is closed.

---

