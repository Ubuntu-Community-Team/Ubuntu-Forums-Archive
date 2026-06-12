---
title: "Very angry at the upgrade. Guest Addons"
date: 2010-10-11
forum: General Help
---

### Post by Adrienk on 2010-10-11
I am running virtual Box 3.2.8 in Windows 7. I upgraded Ubuntu 10.4 to 10.10 via the update manager after making a edit to a file to get it to see the new distro update.

Long story short, I restarted and Ubuntu was like "your theme is broken" and "your dock has a black rectangle around it, please enable compiz to get rid of the box" so I did, or tried to under appearance and  it was like "no you cannot do this" so I thought well I will just re-install guest add on(s) and so admits the uninstalling I got what I call Ubuntu(s) screen of death - purple with white and asci characters every where and it glitches and twitches... - So I thought ok, restart, take a breath and try again....half way through the uninstall SAME THING....

I NEED COMPIZ! mostly for my theme, BUT for general use as well....so what? Ubuntu updates and I have to wait for virtual box to keep up?

tips? suggestions? ideas?

---

### Post by Adrienk on 2010-10-11
Bump - can I get some answers please?

---

### Post by sendblink23 on 2010-10-11
Its a Virtual Image don't worry... just make another new virtual image

Just download the new one 10.10 iso appart & install it
Then after already running Ubuntu 10.10 then inside do this: 
go to Applications > Acessories > Terminal:

```

sudo apt-get install virtualbox-ose-guest-x11
```

---

### Post by Adrienk on 2010-10-11
Um I should not have to do that, plus I use this "vm image" as my "main" (yes I know that sounds silly, but  this way if I need something done in windows, i can minamize the vm do what i need and then go back into ubuntu like nothing ever happened with out restarting.

is there no way to fix this with out re-installing?

---

### Post by sendblink23 on 2010-10-11
> **Adrienk said:**
> Um I should not have to do that, plus I use this "vm image" as my "main" (yes I know that sounds silly, but  this way if I need something done in windows, i can minamize the vm do what i need and then go back into ubuntu like nothing ever happened with out restarting.

is there no way to fix this with out re-installing?

Random can you try that command in Terminal? Or boot into safemode through the grub menu with low graphics and try that command I posted...  maybe that will replace your old guest additions with the newer one

---

