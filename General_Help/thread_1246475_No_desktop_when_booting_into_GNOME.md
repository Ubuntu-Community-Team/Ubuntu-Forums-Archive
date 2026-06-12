---
title: "No desktop when booting into GNOME"
date: 2009-08-21
forum: General Help
---

### Post by Mike_IronFist on 2009-08-21
Well, in all my time using Ubuntu, I've never encountered an issue this weird or random. Please read carefully if you intend to help, this problem seems extremely tough.

Just this morning, my Ubuntu installation (I dual boot Ubuntu and Windows) was working fine. Hours later I logged in again, and inexplicably, my entire desktop was gone.

Nautilus wasn't running, there were no panels - all that was there was my wallpaper.

I hit alt + F2 and the "Run" window came up with no border. I ran
```
compiz --replace
```
Which at least gave me window controls. I also launched a terminal to run Nautilus and Cairo Dock. I used Cairo Dock because it gave me access to the menu usually available in the panel.

None of my visible settings were different. So I decided to try and reset GNOME to see if there were settings I didn't know of causing the problem. I dropped to the true terminal and used this command:
```
rm -rf .gnome .gnome2 .gconf .gconfd .metacity
```

When I rebooted, my GNOME settings apparently DID go back to default, but the problem persists.

In other words, I've tried all I know. Please, help me get GNOME working the way it's supposed to again.

---

### Post by tgeer43 on 2009-08-21
> Please read carefully if you intend to helpYes, Sir!

This is just a thought since I've never had the unfortunate experience to have to try it but...

After backing everything up, try firing up Synaptic and have it show you only installed packages. Type 'gnome' in the search box and then mark all (or nearly all) resulting packages for reinstallation.

There's a possibilty that not only might it not fix your problem but it could conceivably make things worse but that's what the backup is for.

tgeer

---

### Post by Mike_IronFist on 2009-08-21
> **tgeer43 said:**
> Yes, Sir!

This is just a thought since I've never had the unfortunate experience to have to try it but...

After backing everything up, try firing up Synaptic and have it show you only installed packages. Type 'gnome' in the search box and then mark all (or nearly all) resulting packages for reinstallation.

There's a possibilty that not only might it not fix your problem but it could conceivably make things worse but that's what the backup is for.

tgeer

Great idea! I'll give it a try.

Any other suggestions whilst I try this?

---

### Post by Baasha on 2009-08-21
I had the same or a similar problem a month ago.  Tried a number of things:

[http://ubuntuforums.org/showthread.php?t=1215933](http://ubuntuforums.org/showthread.php?t=1215933)

Nothing seemed to work, although I would urge you to try them.  In the end, I had to do a complete re-install to get things back to normal.  There is probably a corrupted configuration file somewhere but none of the usual suspects seemed to be it. Sorry I can't be of more help.

---

### Post by Mike_IronFist on 2009-08-21
Well I've done a reinstall of Ubuntu many times, but I'm trying to avoid that kind of annoyance.

Reinstalling gnome-core did not work, by the way.

---

### Post by wojox on 2009-08-21
```
sudo apt-get reinstall ubuntu-desktop
```

That didn't do anything?

---

### Post by Mike_IronFist on 2009-08-21
> **wojox said:**
> ```
sudo apt-get reinstall ubuntu-desktop
```

That didn't do anything?

Nope. Tried that before posting. I should have mentioned it actually.

---

### Post by Mike_IronFist on 2009-08-21
I FIGURED IT OUT!

Apparently a hidden file inside my home folder must have been corrupted.

If any users have this problem, here's what to do to solve it:

1.) Create a new user with admin privileges.

2.) Log in as the new user. The desktop should be there.

3.) Press alt+F2 and a "Run" window will open. In that window, type,
```
gksudo nautilus
```

4.) After entering in your password, a new file browser window will open, with ROOT privileges. Be sure to avoid deleting anything and continue following these instructions.

5.) Go to "Filesystem", click "home", then find the folder with your original username on it.

6.) Move all the files you need from the home folder of the old user to the desktop or home folder of the new user. DO NOT ATTEMPT TO COPY OR MOVE HIDDEN FILES.

7.) Press ctrl+h to reveal the hidden files. Delete everything in the home folder of the old user.

8.) Put the files you moved to the new account back into the home folder of the old account.

9.) Log back into your old username.

10.) You should now have a desktop. You may delete the new user now if you wish.

---

