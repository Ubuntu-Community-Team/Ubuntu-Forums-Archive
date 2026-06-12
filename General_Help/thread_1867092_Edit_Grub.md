---
title: "Edit Grub"
date: 2011-10-22
forum: General Help
---

### Post by kakashi_12 on 2011-10-22
I've done this before, but never used this distro before. For some reason, I'm having issues. Startup Manager does not allow me to edit the text and Ubuntu Tweak I don't believe is compatible with Lubuntu. So I guess I'm stuck editting it manually.

I can't find menu.lst , so I'm guessing I have GRUB 2. Which makes things more difficult. Hmmm.... which file am I suppose to edit again?

---

### Post by Xanthomryr on 2011-10-22
You need to edit the file:
```
/etc/default/grub
```

After you edited /etc/default/grub run:
```
update-grub
```
to write the changes to /boot/grub/grub.cfg.

/edit: Here some more and deeper infos: [https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

---

### Post by kakashi_12 on 2011-10-22
I'm definately having issues with my OS I think. I tried to edit and first of all, the file does NOT allow me to edit names of the OS's. I can remove Recovery Entries. That's it. Secondly, here are the errors in the terminal.

kakashi12@Sentia:~$ cd ..
kakashi12@Sentia:/home$ cd ..
kakashi12@Sentia:/$ ls
bin    dev   initrd.img  media  proc  sbin     sys  var
boot   etc   lib         mnt    root  selinux  tmp  vmlinuz
cdrom  home  lost+found  opt    run   srv      usr
kakashi12@Sentia:/$ cd etc
kakashi12@Sentia:/etc$ cd default
kakashi12@Sentia:/etc/default$ ls
alsa          bootlogd       cups    halt        locale   pulseaudio  ufw
apport        cacerts        dbus    irqbalance  nss      rcS         useradd
avahi-daemon  console-setup  devpts  kdm.d       ntp      rsync       winbind
bluetooth     cron           grub    keyboard    ntpdate  rsyslog
kakashi12@Sentia:/etc/default$ sudo gedit grub
[sudo] password for kakashi12: 

(gedit:2238): Gtk-WARNING **: Theme parsing error: gtk-buttons.css:159:10: Expected valid border

(gedit:2238): Gtk-WARNING **: Theme parsing error: gtk-bars.css:102:16: Themeing engine 'adwaita' not found

(gedit:2238): Gtk-WARNING **: Theme parsing error: gtk-bars.css:117:16: Themeing engine 'adwaita' not found

(gedit:2238): Gtk-WARNING **: Theme parsing error: gtk-bars.css:134:16: Themeing engine 'adwaita' not found

(gedit:2238): Gtk-WARNING **: Theme parsing error: gtk-bars.css:153:16: Themeing engine 'adwaita' not found

(gedit:2238): Gtk-WARNING **: Theme parsing error: gtk-bars.css:165:16: Themeing engine 'adwaita' not found

(gedit:2238): Gtk-WARNING **: Theme parsing error: gtk-bars.css:175:16: Themeing engine 'adwaita' not found

(gedit:2238): Gtk-WARNING **: Theme parsing error: gtk-bars.css:186:16: Themeing engine 'adwaita' not found

(gedit:2238): Gtk-WARNING **: Theme parsing error: gtk-bars.css:198:16: Themeing engine 'adwaita' not found

(gedit:2238): Gtk-WARNING **: Theme parsing error: gtk-bars.css:208:16: Themeing engine 'adwaita' not found

(gedit:2238): Gtk-WARNING **: Theme parsing error: gtk-bars.css:218:16: Themeing engine 'adwaita' not found

(gedit:2238): Gtk-WARNING **: Theme parsing error: gtk-bars.css:223:16: Themeing engine 'adwaita' not found

(gedit:2238): Gtk-WARNING **: Attempting to store changes into `/root/.local/share/recently-used.xbel', but failed: Failed to create file '/root/.local/share/recently-used.xbel.JOYW3V': No such file or directory

(gedit:2238): Gtk-WARNING **: Attempting to set the permissions of `/root/.local/share/recently-used.xbel', but failed: No such file or directory

(gedit:2238): Gtk-WARNING **: Attempting to store changes into `/root/.local/share/recently-used.xbel', but failed: Failed to create file '/root/.local/share/recently-used.xbel.JJP33V': No such file or directory

(gedit:2238): Gtk-WARNING **: Attempting to set the permissions of `/root/.local/share/recently-used.xbel', but failed: No such file or directory

(gedit:2238): Gtk-WARNING **: Attempting to store changes into `/root/.local/share/recently-used.xbel', but failed: Failed to create file '/root/.local/share/recently-used.xbel.G9EZ3V': No such file or directory

(gedit:2238): Gtk-WARNING **: Attempting to set the permissions of `/root/.local/share/recently-used.xbel', but failed: No such file or directory
kakashi12@Sentia:/etc/default$ update-grub
grub-mkconfig: You must run this as root
kakashi12@Sentia:/etc/default$ sudo update-grub
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-3.0.0-12-generic
Found initrd image: /boot/initrd.img-3.0.0-12-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Microsoft Windows XP Professional on /dev/sda1
done

---

### Post by robbielink on 2011-10-22
I'm getting these same knd of error messages when I try to edit a file in terminal via sudo. For example:

"Gtk-WARNING **: Attempting to store changes into `/root/.local/share/recently-used.xbel', but failed: Failed to create file '/root/.local/share/recently-used.xbel.N8T23V': No such file or directory"

and

"(gedit:8270): Gtk-WARNING **: Attempting to set the permissions of `/root/.local/share/recently-used.xbel', but failed: No such file or directory"

I was able to save the edited grub file - terminal showed these error messages after I closed gedit.

---

### Post by WorMzy on 2011-10-22
You should use gksudo, not sudo, for graphical applications like gedit. But in any case, those are just warnings, and can be safely ignored.

---

### Post by utnubuuser on 2011-10-22
is it gksudo or gksu?

---

### Post by WorMzy on 2011-10-22
Either or. By default, gksu is the same as gksudo. But in the event that it becomes misconfigured, gksu requires the root account's password, rather than your own. If that happens, you can always fix it by running gksu-properties and setting it to use sudo, rather than su, as a back-end.

---

### Post by kakashi_12 on 2011-10-22
Ok. Well anyways, back to the original issue. Why can't I edit grub?

.... i always thought about using lilo, by the way.

---

### Post by KingYaba on 2011-10-22
> **kakashi_12 said:**
> Ok. Well anyways, back to the original issue. Why can't I edit grub?

.... i always thought about using lilo, by the way.

What do you need to do? Remove a few boot entries? I have, like, a dozen kernel options and it became a bit stupid when I don't use the 2.6... versions. I simply used gedit to remove a few lines. I suggest you backup your grub.cfg file in case you boink something.

sudo cp /boot/grub/grub.cfg ~/Desktop

sudo gedit /boot/grub/grub.cfg

Copy it wherever you want but do be careful.

---

### Post by raja.genupula on 2011-10-22
> **KingYaba said:**
> What do you need to do? Remove a few boot entries? I have, like, a dozen kernel options and it became a bit stupid when I don't use the 2.6... versions. I simply used gedit to remove a few lines. I suggest you backup your grub.cfg file in case you boink something.

sudo cp /boot/grub/grub.cfg ~/Desktop

sudo gedit /boot/grub/grub.cfg

Copy it wherever you want but do be careful.
+1 I support this .Pleae dont go for editing the grub.cfg file . If you wanna do any change to your grub please install grub customizer and then you can do modifications there for grub.

All The Best.

---

### Post by Quackers on 2011-10-23
For some reason I get the same errors on every new installation, and have done now for two releases.
It does matter, in my case at least, as any changes made to a file do not get updated when the `/root/.local/share/recently-used.xbel' error is shown.
I have got around it with a suggestion given by MacUntu which is to run ```
sudo mkdir -p /root/.local/share
``` You can then re-save the edited file without errors and the edits are then actually stored.

I don't know why this is necessary and would have thought that the appropriate directory should be created by default, but for some reason it isn't.

---

### Post by kakashi_12 on 2011-10-23
A few things...

I ran that code (above) in the terminal... but I still get errors. :(
Secondly, what is the command to install Grub Customizer? Because it does not show up when I search for it in Synaptics Package Manager.

And lastly, that file I brought up to edit "grub.cfg" says not to edit because it is made from other files. This happened to me before, I editted the grub file like that on my desktop and it would change itself automatically EVERY time there was an update (or at least every time there was an update to grub) and add lines back in there. Grrr.

---

### Post by robbielink on 2011-10-23
> **kakashi_12 said:**
> A few things...
And lastly, that file I brought up to edit "grub.cfg" says not to edit because it is made from other files. This happened to me before, I editted the grub file like that on my desktop and it would change itself automatically EVERY time there was an update (or at least every time there was an update to grub) and add lines back in there. Grrr.

See post #2 for how to properly edit grub. And be sure to run
"sudo update-grub" when you are done.

I don't think grub.cfg is updated very often by Ubuntu updates and when it is you used to be prompted to keep your old cfg or update to the new one (not sure if this is still true). But you could always save a copy of the file with your changes and then copy and paste the changes to the new file if it does get updated.

---

### Post by kakashi_12 on 2011-10-23
Nvm. Finally got Grub Customizer to install. Found out here...

[http://ubuntuforums.org/showthread.php?t=1664134](http://ubuntuforums.org/showthread.php?t=1664134)

that I needed to add it to my Software Sources for it show in searches.
Thanks guys... if you have time, see my other thread "Lubuntu Issues".

---

