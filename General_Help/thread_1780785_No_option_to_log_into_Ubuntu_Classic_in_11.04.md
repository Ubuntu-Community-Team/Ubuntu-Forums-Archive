---
title: "No option to log into Ubuntu Classic in 11.04"
date: 2011-06-12
forum: General Help
---

### Post by elementia on 2011-06-12
Hey all, I recently did a fresh install of 11.04 and decided to poke around with GNOME 3. Long story short it wasn't my cup of tea so I reverted with ppa-purge. Now, Unity isn't my cup of tea either so I like to use Gnome Classic but for some reason now I only have the options of Unity (Ubuntu) and Ubuntu Classic (No effects). Before I installed GNOME 3 I was able to log into Ubuntu Classic (with effects) just fine. 

I'm an average linux user, not pro but not completely nub so I would prefer to find a way of fixing this without re-installing Ubuntu if possible. Any help would be appreciated!

---

### Post by sikander3786 on 2011-06-12
Welcome to the forums :)

Might be, the 'ubuntu-desktop' package got removed or some of its dependencies while you installed Gnome3. Any case, reinstalling that package might help.

Get to Terminal and:

```
sudo apt-get install --reinstall ubuntu-desktop
```

---

### Post by elementia on 2011-06-12
No such luck. My only options are still Unity and Ubuntu Classic (no effects).

However, thank you for your time.

EDIT: Hmmm. I just got exactly what I wanted by logging in with User Defined Session, opening terminal and running "gnome-panel". Obviously this isn't the ideal solution but it's a start.

---

### Post by Frogs Hair on 2011-06-12
Unless it has changed , the Gnome 3 PPA was supposed to break Gnome 2.xx and required  a clean installation to get it to work right again.

---

### Post by elementia on 2011-06-12
Well using ppa-purge you are able to revert back to GNOME 2.xx. I'm not having any problem running GNOME 2 right now, my issue is that my login options are limited to Unity and Ubuntu Classic with no effects. I can't load Ubuntu classic with effects unless I go to User Defined Session, open terminal and run 'gnome-panel&' 

As I said this is not the ideal solution for me because this computer is plugged into the TV in the living room and my girlfriend and roommates use this as a media center. They don't have the technical know-how to do anything in terminal. 

I apologize is I wasn't as clear and concise as I should have been before I hope this cleared up any misunderstanding.

---

### Post by sikander3786 on 2011-06-12
Run this command in Terminal:

```
ls -l /usr/share/gnome-session/sessions
```

If 'classic-gnome.session' isn't listed, create it by:

```
gedit /usr/share/gnome-session/sessions/classic-gnome.session
```

And paste this text in the file that opens up:

```
[GNOME Session]
Name=Classic GNOME
Required=windowmanager;panel;filemanager;
Required-windowmanager=gnome-wm
Required-panel=gnome-panel
Required-filemanager=nautilus
DefaultApps=gnome-settings-daemon;
IsRunnableHelper=/usr/lib/nux/unity_support_test --compiz
FallbackSessionsID=GNOME2d
GNOME2d=2d-gnome
```

If the 'gnome.session' file is also missing, do this:

```
gedit /usr/share/gnome-session/sessions/gnome.session
```

And paste the text from the attached file.

Reboot and test.

---

### Post by elementia on 2011-06-12
Wow I was sure that what you just posted would have worked, but when I did the ls on /usr/share/gnome-session/sessions, sure enough classic-gnome.session is there and the contents are exactly what you said they should be.

Thank you though, I honestly thought that was it.

---

### Post by sikander3786 on 2011-06-12
Lets try purging and re-installing GDM then.

```
sudo apt-get remove --purge gdm
```

```
sudo apt-get install gdm
```

---

### Post by elementia on 2011-06-12
Beautiful! It worked! Thank you so much.

---

