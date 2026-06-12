---
title: "I think I broke my computer"
date: 2010-07-31
forum: General Help
---

### Post by Scooter_X on 2010-07-31
Hey gang, my system was having some bugs, I'd been installing and un-installing stuff, who knows what happened, but it was running slow, conky quit working, cairo-dock was wack... anyway. I was running Karmic. I had partitioned specifically with 1 partition for root (/), another for swap space and another for home (/home) with the understanding that if I later wanted to fresh install the OS I could keep my home folder and not have to worry about backing up everything in /home... Well, I clean installed lucid, I formatted my '/' partition as well as my 'swap' partition, left my /home partition where it was, and mounted everything in the proper locations. Anyway, I logged in after restarting and my desktop looks just like it did before I installed lucid, and I have NO title bars on any of my windows... what's going on, anyone have any ideas? I'd sure appreciate some help. I told my wife that I'd "fix" the computer, and now it's more broke than when I started. :P Thanks. Peace.

---

### Post by mwolfe on 2010-07-31
Try disabling desktop effects.. Right click on your desktop and go to the desktop appearance (I think thats what its called, unfortunately i'm not at home and thus not on an ubuntu pc). From there you can find the menu which gives 3 options for effects, choose the first (basic/no effects).
See if that fixes the issue.. If thats the problem you might have issues with compiz or emerald.
I haven't messed with cairo dock but that could be related.
Keep in mind that by using the same /home partition you are using all the same settings files as you were before and programs that have since been updated may have slight nuances with the old config files.. If you had a highly customized desktop before that could be an issue. Easiest way to fix that is to just delete the configs and re-launch the programs.. I'd start with disabling compiz to see if that fixes it and go from there.

---

### Post by dino99 on 2010-07-31
hey man, big time, are you ready to be spanked  :lolflag: your wife will appreciate =D>

ok i stop joking

this is a common issue flooding this forum: right click on destop and select "create a new launcher", the top panel might popup

sudo apt-get update
sudo apt-get install -f
sudo dpkg --configure -a

metacity --replace

have a good time :D

---

### Post by prshah on 2010-07-31
> **Scooter_X said:**
> I have NO title bars on any of my windows...

Broken window decorator; press Alt+F2, and give the command ```
gtk-window-decorator --replace
``` in the command box that pops up; press Enter, the window decorations (title bar, command buttons) etc should appear within a few seconds.

If they don't repeat the same command, but this time from a terminal (Applications-Accessories-Terminal) and post back the output.

---

### Post by Scooter_X on 2010-07-31
> **mwolfe said:**
> 
Keep in mind that by using the same /home partition you are using all the same settings files as you were before and programs that have since been updated may have slight nuances with the old config files.. 

Is there a directory where I can find all of these config files and delete them? Then what happens if I were to do that? Are they re-created by ubuntu if they aren't found?

My hopes were that it would be completely a clean fresh start and I could just install a couple of the programs I needed again and go from there. Looks like I got a lot of work ahead of me to get it all brand new... dangit.

---

### Post by Nick_Jinn on 2010-07-31
When things get hairy like that, I plop in a Knoppix disk and save all files from both windows and linux partitions....make sure you save all the files from all users....administrator, all users, default user, ect.....Downloads, home folder, music, pictures, ect..Then reinstall your operating systems. If you need help replacing windows message me. Ubuntu is easy to replace.

Its time consuming to reinstall, but its not the end of the world. Windows should run faster with a clean install, since it tends to get 'bent out of shape' the longer you use it.

---

### Post by Scooter_X on 2010-07-31
> **prshah said:**
> Broken window decorator; press Alt+F2, and give the command ```
gtk-window-decorator --replace
``` in the command box that pops up; press Enter, the window decorations (title bar, command buttons) etc should appear within a few seconds.

If they don't repeat the same command, but this time from a terminal (Applications-Accessories-Terminal) and post back the output.

That worked. Got my title bars back. Thank you!

> **Nick_Jinn said:**
> When things get hairy like that, I plop in a Knoppix disk and save all  files from both windows and linux partitions....make sure you save all  the files from all users....administrator, all users, default user,  ect.....Downloads, home folder, music, pictures, ect..Then reinstall  your operating systems. If you need help replacing windows message me.  Ubuntu is easy to replace.

Its time consuming to reinstall, but its not the end of the world.  Windows should run faster with a clean install, since it tends to get  'bent out of shape' the longer you use it.     

Well that's probably what I'm gonna' do. Basically bust out an external drive, dump everything I want onto it  (I have LOADS of stuff I want to keep) and go from there.


I think in the future I'm gonna make a folder in /home called 'personal docs' or something to put all my documents, downloads, music etc folders into and instead of mounting my main storage partition at /home i will mount it at '/home/personal docs', and then if I want to do a 'clean' install such as what I was trying to do here, all I would have to do after installing is re-route my documents, pictures, videos, etc directories to appear in 'places' and such. Easy-cheesy lemon-squeezy. That would probably work, you think? My /home would wind up on my root partition, and everything else on another. Gosh I'm smart.

---

### Post by DrMelon on 2010-07-31
The /home partition likely includes configuration files from the previous version of Ubuntu, which is why some stuff still looks the same, and the decoration manager broke (probably trying to refer to a theme that no longer exists, or manage it in a way that has been removed).

---

### Post by Scooter_X on 2010-07-31
> **DrMelon said:**
> The /home partition likely includes configuration files from the previous version of Ubuntu, which is why some stuff still looks the same, and the decoration manager broke (probably trying to refer to a theme that no longer exists, or manage it in a way that has been removed).

That's exactly what I'm thinking. That's why I want to mount my 'data partition' to something more specific than /home.

And yea, I had a beryl theme previously, I wondered if it had something to do with it.

---

### Post by WorMzy on 2010-07-31
Probably, if you haven't installed Emerald on your new installation, and you're still using the same /home, then gconf will have entries telling the system that it's supposed to use Emerald to decorate the windows, which, of course, doesn't exist on the new installation. This is why recycling /home can be tricky, and isn't really encouraged.

The preferred way of recycling /home is to just recycle the Documents/Pictures/Downloads/etc folders, preferably keeping them bundled together on a dedicated partition, and 'mount --bind'ing them over the new installation's /home/*Documents(etc) folders using fstab.

---

### Post by Scooter_X on 2010-07-31
> **WorMzy said:**
> 
The preferred way of recycling /home is to just recycle the Documents/Pictures/Downloads/etc folders, preferably keeping them bundled together on a dedicated partition, and 'mount --bind'ing them over the new installation's /home/*Documents(etc) folders using fstab.

THAT sounds really smoooooth. I'm not horribly savvy with fstab however. I just barely learned how to basically interpret the fstab file like yesterday, no joke. How would the line look if I wanted to mount from sda2 my Documents folder for example?

---

### Post by masque7 on 2010-07-31
I always knew doing this would break things. What's the best way to have /home as it's own partition? Takes away the point if all your old configs are still there messing things up. Pehaps remove all the dot files before installing onto /?

---

### Post by WorMzy on 2010-07-31
```
UUID=7A5C94995C94522D                     /media/Terastore        ntfs user,uid=1000,gid=100,umask=002,exec,rw 0 0
/media/Terastore/Collection/              /home/wormzy/Collection none bind                                    0 0
/media/Terastore/Users/WorMzy/Pictures/   /home/wormzy/Pictures   none bind                                    0 0
/media/Terastore/Users/WorMzy/Documents/  /home/wormzy/Documents  none bind                                    0 0
/media/Terastore/Downloads/               /home/wormzy/Downloads  none bind                                    0 0
/media/Terastore/Videos/                  /home/wormzy/Videos     none bind                                    0 0
```

Here's the relevant parts of my fstab (excuse the formatting, I like to have the columns lined up, so you'll probably need to scroll to read the entire line), I have a similar group of lines in my other Linux OS' fstabs (I'm on Arch Linux, I also use Debian 5.10, and Ubuntu 9.10 and 10.04).

