---
title: "Windows Max, Min and close now on top left after 9.10 -&gt;10.04 Upgrade"
date: 2010-05-01
forum: General Help
---

### Post by sandfire on 2010-05-01
Hi After upgrading to 10.04. all my windows controls (Maximise, Minimise and close) have been moved to the top left of the window. 

Is there any way I can configure Ubuntu 10.04 to return the controls to the top right, as they were in 9.10?

Thanks in advance,

Gordon

---

### Post by Dayofswords on 2010-05-01
> **Paul T. said:**
> Hi,

I had same concern about moving buttons, but easily fixed:

Open up a terminal, type "gconf-editor" then navigate to /apps/metacity/general and make the "button_layout"
Code:
:minimize,maximize,close

Got that from another user, worked for me :P

[http://ubuntuforums.org/showthread.php?t=1467936](http://ubuntuforums.org/showthread.php?t=1467936)

---

### Post by colorlessprism on 2010-05-01
system --> appearance --> customize --> icons --> gnome

only way i have figured it out so far

---

### Post by JOHNNYG713 on 2010-05-01
Ubuntu Tweak ! [http://launchpad.net/ubuntu-tweak/0.5.x/0.5.4/+download/ubuntu-tweak_0.5.4-1_all.deb](http://launchpad.net/ubuntu-tweak/0.5.x/0.5.4/+download/ubuntu-tweak_0.5.4-1_all.deb)

---

### Post by sandfire on 2010-05-01
> **sandfire said:**
> Hi After upgrading to 10.04. all my windows controls (Maximise, Minimise and close) have been moved to the top left of the window. 

Is there any way I can configure Ubuntu 10.04 to return the controls to the top right, as they were in 9.10?

Thanks in advance,

Gordon


Brilliant, thank you. It has worked a treat.

Cheers,

Gordon

---

