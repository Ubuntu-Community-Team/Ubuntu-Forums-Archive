---
title: "too may boot entries"
date: 2010-02-03
forum: General Help
---

### Post by ubunterooster on 2010-02-03
My fathers Dual-boot  PC keeps adding more entries (mostly older Ubuntu kernels I think)
This is bugging him as there are a LOT more entries then before and he occasionally tries to boot into vista, and has to go through all the others as vista is on the bottom. There is only one Ubuntu partition but many options for it now.
  How do I remove the older entries?

---

### Post by hawthornso23 on 2010-02-03
> **ubunterooster said:**
> My fathers Dual-boot  PC keeps adding more entries (mostly older Ubuntu kernels I think)
This is bugging him as there are a LOT more entries then before and he occasionally tries to boot into vista, and has to go through all the others as vista is on the bottom. There is only one Ubuntu partition but many options for it now.
  How do I remove the older entries?

Computer Janitor under the System > Administration menu is the tool designed to do this job. It'll remove old kernels quite nicely. However be careful how you use it. Do not just blindly accept its recommendations. Go through and read what it thinks can be removed and if you are unsure if you might want it or not, unclick and keep. 

In particular this tool uses the repositaries to get information about which depends on what in order to know what is safe to remove. It is therefore likely to ask to remove anything not installed via the repositaries as it won't think it is needed. So watch out if you've got proprietary stuff or stuff installed from debs. This isn't a problem as long as you are aware of that and make sure it doesn't remove stuff you want. It has however caused problems for people who clicked yes without reading the list.

---

### Post by lloyd_b on 2010-02-03
> **ubunterooster said:**
> My fathers Dual-boot  PC keeps adding more entries (mostly older Ubuntu kernels I think)
This is bugging him as there are a LOT more entries then before and he occasionally tries to boot into vista, and has to go through all the others as vista is on the bottom. There is only one Ubuntu partition but many options for it now.
  How do I remove the older entries?

You can use Synaptic (it's under "System" in the menu).  Put "linux-image" in the search box, and remove all of the images except for the most recent (hint: if it tells you that it'll be removing "linux-generic" as a consequence, that's probably the most recent).

Ideally, you should be able to use "sudo apt-get autoremove" to get rid of them, but there seems to be a bug where doing this doesn't properly update the grub menu, so I'd recommend against this unless you know how to fix things afterward.

Lloyd B.

---

### Post by hemimaniac on 2010-02-03
what version of ubuntu and what version of grub?

if it is legacy grub one could do 

sudo nano /boot/grub/menu.lst

look for the section

## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=all

and change it to 

# howmany=1

but if it is grub2 i'm not sure where you would edit that

---

### Post by lloyd_b on 2010-02-03
> **hemimaniac said:**
> what version of ubuntu and what version of grub?

if it is legacy grub one could do 

sudo nano /boot/grub/menu.lst

look for the section

## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=all

and change it to 

# howmany=1

but if it is grub2 i'm not sure where you would edit that

The problem with that is that the grub menu is rebuilt whenever a new kernel is installed.  If the kernels were left installed, they'd get added back in on the next kernel update...

The equivalent file for grub2 is "/boot/grub/grub.cfg", but you ideally should never manually edit this, for the reasons stated above.

Lloyd B.

---

### Post by hemimaniac on 2010-02-03
Yes they will be added back, but i have never had more then 1 ( the most recent appear on the boot menu and that was through 2.6.28.11 up to 2.6.28.17

---

### Post by RocketRanger on 2010-02-05
Hi

I'm having the same problem and I have tried removing the kernels I don't want through synaptic which didn't remove their respective grub entries. Computer janitor doesn't give me any options at all.

Any ideas?

---

### Post by oldos2er on 2010-02-05
> **lloyd_b said:**
> The equivalent file for grub2 is "/boot/grub/grub.cfg", but you ideally should never manually edit this, for the reasons stated above.

A better (editable) equivalent would be /etc/default/grub

---

### Post by raven2099 on 2010-02-06
how about removing ubuntu from inside windows vista 64 bit...
i removed it but the option is still on the boot list even though the ubutu folders are gone...
 
i don't really want to go around downloading janitor programs...
and i can't find any boot.ini files to try to manually remove...
and i can't afford to reinstall windows or do a recover as i have somne programs i don't want to have to reinstall

---

### Post by smerral on 2010-02-06
To get rid of an older kernel (using 2.6.31-16-generic as an example) do:

sudo apt-get purge linux-image-2.6.31-16-generic

---

### Post by faical117 on 2010-02-06
1/ sudo apt-get purge linux-image-2.6.31-16-generic

2/ sudo update-grub  :KS

---

### Post by oldos2er on 2010-02-06
> **raven2099 said:**
> how about removing ubuntu from inside windows vista 64 bit...
i removed it but the option is still on the boot list even though the ubutu folders are gone...


You'll need to run whatever Vista's equivalent of **fixmbr** is.

---

### Post by faical117 on 2010-02-06
sudo update-grub

---

### Post by Enigmapond on 2010-02-06
Ubuntu Tweak will also get rid of older kernels and their configurations. It has many other helpful clean-up methods as well.

---

### Post by RocketRanger on 2010-02-11
> **smerral said:**
> To get rid of an older kernel (using 2.6.31-16-generic as an example) do:

sudo apt-get purge linux-image-2.6.31-16-generic

Thx. That did the trick!

---

### Post by Aly007 on 2010-02-11
> **Enigmapond said:**
> Ubuntu Tweak will also get rid of older kernels and their configurations. It has many other helpful clean-up methods as well.
You're right mate, so easy to use Ubuntu Tweak for this :)

---

### Post by ubunterooster on 2010-02-11
+1 thanks smerral

---

