---
title: "Mouse cursor movement on dual monitor setup?"
date: 2012-03-06
forum: General Help
---

### Post by dct on 2012-03-06
I just had a dual monitor set up at work.  The primary monitor is directly in front of me and the secondary is to the left.  I am seeing an issue with the Mouse cursor movement. To get my mouse cursor to the  secondary computer, I must move the mouse to the right.  This seems  backwards as to go left, I must go right. I don't want to change  the arrangements of the monitors.

Is there a way where I can keep the arrangement in tact, but move the  mouse cursor left from the primary so it can appear on the secondary?   This is Ubuntu 11.04

**Additional Details:** 2.6.38-13-generic #54-Ubuntu on i686 . 
$ lspci | grep VGA gives
01:00.0 VGA compatible controller: nVidia Corporation G84 [Quadro FX 570] (rev a1)

I am a beginner with the Ubuntu. I would appreciate any early and detailed help!

_***Thanks Much!!***_

---

### Post by Grenage on 2012-03-06
If you're using he proprietary nvidia drivers, you can run nvidia-settings and move them around easily:

```
gksu nvidia-settings
```

If it's not installed, use:

```
sudo apt-get install nvidia-settings
```

If you're *not* using the proprietary driver, the same functionality might be available under the "displays" section of the system config.  If you're using Unity, you can just type "displays" in the search prompt.

---

### Post by Mark Phelps on 2012-03-07
Go into the Display windows from System Settings.  You will see two monitor icons. Drag the left icon to the right.  Save the results.

Your primary monitor will now be on the left.

---

### Post by dct on 2012-03-13
Hi,
Thanks for the replies.

I tried to configure different options from nvidia x server settings but nothing worked for me. System Settings > Displays doesn't show anything for me except 'Unknown'.

Can someone please help me with the exact steps if possible....


Thanks
DCT

---

### Post by Mark Phelps on 2012-03-13
Sorry ... saw the Nvidia info but didn't realize you're running the restricted drivers.  Don't use those; can't help.

---

### Post by Grenage on 2012-03-14
> **dct said:**
> Hi,
Thanks for the replies.

I tried to configure different options from nvidia x server settings but nothing worked for me. System Settings > Displays doesn't show anything for me except 'Unknown'.

Can someone please help me with the exact steps if possible....


Thanks
DCT


We could probably get around the issue of nvidia-settings having issues, but it would be better to investigate that first.  Exactly what information is listed under "X Server Information" and "X Server Display Configuration" when you load nvidia-settings?

Do you have an existing /etc/X11/xorg.conf?  If so, could you post its contents here?

---

