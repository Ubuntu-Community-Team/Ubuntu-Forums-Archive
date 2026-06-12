---
title: "Win32 and Ubuntu Linux, how to resize partition"
date: 2009-08-02
forum: General Help
---

### Post by berlinbrown on 2009-08-02
I haven't done this in a while.  And I have three questions.

I have used this Ubuntu Linux machine for a while.  Pure Linux.  I have the latest Ubuntu version.

It is a 120GIG drive, I setup 80gigs for Linux and let the 40 gigs free.  Not touched.

**Win32**

I needed to do some work solely in win32 (terminal services and other work that will only work under windows).  So, I installed windows on the 40gigs that were free.

**Can't boot back into Ubuntu, problem 1**

I installed windows xp and now I can't get back into windows.  I am assuming the install wrote over the MBR and now all I would need to do is get a live CD or something and install grub or something?  I wish I had the exact details.  I want to be able to dual boot, maybe with a prompt allowing me to select win32 or ubuntu.

**How to resize the win32 system, add a new partition, problem 2**

So I have this win32 install which only has a 40gigs.  I ran through that pretty quickly over the last week.  And now I only have 15gigs free.  I need to install more stuff.  So, how would I use some of the space from the Ubuntu linux install. I have 50gigs free on the Linux side.

What steps would I need to resize the linux and give to the win32 side?

---

### Post by hellmet on 2009-08-02
You mean to say you can't get back into Ubuntu? Yeah, you'd have to reinstall grub
Use Gparted to resize disks so you can use it for Windows.

---

