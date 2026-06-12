---
title: "Copy and Paste images from firefox to openoffice.org"
date: 2010-03-14
forum: General Help
---

### Post by Joshun on 2010-03-14
Most things in ubuntu have been working very well recently, but when i copy and image off firefox and paste it into openoffice (any program) it just comes up as a link. Firefox is 3.6, Openoffice.org is 3.1. I am using rightclick>copy image not copy link location so it isn't that, perhaps there's something wrong with my configuration. Please could somebody help
Joshua

Ubuntu version: 9.10 Karmic Koala

---

### Post by mcduck on 2010-03-14
Why not save the image to your computer first? You can just drag&drop images from Firefox into your desktop to save them.

---

### Post by Joshun on 2010-03-14
Well, if possible, i would like to copy and paste because its quicker and easier, i will save them to my computer if i have to though. When i copy an image from firefox and paste it into openoffice, it just comes up as a link, even though i copied it properly. It must be a firefox issue as it doesn't happen on opera or other web browsers.

---

### Post by Hagar Delest on 2010-03-14
Maybe it's... a feature. The logic behind this would be: if a user copies and pastes remote content on the wen then, keep the links so that if there is an update in the online content, it's updated when the user opens the file again.

Once pasted, go to the menu Edit>Links, select all the entries and *Break link*.

---

### Post by Slim Moe on 2010-03-14
Works just fine for me, even when saved and opened from another computer. Are you up-to-date ?

---

### Post by fisheater on 2010-03-14
This works but has two issues:

1. The entire file size of your document gets big quick. My understanding is that the image is saved as a PNG (which means it gets converted from what you drag into it). I have a 220 page document with pics I had copy/pasted and the save time was 2-5 minutes on a new computer. My second large document I have inserted the jpegs and it seems to save more quickly.

2. On occasion I have lost my images in the document and was left with a generic placeholder. This is problematic if you copy/paste without a local copy to reinsert the picture. 

OOo is very good, but I am still learning how to make it work to my needs. 

Good luck 

FE

---

### Post by Joshun on 2010-03-14
Thankyou for your guidance and support, its not that its a particularly large openoffice document, it happens as soon as from when you start from scratch. I'll install parcellite and see if that makes it any better.

---

### Post by Joshun on 2010-03-14
The effect is the same on drag and drop as it is copy and paste. I'm 100% up to date, even got backports enabled. It can't be an openoffice issue, as other web browsers like opera copy and paste fine. Perhaps its a firefox config issue or something. It must be a GNOME related issue, as i dont get this problem on my xubuntu computer which is also running karmic.

Its not just openoffice - firefox won't paste into other things either.

---

### Post by Joshun on 2010-03-15
Solved! What happened was that firefox was set to "Never Remember History", and so this was conflicting with the clipboard and preventing copy and paste on images. I've set it to "Use custom settings" and "Clear History When Firefox Closes".:popcorn::o:D;):p:):P

---

