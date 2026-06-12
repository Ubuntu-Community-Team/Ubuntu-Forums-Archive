---
title: "burn vobs"
date: 2006-02-15
forum: General Help
---

### Post by neoroses on 2006-02-15
Hi i have some dvd files .. video_ts audio_ts --- the usual...i want to quickly and easily put them on dvd so they will play :D is there a simple way to do this???? oh and btw i have tried using mkisofs but it always fails i get this:
mkisofs: Can't open VMG info for '/home/sam/dvd/'.
mkisofs: Unable to parse DVD-Video structures.
mkisofs: Unable to make a DVD-Video image.

or

INFO:   UTF-8 character encoding detected by locale settings.
        Assuming UTF-8 encoded filenames on source filesystem,
        use -input-charset to override.
mkisofs: No such file or directory. Invalid node - dvd/
sam@tuxbox:~/dvd$


thanks :D

---

### Post by StefanoCole on 2006-02-16
How did you get the VIDEO_TS and AUDIO_TS files? Did you get them starting from a DVD and using the "dvdbackup" command? If yes, you could try the following command:```
growisofs -speed 2 -dvd-compat -Z /dev/dvdrw -dvd-video MY_DVD/
```
where /dev/dvdrw is the device of the DVD burner and MY_DVD/ is the directory where VIDEO_TS and AUDIO_TS are contained.

Stefano

---

### Post by taurus on 2006-02-16
If you have k3b, then fire it up and at the top left, click on Files.  Then New Project and pick the DVD movie option.  Then, scroll to where you have VIDEO_TS and just drag the whole folder into it...  Click Burn and sit back and wait for it to finish!

---

