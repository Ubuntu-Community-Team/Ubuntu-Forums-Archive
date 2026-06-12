---
title: "Firefox AND Thunderbird freeze EVERY time in Oneiric 11.10"
date: 2011-10-17
forum: General Help
---

### Post by blackdalek on 2011-10-17
Yesterday I upgraded to 11.04 Natty. That was a huge failure, whole system would lock up the instant I logged in.
I was able to boot up into recovery mode and from there I made it upgrade to Oneiric 11.10 to see if that fixed anything. That was another big mistake. Same problem - whole system locks up dead after login.
I then found out how to install gnome-session-fallback so that I could choose classic gnome desktop with no effects at login.
Now I can login, and most apps will run... but not any of the Mozilla stuff (Thunderbird or Firefox).
If I try to launch either of these, the mouse pointer continues to move for 2 seconds, then the entire system freezes dead. No keyboard or mouse movement/response.
I've tried completely removing both apps and reinstalling them. Same result - dead computer.
Does anyone else have this problem and is there a fix?
11.10 has crapped all over my email access and I need to get it back up.
I've searched this forum and google for an answer. This is NOT random or unpredictable freezing like many other people have been experiencing - This is predictable guartanteed freezing at application launch EVERY time.

---

### Post by hwttdz on 2011-10-17
You can try resetting your mozilla settings by moving .mozilla and .thunderbird to different folder names.

---

### Post by lovinglinux on 2011-10-18
Try starting Firefox in safe mode:

```
firefox -safe-mode
```
If it works, then most likely is an extension, plugin or theme causing the problem.

However, since both Firefox and Thunderbird are failing, I suppose the problem might be somewhere else. Try to open Firefox from terminal and report if you get any errors:

```
firefox
```

---

### Post by blackdalek on 2011-10-18
> **hwttdz said:**
> You can try resetting your mozilla settings by moving .mozilla and .thunderbird to different folder names.
Where do I find these?



> **lovinglinux said:**
> Try starting Firefox in safe mode:

```
firefox -safe-mode
```
If it works, then most likely is an extension, plugin or theme causing the problem.

However, since both Firefox and Thunderbird are failing, I suppose the problem might be somewhere else. Try to open Firefox from terminal and report if you get any errors:

```
firefox
```

I can't start firefox using safe mode. Whole system freezes dead before anything even loads.

Can't get anything from running in a terminal. Whole system freezes before anything happens.

---

### Post by lovinglinux on 2011-10-18
> **blackdalek said:**
> Where do I find these?

Try to create a new profile instead of deleting the one you have.

You can do that with this command:

```
firefox -P
```

If that command doesn't work, then you problem is not in the profile.

> **blackdalek said:**
> I can't start firefox using safe mode. Whole system freezes dead before anything even loads.

Can't get anything from running in a terminal. Whole system freezes before anything happens.


You can't run any commands or you can't just start applications or just Firefox and Thunderbird?

---

### Post by blackdalek on 2011-10-18
Ok, I found the .mozilla and .thunderbird folders.

I moved them to a new location. This allowed both Thunderbird and Firefox to launch without problems. However this also lost all my bookmarks/passwords etc in Firefox and lost all my email and account settings in Thunderbird. aaaargh!!

I deleted the newly created .mozilla and .thunderbird and moved the originals back to the home folder. Remarkably, after doing this both Thunderbird and Firefox were still able to open without killing my machine. And I got all my info/passwords/etc back.

