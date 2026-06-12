---
title: "Question about moving my current Ubuntu setup to another computer"
date: 2010-06-06
forum: General Help
---

### Post by VinoFuriaRoja on 2010-06-06
Hey everyone, 

I have a new laptop that came across my way a few days ago and I want to use that laptop now as a dual boot with XP that is on it.  My current laptop is an oldie (HP Compaq nx7400, 60GB HDD, Intel Integrated Video, Intel Duo Core 1.67GHz processor, 2MB RAM) and only has Ubuntu Lucid Lynx on it.  No Windows or anything as I did a clean sweep of it when I installed Lucid on it two weeks ago.  

But I think I will probably need to have some Windows access for school and what not.  

My question is how can I move my current Ubuntu setup over to the new laptop without having to go through installing and customizing everything?  I understand that I can back up applications such as photos, music, etc.  But what about things that Ive installed like WINE, Root, etc, and themes that Ive added and customizations that I have done?  

Any help would be encouraged guys.  Thank you in advance!

---

### Post by VinoFuriaRoja on 2010-06-06
bump...someone please help?

---

### Post by Dennis N on 2010-06-06
You might look into remastersys. Here is a link to a description of what it does, and tutorial of how to use it.

[http://www.dedoimedo.com/computers/remastersys.html](http://www.dedoimedo.com/computers/remastersys.html)

---

### Post by searchfgold6789 on 2010-06-06
If this were a desktop I'd tell you to hook both hard disks to your new laptop and reinstall grub (maybe even get PLOP), and maybe copy both partitions to the hard disk, do a reinstall of grub again, and then unhook the emptied HDD, 


...


BUT ... this is a laptop and I don't do a lot of laptop stuff. So I'll let someone else tell you to do this instead :)

gl. :guitar:

---

### Post by sites on 2010-06-06
If you have an external drive to backup to you can copy your home directory, including hidden files, then copy it to the new computer.

*sudo cp -R .* /home/your-home-folder/* /folder-on-external-drive*

*sudo cp -R .* /folder-on-external-drive/* /home/your-home-folder*

---

### Post by VinoFuriaRoja on 2010-06-07
Thanks guys.  Ill try this out and see if it works.

---

### Post by john newbuntu on 2010-06-07
You could actually clone the ubuntu partition using a utility like clonezilla.  The good thing about this is that it automatically rectifies the /etc/fstab and adjusts grub.cfg so that you could just straight boot into your destination computer after the cloning is complete(assuming you were able to boot into the source ubuntu install).  However, to use clonezilla, your destination partition should be at least as big as the source.

If not, you could clone using dd combined with gzip(or bzip2) over netcat if both the computers have a network connection.  Here's an example on how it works:
[http://www.cyberciti.biz/tips/howto-copy-compressed-drive-image-over-network.html](http://www.cyberciti.biz/tips/howto-copy-compressed-drive-image-over-network.html)

---

