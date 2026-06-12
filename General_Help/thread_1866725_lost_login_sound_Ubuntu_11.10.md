---
title: "lost login sound Ubuntu 11.10"
date: 2011-10-21
forum: General Help
---

### Post by mike_rep on 2011-10-21
Hi  After a clean install I had the login sound. Do not know what happened but lost it. Guest account still plays the sound. I found in a bug that the path to the sound files may be wrong. So I copied the ogg files from "/usr/share/sounds/ubuntu/stereo/" to "/usr/share/sounds/" and now it works. Found this here [https://bugs.launchpad.net/ubuntu/+source/libcanberra/+bug/862374](https://bugs.launchpad.net/ubuntu/+source/libcanberra/+bug/862374)  Can somebody tell me in which file the path above is stored and can be modified.  cu

---

### Post by Utew on 2011-10-21
Hmmm... thanks for the info.. and now I have my login drums back (for better or worse) ;)

Looks like this bug isn't getting any attention from the devs, at present...

---

### Post by ioca100 on 2011-10-25
Thank you , now I heard ubuntu studio login sound.__[]("http://ubuntuforums.org/member.php?u=1476719")

---

### Post by mike_rep on 2011-11-03
Oh found now another way to fix it. Files copied to  "/usr/share/sounds/" can now go into trash.
Download dconf editor and start dconf. goto org-gnome-desktop-sound
do not remember the theme name I had but below it showed freedesktop and pressed below right the default button. So the theme I had was replaced by freedesktop and login sound works again.
Something seems changed the theme name.

---

