---
title: "Amarok doesn't recognise audio cd's"
date: 2011-09-08
forum: General Help
---

### Post by searchfgold6789 on 2011-09-08
Hi,
I am not able to play audio CD's using Amarok. They are supposed to appear as a collection, from what I gather...but they do not. I put the CD in, and then a device notifier appears asking me if I want to play the audio CD. When I click the message Amarok opens (best splash screen ever?!) but the CD does not appear or play.
I would be eternally grateful for any help with this issue. 
 - search

EDIT: **Dear Viewers of the future,**
According to [helmut_hed]("http://ubuntuforums.org/member.php?u=32195"), the rumor is that this will be *fixed* in Amarok version 2.5! I am using Natty Narwhal and cannot figure out how to install th beta, and will be content with waiting for 2.5 to become mainstream.

---

### Post by searchfgold6789 on 2011-09-09
bump

---

### Post by searchfgold6789 on 2011-09-12
I am doing some googling and am beginning to see that it has to do with  whether or not KDE uses an HAL or not. If this is a problem, is there a  setting I can change to turn the HAL "on"?

---

### Post by searchfgold6789 on 2011-09-13
bump

---

### Post by searchfgold6789 on 2011-09-13
bump.
Courtesy xkcd comic: [http://xkcd.com/950/](http://xkcd.com/950/)

---

### Post by searchfgold6789 on 2011-09-14
bump.
more xkcd: [http://xkcd.com/783/](http://xkcd.com/783/)

---

### Post by searchfgold6789 on 2011-09-14
OK, I just realized I could access my CD's **but** I still cannot play them with Amarok which was my original problem. Anyone?
:popcorn:

---

### Post by searchfgold6789 on 2011-09-14
Please tell me if this is getting old, but:
bump

---

### Post by searchfgold6789 on 2011-09-17
bump

---

### Post by searchfgold6789 on 2011-09-18
bump

---

### Post by Lisiano on 2011-09-18
Okay so it seems amarok refuses to read the disk on legal reasons. Dolphin does not mount the disk. Quick and dirty workaround, go to the CD on Dolphin and Rip the CD.
The folders show the codec the file will be in after you "Copy" it. So let's say I want Ogg.
I put my Radiohead - Rainbow disk in and go to CD-ROM then go to Ogg Vorbis and drag the whole album or just the songs I want to some folder in ~/Music/

EDIT: As you already noticed. Playing Audio CDs will not viable using Amarok in Kubuntu using standard means to play Audio-CDs. You still can play them if you Rip the files with the above method or use Nautilus (Gnome app) to mount the disk.

---

### Post by oldos2er on 2011-09-18
> **Lisiano said:**
> EDIT: As you already noticed. Playing Audio CDs will not be viable in Kubuntu. 

This is simply not true. I use either kaffeine or vlc to play audio CDs in Kubuntu.

---

### Post by searchfgold6789 on 2011-09-19
Okay, I have collectied some more information. Apparently, the CD-ROM is never actually mounted, instead, CDDB reads the disk in some way and then presents information to me in the form of a "file structure". I can "copy" information from this "file structure" as Lisiano said. Instead I would like the CD to actually be mounted, with all the data laid bare before my eyes. I suppose this would mean being able to automatically mount the CD whenever I pop it into the drive. How would I go about doing this? Is there software, perhaps?

---

### Post by oldos2er on 2011-09-19
> **searchfgold6789 said:**
>  I suppose this would mean being able to automatically mount the CD whenever I pop it into the drive. How would I go about doing this? Is there software, perhaps?

That should be the default behavior. Does your CD drive work with data CDs?

---

### Post by searchfgold6789 on 2011-09-19
Yes, it works with Data CD's. They have three options: gwenview, K3B, and Dolphin, whereas my audio CD's have only one which is Amarok.

---

### Post by Lisiano on 2011-09-20
Well one solution is to use Nautilus (Which I did that time since I have both Gnome and KDE) or to manually mount the disk using gvfs
First we need gvfs (Note: This will pull down policykit-1-gnome but other than that it won't download half of gnome [Didn't on a VM of 11.10])
```
sudo apt-get install gvfs-bin
```
```
gvfs-mount cdda://sr0
```
You can replace sr0 with cdrom if you wish.
Now you will find the cd mounted under ~/.gvfs/cdda mount on sr0 or under ~/.gvfs/cdda mount on cdrom. There you will find the files in .wav and they can be easily played under Amarok.
If anyone could point me how to add actions to the "Available Devices" I might be able to cook up a small script to mount it and add the files to Amarok.
> **oldos2er said:**
> This is simply not true. I use either kaffeine or vlc to play audio CDs in Kubuntu.

I meant that as it will not be viable using Amarok in Kubuntu using standard means to play Audio-CDs. I know other stuff plays well.

Also, anyone noticed that if you eject and insert the disk, Amarok will recognize the CD, find the information and get the cover art? Sadly still fails to read it on it's own. A screenshot for the skeptic

---

### Post by oldos2er on 2011-09-20
> **searchfgold6789 said:**
> Yes, it works with Data CD's. They have three options: gwenview, K3B, and Dolphin, whereas my audio CD's have only one which is Amarok.

Ok, I thought there might be a hardware problem with your CD drive. If you install kaffeine, it should show up as an option when you insert an audio CD.

---

### Post by oldos2er on 2011-09-20
> **Lisiano said:**
> I meant that as it will not be viable using Amarok in Kubuntu using standard means to play Audio-CDs. I know other stuff plays well.


That might be what you meant, but it's not what you said.

---

### Post by searchfgold6789 on 2011-09-20
> If you install kaffeine, it should show up as an option when you insert an audio CD. 	Yes, but unfortunately, Kaffeine is not Amarok.
I've got 3 different CD-ROM's, as you can see from the paste in my signature. Each of them will work with VLC or Kaffeine but not Amarok. 
I tried the commands for gvfs but none of them worked! I do not see my CD-ROM appear in the specified home folder.
Also, re-insterting the CD will not get any response from Amarok.
Does anyone know if this is planned to be fixed in future versions of Amarok?
I don't know how to add stuff to Available Devices *except* for under System Settings there is an option for it. I think. Yeah, there is: It's "Device Actions". Okay there ya go!
I am going to do some very heavy research now, into this matter, and create a tutorial later if I find anything.
 - search

---

### Post by Lisiano on 2011-09-20
Interesting, try looking at ```
gvfs-mount -l -i
``` under activation_root= there you should see what is needed to mount using cdda://. Or use -d /dev/sr0.

Also thanks for pointing out about where to add the options, now to research.

> That might be what you meant, but it's not what you said.Fixed. Dunno why I didn't edit it last time.

---

### Post by Lisiano on 2011-09-20
Okay. Looks like this short script will work
```
#!/bin/sh
gvfs-mount -d "$@"
amarok --play ~/.gvfs/cdda\ mount\ on\ `echo $@ | cut '-f3' '-d/'
```
Place it anywhere you wish. For example your home. If on a multi-user system then /bin or the likes.
And it seems Amarok takes the highest priority. So we modify it instead.
/usr/share/kde4/apps/solid/actions/amarok-play-audiocd.desktop
```
[Desktop Entry]
X-KDE-Solid-Predicate=OpticalDisc.availableContent & 'Audio'
Type=Service
Actions=Play;
X-KDE-Priority=TopLevel

[Desktop Action Play]
Name=Play Audio CD with Amarok (Workaround)
Icon=amarok
Exec=sh /path/to/script %d
X-Ubuntu-Gettext-Domain=desktop_extragear-multimedia_amarok
```
Basically change the name (Optional) and change the Exec from Exec=amarok --cdplay %f to Exec=sh /path/to/script %d

---

### Post by searchfgold6789 on 2011-09-20
```
Drive(1): CD/DVD Drive
  Type: GProxyDrive (GProxyVolumeMonitorGdu)
  ids:
   unix-device: '/dev/sr2'
  themed icons:  [drive-optical]  [drive]
  is_media_removable=1
  has_media=1
  is_media_check_automatic=1
  can_poll_for_media=1
  can_eject=1
  can_start=0
  can_stop=1
  start_stop_type=shutdown
  Volume(0): Audio Disc
    Type: GProxyVolume (GProxyVolumeMonitorGdu)
    ids:
     unix-device: '/dev/sr2'
    activation_root=cdda://sr2/
    themed icons:  [media-optical-audio]  [media-optical]  [media]
    can_mount=1
    can_eject=1
    should_automount=0

``````
gvfs-mount cdda://sr2

```...doesn't put anything in my ~/.gvfs file. It's empty:
```

ls -l ~/.gvfs
total 0

```Although the device spins into action and I can hear the CD spinning up quite audibly.
EDIT:::::::::::::trying your other post
Okay:
```
gvfs-mount -d cdda://sr2
Error mounting location: volume doesn't implement mount
```

---

### Post by Lisiano on 2011-09-20
Don't pass cdda:// if you use -d, like this```
gvfs-mount -d /dev/sr2
```

---

### Post by searchfgold6789 on 2011-09-20
Oddly enough:```
$ gvfs-mount -d /dev/sr2/
Error mounting location: Location is already mounted
```

---

### Post by Lisiano on 2011-09-20
Outputs of
```
mount
```
and
```
gvfs-mount -l
```
probably will explain this.

Note: Still trying to debug my workaround on a VM but it stubbornly refuses to cooperate, won't notice at all Audio-CDs. The VM itself that is, not Kubuntu.

---

### Post by searchfgold6789 on 2011-09-20
Ok, I rebooted, and it mounts like this:```
$ gvfs-mount -d /dev/sr2
Mounted /dev/sr2 at (null)
```The CD drive whirrs.
Thank you so much for the script. It makes the CD drive whir but I do not see anything else happening. Going to bed now, see you tomorrow.

---

### Post by Lisiano on 2011-09-20
Seems like it is getting mounted (Mounted /dev/sr2) the reason why it whirs but at the same time not mounted (at (null) ) reason why nothing else happens. Trying to find why this could be happening and a fix.

---

### Post by Lisiano on 2011-09-20
Found a solution. And no undocumented gnome stuff. "Mounting" a Audio-CD. Yes, some people will say it is impossible because it has no filesystem, why did I quote "Mounting" then? Nothing stops us from reading the information and presenting it to ourselfs. First we need to install some tasty source code.
```
sudo apt-get install cdfs-src
```
cdfs-src. Now due to the fact we don't have a cdfs-generic (Or at least I couldn't find one) we need to get dirty and compile it with a easy to use ncurses menu.
```
sudo module-assistant
```
Update -> Prepare -> Select -> Mark cdfs -> Build -> Install -> Exit.
All done. Now without further ado.
```
sudo mkdir /media/sr0
sudo mount -t cdfs /dev/sr0 /media/sr0
amarok --play /media/sr0/*
```
And for those that don't like sudo or want to script this add this line to your /etc/fstab. One for each drive, changing sr0 accordingly.
```
/dev/sr0       /media/sr0       auto        noauto,users,ro  0   0
```
After this, sudo can be easily dropped from the commands above.
Let me explain the fstab entry:
/dev/sr0 is our CD drive
/media/sr0 is where it should be mounted
auto means that the filesystem is detected automatically
noauto means the system is not automounted on boot.
users means that it is accessible to every user on the system, not just the person that used mount.
ro means it's read only, no need for rw any way.

So now we can just use this
```
mount /dev/sr0
amarok --play /media/sr0/*
```
And if you want to put it in a script like the gvfs one (I still don't know if that one works anywhere else beside my machine)
```
#!/bin/sh
mount $@
amarok --play /media/`echo $@ | cut '-f2' '-d/'`/*
```
Only problem is that I can't find a way to make amarok play the newly added stuff instead of what it was playing, well it adds them to the end of the current playlist so good on that.

---

### Post by oldos2er on 2011-09-21
As you might have guessed, I don't use Amarok. I do from time to time, but it seems eternally buggy in one way or another.

---

### Post by searchfgold6789 on 2011-09-21
**Thank you Mr Lisiano Sir!!!!!**
My goal was to be able to play audio CD's with Amarok without doing any copying of CD data, and that goal has just been accomplished! Thank you! At the very least I will add your scripts, etc. to the Ubuntu Natty Known Bugs and Workarounds Thread. With all due credit of course.
Solved.
 - search

---

### Post by helmut_hed on 2011-11-19
From what I've just learned on IRC, the problem may be due to [this bug]("https://bugs.kde.org/show_bug.cgi?id=254459") which is supposed to be fixed in Amarok 2.5, coming out sometime soon.  I don't know what the process would be for getting Kubuntu to take the upstream update, though...

---

