---
title: "Firefox 1.5.0.1"
date: 2006-02-02
forum: General Help
---

### Post by Protex on 2006-02-02
Hey guys, a new version of Firefox has just been released that solves some memory leak issues.

I was just wondering how to install this? I have Firefox 1.5.0.0 right now, how can I simply update it?

---

### Post by jasplund on 2006-02-02
Yes you can if you have writing-permission to the firefox directory otherwise you have to run firefox as gksudo

j

---

### Post by Protex on 2006-02-02
I'm still fairly new to linux, so how would I go about updating it? Can you give me a step by step? Thanks a lot.

---

### Post by bjweeks on 2006-02-02
It would be best to wait for daper or use backports. Don't use the firefox updater as it is a messy way to do it.

---

### Post by jasplund on 2006-02-02
If you have writing permissions:
Help-->Check for updates

if not start firefox with Alt+F2 and then write gksudo firefox

now try Help-->Check for updates

---

### Post by Protex on 2006-02-02
Alrighty, fair enough.

This may be already out there somewhere, but when is the release date for Dapper?

---

### Post by jasplund on 2006-02-02
Since you write that you're using version 1.5 now I'm assuming that you're not using firefox from any repositories

---

### Post by Protex on 2006-02-02
Aye, Jaslund, I used your suggestion from above and used gksudo and used the Update feature from there.

Thanks a lot!

---

### Post by magnusbb on 2006-02-02
Finally, the problems with menus and dialogs are fixed!

---

### Post by jimbo2150 on 2006-02-02
```
This may be already out there somewhere, but when is the release date for Dapper?
```

I believe the dev area says some time in April.

---

### Post by jimbo2150 on 2006-02-02
[QUOTE=Protex]This may be already out there somewhere, but when is the release date for Dapper?[/QUOTE]

I believe some time in April.

---

### Post by krusbjorn on 2006-02-02
I used the automatic update, and it erased all my settings. Had to configure all extensions, fonts, start pages etc etc. Luckily, the bookmarks were spared.

---

### Post by ronmarley1 on 2006-02-02
I did the Help-->Check for Updates and the only thing I lost was my theme.  Home page and bookmarks are fine.

---

### Post by saubz on 2006-02-02
[QUOTE=jasplund]If you have writing permissions:
Help-->Check for updates

if not start firefox with Alt+F2 and then write gksudo firefox

now try Help-->Check for updates[/QUOTE]


great tip.  thanks

---

### Post by Rellik on 2006-02-02
Yeah, thanks for the tip - I didn't know how to check for updates!

I kept my themes and extensions and bookmarks, but it seems that now going to "Tools->Extensions" or "Tools->Themes" brings up a window that shows nothing but "Key(event);">
---^" in big letters, so that's kind of odd... maybe I'll exiting the session.

EDIT: to my surprise, this worked!

---

### Post by PapaWiskas on 2006-02-02
[QUOTE=jasplund]If you have writing permissions:
Help-->Check for updates

if not start firefox with Alt+F2 and then write gksudo firefox

now try Help-->Check for updates[/QUOTE]

Holy Mackerel.....it worked.....awesome tip indeed....
Thank you.

---

