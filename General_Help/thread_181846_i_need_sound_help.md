---
title: "i need sound help"
date: 2006-05-24
forum: General Help
---

### Post by Polygon on 2006-05-24
when i was installing the alsa drivers for my sound card, i did not realize that it was already installed with ubuntu, and now when any sounds play together (like im listening to music, and a gnome sound plays) then the music gets distorted for a few seconds. Also sound on websites sounds horrible, sound on games is nonexistant....

i want to reinstall alsa and reconfigure it, but i have no idea where the alsa drivers that i downloaded from the site got installed, so i cant delete them.

does anyone know where they got installed, so i can delete them and configure only the native ubuntu ones? 

thanks

my soundcard is a sound blaster live 24 bit btw

---

### Post by yager on 2006-05-24
Go to System>Administration>Synaptic Package Manager and check to see if you have multiple entries named alsa.... that are checked as installed. On my system, the only packages installed are alsa-base and alsa-utils.

You can click the check box to remove any or all of the packages and then after confirming this, recheck only the ones you need.

---

### Post by Polygon on 2006-05-24
i have alsa-base and alsa-utils installed on my machine too, but i also have 


gstreamer0.8-alsa, 
ibasound2,
libesd0-alsa,
libmikmod2,
libpt-plugins-alsa and 
linux-sound-base installed 

(all of these come up when i search for alsa)

but would sypnatic show programs that i have installed without synaptic? i used the instructions on this site: ([click here]("http://www.alsa-project.org/alsa-doc/doc-php/template.php?company=Creative+Labs&card=Sound+Blaster+Live+7.1.&chip=SB0410%2C+P17&module=ca0106")) 

and installed the driver and the library, but i could not install the utils because it needed some library, and right then i realized that ubuntu already had the driver and utils installed, so i just configured it that way.

---

### Post by yager on 2006-05-24
[QUOTE=Polygon]
gstreamer0.8-alsa, 
ibasound2,
libesd0-alsa,
libmikmod2,
libpt-plugins-alsa and 
linux-sound-base installed 
[/QUOTE]I have all of these checked as well so that appears to be ok.

The link you included is in deep.  It is over my head at this point.  I will say this though, the only items in my /etc/modutils directory are:
```
0keep    aliases    apm   bluez  lvm-common         paths
actions  alsa-base  arch  evms   nvidia-kernel-nkc

```

If you created a separate alsa file as directed, you might be able to remove it from this folder and follow the directions to run update-modules again to see if that removes from the kernel the alsa files that you installed.  It appears that every command that you are instructed to put in the alsa file is already in the alsa-base file so this may be what is causing the confusion with the sound setup.

---

### Post by Polygon on 2006-05-25
yeah i also have "alsa-base" in my /etc/moduitls folder, so let me just make sure of what im doing here

remove "alsa-base" from the /etc/modutils folder
"update modules" to see if the snd*(whatever) modules are removed

is that right?

---

### Post by yager on 2006-05-26
The directions at your link said to create a file named alsa.  This is the file that you need to remove.  Leave the alsa-base file.

Then run the update-modules.

Of course all of this assumes that you were following the debian specific directions.  If you used a different part of the web page, which section was that?

Just to be clear, this is outside of my experience so you may want to start another thread if this does not solve your problem.

---

