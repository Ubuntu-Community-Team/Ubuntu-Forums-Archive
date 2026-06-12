---
title: "Kernel selection at startup"
date: 2010-10-14
forum: General Help
---

### Post by dreamquartz on 2010-10-14
Before I had to re-install, because I ran out of space on my partition and could not grow it, I had a setting that would not show the selection screen for the different kernels at start up.

Does anyone know how to set the start up as such that the selection screen does not show?

---

### Post by anglican on 2010-10-14
> **dreamquartz said:**
> Before I had to re-install, because I ran out of space on my partition and could not grow it, I had a setting that would not show the selection screen for the different kernels at start up.

Does anyone know how to set the start up as such that the selection screen does not show?If GRUB 2's os-prober  identifies additional operating systems while  running the /etc/grub.d/30_os-prober  script the hidden menu timeout  feature is disabled by conditional statements. This also disables the  ability to use the SHIFT  key to display the menu during boot. So if you have multiple operating systems and wish to hide the menu you need to use scripts which will allow you to add a hidden timeout  feature to the boot sequence:                       

First is /etc/grub.d/03_hiddenmenu 
_________ 
#!/bin/sh 
# This is to provide legacy "hiddenmenu" from /etc/default/grub 

 if [ "x${GRUB_HIDDENMENU}" = "xtrue" ]; then
 cat << EOF
echo -n "Press ESC to enter the menu... " 
if sleep --verbose --interruptible ${GRUB_TIMEOUT} ; then 
 set timeout=${GRUB_TIMEOUT}
else  
 set timeout=-1
fi 
EOF
fi 
_________   
Second add this to /etc/default/grub 
 _________ 
# Uncomment to hide the menu (use 'ESC' to display) 
#GRUB_HIDDENMENU=true 
_________ 
And finally added GRUB_HIDDENMENU in the optional user defined vars in update-grub

Hope this helps.

H

---

### Post by dreamquartz on 2010-10-15
> **anglican said:**
> If GRUB 2's os-prober  identifies additional operating systems while  running the /etc/grub.d/30_os-prober  script the hidden menu timeout  feature is disabled by conditional statements. This also disables the  ability to use the SHIFT  key to display the menu during boot. So if you have multiple operating systems and wish to hide the menu you need to use scripts which will allow you to add a hidden timeout  feature to the boot sequence:                       

First is /etc/grub.d/03_hiddenmenu 
_________ 
#!/bin/sh 
# This is to provide legacy &quot;hiddenmenu&quot; from /etc/default/grub 

 if [ &quot;x${GRUB_HIDDENMENU}&quot; = &quot;xtrue&quot; ]; then
 cat << EOF
echo -n &quot;Press ESC to enter the menu... &quot; 
if sleep --verbose --interruptible ${GRUB_TIMEOUT} ; then 
 set timeout=${GRUB_TIMEOUT}
else  
 set timeout=-1
fi 
EOF
fi 
_________   
Second add this to /etc/default/grub 
 _________ 
# Uncomment to hide the menu (use 'ESC' to display) 
#GRUB_HIDDENMENU=true 
_________ 
And finally added GRUB_HIDDENMENU in the optional user defined vars in update-grub

Hope this helps.

H

Tx for the update.
I remember that is was a simple thing. I normally take notes of the changes I make to the system, so that I can redo them again, if something goes wrong. In this case I forgot to do that, and I had to re-install my system.

Cheers,
Dreamquartz

---