However don't get your hopes up. As soon as I reboot the computer, the freezing problem came back. Now I am back at square 1.
It seems the only way I can use Firefox or Thunderbird is to move the .mozilla and .thunderbird folders, start the apps, exit them, move the hidden folders back, restart the apps... then if I need to reboot the computer for any reason, I have to do the whole process again. :(

---

### Post by lovinglinux on 2011-10-18
> **blackdalek said:**
> Ok, I found the .mozilla and .thunderbird folders.

I moved them to a new location. This allowed both Thunderbird and Firefox to launch without problems. However this also lost all my bookmarks/passwords etc in Firefox and lost all my email and account settings in Thunderbird. aaaargh!!

I deleted the newly created .mozilla and .thunderbird and moved the originals back to the home folder. Remarkably, after doing this both Thunderbird and Firefox were still able to open without killing my machine. And I got all my info/passwords/etc back.

However don't get your hopes up. As soon as I reboot the computer, the freezing problem came back. Now I am back at square 1.
It seems the only way I can use Firefox or Thunderbird is to move the .mozilla and .thunderbird folders, start the apps, exit them, move the hidden folders back, restart the apps... then if I need to reboot the computer for any reason, I have to do the whole process again. :(

Rename the folders again. Start Firefox to create a clean profile. Close it then copy *places.sqlite*, *signons.sqlite* and *key3.db* to the new profile. This will give you bookmarks and passwords. The settings are stored in *prefs.js*, but test Firefox before copying it.

For Thunderbird, copy *singons.txt*, *key3.db*, *prefs.js*, *history.mab*, *abook.mab*  and the folders *mail* and *imap*.

If you want to copy more stuff see:

[http://kb.mozillazine.org/Profile_folder_-_Thunderbird#Files](http://kb.mozillazine.org/Profile_folder_-_Thunderbird#Files)

[http://kb.mozillazine.org/Profile_folder_-_Firefox#Files](http://kb.mozillazine.org/Profile_folder_-_Firefox#Files)

Keep in mind one of these files or folder will cause the problem, so it is recommended to copy one by one and test Firefox and Thunderbird to determine the culprit.

---

### Post by blackdalek on 2011-10-18
> **lovinglinux said:**
> You can't run any commands or you can't just start applications or just Firefox and Thunderbird?

Just can't start Firefox or Thunderbird without it freezing. When starting from terminal the system freezes up before anything even outputs to the terminal. The cursor flashes on the line immediately after the command is entered, then stops flashing when the system freezes at about 2 seconds later.

> **lovinglinux said:**
> Rename the folders again. Start Firefox to create a clean profile. Close it then copy *places.sqlite*, *signons.sqlite* and *key3.db* to the new profile. This will give you bookmarks and passwords. The settings are stored in *prefs.js*, but test Firefox before copying it.

For Thunderbird, copy *singons.txt*, *key3.db*, *prefs.js*, *history.mab*, *abook.mab*  and the folders *mail* and *imap*.

If you want to copy more stuff see:

[http://kb.mozillazine.org/Profile_folder_-_Thunderbird#Files](http://kb.mozillazine.org/Profile_folder_-_Thunderbird#Files)

[http://kb.mozillazine.org/Profile_folder_-_Firefox#Files](http://kb.mozillazine.org/Profile_folder_-_Firefox#Files)

Keep in mind one of these files or folder will cause the problem, so it is recommended to copy one by one and test Firefox and Thunderbird to determine the culprit.

I will have a go at that later today when I have more time.
Thanks for helping.

---

### Post by jan1001 on 2011-10-26
I'm also having problems with Firefox and Thunderbird.

Firefox freezes on start, displaying only white window. Cannot close. Has to be killed.

I'm using 2D Unity.

Any news on the subject?

---

### Post by lovinglinux on 2011-10-27
> **jan1001 said:**
> I'm also having problems with Firefox and Thunderbird.

Firefox freezes on start, displaying only white window. Cannot close. Has to be killed.

I'm using 2D Unity.

Any news on the subject?

I suppose your video card doesn't support Unity 3D. Looks like more a video card issue than Firefox itself. Unfortunately, I can't reproduce the problem. Have you tried starting Firefox from terminal and in safe mode?

---

### Post by elefthera on 2011-11-01
I have the same problem as the OP. Worrying to find my problem on a thread that's not resolved...

For the record, it's an old PC with an old Nvidia card (GeForce MX 400, or similar); wiped the HD and made fresh install of 11.10. All seems fine except launching Firefox causes a system freeze. Haven't tried Thunderbird yet. Launching from a terminal spews several repeats of this message:

(firefox:2248): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

...then lockup.

I have tried the trick of renaming .mozilla before launching, but that didn't work for me. I did try installing Chromium - runs fine.

This shouldn't be this difficult - and I bet we aren't the only ones with the problem. Any ideas/advice most welcome.

---

### Post by Rodnox on 2011-11-05
In most cases, the Problem is solved by installing the following package: 

sudo apt-get install gtk2-engines-pixbuf

unfortunately, in my case it didn't do the trick. 


I also had to disable "Ad-Block Plus".

rund FF from terminal in safe mode

sudo firefox --safe-mode

disable all addons and run in safe mode. Now remove Ad Block, close FF and restart normal. 

should work finde now

---

### Post by elefthera on 2011-11-09
> **Rodnox said:**
> In most cases, the Problem is solved by installing the following package: 

sudo apt-get install gtk2-engines-pixbuf
<snip>
disable all addons and run in safe mode. Now remove Ad Block, close FF and restart normal. 


Tried that - no joy.

SOME success came from following this thread:

[https://support.mozilla.com/en-US/kb/Could%20not%20initialize%20the%20browser%20security%20component](https://support.mozilla.com/en-US/kb/Could%20not%20initialize%20the%20browser%20security%20component)

In my case, since it was a virgin install, lack of disk space was NOT the problem, but resetting the Default user profile fixed it, to the point of letting me launch a session and browse. But, the problem returned on the next launch - which suggests the problem lies in Firefox corrupting profile data when it tries to save at the end of a session.

---

### Post by blackdalek on 2011-12-12
well... I found more than just the mozilla apps were freezing, so I gave up on Oneiric completely and went back to Maverick. That fixed everything.

---

