---
title: "Firefox oddity"
date: 2009-11-03
forum: General Help
---

### Post by TheGreatGoat on 2009-11-03
Greetings,

I am having an extremely odd problem with Firefox (3.5.3) that I can only recreate on Ubuntu.

My laptop (Acer Aspire 3680) has a 4-way scroll button built-in with the touchpad. I use the top and bottom to scroll (works perfectly), and, until my recent reinstall to upgrade to Karmic, I used the left-right to go back and forward in Firefox (left=back, right=forward). However, I've noticed that in Firefox 3.5.3, left brings me forward one page, and right brings me back.

I know it's not a hardware issue, because using those same buttons in a scroll function causes the page to scroll left and right properly, and is consistently that way across multiple programs on Ubuntu. Also, I know it's not a hardware problem because it works fine when I boot into XP.

So it seems to be a bug with Firefox, I believe, but I cannot find any other people who have run into this as of yet. I've looked in about:config and tried several different settings there, but with no luck, and I was hoping maybe someone out there might have an idea.

---

### Post by TheGreatGoat on 2009-11-21
*bump*

---

### Post by TheGreatGoat on 2009-12-16
*bumps again*

---

### Post by TheGreatGoat on 2010-02-23
Here's how I managed to fix it, in case anyone out there runs into this again:

Open up a new tab in Firefox, and type in about:config

Search for mousewheel.horizscroll.withnokey

The three values for the settings listed should be 2, -1, and False.

This will allow you to properly use your left/right scrolling as back/forward.

---

