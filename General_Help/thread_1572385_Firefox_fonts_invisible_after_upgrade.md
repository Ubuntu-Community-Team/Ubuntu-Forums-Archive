---
title: "Firefox fonts invisible after upgrade"
date: 2010-09-11
forum: General Help
---

### Post by fmouse on 2010-09-11
I just upgraded a laptop from an older version of Ubuntu to 10.04.1 LTS, which included an upgrade of firefox to ver. 3.6.9.  Many pages in firefox now display only some of the text, although if I hilight where the text should be I get hilighted areas and if I copy and paste them into an editor the text shows up.  Other pages display normally.

An example of this is [http://ubuntuforums.org]("http://ubuntuforums.org") where the "Welcome to the Ubuntu Forums ..." (un-logged in) paragraph is invisible although the off-white box which should contain this text is there.  A few things I've tried and discovered:

* SeaMonkey doesn't have this problem (I'm using it to write this).

* If I un-check "Allow pages to choose their own fonts", the invisible text shows up with locally spec'd fonts.  Specifying local font colors makes no difference.

* Switching users makes no difference.  

* I've tried re-installing a large number of ttf fonts plus fontconfig, which makes no difference.

* This problem wasn't there before the upgrade.

Any reasonable suggestions on how to fix this will be appreciated!

---

### Post by lovinglinux on 2010-09-12
Screenshot please.

---

### Post by fmouse on 2010-09-13
> **lovinglinux said:**
> Screenshot please.

[IMG]http://www.frobniz.com/firefox_font_issue.png[/IMG]

---

### Post by lovinglinux on 2010-09-13
Create a new Firefox profile, to see if the problem persists. See Firefox [[COLOR="Sienna"]**General Troubleshooting Steps**[/COLOR]](http://firefox-tutorials.blogspot.com/2010/05/general-troubleshooting-steps.html) tutorial.

---

### Post by fmouse on 2010-09-13
> **lovinglinux said:**
> Create a new Firefox profile, to see if the problem persists. See Firefox [[COLOR="Sienna"]**General Troubleshooting Steps**[/COLOR]](http://firefox-tutorials.blogspot.com/2010/05/general-troubleshooting-steps.html) tutorial.

I saved off my bookmarks and moved my user profile completely out of the way, which doesn't help.  I did this before posting, which I suppose I should have mentioned in the first place.

---

### Post by lovinglinux on 2010-09-13
[http://ubuntu-ky.ubuntuforums.org/showpost.php?p=9403517&postcount=9](http://ubuntu-ky.ubuntuforums.org/showpost.php?p=9403517&postcount=9)

EDIT: I just noticed you already did that, but I think your problem is related to the new tff installed fonts. Try to change the font type.

---

### Post by fmouse on 2010-09-13
> **lovinglinux said:**
> [http://ubuntu-ky.ubuntuforums.org/showpost.php?p=9403517&postcount=9](http://ubuntu-ky.ubuntuforums.org/showpost.php?p=9403517&postcount=9)

EDIT: I just noticed you already did that, but I think your problem is related to the new tff installed fonts. Try to change the font type.

That's entirely possible.  I seem to recall that in my research on the problem I came across someone who said that this problem could be caused by corrupted external fonts.  I can, of course, spec my own fonts and the problem goes away, but I do web development work, so this really isn't an option.

So the question is, what fonts *should* I be using to give firefox a minimal standard set.  I assume firefox gets its fonts from the fontconfig system from those specified in /etc/fonts/conf.avail, yes?  I've got several Windows TTF collections pulled in via /etc/fonts/local.conf, and from what I know about Linux, I'm beginning to smell a rat here ;).  I don't have time to mess with it now, but when I get a chance I'll pull out these fonts and see if it makes a difference.

EDIT:  Actually the Windoze TTF fonts are on my desktop.  I *may* also have them on the laptop, where the problem is.  It's kinda likely.  On the other hand, I'm running Firefox 3.6.3 on my desktop and I don't have the problem.  It'll be tomorrow before I can look at it.

---

### Post by fmouse on 2010-09-14
Bingo!  I had a Windows verdana font spec'd in /etc/fonts/local.conf.  Commenting that out and re-running fc-cache solved the problem.

This doesn't entirely address the larger problem.  At one time, I had a number of Windows TTF fonts spec'd in /etc/fonts/local.conf.  Since I do web development work, these were used to allow me to see what a page would look like if a specific standard Windows font were used to render it.  The fontconfig system, and all applications which depend on it, *should* properly handle a 3rd party font set.  There's no problem with the same pages in SeaMonkey, and TTF is a known, standard font file format.  So although this solves my particular problem, this looks like an upstream problem with Firefox for Linux.

Thanks, lovinglinux, for pointing me in the right direction :)

---

### Post by lovinglinux on 2010-09-15
> **fmouse said:**
> Bingo!  I had a Windows verdana font spec'd in /etc/fonts/local.conf.  Commenting that out and re-running fc-cache solved the problem.

This doesn't entirely address the larger problem.  At one time, I had a number of Windows TTF fonts spec'd in /etc/fonts/local.conf.  Since I do web development work, these were used to allow me to see what a page would look like if a specific standard Windows font were used to render it.  The fontconfig system, and all applications which depend on it, *should* properly handle a 3rd party font set.  There's no problem with the same pages in SeaMonkey, and TTF is a known, standard font file format.  So although this solves my particular problem, this looks like an upstream problem with Firefox for Linux.

Thanks, lovinglinux, for pointing me in the right direction :)

You are welcome. About the font, I use Verdana without problems, but I have installed all my ttf fonts through *ubuntu-restricted-extras* and I'm using KDE.

---

