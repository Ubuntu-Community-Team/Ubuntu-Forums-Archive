---
title: "Startup Applications Appear in Duplicate"
date: 2010-05-16
forum: General Help
---

### Post by Random_Dude on 2010-05-16
Well, let's see if I can explain my problem.

I tried to put a terminal in the desktop using more or less the procedure described in this article: [http://www.webupd8.org/2009/05/ubuntu-embed-terminal-into-you-desktop.html](http://www.webupd8.org/2009/05/ubuntu-embed-terminal-into-you-desktop.html)

It worked fine, but then I installed avant-windows-navigator and I think it created some conflicts with compiz and other applications.
Both the desktop terminal and Skype started to appear in duplicate when I logged in. So I went to the startup applications menu and disabled them both. When I logged back in they both appear only once, but the terminal is in the wrong spot in the desktop.
So there are probably some startup registers somewhere that are causing this.

Is there a way to erase them?
I've tried reinstalling compiz and I uninstall AWN and it didn't work.

Cheers :cool:

---

### Post by jetsam on 2010-05-18
Why would you ever want to fix this problem?

You're _complaining_ about getting two for the price of one?

:P:guitar:

---

### Post by colorlessprism on 2010-05-23
im not sure if this will work for you (i use UNE), but when i have duplicate wine entries i can go:
~/.local/share/applications
~/.local/share/desktop-directories
and delete the extra entries. if you are not sure about something make sure and back it up before deleting it. if this does not fix your issue, try using the search option in nautilus and search for the name of the launcher.

---

### Post by dragos240 on 2010-05-23
Try using gconf. You might find something....

---

### Post by jetsam on 2010-05-23
Where is the how to I was promised.

How do I reproduce your bug?

---

### Post by Random_Dude on 2010-05-24
> **colorlessprism said:**
> im not sure if this will work for you (i use UNE), but when i have duplicate wine entries i can go:
~/.local/share/applications
~/.local/share/desktop-directories
and delete the extra entries. if you are not sure about something make sure and back it up before deleting it. if this does not fix your issue, try using the search option in nautilus and search for the name of the launcher.

It's not a wine problem (I think), so the problem isn't probably there.:|

@dragos240
Where exactly in the gconf should I be looking.:confused:

Thanks for the tips. ;)

---

### Post by colorlessprism on 2010-05-24
i understand its not a wine problem i was attempting to relate an issue i had to you. if it were wine related i would have pointed you to:
~/.local/share/applications/[I][B]WINE
[/B][/I]
i havent run a standard desktop environment in over a year now, but it seems like shorcuts are stored in the ~/.local/share/applications directory and ~/.local/share/desktop-directories housed desktop items

---

### Post by Random_Dude on 2010-05-25
> **colorlessprism said:**
> i understand its not a wine problem i was attempting to relate an issue i had to you. if it were wine related i would have pointed you to:
~/.local/share/applications/[I][B]WINE
[/B][/I]
i havent run a standard desktop environment in over a year now, but it seems like shorcuts are stored in the ~/.local/share/applications directory and ~/.local/share/desktop-directories housed desktop items

In ~/.local/share/applications there are two files very similar
> alacarte-made-1.desktop
alacarte-made.desktop   Is it suppose to be two of them?

Thanks.:cool:

---

### Post by colorlessprism on 2010-05-25
there should probably only be one. assuming you named the launcher "alacarte-*" . you could backup the  			 				"alacarte-made-1.desktop" by moving it to a flash drive. you could probably rename it by removing the "desktop" part, but i have found ubuntu to be smart enough from time to time to still know what the file is for, so i resort to putting files in my "crypt" file.

---

### Post by nerdy_kid on 2010-06-22
do you have your gnome session set to auto restore your session on login?  i dont know where the settings for that is (im using KDE :D) but it could cause the problem you are describing.

---

### Post by Random_Dude on 2010-10-13
Well, I no longer have this issue since I just did a fresh install with 10.10. Although, I didn't find a solution anywhere on the internet.
So, does this thread remains open for anyone who has the same issue?

Cheers :cool:

---

