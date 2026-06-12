---
title: "Working ISO refuses to mount under Ubuntu"
date: 2010-07-04
forum: General Help
---

### Post by The Flying Penguin on 2010-07-04
I have an ISO that I am trying to mount under Ubuntu so I can install its contents under Wine. I know it works. I have mounted and installed from it using Windows 7 and Daemon tools. I even booted into XP under VB and mounted the image and it worked fine. I have it stored on an NTFS partition that I use for all my storage.

Gmount gives me this error: "An error occured
 wrong fs type, bad option, bad superblock on /dev/loop0,       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so"

AcetoneISO gives me:   p, li { white-space: pre-wrap; }  Error, could not mount image.
 
 Solution:
 Try converting the image to ISO or extract the content to a folder from the upper menu "Image Conversion."
 NOTE: it is NOT possible to mount multi-sector images.
 For more information, please visit official website: [http://www.acetoneteam.org](http://www.acetoneteam.org)

Kiso gives me: This does not seem to be a valid image !

And I even tried mounting in terminal. This is what I did.
1) sudo  mkdir /media/iso
2) I navigated to the directory containing my ISO
3) sudo mount -t iso9660 rld-sims3.iso /media/iso -o loop

That gives me the error: "No such file or directory".

I am at a loss here as to why this won't work.

I'm on 64bit if that matters...

---

### Post by 4Orbs on 2010-07-04
Just a guess. When you use the terminal command to mount an iso, you need to include the full path along with the name of the iso file. Just navigating to the folder that contains the iso will not work.
EXAMPLE:
sudo mount -t iso9660 /home/MY-HOME/MY-ISO-FOLDER/rld-sims3.iso /media/iso -o loop

I could be wrong, however.

---

### Post by The Flying Penguin on 2010-07-04
Makes sense but it still doesn't work.

This is exactly what I typed:
sudo mount -t iso9660 /media/Additional\ Space/Files/Installation\ Files/Games/The\ Sims\ 3/rld-sims3.iso /media/iso -o loop

I get this error: /media/Additional Space/Files/Installation Files/Games/The Sims 3/rld-sims3.iso: No such file or directory

The ISO is 5.6GB so it must be from a dual layer dvd. Could that be an issue? Is Ubuntu unable to mount such an ISO?

---

