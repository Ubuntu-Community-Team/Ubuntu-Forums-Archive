---
title: "kernel crash on playing video from youtube in chromium"
date: 2012-07-13
forum: General Help
---

### Post by o1e9 on 2012-07-13
Hi,

I have got kernel crash yesterday evening trying to play a video from youtube in chromium.  I did not run anything special that day but few copies of VirtualBox guests, Thunderbird, few terminals and chromium undex XFCE desktop Ubuntu 12.04.  I had had many "frozen desktop" before forcing me to hard reset.  XFCE looks like quite stable compare to Unity or Gnome shell even running the latest 4.10 from PPA.  See the screenshot of kernel message after I had to hard reset.  Nothing appeared in logs or /var/crash.  atop is running every 10 minutes to collect statistics and nothing suspicious but chromium allocated a lot of virtual memory.

I am running on one year old Lenovo T520.  Random freezes and kernel panic something I have seen before however that kernel BUG is something new. See the screenshot for actual message.

Has anyone seen the problem before?

Thanks,
Oleg
P.S. Guess I would have to submit bug report.

---

### Post by Redblade20XX on 2012-07-13
> **o1e9 said:**
> Hi,

I have got kernel crash yesterday evening trying to play a video from youtube in chromium.  I did not run anything special that day but few copies of VirtualBox guests, Thunderbird, few terminals and chromium undex XFCE desktop Ubuntu 12.04.  I had had many "frozen desktop" before forcing me to hard reset.  XFCE looks like quite stable compare to Unity or Gnome shell even running the latest 4.10 from PPA.  See the screenshot of kernel message after I had to hard reset.  Nothing appeared in logs or /var/crash.  atop is running every 10 minutes to collect statistics and nothing suspicious but chromium allocated a lot of virtual memory.

I am running on one year old Lenovo T520.  Random freezes and kernel panic something I have seen before however that kernel BUG is something new. See the screenshot for actual message.

Has anyone seen the problem before?

Thanks,
Oleg
P.S. Guess I would have to submit bug report.

Can you reproduce this kernel panic?

 It seems as if there was a bad pointer reference that accessed memory from the chromium process, therefore "tainted" it, and caused it to be killed. Since it caused the kernel to crash, nothing was logged into the logs.

It might be linked to the ppa version your using. Is the software you installed through the ppa stable or experimental?

- Red

---

### Post by o1e9 on 2012-07-13
> **Redblade20XX said:**
> Can you reproduce this kernel panic?

 It seems as if there was a bad pointer reference that accessed memory from the chromium process, therefore "tainted" it, and caused it to be killed. Since it caused the kernel to crash, nothing was logged into the logs.

It might be linked to the ppa version your using. Is the software you installed through the ppa stable or experimental?

- Red

I am not able to reproduce the problem because it happens eventually, so I do not have any control over it.

I am using 12.04 release with precise-proposed is off.  XFCE is isntalled as a package in Ubuntu and then upgraded to 4.10 version via ppa.  I do not think it is XFCE related because I have had kernel panic using unity 3D/2D and gnome shell.

---

### Post by Redblade20XX on 2012-07-13
> **o1e9 said:**
> I am not able to reproduce the problem because it happens eventually, so I do not have any control over it.

I am using 12.04 release with precise-proposed is off.  XFCE is isntalled as a package in Ubuntu and then upgraded to 4.10 version via ppa.  I do not think it is XFCE related because I have had kernel panic using unity 3D/2D and gnome shell.

Well if it's not reoccuring (panic is exactly like the one in your attachment) then you shouldn't worry about this one. Do you get kernel panics, in general, often?

- Red

---

### Post by o1e9 on 2012-07-13
> **Redblade20XX said:**
> Well if it's not reoccuring (panic is exactly like the one in your attachment) then you shouldn't worry about this one. Do you get kernel panics, in general, often?

- Red

Unfortunately it is quite often, lets say 1-3 times per month.  I am not always able to make a screenshot using my phone, so the latest from March using 11.10 release is attached.

