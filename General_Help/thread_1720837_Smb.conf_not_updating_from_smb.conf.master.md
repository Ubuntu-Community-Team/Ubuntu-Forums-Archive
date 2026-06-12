---
title: "Smb.conf not updating from smb.conf.master"
date: 2011-04-03
forum: General Help
---

### Post by darkeale on 2011-04-03
Hi,

I'm trying to set up samba.  I am editing the smb.conf.master file, and then using the testparm -s "smb.conf.master > smb.conf" command to make the smb.conf file.  I am running this command as root.  However, the smb.conf is not updating with the changes I am making.  Does anyone know why?  It just stays the same no matter what I change.  The only way to change it is to edit the smb.conf file itself.

Alex

---

### Post by darkeale on 2011-04-04
Problem solved.  

I needed to start the terminal session with:-

sudo su

then run the command:-

testparm -s smb.conf.master >smb.conf

Alex

---

