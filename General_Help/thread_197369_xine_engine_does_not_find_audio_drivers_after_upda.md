---
title: "xine engine does not find audio drivers after update"
date: 2006-06-15
forum: General Help
---

### Post by chris2000 on 2006-06-15
Hi,
this is my first posting in the forum :-)
after feching the latest (security) updates for Kubuntu 6.06 with adept today i cannot not use the xine engine anymore. amarok as well as kaffeine are affected.

The following packages where updated: 
libkonq4_4%3a3.5.2-0ubuntu27_i386
kwin_4%3a3.5.2-0ubuntu27_i386
ksysguardd_4%3a3.5.2-0ubuntu27_i386
ksysguard_4%3a3.5.2-0ubuntu27_i386
ksplash_4%3a3.5.2-0ubuntu27_i386
ksmserver_4%3a3.5.2-0ubuntu27_i386
konsole_4%3a3.5.2-0ubuntu27_i386
konqueror_4%3a3.5.2-0ubuntu27_i386
konqueror-nsplugins_4%3a3.5.2-0ubuntu27_i386
kmenuedit_4%3a3.5.2-0ubuntu27_i386
klipper_4%3a3.5.2-0ubuntu27_i386
kicker_4%3a3.5.2-0ubuntu27_i386
khelpcenter_4%3a3.5.2-0ubuntu27_i386
kfind_4%3a3.5.2-0ubuntu27_i386
kdm_4%3a3.5.2-0ubuntu27_i386
kdesktop_4%3a3.5.2-0ubuntu27_i386
kdeprint_4%3a3.5.2-0ubuntu27_i386
kdepasswd_4%3a3.5.2-0ubuntu27_i386
kdebase-kio-plugins_4%3a3.5.2-0ubuntu27_i386
kdebase-data_4%3a3.5.2-0ubuntu27_all
kdebase-bin_4%3a3.5.2-0ubuntu27_i386
kcontrol_4%3a3.5.2-0ubuntu27_i386
kate_4%3a3.5.2-0ubuntu27_i386
kappfinder_4%3a3.5.2-0ubuntu27_i386
libgd2-noxpm_2.0.33-2ubuntu5.1_i386

unfortunately, I havent made a backup before hitting the update button, stupid me ;) 

Anybody out there who could help me please?
thanks a lot
Chris

---

### Post by blackjack6.21.91 on 2006-06-15
Open up synaptic and see if those packages are broken.  In the bottom of the left panel, hit custom, and then hit broken.  Select all the broken packages, right click, and click repair.  If no packages show up, then try generating a new sources.list with the link in my signature and see if the update manager has you installing new packages.

best of luck,
blackjack

---

### Post by chris2000 on 2006-06-15
You are great blackjack!

there were no broken packages, but with the new sources list i got amarok 1.4 instead of of 1.39 + updated xine packages. in the update, xine was newly set up and now everything works fine, even with  kaffeine!
thanks a lot
chris

---

