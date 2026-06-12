---
title: "grub - error out of partition"
date: 2010-02-17
forum: General Help
---

### Post by bwuk on 2010-02-17
Hi, 

I'm a web developer running Karmic on an MSI laptop, and I started having problems today. Basically, my home directory was being set as read-only for some reason. Anyhow, a quick reboot soon sorted that. 

So, I turned off the laptop as I was going into a meeting, and then came back, turned it on and I'm greeted with the following screen:

```

GRUB loading.
error: out of partition
grub rescue>

```

So, I'm tried 'help', and it's an unknown command. 

I've tried following instructions from: [http://209.85.229.132/search?q=cache:qtNvD7gOqkEJ:osdir.com/ml/ubuntu-users/2009-10/msg01413.html+grub+rescue+commands&cd=2&hl=en&ct=clnk&gl=uk&client=firefox-a](http://209.85.229.132/search?q=cache:qtNvD7gOqkEJ:osdir.com/ml/ubuntu-users/2009-10/msg01413.html+grub+rescue+commands&cd=2&hl=en&ct=clnk&gl=uk&client=firefox-a)

and 'root' isn't a function.

I'm really stumped as to what to do here......can anyone help?

The results of 'ls' are:

```

(hd0) (hd0,5) (hd0,1)

```

Thanks

bwuk

---

### Post by bwuk on 2010-02-17
Extra info - I've downloaded the Karmic live CD (though burnt to a DVD), and that won't boot either. The DVD drive spins, but then doesn't boot. It was burnt using Vista Business Edition.

Is it ok to burn a live CD to DVD?

---

### Post by mk1w86 on 2010-02-17
A CD image should work on a DVD as long as it was burnt correctly.  It might just be a bad disk, have you tried the Live CD on another machine?  Also are you sure that the DVD drive is OK?

If you burn the image again try burning at a slower speed. ;)

---

### Post by bwuk on 2010-02-17
Hi,

Ok, I tried the live CD/DVD on a second laptop running Vista, and it wasn't a valid boot disk, so I burnt it again burning at x1.7. This time it worked on the Vista laptop, and seemed to work on Ubuntu. Unfortunately, I get another error when trying to access any of the options on the live CD. I get an I/O error - saying can't read from disc.

I'm not sure what to do....is this an ubuntu issue? is it a live CD issue caused by the grub MBR?

This is my work laptop and I'm meant to be presenting tomorrow. I don't know if I'll be able to do it. It's nearly 9pm now and I'm starting to panic. I didn't (SVN) commit my changes today - a very bad practice I know, and now I'm thinking I won't be able to retrieve my files.

Ermmm....help??

---

### Post by bwuk on 2010-02-17
Further info - live CD will boot up into Ubuntu on Vista

---

### Post by mk1w86 on 2010-02-17
If you need Vista in emergency take a look at this guide which will reinstall the Windows boot loader:

[http://www.bleepingcomputer.com/tutorials/tutorial148.html](http://www.bleepingcomputer.com/tutorials/tutorial148.html)

If you can boot a Ubuntu Live CD take a look at this guide, particularly the Recover Grub 2 via LiveCD section:

[https://wiki.ubuntu.com/Grub2](https://wiki.ubuntu.com/Grub2)

---

### Post by violens on 2010-03-21
I have the same problem. I restarted my computer and i also was greeted with the screen:

```

GRUB loading.
error: out of partition
grub rescue>

```

I dont know what to do. The live DVD want boot although it is a valid boot disk.
*Can [I]someone please help me*[/I] :(

P.S. Sorry for the bad english...

---

### Post by Stuball on 2010-07-12
I just solved an "out of partition" GRUB problem on my computer.  I have a Dell Dimension 4550 with XP, so about an 8-year-old box.  I tried every kind of installation and could not get past the "Out of partition" GRUB error.  

Turns out, I had to update my BIOS so it could deal with a larger hard disk that I had installed.  Now it works fine.  

Alternately, I've read posts about creating a special /boot partition for the GRUB boot loader - like 1MB near the front of the disc - where an old BIOS image can find it. Here's one article on the subject: [http://www.troubleshooters.com/linux/grub/grubpartition.htm](http://www.troubleshooters.com/linux/grub/grubpartition.htm)

---