### Post by towsonu2003 on 2006-02-02
[http://wiki.ubuntu.com/FirefoxNewVersion](http://wiki.ubuntu.com/FirefoxNewVersion)
> 
To get firefox's own update/autoupdate to work at all, you have three choices (read them all and choose one):

    1.      Change the /opt/firefox directory to have 'write' permissions & ownership set for the user instead of the root. To change ownership, after installation type:

       sudo chown -R ${USER}:${USER} /opt/firefox
       

      This is the only way to get update notification working, but doing this has security implications in a multi-user environment, and is not recommended: a virus or malicious program running as a user may now replace or corrupt the files in /opt/firefox, which would affect other users of the computer.
    

      2. An alternative to the above method is to run firefox with sudo to get the updates. That is, when there is an update available, you would run sudo firefox -safe-mode (the safe-mode is an extra layer of protection since it will not load any extensions while running as sudo), install the update (Help -> Check for Updates...), close firefox, and then restart firefox as a normal user. You should NOT browse other websites while you are running firefox with sudo. (The author does not know whether this method is any safer/more secure than the first method).
    

      3. A third option, is to use method 1, but only for updates: Keep the firefox folder owned by root and use it normally until you need an update, then give your user ownership: sudo chown -R ${USER}:${USER} /opt/firefox. Start firefox normally and update (Help -> Check for updates...). Once the update is completed, you should restore ownership to root: sudo chown -R root:root /opt/firefox. Again, do NOT browse other sites while firefox has these elevated permissions. This is probably the best option although it is also the most cumbersome.


To backup your profile:
```
cp -R ~/.mozilla ~/.mozilla.backup.1500
```

---

### Post by scrillamaan on 2006-02-03
I just updating Firefox 1.5 with this method and I think I killed it. Seg faults at every attempt.

```
/opt/firefox/run-mozilla.sh: line 131: 11513 Segmentation fault      "$prog" ${1+"$@"}

```

---

### Post by bjweeks on 2006-02-03
[QUOTE=scrillamaan]I just updating Firefox 1.5 with this method and I think I killed it. Seg faults at every attempt.

```
/opt/firefox/run-mozilla.sh: line 131: 11513 Segmentation fault      "$prog" ${1+"$@"}

```[/QUOTE]

You can remove the firefox package and reinstall it. Also it is better to update with apt-get not the firefox updater because your computer still thinks you have 1.0.7 and any update will restore it to its orginal state.

---

### Post by scrillamaan on 2006-02-03
[QUOTE=bjweeks]You can remove the firefox package and reinstall it. Also it is better to update with apt-get not the firefox updater because your computer still thinks you have 1.0.7 and any update will restore it to its orginal state.[/QUOTE]
I used synaptic to remove 1.0.7 and then reinstalled, but I still get sef faults. How do I remove 1.5.0.1?

---

### Post by steve.horsley on 2006-02-03
[QUOTE=scrillamaan]I used synaptic to remove 1.0.7 and then reinstalled, but I still get sef faults. How do I remove 1.5.0.1?[/QUOTE]
Just delete its install directory. 

You may also have to delete your settings file ~/.mozilla/firefox, as it may be an entry in here that's making it segfault. Come to think of it, before de-installing, temporarily rename this directory and try firefox again then, just to see if it's a setting that's upsetting it.

--------------------------------------------------------------------

I just updatad my firefox install by doing the following. This is for people who have firefox installed in a directory owned by root:

Make sure you are in your home directory:
```
cd
```

Make a backup of the mozilla settings folder:
```
tar cf .mozilla.tar .mozilla
```

Run firefox as root and get the update. When it asks if you want to restart firefox, say no you will do it later.
```
sudo firefox
```

Run firefox as root for a second time, to complete the update. When the update is finished, exit firefox again.
```
sudo firefox
```

Now replace the .mozilla settings directory, removing any pesky root-owned files that the update made:
```
sudo rm -rf .mozilla
tar xf .mozilla.tar
rm .mozilla.tar
```

---

### Post by scrillamaan on 2006-02-03
[QUOTE=steve.horsley]Just delete its install directory. 

You may also have to delete your settings file ~/.mozilla/firefox, as it may be an entry in here that's making it segfault. Come to think of it, before de-installing, temporarily rename this directory and try firefox again then, just to see if it's a setting that's upsetting it.
[/QUOTE]

I deleted the settings file and now firefox is working and hasn't segfaulted so far.

Thanks

---

### Post by radioraheem on 2006-02-05
holy cow... 

I ran the gksudo firefox basic command and it updated everything perfectly, including extensions and bookmarks.

Memory usage is way down too :)

great tip

---

### Post by steve.horsley on 2006-02-05
[QUOTE=radioraheem]holy cow... 

I ran the gksudo firefox basic command and it updated everything perfectly, including extensions and bookmarks.

Memory usage is way down too :)

great tip[/QUOTE]

Yes, but the thing that worries me about this is updating the extensions and settings that are in your home directory. The ownership will change to root, and you may not be able to change your settings after that. That's why I said to save and restore .mozilla. However, **sudo chown -r me:me .mozilla** afterwards should fix it too.

---

