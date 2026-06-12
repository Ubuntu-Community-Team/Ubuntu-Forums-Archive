---
title: "Custom sound events in 9.10."
date: 2009-10-24
forum: General Help
---

### Post by ./BlackHawk on 2009-10-24
Hi,
    I was wondering how to add custom sounds to different events in Ubuntu 9.10. For example, when a download from firefox or a file transfer has finished it would play a sound, or when the system prompts me for a password. Does anyone have any ideas on how to do this?

Thanks.

---

### Post by Johnny B on 2009-10-24
theres an addon called "download statusbar" that will do this for file downloads
im not sure about when the system prompts though, i'll have to look into that.

---

### Post by Mosdarkrai on 2009-11-18
Is there a way to customize the system sound preferences?
It used to be easy on Jaunty, but now I can't figure out how to change the system sounds :(.

---

### Post by BrMBr on 2009-11-19
Karmic is a crap!

They took off login screen config, they took off custom sounds... I hate Karmic! :mad:

---

### Post by ./BlackHawk on 2009-11-20
You can still change the system sound preferences, but not using a config editor, you will have to do it manually.

Open up a terminal and type:
**sudo nautilus**
Type in your password and hit enter. This will bring up root's file browser.

On the side, click on 'File System' then, usr > share > sounds > ubuntu > stereo.
These are the sounds the system uses for the login, question, error sounds etc.

Just simply replace the files with your own, making sure that they have the exact same name or else they won't work. They also have to be 'ogg'.
This program will convert the files to ogg for you:
**sudo apt-get install soundconverter**

If you find the sound you want to use, for this example, the login sound, copy it to your desktop, change the name to 'desktop-login', then, using the root's file browser, drag the file to the ubuntu sounds folder, replacing the original.

Hope this helps :).

---

### Post by musarraf172 on 2009-12-08
I am facing a different problem. If I change the sound theme nothing changes . It play the default sounds only. Recently karmic does not play the log in and log out sound.. Anybody having idea?? how to solve it??
Please help..

---

### Post by DJ_Peng on 2009-12-20
> **./BlackHawk said:**
> You can still change the system sound preferences, but not using a config editor, you will have to do it manually.

Open up a terminal and type:
**sudo nautilus**
Type in your password and hit enter. This will bring up root's file browser.

On the side, click on 'File System' then, usr > share > sounds > ubuntu > stereo.
These are the sounds the system uses for the login, question, error sounds etc.

Just simply replace the files with your own, making sure that they have the exact same name or else they won't work. They also have to be 'ogg'.
This program will convert the files to ogg for you:
**sudo apt-get install soundconverter**

If you find the sound you want to use, for this example, the login sound, copy it to your desktop, change the name to 'desktop-login', then, using the root's file browser, drag the file to the ubuntu sounds folder, replacing the original.

Hope this helps :).
Thanks for posting this. It seems that they've really taken GNOME's no-configuration-dialog philosophy to an extreme. 

[PotentiallyOT]It's also looking like they're planning on taking the logon/logoff sounds out completely for fedora if I'm reading [this]("https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/214370/comments/42") correctly (actually the notice is just above comment #43). At least there is a [workaround for getting the logout sound working again]("https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/214370/comments/45"), although I haven't tested it yet.[/PotentiallyOT]

---

### Post by dcstar on 2009-12-20
> **DJ_Peng said:**
> Thanks for posting this. It seems that they've really taken GNOME's no-configuration-dialog philosophy to an extreme. 

[PotentiallyOT]It's also looking like they're planning on taking the logon/logoff sounds out completely for fedora if I'm reading [this]("https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/214370/comments/42") correctly (actually the notice is just above comment #43). At least there is a [workaround for getting the logout sound working again]("https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/214370/comments/45"), although I haven't tested it yet.[/PotentiallyOT]

I would speculate that the actual problem of the Gnome system not actually running the logout sound got confused with all the Pulseaudio issues, and this is why it has dragged on for so long.

It is a pity that users of 9.10 upwards cannot (easily) specify their own sound events any longer - this seems a backward step and is actually a bit embarrassing when people switch over from another OS that has this basic feature.

---

### Post by Yellow Pasque on 2009-12-21
Did they remove the system/event sound editor from the new sound dialog? You can always install the old one:
> One can still run the old gnome-sound-properties with a couple of files. The attached file has 32bit/x86 and 64bit/x86-64 versions of the gnome-sound-properties program. Move the appropriate version of this file to /usr/local/bin and move the sound-properties.glade (this file is not architecture-dependent) to /usr/share/gnome-control-center/glade/ (you'll probably need to create this directory).
[http://launchpadlibrarian.net/33491183/soundproperties.tar.gz](http://launchpadlibrarian.net/33491183/soundproperties.tar.gz)

---

### Post by DJ_Peng on 2009-12-21
Thanks for the info, Temüjin. Should we select wav's or ogg's with that dialog. I don't get any sound previews using either format.

---

### Post by Yellow Pasque on 2009-12-21
.ogg should work. Can you play an .ogg from the command line, e.g.:
```
canberra-gtk-play --file=/usr/share/sounds/ubuntu/stereo/bell.ogg
```
Maybe you have to install the libcanberra-pulse package if it's not already installed.

---

### Post by DJ_Peng on 2009-12-21
I have that package installed but running your command returns an error.
> ~$ canberra-gtk-play --file=/usr/share/sounds/ubuntu/stereo/bell.ogg
Gtk-Message: Failed to load module "gnomenu-panel": libgnomenu-panel.so: cannot open shared object file: No such file or directoryThe file definitely exists but it won't play. :(

---

### Post by DJ_Peng on 2009-12-21
I have that package installed but running your command returns an error.
> ~$ canberra-gtk-play --file=/usr/share/sounds/ubuntu/stereo/bell.ogg
Gtk-Message: Failed to load module "gnomenu-panel": libgnomenu-panel.so: cannot open shared object file: No such file or directoryThe file definitely exists but it won't play. :(

---

### Post by Yellow Pasque on 2009-12-21
You've got me stumped as to why libcanberra is looking for that. DId you install something like this at one point?: [http://code.google.com/p/gnome2-globalmenu/](http://code.google.com/p/gnome2-globalmenu/)

---

### Post by DJ_Peng on 2009-12-22
I use the GlobalMenu on a daily basis, but this would be the first I heard of it affecting system sounds. I am using the Main Menu applet rather than the Menu Bar applet to provide my menu listings, and my AWN uses the Cairo Main Menu. I removed both my menu applets and tried that again but I have no idea why it should be still be causing problems. At least I have a new lead to pursue so I'll report back if I can find any success going in that direction.

I will say that I had no problem hearing system sounds in jaunty and I've been a GM user since at least intrepid so it may be due to how the sounds are being handled now.

---

### Post by Cuppa-Chino on 2009-12-25
Thanks guys, this thread as been a help, by the way a step back is not even correct. "Forcing the logon & logout sounds on me" is a total nuisance and daft beyond words - well I think I will revisit kde....

---

