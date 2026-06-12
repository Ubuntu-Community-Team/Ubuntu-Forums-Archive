---
title: "Sharing firefox bookmarks with windows"
date: 2009-11-29
forum: General Help
---

### Post by Dr. Oddbio on 2009-11-29
Is there any easy way to share my bookmarks between firefox and windows?

So I'm thinking, maybe I can redirect my linux firefox to store/retrieve the bookmarks from my windows partition where firefox is installed.

OR, I could make startup scripts that will add to the bookmarks, what it is on the other partition.

Also, it would be nice if I could share other things like history / passwords, cookies. But I will be content with bookmarks.

So, any other ideas? Where are the firefox bookmarks stored?
Thanks.

---

### Post by Cheesemill on 2009-11-29
The easiest way is probably to install the xmarks extension in both firefoxes, this will keep your bookmarks synced.

---

### Post by howefield on 2009-11-29
Another vote for xmarks. But...

Opera also has a nice synchronisation feature built in which takes care of this, (bookmarks amongst other things) xmarks was one of the last hooks keeping me with Firefox, but with this feature I think Opera gets the thumbs up.

---

### Post by grizzler on 2009-11-29
> **Dr. Oddbio said:**
> Is there any easy way to share my bookmarks between firefox and windows?
Yes. Well, easy enough anyway. :-)

> So I'm thinking, maybe I can redirect my linux firefox to store/retrieve the bookmarks from my windows partition where firefox is installed.
You can.

> OR, I could make startup scripts that will add to the bookmarks, what it is on the other partition.

Also, it would be nice if I could share other things like history / passwords, cookies. But I will be content with bookmarks.

So, any other ideas? Where are the firefox bookmarks stored?
They're in the file places.sqlite in your profile folder.

This is what I've done.

On both Windows and Ubuntu I've moved the profile data out of the usual location, i.e. the one with the default.hdyewfce (whatever) name to a folder with a simpeler name (D:\Data\Firefox on Windows and /home/data/firefox on Ubuntu). I've changed the entry in the profiles.ini file to read **IsRelative=0**, with the real path in the **Path** entry. All of this isn't *necessary*, but I find it makes referencing things easier.

The main files are all on the Windows partition. In Ubuntu, this is mounted (using ntfs-3g) as /mnt/data/Data/Firefox.

I've created symlinks in /home/data/firefox, pointing to the relevant files in /mnt/data/Data/Firefox, i.e.:

cookies.sqlite
permissions.sqlite
places.sqlite

I'm not particularly interested in the history and the like myself, but I suppose you could create symlinks to the other sqlite files as well.

Unfortunately, some extensions have the nasty habit of storing their settings in prefs.js and this is the one file you can't (successfully) create a symlink to, because there are absolute pathnames in there and you can't make them relative and expect them to stay that way (in my experience at least...).

This setup has worked fine for me for over a year.

---

### Post by oldfred on 2009-11-29
I have shared firefox and thunderbird for 3 years. Orginally we were primarily Windows and the spouse was not big on the idea of change. I got her working primarily on firefox and thunderbird and then the change to Ubuntu was much easier. We still use Windows for one application and occassionly other things so I still dual boot.

My original shared partition was FAT32 because 3 years ago the NTFS-3g driver was considered not quite ready yet. I just converted my shared partition to NTFS. I actually have it shared with whatever I boot Win, 9.04 or 9.10. I also copy the entire profile directory (8chars.default) to my windows portable when we travel and copy back when we return.

You will need a shared partition that can be read by both windows and Ubuntu, I suggest NTFS now. You have to install the applications in both and modify to profile.ini files to point to the new location with the correct profile directory.

More info:

[http://kb.mozillazine.org/Sharing_a_profile_between_Windows_and_Linux](http://kb.mozillazine.org/Sharing_a_profile_between_Windows_and_Linux)
[http://kb.mozillazine.org/Category:Profiles](http://kb.mozillazine.org/Category:Profiles)

---

### Post by el cameleon on 2009-12-04
Another possibility will be to use weave synch, which is the official add-on from Mozilla Labs:
> Whether you use Firefox on your phone, laptop, or desktop, Weave Sync lets you securely take your bookmarks, history, tabs and passwords wherever you go.

[https://addons.mozilla.org/en-US/firefox/addon/10868](https://addons.mozilla.org/en-US/firefox/addon/10868)

---

### Post by Dr. Oddbio on 2009-12-04
Actually I just remembered messing around with this a while back.

[http://www.stardock.com/products/desktopx/](http://www.stardock.com/products/desktopx/)

I used it to get rid of everything on my desktop so you just see an image, but I had widgits blend in with the image on the screen, so I would click on an eye or something and it would open a home folder or control panel etc..

Not sure if it's still free though.

---

