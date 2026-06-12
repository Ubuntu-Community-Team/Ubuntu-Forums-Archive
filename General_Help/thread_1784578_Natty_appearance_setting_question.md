---
title: "Natty appearance setting question"
date: 2011-06-17
forum: General Help
---

### Post by firstrock on 2011-06-17
Hello

Newbie linux user here. I seemed to have screwed with my appearance settings to the point that any open windows go to the top left of the screen and the top of the open window is not visible, I.E. the close and minimize buttons are no longer visible.

Any idea how to fix this?? Awfully annoying to have to rclick to close a window!

Thanks.

John

---

### Post by ssreddy555 on 2011-06-17
Type in the Terminal

```
unity --reset
``` This may help u.

---

### Post by firstrock on 2011-06-17
That did help some. I'm still missing the "x", "-" buttons to the left of File Edit etc. Any ideas?

---

### Post by ssreddy555 on 2011-06-17
> **firstrock said:**
> That did help some. I'm still missing the "x", "-" buttons to the left of File Edit etc. Any ideas?

See if u get them back after a reboot.

---

### Post by firstrock on 2011-06-17
A reboot didn't help. After I installed Natty, I installed compizconfig and was playing around with some of the settings. It was after this that I lost some functionallity of my windows. Also, my conky on the desktop disappears for good when I hit the hide all windows button in the bottom left corner.

If I were in Windows this would be an easy fix but I'm not farmiliar enough with Natty yet to know what I did. I'm considering a re-install just to start fresh (had to redo my natty server this morning due to screwinging up my network settings!) ;)

Thanks!

John

---

### Post by firstrock on 2011-06-17
Here is how my windows look:

[IMG]http://i27.photobucket.com/albums/c186/firstrock/Screenshot-1.png[/IMG]

---

### Post by firstrock on 2011-06-18
I got it fixed via this article [http://mihirknows.blogspot.com/2008/03/reset-ubuntugnome-settings-to-defaults.html](http://mihirknows.blogspot.com/2008/03/reset-ubuntugnome-settings-to-defaults.html)

I simply reset Gnome's settings by running this command:

rm -rf .gnome .gnome2 .gconf .gconfd .metacity


Thanks for the help!

---

