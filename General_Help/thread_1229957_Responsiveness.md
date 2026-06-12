---
title: "Responsiveness"
date: 2009-08-02
forum: General Help
---

### Post by LoneWolfJack on 2009-08-02
Ok, here's the thing: just a few minutes ago I booted one of my other machines that I haven't used for months. It's an ancient 1,4GHz Athlon with Win 2k on it.

What struck me was the responsiveness of that system. All menus are lightning fast, in fact, I could probably get 10 or 15 minutes of additional work time a day out of that alone if ubuntu was equally fast.

I don't run compiz for the fact that it slows down ubuntu even more.

So now having been reminded of the lightning fast interface of Win 2k I want that for ubuntu, too. 

Don't get me wrong, it's not that ubuntu is that much slower, but when I click the start button on that win2k system for exaple, the menu pops up instantly without any noticable delay. in ubuntu, it has a delay of about 0,2-0,3 seconds. 

this carries on for the entire interface, nautilus for example, is painfully slow compared to windows explorer on the windows machine. for example, loading a directory that contains about 800 mp3 files takes less than a second to load in win2k but about 20 (!) in ubuntu. could it be nautilus is trying to retrieve id tags from all the files or something like that?

bottom line... how to I improve responsiveness on ubuntu if that's at all possible?

---

### Post by kerry_s on 2009-08-02
win2k was the best version, designed to be speedy an low resource. there is no linux comparison, but as with all windows things do eventually slow down with time and use.

to get that kind of performance you can try using lighter programs.
instead of gnome try xfce4, you can try a window manager if you want to go even lighter.
instead of nautilus, pcmanfm or thunar.
instead of gedit, leafpad or mousepad
etc...

---

### Post by snowpine on 2009-08-02
Ubuntu's not the fastest distro for "ancient" hardware--give something like Puppy, DSL, or SliTaz a try. Those distros load entirely into ram (assuming you have enough; 256mb is plenty) so they are very responsive.

---

### Post by LoneWolfJack on 2009-08-02
> 
instead of gnome try xfce4, you can try a window manager if you want to go even lighter.


I was considering trying another DE, but never tried because I actually use this machine for work... can't spend an entire day backing up and reinstalling if something goes wrong.

is there any tutorial for installing another DE? and wouldn't I lose all the gnome programs along with gnome?

> instead of nautilus, pcmanfm or thunar.

pcmanfm appears to have trouble with utf-8 file names (at least this is what the description says if I read it correctly), but thunar looks promising, will investigate. thanks for the tip.

> instead of gedit, leafpad or mousepad

In fact, I actually like gedit after getting used to it. :)

> Ubuntu's not the fastest distro for "ancient" hardware

perhaps I was a bit unclear in this regard. I'm running ubuntu on a dual xeon 3,8GHz with 4GB ram and a U320 scsi raid 0. ok, the machine is about 3 years old now but still I wouldn't call it ancient. :)

---

### Post by snowpine on 2009-08-02
> **LoneWolfJack said:**
> perhaps I was a bit unclear in this regard. I'm running ubuntu on a dual xeon 3,8GHz with 4GB ram and a U320 scsi raid 0. ok, the machine is about 3 years old now but still I wouldn't call it ancient. :)

SliTaz would fly on those specs; check it out. :)
Another good option would be Arch with a fast windows manager like Openbox.

---

### Post by kerry_s on 2009-08-03
> I'm running ubuntu on a dual xeon 3,8GHz with 4GB ram and a U320 scsi raid 0. 

:shock: and it feels slow? you should try a faster distro like debian testing. [http://cdimage.debian.org/cdimage/daily-builds/daily/arch-latest/amd64/iso-cd/](http://cdimage.debian.org/cdimage/daily-builds/daily/arch-latest/amd64/iso-cd/)
thats the 64bit version. the xfce4 install is in the advanced section in the boot selection menu.

i'm using debian testing on 450mhz 256mb & it runs faster then the win2k sp3 i had on it before. so you must be doing something wrong. :D

---

### Post by XCan on 2009-08-03
> **LoneWolfJack said:**
> I was considering trying another DE, but never tried because I actually use this machine for work... can't spend an entire day backing up and reinstalling if something goes wrong.

is there any tutorial for installing another DE? and wouldn't I lose all the gnome programs along with gnome?


You can easily install xfce using
```
sudo apt-get install xfce4
```

This will enable you to choose xfce in the login window. You won't lose any of your currently installed program, to be honest, this may be considered a curse. Since speed gains may be small if it still needs to load tons of libs (especially those belonging to KDE). But since it's so easy, it should be worth a try.

---

### Post by CatKiller on 2009-08-03
> **LoneWolfJack said:**
>  I don't run compiz for the fact that it slows down ubuntu even more.

Actually, if it's set up correctly it makes the computer **more** responsive, since the manipulation of windows is offloaded to the GPU, freeing the processor for other things. The animations default to taking too long, though, which makes it all appear slow. And animations that can't be done in the graphics hardware need to be done on the processor, which makes it slow again.

It's the same with the menu. The first time you use it, it caches the entries from all the disparate locations which takes some time. The next time you use it, it works quickly. There are animations for that, too, which you can turn off.

You might find that you do better with a lighter window manager or file manager, but it's still possible to configure the default to be faster.

---

### Post by LoneWolfJack on 2009-08-03
> i'm using debian testing on 450mhz 256mb & it runs faster then the win2k sp3 i had on it before. so you must be doing something wrong

well, I'm running the 64 bit version... also, it's not that ubuntu is really slow... it's just slower than win2k...

As for file managers, I tried both, thunar and pcman. 
nautilus:
20 seconds to display the aforementioned folder with 800 mp3 files
thunar:
about 5 seconds
pcman:
as fast as win2k (<1 sec), which is probably due to being multithreaded. utf-8 file names also work.

so the filemanager problem might be solved... added pcman to quicklaunch and will try getting used to it. will have to see if issues come up with it.

I might give xfc a shot later today.

---

