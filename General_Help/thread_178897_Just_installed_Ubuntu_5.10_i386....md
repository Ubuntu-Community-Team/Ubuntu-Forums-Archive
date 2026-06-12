---
title: "Just installed Ubuntu 5.10 i386..."
date: 2006-05-18
forum: General Help
---

### Post by ROUBOS on 2006-05-18
Hi people,
I have just installed Ubuntu 5.10 on my spare machine and everything seems fine. It's now downloading updates.

What I would like to do it is to setup Ubuntu so I can watch DVDs, listen to MP3s, mount my extra NTFS HDD on this sytem.

I would also like to setup Gnome the way I see some screenshots of people that have customised it nicely...

Can anyone please direct me?

Eventualy i would like to be able to run a web-server with PHP and MySQL etc etc... but slowly I guess... a new commer to Ubuntu and Linux (even though I have played around with Linux before) and would like to stay... :) 

I have tried RedHat, Mandrake, SUSE, and eve Kubuntu... I realy like Ubuntu (last time I installed it was version 5.04), and seem to prefer it so I would like to become familiar with it.

Any direction in customizing my Gnome Desktop and running things in general will be great.

Thanks!

---

### Post by xXx 0wn3d xXx on 2006-05-18
Have you tried using [ Automatix ](http://ubuntuforums.org/showthread.php?t=138405) to install the codecs that you need ? To install automatix, do the following in terminal: (Applications > Accessories > Terminal)

> wget [http://beerorkid.com/automatix/automatix_5.8-4_i386.deb](http://beerorkid.com/automatix/automatix_5.8-4_i386.deb)
sudo dpkg -i automatix_5.8-4_i386.deb

Once you have installed Automatix, start it by going under Applications > System Tools > Automatix. Then select the things that you want (Non-free audio, video, and dvd codecs) and then hit ok.

That takes care of the codecs. Now onto the customization; visit [www.gnome-look.org](www.gnome-look.org) or art.gnome.org for themes,desktop backrounds, and much more.

The difference between SuSE and Fedora and Ubuntu, is that Ubuntu uses debian files. Read [ this guide](http://www.psychocats.net/ubuntu/installingsoftware.php) to get information on how to install software in Ubuntu if you don't know how.

I can't really help on the webserver or NTFS, sorry.

---

### Post by gerbman on 2006-05-18
[QUOTE=ROUBOS]What I would like to do it is to setup Ubuntu so I can watch DVDs, listen to MP3s[/QUOTE]
[This]("https://wiki.ubuntu.com/RestrictedFormats?highlight=%28dvd%29%7C%28playback%29") should take care of MP3s and DVD playback. Automatix will probably work, but I don't like it, personally. Give both methods a try and decide for yourself :-)

> mount my extra NTFS HDD on this sytem
[This]("https://wiki.ubuntu.com/MountingWindowsPartitions?highlight=%28mounting%29") should help with the NTFS drive.

> I would also like to setup Gnome the way I see some screenshots of people that have customised it nicely...
You might try [this]("http://doc.gwos.org/index.php/EyeCandyBreezy") list of tweaks and how-tos. There is a lot out there on this subject, so do some searching (for "eye candy", maybe).

Hope that helps a little.

---

### Post by ROUBOS on 2006-05-18
Thanks, will look into it... 

Thank you

---

### Post by rcarring on 2006-05-19
Roubos, if you do plan to widen your knowledge and run your Ubuntu box as a web server etc, you may want to try out the new Dapper, when it is released, as I understand that this version should enjoy long term support.

I don't know if Breezy will continue to be updated for the same period of time.

(Nb if after updating Breezy your xserver crashes, try apt-get install xserver-xorg and then when it is done installing, startx)

---

