---
title: "How can I change the default file manager in GNOME?"
date: 2010-12-13
forum: General Help
---

### Post by Rytron on 2010-12-13
Hi.

How can I change the default file manager in GNOME?

I've got these notes but neither methods work:

**_GUI_** 

Change under 'Session control' in 'Ubuntu Tweak'
Delete nautilus and type in pcmanfm or another file manager such as thunar
Apply
Quit ubuntu-tweak
Reboot

-------

**_TERMINAL_**

```
gksu gedit /usr/share/applications/nautilus-folder-*handler.desktop
```

Then replace 'nautilus --no-desktop %U' to whatever you like. Example: pcmanfm %U

Save, logout & login

Update: This works. Why does the Ubuntu Tweak method not work though?
```
sudo gedit /usr/share/applications/nautilus-folder-*handler.desktop
```

---

### Post by tajiknomi on 2010-12-13
[SIZE=2]Yes..

You can edit > /usr/share/applications/nautilus-folder-handler.desktop

Once you opened it , replace "***--no-desktop %U***" with "***dolphin***[/SIZE][SIZE=2]"

In this case, i had change it to Dolphine...you can select your desire..
[/SIZE]

---

### Post by apollothethird on 2010-12-13
> **tajiknomi said:**
> [SIZE=2]Yes..

You can edit > /usr/share/applications/nautilus-folder-handler.desktop

Once you opened it , replace "***--no-desktop %U***" with "***d3lphin***[/SIZE][SIZE=2]"

In this case, i had change it to Dolphine...you can select your desire..
[/SIZE]

Is there a way to do this on a per user base rather than making all the users change?

-- L. James

-- 
L. D. James
[email]ljames@apollo3.com[/email]
[www.apollo3.com/~ljames](www.apollo3.com/~ljames)

---

### Post by tajiknomi on 2010-12-13
> **apollothethird said:**
> Is there a way to do this on a per user base rather than making all the users change?

-- L. James

-- 
L. D. James
[EMAIL="ljames@apollo3.com"]ljames@apollo3.com[/EMAIL]
[www.apollo3.com/~ljames]("http://www.apollo3.com/%7Eljames")

[SIZE=2]Sorry for that, i Don't know about this that how to do this for current User only.......[/SIZE]

---

### Post by Rytron on 2010-12-13
> **tajiknomi said:**
> [SIZE=2]Sorry for that, i Don't know about this that how to do this for current User only.......[/SIZE]

Good question. As far as I know this method will affect all users.


> Originally Posted by tajiknomi View Post
Yes..

You can edit > /usr/share/applications/nautilus-folder-handler.desktop

Once you opened it , replace "--no-desktop %U" with "d3lphin"

In this case, i had change it to Dolphine...you can select your desire..

Hi.
d3lphin / Dolphine - do you mean **dolphin**?

---

### Post by tajiknomi on 2010-12-13
> **Rytron said:**
> Hi.
d3lphin / Dolphine - do you mean **dolphin**?

[SIZE=2]I didn't tried it, but i think this is for Dolphin-File-manager, [/SIZE]

[SIZE=2]But one thing i ***noticed***[/SIZE], [SIZE=2]When i placed an icon of Dolphin on my DESKTOP, the Command come out to be > "***dolphin %i -caption "%c" %u***"[/SIZE],

[SIZE=2]Please ***correct*** me ,if i am missing something[/SIZE]....

---

### Post by Rytron on 2010-12-13
> **tajiknomi said:**
> [SIZE=2]I didn't tried it, but i think this is for Dolphin-File-manager, [/SIZE]

[SIZE=2]But one thing i ***noticed***[/SIZE], [SIZE=2]When i placed an icon of Dolphin on my DESKTOP, the Command come out to be > "***dolphin %i -caption "%c" %u***"[/SIZE],

[SIZE=2]Please ***correct*** me ,if i am missing something[/SIZE]....

'dolphin' is the correct term.

---

### Post by redryder749 on 2010-12-13
i dont think it should affect the other users because nautilus is not uninstalled. but im not the expert. give it a try. you can always get nautilus back.
what the second method does is to use PCmanfm in place of nautilus. you can still open stuff with nautilus. either open nautilus through the terminal or through alt+F2 command.
although you do lose the windows "My Computer" style directory for some reason. the icon says that the file doesnot exist. i wish i could fix that. and then i would definitely use PCmamfm. 
but for everything else its fine and fast.

to get nautilus back replace all the previous steps command with nautilus instead of pcmanfm. and uninstall pcmanfm.

---

### Post by tajiknomi on 2010-12-13
![SIZE=2]
[/SIZE]

---

### Post by tajiknomi on 2010-12-13
> **Rytron said:**
> 'dolphin' is the correct term.

[SIZE=2]Ok so now i had Edited:-

[B][I]Exec=dolphin %u,
[/I][/B]
Nothing happens,although i had log-off, log-in...

Update:- i had use "u" as LOWER-CASE, which is Wrong, i had tried "***U***"as upper-case, and now its fine....;)
[/SIZE]

---

### Post by apollothethird on 2010-12-13
> **redryder749 said:**
> i dont think it should affect the other users because nautilus is not uninstalled. but im not the expert. give it a try. you can always get nautilus back.
what the second method does is to use PCmanfm in place of nautilus. you can still open stuff with nautilus. either open nautilus through the terminal or through alt+F2 command.
although you do lose the windows "My Computer" style directory for some reason. the icon says that the file doesnot exist. i wish i could fix that. and then i would definitely use PCmamfm. 
but for everything else its fine and fast.

to get nautilus back replace all the previous steps command with nautilus instead of pcmanfm. and uninstall pcmanfm.

When you have to use su or sudo to make a chance, you can almost be certain that it's a system wide change and not a per-user change.  A regular user can't make a chance to the files in /usr/share folders.  Almost all files that are components of a per-user configuration is in a hierarchy of their "~" directory and can be changed without elevated access.  When that is available, that's almost always the best way.  That way, if something goes wrong with the changes and experiments it's easy to remove the local files and resort to the system wide default that should still work.

-- L. James

-- 
L. D. James
[email]ljames@apollo3.com[/email]
[www.apollo3.com/~ljames](www.apollo3.com/~ljames)

---

