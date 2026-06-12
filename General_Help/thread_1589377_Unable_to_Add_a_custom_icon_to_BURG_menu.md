---
title: "Unable to Add a custom icon to BURG menu"
date: 2010-10-06
forum: General Help
---

### Post by nbulchandani on 2010-10-06
Hello,
I installed Backtrack on my System and need to add a custom icon to the BURG menu for it.
1)I added an icon named Backtrack.png to /boot/burg/themes 
2)modified the /boot/burg/themes/icons/large file to have in the class block
3)modified /etc/burg.d/40_custom for the entry Backtrack to
menuentry "BackTrack 4.0" --class backtrack --class os --group group_/dev/sda7

Still on loading the place for Backtrack is Occupied by the image for Unknown Classes...
Where am i wrong??
Thanks

---

### Post by nbulchandani on 2010-10-07
anybody can give me any hint please......
Thanks

---

### Post by psic0 on 2010-12-05
Hi.

I don't know if you have found the solution: add a new class in hover file to use your new icons.

File: /boot/burg/themes/icons/hover

New entry:   -backtrack { image = "$$/grey_backtrack.png:$$/large_backtrack.png" }

If you are using a grey image, remember that Burg uses RGB images, not grey ones.

Ciao

---

### Post by h4uw1n3 on 2011-02-22
i did it also...for android system.... the file didn't show the picture only a file with "x"icon...
when i try burg-emu... it didn't show anything... unnknown... >.<


any idea to custom the themes and icon?

---

### Post by h4uw1n3 on 2011-02-23
i was moving the icons folder to another partition and then edit it, after that moving it back again....it works now... no idea why..... XD

---

