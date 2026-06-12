---
title: "blank video playback ubuntu 10.04"
date: 2010-05-08
forum: General Help
---

### Post by m4tic on 2010-05-08
i cant get video playback on a computer with sis 741 graphics. I get sound but video is blank, only appears if i right click where the window should be, if i remove the right click menu, sometimes the video shows but with a blank spot where the menu was. I noticed this on the live cd while opening the example content, but carried on with the install anyway. Right now i have no ability of playing videos, previous releases where fine but they were this way only when i had metacity on. But on 10.04 whether metacity is on or off, same blank screen.

---

### Post by lereveur on 2010-05-09
I'm also having this problem. I hope someone can help us. Sometimes I can get the video to show completely but I haven't figured out the exact sequence of things to do yet. I know in 9.10 I had to add commands to get 1280 x 1024 resolution. However, I removed those commands during the upgrade.

---

### Post by lereveur on 2010-05-09
I decided to try something that I used to have to do prior to 9.10. Voila! I got the video playback problem fixed! Now someone might want to figure out why. Try the following to see if it works for you:

[LIST=1]
[*]System --> Preferences --> Multimedia Systems Selector
[INDENT]If it's not there, you'll have to enable it by editing the menus.[/INDENT]
[*]Click on the "Video" tab.
[*]In the "Default Output" section, select "X Window System (No Xv)" for the "Plugin".
[/LIST]

---

### Post by m4tic on 2010-05-09
hi thanks i will try it someday but i've already moved to Mandriva. I downloaded Mandriva One 2010 and its working great, i recommend.

---

### Post by foripepe on 2010-10-07
It works fine for me. Thanks.

---

### Post by SuporteTecnicoID on 2010-11-16
> **lereveur said:**
> I decided to try something that I used to have to do prior to 9.10. Voila! I got the video playback problem fixed! Now someone might want to figure out why. Try the following to see if it works for you:

[LIST=1]
[*]System --> Preferences --> Multimedia Systems Selector
[INDENT]If it's not there, you'll have to enable it by editing the menus.[/INDENT]
[*]Click on the "Video" tab.
[*]In the "Default Output" section, select "X Window System **(No Xv)**" for the "Plugin".
[/LIST]

Thank you, this is solution for my video error....in my Linux KDuXP, congratulations....

**(No Xv)** :popcorn:

---

