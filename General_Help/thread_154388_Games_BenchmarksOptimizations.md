---
title: "Games Benchmarks/Optimizations?"
date: 2006-04-03
forum: General Help
---

### Post by Intangir on 2006-04-03
I recently installed Ubuntu Dapper Drake. I play alot of world of warcraft and after trying it in Ubuntu.. i am a bit disappointed ;) i was hoping someone would know some good ways to optimize this

Check out my benchmarks for world of warcraft on Ubuntu, Gentoo (with cedega) and Windows

my system is a 2.2Ghz Athlon(64bit) with 1 gig of ram and a Geforce 6800 GT (256 Mb) PCI-express

My ubuntu setup is:
Dapper Drake flight5 (32bit)
Kernel 2.6.15 (default)
Cedega (5.0.3 and 5.1.1 both did about the same)
Nvidia driver 8178
(most everything is default install, default settings)

My Gentoo setup is:
2005.0 or .1? (64bit) (like 6 month old install barely updated)
Kernel 2.6.12 (recompiled very light)
Cedega (5.0.3)
Nvidia driver 6629 (old..)

Windows setup is..
Windows 2000, all the SPs and patches available
whatever the newest nvidia driver is for windows..

I got framerates while standing in the same 3 spots on all 3 setups, one looking out over the water, one looking toward a city with trees and water in it (auberdine) and one looking straight at the ground outside of town

now the framerates:

Ubuntu:
Water: 40
Town: 30
Ground: 80

Gentoo:
Water: 55-60
Town: 37
Ground: 90-95

Windows:
Water: 90
Town: 75
G: 90-100


there are some differences here with drivers i dont know if thats the problem? or if its some other issues with ubuntu processes running or what
does anyone know any easy effective ways to increase the framerate?

i heard something about a bug on the latest version of the nvidia drivers but i was told it only effected AGP cards, i have PCIe
i like how userfriendly ubuntu is, and how you dont have to compile everything you download ;) so if there is a way i can optimize it more for games that would be great

anyway thanks

---

### Post by Intangir on 2006-04-03
I did even more benchmarks

i used this program called GL O.B.S.
[http://globs.sourceforge.net/](http://globs.sourceforge.net/)

here are the results: (i dont really know what these really mean, they seem like fairly weak tests) (U = my ubuntu install, G = my gentoo install)

GL_pointz:
U: 1476
G: 1263

GL_shadow:
U: 1440
G: 1503

GL_blit
U: 2584
G: 3016

Fake (this might actually have some relevancy testing cpu)
U: 220610
G: 11421858 (i have 64bit build on this so it probably has an unfair advantage)

GL_blit_ext:
U: 2578
G: 2989

GL_smoke:
U: 832
G: 863


ALso i ran glxgears on both ;)
U: 12608
G: 13309

------------

I dont know if its just the different between 32bit to 64.. or the driver difference, or the distro difference, or a mix

the globs test really dont show a whole lot of a difference on most of the tests.. these tests are weak though

i might try and install quake or something on these and use that to test

---

### Post by mlalkaka on 2006-04-03
One thing you could do is run the game directly from GDM (or a light-weight window manager such as Blackbox). This may provide you with better performance. 

**Running the game directly from GDM**
Create a file called WorldOfWarcraft.desktop (or something similar) in /usr/share/xsessions. The contents of the file should be as follows:
```

[Desktop Entry]
Encoding=UTF-8
Name=World of Warcraft
Comment=World of Warcraft
Exec=**<COMMAND_TO_RUN_WORLD_OF_WARCRAFT>**
Terminal=False
TryExec=**<COMMAND_TO_RUN_WORLD_OF_WARCRAFT>**
Icon=**<PATH_OF_WORLD_OF_WARCRAFT_ICON>**
Type=Application

[Window Manager]
SessionManaged=true

```

Replace all instances of **<COMMAND_TO_RUN_WORLD_OF_WARCRAFT>** and **<PATH_OF_WORLD_OF_WARCRAFT_ICON>** in the above example with the appropriate information. Note that once <COMMAND_TO_RUN_WORLD_OF_WARCRAFT> exits, you will be logged off.

Once you have saved this file, you can log out. At the GDM login screen, open the "Session" dialog and voila - your World of Warcraft session should appear as an option. Select that session, click "OK", and log in. WoW will/should run automatically. 
I did this for Unreal Tournament 2004, although the developers made the Unreal series natively compatible with GNU/Linux.

**Running the game through Blackbox**
Blackbox is a "lean" window manager that takes up less memory than most window managers. You can install it from the Ubuntu software repositories (you may need to use the universe repository). Once, that is done, simply choose Blackbox from the "Session" dialog prior to logging in. Blackbox will start up in less than a second; run your game from inside Blackbox.

I think you should also pass the -opengl argument to the wine command that runs WoW. For example "wine WoW.exe -opengl". This may improve performance since OpenGL is natively compatible on GNU/Linux. I know you can do this with the original Wine (from [www.winehq.org)](www.winehq.org)), but I'm not sure whether the same applies for Cedega.

I hope this helps.
By the way, could you please tell me what your results were? Just reply to this thread. Thanks :-D .

---

### Post by Intangir on 2006-04-03
i will try it

---

### Post by Intangir on 2006-04-03
ok i found the problem it was the cedega config.. it was using the wrong one

the one i edited wasnt the one it was using, once i put in the same edits as on gentoo it gets basically the exact same framerates

the only difference now is my sound (cedega doesnt seem to use alsa correctly?, oss worked though) and the mouse flickers when it moves

---