### Post by 4Orbs on 2010-07-04
Do you have enough space in your Ubuntu home folder to copy the iso onto your desktop just for testing purposes? That would be my starting point for troubleshooting (I'm not an iso guru).

Personally, I have gmountiso installed so I don't ever use the terminal for mounting my game iso's .... also have you checked in the wine hq database to see if sims3 will work in wine? You might be wasting your time trying to install something that is already confirmed to be a no-go

---

### Post by The Flying Penguin on 2010-07-04
Yes, The Sims 3 works under Wine: [http://appdb.winehq.org/objectManager.php?sClass=application&iId=9732](http://appdb.winehq.org/objectManager.php?sClass=application&iId=9732) :D

And I just tried putting the ISO in my home directory.

```
 :~$ sudo mount -t iso 9660 home/masterchief/sims3/rld-sims3.iso /media/iso -o loop
Usage: mount -V                 : print version
       mount -h                 : print this help
       mount                    : list mounted filesystems
       mount -l                 : idem, including volume labels
So far the informational part. Next the mounting.
The command is `mount [-t fstype] something somewhere'.
Details found in /etc/fstab may be omitted.
       mount -a [-t|-O] ...     : mount all stuff from /etc/fstab
       mount device             : mount device at the known place
       mount directory          : mount known device here
       mount -t type dev dir    : ordinary mount command
Note that one does not really mount a device, one mounts
a filesystem (of the given type) found on the device.
One can also mount an already visible directory tree elsewhere:
       mount --bind olddir newdir
or move a subtree:
       mount --move olddir newdir
One can change the type of mount containing the directory dir:
       mount --make-shared dir
       mount --make-slave dir
       mount --make-private dir
       mount --make-unbindable dir
One can change the type of all the mounts in a mount subtree
containing the directory dir:
       mount --make-rshared dir
       mount --make-rslave dir
       mount --make-rprivate dir
       mount --make-runbindable dir
A device can be given by name, say /dev/hda1 or /dev/cdrom,
or by label, using  -L label  or by uuid, using  -U uuid .
Other options: [-nfFrsvw] [-o options] [-p passwdfd].
For many more details, say  man 8 mount .

```I'm not sure exactly what this is telling me to do..

---

### Post by 4Orbs on 2010-07-04
This time it looks like you made a typo error... there shouldn't be a space between iso and 9660

EDIT: also there should be a slash before home
```
sudo mount -t iso9660 /home/masterchief/sims3/rld-sims3.iso /media/iso -o loop

```

---

### Post by The Flying Penguin on 2010-07-04
Ok, I fixed the space and then got a "No such file or directory" error message.

---

### Post by 4Orbs on 2010-07-04
OK. I added an edit to my post while you were posting. Check it out.

Also, you need to first configure wine to see your new mount point /media/iso and use it as the virtual drive. Do that before anything else. And you need to make sure the windows .exe will be opened by wine instead of the Ubuntu archiver.

Open the "Configure Wine" thing and select the "Drives" tab then use the button to navigate to your /media/iso folder and specify it as a new drive and set it's type to cdrom. Be sure to specify the audio device under the audio tab also.

Once your iso is mounted, open the the /media/iso folder and find the install.exe for sims3, right-click on the exe and specify that it should be opened with the "Wine program loader" (or whatever it's called) and not the archiver.

After you've done the above steps, you can double-click the install.exe for sims3 and your installation should proceed with no problems. Fingers crossed.

---

### Post by The Flying Penguin on 2010-07-04
sudo mount -t iso9660 home/masterchief/sims3/rld-sims3.iso /media/iso -o loop

That gives me the no such file or directory error. I can navigate there through terminal and see the ISO just fine. It makes no sense.

---

### Post by 4Orbs on 2010-07-04
You gotta have the slash before home in the file path. It would be far easier to just install gmountiso and use it to mount the iso rather than typing paths in the terminal. Or just copy and paste the below into the terminal.
```
sudo mount -t iso9660 /home/masterchief/sims3/rld-sims3.iso /media/iso -o loop
```

---

### Post by The Flying Penguin on 2010-07-04
Ok, I pasted exactly what you said and I got a no such file or directory error.

And when trying to usde gmountiso it gives me this error:

An error occured
 wrong fs type, bad option, bad superblock on /dev/loop0,       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

---

### Post by 4Orbs on 2010-07-04
Is this iso maybe something like a .bin file that was renamed to .iso? I know you can do things like that in Windows when using Daemon tools, but don't know if it works the same in Linux.

---

### Post by The Flying Penguin on 2010-07-05
Interesting you should ask that as AcetoneISO recommends that I convert the image to ISO format. So perhaps it isn't an ISO and was just renamed. I never renamed it but someone else may have. When I tell Acetone to convert it, it warns me that ISO9660 doesn't support multiple layers and I may lose copyright information. I guess I can try anyway and see what happens.

UPDATE:

So I tried converting it and then I received an error saying that I am trying to convert to the same format as the source. So I'm pretty sure this is certainly an ISO file.

Acetone tells me that I cannot mount a multi-sector image. Perhaps this has something to do with the problem? Is there a special way to mount a multi-sector image in Ubuntu?

---

### Post by 4Orbs on 2010-07-05
At this point I can only guess as to what the problem could really be. Acetone might be throwing the error simply because the file extension is already .iso and therefore unable to detect it's true nature. The actual source could be .bin or a number of other extensions that can be renamed to .iso and still work in Windows with Daemon tools.

I suppose it may be possible to rename the file to .bin and then try to convert it to .iso, but if the source was something other than .bin you could be wasting an enormous amount of time during the conversion only to receive an error at the very end of the process. If the file is truly an .iso file but cannot be mounted in Ubuntu.... the reason is beyond my realm of understanding. Hopefully someone else will read this thread and offer a workable solution.

And as for the multi sector image question; I think all game disks are multi sector. The games I've converted with Alcohol 120% (in Windows) are loaded with a bunch of hidden sectors that consume most of the time waiting during the conversion to .iso, and during the conversion the program shows the estimated time of completion as being hundreds of hours away... although I've never actually had to wait more than an hour for the process to complete.

---

### Post by bulletxt on 2010-07-06
> **4Orbs said:**
> At this point I can only guess as to what the problem could really be. Acetone might be throwing the error simply because the file extension is already .iso and therefore unable to detect it's true nature. The actual source could be .bin or a number of other extensions that can be renamed to .iso and still work in Windows with Daemon tools.

I suppose it may be possible to rename the file to .bin and then try to convert it to .iso, but if the source was something other than .bin you could be wasting an enormous amount of time during the conversion only to receive an error at the very end of the process. If the file is truly an .iso file but cannot be mounted in Ubuntu.... the reason is beyond my realm of understanding. Hopefully someone else will read this thread and offer a workable solution.

And as for the multi sector image question; I think all game disks are multi sector. The games I've converted with Alcohol 120% (in Windows) are loaded with a bunch of hidden sectors that consume most of the time waiting during the conversion to .iso, and during the conversion the program shows the estimated time of completion as being hundreds of hours away... although I've never actually had to wait more than an hour for the process to complete.

Let's discover together what kind of image it is.
Open a terminal and type:     file   image.iso

Of course replace "image.iso" with your iso file name. I'm quite sure the output will report "data" and not "iso9660 filesystem"  :)

---

### Post by The Flying Penguin on 2010-07-07
Bulletxt, I tried what you said.

First, I tried with the image I have been using and I got another no such file or directory error. I don't know why I keep getting these.

So I figured maybe I need to "re-image" this image. I went into Windows 7, mounted it with Daemon tools, and then made an image from the virtual drive using Alcohol 120%. I selected the ISO option.

I still get the no file or directory error when trying to mount the new image but now when I run the file command you gave me, it says data.

---

### Post by 4Orbs on 2010-07-07
About the "no such directory or file" error, if the file really exists and you are entering the file name correctly then the terminal should see it. I think this problem has more to do with the file path. Where do you have your file saved? The terminal opens in your personal home directory by default. So the file path must be adjusted in order for the terminal to find the file. So if the file is saved in a folder on your desktop, the file path would be this: (the absolute path) /home/masterchief/Desktop/sims3/rid-sims3.iso or a shorter version would be (assuming the terminal is still opened to the default location) Desktop/sims3/rid-sims3.iso or you can first tell the terminal to relocate itself to any folder you choose by using the cd command (cd means change directory), so first you would enter in the terminal; cd /home/masterchief/Desktop/sims3 then you could just enter the mount command without any path pieces - sudo mount -t iso9660 rid-sims3.iso /media/iso -o which should mount without errors, or at least no errors of "no such directory or file"... but you still might get the error "wrong fs type" etc.

EDIT: gmountiso has no problem finding the file, but won't mount it because of the "wrong fs type" and that is why I suspect you are not entering the correct file path when you use the terminal.

---

### Post by The Flying Penguin on 2010-07-07
I have the ISO in my home directory in a folder called sims3.

I have tried entering:

sudo mount -t iso9660 /home/masterchief/sims3/rld-sims3.iso /media/iso -o loop
sudo mount -t iso9660 /sims3/rld-sims3.iso /media/iso -o loop
sudo mount -t iso9660 sims3/rld-sims3.iso /media/iso -o loop

Just now, I even tried putting the ISO right in my home directory and not in a folder. So I typed:
sudo mount -t iso9660 rld-sims3.iso /media/iso -o loop

All of them give me no such file or directory.

I even tried, as you suggested, navigating to the folder first and then entering the command. It gives me the same thing!

Using the cd command I am able to navigate to the folder containing my ISO and using the ls command, it even shows the ISO is there! So something is fishy here.

---

### Post by 4Orbs on 2010-07-07
Have you checked to see if there is a /media/iso folder? Maybe if you change the permissions on that folder to give read and write access to others or all users. I'm just guessing now.

EDIT: You might even try renaming the iso. You may also want to take a look inside the iso while it's mounted in Windows and see if there is anything odd, like maybe a second iso stored inside. In Windows you can right-click on the mounted iso and choose "Explore" or even use 7zip to expose it's innards.

---

### Post by GiuseppeP on 2010-07-08
I solved this problem with:
sudo mount -t udf /home/utente/sims3/sims3.iso /media/iso  -o loop

but the installation fail for a CRC Error why?

---

### Post by Ocxic on 2010-07-08
CRC Error = checksum issue = the file/image got corrupted.

---

### Post by GiuseppeP on 2010-07-08
> **Ocxic said:**
> CRC Error = checksum issue = the file/image got corrupted.

Yes, but the image file isn't corrupted, in windows it works correctly

---

### Post by The Flying Penguin on 2010-07-08
I read something about Ubuntu having trouble with certain images that were made under Vista, in particular ISOs made using the udf file system. Perhaps this is the problem.

I'll try to find some links.

I really wish I could get this going. I'd like to play the game in Ubuntu instead of having to reboot into Windows.

---

### Post by The Flying Penguin on 2010-07-13
Hey, I have an idea!

Could I just mount the game in XP in a VM and then share the drive over the network and point wine to the shared virtual drive? I could even move the iso to a XP machine if it won't work with VirtualBox.

I don't have the time at the moment to try this out. Should I give it a go when I have a chance or is this not possible?

---

### Post by Ocxic on 2010-07-13
Sounds like it should work. 
if not a little overly complicated, and you'll most likely see a small performance decrease.
Give it a shot!

---

### Post by The Flying Penguin on 2010-07-13
> **Ocxic said:**
> Sounds like it should work. 
if not a little overly complicated, and you'll most likely see a small performance decrease.
Give it a shot!

Great. I'll give it a go when I have a chance.

Hopefully, I will only see a performance hit during the install process. Since I rock an ultra-portable with no optical drive I aways either use a no-cd crack or mount the ISO to play my games. I'm hoping the cracked .exe to play the game with no cd will work under Wine. *Crosses fingers*

---

### Post by The Flying Penguin on 2010-07-20
Well, I finally managed to install this game. Sadly, I never managed to make the iso mount in Ubuntu. I wish I could figure out why. Instead, I just mounted it on an XP machine using Daemon Tools (really good app for Windows) and shared it on my network. I then was able to mount the network drive on my Ubuntu machine and then was able to install the game using Wine.

All that effort, and the game doesn't launch! The Wine desktop pops up for less than a second and that's it! That's not a problem for this thread though.

So, for anyone having a similar issue, you may need to just mount the iso on another machine and then mount the network drive in Ubuntu. So, not really solved but I found a workaround so I'll mark it as solved. ;)

---

### Post by dc_williamson on 2010-12-05
Hi,

Stumbled across this post...

Wondering if
sudo mount -t iso9660 $HOME/sims3/rld-sims3.iso /media/iso -o loop
or
sudo mount -t iso9660 ~/sims3/rld-sims3.iso /media/iso -o loop
would work?

dc_.

---

### Post by danbishop on 2011-03-06
The reason it didn't work was because you were using the wrong fstype. I'm pretty sure The Sims 3 DVD is NOT iso9660, I *think* it's UDF. The DVD is designed to work automagically on both Windows and OS X which is why the standard iso9660 is not used.

Whatever format it is in though, you're best to use "auto" that will almost certainly work :)


sudo mount -t auto ~/sims3/rld-sims3.iso /media/iso -o loop


:)

---

