---
title: "Update grub issue."
date: 2011-01-23
forum: General Help
---

### Post by cardy_c on 2011-01-23
I have a grub issue.  I have restored grubs in the past successfully several times to give me treble boots into Windows OSX and Ubuntu 10.4 but this one is giving me the following error no matter what I try.

Generating grub.cfg ...
No path or device is specified.
Try `/usr/sbin/grub-probe --help' for more information.
No path or device is specified.
Try `/usr/sbin/grub-probe --help' for more information.

Anyone any ideas?

---

### Post by mikewhatever on 2011-01-23
Can you also include the command used.

---

### Post by cardy_c on 2011-01-23
Wouldn't you know - after spending all day at this I figured it out 10 minutes after opening this thread!!!

It's working OK when I set bg=false in the /etc/grub.d/05_debian_theme.

Even though this file is identical to another working system, in fact i even copied it from the other system and I have the background image (ubuntu+blue) located in the same location as the other system. (/usr/share/images/grub)

So this is resolved 


It's late - Ill figure that part out tomorrow.




use_bg=false
if [ "$GRUB_TERMINAL_OUTPUT" = "gfxterm" ] ; then
  for i in {/boot/grub,/usr/share/images/desktop-base,/usr/share/images/grub}/ubuntu+blue.{png,tga} ; do
    if is_path_readable_by_grub $i ; then

---

### Post by mikewhatever on 2011-01-23
Have a good night.

---

### Post by cardy_c on 2011-01-24
Just in case this helps anyone else - to make this work all I did was changed the file type of the image I was trying to use a for a background to a tga. 

A jpg or png would not work for some reason.

---

