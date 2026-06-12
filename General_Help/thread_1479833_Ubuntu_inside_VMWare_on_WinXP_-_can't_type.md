---
title: "Ubuntu inside VMWare on WinXP - can't type"
date: 2010-05-11
forum: General Help
---

### Post by Reedbeta on 2010-05-11
Hello all,

I installed Ubuntu 10.04 inside VMware Player running in a WinXP SP 2 host.  But Ubuntu can't seem to get any keyboard input.  This means I can't even log in, as I can't type the password.  I clicked in the VMware window, and tried pressing Ctrl+G etc, but to no avail.  Anyone else encountered this issue?

---

### Post by dcstar on 2010-05-11
> **Reedbeta said:**
> Hello all,

I installed Ubuntu 10.04 inside VMware Player running in a WinXP SP 2 host.  But Ubuntu can't seem to get any keyboard input.  This means I can't even log in, as I can't type the password.  I clicked in the VMware window, and tried pressing Ctrl+G etc, but to no avail.  Anyone else encountered this issue?

Please go the Virtualization forum as this - along with many other VMware - issues has already been answered.

---

### Post by ivboy on 2010-05-11
I have the same problem ... if you got answer pls post here ... tnx in advance !

---

### Post by ivboy on 2010-05-11
I found a solution ... 

at the boot time 

1) hold down the 'SHIFT' key at bootup
2) select 'recovery mode' 
3) select 'drop to a root shell prompt'
4) run 'dpkg-reconfigure console-setup'
5) answer questions regarding keyboard/format/etc (arrow up/down to select option, TAB moves cursor to <ok>/<select> buttons). I think I selected a 'Generic101' keyboard and just used the default answer for things I didn't know about. 
6) when its done type 'reboot'

---

### Post by Reedbeta on 2010-05-12
I reinstalled Ubuntu without using VMware's "easy install" option, as directed in [this thread](http://communities.vmware.com/thread/267044;jsessionid=AB2D80D98A5AE6F30DFB8E0139B27EAA?tstart=0) on the VMware forums, and that worked for me.

---

### Post by shannon.jacobs on 2010-05-13
I've tried a number of these tricks and workarounds, but little joy so far... I've already lost count of how many upgrades and reinstalls I've been through. I'm not even sure of how many machines I've tried, but at least three and probably more like five. When will the actual problem be properly fixed?

I've been using Ubuntu for 3 or 4 years now. Each major release of Ubuntu is NOT getting better. I've already stopped recommending Ubuntu, and now I'm considering abandoning it completely... I'm just unable to trust it enough. :(

---

### Post by ivboy on 2010-06-04
... there will be always some bug in every operating system. And there will be always debugging... so, for now on this is the cure for this bug .... not just for me but for many people ... 

**at the boot time **

1) hold down the 'SHIFT' key at bootup
2) select 'recovery mode' 
3) select 'drop to a root shell prompt'
4) run 'dpkg-reconfigure console-setup'
5) answer questions regarding keyboard/format/etc (arrow up/down to select option, TAB moves cursor to <ok>/<select> buttons). I think I selected a 'Generic101' keyboard and just used the default answer for things I didn't know about. 
6) when its done type 'reboot'

Did you try this ... and if you did pls replay again ... we can think of som&#1077;thing ;)

---

### Post by moffa on 2010-07-29
> **ivboy said:**
> ... there will be always some bug in every operating system. And there will be always debugging... so, for now on this is the cure for this bug .... not just for me but for many people ... 

**at the boot time **

1) hold down the 'SHIFT' key at bootup
2) select 'recovery mode' 
3) select 'drop to a root shell prompt'
4) run 'dpkg-reconfigure console-setup'
5) answer questions regarding keyboard/format/etc (arrow up/down to select option, TAB moves cursor to <ok>/<select> buttons). I think I selected a 'Generic101' keyboard and just used the default answer for things I didn't know about. 
6) when its done type 'reboot'

Did you try this ... and if you did pls replay again ... we can think of som&#1077;thing ;)

How did you get to select 'drop to a root shell prompt' without using the arrow keys?

---

