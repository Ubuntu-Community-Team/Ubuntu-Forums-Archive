---
title: "upgrading to ubuntu 10.04 beta from 9.10"
date: 2010-03-23
forum: General Help
---

### Post by Amgad elsaiegh on 2010-03-23
the official ubuntu website says you cna easily test the new ubuntu 10.04 beta by upgrading from 9.10 in the following page 
[http://www.ubuntu.com/testing/lucid/beta1](http://www.ubuntu.com/testing/lucid/beta1)
i applied the instructions many times & tried many ways to get the upgrade message but nothing happens , i`m going insane :(
i wanna see the new version

---

### Post by 666f6f on 2010-03-23
I can't answer to your question, since I haven't upgraded yet.

However, if I were you and *I just wanted to see how the new version looks like*, I would install Ubuntu Lucid in a virtual machine. You can use VirtualBox for that; here's a guide on how to do that: [http://helpdeskgeek.com/linux-tips/how-to-install-ubuntu-in-virtualbox/](http://helpdeskgeek.com/linux-tips/how-to-install-ubuntu-in-virtualbox/)

If you **really** want to upgrade your main system to Lucid you must expect some problems or glitches (like the one you encounter right now..), since this release is a beta and not a final release.

If you want a stable usable system for everyday use, stick with Karmic for the moment.

Cheers

---

### Post by warfacegod on 2010-03-23
The simplest way to try it out is to create a LiveCD/USB and give it a whirl. I don't recommend upgrading to something that is likely to be unstable. In fact, as far as I can tell, the only thing that is stable about Lucid is GRUB 1.98 (GRUB2 is no longer a beta, yeah!). If you really want to install it, you would be wise to give its own partition.

---

### Post by Mark Phelps on 2010-03-23
While it's true that you can easily "upgrade", what you can't do is "downgrade" later.  

So, it's not a good idea to upgrade to Alpha or Beta releases since they are likely to have problems (after all, they're still in testing!) and there is no easy way to go back to a stable install.

If you want to try out 10.04, download and burn a LiveCD and boot from that.  It will be a lot slower, because it's constantly reading from disk, but it will show you the features of 10.04.

---

### Post by Amgad elsaiegh on 2010-03-23
thanks guys for the advice , i`m now convinced that i should not upgrade to a BETA version but i still wanna know why no message appear in the update manager !!!

---

### Post by warfacegod on 2010-03-23
I just tried the update-manager -d thing and it worked fine for me (I didn't install it of course). You got no upgrade button in the top right?

---

### Post by Amgad elsaiegh on 2010-03-23
no warfacegod ,it don`t appear at all here :(

---

### Post by warfacegod on 2010-03-23
Go to: System> Admin.> Software Sources> Updates Tab> at the bottom make sure it says Normal Releases under Upgrade Distribution.

---

