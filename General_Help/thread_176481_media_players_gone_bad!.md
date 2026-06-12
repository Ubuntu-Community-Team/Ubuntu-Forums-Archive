---
title: "media players gone bad!"
date: 2006-05-14
forum: General Help
---

### Post by GhandiBurger on 2006-05-14
I went to watch a movie with aviplayer and it didn't work. So I went to Totem, and that didn't work. Then I went to Mplayer and that didn't work. I installed about 5 more media players and none of them worked. All I want to do is watch avi files. Is there a setting I have to change in order to use the players? I have uninstalled and then reinstalled all of them several times. please help....utter boredom is ensuing......

---

### Post by simonn on 2006-05-14
RTFM :)...

[https://wiki.ubuntu.com/MplayerInstallHowto?highlight=%28mplayer%29](https://wiki.ubuntu.com/MplayerInstallHowto?highlight=%28mplayer%29)

[https://wiki.ubuntu.com/RestrictedFormats](https://wiki.ubuntu.com/RestrictedFormats)

---

### Post by GhandiBurger on 2006-05-14
None of it worked....:(

Edit: I got an error message telling me the mplayer configuration file could not be saved.

---

### Post by Dr. Nick on 2006-05-15
[quote=GhandiBurger]None of it worked....:(

Edit: I got an error message telling me the mplayer configuration file could not be saved.[/quote]

Try vlc yet, It has its own codecs for smoe formats I think.
If you have all gstreamer plugins and the w32codecs installed then launch the players from a terminal and look for more detailed error messages. you may also launc them as sudo user to see if its permission problems

---

### Post by GhandiBurger on 2006-05-15
```
root@ubuntu:/home/sam# sudo totem

(totem:9023): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified  are supported and host-based authentication failed.

(totem:9023): Gtk-CRITICAL **: gtk_accel_label_set_accel_closure: assertion `gtk _accel_group_from_accel_closure (accel_closure) != NULL' failed

(totem:9023): Gtk-CRITICAL **: gtk_accel_label_set_accel_closure: assertion `gtk _accel_group_from_accel_closure (accel_closure) != NULL' failed

** (totem:9023): WARNING **: Failed to connect to the D-BUS daemon: No reply wit hin specified time

```

I got that message in the terminal after I tried to play a file.

Edit: I checked the permissions on the program file and all it had was:
Owner: *Read   *Write   *Excecute
Group: *Read     Write   *Excecute
Others: *Read   Write   *Excecute

Totem gives me this when I play a file: Failed to play: Could not open resource for writing.
Should I change the permissions? and if so, how?

---

### Post by sinkxdie on 2006-05-15
You can't run a media player in Root!!!

And besides, using sudo is useless if your in a root terminal

---

### Post by GhandiBurger on 2006-05-15
mehhh.....*is a linux n00b*

---

### Post by sinkxdie on 2006-05-15
Lol, did you try running it **not** in root?

---

### Post by GhandiBurger on 2006-05-15
I have tried EVERYTHING!!! lol. (at least, everythign I could think of) I did it just by clicking on the file, but totem crashes. meh. *wallows in self-pity*

---

### Post by Dr. Nick on 2006-05-15
Dont know what it would be, I only suggested running as root since it said it couldnt save the configureation, thought maybe the spot it saves to was unwriteable for normal users for some reason.
I have no trouble playing avi files using totem so I know its possible, just dont know what is not right on yours. When you removed and reinstalled them did you do a complete uninstall in synaptic as to get the confiuration files deleted? Probably wouldnt make a difference but its a idea. 

It could just be they were made using some very odd codec, only way to test it would be to get anoter video and see if you can get any files to play. Or by resinstalling ubuntu and seeing if it worked then but that is sort of an extreme solution

---

### Post by GhandiBurger on 2006-05-16
They had worked untill I installed my graphics drivers. Maybe it has something to do with the X settings?

---

### Post by Dr. Nick on 2006-05-16
[quote=GhandiBurger]They had worked untill I installed my graphics drivers. Maybe it has something to do with the X settings?[/quote]

Not sure if that would mess them up or not, Only way to find out would be to edit /etc/X11/xorg.conf back to the default driver

nv for nvidia
vesa for anything
not sure with the ati

Ive never seen this sort of trouble before

---

### Post by GhandiBurger on 2006-05-16
I uninstalled and reinstalled totem-xine and got this error message:

Errors were encountered while processing:
 lilypond-data
E: Sub-process /usr/bin/dpkg returned an error code (1)

Is that a problem and how can I fix it?

---

### Post by Dr. Nick on 2006-05-16
[quote=GhandiBurger]I uninstalled and reinstalled totem-xine and got this error message:

Errors were encountered while processing:
 lilypond-data
E: Sub-process /usr/bin/dpkg returned an error code (1)

Is that a problem and how can I fix it?[/quote]

Have you ran
sudo dpkg --configure -a

that will finish any incomplete installations you have. Also try to sudo apt-get install lilypond-data and see if it lets you, or gives more errors

---

