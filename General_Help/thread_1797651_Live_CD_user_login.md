---
title: "Live CD user login"
date: 2011-07-05
forum: General Help
---

### Post by aussie.ian on 2011-07-05
I am currently using linux mint 10 on my main machine and wanted to try out ubuntu maverik to see what if any differences there are.
Ok, I had a copy of the live CD (from Linux Magazine 12-2010) booted it and was faced with a user login screen. I tried the usual, user - user, root - root even tried ubuntu - ubuntu none of which worked. Why would there be a user login on a live cd and does anyone know what the user name and password would be.


The description in the magazine suggested the live cd was a good way for those new to linux to try it before installing.. Great idea except; many who are not used to linux would simply give up when faced with the issue I have just found, I think this is something that needs to be sorted out. I've used many live cd's over the years and this is the 1st I have found where user or root don't log you in..

---

### Post by dcstar on 2011-07-05
> **aussie.ian said:**
> I am currently using linux mint 10 on my main machine and wanted to try out ubuntu maverik to see what if any differences there are.
Ok, I had a copy of the live CD (from Linux Magazine 12-2010) booted it and was faced with a user login screen. I tried the usual, user - user, root - root even tried ubuntu - ubuntu none of which worked. Why would there be a user login on a live cd and does anyone know what the user name and password would be.
.........

The Live CD should not require a login - but since it does the user "ubuntu" password "ubuntu" should work.

I have found that existing Linux installations can confuse the Ubuntu Live CDs/USBs, they seem to link in the existing file systems and use them instead of the Live system resources.

Possibly this is the problem in your case, and the default Ubuntu credentials are been overridden by something it is incorrectly using on your hard disk.

---

### Post by aussie.ian on 2011-08-03
> **dcstar said:**
> The Live CD should not require a login - but since it does the user "ubuntu" password "ubuntu" should work.

I have found that existing Linux installations can confuse the Ubuntu Live CDs/USBs, they seem to link in the existing file systems and use them instead of the Live system resources.

Possibly this is the problem in your case, and the default Ubuntu credentials are been overridden by something it is incorrectly using on your hard disk.
I did eventually sort this out.. It seems by rebooting out of an existing install of LinuxMint for some reason caused the live CD to ask for the user name and password associated with mint. By simply shutting my computer down and booting from the CD, everything worked as it should.

---

