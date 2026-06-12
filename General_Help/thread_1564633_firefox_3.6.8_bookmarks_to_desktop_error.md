---
title: "firefox 3.6.8 bookmarks to desktop error"
date: 2010-08-30
forum: General Help
---

### Post by elj4176 on 2010-08-30
I have had 2 people ask me about this lately so I thought I would try it.
They want to take a bookmark for a site and put it on their desktop. Seems easy enough - just drag the bookmark to the desktop. It works in chrome but when I tried it on 2 different pc's I get the same error:

Error while copying
There was an error getting information about "" 

Automount failed: DBus error org.freedesktop.DBus.Error.InvalidArgs: Mountpoint Already registered

Any idea how to fix it? I could just have them use chromium-browser I guess.

---

### Post by Frogs Hair on 2010-08-30
You can right click the page and save page as - - - and save to desk top but this will create a folder on the desktop.

---

### Post by scouser73 on 2010-08-30
> **elj4176 said:**
> I have had 2 people ask me about this lately so I thought I would try it.
They want to take a bookmark for a site and put it on their desktop. Seems easy enough - just drag the bookmark to the desktop. It works in chrome but when I tried it on 2 different pc's I get the same error:

Error while copying
There was an error getting information about "" 

Automount failed: DBus error org.freedesktop.DBus.Error.InvalidArgs: Mountpoint Already registered

Any idea how to fix it? I could just have them use chromium-browser I guess.

**1** - Right click on the **Desktop** & select **Create Launcher**

**2** - At the **Type** drop-down menu, select **Location**

**3** - Enter a name for the website

**4** - In the **Command** section enter the web address including **[COLOR="Red"]http[/COLOR]** or **[COLOR="Red"]https[/COLOR]** depending on whether the website is for online banking etc.

**Example:** [http://www.bbc.co.uk](http://www.bbc.co.uk) or [https://www.somefakewebsite.org](https://www.somefakewebsite.org)

Now click OK and the launcher will appear on your Desktop, click & surf.

---

### Post by elj4176 on 2010-08-31
Thanks! That worked.

I'm still wondering why I get an error when dragging a bookmark to the desktop when it works in Epiphany and chromium (and should work in firefox). 

Now I have an answer to their question and can put web links on their desktop.

---

