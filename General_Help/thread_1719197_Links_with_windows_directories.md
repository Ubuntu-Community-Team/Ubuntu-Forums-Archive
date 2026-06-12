---
title: "Links with windows directories"
date: 2011-04-01
forum: General Help
---

### Post by magodiafano on 2011-04-01
Hi
I have a problem.
I'd like to create some links in ubuntu to some directories which are under the windows partition (such as music, video, images) so that I can find easily some files.
The problem is that everytime I boot ubuntu the links do not work anymore as if the position of the original directories was changed.
What I have to do?
I installed ubuntu and windows vista in two different directories.

---

### Post by strafe_sawdoffe on 2011-04-01
Give this a try:

```
ln -s /media/[Windows Partition]/Users/[your windows name]/directory /home/[linux name]/Desktop
```...assuming you want the links on your desktop, of course. 

I tried this with Mint 9 and Vista, and at first it looked like I had your problem: the links appeared to break after a reboot... BUT... if you simply browse to the Windows partition (as in, double click on it) once, the links instantly work for the rest of the session.

I know it's kind of a workaround, almost like the Windows directory isn't truly mounted until you interact with it in some way. If I find a way to make the links work immediately I'll share with you. If not, it's only a couple extra clicks.

---

### Post by Lateralis on 2011-04-01
The links don't work to begin with probably because the drive isn't mounted automagically at boot.  You can add the respective NTFS/Windows drives at boot by editing /etc/fstab.  However it is not recommended that you mount a Windows sytem partition and edit files contained therein.  The reason is because NTFS support in Linux is backwards engineered (NTFS is a closed source file system, the specifications of which are not in the public domain) and occasionally things break.  I personally have never had any issues, but the risk is always there.  Moreover Windows sometimes gets a bit uppity if it finds its system partition has been fondled without its prior knowledge or consent.  

As such I would recommend having all of your important documents, i.e. those you wish to fiddle with in Windows and Ubuntu in a separate partition, called "Data" for instance which is separate from the Windows system partition.  You should be able to do what you like without too many issues, but of course it is always a very good idea to make repeated backups just in case.  But, you already knew that, right?

---

