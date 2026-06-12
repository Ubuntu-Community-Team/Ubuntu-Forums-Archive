---
title: "can't find downloaded package!"
date: 2010-01-15
forum: General Help
---

### Post by Overthere on 2010-01-15
hi everyone,
my "struggle" for today:
I download packages (nautilus or squash) for photo bulk resizing, and voilà! I can't find where they end up!
Any ideas?

Thanks a ton!
Brian

---

### Post by audiomick on 2010-01-15
Downloaded with firefox?
Under edit> preferences on the first tab the is a point called "save to the following directory". That should tell  you where they should be.

---

### Post by Overthere on 2010-01-15
HI Micheal,
well, no, I used synaptic package manager. Was I supposed to use a site download?

Brian

---

### Post by Leppie on 2010-01-15
when you say you downloaded with synaptic, do you mean that you installed the package?
i've never found an option to just download a package in synaptic.

---

### Post by Overthere on 2010-01-15
Sorry, I meant installed.. 

B

---

### Post by ajcham on 2010-01-15
Open a terminal and run the command, **squash**

You should be able to add a menu item to run the software (it seems the installer doesn't create one for some reason), but I'm not familiar with doing this in xfce, so can't you help there.

EDIT: Addendum - as for the other one, do you mean nautilus-image-converter?  If so, that is just a matter of locating the image files within the Nautilus file browser, highlight and right-click.  There will be a menu item labelled 'Resize Images...'

---

### Post by Leppie on 2010-01-15
if you're looking for an installed application you cannot find, use the built in application finder. go to Applications>Accessories>Application Finder, type in the application name in the search box and the app will appear in the main window.

---

### Post by Overthere on 2010-01-15
I did... still can't find Nautilus!

---

### Post by Leppie on 2010-01-15
ah, you installed nautilus...
it won't appear in your xfce menu as it is a gnome app...
but if you wish you can press ALT-F2, then use "nautilus --no-desktop --browser" (without the quotes) as the command to run. or create a desktop launcher: right click your desktop, choose "Create Launcher...", put Nautilus as name and "nautilus --no-desktop --browser" (without the quotes) as the command to execute, you can also set an icon if you want, click the "Create" button.

---

### Post by Overthere on 2010-01-15
Leppie,
I got the icon onto the desktop using the launcher, but it doesn't open, even if I right-click and select "execute."

---

### Post by Leppie on 2010-01-15
> **Overthere said:**
> Leppie,
I got the icon onto the desktop using the launcher, but it doesn't open, even if I right-click and select "execute."
then try to add the path to the executable. you can find the path like this:
```
which nautilus
```
on my system it's /usr/bin/, so the complete command would be:
```
/usr/bin/nautilus --no-desktop --browser
```

---

### Post by Overthere on 2010-01-15
Leppie,
I DID get it to work using alt+F2, but I'd still like to use that icon....!

B

---

### Post by Leppie on 2010-01-15
> **Overthere said:**
> Leppie,
I DID get it to work using alt+F2, but I'd still like to use that icon....!

B
just posted new instructions ;)

---

### Post by Overthere on 2010-01-15
Leppie,
I DID IT!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!
I went into my usr/bin and found the app!! So I made a link on the desktop!

I can't thank you enough!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!

Thanks for your time, and best to you,
Brian

---

### Post by Overthere on 2010-01-15
I hope one day I can help others like you all do here!!!!

B

---

### Post by Leppie on 2010-01-15
> **Overthere said:**
> I hope one day I can help others like you all do here!!!!

B
of course you will be able to. now you know a couple more things in ubuntu, so you can use these to start with ;)

i'm glad it's working more or less as you wanted it to :)

---

