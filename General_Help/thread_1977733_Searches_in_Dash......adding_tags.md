---
title: "Searches in Dash......adding tags"
date: 2012-05-10
forum: General Help
---

### Post by Derek Karpinski on 2012-05-10
I've installed guvcview, a webcam viewer similar to cheese.  When I search in the dash for 'webcam' or 'cam' or anything remotely close to guvcview's function, the search turns up nothing.

Now, this is not a big deal for me, because I know the name of the program 'guvcview'.  But trying to show my wife (who is reluctant to use Ubuntu) how to search for things in the dash is proving tough, because 'guvcview' means nothing to her.:confused:

So, my question is not specific to 'guvcview', but more of a general question:

_How can I add tags to the searchable items in the dash to help refine, or expand in this case, the amount of results the dash returns?_

---

### Post by JRV on 2012-05-10
This thread expains how to create a launcher.

[http://ubuntuforums.org/showthread.php?t=1961158](http://ubuntuforums.org/showthread.php?t=1961158)

The launcher will be a .desktop file located in /home/YOUR_USER_NAME/.local/share/application.
It will be available through the dash.

---

### Post by mc4man on 2012-05-10
I don't think you can, the Dash searches name & generic name, the Filter is bases on Categories

So in the case of guvcview it would be listed with the Media filter.

As far as searches, -   it's name, guvcview (.desktop) or anything in it's 'GenericName' or top of Description (GTK UVC video viewer
So UVC returns
video returns
viewer returns
(gtk won't

So again in the case of guvcview there is not much you can do after the fact, it doesn't mention webcam - ck. out 
apt-cache show guvcview

From the end user perspective I guess you could alter the Name= in it's .desktop, wouldn't affect anything but would return on a webcam search, ie
sudo gedit /usr/share/applications/guvcview.desktop
And change the Name=guvcview to Name=Webcam

---

### Post by Derek Karpinski on 2012-05-10
> **JRV said:**
> This thread expains how to create a launcher.

[http://ubuntuforums.org/showthread.php?t=1961158](http://ubuntuforums.org/showthread.php?t=1961158)

The launcher will be a .desktop file located in /home/YOUR_USER_NAME/.local/share/application.
It will be available through the dash.

I need it available for ALL users, not just me.  Thanks for the link though.

> **mc4man said:**
> I don't think you can, the Dash searches name & generic name, the Filter is bases on Categories

So in the case of guvcview it would be listed with the Media filter.

As far as searches, -   it's name, guvcview (.desktop) or anything in it's 'GenericName' or top of Description (GTK UVC video viewer
So UVC returns
video returns
viewer returns
(gtk won't

So again in the case of guvcview there is not much you can do after the fact, it doesn't mention webcam - ck. out 
apt-cache show guvcview

From the end user perspective I guess you could alter the Name= in it's .desktop, wouldn't affect anything but would return on a webcam search, ie
sudo gedit /usr/share/applications/guvcview.desktop
And change the Name=guvcview to Name=Webcam

This is more what I'm talking about.  So, Instead of changing the with 'sudo gedit /usr/share/applications/guvcview.desktop', could I:

```
gksudo nautilus
```

Browse to:
```
cd /usr/share/applications/
```

and right click on the 'guvcview.desktop' file and change the description to include webcam?

Will that mess anything up?:P

Also, should bugs be filed against any app that doesn't show up with generic search strings?  This really is a Unity issue, and not an application problem.  And I'm sure guvcview is not the only app that doesn't return a result.  Just curious.

---

### Post by mc4man on 2012-05-10
I don't believe altering the "GenericName=GTK UVC video viewer" in the .desktop will matter, it feels like the Dash search uses what apt-cache shows

Altering the Name= in the .desktop will be seen in the search.

I gather if the app, (upstream) altered it's Description to include webcam then it would show on a webcam search
(seen by if you search an app that's Not installed, the description comes from wherever such things are stored when you update your sources
- likely not a good idea to edit those files...

Changing the Name= in a .desktop is innocuous, really not much more than a descriptive element
screen shows

---

