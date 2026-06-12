---
title: "Ubuntu 10.04 launches a few times but then fails PLEASE HELP"
date: 2010-07-14
forum: General Help
---

### Post by Hand_Of_Reform on 2010-07-14
Hey, I have now installed Ubuntu 10.04 twice as a dual boot with Windows 7, on a separate partition of the Windows Hard drive, I have 3 other hard drives but Ubuntu is installed on a 80Gb partition of a 300Gb WD Veloci-Raptor. So after my machine installs it inside Windows I restart it and it posts and comes up with the dual boot OS selection screen. For the first few times this works; I just choose Ubuntu then choose Ubuntu 10.04 default from the sub menu, however now it tries loading and I just get the flashing cursor followed by an error message that xxx/xxx/xxx is missing and the loading timed out. It's accompanied by something like DOS with command prompt styled commands, but no matter how many times I try it will not boot. This happened last night as well but I fixed it by reinstalling. The file missing last night was something like /dev/sda3 or something, however it is different today...I'm not sure what to do at this point as I really don't want to have to repeatedly reinstall.

---

### Post by HenneBaby02 on 2010-07-14
hmm i'm not sure what the problem is, more or likely ur gonna have to re-install anyway by the sound of it.. I also split my partition a while ago to dual-boot... but you know its easier to just install ubuntu inside windows using Wubi (Which is located inside of the Ubuntu xx.xx.ISO



Did you install it on a Ext. Hard drive by the way ?

I'm still new to linux but i figured least i can do is post a somewhat slightly helpful post :)

---

### Post by Hand_Of_Reform on 2010-07-14
> **HenneBaby02 said:**
> hmm i'm not sure what the problem is, more or likely ur gonna have to re-install anyway by the sound of it.. I also split my partition a while ago to dual-boot... but you know its easier to just install ubuntu inside windows using Wubi (Which is located inside of the Ubuntu xx.xx.ISO



Did you install it on a Ext. Hard drive by the way ?

Nope it's not an external it's just one of my internals, and I've been using Wubi Rev. 189 to install it inside of Windows. I just used Windows Disc Manager to shrink my Windows partition, format it and then install through Wubi.

Also I've read that the sda3 or whatever it is usually deals with USB installations, so I'm not sure how it applies to me or even if it was what the error was. I'm reinstalling right now, hopefully it sticks this time.

---

### Post by HenneBaby02 on 2010-07-14
"The file missing last night was something like /dev/sda3 or something,  however it is different today...I'm not sure what to do at this point as  I really don't want to have to repeatedly reinstall."

I'm not positive but that sounds like your harddrives must of mounted differently after a reboot or something ?

(disregard this post, i didn't notice you replied lol

---

### Post by Hand_Of_Reform on 2010-07-14
> **HenneBaby02 said:**
> "The file missing last night was something like /dev/sda3 or something,  however it is different today...I'm not sure what to do at this point as  I really don't want to have to repeatedly reinstall."

I'm not positive but that sounds like your harddrives must of mounted differently after a reboot or something ?

(disregard this post, i didn't notice you replied lol


Well, you could be right but Windows 7 still boots fine, not sure if that would effect that or not but it could.

---

