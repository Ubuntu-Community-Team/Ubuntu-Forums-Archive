---
title: "Low Graphics mode 10.04 intel 845"
date: 2010-07-30
forum: General Help
---

### Post by hornetster on 2010-07-30
There is already a thread similar to this, I believe, but not up to reading *many* pages, and I think that is mainly nVidia....
Have a reasonably old HP D510 running onboard Intel 845G graphics, which has worked fine to date using Suse 10/11.x x86 and also have tried various Ubuntu breeds on it before, as well.
Have just installed Kubuntu 10.04, and am having issues that irregularly, and apparently randomly, screen goes black and I get a message saying "Ubuntu is running in low-graphics mode". I OK this and get a messages asking me what I would like to do:
1 Run in low graphic for this session
2 Reconfigure graphic
3 Troubleshoot
4 Exit to console
5 Restart x
Basically, none of these work....
If I click 2, there are a number of choices which don't work, can only cancel....
Basically the only fix is a reboot, and it will again work for a 'random period of time'.
Have never had this issue previously, so it is obviously something that has been introduced with 10.04??
Briefly installed Ubuntu 10.04 prior to Kubuntu, and think I had the same prob.
Any solutions?
Thanks, John.

---

### Post by clhsharky on 2010-07-31
hornetster

There should be a ( nomodeset )option that works with older Intel chips.
Try ( e ) at grub to get edit.

Sharky

---

### Post by hornetster on 2010-07-31
> **clhsharky said:**
> hornetster

There should be a ( nomodeset )option that works with older Intel chips.
Try ( e ) at grub to get edit.

Sharky

Isn't that just an option for when the system won't start...? My system runs normally for a while (15mins++) before I get the message and the black screen.
John.

---

### Post by polomint77 on 2010-07-31
Try this post.. I have the 855GM which has the same problems that you have, so I followed the instructions _[here]("http://ubuntuforums.org/showpost.php?p=9600375&postcount=5")_ and it's been working great so far.. I've even got wobbly windows, lmao....
Because you have 10.04 installed already, you can ignore steps 1-3.

Oh, there is only one problem that crops up on mine for some strange reason.  If I run any Windows programs under Wine, and even if I run WindowsXP in a VirtualBox session then it seems to kill Compiz after about 20 minutes. Could be coincidence though.

Hope that helps...

John Young

---

