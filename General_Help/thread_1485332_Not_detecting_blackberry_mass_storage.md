---
title: "Not detecting blackberry mass storage"
date: 2010-05-16
forum: General Help
---

### Post by ezm on 2010-05-16
Hi All: I have a blackberry Tour.  I am trying to connect it to my computer via USB so that I can access the memory storage (just like I would a USB stick or something).  But when I plug the device into the computer, nothing happens.  Now I know from looking at the kernel.log file that it has detected the device, but it does not seem to mount it; nor can I figure out how to force it to.  Any suggestions?  By the way, I also have Barry (this blackberry syncing software installed) but I have no desire to sync the device; I simply want to access the device's memory.

---

### Post by Dportner on 2010-07-06
same problem
anything?

---

### Post by Morm on 2010-07-29
Taking a cue from this [post]("http://forums.opensuse.org/english/get-help-here/applications/438003-barry-mount-drive-problems-2.html"), I tried:

sudo mv /etc/udev/rules.d/10-blackberry.rules /etc/udev/rules.d/10-blackberry.rules.backup

I've now mounted my Blackberry and transferred files. One another note - I also removed usbmount (sudo apt-get remove usbmount) as it was preventing me from having write access unless I made myself root.

Hope that helps!

---

### Post by xrecar on 2010-09-02
Worked like a charm! Thank You!

---

### Post by shane2peru on 2010-09-11
> **Morm said:**
> Taking a cue from this [post]("http://forums.opensuse.org/english/get-help-here/applications/438003-barry-mount-drive-problems-2.html"), I tried:

sudo mv /etc/udev/rules.d/10-blackberry.rules /etc/udev/rules.d/10-blackberry.rules.backup

I've now mounted my Blackberry and transferred files. One another note - I also removed usbmount (sudo apt-get remove usbmount) as it was preventing me from having write access unless I made myself root.

Hope that helps!

Moving the rules worked for me!!! Thanks!!!

Shane

---

### Post by shane2peru on 2010-09-11
Ok, I found out that the udev rules won't allow me to connect via USB as mass storage device, so moving them as stated works.  However I was following this guide:  [http://www.chipbennett.net/2008/05/31/synchronizing-a-blackberry-in-linux/](http://www.chipbennett.net/2008/05/31/synchronizing-a-blackberry-in-linux/)  And because I had moved the rules, syncing didn't work!  I got this error:```
Member 1 of type barry-sync had an error while connecting: (-1, error sending control message: Operation not permitted): Probe: GetConfiguration failed
```  So, odd, but seems the rules matter to sync, but are in the way for mass storage device.  Any ideas?

Shane

---

### Post by kelly harlton on 2010-09-13
Thanks for the help. moving rules worked for me! Only caveat is that  now I have to run the barrybackup utility as sudo...no biggie

---

### Post by gargoyle297 on 2010-11-18
Doesn't work for me.
I was able to read-write mass storage and sync via opensync since 4 days ago with Jaunty.
After the upgrade to karmic i cannot read-write the mass storage but I can still sync.
The trick of renaming the file doesn't work for me...
What's the difference between Karmic & Jaunty?

Norberto

---

### Post by excetara2 on 2010-12-02
I think this issue has to do with bcharge but not sure. So maybe wherever those configuration files are kept.

---

### Post by chitowner2 on 2010-12-07
to all interested, I found relevant info here:

[http://www.mail-archive.com/barry-devel@lists.sourceforge.net/msg02588.html](http://www.mail-archive.com/barry-devel@lists.sourceforge.net/msg02588.html)
[http://www.mail-archive.com/barry-devel@lists.sourceforge.net/msg02949.html](http://www.mail-archive.com/barry-devel@lists.sourceforge.net/msg02949.html)

[https://bugs.launchpad.net/ubuntu/+source/barry/+bug/617721](https://bugs.launchpad.net/ubuntu/+source/barry/+bug/617721)

Hope this helps! Anybody who tries this please post results!

I tried the option shown here:
[http://forums.opensuse.org/english/get-help-here/applications/401468-barry-sync-opensync-barry-0-14-a-2.html](http://forums.opensuse.org/english/get-help-here/applications/401468-barry-sync-opensync-barry-0-14-a-2.html)
Which is basically deactivating all blackberry.rules (and barry-perms if present), then did  a reload rules and its all fine. Mass storage access works and so does barrybackup.

Go figger...

CT

---

### Post by bthomson100 on 2011-05-19
I've been through all the posts about Blackberry and am at my wits end trying to access the minisd card on the Blackberry Curve 8320 that my son gave me. When I first got it, I could see the card as a drive on my Asus EEE 1005 netbook running Ubuntu 10.10 without any problems

Now, after installing Barry 015 and barry-utils (and uninstalling them and reinstalling them, I still can't get it to work. At one point this morning it recognized the card and I was able to back up the card and do a barrybackup at least as far as the MMS Options database when barrybackup crashed. Since then it won't recognize the card, the Blackberry doesn't show up under lsusb. It just asked me if I wanted to enable mass storage and I clicked yes but it still doesn't show up under lsusb!

I've changed the 10-blackberry.rules file to 65-blackberry.rules and several other combinations. I've tried rebooting the computer and also using "udevadm control --reload-rules". I've tried changing the Blackberry media card setting on and off.

I'm a complete newbie but I've figured out it has something to do with the rules files. Just as they did with a problem preventing me from syncing my Clie/Palm with jPilot (a problem I never did solve!)

What do I need to do, step by step by step (I'm a complete) newbie, to get this working.

Bob Thomson, Ottawa, Canada

---

