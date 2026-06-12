---
title: "Ubuntu 8.04 &amp; Firefox-3.5.7"
date: 2009-12-10
forum: General Help
---

### Post by Barney on 2009-12-10
Ubuntu 8.04, have Firefox-3.5.7 installed - Firefox does not display pictures on websites...????

Synaptic shows installed:
firefox-3.5
firefox-3.5-branding
firefox-3.5-gnome-support
xulrunner-1.9
xulrunner-1.9.1

and not installed:
xulrunner
xulrunner-1.9.2
xulrunner-1.9.3

---

### Post by hwttdz on 2009-12-10
Do you see an image if you browse to here [http://ubuntuforums.org/customavatars/avatar40096_2.gif](http://ubuntuforums.org/customavatars/avatar40096_2.gif) ?

---

### Post by bodhi.zazen on 2009-12-10
Are you using some type of adblock such as NoScript ?

---

### Post by Barney on 2009-12-10
Yes, I see the image at: [http://ubuntuforums.org/customavatars/avatar40096_2.gif](http://ubuntuforums.org/customavatars/avatar40096_2.gif)

---

### Post by Barney on 2009-12-10
I'm using Adblock, but not NoScript - disabling AdBlock doesn't help.

---

### Post by Barney on 2009-12-10
I'm using Opera to post here, as I could not enter user name and password in Firefox.

---

### Post by hwttdz on 2009-12-10
And what if you start firefox as

firefox -safe-mode

If that works then it seems to be a problem with firefox, if it does then it seems to be a problem with your add-ons.

---

### Post by Barney on 2009-12-10
Strange:  in firefox -safe-mode, on thedailypuppy.com the ads (pictures) show okay, but the pictures of the puppies don't show....

---

### Post by hwttdz on 2009-12-10
Try clearing your cache.  Then try viewing source and pulling up the image of a missing image.  Or going to tools->page info->media.

On an unrelated note, ... so cute!

---

### Post by Barney on 2009-12-10
Tried all of the above - pictures pull & show, from source; just seems like Firefox is not loading what's there in the source........

---

### Post by hwttdz on 2009-12-10
Report the bug to firefox? How did you end up with 3.5.7 anyways?

---

### Post by Barney on 2009-12-10
Feeling like "El Stupido" here: Somehow in Preferences/Content the Load images automatically had gotten "unchecked!"

Sheeeesh!!

My bad.

---

