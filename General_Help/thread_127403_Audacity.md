---
title: "Audacity"
date: 2006-02-08
forum: General Help
---

### Post by eight_car on 2006-02-08
Audacity is not seeing my sound card at all.

The pull down boxes are empty on it.

I tried to find configuration files, no luck (I know that part IS my fault)

All other sound programs see my sound card (except realplayer which I really don't care that much about at this time).

Any help appreciated. thanks

Running Breezy 5.10 i686

---

### Post by lha on 2006-02-10
[QUOTE=eight_car]Audacity is not seeing my sound card at all.

The pull down boxes are empty on it.

I tried to find configuration files, no luck (I know that part IS my fault)

All other sound programs see my sound card (except realplayer which I really don't care that much about at this time).

Any help appreciated. thanks

Running Breezy 5.10 i686[/QUOTE]
Ive got the same problem. Open terminal and do
```
killall esd
```
It does the trick for me.

---

### Post by Denis on 2006-02-10
There is a configuration file in your home directory. 

~/.audacity

in there I have:

[AudioIO]
PlaybackDevice=/dev/dsp1
RecordingDevice=/dev/dsp1

And the following choices are available in the program: /dev/dsp and /dev/dsp1
Maybe you can try setting it to "/dev/dsp1" too?

---

### Post by eight_car on 2006-02-10
[QUOTE=lha]Ive got the same problem. Open terminal and do
```
killall esd
```
It does the trick for me.[/QUOTE]


That does work, until I reboot.

Found the config file (thanks to post below yours), anyways it has dev/dsp in it, but it doesn't show when I run audacity, unless I do the killall esd command.

Is there anyway to fix this so I don't have to type that command everytime I reboot/turnoff the computer?

Thanks in advance :)

---

### Post by lha on 2006-02-10
[QUOTE=eight_car]That does work, until I reboot.

Found the config file (thanks to post below yours), anyways it has dev/dsp in it, but it doesn't show when I run audacity, unless I do the killall esd command.

Is there anyway to fix this so I don't have to type that command everytime I reboot/turnoff the computer?

Thanks in advance :)[/QUOTE]

Do```

sudo sh -c 'echo -e "#!/bin/sh\nkillall esd\n/usr/bin/audacity">>/usr/local/bin/audacity;chmod a+x /usr/local/bin/audacity'
``` It creates a small script that kills esd and launches audacity. If you want to remove it at a later time, do
```
sudo rm /usr/local/bin/audacity
```

---

### Post by eight_car on 2006-02-10
thanks :)

I've been trying to get eerything on the PC I can think of now that I have totally dumped my WinBlows partition.

---

