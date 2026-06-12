---
title: "where is the shared folder?"
date: 2011-07-21
forum: General Help
---

### Post by liquidmonkey on 2011-07-21
i'm using ubuntu 10.10 inside Virtual Box.
i have shared a folder on win7.
i can't for the life of me find where that folder is in ubuntu now?

maybe i'm missing a step with the whole folder sharing but a shared folder is created and the box is ticked, so where in ubuntu is it?


thanks!

---

### Post by DawieS on 2011-07-21
Open a Nautilus file browser. On the side pane, click on Network, then Windows Network.
Alternatively, click on Places, then Network, then Windows Network.:smile:

---

### Post by Morbius1 on 2011-07-21
If you mean you shared it using VBox on WIn7 then the share is in the following location in the Ubuntu guest:

/media/sf_share-name

---

### Post by liquidmonkey on 2011-07-22
well i found the folder in the /media as suggested which is good but weird since i didn't have to mount anything like i read on google.

so now my question is

- how often does this refresh?
- is there a max filesize?
- i have added some files (on the windows side), a 68KB txt file, a 2.4MB .exe file and a 4.8 gig .iso file.
none of the above are showing :( even after a reboot of the VB.

i also added a txt file on the ubuntu side but that is not showing up on the windows side.

i must be doing something wrong here, or?

---

### Post by liquidmonkey on 2011-07-22
not sure what has happened now but i renamed the shared folder on the win7 side, changed it in VB and then started UBUNTU and now it works awesome!!

refreshes right away and all files show up!
fantastic!


if anyone knows why this works without having to mount it as i read here, i'm curious to know why.

[http://www.sysprobs.com/virtualbox-shared-folders-ubuntu-1010-guest-windows-7-host](http://www.sysprobs.com/virtualbox-shared-folders-ubuntu-1010-guest-windows-7-host)

thanks!

---

### Post by Morbius1 on 2011-07-22
Different versions of Virtual Box. Version 4 automatically mounts these shared folders in Windows and Linux guests. It's more obvious in Windows since it shows up as a drive letter. It would be more obvious in Linux if it would mount off the root ( / ) directory.

It threw me off as well when I first used the new version. Pays to read the User Manual I guess.

---

