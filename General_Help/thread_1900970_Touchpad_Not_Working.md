---
title: "Touchpad Not Working"
date: 2011-12-27
forum: General Help
---

### Post by Momof9Blessings on 2011-12-27
Hi all,

I have recently added ubuntu 11.10 to my vista laptop....

I thought it has been running great... then all of a sudden I could not use the touchpad (I don't us an external mouse other than my wacom tablet occassionally - which I am using now to move around the forums).

Yesterday and some this morning I have been tweaking GIMP.  This morning I installed synaptics so that I could get GIMP-Gap...

Sometime in all this tweaking, when I had GIMP open and then went back to firefox (alt tab) - GIMP would close....  Then I had that transparent orange thing and then had problems with the unity bar etc....  So I eventually closed everything down and restarted the computer and when it started up again - that is when the touchpad started freezing.....

I tried to find similar problems, but I saw things mostly with usb mouses freezing....

Thank you for your help,

---

### Post by Momof9Blessings on 2011-12-27
I just found this....

```
sudo rmmod psmouse
sudo modprobe psmouse
```

works now!!!


BTW how do I make a post say solved???

---

