---
title: "Screwed something up, please help"
date: 2009-06-27
forum: General Help
---

### Post by complete-linux-noob on 2009-06-27
Second time messing up my install. I am using **Mint **which is Ubuntu based so I thought to come here for the larger helpful community. Im coming over from windows, trying to rid myself of it much as possible. Things aren't looking up for me.


First time I messed things up was copy pasting stuff into the terminal, but this time I screwed it up just graphically!!! I am now posting from XP.   


**TO THE POINT:      **Last I recall, I was resetting permissions  for my linux filesystem partition,  also I was messing around with trying to configure the grub bootloader settings.


All of sudden, I cant get into anything other than firefox. Everything was telling me **"user root does not exist". ** I try to get back into wherever places I was and change everything back. Couldn't get in. Tried opening the terminal, all of the pre-filled in stuff thats usually there didn't initilialize and I got an error message. It would not let me type in anything.

I rebooted, thought it might help.   Now I cant even get into the OS!

It gives me a message that says **" user's $HOME/.dmrc file is being ignored. This prevents default session / language from being saved. File should be owned by user and have 644 permissions....."**

It has an OK button to continue forward but the cursor is frozen and I cant do a thing.

---

### Post by plewisfdx on 2009-06-28
In general, permissions are set to help protect you, and changing them drastically is usually not a good idea.  It looks like you locked yourself out of your home folder.

If you have a live cd, boot into the live cd and you may be able to fix the permissions.

From the live cd, locate your ubuntu install in the file manager.  You are looking for the /home/YOUR_NAME directory.  Don't mistake this for the live CD's home directory.  Your username should be there.

Make sure the live cd mounts the directory, then move to the terminal.

It should mount your home directory (or your entire filesystem) in the /media folder.  So if you know the name of your broken system, and it mounted in media, you would type in the terminal:
```
cd /media/BROKEN_SYSTEM/home
```

inserting the correct name for BROKEN_SYSTEM.

now from that directory, you need to see what permissions are set for your home folder.

```
ls -l
```

Here's mine:
```
drwxr-xr-x 62 phil phil  4096 2009-06-28 07:42 phil

```

Since my username is phil, I am the owner of the directory (the first phil) and my group has access to this directory (the second phil).  

You need to have your username in both of these places in your home directory.

To fix it if thats not the case, type:

```
chown phil:phil phil
```

substituting your username for phil.

If you get an error about permissions, type this:
```
sudo su
```

and your terminal should have a # as the final character instead of the $ meaning you are root, and should be able to execute all of these commands without a permission problem. 

Then type that last chown command again.

You also need to have the same drwxr-xr-x on the left of that line as I do above.  

To fix it if thats not the case, type:

```
chmod 755 phil
```

substituting your username for phil.

Now your username should have access to your home directory.

All the config files in your home directory also need to be accessed by you.

Looking through my home folder, I own all the folders and files.

So to try to fix this, type:
```
cd phil
chown -R phil:phil *
```

substituting your username for phil.

now from your home directory type: 

```
ls -la
```

and see if your username is listed twice on all the files and folders (the .. folder should be owned by root)

As the error said, most of the files are gonna need 644 permissions, which means anyone can read it (r), only people in your group can write to it (w) and only people in your group can execute it (x).  If its a directory, the equivalent to this is 755.  The problem is, some files and folders in home shouldn't be accessible at all from your group, just you.

So the thing that may get you back up and running won't be very safe from a security standpoint. 

But try this from the home directory:
```
chmod -R 644 *
```

Then try to boot into the broken system again, and see if that worked. 

Its tough to try to rebuild from a permissions problem, so you may have to reinstall, but this should allow your username access at least to the config files it needs to load the system, so there's a chance it will work.

---

### Post by mhgsys on 2009-06-28
user's $HOME/.dmrc file is being ignored. This prevents default session / language from being saved. File should be owned by user and have 644 permissions....."


To repair this issue:


Go in to console with Ctrl+Alt+f1 (f2, f3,f4, etc)
and type in:


```


sudo chmod 644 /home/username/.dmrc

```
```

sudo chown username /home/username/.dmrc

```
```

sudo chmod 755 /home/username

```

**In case you can't go into console try booting recovery modes.in case you cant boot recovery modes boot a live cd and mount your disk)

---

### Post by flugh on 2009-06-28
If the error message contains "user root does not exist", there's a possibility of a really munged /etc/passwd too right? Maybe a:
~/$ grep root /etc/passwd
just to be sure somehow the actual root account hasn't been deleted.

(been a while, my linux mojo is rusty, sorry if that's totally in the wrong direction)

---

