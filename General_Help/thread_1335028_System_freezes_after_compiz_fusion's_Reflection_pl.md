---
title: "System freezes after compiz fusion's Reflection plugin unabled and cant boot back"
date: 2009-11-23
forum: General Help
---

### Post by PullusPardus on 2009-11-23
hi all.
my ubuntu doesn't seem to boot into the desktop at all after i enabled the "Reflections" plugin from Compiz Fusion it only goes into the desktop and freezes there can't even move the mouse or turn off compiz.

so i searched around and tried booting from the terminal via the recovery mode (before booting click ESC and then select recovery mode, then select the first option and type in your login and password)

i also tried turning off compiz by using the metacity code but it didn't work.

is there a way to boot in a safe mode without having to use compiz? 

thanks in advance!

---

### Post by PullusPardus on 2009-11-23
sorry i meant Enabled not Unabled in the thread title.

---

### Post by PullusPardus on 2009-11-23
bump seriously need help on this , my computer is completly unuseable.

---

### Post by baytuni on 2009-11-23
ok. I have the same problem. Now I am searching the file which ccsm (advanced compiz settings) keeps the settings. If you or I can find it then you can boot from a live cd and disable reflection plugin on that file.

---

### Post by baytuni on 2009-11-23
ok here is my workaround for this problem
if you rename the folder "reflex" in both
```
~/.gconf/apps/compiz/plugins/
      ~/.gconf/apps/compizconfig/plugins/  
```

It makes ccsm to ignore reflex. so X starts correctly.

---

### Post by PullusPardus on 2009-11-23
> **baytuni said:**
> ok. I have the same problem. Now I am searching the file which ccsm (advanced compiz settings) keeps the settings. If you or I can find it then you can boot from a live cd and disable reflection plugin on that file.

how exactly do you disable it from a live CD? , i tried going on the package manager and removing it completely but its still there. 

and where should i have this code? 

~/.gconf/apps/compiz/plugins/
      ~/.gconf/apps/compizconfig/plugins/
thanks =]

---

### Post by baytuni on 2009-11-23
actually you do not require live cd. if you press ctrl+alt+f1 just before the lock down you can reach tty1. enter your user name and password. then 

```
$ cd .gconf/apps/compiz/plugins/
      $ mv ./reflex ./reflex_bak
      $ cd ~/.gconf/apps/compizconfig/plugins/
      $ mv ./reflex ./reflex_bak 
      $ sudo shutdown -r now
```

and cross your fingers :D

---

### Post by PullusPardus on 2009-11-23
> **baytuni said:**
> actually you do not require live cd. if you press ctrl+alt+f1 just before the lock down you can reach tty1. enter your user name and password. then 

```
$ cd .gconf/apps/compiz/plugins/
      $ mv ./reflex ./reflex_bak
      $ cd ~/.gconf/apps/compizconfig/plugins/
      $ mv ./reflex ./reflex_bak 
      $ sudo shutdown -r now
```

and cross your fingers :D

i am typing that not copying it the first part worked, but the MV ./reflex one it says 
"mv : cannot stat './reflex' no such file or directory.

weird because it does exist on my computer

---

### Post by baytuni on 2009-11-23
sorry my mistake remove both "./" just type 
```
mv reflex reflex_bak
```

---

### Post by PullusPardus on 2009-11-23
> **baytuni said:**
> sorry my mistake remove both "./" just type 
```
mv reflex reflex_bak
```

it still says "no such file or directory" for reflex.

i think i might have to do it the live CD way, how do i do that ?

---

### Post by baytuni on 2009-11-23
no it does not require live cd at all. just make sure that you follow the steps in that order. However I am not sure which version of compiz you have. the trick is to rename the folder named "reflex " in your home folder. so if you type 

```
locate reflex
```

it will tell you where it is. There should be many of them. just make sure rename the ones that are inside /compiz and /compizconfig

---

### Post by PullusPardus on 2009-11-23
> **baytuni said:**
> no it does not require live cd at all. just make sure that you follow the steps in that order. However I am not sure which version of compiz you have. the trick is to rename the folder named "reflex " in your home folder. so if you type 

```
locate reflex
```

it will tell you where it is. There should be many of them. just make sure rename the ones that are inside /compiz and /compizconfig

gotcha.

it says these

```
/home/ppardus/.cache/compizconfig/reflex.pb
/usr/lib/compiz/libreflex.a
/usr/lib/compiz/libreflex.la
/usr/lib/compiz/libreflex.so
/usr/share/ccsm/icons/hicolor/scalable/apps/plugin-reflex.svg
/usr/share/compiz/reflex.xml
/usr/share/gconf/schemas/compiz-reflex.schemas
```

---

### Post by baytuni on 2009-11-23
I really don't know pallus. I think it depends on the versions etc. you should wait for a wiser one than me. but this solution worked for me that's all I know.

---

### Post by PullusPardus on 2009-11-23
> **baytuni said:**
> I really don't know pallus. I think it depends on the versions etc. you should wait for a wiser one than me. but this solution worked for me that's all I know.

dont worry, you were a great help =]

---

### Post by ximatz on 2009-11-24
I just had the same problem. My system froze after activating the compiz reflections plug-in. I found on the forum another thread were two solutions were proposed:
[http://www.uluga.ubuntuforums.org/showthread.php?p=8339875](http://www.uluga.ubuntuforums.org/showthread.php?p=8339875)

I didn't try the second one, because the first one worked for me.
This is what I did:

1. On the GRUB menu select the standard option and not the recovery mode to start Ubuntu.
2. Once on the Ubuntu log in screen select you user only, do not enter your password or log in to GNOME.
3. Three combo-boxes appear on the bottom of the log in screen after selecting the user: language, keyboard and sessions.
4. Select the option "Failsafe GNOME" on the sessions combo-box.
5. Now enter your password and log in

Now you should be able to go to System-> Preferences -> CompizConfig Settings Manager and deactivate the problematic plug-in from there. Once deactivated, you should be able to log out from the failsafe session and log in with the normal standard session without freezing.

I hope this helps you.
Good luck!

---

### Post by itsjustarumour on 2009-12-04
If anyone on this thread is having problems and uses Intel graphics, its possible you're being affected by this bug:

[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/298532](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/298532)

---

### Post by Geraba on 2009-12-06
I was afflicted by this problem too...
I tried to use Failsafe-GNOME, but it locked up... I guess it was just bad luck, but anyway...
I booted in recovery mode, entered root prompt, and used:

```
locate reflex
```

to find where the config files where...
I went to 

/usr/share/compiz/reflex.xml
/usr/share/gconf/schemas/compiz-reflex.schemas
and renamed both files to something else... Rebooted, and it worked!
Before this, I also tried to uninstall compiz via recovery prompt... It kinda worked, but when I logged in GNOME, it was REALLY sluggish... And eventually locked up again...

---

