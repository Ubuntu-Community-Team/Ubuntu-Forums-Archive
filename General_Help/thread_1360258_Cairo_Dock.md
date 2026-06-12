---
title: "Cairo Dock"
date: 2009-12-20
forum: General Help
---

### Post by Bigtime_Scrub on 2009-12-20
I'm trying to install Cairo-Dock on Karmic and I got a strange error I've never seen before. I followed the docs here. [https://help.ubuntu.com/community/CairoDock](https://help.ubuntu.com/community/CairoDock)

I tried by adding the repository to my sources list and then I added the key ring, no dice. I also tried the .deb packages from here. [http://developer.berlios.de/project/showfiles.php?group_id=8724](http://developer.berlios.de/project/showfiles.php?group_id=8724)

Each time I try I get this error:

```
gary@gary-laptop:~$ sudo apt-get install cairo-dock cairo-dock-plug-ins
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  cairo-dock-core cairo-dock-data cairo-dock-plug-ins-data
  cairo-dock-plug-ins-integration curl libetpan13 libgtkglext1 xdotool
Suggested packages:
  gnote
The following NEW packages will be installed:
  cairo-dock cairo-dock-core cairo-dock-data cairo-dock-plug-ins
  cairo-dock-plug-ins-data cairo-dock-plug-ins-integration curl libetpan13
  libgtkglext1 xdotool
0 upgraded, 10 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/6,279kB of archives.
After this operation, 14.9MB of additional disk space will be used.
Do you want to continue [Y/n]? y
dpkg: parse error, in file '/var/lib/dpkg/status' near line 14232 package 'gstreamer0.10-plugins-bad':
 `Provides' field, invalid package name `gstreamer0.10)videosink': character `)' not allowed (only letters, digits and characters `-+._')
E: Sub-process /usr/bin/dpkg returned an error code (2)

```

---

### Post by gradinaruvasile on 2009-12-20
sudo apt-get install -f

Does it help?

---

### Post by lrcaballero on 2009-12-20
Try installing it from:

Applications/Ubuntu Software Information.

I had some problems manually installing it, and I did this and it works PERFECT!!!!!

Good Luck

Luis

---

### Post by Bigtime_Scrub on 2009-12-20
> **gradinaruvasile said:**
> sudo apt-get install -f

Does it help?

I just tried that, 0 installed, upgraded, and removed.

I also tried ```
sudo apt-get install -f cairo-dock cairo-dock-plug-ins
``` and I got the same error message.

---

### Post by Bigtime_Scrub on 2009-12-20
> **lrcaballero said:**
> Try installing it from:

Applications/Ubuntu Software Information.

I had some problems manually installing it, and I did this and it works PERFECT!!!!!

Good Luck

Luis



I just tried that too.

"installArchives() failed: dpkg: parse error, in file '/var/lib/dpkg/status' near line 14232 package 'gstreamer0.10-plugins-bad':

 `Provides' field, invalid package name `gstreamer0.10)videosink': character `)' not allowed (only letters, digits and characters `-+._')
"

Which is the same error I got from the command line. I don't know what the gstreamer plugins have to do with the dock or why a problem there would prevent the install.

---

### Post by mIXpRo on 2009-12-20
i had the same problem ,
search for it at the synaptic pack.. and install it from their .

---

### Post by lrcaballero on 2009-12-20
Try this:

System/Administrator/Synaptic Package manager

in the left hand-side window click on broken

see if there is anything that needs attention and just follow through....

also restart your computer go to Applications/Accesories and check if is there!!!! if not try installing it from ubuntu software center again.

By the way I Love your QUOTE!!!!!!

Good Luck

Luis

---

### Post by mIXpRo on 2009-12-20
take this link it builds for you a sources.list file 

don't build new one , just select the cairo doc and it shows the software source and the keys you need , plus there is a lot of good "add ones" for ubuntu .

the [link]("http://repogen.simplylinux.ch/")

enjoy.

---

### Post by gradinaruvasile on 2009-12-20
gstreamer0.10-plugins-bad - that package isnt configured correctly on your system and crashes the package installer. You have to remove it to sort it out otherwise there is a chance you cannot upgrade your system because of it, and cant install any other packages.
Remove it:

sudo apt-get purge gstreamer0.10-plugins-bad

But first watch out what other packages/programs takes with it to reinstall those if needed.

---

### Post by howefield on 2009-12-20
As an extremely minor side note,.. when you get the choice  *```
"Do you want to continue [Y/n]? y"
```*

you can simply press enter without typing the confirming "y". The capitalised letter has the focus, so the only way you would need to type a letter would be for "n".

As I said, extremely minor. ;)

---

### Post by Bigtime_Scrub on 2009-12-20
I've tried all that I still get the same error message. I will try to compile it myself if that doesn;t work I have no idea.

---

### Post by gradinaruvasile on 2009-12-20
If all else fails and you cant install anything because of that package, there is a dirty hack:

Edit the /var/lib/dpkg/status file, first backing it up:
backup:

```
sudo cp /var/lib/dpkg/status /var/lib/dpkg/status.backup
```

and edit:

```
sudo gedit /var/lib/dpkg/status
```

Press CTRL+F, type in the search string box (no quotes): "Package: gstreamer0.10-plugins-bad"

Select the whole section that belongs to it and delete it and make sure there is 1 empty line remaining between the previous and the next section - to keep the formatting of the file.

Open a terminal and try to install whatever you want. 
Is it working?

If there is something wrong (other fatal errors), restore the backup, typing:

```
sudo cp /var/lib/dpkg/status.backup /var/lib/dpkg/status
```

---

