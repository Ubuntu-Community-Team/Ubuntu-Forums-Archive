---
title: "Add a ubuntu server to a Work Group &amp; file sharing"
date: 2009-07-14
forum: General Help
---

### Post by milindras on 2009-07-14
Hi,
I Intalled **Ubuntu Server 8.04 LTS** on a local machine for testing purposes. 
This machine uses as a test web server, already installed & configured virtualmin.
 
I have mounted a 500GB second hard drive to this machine & I like to share that drive with my other XP machines. I have 02 questions:
 
(1) Would like to see the Ubuntu server on the windows network. 
Have a work group for XP Machines. Should I need to add this server to the work group? If so how to do that?
 
(2)How to share that mounted drive (or a directory in the monted drive), So I can map that directory/drive from XP machines to save files there.
 
Thank you very much..

---

### Post by rampageoberon on 2009-07-14
Hi there, you need a package "samba" to enable file sharing with Windows computers.

Please refer to documentation from the below links to help you set it up.
[https://help.ubuntu.com/community/SettingUpSamba](https://help.ubuntu.com/community/SettingUpSamba)
[http://www.howtogeek.com/howto/ubuntu/install-samba-server-on-ubuntu/](http://www.howtogeek.com/howto/ubuntu/install-samba-server-on-ubuntu/)
[http://ubuntuforums.org/showthread.php?t=202605](http://ubuntuforums.org/showthread.php?t=202605)

Hope that gets you going. Feel free to post if you encounter any difficulties.

---

### Post by milindras on 2009-07-14
Thank you. I will try this tomorrow & come back to you.
 
Appreciate the prompt reply...

---

### Post by milindras on 2009-07-16
I sorted the file sharing thing. Instructions were helped on given links.
Thank you again

---

### Post by rampageoberon on 2009-07-16
> **milindras said:**
> I sorted the file sharing thing. Instructions were helped on given links.
Thank you again

Glad to hear you got it configured and working!

---

