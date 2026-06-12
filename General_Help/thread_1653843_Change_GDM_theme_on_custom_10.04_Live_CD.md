---
title: "Change GDM theme on custom 10.04 Live CD"
date: 2010-12-27
forum: General Help
---

### Post by DavidRaid on 2010-12-27
Hi, I've been working on a custom live CD for some time, it's a heavily altered and tweaked version of 10.04 Lucid Lynx.

I am near to completion and the only thing I have left to change is the look of my GDM login screen. I just want to change the font it uses and the theme to elementary, I intend to keep the icon theme as it is.

I have the contents of my filesystem.squashfs file accessable but I can't for the life of me find where GDM saves its theme information. I know it can be changed because you can make Appearance Preferences pop-up at login and change these things, there are also tools like GDM2Setup that let you do this, but I can't figure out how that does it either.

I've looked at all the files in /var/lib/gdm and /etc/gdm and flicked through my gconf-editor. While there are signs of config files in hidden folders inside /var/lib/gdm, I can't find a way to make these the default in my liveCD. Copying the .gconf folder into the gdm folder on the livecd (which didn't exist there) did nothing, nor did copying the contents of the .gconf folder into the .gconf.defaults folder on the livecd.

Does anyone know where Ubuntu stores the default appearance settings for GDM?

Thanks!

---

### Post by elmanuelito on 2011-01-15
If you are using locate
$locate gdm 
should give you some locations.

I don't use gdm, but it seems I have some leftovers of a badly purged gdm install here: 
/usr/share/gdm/greeter-config/

---

### Post by fret669 on 2011-01-22
I haven't been able to change the gdm theme... but I've been looking for the same thing. if you download "gdm2setup" and have a look at the python scripts, it has sent me in the right direction.

So far I've made "/usr/share/images/xsplash/"
Then I place my background in there. I've only tried this on my actual system so I don't know if it will work for the live cd or not. At least you'd be able to change the background to something a little nicer.

---

### Post by Spr0k3t on 2011-01-22
To change the theme add gnome-appearance-properties to GDM's autostarted applications:
```
sudo cp /usr/share/applications/gnome-appearance-properties.desktop /usr/share/gdm/autostart/LoginWindow/
```

Log out. Select a new theme/wallpaper/font. Log in and remove gnome-appearance-properties to GDM's autostarted applications:
```
sudo rm /usr/share/gdm/autostart/LoginWindow/gnome-appearance-properties.desktop
```

Here's an example of what I created for one user
[http://ubuntuforums.org/attachment.php?attachmentid=161733&stc=1&d=1277673655](http://ubuntuforums.org/attachment.php?attachmentid=161733&stc=1&d=1277673655)

Here's the key, the settings are changed for the user "gdm"... good place to look for configs if you ask me.

---

### Post by fret669 on 2011-01-22
As far as I know, you can't get to the login screen in your chroot. I found the config files for gdm. /var/lib/gdm/

That folder is GDM's home folder. Enable hidden files and edit it just like you would your own settings.

Or you could use gdm2setup to change your own login, then copy /var/lib/gdm/* to /Ubuntu_path/var/lib/gdm/*

I just got it to work. Once I copied my files into the gdm home directory, i had to chmod 777 everything or else it wouldn't load.

---

### Post by DavidRaid on 2011-01-23
@Spr0k3t

That's the method I referenced in my first post. :p 
> I know it can be changed because you can make Appearance Preferences pop-up at login and change these things, there are also tools like GDM2Setup that let you do this, but I can't figure out how that does it either.

As I said, I'm not trying to change the GDM theme of my Ubuntu system, I'm trying to change it for a custom 10.04 LiveCD.

Unfortunately, after searching the contents of the filesystem.squashfs file (I extracted it to make more modifications) I can't find a GDM user. It's my belief that this is actually created during the installation process and doesn't exist beforehand.

In the end, I went the long and complicated method of replacing the Ambiance theme with an edited elementary one and left it in that folder and I replaced the default Ubuntu wallpaper with my own, so that GDM was forced to use it. This has worked well, though it has meant I needed to edit the theme file so it would still identify itself in Appearence Properties as elementary and not Ambiance, after the folder. It also meant I needed to change the wallpaper config file to account for this. 

I then added the default Ambiance theme as a second theme, including the 10.10 one as well while I was at it. :p

---

### Post by fret669 on 2011-01-23
I know :P i realized after i posted it. I have gotten my themes to work on the livecd by using gdm2setup to make my host's login the way I want it, then copying everything important in /var/lib/gdm to $Mod_Path/var/lib/gdm in squashfs. The only catch is that I have to chmod them, and every time i do, I ruin my ability to sudo. I'll probably end up doing what you did, because I'm getting tired of constantly rebuilding the squashfs and iso :P

---

### Post by DavidRaid on 2011-01-24
If it makes you feel better, my process is longer. I'm running 10.10, and the live USB creator on Maverick is incompatible with Lucid 10.04. 

So after making the filesystem.squashfs file (which as you know takes ages to build) and after swapping the old one for it inside my iso and saving that) I have to then wait for it to copy over to my external hard drive so that I can then wait for it to copy onto my netbook and then wait for it to make the live USB so I can finally test it. Since my netbook is the only thing I have still running Lucid.

---

### Post by fret669 on 2011-01-25
Wow yeah :o That is quite a long process. It'll be worth it once you get it working though ;) I have no experience forcing application versions, but could you force Maverick to run Lucid's USB creator?

I did get the login changed in the end though. It was also a good opportunity to learn some more about Ubuntu.

---

