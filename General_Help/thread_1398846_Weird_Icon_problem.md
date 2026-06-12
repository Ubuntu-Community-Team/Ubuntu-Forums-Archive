---
title: "Weird Icon problem?"
date: 2010-02-05
forum: General Help
---

### Post by Roasted on 2010-02-05
I installed the Moomex theme on my desktop, and grabbed the Black/White icon set in the picture seen here:

[http://www.gnome-look.org/content/preview.php?preview=1&id=72619&file1=72619-1.jpg&file2=72619-2.jpg&file3=72619-3.jpg&name=black-white+2+Style](http://www.gnome-look.org/content/preview.php?preview=1&id=72619&file1=72619-1.jpg&file2=72619-2.jpg&file3=72619-3.jpg&name=black-white+2+Style)

So I did the same thing on my work laptop, running the same version of Ubuntu. Went to the same link, downloaded, dropped the unzipped folder into my .icons folder and applied it accordingly.

Well, it worked. My folder icons changed, but my application icons for the most part didn't. The red flag for me was the Firefox icon, it's still the default one you see on the Firefox web page - not the large black/blue one you see on that link.

Any idea?

---

### Post by Roasted on 2010-02-05
Okay, more problems. I was trying different icon sets and it became apparent that icons were crossing over from set to set. For example, I was running with the black and white gloss icon set, but some icons from nostromo's icon set were in it. Why? What the hell?

So I deleted all of my icon sets in an attempt to start over, and added black and white gloss again. Now I have no icon for xchat, firefox, thunderbird, etc etc.

So, I beg. How do I get black and white gloss icon sets to... work... just like my desktop?

EDIT - Okay, so I just had to restart Docky to get them working. But my firefox icon is STILL not right. It's still the default orange, and not part of the black/white gloss set. How can I individually change it?

---

### Post by Roasted on 2010-02-07
Okay, so let's go through a rerun of the problem.

Icon package.
Gnome-Look.org
Perfect on desktop
Perfect on laptop
EXCEPT no firefox icon on laptop
Permissions are fine
1,566 files in each folder on each system
File in folder exists
DOESNT WORK

How can I change JUST the firefox icon at the very least to get this flipping icon theme to work right?

EDIT - I must be missing a package. I just installed another icon set and some of it is missing from my laptop while everything is fine on my desktop. What package would cause this? What am I missing?

SOLVED - A user in the Ubuntu IRC helped me out. In the folder path to my icon set, which in my case was:

/home/jason/.icons/black-white_2-Gloss/scalable/apps/256

I had to copy the firefox-3.0.png file, paste it, and rename it to firefox-3.5.png, and it worked. Guess the icon pack just hadn't been updated since the new firefox was out.

---

