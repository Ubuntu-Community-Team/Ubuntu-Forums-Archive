---
title: "Disc Image (Backup) Linux Mint"
date: 2010-07-20
forum: General Help
---

### Post by minty fresh taste on 2010-07-20
I use windows 7 as my secondary computer and it has a stellar built-in
Disc imaging utility (full system backup)
What is the best way to image my Mint box
(in case of catastrophic failure)
And is it even necessary?

---

### Post by CharlesA on 2010-07-20
I use Clonezilla for imaging drives, but I've heard you can use other software as well.

---

### Post by mike555 on 2010-07-20
You might want to try "http://redobackup.org/" it will let you make a bootable image file and it looks good .... I think it will clone a disc with Windows & linux on it or just a partition .

---

### Post by minty fresh taste on 2010-07-20
how about remastersys?
anyone know of this?
Thanks

minty  :KS

---

### Post by giddyup306 on 2010-07-20
> **minty fresh taste said:**
> how about remastersys?
anyone know of this?
Thanks

minty  :KS


I've tried it twice with bad results.  When I tried to do a complete backup of my system it said that the file was too big to meet ISO standard yada yada yada.  So that didn't work.  I then tried to make a distro copy.  I don't remember what the exact problem was, but I did some searching on here and finally decided to ask about it.  I don't think I got any replies, so I went to the remastersys site.  The guy won't help with distro copies unless you give him $50.  I'll have to try it again.  Third time's a charm...

---

### Post by Irony on 2010-07-20
The simplest way is to issue;

```
sudo cp -ax /. /media/ext4/20072010/.
```

This is what I do each week. It means copy the root install into a folder called 20072010.

Thus I have an external usb drive which has a partition formatted as ext4 and I first create a folder called 20072010 (today's date) and then I issue the above command. This is done whilst booted into the install.

If my install messes up then I simply use a live cd and format my messed up partition and then copy the contents of 20072010 back and all is corrected.

---

