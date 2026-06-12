---
title: "New /Boot partition and how to edit grub2"
date: 2010-07-21
forum: General Help
---

### Post by VastOne on 2010-07-21
I have an existing Ubuntu build - Maverick which had it's own grub2 (obviously) from the original build.

I created a new partition in further testing of Maverick with btrfs and in building that the new test sandbox, I created a /boot partition to handle grub for all builds current and future.

All this works fine until I want to edit anything grub related in the original build. It still "sees" it's own build of grub instead of the /Boot partition and the actual grub

From within the Maverick original build I do a:

```
grub-probe -t device /boot/grub

```

and it finds the right location on the correct sda7 partition

But if I do 

```
gksudo gedit /etc/default/grub

```

It opens what was the original grub files on this build and not the actual grub files on /Boot

I am thinking it is a sym link of some kind and just need to correct it.

Thanks

Edit - 

Marking this as solved to close my end of it.  I searched through and read at least a thousand How To's and suggestions to come to the conclusion that there is no real value in having a /Boot partition and even in Ubuntu's Grub tutorial suggests the same thing.

I ended up just deleting the /Boot partition and booted back to the original grub from the original install.

At least this way I can edit grub.  

This was all an exercise in understanding the value of a separate /Boot menu and I got my answers.

---

### Post by Mike Krall on 2010-08-02
> **VastOne said:**
> Edit - 

Marking this as solved to close my end of it.  [COLOR="RoyalBlue"]I searched through and read at least a thousand How To's and suggestions to come to the conclusion that there is no real value in having a /Boot partition and even in Ubuntu's Grub tutorial suggests the same thing.[/COLOR]

I ended up just deleting the /Boot partition and booted back to the original grub from the original install.

At least this way I can edit grub.  

This was all an exercise in understanding the value of a separate /Boot menu and I got my answers.

I'm adding 10.04 to a Win7 laptop (ASUS Ul50Ag) I've got one primary and one extended primary available (lots of room in the drive... at least for my use-types). Will not use Win7 at all (will keep updated, etc.)

I know... everybody is different... but in your research, did you find any good reason to have a /boot partition in a multiple OS/dual boot scenario?

Mike

---

### Post by VastOne on 2010-08-02
> **Mike Krall said:**
> I'm adding 10.04 to a Win7 laptop (ASUS Ul50Ag) I've got one primary and one extended primary available (lots of room in the drive... at least for my use-types). Will not use Win7 at all (will keep updated, etc.)

I know... everybody is different... but in your research, did you find any good reason to have a /boot partition in a multiple OS/dual boot scenario?

Mike

That was the entire reason for the research...

I have multiple distros and test environments along with Win 7, I was setting up a new machine and decided to try a /boot drive.

Within in each distro, there was no control back to the grub on the /boot drive, so if you did some kind of update of the kernel or new kernel within one of your environments, it did not updtae grub on /Boot.

What I found was that it worked as a boot environment, but you had very little control over that environment and it was frustrating.

Normal grub from a normal install is perfect for a dual boot scenario and finds all OS's with a sudo update-grub, or when first build Ubuntu it will scan and find your Win 7

---

### Post by Mike Krall on 2010-08-02
Thanks for the loan of your experience... answered questions I was having a hard time wading through.

Mike

---

### Post by VastOne on 2010-08-02
> **Mike Krall said:**
> Thanks for the loan of your experience... answered questions I was having a hard time wading through.

Mike

No worries mate, just as a payback of the loan, pass it along when you can!

---