I am having other strange "freezing" problem then suddenly the screen freeze so no way to switch other console or use magic sysrq.  That way the cold reset is the only option and waiting until fsck is done on startup.  It may be exactly the same problem but it fails to switch into system console to show me kernel panic error message rather the screen is "frozen" on the latest picture from frame buffer.  That kind of problems happen 1-3 per week!  Sometimes I am the lucky one to survive a week with no crashes however if I use Unity 3D with compiz then it increases chances to receive at least one crash (frozen screen) per day.  That is why I have switched to XFCE and by the way do not regret that because it is very nice desktop environment indeed.

Gnome Shell looks like having some issues as well.  I have been using it on 11.10 release however on 12.04 it is crashing for me too often, I am not able to use desktop for more then 5 hours and do not receive gnome-shell crash with abandoned windows, so close everything I can and reboot.  Just restaring gnome-shell does not help because it would switch to fallback gnome mode instead.

It looks like the problem leads to GPU usage however Chromium flags are explicit: no GPU features are enabled on my desktop.  I am not sure if Google V8 uses GPU to JIT JavaScript by default.

If I am using VirtualBox to run guests then it would increase chances the system crash (freeze) however "when" I am not able to predict.  I am not using 3D Accel options for guests in VB, so it shall not be an issue, I think.

---

### Post by Redblade20XX on 2012-07-13
> **o1e9 said:**
> Unfortunately it is quite often, lets say 1-3 times per month.  I am not always able to make a screenshot using my phone, so the latest from March using 11.10 release is attached.

I am having other strange "freezing" problem then suddenly the screen freeze so no way to switch other console or use magic sysrq.  That way the cold reset is the only option and waiting until fsck is done on startup.  It may be exactly the same problem but it fails to switch into system console to show me kernel panic error message rather the screen is "frozen" on the latest picture from frame buffer.  That kind of problems happen 1-3 per week!  Sometimes I am the lucky one to survive a week with no crashes however if I use Unity 3D with compiz then it increases chances to receive at least one crash (frozen screen) per day.  That is why I have switched to XFCE and by the way do not regret that because it is very nice desktop environment indeed.

Gnome Shell looks like having some issues as well.  I have been using it on 11.10 release however on 12.04 it is crashing for me too often, I am not able to use desktop for more then 5 hours and do not receive gnome-shell crash with abandoned windows, so close everything I can and reboot.  Just restaring gnome-shell does not help because it would switch to fallback gnome mode instead.

It looks like the problem leads to GPU usage however Chromium flags are explicit: no GPU features are enabled on my desktop.  I am not sure if Google V8 uses GPU to JIT JavaScript by default.

If I am using VirtualBox to run guests then it would increase chances the system crash (freeze) however "when" I am not able to predict.  I am not using 3D Accel options for guests in VB, so it shall not be an issue, I think.

If you aren't running any experimental software, maybe it is a good time to run a memory check to see if your memory has any bad blocks. Also take a look at your S.M.A.R.T harddrive information to see if anything is happening.

From my experience, kernel panics without "cutting edge" software tends to be hardware related and since you've isolate gpu then it maybe something else.

- Red

---

### Post by matt_symes on 2012-07-13
Hi

When the kernel crashes are you running virtualbox at that point in time ? i.e when the kernel crashes, is virtualbox running ?

Was chromium running in a Vbox guest ?

Kind regards

---

### Post by o1e9 on 2012-08-04
> **matt_symes said:**
> Hi

When the kernel crashes are you running virtualbox at that point in time ? i.e when the kernel crashes, is virtualbox running ?

Was chromium running in a Vbox guest ?

Kind regards

I may be running VirtualBox or not, it depends.  Nonetheless running Chromium in host with flash playing music or videa and at the same time VirtualBox quest then may crash system with a good probability.

Anyway it looks the problem is in the past after I had installed the latest firmware from Lenovo.  It looks like they release updates almost every month and changelog shows they really fix a lot of issues.  Therefore anyone has T520 or the like follow firmware releases or install the latest update (1.37 or later) to fix strange system freeze problems and unexpected kernel panic.

I have been running 1.37 update for 3 weeks and no problems whatsoever.

---

