---
title: "All windows are white. Compiz and Nvidia"
date: 2011-01-27
forum: General Help
---

### Post by Artiom.Fiodorov on 2011-01-27
With the latest update all the windows went white with compiz on.
Using 270.18 Nvidia driver.
Switched compiz off (it wasn't easy - because in the settings everything was white), so just right clicked on the desktop and went straight to appearance.
Quite a serious issue.
There's a bug reported, (I found on it google) but only 3-5  people responded to it.

---

### Post by gordintoronto on 2011-01-27
Interesting. Additional Drivers tells me I have the current driver, and it's 260. What video adapter? What kernel?

---

### Post by Artiom.Fiodorov on 2011-01-27
Linux tom 2.6.35-25-generic #44-Ubuntu SMP Fri Jan 21 17:40:44 UTC 2011 x86_64 GNU/Linux

Nvidia driver: 270.18-0ubuntu1~maverick~xup1 (nvidia-glx-185) (proprietary)

---

### Post by vanisher on 2011-03-08
I have the same issue:

Linux orion 2.6.32-29-generic #58-Ubuntu SMP Fri Feb 11 20:52:10 UTC 2011 x86_64 GNU/Linux

Nvidia driver: 270.29

---

### Post by Canada Lee on 2011-05-29
I have the same issue, and have had it for a while...since the day 10.04 Lucid was released.  What I have noticed is, the amount of windows you have open makes it worse, and the size of the windows.  If a window opens up white...resize it smaller and then it becomes visible.    I also searched a long time ago, and read something about having two displays running causes this problem.  I have turned off or disconnected my second display and after time I will still get white windows.  Also I noticed, when using the desktop zoom...when it is working, i wont get white windows...but when i do get white windows the desktop zoom does not work.  It will not zoom,, but when windows are popping up the mouse pointer will coast to the center of that window that popped up...usually this coasting affect happens when the zoom is on...so it thinks it is on, or maybe the zoom is actually on, but visually it is not zoomed in.  I also run Ubuntu 10.04 LTS 64-bit with latest nvidia drivers.

---

### Post by wildmanne39 on 2011-05-29
> **Artiom.Fiodorov said:**
> With the latest update all the windows went white with compiz on.
Using 270.18 Nvidia driver.
Switched compiz off (it wasn't easy - because in the settings everything was white), so just right clicked on the desktop and went straight to appearance.
Quite a serious issue.
There's a bug reported, (I found on it google) but only 3-5  people responded to it.
Hi, I had to change my driver from the current one to the older one and I have not had a problem in a month.

---

### Post by DrQbird on 2011-06-08
I had the same issue.  Selecting "Ubuntu classic" from the sessions menu in the login screen solved the problem without having to rollback the nvidia driver.

---

### Post by amishphysicist on 2011-06-21
Same here.  Went with classic mode with no effects before things stopped being wonky.

---

### Post by watcheroftheskies on 2011-12-12
Hi,

I had the same problem trying Kubuntu. Windows all white when maximized, normal when reduced in window size.

My system reads: "GeForce 6150 LE/PCI/SSE2/3DNOW!" for graphics. I currently am running Ubuntu Oneric, Gnome shell with proprietatry driver (current) for Nvidia enabled. No problems now.

I had the same problem sometimes in Mint 11 (Natty), but switching from compiz to matacity solved the problem

I would like to try KDE (Kubuntu) for a while though. So, does anybody know how to tweak kubuntu - kde - compiz to eliminate this bug? :confused:

regards

---

