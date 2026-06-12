---
title: "Saving GRUB parameters."
date: 2010-05-18
forum: General Help
---

### Post by dustinkredmond on 2010-05-18
First let me say that I am kind of a newbie to GRUB 2. I have Ubuntu 9.10 installed on my Acer Aspire One netbook laptop. I have a dual boot between Ubuntu and Windows XP. I can boot Ubuntu without problem but however whenever I select Windows in the GRUB menu it fails to boot and returns the following error message. "error: no such device: d648aabd30653bca" if it press "e" at the GRUB menu and edit out the line that says "search --no-floppy --fs-uuid --set d648aabd30653bca" it boots and works perfectly fine. However it is much of a pain to have to delete this line every time. Is there a way that i could save this. Thank you in advance again as I am not very proficient in GRUB 2.

---

### Post by drs305 on 2010-05-18
You can check the UUID's to make sure they are correct. If so, here is a guide to resolving the 'search' issue:
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:search]("http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:search")

Search issues were very common in the early development of Grub2 so there has been time to 'perfect' workarounds.  ;-)

---

### Post by Nythain on 2010-05-18
heh, someone smarter got to it faster than me :P

---

### Post by dustinkredmond on 2010-05-18
Thanks drs305, I'm trying your suggestion now. I believe that will solve it. Thank you again.

---

### Post by drs305 on 2010-05-18
Editing grub-mkconfig will definitely remove the search line from your grub menu and should correct things. The only time you will have to reaccomplish the edit is if there is a major update to the Grub library files. So bookmark the page but you don't have to keep it handy.

Don't forget to mark this solved with the Thread Tools link if in fact things work out as they should.

---

### Post by dustinkredmond on 2010-05-18
Woah, ok I've followed the tutorial and double checked it. I've placed the #'s and made sure to update grub following, but the search line is still there.

---

### Post by drs305 on 2010-05-18
Ok, for review. I'm using Grub 1.98. You can check the version with:
```
grub-install -v
```

Open /usr/lib/grub-mkconfig_lib for editing:
```
gksu gedit +138 /usr/lib/grub/grub-mkconfig_lib
```

This should place the cursor on or near these lines:
> 
  if fs_uuid="`${grub_probe} --device ${device} --target=fs_uuid 2> /dev/null`" ; then
     echo "search --no-floppy --fs-uuid --set ${fs_uuid}"
  fi


Add the #'s and save the file:
> 
**#**  if fs_uuid="`${grub_probe} --device ${device} --target=fs_uuid 2> /dev/null`" ; then
**#**     echo "search --no-floppy --fs-uuid --set ${fs_uuid}"
**#**  fi


Update grub:
```
sudo update-grub
```

---

