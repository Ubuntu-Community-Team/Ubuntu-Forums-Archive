---
title: "Cannot unistall xdm"
date: 2009-12-14
forum: General Help
---

### Post by Weepleman on 2009-12-14
Hi, I am running gdm, but a while ago, I had installed xdm.  Now, when ever I run update manager, synaptic, apt-get, or add-remove programs, I get an error saying that unistall xdm exited with error status (2).  I have no idea what that means, or how to manually remove xdm.  If anyone knows how that would be very helpful.

---

### Post by MooPi on 2009-12-14
Open a terminal and type this. Or you can copy and paste.

```
sudo apt-get purge xdm
```

---

### Post by Weepleman on 2009-12-14
That did not work, I got this ```
Removing xdm ...
dpkg (subprocess): unable to execute installed pre-removal script: Exec format error
dpkg: error processing xdm (--purge):
 subprocess installed pre-removal script returned error exit status 2
dpkg (subprocess): unable to execute installed post-installation script: Exec format error
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 2
Errors were encountered while processing:
 xdm
E: Sub-process /usr/bin/dpkg returned an error code (1)

```
Which is what I normally get when it tries to remove xdm

---

### Post by Leppie on 2009-12-14
In synaptic try re-installing xdm before removing it.

---

### Post by MooPi on 2009-12-14
Does this in any way degrade your computers performance? The reason I ask is it really that important to remove this on the chance some process is still using xdm. If you force the computer to remove a dependency and everything goes fubar, you may wish you never went down this path. Other than the annoyance of the recurring message does it bother you.

---

### Post by Weepleman on 2009-12-14
It makes it so I cannot automatically run things like update manager or synaptic because I have to watch them, but other than than not really, and I have already tried installing xdm and then uninstalling.

---

### Post by Weepleman on 2009-12-14
The only real problem is hat I cannot run update manager by automatically, because I have to watch it, and when I shutdown or reboot, all I get is a black screen with a mouse on it no matter how long I wait, and I think it may be caused by this.  Also, I have already tried reinstalling and unistalling. Sorry for the double post!

---

### Post by Weepleman on 2009-12-15
When I log out I just see my by background and a cursor just like when I try to shutdown, but I can see my background.  Right now I am just unplugging my computer to turn it off.  Will this hurt it?

---

### Post by Weepleman on 2009-12-16
Okay, I think I have a bigger problem.  I don;t think I can uninstall any program with atp.  I tried to uninstall wicd when I started to act up earlier, and there were the ame problems as with xdm.  For some reason I tried dpkg-reconfigure python2.6 and that got wicd to uninstall.  I then tried to install network manager, and that did not work for some reason, and now I cannot uninstall that.  I get the same errors as with xdm, only now there are three broken packeges, xdm, network-manager, and network-manager-gnome.  The bad part is that I can't use the internet in ubuntu, so I have to use vista.  Is there anyway to fix this?

---

### Post by Chesamo on 2009-12-16
> **Weepleman said:**
> Right now I am just unplugging my computer to turn it off.  Will this hurt it?
Yes.
> **Weepleman said:**
> Okay, I think I have a bigger problem.  I don;t think I can uninstall any program with atp.  I tried to uninstall wicd when I started to act up earlier, and there were the ame problems as with xdm.  For some reason I tried dpkg-reconfigure python2.6 and that got wicd to uninstall.  I then tried to install network manager, and that did not work for some reason, and now I cannot uninstall that.  I get the same errors as with xdm, only now there are three broken packeges, xdm, network-manager, and network-manager-gnome.  The bad part is that I can't use the internet in ubuntu, so I have to use vista.  Is there anyway to fix this?
Sounds like your machine up and died... sounds fubar. Is reinstalling Ubuntu out of the question?

---

### Post by Weepleman on 2009-12-17
No, I was actually thinking about reinstalling, but I have no ide how to do it, and I want to try to keep my programs, but it would not be that bad of a loss if I couldn't.  Is there anyway to keep the installed programs when you reinstall ubuntu?

---

### Post by MooPi on 2009-12-17
Is that no ide drive or no idea on how to do this? If you have a CD-rom drive or dvd drive just use a Live Ubuntu CD. If your installed programs are from the Ubuntu repository, then yes. Those programs are always there.

---

### Post by Weepleman on 2009-12-17
I meant to say idea. Sorry. Okay, I am going to try to reinstall it today, I hope it goes well!

---

### Post by Weepleman on 2009-12-20
Okay, I reinstalled Ubuntu and that fixed the problem thank you all for your help.

---

