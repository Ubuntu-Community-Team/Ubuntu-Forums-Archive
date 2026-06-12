---
title: "virtualbox on Lucid Lynx (64 bit)"
date: 2010-10-01
forum: General Help
---

### Post by rwigle on 2010-10-01
I am puzzled that no one else has seen this issue.

I installed virtualbox from Ubuntu Software Center and started it (Applications=>Accessories=>virtualbox OSE.

I tried to add a new machine, but no matter what I have tried, it failed saying it couldn't write to the .Virtualbox folder.

The solution (which doesn't really seem ideal to me) was as follows:

```
sudo -s
root@Mary-Garth:~/.VirtualBox# virtualbox 

```

It creates all the files in /root/.Virtualbox, and everything is running fine, but I am sort of nervous doing it this way.

Question: Is there a better way to get this working, or is this what I am supposed to do?

---

### Post by cek on 2010-10-01
Sometimes that happens if you accidentally run a command under sudo.  Root takes ownership of the directories and this can cause permission issues.

If the .VirtualBox folder is truly in your home folder, then you should be the owner of it.

You can try to type this in a terminal, then try running VirtualBox:

cd ~
sudo chown -R <username> ./.VirtualBox

Note, this this will change the .VirtualBox folder in your home folder, not the /root/.VirtualBox, so any settings that you had made in /root/.VirtualBox will only be there.  You could attempt to copy the /root/.VirtualBox to your home folder first, then do the chown command, but I don't know what the effects of that would be...

---

### Post by gapjunk on 2010-10-01
I've been running VirtualBox without having your issue.  It sounds to me like a permissions problem like rwigle suggested.  I'd try deleting .virtualbox and restart.  

I run VirtualBox as root so I can install port forwarding on lower ports.  I also run it in my account.  It keeps the machines segregated.

---

### Post by rwigle on 2010-10-04
Thanks All:

It seems that file ownership was part of the problem, but it also seems that the solution is a bit more complicated.

1. I copied the .VirtualBox folder to my home folder and changed the ownership
```

chown -R myuser:myuser ~/.VirtualBox

```
2. I then edited the VirtualBox.xml file to point to "Guestadditions---.iso" (I assumed that meant in .VirtualBox in my home folder). I edited the paths to the virtualmachines in the appropriate folder (not in /root).

3. But I still got.. that the GuestAdditions---.iso was unavailable. 

I edited the Image uuid tag in VirtualBox.xml to point to the fully qualified file name for the Guest Additions iso file. (The file was in .VirtualBox, but virtualBox was looking for it in .VirtualBox/HardDisks.)

Now my virtual XP is running.....

---

