---
title: "Re-Installing Ubuntu"
date: 2006-04-13
forum: General Help
---

### Post by thelagoons on 2006-04-13
I installed Ubuntu-server and encountered problems like xserver is not installed, and the ubuntu desktop is not showing up, and other error 104 message. It seems that its a lot  mess which IS IMPOSIBLE for mefigure it out. May re installing UBUNTU in a regular way would be an option. My question is How do I remove the previous installation and install it again? Anybody could help?

---

### Post by aysiu on 2006-04-13
I don't know what a 104 message is, but if you do a server install, there will, in fact, be no x server.

You can fix this by typing ```
sudo apt-get update
sudo apt-get install ubuntu-desktop
sudo /etc/init.d/gdm start
```

If that doesn't work, you can just reinstall. The default options overwrite your existing install--you don't have to erase it first.

---

### Post by thelagoons on 2006-04-13
when I inserted the install CD, it guide me thru partioning process, and one of the problem I encountered  is a message that says: there was no root file system created or mounted. How will I do that? thanks for your help

---

### Post by aysiu on 2006-04-13
When you get to this part, just select **Erase entire disk**

---

### Post by thelagoons on 2006-04-13
If I choose that, would it wipe out my MS windows OS or just the linux? I still need my MS windows part so please advise

---

### Post by aysiu on 2006-04-13
[QUOTE=thelagoons]If I choose that, would it wipe out my MS windows OS or just the linux? I still need my MS windows part so please advise[/QUOTE] I didn't know you had a Windows partition.

Make sure you select your Linux partition (probably Ext3) and choose the mount point to be **/**

If there's no mount point that's

**/**

then the installation can't proceed.

---

### Post by thelagoons on 2006-04-13
Did you mean that I have to turn the bootable flag to off, is that correct?

---

### Post by aysiu on 2006-04-13
[QUOTE=thelagoons]Did you mean that I have to turn the bootable flag to off, is that correct?[/QUOTE] No. I'm talking about the slash next to **Mount point**.

This:

/

---

