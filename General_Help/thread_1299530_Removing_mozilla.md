---
title: "Removing mozilla"
date: 2009-10-24
forum: General Help
---

### Post by Orbegoso on 2009-10-24
I want to completely remove/uninstall anything mozilla/firefox related(including folders, addons etc.). We had a huge fight. Seriously though, anyone know a quick commands to do this? Thanks.

---

### Post by Ravernomina on 2009-10-24
```
sudo apt-get purge firefox
```

---

### Post by Orbegoso on 2009-10-24
> **Ravernomina said:**
> ```
sudo apt-get purge firefox
```
That didn't work completely, it only removed a couple of items. I think it might me because I have mozilla firefox instead of the ubuntu verison of firefox.

---

### Post by Ravernomina on 2009-10-24
thats a high chance why.... try this



sudo apt-get purge mozila-firefox

---

### Post by Orbegoso on 2009-10-24
> **Ravernomina said:**
> thats a high chance why.... try this



sudo apt-get purge mozila-firefox


That didn't work either, I'm still able to alt+f2 firefox, any other ideas?
You spelled mozilla wrong, btw, that wasn't the problem.

---

### Post by Ravernomina on 2009-10-24
if your typing in that code that means ur launching the ubuntu firefox :l

---

### Post by rockstarrem on 2009-10-24
What about this...

```

sudo apt-get remove firefox --purge

```

Try mozilla-firefox if that doesn't work.

---

### Post by Orbegoso on 2009-10-24
> **Ravernomina said:**
> if your typing in that code that means ur launching the ubuntu firefox :l
I searched "firefox" under installed programs under add/remove nothings there, plus if thats true shouldn't your first command have gotten rid of firefox?

---

### Post by Orbegoso on 2009-10-24
> **rockstarrem said:**
> What about this...

```

sudo apt-get remove firefox --purge

```Try mozilla-firefox if that doesn't work.
Thanks, but that didn't work for either of them. I think I might just try doing it manually.

---

### Post by rockstarrem on 2009-10-24
Alright, sorry about that. Post your results.

---

### Post by Orbegoso on 2009-10-24
> **rockstarrem said:**
> Alright, sorry about that. Post your results.

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package mozilla-firefox is not installed, so not removed
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
```

Same thing for both of them.

---

### Post by rockstarrem on 2009-10-24
No I meant your results with the manual uninstallation :P not sure how your going to do it.

---

### Post by Orbegoso on 2009-10-24
> **rockstarrem said:**
> No I meant your results with the manual uninstallation :P not sure how your going to do it.

Oh lol, I'm just going to try tomorrow, getting late.

---

### Post by Evontroy on 2009-10-24
Just use the Synaptic Package Manager to remove Mozilla Firefox. I've went from Firefox to Google Chrome and use Synaptic Package Manager to COMPLETELY remove Firefox.

---

### Post by tommcd on 2009-10-24
Open a terminal and run:
```
aptitude search firefox
```
This will return a list of everything with firefox in it's name from the Ubuntu repos. A "p" before the package means it is not installed. An "i" before the package means it is installed. So remove with apt-get anything with firefox that has an "i" before the package name.
On my clean install of Ubuntu 9.10 I have these firefox packages:
firefox
firefox-3.0
firefox-3.0-branding
firefox-3.5
firefox-3.5-branding
firefox-3.5-gnome-support
firefox-gnome-support
You will also have a .mozilla directory in your home directory that will have your firefox profile and user settings for firefox in it.

---

### Post by lovinglinux on 2009-10-24
> **rockstarrem said:**
> What about this...

```

sudo apt-get remove firefox --purge

```

Try mozilla-firefox if that doesn't work.

There is no such thing as mozilla-firefox package.

> **Orbegoso said:**
> I searched "firefox" under installed programs under add/remove nothings there, plus if thats true shouldn't your first command have gotten rid of firefox?

> **Evontroy said:**
> Just use the Synaptic Package Manager to remove Mozilla Firefox. I've went from Firefox to Google Chrome and use Synaptic Package Manager to COMPLETELY remove Firefox.

It seems the OP has installed Firefox package downloaded from Mozilla web site, so it won't show up in Synaptic and can't be removed with apt-get commands. 

> **Orbegoso said:**
> Oh lol, I'm just going to try tomorrow, getting late.

Look if you have a folder /opt/firefox. If yes, then delete it:

```
sudo rm -R /opt/firefox
```

If you wanna get rid of extensions, passwords, bookmarks and all personal things related to Firefox, then do this:

```
rm -fr ~/.mozilla/firefox
rm -fr ~/.mozilla/firefox-3.5
```

To restore the original Firefox go to Synaptic and install firefox-3.0 if it is not installed or re-install it. This will ensure the correct links are created for launchers if you have changed that when installed Firefox from Mozilla.

Next time you install something without using the package manager, please write down the steps used to install the application, so you can revert what you did without guessing how to remove the application.

If you want to properly install Firefox 3.5 and optimize Firefox to have a good experience, see [Firefox optimization and troubleshooting thread](http://ubuntuforums.org/showthread.php?t=1193567).

---

