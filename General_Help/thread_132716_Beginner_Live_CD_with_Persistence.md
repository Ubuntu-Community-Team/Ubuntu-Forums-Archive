---
title: "Beginner: Live CD with Persistence?"
date: 2006-02-18
forum: General Help
---

### Post by macroron on 2006-02-18
Hello,

I have read this page on the wiki:

[https://wiki.ubuntu.com/LiveCDPersis...8d4f459868bb82](https://wiki.ubuntu.com/LiveCDPersis...8d4f459868bb82)

I partitioned and formatted a floppy.

I inserted the live cd, the newly partitioned and formatted floppy,
and rebooted then clicked on f4.

I typed 'persistent' and clicked on enter.

But I got an error: 'could not find kernel image persistent'.

So I clicked on enter and started up.

After making some changes I rebooted to check if 'persistent' worked.

It did not!

Here is some info from fstab and gparted:

fstab:

/dev/mapper/casper-snapshot / auto noatime 0 0
tmpfs /tmp tmpfs nosuid,nodev 0 0

--

gparted:

/dev/mapper/casper-snapshot1 filesystem=ext2 size=2,047mb used=0 unused=0

/dev/mapper-casper-cow partition=unallocated filesystem=--- size=1,020
unused=0 used=0

Can you please help me?

-ron-

---

### Post by dcstar on 2006-02-18
[QUOTE=macroron]Hello,

I have read this page on the wiki:

[https://wiki.ubuntu.com/LiveCDPersis...8d4f459868bb82](https://wiki.ubuntu.com/LiveCDPersis...8d4f459868bb82)

I partitioned and formatted a floppy.

I inserted the live cd, the newly partitioned and formatted floppy,
and rebooted then clicked on f4.

I typed 'persistent' and clicked on enter.

But I got an error: 'could not find kernel image persistent'.
......[/QUOTE]
It says:

At the **end of this argument list** just add a space and add the word “persistent”

Just "typing" probably replaced the whole line.

---

### Post by macroron on 2006-02-18
Quote:
Originally Posted by macroron
Hello,

I have read this page on the wiki:

[https://wiki.ubuntu.com/LiveCDPersis...8d4f459868bb82](https://wiki.ubuntu.com/LiveCDPersis...8d4f459868bb82)

I partitioned and formatted a floppy.

I inserted the live cd, the newly partitioned and formatted floppy,
and rebooted then clicked on f4.

I typed 'persistent' and clicked on enter.

But I got an error: 'could not find kernel image persistent'.
......
It says:

At the end of this argument list just add a space and add the word “persistent”

Just "typing" probably replaced the whole line.
__________________
Regards, David.

David,

There is no argument list. Just the boot prompt. I tried "persistent", "live persistent", and "linux persistent". Nothing works. Hasn't any body tried this with a floppy?

-ron-

---

### Post by dcstar on 2006-02-18
[QUOTE=macroron]
......
David,

There is no argument list. Just the boot prompt. I tried "persistent", "live persistent", and "linux persistent". Nothing works. Hasn't any body tried this with a floppy?

-ron-[/QUOTE]
You should boot of the Live CD, then "F4" **when the menu is displayed**.

Make sure your system is not booting of anything else.

[https://wiki.ubuntu.com/LiveCDPersistence](https://wiki.ubuntu.com/LiveCDPersistence)

---

### Post by Limulus on 2006-02-20
[QUOTE=macroron][https://wiki.ubuntu.com/LiveCDPersistence](https://wiki.ubuntu.com/LiveCDPersistence)

I partitioned and formatted a floppy.

I inserted the live cd, the newly partitioned and formatted floppy,
and rebooted then clicked on f4.

I typed 'persistent' and clicked on enter.

But I got an error: 'could not find kernel image persistent'.

So I clicked on enter and started up.

After making some changes I rebooted to check if 'persistent' worked.

It did not![/QUOTE]

Are you using the new flight 4 CD?  I just tried it and the Wiki page is wrong; you need to press **F5**.

Mind you, I'm having the same problem as in [http://ubuntuforums.org/showthread.php?t=133040](http://ubuntuforums.org/showthread.php?t=133040) (when using the 'persistent' option)

---

### Post by macroron on 2006-02-20
> **]Originally Posted by macroron
[https://wiki.ubuntu.com/LiveCDPersistence](https://wiki.ubuntu.com/LiveCDPersistence)

I partitioned and formatted a floppy.

I inserted the live cd, the newly partitioned and formatted floppy,
and rebooted then clicked on f4.

I typed 'persistent' and clicked on enter.

But I got an error: 'could not find kernel image persistent'.

So I clicked on enter and started up.

After making some changes I rebooted to check if 'persistent' worked.

It did not!


Posted by Limulus:

Are you using the new flight 4 CD? I just tried it and the Wiki page is wrong said:**
> http://ubuntuforums.org/showthread.php?t=133040[/url]

Hello Limulus,

I'm new to linux and ubuntu. I am on fedora core3. I like unbuntu for it's ease of use and active community. I received the ubuntu Live CD in the mail and I guess it's flight3. I was trying to make the CD useful and found the Wiki Page and assumed by its tone that everything would just work. Since I wanted to use the Live CD to test drive and learn ubuntu until I knew enough to confidently install ubuntu along with fc3 in a dual boot. I was happy to read I could save all my settings. I also wanted to utilize my floppy instead of a usb flash drive. It seems like I managed to partition and format the floppy. I used gparted while on the Live CD to look at it. But my setting are not being saved. On boot maybe the loader only looks for the casper-cow label on the usb ports and ignores the floppy. I decided to learn more about ubuntu and installing it in dual boot mode and wait. The only questions I have and need to learn how to do are:

1. Does 'persistence" work at all? Will it work with a floppy or do I need a flash drive?

2. What is the easiest way to install ubuntu dual boot? Here I need to learn how to repartition and format the harddrive and how to use the ubuntu installer to partition the harddrive the way I want.

I want to be very careful and keep from erasing my fc3 image. I would like to use the Live Cd preferably with persistence until I'm confident enough to switch completely. For me the hardest part is learning how to partition and format the harddrive. Persistence would make learning go much faster. I'm sure my concerns and problems are very common to new users and if overcome would make converting much easier.

-ron-

---

### Post by Limulus on 2006-02-20
Just a quick reply for now as I have to dash; I'll write more later...

[QUOTE=macroron]I received the ubuntu Live CD in the mail and I guess it's flight3.[/QUOTE]

If you mean you got it from Ubuntu (their shipit program), that's not (Its probably Breezy; version 5.10; check what it says on the disk/on the packaging)

What we're talking about is the Dapper (6.04) Flight 3 or 4 (= alpha 3 or alpha 4) as linked from [https://wiki.ubuntu.com/LiveCDPersistence](https://wiki.ubuntu.com/LiveCDPersistence)

---

### Post by Limulus on 2006-02-20
the longer reply I promised:

> I was trying to make the CD useful and found the Wiki Page and assumed by its tone that everything would just work.

Anything in a flight CD is experimental by definition (its alpha software), so no it won't necessarily just work; what will 'just work' is what's on an actual release CD (Warty, Hoary and Breezy so far).

Breezy and prior do *not* have CD Persistence; that's something they're rolling out for Dapper.

> I also wanted to utilize my floppy instead of a usb flash drive.

I think the reason they want you to use a USB thumb drive is that floppies are just too small to store all the required settings, packages, etc....

>1. Does 'persistence" work at all?

While I have not tried very long, its supposed to work fine using a Dapper Flight 3 Live CD but there's some sort of trouble with a Flight 4 one.

> 2. What is the easiest way to install ubuntu dual boot? Here I need to learn how to repartition and format the harddrive and how to use the ubuntu installer to partition the harddrive the way I want.

Partitioning can be scary; I don't recommend trying to do it yourself unless you've tried it out on a test system before or have someone to at least call and walk you though it the first time.  Ubuntu's default option is to erase everything (I don't think you want this ^_-; ). Alternately, you can install to a separate drive (even an external drive; see [http://ubuntuforums.org/showthread.php?t=80811](http://ubuntuforums.org/showthread.php?t=80811))

Maybe find a local LUG ([http://www.linux.org/groups/](http://www.linux.org/groups/)) and get someone there to help? :)

---

### Post by macroron on 2006-02-21
Limulus,

Thanks so much for clearing this up for me.

-ron-

---

### Post by Limulus on 2006-03-17
FYI, there actually wasn't a problem with Flight 4, it was a bad set of instructions on the Wiki!  I've fixed it; have a look: [https://wiki.ubuntu.com/LiveCDPersistence](https://wiki.ubuntu.com/LiveCDPersistence)

---

### Post by macroron on 2006-03-17
> **Limulus]FYI, there actually wasn't a problem with Flight 4, it was a bad set of instructions on the Wiki!  I've fixed it said:**
> https://wiki.ubuntu.com/LiveCDPersistence[/url]
Thanks so much for the clarification.

-ron-

---

