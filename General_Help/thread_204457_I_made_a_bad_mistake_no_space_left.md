---
title: "I made a bad mistake no space left"
date: 2006-06-27
forum: General Help
---

### Post by CameronCalver on 2006-06-27
Hey i did a full backup and i forgot that it didnt have a very big hard drive and then when i clicked filesystem i it says free space o bytes which i expected so i deleted the backup file and removed it from trash and it did not do anything still no space left so i did a restart and it said
Could not start gdm  could no write athentification file maybe no disk space and how will i mount the hard drive in the live cd and free some space up but the computer has 2 hard drives and like 3 partions so can some1 help me

---

### Post by mlind on 2006-06-27
If you're going with that liveCD method, then create temporary mount point for
your partition and mount it there

```

sudo mkdir /mnt/root
sudo mount -t ext3 /dev/**xxx** /mnt/root -o defaults

```

to find the partition (xxx) you want to mount, use
```

sudo fdisk -l

```


package called *xdiskusage* could help you here

---

### Post by aysiu on 2006-06-27
You could use the live CD, but have you tried rebooting into recovery mode? This will make you root in a terminal.

```
apt-get clean
rm -rf /home/cameroncalver/.Trash/*
reboot
``` should take care of your problem.

---

### Post by CameronCalver on 2006-06-27
mlind im going to try your aproach second becuase the other one with apt-get clean thing looks easyer and whats does that clean thing do anyway

---

### Post by aysiu on 2006-06-27
It empties the /var/cache/apt/archives folder, that has the installer files (the .deb files) for all the applications you've installed via Synaptic, aptitude, or apt-get.

By the way, this command will work only if you're using Gnome: ```
rm -rf /home/cameroncalver/.Trash/*
``` If you're using KDE, you should use this command instead: ```
rm -rf /home/cameroncalver/.local/share/Trash/files/*
rm -rf /home/cameroncalver/.local/share/Trash/info/*
``` And, of course, this all assumes your Ubuntu username is cameroncalver. Substitute your real username.

---

### Post by CameronCalver on 2006-06-27
will that meen i will have to download everything again

---

### Post by mlind on 2006-06-27
[QUOTE=CameronCalver]will that meen i will have to download everything again[/QUOTE]

*sudo apt-get clean* will remove .deb archives you've downloaded from
/var/cache/apt/archives/ folder

It's safe and recommended to do. You rarely need these packages again, and if
you do, you can download them again.

---

### Post by CameronCalver on 2006-06-27
ok none of you sugestions are working so i am going to delete everything i dont need then do a backup so when i extract the files everthing that was before willl be there incluiding all the things like applications games and internet you know what will the comand be

---

### Post by aysiu on 2006-06-27
You know what--all along we were assuming there was no disk space left.

If you clean out your /var/cache/apt/archives folder, that deletes a lot of used space.

Maybe it's that it couldn't write to your authentication file, and that's the problem. [This thread](http://www.ubuntuforums.org/showthread.php?t=90361) may help you--please scan through the whole thing; it's not that long.

Otherwise, I believe that backup command you're looking for is [here](http://www.ubuntuforums.org/showthread.php?t=35087).

---

### Post by CameronCalver on 2006-06-27
well the thing is i try to do that command to backup everything but i have like used only 2 gb o a 40gb hd and it says no space left do you think i should do a reinstall

---

### Post by mlind on 2006-06-27
Could you post the original exact error message and describe where it happened.

---

### Post by aysiu on 2006-06-27
I think it depends on you.

If you have some time to learn how to fix this, you may find the fix is easier than you think, and it could save you time in the long run. The added bonus to this is that you actually learn the solution to the problem, and you may be able to help someone else who has the same problem.

But... to be perfectly honest, sometimes it just is easier to back up settings and files reinstall.

---

### Post by aysiu on 2006-06-27
[QUOTE=mlind]Could you post the original exact error message and describe where it happened.[/QUOTE]
Based on the original loose paraphrase, I'm willing to guess it was this: > GDM could not open your authorization file. This could mean that you are out of disk space or that your home directory could not be opened for writing. In any case, is not possible to log in. Please contact your system administrator Do you think it could be something so simply as this? ```
sudo chown /home/cameroncalver/.ICEauthority
chmod 600 /home/cameroncalver/.ICEauthority
```

---

### Post by dishbert on 2006-07-06
I am in the same pickle after trying to use the cleandrive script that came with G4L.  I think that cleandrive successfully wrote numbers to all my blank disc space, but that when it deleted them they just ended up in the trash and left the hard drive full.  Now I get the "GDM could not write to the authorization file..." message.

I've tried using the recovery teriminal and the "rm -rf /home/me/.Trash/* command, but no joy.

Did anything work for you aysiu?

---

### Post by richardh9935 on 2006-07-17
[COLOR=DarkRed]Oh boy am I glad I found this suggestion.  I had zero free space; then I used apt-get clean, and now I have 258MB free!  I am very grateful to you.

Richard.[/COLOR]

---

