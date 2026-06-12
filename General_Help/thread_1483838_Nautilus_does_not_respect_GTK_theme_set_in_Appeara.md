---
title: "Nautilus does not respect GTK theme set in Appearance"
date: 2010-05-15
forum: General Help
---

### Post by guitarMan666 on 2010-05-15
I have recently experienced an odd issue regarding Nautilus and the GTK theming. No matter what theme is set in the "Appearance" dialog, Nautilus shows the bland default GTK theme with the title bars of the theme set in Appearance.

I think this is related to an error regarding GConf I saw once, but never again. It flashed so quickly on shutdown that I did not have time to note down what it says. This issue effects the desktop as well. Any ideas? Rebooting doesn't fix it and beyond that, I have no clue where to start for an issue like this.

---

### Post by thomas_toscani on 2010-05-15
> **guitarMan666 said:**
> I have recently experienced an odd issue regarding Nautilus and the GTK theming. No matter what theme is set in the "Appearance" dialog, Nautilus shows the bland default GTK theme with the title bars of the theme set in Appearance.

I think this is related to an error regarding GConf I saw once, but never again. It flashed so quickly on shutdown that I did not have time to note down what it says. This issue effects the desktop as well. Any ideas? Rebooting doesn't fix it and beyond that, I have no clue where to start for an issue like this.

Funnily enough.  I'm having the exact same problem.  This problem started happening after a crash that I experienced last night.  

If anyone has any ideas on how to fix it, I would be most grateful.  Thanks!

---

### Post by sidneylopsides on 2010-05-15
I've got this problem too, a search led me to this:

[https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/500417](https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/500417)

Post 22 seems to have a fix, but I'm too new to know how to do it...

I guessed it might be in the root folder, so used terminal to launch Nautilus with sudo, and it loaded with the theme....

I can't find that thing to delete like in the post though

---

### Post by guitarMan666 on 2010-05-16
The fix is actually very simple. It involves removing a folder. The simplest way to accomplish this is to open a terminal and run the following:
```

rm -vr ~/.gconf/apps/nautilus && killall nautilus

```
This command removes the directory /home/yourname/.gconf/nautilus and the files in it giving you written confirmation, and kills the nautilus process IF the delete is successful.

You may find this solution more comfortable as a beginner:
```

rm -vr ~/.gconf/apps/nautilus && sudo reboot

```
Which reboots instead of merely killing the process. This may save any abnormalities that might occur from killing nautilus (like missing desktop icons).

EDIT: First command works flawlessly. No abnormal effects or anything.

---

### Post by sidneylopsides on 2010-05-16
awesome, thankyou! It worked :D

---

### Post by thomas_toscani on 2010-05-16
> **guitarMan666 said:**
> The fix is actually very simple. It involves removing a folder. The simplest way to accomplish this is to open a terminal and run the following:
```

rm -vr ~/.gconf/apps/nautilus && killall nautilus

```This command removes the directory /home/yourname/.gconf/nautilus and the files in it giving you written confirmation, and kills the nautilus process IF the delete is successful.

You may find this solution more comfortable as a beginner:
```

rm -vr ~/.gconf/apps/nautilus && sudo reboot

```Which reboots instead of merely killing the process. This may save any abnormalities that might occur from killing nautilus (like missing desktop icons).

EDIT: First command works flawlessly. No abnormal effects or anything.

Thank you!  Worked for me as well!  :)

---

### Post by sidneylopsides on 2010-05-22
Ok, maybe it didn't work... it keeps going back to the rubbish theme, and it makes noises when it does it! Clicking things makes a noise, it's gets very irritating. 
It works if I do the above, but goes back when I restart.

---

### Post by sidneylopsides on 2010-06-14
*bump*

No one got any ideas? 
This is starting to get annoying now, and I don't want to do an complete reinstall just for a theme problem.

---

