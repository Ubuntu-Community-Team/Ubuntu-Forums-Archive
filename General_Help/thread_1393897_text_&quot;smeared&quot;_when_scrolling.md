---
title: "text &quot;smeared&quot; when scrolling"
date: 2010-01-29
forum: General Help
---

### Post by tjk on 2010-01-29
Recently, I'm getting an annoying problem: When I scroll quickly the text smears or duplicates itself -- doesn't happen with all applications.  I haven't had this problem until I started to use OpenGL compositing with my NVidia card.  Any ideas how I can fix this?

---

### Post by Zorael on 2010-01-30
I've had this once in an svn version of Konversation I tried, but it disappeared when I downgraded back to the repository version. I made a screencast of it just for archival purposes - see attachment.

Does that look like what you're experiencing?

---

### Post by tjk on 2010-02-09
> **Zorael said:**
> I've had this once in an svn version of Konversation I tried, but it disappeared when I downgraded back to the repository version. I made a screencast of it just for archival purposes - see attachment.

Does that look like what you're experiencing?

This is similar to the problem that I have... although there is some variance from what you have shown.  I tried changing all the settings in the advanced tab... short of removing the OpenGL -- nothing helped.  I also looked for NVidia config settings, but didn't find anything useful.

Now I have switch to the Enlightenment (e17) window manager.  And I have enable xcompmgr with the -c option (-a  Use automatic server-side compositing. Faster, but no special effects.)  This works fine -- with some of the other options I also get "smearing".

*I am wondering if there are similar settings that can be set in the KDE compositing?  Or it just occurred to me that I might be able to run xcompmgr under KDE?*

---

### Post by tjk on 2010-03-29
It's really odd why some apps are almost unusable because of the smearing (for example: I don't use Konquor any more because it makes such a mess when I scroll).  Some apps scroll perfectly fine, others scroll down okay but not upwards.  Some smear when I scroll, but will "reset" after a second or two. It's weird...

---