To give a bit of an explanation, I have two terabyte drives in my PC; one for OS's, and one for data storage. The data storage is formatted as NTFS, so it can be accessed from either Windows or Linux, and is called Terastore (imaginative, I know =P). It contains several main folders, like Downloads, Videos, Collection (music), which are mounted on top of my /home/ folders of the same name. The actual /home folder is just part of the / partition of each OS, so each one can have it's own config files, and none will conflict with each other.

There are a few dot folders that I like to keep syncronised, such as .gimp-2.6, .fonts, and .scripts (for conky scripts), so I copy them across periodically. I could use the same bind technique for them, but it's not too much of a big deal - the main folders are taken care of.

---

### Post by Scooter_X on 2010-07-31
Ok, I think I got it. Let me throw this out there:

```

UUID=a68c8f36-38f7-4c24-bb58-9bbe28782ea1     /mnt/personalFiles      ext4 defaults    0 2
/mnt/personalFiles/Documents                  /home/Documents         none bind        0 0
etc
etc
etc
```That's probably about how I'm gonna have to get it done, yea? mount and pass were listed as 0 and 2 respectively for the partition as it is now mounted as /home. I don't know what that means. I notice yours are both 0...

This is slick.

---

### Post by WorMzy on 2010-07-31
The 2 indicates that you want fsck to check the filesystem when you mount the partition, which is fine for exr4, but since I'm using ntfs, fsck wouldn't know what to do with it.

The rest of your fstab entries looks fine, but you're missing the username after /home/ on the second argument of your Documents line. And you need to make sure that the mount point exists before it'll allow you to mount a file system there, so if you don't already have a /mnt/personalFiles, make sure to make one before you test your fstab.

Remember, you can test your fstab by running

```
sudo umount -a && sudo mount -a
```


Oh, and one final thing: if you set Ubuntu up at installation time to mount the partition as /home, you may need to recreate your /home/USERNAME folder, chown it to yourself, and copy all the other files into it before you restart.

---

### Post by Scooter_X on 2010-08-02
Excellent. Thank you WorMzy for helping with the fstab thing, I got it working wonderfully now. This fstab thing really is cool. I was just going to do 'shortcuts', but that don't work as nice.

---