### Post by muschiosauro on 2010-06-21
Check if you have a file named gnome-settings-daemon.desktop in your /home/username/.config/autostart folder. If you find it there, just delete it (or, if you don't feel like, just try moving it to another location) and reboot. That solved the problem with me.

---

### Post by sidneylopsides on 2010-06-22
Thanks for the reply, but I don't have that file.

---

### Post by sidneylopsides on 2010-07-17
Reinstalled Ubuntu, it was fine for less than a day, the theme has broken again. 
This time the things suggested before don't work, I can't get the toolbars etc to change at all.

---

### Post by chiriones on 2010-07-24
I renamed ~/.gconf/apps/nautilus and closed all Nautili.  When I reopened Nautilus, the GTk theme was back as usual.

---

### Post by kidknapp on 2010-08-13
> **guitarMan666 said:**
> The fix is actually very simple. It involves removing a folder. The simplest way to accomplish this is to open a terminal and run the following:
```

rm -vr ~/.gconf/apps/nautilus && killall nautilus

```
This command removes the directory /home/yourname/.gconf/nautilus and the files in it giving you written confirmation, and kills the nautilus process IF the delete is successful.

You may find this solution more comfortable as a beginner:
```

rm -vr ~/.gconf/apps/nautilus && sudo reboot

```
Which reboots instead of merely killing the process. This may save any abnormalities that might occur from killing nautilus (like missing desktop icons).

EDIT: First command works flawlessly. No abnormal effects or anything.

The first line worked great but I had to type sudo in front of it to get it to stick.

The last major change I had made was installing Amarok - which uses a slew of KDE libraries. I'm going to reinstall and see if I can recreate the problem on my own or if my hypothesis is wrong and the KDE libraries are not having any conflict with the gnome-settings-daemon...:o

---

### Post by kidknapp on 2010-08-13
For the moment my presupposition was incorrect. The fix sticks!

---

### Post by marbour on 2010-10-29
Hi

I am experiencing the exact same problem with 10.04 fully updated.

Deleting the directory is still the solution for Nautilus reverting to square/ugly theme.

BUT BEWARE: it also deletes all shorcuts and custom config you may have made in Nautilus... Like list view instead of... etc.

Not that big a problem if you have all your shortcuts' users and passwords...

Regards

Marc

---

### Post by Voland on 2010-11-09
I've got this bug too and removing ~/.gconf/apps/nautilus doesn't work. Also I haven't got gnome-settings-daemon.desktop file in ~/.config/autostart folder

---

### Post by nyteryder79 on 2010-12-20
I posted this in another thread as well. I also had this problem in 10.10 x64, but it only started today when I did updates.  I noticed that there was a nvidia-current-modaliases package updated, but I'm running ATI.  Although the modaliases package shouldn't have made a difference, I uninstalled this package and, like magic, my gnome-theme-reset issue is now resolved.  I've done a series of reboots and the issue still has yet to reappear.  May work for others, hope it helps.

TLDR; if you have ATI, remove the Nvidia modaliases package.  Vise-versa if you have Nvidia.

---

### Post by catrincm on 2011-01-03
more discussion in [http://www.ubuntuforums.org/showthread.php?t=1575703](http://www.ubuntuforums.org/showthread.php?t=1575703) although it doesn't seem to provide any solution yet.

---

### Post by alexpennos on 2011-01-04
> **catrincm said:**
> more discussion in [http://www.ubuntuforums.org/showthread.php?t=1575703](http://www.ubuntuforums.org/showthread.php?t=1575703) although it doesn't seem to provide any solution yet.
Since there is no solution there, lets keep this post alive, and when any solution comes up, we could post it here too

---

### Post by alexpennos on 2011-01-09
Update:
I ince executed a 
```
killall nautilus
```

and since then, the problem hasnt appeared... :D
LUCKY!!!

---

### Post by serhinho on 2011-01-12
Hi,

I'm getting the same nasty problem with nautilus and all of the mentioned fixes don't help. I've tried restarting nautilus removing ~/.gconf/nautilus but still no change, until... 

I've killed nautilus and started it with sudo!

for some reason now it appreciates the theme but I don't want to run every piece of soft with sudo just to get some nice looks.

Someone have some ideas what might be the cause??

I'm running Ubuntu 10.10 i686

---

### Post by valids on 2011-03-09
Change Visual Effects to "None"
Log Off then Log On
Check Nautilus theme: should be OK
Change Visual Effects to "Extra"
Check Nautilus theme: should be OK

---

### Post by hnfmr on 2011-03-10
Same problem here. After a reboot, gnome panel appearance can't be set. And overall desktop theme becomes ugly.

Using Maverick 10.10 x86_64

Please help.

---

### Post by zooooz on 2011-03-21
I was wrong. as soon as i reactived compiz, the theme reset to ugly mode again...

the following is not correct i'm afraid
[INDENT][INDENT]had a segfault of gnome-settings due to libc-2.12.1.so
the theme of gnome kept resetting, most notably in the gnome-panel.
started right after upgrading to 10.10

SOLUTION: shut down the experimental settings in chromium:
*GPU Accelerated Canvas 2D
*Composited render layer borders.

works so far. hope, it does for others.[/INDENT][/INDENT]

---

### Post by Duolc on 2011-04-09
I'm having this issue as well.  I have tried all the fixes and nothing sticks... I am getting very fustrated

---

### Post by Krytarik on 2011-04-10
> **Duolc said:**
> I'm having this issue as well.  I have tried all the fixes and nothing sticks... I am getting very fustrated
May it be related to this?:
[http://ubuntuforums.org/showthread.php?t=1575703](http://ubuntuforums.org/showthread.php?t=1575703)

Recent threads with summed-up workarounds:
[http://ubuntuforums.org/showthread.php?t=1722179](http://ubuntuforums.org/showthread.php?t=1722179)
[http://ubuntuforums.org/showthread.php?t=1724702](http://ubuntuforums.org/showthread.php?t=1724702)

Greetings.

---

### Post by demilord on 2011-04-10
TY saved my day

---

### Post by Buzz Knightyear on 2011-05-07
Same with me but im using 11.04 with Unity 2D and this only happens at boot at just at random.

---

### Post by oltio on 2011-05-17
Thank you guys, the workaround above gave me a hint to fix my issues.

Instead of removeing all preferences of Nautilus, you can remove only harmful settings and keep others as they are.

Open ~/.gconf/apps/nautilus/preferences/%gconf.xml with your favorite editor and remove some entries whose names are 'desktop_font', 'theme', 'background_color', 'background_filename', 'background_set', and so on.

Then kill the procss of nautilus and change the desktop theme with "Appearance Preferences". It nicely worked for me.

---

### Post by oltio on 2011-05-17
Gosh, something wrong... Please forget the workaround just above. By the way, the issue I'm attacking is [https://bugs.launchpad.net/ubuntu/+source/gnome-settings-daemon/+bug/649809](https://bugs.launchpad.net/ubuntu/+source/gnome-settings-daemon/+bug/649809)
If you have a problem around appearance/theme, check them out.

---

### Post by chrisgianti on 2012-05-18
> **chiriones said:**
> I renamed ~/.gconf/apps/nautilus and closed all Nautili.  When I reopened Nautilus, the GTk theme was back as usual.

I don't understand what you just said here. You renamed the directory "nautilus" to what? 

Then you closed all folders? Then when you re-opened them it worked?

So far nothing on this thread has worked for me. I ran into the problem when I installed some live wallpapers or desktop themes in synaptics (trying to get live wallpapers). I uninstalled everything that I installed trying to fix this ugly grey theme. But nothing has worked.

---

### Post by Combimux on 2012-06-05
I got the same issue as all above after an update.

All I did to tackle this prob was:
start gnome-editor (Alt + F2 ) go to Apps -> Nautilus -> Preferences -> theme edit this key (has "default" now probably) to your theme of choice. Now open a terminal (Ctrl + Alt + t) and give the command "killall nautilus" Enter.
Start Nautilus the way you normally do and everything should be as normal.

---

### Post by oldos2er on 2012-06-05
Old thread closed. Please, if you have a question, start a new thread. Much has changed with Nautilus and Gnome over the past two years.

---

