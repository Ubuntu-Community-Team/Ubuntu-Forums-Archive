---
title: "File associations"
date: 2011-05-15
forum: General Help
---

### Post by OldManRiver on 2011-05-15
All,

Been looking for a HOWTO on file associations.  One of my U Boxes has suddenly decided that all logs, text files, scripts, etc are now opened and edited with OpenOffice (OO).

I need to find a way to reset these where Gedit is default text editor, Sream is default HTML, PHP, JAVA editor, .... so on.

I have not been able to find anything on this.

Help please!

Thanks!

OMR

---

### Post by oldos2er on 2011-05-16
Look in either ~/.local/share/applications/mimeapps.list or /usr/share/applications/defaults.list
More info here: [http://www.johannes-eva.net/change-the-default-application-ubuntu-linux](http://www.johannes-eva.net/change-the-default-application-ubuntu-linux)

---

### Post by akand074 on 2011-05-16
[Ubuntu-Tweak]("http://ubuntu-tweak.com/") is a good GUI tool for such things. There is a ppa for it if you're interested.

---

### Post by OldManRiver on 2011-05-18
> **akand074 said:**
> [Ubuntu-Tweak]("http://ubuntu-tweak.com/") is a good GUI tool for such things. There is a ppa for it if you're interested.

akand074,

Yes ppa please!  Tweak is a really grat program, enjoying it but still learning.

Thanks!

OMR

---

### Post by mc4man on 2011-05-18
This was simply caused by using a r. click > open with - use other application on one example of those file types
On that dialog box there is an option that is enabled by default - 
"remember this application for ..."
That option switches the default for the file type you were opening.
So this can happen again if you use 'open with - use other application' and leave the option enabled

All filetypes can have their default app to open changed in this manner or thru the more typical of >  take any 1 example and 
right click on the file > **properties** > open with

---

### Post by akand074 on 2011-05-18
> **OldManRiver said:**
> akand074,

Yes ppa please!  Tweak is a really grat program, enjoying it but still learning.

Thanks!

OMR

Here's the terminal commands to add the stable PPA and installing Ubuntu Tweak

```
sudo add-apt-repository ppa:tualatrix/ppa
sudo apt-get update
sudo apt-get install ubuntu-tweak
```

Here's the [link]("https://launchpad.net/%7Etualatrix/+archive/ppa") for it if you want to look at it.

---

### Post by OldManRiver on 2011-05-19
akand074,

Had already installed but added ppa anyway to get updates.

Tweak did the job on first round, found some more association issues so will going back for round 2 soon.

Thanks!

OMR

---

### Post by wildmanne39 on 2011-05-19
> **OldManRiver said:**
> All,

Been looking for a HOWTO on file associations.  One of my U Boxes has suddenly decided that all logs, text files, scripts, etc are now opened and edited with OpenOffice (OO).

I need to find a way to reset these where Gedit is default text editor, Sream is default HTML, PHP, JAVA editor, .... so on.

I have not been able to find anything on this.

Help please!

Thanks!

OMR
Hi, go to preferences and click on prefered applications and you should be able to set it there.

---

### Post by OldManRiver on 2011-05-21
wildmanne39,

Noticed when looking in this that Evolution is still installed, and I had taken steps to remove it.  Problem is the integration into everything.

Do you know a clean way to remove it?

Thanks!

OMR

---

### Post by AlphaLexman on 2011-05-21
> **OldManRiver said:**
> Do you know a clean way to remove it?
From a terminal window,
```
sudo apt-get remove evolution
```
will remove the program only.
```
sudo apt-get purge evolution
```
will remove the program **and** all user settings.

Good Luck!

---

### Post by OldManRiver on 2011-06-04
All,

Closing this thread as all problems resolved.

Thanks All!

OMR

---

### Post by OldManRiver on 2011-07-11
All,

Hate to add something here, since I said "closed", but need to add extenson handling for .ini and .php5 files and have not figured out how to "add" extensions in Tweak.

If you know how please respond!

Thanks!

OMR

---

### Post by CatKiller on 2011-07-11
> **OldManRiver said:**
> need to add extenson handling for .ini and .php5

It's not extension, it's MIME type. File name is no way to work out what type of file it is.

Right-click on one of them, select Properties, select the Open With tab and pick the program you want to use from the list. If the program you want to use isn't in the list, click on Add and type in the command of the program you want to use.

---

### Post by OldManRiver on 2011-07-12
> **CatKiller said:**
> Right-click on one of them, select Properties, select the Open With tab and pick the program you want to use from the list. If the program you want to use isn't in the list, click on Add and type in the command of the program you want to use.

CK,

Hey used to have the checkbox for "Always use this action for this file type" but no longer comes up or would do this, now always getting the list, so tired of that and want to force .ini, .php5, .conf, and a few more to open with Screem Editor and can not get it done.  They do not appear in the list of file types in the Tweak dialog and need to add them into that list so I can always get the "Open" and "Edit" actions I need.

Thanks!

OMR

---

### Post by CatKiller on 2011-07-12
Putting an entry in the Properties -> Open With tab also adds it to the right-click context menu AFAIK.

---

### Post by OldManRiver on 2011-07-13
CK,

Not on my machine!

OMR

---

### Post by skibler on 2011-07-14
The "Always use this action for this file type" seems to be gone in Nautilus 3, as far as I can tell. That leaves no straight forward way to change file types, except to use something like ubuntu-tweak.

Having text files associated with notepad.exe is hilariously annoying.

---

### Post by CatKiller on 2011-07-14
> **skibler said:**
> That leaves no straight forward way to change file types, 

You mean apart from right-clicking on it and selecting Properties? This really isn't difficult.

---

### Post by skibler on 2011-07-14
> **CatKiller said:**
> You mean apart from right-clicking on it and selecting Properties? This really isn't difficult.

Oh shi. . .

I am not sure how I missed that one.

---

### Post by CatKiller on 2011-07-14
> **skibler said:**
> Oh shi. . .

I am not sure how I missed that one.

:)

Me either. I'd mentioned it twice in this thread already...

---

### Post by OldManRiver on 2011-07-14
> **CatKiller said:**
> You mean apart from right-clicking on it and selecting Properties? This really isn't difficult.

No option for this in the "right-click".  Example of what I'm talking about is:

Nautilus and Tweak have .php set as PHP file and assigned to SCREEM editor, but when you right click the file to edit, SCREEM is not an option in the list, so "Open with other application" always must be selected.

This is both irritating and time consuming.

That is why I must fix it, loosing my mind, as I work 10-12 hours daily on this machine.

Thanks!

OMR

---

### Post by CatKiller on 2011-07-14
> **OldManRiver said:**
> No option for this in the "right-click".  Example of what I'm talking about is:

Nautilus and Tweak have .php set as PHP file and assigned to SCREEM editor, but when you right click the file to edit, SCREEM is not an option in the list, so "Open with other application" always must be selected.

This is both irritating and time consuming.

No.

Right-click. **Select Properties.**

---

### Post by OldManRiver on 2011-07-15
CK,

Not totally working but Yes better.

Thanks for insisting!

OMR

---

