---
title: "rsync and kde-hotplug a.k.a. how to synchronise my player."
date: 2006-03-12
forum: General Help
---

### Post by gidsouljah on 2006-03-12
hi at everyone

first of all i wan't to say that ubuntu-community rocks. this is the first thread i have to post after using (k)ubuntu and the related forums for over a year.. do i have to say more? :-D

my problem: i have bought a mp3-player which is recognised as removable device when i plug it in my comp. i would like to have a new option in the kde-hotplug-window which is popping up on plugging the player (kde 3.5) to synchronise my player with a certain directory.

if the device is mounted, the command

rsync --size-only -r -u -v ~/sound/* /media/sda1/MUSIC/

does this job perfect. I've added an action in systemsettings for unmounted devices (in "Speichermedien" in the german version, the place where u can choose the actions for CD, DVD etc.). the command:

rsync --size-only -r -u -v ~/sound/* %u/MUSIC/

but this does nothing (%u standing for the device?--> i'm not sure about this). the player isn't even mounted. do i have to do this manually? and how can i choose that the command is executed in the shell, so that i can see, what is going on?

---

### Post by jimbren on 2006-03-13
what player are you using?  

I'd also like to do something like this.

---

### Post by gidsouljah on 2006-03-13
i'm using a samsung yh-j70 --> really nice 20-gb player without any itunes and drm pressure. just plug and drag & drop.:cool: :-D

---

