---
title: "KDE wallpaper question:"
date: 2006-02-28
forum: General Help
---

### Post by Prospero2006 on 2006-02-28
Ok, check this out:

When I go to 

K-MENU --> Settings --> Control Center --> Appearance and Themes -->
Background

           -The wallpapers I add there and apply don't have any effect on the system. (I never see them show up.)

            -However, when I right click on the desktop and choose configure desktop, I can switch the wallpapers at will. (The new wallpapers apply immediately.)
            -What the hell is going on here. I'm looking for a way to 
              edit the background from a text editor.

                        -Thanks, 
                           Prospero

---

### Post by Jucato on 2006-02-28
That is strange... both ways work fine for me. Would you happen to be running KDE 3.4.x?

As for changing backgrounds from a text editor, you can try checking the ~/.kde/share/confige/kdedesktoprc file

---

### Post by tadashi on 2006-02-28
I ran both 3.4.3 and 3.5.1 and could change my wallpapers in both areas.

---

### Post by Prospero2006 on 2006-02-28
I'm running kde 3.5.1 

Right, I've worked with my ~/.kde/share/config/kdesktoprc, but for some reason 
KDE completely ignores it. I can't figure out for the life of me where it is storing the new backgrounds I apply.

Thanks,
Pros

---

### Post by Jucato on 2006-02-28
Wallpapers downloaded by user are found in ~/.kde/share/wallpapers
Wallpapers installed/downloaded by root are in /usr/share/wallpapers

---

### Post by Prospero2006 on 2006-02-28
That was very good info there, but  ~/.kde/share/config/kdedesktoprc must not be the only file referencing which one is active.

That was a great pointer there.

Thanks, 
Prospero

---

### Post by Jucato on 2006-02-28
Well, I'm not sure if there are any other config files, since most of the local config files are found in ~/.kde/share/config.

But I must say that your problem is really unique. Haven't encountered anyone with that problem... yet. :D

Sorry if I couldn't offer anymore help. That's about all that I know for now.

---

### Post by Prospero2006 on 2006-03-01
For the record:

I rebooted my machine and the ~/.kde/config/share/kdesktoprc 
file lists a different wallpaper than the one that loads on startup.

Also, I log in as root.


time to grep the whole system for the wallpaper reference.

Pros

---

### Post by Jucato on 2006-03-01
Ok now that is REALLY strange. I just changed my background image and checked kdesktoprc. It was updated...

---

### Post by Prospero2006 on 2006-03-01
Here's an update for those of you that have so kindly followed this thread:

I got to work this morning, which is far from my home desktop. 
I've been turning this over in the back of my brain for at least 24 hours.
About 10 minutes ago, it occured to me:
     locate kdesktoprc
/root/share/config/kdesktoprc
/root/.kde/share/config/kdesktoprc both show up

the /root/share/config/kdesktoprc has the wallpaper configured that 
is currently on the desktop. (I'm assuming when I go home and change it, all will be well.) 

Here's the reason why I'm doing this:
    I'm going to write a short shell script that parses through a specific directory, or maybe even goes out to kde-look.org for a random download, every 24 hours. It will rewrite the file with the new background, kill the X session, and restart it. That way when I get home from work, I'll have a wallpaper of the day.

-I'd like to do the same with themes and widget sets, but I figure I'd start simple.

Pros

---

### Post by Jucato on 2006-03-01
There is an option in the Background configuration to have a sort of slideshow with the wallpapers, and you can set it to change after how many minutes (or hours, too, I guess). I don't know if it works with online images.

The only problem I see with the scripting that you will do is that if you manually change the kdesktoprc, you would have to restart the X session for it to take effect (I think). If it does this automatically, what would happen if some important processes were running in the background?

Could it also be possible that the reason for your problem is that there are two kdesktoprc? I tried searching my system and didn't find any in /root/share/config. How about trying to delete/rename that file and see if it solves your problem? Of course, back it up first. :D

EDIT: I don't know how this affects things, but I found another kdesktoprc in /usr/share/kubuntu-default-settings/kde-profile/default/share/config/

---

### Post by GeneralZod on 2006-03-01
[QUOTE=Prospero2006]
Here's the reason why I'm doing this:
    I'm going to write a short shell script that parses through a specific directory, or maybe even goes out to kde-look.org for a random download, every 24 hours. It will rewrite the file with the new background, kill the X session, and restart it. That way when I get home from work, I'll have a wallpaper of the day.
[/QUOTE]

No need to restart X or KDE or anything - wallpaper can be changed to any file on your drive from a script with a simple dcop call :) I'm away from my KDE machine at the moment; I'll see if I can elaborate on this when I get back home :)

Edit:

Or search this page for dcop - it gives you the call to use.  In your script, you will have to have a 

```

export DISPLAY=<your display id here>

```

before the dcop call - you can work out your display id just by calling 

```

echo $DISPLAY

```

in a konsole.

---

### Post by Jucato on 2006-03-01
Oh yeah, DCOP completely slipped my mind (how ironic, as dcop is what I'm browsing when I posted my previous response.)

I'll be waiting for your info, to add to my dcop research :D
(OT: General Zod, do you know of some good DCOP tutorials/manuals/guides?)

---

### Post by GeneralZod on 2006-03-01
[QUOTE=Fenyx]
(OT: General Zod, do you know of some good DCOP tutorials/manuals/guides?)[/QUOTE]

Afraid not; I only know the bits and pieces I've picked up on my travels :) I assume you know about kdcop, the dcop browser? Also, a fun fact - there is dcop bash completion available, which is very handy!

---

### Post by Jucato on 2006-03-01
Yep, I know a bit of dcop and have been using kdcop. (I've made a keyboard shortcut that will display the K Menu wherever my  mouse is :D ) But I've been looking for the command that would refresh the desktop background after kdesktoprc is changed manually (through a text editor or script). I guess I'll have to wait for your input. :D

OT: I just woke up after a very uncomfortable sleep (I have a fever and it's still 4 a.m. here). Guess what I was dreaming about? DCOP, Superkaramba, and KDE. \\:D/

---

### Post by emuman on 2007-09-01
> **Prospero2006 said:**
> Ok, check this out:

When I go to 

K-MENU --> Settings --> Control Center --> Appearance and Themes -->
Background

           -The wallpapers I add there and apply don't have any effect on the system. (I never see them show up.)

            -However, when I right click on the desktop and choose configure desktop, I can switch the wallpapers at will. (The new wallpapers apply immediately.)
            -What the hell is going on here. I'm looking for a way to 
              edit the background from a text editor.

                        -Thanks, 
                           Prospero

I have the same problem. Any solution?

---

