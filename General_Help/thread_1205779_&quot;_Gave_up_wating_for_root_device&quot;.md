---
title: "&quot; Gave up wating for root device&quot;"
date: 2009-07-06
forum: General Help
---

### Post by psychic019 on 2009-07-06
Hello all :)
this is my problem : 

Hello,
when my ubuntu is loading @ startup Iam getting this error:
[http://dominikengbers.gmxhome.de/bug.JPG](http://dominikengbers.gmxhome.de/bug.JPG)  (pic from google, not my monitor:P)
so xealot told me to do this: 
"when you are in the boot menu, where you c an select ubuntu press E " * (actuaclly its ESC but w/e)
" select the line starting with kernel, press E again (i think) to edit it"
" add the rootdelay thing at the end "
" enter enter " 
After I did all of that, xealot told me to do that: 
" the next step is to modify the root=/ parameter in the bootup menu; " 
" almost the same as before " 
" except when you edit the line starting with kernel"
" you need to use the arrow keys to find where it says root=/ "
" followed by a lot of crazy numbers "
" remove those, and make it say root=/dev/sda1 instead
" thats assuming it is sda1, I trust you gave me the right info "
After I did all of this, and let's assume I did it right.. when I go to the menu (*)
I'm getting some new stuff:
Find /Ubuntu/disks/boot/grub/menu.lst
Find /ubuntu/install/boot/grubl/menu.lst
Find /menu.lst
Find /boot/grub/menu.lst
Find grub/menu.lst
Commandline.
Reboot.
Halt.
-
And I can choose between them with the marker.
anyway.. I know its really complicated, but anyone here can help me out? :'((
xealot is a guy from #ubuntu [quaknet] and he is an OPerator.

I summarized all of this from IRC logs, if more information is needed tell me, but I'm almost sure that this is enough.

Thanks in advance!

---

### Post by psychic019 on 2009-07-06
someone ? :\

---

