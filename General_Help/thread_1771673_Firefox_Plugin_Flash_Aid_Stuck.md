---
title: "Firefox Plugin Flash Aid Stuck"
date: 2011-05-30
forum: General Help
---

### Post by linuxinstalledfromhdd on 2011-05-30
Hi there.. I had a really quick question for anyone that uses the Flash Aid plugin for Firefox...  Is anyone experiencing trouble trying to use it today?  It was working great the other day, but now when I click on:

Firefox >> Tools >> Add-ons >> Extensions >> Flash Aid Preferences

Usually it takes you to a main menu, but today it seems stuck at a window that is asking about the path for the terminal utility/application and something to do with upgrades. It doesn't give the user the same options as before, or allow a user to generate a script to install the actual plugin anymore.

---

### Post by Frogs Hair on 2011-05-30
There have been updates for flash aid , you may want to leave a post for lovinglinux (developer)  on the FF4 mega thread .

I think it only runs when a new version of flash available and if you have the latest version the there is no need to run it . The update option checks for new versions and the option to install flash only appeared when I installed  Flash Aid.

---

### Post by linuxinstalledfromhdd on 2011-05-30
Oh cool. You're right. It's much more streamlined. Thanks.

---

### Post by lovinglinux on 2011-05-30
Hi,

I need some information so I can troubleshoot what is going wrong on your system.

**What version of Flash-Aid you are using?**

**Do you see the Flash-Aid button in Firefox navigation toolbar? **

If no, right-click on any toolbar, select "Customize", locate the button in the Customize dialog and drag it to a Firefox toolbar.

**When you click the Flash-Aid toolbar button, what menu options do you see?**

Let me explain some few changes in the latest version (2.1.1).

The script installer is no longer available from the preferences. It has been moved to different dialogs, because the extension has now 3 different installation modes: wizard, quick and advanced. They can be accessed from the extension toolbar button menu. 

The extension triggers some warnings when it cannot find some stuff it needs, like the path to the terminal. However the Preferences dialog should be accessible any time and should not be affected by those alerts. They are triggered only when you access the extension toolbar button menu. Nevertheless, the warning is displayed only once. After that you can still access the extension button menu, in order to open the Preferences and set the terminal path properly. After you do that, when you click the toolbar button menu, the installation modes menus will be available.

---

### Post by linuxinstalledfromhdd on 2011-05-30
It works great. I thought the screen was stuck on the first window that came up, but my flash was already updated to the latest version.  Thanks :)

---

### Post by lovinglinux on 2011-05-30
> **linuxinstalledfromhdd said:**
> It works great. I thought the screen was stuck on the first window that came up, but my flash was already updated to the latest version.  Thanks :)

The extension doesn't work only when flash is not updated. You should be able to use it any time, so please confirm if you can see the button in the toolbar and if you can see the Wizard option in the menu?

---

### Post by linuxinstalledfromhdd on 2011-05-30
I downgraded to the previous version from your firefox add-on page. And the wizard comes up fine now.

---

### Post by lovinglinux on 2011-05-30
> **linuxinstalledfromhdd said:**
> I downgraded to the previous version from your firefox add-on page. And the wizard comes up fine now.

I am more confused now, because the version on my web page is the latest one (2.1.1). What version is displayed in the Add-on Manager?

---

### Post by linuxinstalledfromhdd on 2011-05-30
Yeah, that's the one.  It works great.  No issues. :)

[http://www.youtube.com/watch?v=XluKcRSlXAw](http://www.youtube.com/watch?v=XluKcRSlXAw)

Thanks for the plugin too.  Going to make a donation.

---

### Post by lovinglinux on 2011-05-30
> **linuxinstalledfromhdd said:**
> Yeah, that's the one.  It works great.  No issues. :)

[http://www.youtube.com/watch?v=XluKcRSlXAw](http://www.youtube.com/watch?v=XluKcRSlXAw)

Thanks for the plugin too.  Going to make a donation.

You are welcome and thanks.

BTW, I just watched several Star Wars movies again this week :-)

I need to finish the The Empire Strikes Back.

---

### Post by linuxinstalledfromhdd on 2011-05-30
That's the best one of them all! 

Use the force.:popcorn:

---

### Post by lovinglinux on 2011-05-30
> **linuxinstalledfromhdd said:**
> That's the best one of them all! 

Use the force.:popcorn:

:-)

---

### Post by Frogs Hair on 2011-05-30
The options appear when I add the button to the tool bar on 2.1.1 . I didn't notice because I don't keep that one on the visible once flash is installed.

---

### Post by Frogs Hair on 2011-05-30
> **lovinglinux said:**
> You are welcome and thanks.

BTW, I just watched several Star Wars movies again this week :-)

I need to finish the The Empire Strikes Back.

There is an episode 1-3 marathon on one of the cable stations today .

---

