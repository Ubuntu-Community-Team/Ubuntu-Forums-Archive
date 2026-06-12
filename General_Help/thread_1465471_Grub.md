---
title: "Grub"
date: 2010-04-29
forum: General Help
---

### Post by Tkdboy on 2010-04-29
Hi...

I want to edit the GRUB menu in ubuntu but Menu.1st is missing.
When I open the /boot/grub.cfg from terminal I cant save it.

Any suggestions??

---

### Post by cariboo on 2010-04-29
Moved from FF&H.

Grub-legacy is no longer used, so there is no /boot/grub/menu.lst.  

I was going to give you a link to the **Ubuntu grub2 wiki**, but they seem to be down due to updating to the new look. Once the wiki comes back up again do a search fro the term I bolded.

---

### Post by Tkdboy on 2010-04-29
what I have to do now??
any solution?

---

### Post by ezsit on 2010-04-29
Read through this post on a very detailed explanation of how grub2 works and is configured:

[http://ubuntuforums.org/showthread.php?t=1195275&highlight=grub2+basics](http://ubuntuforums.org/showthread.php?t=1195275&highlight=grub2+basics)

---

### Post by vamc on 2010-04-29
Actually quite simple solution. Change the permissions of the file. Right click > Permissions. There give the privilege to "Read and Write" to the root. This should help.

EDIT:

Open grub.cfg as root.

---

### Post by Tkdboy on 2010-04-29
Grub.cfg cannot be edit. (i cant change the premissions)

I have seen that menu.1st is the same as /etc/default/grub.
If you change etc/default/grub. the Grub.cfg is updated automatic.

So if I want to delete the old kernels from the bootloader this is a good method?

System -> Administration -> Synaptic Package Manager 
Paste "linux-image-" (without quotes) into the search box of Synaptic Package Manager. The results should show every available and installed kernel. A green box on the left indicates that the package is installed.
Once you have located an old kernel, right-click on it and select "Mark For Complete Removal". Repeat for every kernel that you want to remove (make sure to leave the current kernel!!!) and click the Apply.

---

### Post by faqwad on 2010-04-30
[QUOTE=Tkdboy;9195542]Grub.cfg cannot be edit. (i cant change the premissions)

Don't edit grub.cfg. Go to /etc/grub.d and edit 40_custom. Then run update-grub (from terminal) and you'll see your edits appear in grub.cfg. 

If you want to not include the results of any of the other /etc/grub.d entries you can copy the bits you want to 40_custom and then set the generating file to not execute next time you run update-grub.

Make sense?

---

### Post by Tkdboy on 2010-05-18
Yeap, thats the best way.
Edit grub.d
and then update-grub.
grub.cfg automatically updated!!

---

