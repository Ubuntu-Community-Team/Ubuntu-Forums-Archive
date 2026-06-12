---
title: "Network drive visible in Nautilus, not in &quot;Open File Dialog&quot;"
date: 2010-04-23
forum: General Help
---

### Post by lenn-art on 2010-04-23
I have succesfully attached some networkdrives (Windowsshares actually) to Nautilus. It's possible to access these with Nautilus and the Open File Dialog of Open Office.

However .. The "Save To" in Google Chrome and "Open File" in Notecase are not showing these networkdrives. Is this a different browser? Is there somewhere somehow a setting to see the drives?

---

### Post by StuartN on 2010-04-23
> **lenn-art said:**
> Is there somewhere somehow a setting to see the drives?

The file chooser is specific to each application. You will need to browse through the mount points at /media, /mnt and ~/.gvfs to find your network drives.

Pressing control-H or "view hidden" will reveal .gvfs in your home directory.

---

### Post by lenn-art on 2010-04-23
Hey tnx! I found the drive in the .gvfs folder! 

But i'm still wondering why i can't see the bookmarks in the left toolbar (Places). I can add a new location as bookmark in Notecase, but the new bookmark is not visible. It appears in Nautilus.

---

### Post by artooro on 2010-07-16
You're not the only one. I'm looking for a user friendly solution to this as well for a business deployment. Can't believe every single browser (tried Firefox, Epiphany, and Google Chrome) and they all use the same open/save dialog which does not display the bookmarks I've added in Nautilus for the network shares. This is frustrating!

If anyone finds a solution please post it here.

---

### Post by lenn-art on 2010-09-10
Still wondering if someone knows the solution for this ..

---

### Post by HornedBeast on 2010-12-01
I am still wondering this too. Seems like a HUGE oversight to me. Argue security, or whatever you like... but Nautilus can do it, why can't File Open dialogs from GTK?

---

### Post by ccsrgv on 2011-02-08
I too am experiencing this problem...
No network locations are viewable, much less accessible, via an "Open File" selection or dialog window from within the Chromium or Firefox browsers running on Ubuntu.  What gives???

---

### Post by Morbius1 on 2011-02-08
Right click an open space in the "Open File" section and select "Show hidden files".  Then go to .gvfs and your remote share will be mounted there.

---

### Post by ccsrgv on 2011-02-14
Thank you Morbius1 & StuartN for your guidance.  I finally figured out what you were trying to tell me & I found the mounted resource in the [user home]/.gvs folder after enabling the "Show Hidden Files" option within the "File Open" dialog box.

I hope that this shortcoming will be remedied soon.

---

### Post by scarf on 2011-04-13
i have an sftp mounted and it's not showing up in /mnt, /media, nor ~/.gvfs

---

### Post by kadm on 2011-06-17
I got the same, I can connect to remote locations via nautilus-connect-server and browse them inside Nautilus, but I do not get anything at all inside ~/.gvfs (nor the other two locations). Perhaps I am missing some service that should be installed/running?

---

### Post by Saprissa on 2012-01-15
> **kadm said:**
> I got the same, I can connect to remote locations via nautilus-connect-server and browse them inside Nautilus, but I do not get anything at all inside ~/.gvfs (nor the other two locations). Perhaps I am missing some service that should be installed/running?
If you're having this problem of not seeing your network shares in ~.gvfs, check to be sure you have read/write permission.

For some unknown reason, I did not and I couldn't find the network shares. Changing the permissions fixed everything.

---

### Post by parix on 2012-02-09
I've made a bookmark to the .gvfs folder, and it works, given that you have to first mount the share using the nautilus link (for gscan2pdf,Ub11.10).

But I'm still wondering if is it in any way possible to make visible the bookmark from the Nautilus left column, when opening the "save as" dialogue. If you use shares all the time, I find the current solution is not good enough.

EDIT:** [SOLVED] **
Still a bit of a workaround but,

1) I've found an easy way to make a network share automount in .gvfs, using the graphic tool** GIGOLO**:
[http://ubuntuforums.org/showpost.php?p=9941016&postcount=3](http://ubuntuforums.org/showpost.php?p=9941016&postcount=3)
[http://askubuntu.com/questions/56428/how-to-automount-a-gvfs-file-system-on-logon](http://askubuntu.com/questions/56428/how-to-automount-a-gvfs-file-system-on-logon)

2) To make, that a nautilus bookmark to it, appears into a "Save as..." popup dialogue, I make a **symbolic link** and then a** Nautilus bookmark** of it. That bookmark will be seenfrom the  "Save as..." "Open File", etc popup browsers, eg.:
ls ~/.gvfs/"_scan on w7" ~/_scanLink
Where _scan is an example of a remote shared folder, w7 an example of a name for a remote machine(samba/cifs/dynamicIP) and _scanLink a random name for the local symbolic link , placed in the home directory.

---

### Post by arune on 2012-04-07
I have reported this as a bug as I consider this to be a usability issue with such a common package as chromium-browser.

Please go to [https://bugs.launchpad.net/ubuntu/+source/chromium-browser/+bug/976168](https://bugs.launchpad.net/ubuntu/+source/chromium-browser/+bug/976168) and add yourself as "Affected" at the top, this will help getting this issue fixed faster.

Regards

---

