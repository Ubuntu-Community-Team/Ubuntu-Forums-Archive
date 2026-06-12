---
title: "medibuntu"
date: 2010-04-18
forum: General Help
---

### Post by goldshirt9 on 2010-04-18
having decided to dump Windows on my latop, i cannot install libdvdread4 via terminal.

i have even tried to go to their web site but it fails to load at all.(the package link fails to load)

no application that requires their input will download ( awn via software sources fails)

is their a problem on their servers or a upgrade about to happen.:confused:

grateful for any infomation as i originally tough it was my network / install.

---

### Post by howefield on 2010-04-18
> **goldshirt9 said:**
> having decided to dump Windows on my latop, i cannot install libdvdread4 via terminal.

libdvdread4 is not part of the Medibuntu packages list.

You should be able to install via Synaptic Package Manager or download from here...

[http://packages.ubuntu.com/jaunty/libdvdread4](http://packages.ubuntu.com/jaunty/libdvdread4)

---

### Post by goldshirt9 on 2010-04-18
[http://https://help.ubuntu.com/community/RestrictedFormats]("http://https//help.ubuntu.com/community/RestrictedFormats")
basically im trying to install from the above link to play dvd's

even trying to open and reload synaptic fails.

a web addresse is quoted 
W: Failed to fetch [http://packages.medibuntu.org/dists/karmic/Release.gpg](http://packages.medibuntu.org/dists/karmic/Release.gpg)  Could not connect to packages.medibuntu.org:80 (88.191.82.11), connection timed out

W: Failed to fetch [http://packages.medibuntu.org/dists/karmic/free/i18n/Translation-en_GB.bz2](http://packages.medibuntu.org/dists/karmic/free/i18n/Translation-en_GB.bz2)  Unable to connect to packages.medibuntu.org http:

---

### Post by howefield on 2010-04-18
Then try this from

[https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs](https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs)

> Ubuntu 9.04, 9.10 and 10.04 (i386, amd64)
Install the libdvdread4 package (no need to add third party repositories) via Synaptic or command line:

sudo apt-get install libdvdread4
Then open a terminal window and execute:

 sudo /usr/share/doc/libdvdread4/install-css.sh

---

### Post by howefield on 2010-04-18
> **goldshirt9 said:**
> W: Failed to fetch [http://packages.medibuntu.org/dists/karmic/Release.gpg](http://packages.medibuntu.org/dists/karmic/Release.gpg)  Could not connect to packages.medibuntu.org:80 (88.191.82.11), connection timed out

W: Failed to fetch [http://packages.medibuntu.org/dists/karmic/free/i18n/Translation-en_GB.bz2](http://packages.medibuntu.org/dists/karmic/free/i18n/Translation-en_GB.bz2)  Unable to connect to packages.medibuntu.org http:

The Medibuntu repositories are down, but that won't affect your ability to install libdvdread4.

---

### Post by goldshirt9 on 2010-04-18
> **howefield said:**
> The Medibuntu repositories are down, but that won't affect your ability to install l[COLOR=Red]ibdvdread4[/COLOR].

already installed but no dvd will play.
on my desktop i have no problem

---

### Post by Water_Spirit on 2010-04-18
Have you installed libdvdcss2.

---

### Post by wojox on 2010-04-18
You ran this command in the terminal:

```
sudo /usr/share/doc/libdvdread4/install-css.sh
```

---

### Post by howefield on 2010-04-18
Did you run the terminal command...

```
sudo /usr/share/doc/libdvdread4/install-css.sh
```

If that doesn't do it, you'll need to keep trying till the Medibuntu site is back up.

I have a copy of libdvdcss but for Lucid 64 bit,  I'm not sure if it is the same version as you need for Karmic, but if you want it I'll send it you.

It is only a tiny file.

---

### Post by goldshirt9 on 2010-04-18
> **Water_Spirit said:**
> Have you installed libdvdcss2.
yes all are installed
kubuntu
xubuntu
ubuntu.

wojox i keep trying .
howefield i keep trying ,

looks as though i will have to wait until the site is back up.

thanks for the offer of the file.
unfortunately i have no idea if i could use it.

looks like i'll just have to wait.

---

### Post by wojox on 2010-04-18
Try updating from your Update Manager.

---

### Post by wojox on 2010-04-18
You could also try this [http://www.webupd8.org/2010/04/medibuntu-repository-down-what-to-do.html](http://www.webupd8.org/2010/04/medibuntu-repository-down-what-to-do.html)

---

### Post by interval1066 on 2010-04-18
> **howefield said:**
> The Medibuntu repositories are down, but that won't affect your ability to install libdvdread4.

Yeah, what's up w/Medibuntu? Anything serious?

---

### Post by uRock on 2010-04-18
> **wojox said:**
> Try updating from your Update Manager.

The Medibuntu servers are down.

---

### Post by howefield on 2010-04-18
> **interval1066 said:**
> Yeah, what's up w/Medibuntu? Anything serious?

Probably not too serious, who knows, they don't seem to update with status messages during their pretty frequent outages.

Best to be aware of the alternative mirrors, and/or download the relevant packages from Medibuntu when they are up and keep a hold of them on your disk somewhere.

---

### Post by taurolyon on 2010-04-19
Check out this mirror... it goes back a couple releases but has the i386 and AMD64 versions

[http://mirror.ubuntulinux.nl/dists/gutsy-seveas/all/](http://mirror.ubuntulinux.nl/dists/gutsy-seveas/all/)

just look for:
>  Package [libdvdcss2_1.2.9-2medibuntu4_i386.deb]("http://mirror.ubuntulinux.nl/pool/gutsy-seveas/extras/libdvdcss2_1.2.9-2medibuntu4_i386.deb")
Package [libdvdcss2_1.2.9-2medibuntu4_amd64.deb]("http://mirror.ubuntulinux.nl/pool/gutsy-seveas/extras/libdvdcss2_1.2.9-2medibuntu4_amd64.deb")I installed the AMD64 version last night and it's working great!! I suppose when medibuntu is back up, it'll go on my update list if there's a new version in the repository.

---

### Post by goldshirt9 on 2010-04-19
you are a hero :P
many thanks for the link:P

---

