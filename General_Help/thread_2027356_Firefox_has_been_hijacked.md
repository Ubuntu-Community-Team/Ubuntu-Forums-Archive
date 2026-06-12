---
title: "Firefox has been hijacked"
date: 2012-07-16
forum: General Help
---

### Post by rapattack1 on 2012-07-16
Hi i have had this happen once before where i accidentally visited a malicious website and i couldn't close firefox after that. I think i got the applet saying something about 'stay on the page' and or 'leave the page'? After several reboots i can't use firefox but can use Chrome. I know there was a solution out there but i forgot what it was and googling didn't bring me any decent results

---

### Post by Frogs Hair on 2012-07-16
Remove Firefox and open home/hidden folders (Ctrl+H or show hidden.)Delete the .mozilla folder and reinstall Firefox. A new folder will be created when Firefox is installed. The bookmarks settings and extensions will be lost but so will the corrupt profile. I would suggest NoScript if didn't have it installed already.

---

### Post by raja.genupula on 2012-07-16
use NoScript add-on for firefox so you can know what scripts can allow and what can ban in that site. for more information  use this 

[https://addons.mozilla.org/en-US/firefox/addon/noscript/](https://addons.mozilla.org/en-US/firefox/addon/noscript/)

---

### Post by rapattack1 on 2012-07-16
Oh this just happened as well when i was told to update by the system

---

### Post by rapattack1 on 2012-07-16
If i let chrome import the bookmarks etc will that mean chrome will go bad too? I might have installed noscript but it was ages ago....ok will uninstall then

---

### Post by chocklet on 2012-07-16
sorry for my post, rapattack1.  On my first reading I failed to see that you could no longer start Firefox, so you can't export your bookmarks.

---

### Post by rapattack1 on 2012-07-16
i can start firefox. I just can't use it. It holds  where it last was before it got hijacked....i don't know how to explain...i can't close it. i can't do anything with it.

---

### Post by philinux on 2012-07-16
> **rapattack1 said:**
> i can start firefox. I just can't use it. It holds  where it last was before it got hijacked....i don't know how to explain...i can't close it. i can't do anything with it.

Your bookmarks are here.

/home/[COLOR="Red"]YOURUSERNAME[/COLOR]/.mozilla/firefox/[COLOR="Red"]RANDOMPROFILENUMBER[/COLOR].default/bookmarkbackups/bookmarks.[COLOR="Red"]DATE[/COLOR].json

You could copy them to the desktop and import them after sorting firefox out.

You could open a terminal and try launching in safe-mode. to see if you can export them.

```
firefox -safe-mode
```

---

### Post by chocklet on 2012-07-16
If you can't do anything with Firefox, then use Synaptic or  Ubuntu Software Center to uninstall/remove it.  If ininstalling does not remove the .mozilla directory, then do as Frogs Hair recommends and delete the .mozilla directory.

But first, export your bookmarks (to maybe your Documents directory).  Later, after reinstalling Firefox, import the bookmarks.  The problem is not a bookmark itself, but the web site.  There should be no problem importing the bookmarks into Chrome - but if you visit the offending site(s), then it may (or may not) cause a problem with Chrome.

You will find that turning off scripts with NoScript will cause in some web sites to stop working.  You will find yourself allowing scripting on your favorite sites.  The trick is to not allow scripts on the crucial site(s) that are giving you grief.

---

### Post by rapattack1 on 2012-07-16
Thanks will grab those....was concerned that they might have something in the folders...

---

### Post by rapattack1 on 2012-07-16
i went into safe mode and i got this. unchecked that last website which was the accidental clicked onto site and was able to fully open with it

---

### Post by philinux on 2012-07-16
> **rapattack1 said:**
> i went into safe mode and i got this. unchecked that last website which was the accidental clicked onto site and was able to fully open with it

Good old safe mode eh. Nice one.

---

### Post by rapattack1 on 2012-07-16
Wasn't able to import/export whatever but i got the file manually and just uninstalled/complete removal of firefox...rebooting now then reinstalling :0)

---

### Post by ajgreeny on 2012-07-16
As FF now stores its bookmarks in a sqlite database instead of a more easily browsable file such as the previous html file, it is worth making a change to the FF configuration so that a bookmarks.html file is made when FF is closed, as well as the sqlite db file.

Go to **about:config** in the FF addressbar, accept the warning, but be careful, then in the searchbar the top look for **bookmarks** and change the first one (it is in mine, anyway), **browser.bookmarks.autoExportHTML** to "true" by double clicking on it.  You will now have a html file which you can open and look at in FF or if you want to edit it you can use gedit

---

### Post by rapattack1 on 2012-07-16
OK i think i did that right?
I think everything else is right too...reinstalled ff...just have to get all the add-ons and don't really have time to learn no scripts but will try :0) Thanks everyone...time for bed zzzzzzzzzzzz

---

### Post by mike555 on 2012-07-16
When you get it straightened out you should install the addon/extension " WOT ".

---

### Post by rapattack1 on 2012-07-16
Yep always had that. It warned me but too late

---

