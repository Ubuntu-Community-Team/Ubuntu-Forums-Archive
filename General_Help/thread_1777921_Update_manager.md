---
title: "Update manager"
date: 2011-06-08
forum: General Help
---

### Post by Faan on 2011-06-08
The last few days I get this little warning message on the screen which says the following when I click on it:

"Software updates might be available for your computer. 
The package information was last updated 12 days ago.
Press the 'Check' button below to check for new software updates."

There must be something wrong as I set it that updates take place daily and I also update or look for something else to download myself.  The little warning sign just remains.

---

### Post by seawolf167 on 2011-06-08
This is normal - it checks for updates daily based on your input there, and then displays what updates are available and prompts you to install them. If you hit "check" it does the same thing as 

```
sudo apt-get update
```

i.e. updating the repo lists. Then if you install the updates, it is the same as

```
sudo apt-get upgrade
```

so you can go ahead and install the updates daily from that box without worrying

---

### Post by Ievoigh0 on 2011-06-08
I just registered here and am lost.
I keep getting a msg saying I need to report a bug against update manager. I can't find a bug forum, and this is the first thing I've seen on update manager, so here goes.

E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_natty_main_i18n_Translation-en
E: The package lists or status file could not be parsed or opened.
E: _cache->open() failed, please report.

---

### Post by seawolf167 on 2011-06-08
Please open a terminal (the keyboard shortcut by default is [CRTL][ALT][T]), then type in the following lines, hitting enter after each one

```
sudo rm /var/lib/apt/lists/* -vf
sudo apt-get update
sudo apt-get upgrade
```

and tell me if you have any errors that appear, you'll get a lot of scrolling text, specifically look for anything that stops the process and spits out an error.

---

### Post by jramshu on 2011-06-08
It should work.

Just to let OP know, look in forums first before filing a bug report. It's usually already been solved here.

---

### Post by Ievoigh0 on 2011-06-08
:guitar:
THANK YOU SEAWOLF!!!
Now, could you explain what I just did? :)

---

### Post by seawolf167 on 2011-06-08
> **yonatan703 said:**
> THANK YOU SEAWOLF!!!
Now, could you explain what I just did?

The first command removed the lists cache, the second fetched the updated lists, and the third preformed the necessary upgrades according to the updated lists

---

### Post by dFlyer on 2011-06-08
> **seawolf167 said:**
> Please open a terminal (the keyboard shortcut by default is [CRTL][ALT][T]), then type in the following lines, hitting enter after each one

```
sudo rm /var/lib/apt/lists/* -vf
sudo apt-get update
sudo apt-get upgrade
```

and tell me if you have any errors that appear, you'll get a lot of scrolling text, specifically look for anything that stops the process and spits out an error.

If you ran the above commands you deleted files from /var/lib/apt/lists/

you than updated you archives with apt-get update and then updated your computer with apt-get upgrade from the command line.

---

### Post by Ievoigh0 on 2011-06-08
jramshu, What is OP?
I searched the term 'report bug' and found nothing relevant.
I searched the term 'update manager' and found this.
Seems I already said I can't find a bug forum.

---

### Post by seawolf167 on 2011-06-08
> **yonatan703 said:**
> What is OP?
I searched the term 'report bug' and found nothing relevant.
I searched the term 'update manager' and found this.
Seems I already said I can't find a bug forum.

OP = original poster

You do not have to file a bug report, very rarely will you find a new and un-reported bug in anything but a development release

---

### Post by Faan on 2011-06-08
> **seawolf167 said:**
> This is normal - it checks for updates daily based on your input there, and then displays what updates are available and prompts you to install them. If you hit "check" it does the same thing as 

```
sudo apt-get update
```

i.e. updating the repo lists. Then if you install the updates, it is the same as

```
sudo apt-get upgrade
```

so you can go ahead and install the updates daily from that box without worrying


I am a little confused as I do not know whether you answered me or whether you answered yonatan703.

I can manually update and can do so by clicking on "check" only to find later on that the warning message is back there.

What concerns me is that it tells me that system was last updated 
12 days ago.  When I click on check it does so, but then get an error message saying "Failed to download repository information and check your internet connection.  As far as I know there is nothing wrong with my internet connection as I am submitting this onto the forum. 

This what appears in the window: 

W:Failed to fetch cdrom://Ubuntu 10.10 _Maverick Meerkat_ - Release i386 (20101007.1)/dists/maverick/main/binary-i386/Packages  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
, W:Failed to fetch cdrom://Ubuntu 10.10 _Maverick Meerkat_ - Release i386 (20101007.1)/dists/maverick/restricted/binary-i386/Packages  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
, E:Some index files failed to download. They have been ignored, or old ones used instead.

Thanks very much for the help.

---

### Post by seawolf167 on 2011-06-08
The problem there is that the cdrom has been added as a repo.

```
W:Failed to fetch cdrom://Ubuntu 10.10 _Maverick Meerkat_ - Release i386  (20101007.1)/dists/maverick/restricted/binary-i386/Packages  Please use  apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot  be used to add new CD-ROMs
```

Open your update manager (System -> Administration -> Software sources) and ensure that the cdrom source is unchecked. Then re-check for updates and you should be good to go.

---

### Post by Faan on 2011-06-08
Thanks very much, will do.

---

### Post by seawolf167 on 2011-06-08
> **Faan said:**
> Thanks very much, will do.

Report back if it works (or not)

---

### Post by Faan on 2011-06-08
Yes, thanks very much.  I did what you said and the message is gone.

Something I find strange is that the facility is there, surely hardly any person updates from a CD.

---

### Post by seawolf167 on 2011-06-08
Glad it is working!

It depends on where they are located usually (now-a-days anyway) - say you don't have high speed internet in your area, it could be much easier to have a disk mailed to you or to say download the updates at work or a friends house and bring the disk back home. It is much less of an issue now-a-days, but back in the 5600 baud modem days... lol

---

### Post by Faan on 2011-06-08
Thanks

---

