---
title: "Firefox toolbar default icon images are missing"
date: 2009-12-06
forum: General Help
---

### Post by qlinux on 2009-12-06
Ahh... Another upgrade another challenge..  I like linux and I really like Ubuntu but sometimes it's like raising teenagers - it's a labour of love.  :-)
Here's the latest challenge..  

The default toolbar icons in Firefox are missing.  Here's what's happening:
1. The buttons are there but there is no image on the icon. 
2. When I select to customize the toolbars the selection of buttons are also missing the icons.
3. It seems to be with only the standard buttons such as forward, back, home, reload, copy, etc..
4. No other apps, eg openoffice appear to be having this problem.
5. "System >> Preferences >> Appearance >> Interface" and check "Show icons in menus". Is already set and has no effect.
6. disabling the "Ubuntu Firefox Modifications 0.8" add-on as I saw in another post does work until the next restart and then oddly enough enabling the add-on will have the icons appear until the next system restart .

Info:  Ubuntu 9.10,upraded from 9.04, Firefox 3.5.5


I wish I did not have to trouble you good people with this matter but nothing I've tried seems to be working.  

Any ideas or solutions?

Thank you in advance for your assistance.

---

### Post by lovinglinux on 2009-12-07
You could try to reset your toolbars to default. Right-click on a toolbar, select "customize" then hit the "Restore Default Set" button.

---

### Post by qlinux on 2009-12-09
Thank you for the tip lovinglinux but your suggestion didn't work.  In fact when I right-click on a toolbar, select "customize" in the Customize Toolbar dialogue box some of standard buttons are missing their respective icons.  For example the cut and Copy buttons are in the dialogue box but neither has an icon.

I tried dragging the New Tab button to the toolbar.  This is one of the buttons that does show an icon.  This was successful but I'm curious to see what happens when I restart Firefox.

---

### Post by lovinglinux on 2009-12-09
> **qlinux said:**
> Thank you for the tip lovinglinux but your suggestion didn't work.  In fact when I right-click on a toolbar, select "customize" in the Customize Toolbar dialogue box some of standard buttons are missing their respective icons.  For example the cut and Copy buttons are in the dialogue box but neither has an icon.

I tried dragging the New Tab button to the toolbar.  This is one of the buttons that does show an icon.  This was successful but I'm curious to see what happens when I restart Firefox.

You could try to delete the **localstore.rdf **file inside your FF profile folder. Don't forget to close Firefox first.

---

### Post by BoeroBoy on 2011-01-03
No I have the same problem on my Sabayon x86_64 after an upgrade to 3.6.13.  Funny a full system update finally fixed the common gecko animated GIF bug but now my left and right arrow images are missing.  Is there a standard location for default theme images or a place we can verify they are installed?  Both my firefox built from source and my firefox-bin 3.6.13 are missing images.

BTW, changing themes correctly shows images from that theme, and back/forth buttons are still clickable in default theme, but the images are missing.

Thanks

---

### Post by BoeroBoy on 2011-01-03
I finally used entropy to install the tango icon theme manually.  It looks like Ubuntu equivalent fix:

```
sudo apt-get install tango-icon-theme-common
```

---

### Post by saluk on 2011-05-26
Thanks lovinglinux, the localstore trick fixed the problem for me. I think the images got lost when firefox upgraded to the 5 beta. I wonder if it has something to do with firefox level updates that conflict with ubuntu files?

---

### Post by lovinglinux on 2011-05-26
> **saluk said:**
> Thanks lovinglinux, the localstore trick fixed the problem for me. I think the images got lost when firefox upgraded to the 5 beta. I wonder if it has something to do with firefox level updates that conflict with ubuntu files?

You are welcome.

I don't think there is a conflict with Ubuntu. Is probably just a file corruption.

---

