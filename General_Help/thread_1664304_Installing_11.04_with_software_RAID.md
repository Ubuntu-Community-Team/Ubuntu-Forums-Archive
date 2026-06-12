---
title: "Installing 11.04 with software RAID"
date: 2011-01-10
forum: General Help
---

### Post by sshannin on 2011-01-10
Hey,

I'm trying to install 11.04 and setup software raid on two hdd's in the process for the home partition.  Even in the manual setup I don't really see any option to do this.

Any suggestions?

Thanks.

---

### Post by psusi on 2011-01-10
First, 11.04 has not been released and is still in early development.  Either you should be using 10.10, or you should be posting in the development forums.

Second, you need to use the alternate installer for software raid.

---

### Post by wcorey on 2011-04-30
> **psusi said:**
> First, 11.04 has not been released and is still in early development.  Either you should be using 10.10, or you should be posting in the development forums.

Second, you need to use the alternate installer for software raid.

Hi, pardon the intrusion. Which alternate installer would that be? Years back, in order to do firmware raid, perhaps any raid, you needed the alternate install cd. Fedora never had that issue. But I believe it was in the 9.04, or maybe 9.10, timeframe the standard installer knew how to install on a system with firmware raid active. Why I bring this up is that it appears that ability is completely broken in 11.04 (GA version). The install runs fine but, upon reboot, nothing happens, just a blank screen with a fast blinking cursor. I originally thought this was related to a known bug of installing fine but not booting into grub if one installed encrypted LVM, which I think turned into any LVM. I removed, or at least thought I removed, my LVM and U11.04 would not boot at all, no errors, no warnings, just not boot. I now believe it has to do with firmware raid. 

So I thought I'd ping you on that topic. BTW, 10.10 installed just fine with firmware RAID.

Walt

---

### Post by psusi on 2011-05-02
The alternate installer is the one on the -alternate iso image, as opposed to the -desktop one, as well as the text mode installer option on the dvd image.  The desktop installer should work with fakeraid, and you can get it to work with software raid if you know how to install the packages and configure it yourself in the terminal, but the preferred method for installing to software raid is to use the text mode installer.

---

