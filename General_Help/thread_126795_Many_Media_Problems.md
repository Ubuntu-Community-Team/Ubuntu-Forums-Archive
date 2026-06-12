---
title: "Many Media Problems"
date: 2006-02-07
forum: General Help
---

### Post by Gijith on 2006-02-07
Hello,

I recently setup a fresh install of Breezy. I've been having many problems, but so far, the most vexing have been with removable media. I'll take you through what I'm dealing with:

**1) DVDs.**
When I insert a DVD, the following things happen:
- Koqueror window pops up showing system:/media (okay by me)
- Another Konqueror window pops up, blank, but with little message window asking "Open 'media:/hda'?" and identifying the inserted disc as a DVD. If I select yes and choose from any video program, I get "/media/cdrom0 is a folder but a file was expected"
-Kaffeine opens with several errors (all Xine messages). The first reads "The source can't be read. Maybe you don't have enough rights for this, or source doesn't contain data (e.g:no disc in drive). (system:/media/hda)"... The second reads "No plugin found to handle this resource (dvd:/)" and gives the follwing details:
xine: cannot find input plugin for MRL [dvd:/]
xine: input plugin cannot open MRL [dvd:/]
xine: found input plugin  : DVD Navigator
demux_avi: invalid avi chunk "demux_avi: invalid avi chunk "demux_avi: invalid avi chunk "demux_avi: invalid avi chunk "demux_avi: invalid avi chunk "demux_avi: invalid avi chunk "demux_avi: invalid avi chunk "demux_avi: invalid avi chunk "demux_avi: invalid avi chunk "demux_avi: invalid avi chunk "demux_avi: invalid avi chunk "demux_avi: invalid avi chunk "demux_avi: invalid avi chunk "demux_avi: invalid avi chunk "demux_avi: invalid avi chunk "demux_avi: invalid avi chunk "xine: found demuxer plugin: AVI/RIFF demux plugin
xine: found input plugin  : file input plugin 

The third message reads "No plugin found to handle this resource (dvd://1)" and gives the following details:
xine: cannot find input plugin for MRL [dvd://1]
xine: input plugin cannot open MRL [dvd://1]
xine: found input plugin  : DVD Navigator
xine: cannot find input plugin for MRL [dvd:/]
xine: input plugin cannot open MRL [dvd:/]
xine: found input plugin  : DVD Navigator
demux_avi: invalid avi chunk "demux_avi: invalid avi chunk "demux_avi: invalid avi chunk "demux_avi: invalid avi chunk "demux_avi: invalid avi chunk "demux_avi: invalid avi chunk "demux_avi: invalid avi chunk "demux_avi: invalid avi chunk "demux_avi: invalid avi chunk "demux_avi: invalid avi chunk "demux_avi: invalid avi chunk "demux_avi: invalid avi chunk "demux_avi: invalid avi chunk "demux_avi: invalid avi chunk "demux_avi: invalid avi chunk "demux_avi: invalid avi chunk "xine: found demuxer plugin: AVI/RIFF demux plugin
xine: found input plugin  : file input plugin

And I get no playback. Any ideas?

**2) iPod**
I have an iPod nano. When I plug it in, the following things happen:
-A Konqueror window pops up (with address 'system:/media/sdb2' but blank) and gives the following error: "Could not mount device. Reported error was: mount: can't find /dev/sdp2 in /etc/fstab or /etc/mtab"
-A Konqueror window pops up (media:/sdb2) which shows the contents of the ipod (Control, contacts, calenders, etc)
-A Konqueror window pops up (media:/sdb1) with the with the following message: "An error occurred while loading media:/sdb1: The file or folder media:/sdb1 does not exist."
-A Konqueror window pops up (media:/hda) that is completely blank
-A Konqueror window pops up (system:/media) that shows my ipod, along with my DVD from problem 1. The ipod shows up as Mounted Removable Medium, Base URL: file:///media/sdb2, Device Node: dev/sdb2....
-The ipod seems to display properly if I go to it in amaroK, but I can't write to it. Or play from it.
-I get an error message (permissions) if I try to erase any of the material on it, even if I do it as sudo.
-The ipod does recharge.

Any help would be appreciated.

**Flash Drive**
I have an old 128m flash drive. When I plug it in, I get the same error as ipod: a Konqueror window pops up (with address 'system:/media/sdb2' but blank) and gives the following error: "Could not mount device. Reported error was: mount: can't find /dev/sdp2 in /etc/fstab or /etc/mtab"
However, the drive does seem to work okay and I seem to be able to read write from it.

The good news:
1) After following the ubuntu wiki, my windows partition has mounted successfully. 
2) After getting a new driver, my Labtec webcam works.
3) My Logitech gamepad shows up (in system settings) without error. I haven't gotten it to work yet, but I think that's a issue with my emulator (xmess through kxmame) and not kubuntu.

I haven't tried my digital camera yet. It's old and not listed under the supported cams in 'system settings', but I'll post again if I have issues with it.

If anyone can help, I'd be very appreciative. As you can tell, I'm still fairly new and very lost when it comes to certain things. I'm gonna go take refuge in my XP partition for a while.

Thanks a bunch.

-Gijith :-D

---

### Post by gingermark on 2006-02-07
[QUOTE=Gijith]**1) DVDs.**
When I insert a DVD, the following things happen:
- Koqueror window pops up showing system:/media (okay by me)
- Another Konqueror window pops up, blank, but with little message window asking "Open 'media:/hda'?" and identifying the inserted disc as a DVD. If I select yes and choose from any video program, I get "/media/cdrom0 is a folder but a file was expected"
-Kaffeine opens with several errors (all Xine messages). The first reads "The source can't be read. Maybe you don't have enough rights for this, or source doesn't contain data (e.g:no disc in drive). (system:/media/hda)"... The second reads "No plugin found to handle this resource (dvd:/)" and gives the follwing details:
xine: cannot find input plugin for MRL [dvd:/]
xine: input plugin cannot open MRL [dvd:/]
xine: found input plugin  : DVD Navigator
demux_avi: invalid avi chunk "demux_avi: invalid avi chunk "demux_avi: invalid avi chunk "demux_avi: invalid avi chunk "demux_avi: invalid avi chunk "demux_avi: invalid avi chunk "demux_avi: invalid avi chunk "demux_avi: invalid avi chunk "demux_avi: invalid avi chunk "demux_avi: invalid avi chunk "demux_avi: invalid avi chunk "demux_avi: invalid avi chunk "demux_avi: invalid avi chunk "demux_avi: invalid avi chunk "demux_avi: invalid avi chunk "demux_avi: invalid avi chunk "xine: found demuxer plugin: AVI/RIFF demux plugin
xine: found input plugin  : file input plugin 

The third message reads "No plugin found to handle this resource (dvd://1)" and gives the following details:
xine: cannot find input plugin for MRL [dvd://1]
xine: input plugin cannot open MRL [dvd://1]
xine: found input plugin  : DVD Navigator
xine: cannot find input plugin for MRL [dvd:/]
xine: input plugin cannot open MRL [dvd:/]
xine: found input plugin  : DVD Navigator
demux_avi: invalid avi chunk "demux_avi: invalid avi chunk "demux_avi: invalid avi chunk "demux_avi: invalid avi chunk "demux_avi: invalid avi chunk "demux_avi: invalid avi chunk "demux_avi: invalid avi chunk "demux_avi: invalid avi chunk "demux_avi: invalid avi chunk "demux_avi: invalid avi chunk "demux_avi: invalid avi chunk "demux_avi: invalid avi chunk "demux_avi: invalid avi chunk "demux_avi: invalid avi chunk "demux_avi: invalid avi chunk "demux_avi: invalid avi chunk "xine: found demuxer plugin: AVI/RIFF demux plugin
xine: found input plugin  : file input plugin

And I get no playback. Any ideas?
[/QUOTE]

There are a few things happening here. First off, have a look at [this thread](http://www.ubuntuforums.org/showthread.php?t=90457). It deals with a program called ivman, which is evil. Well, actually, it isn't but it is responsible for opening windows and programs up the ying-yang when you put a DVD into your drive.

As far as playback issues are concerned, have you installed all your codecs? libdvdcss2 is the one that comes to mind, but have a look [here](https://wiki.ubuntu.com/RestrictedFormats) for details on that kind of thing.

---

### Post by Gijith on 2006-02-07
Thank you very much for the response. By altering the ivman file, I was able to eliminate almost all the windows that pop up when I connect these devices or insert a disc. 

Following problems still remain:

Still getting error when DVD tries to play. 2 messages:
'Sources can't be read....'
'No plugin found... (dvd:/)'

ipod still having issues:
'Could not mount device - can't find /dev/sde2'
and I still can't write to it

I checked the DVD codecs. They've been installed (I'm guessing they came with Automatix, which I used a few days ago).


If anyone can point me in the right direction on these remaining issues, it would be wonderful.

---

### Post by Gijith on 2006-02-09
Bump.
If anyone has any ideas, please post. Thanks.
:D

---

### Post by prox2far on 2006-02-10
I guess you have added the extra repositories, otherwise you can find info on how to do this on the forum.

install videolan ( sudo apt-get install vlc )

this should solve all your DVD playback problems

---

### Post by Gijith on 2006-02-10
Yeah, as far as I can tell the repositories aren't the problem.
I've now gotten a DVD to play. And I think I'm starting to understand the DVD problem a little better. If xine is set to look for a DVD at /dev/dvd it will play no problem. But for some reason, whenever a DVD is inserted or when I try to play from the Storage folder, my xine settings somehow get set so that it's trying to read the DVD from system:/media/hda. And then I get the 'source can't be read...  source doesn't contain data' error. If i try to set the DVD path to /dev/dvd within the xine configuration panel in Kaffeine, it only lasts until a DVD is reinserted... Am I getting closer to the problem? Can anyone offer a hint on how to set the xine DVD path so it will stick? Or how to set the system so it won't look for a DVD in system:/media/hda?

ipod still not working. I'll post more on that some other time.

---

### Post by Gijith on 2006-02-17
Bump. If anyone has any ideas, please post. :D

---

### Post by eqisow on 2006-02-17
Have you tried using VLC instead of Xine, as suggested? As for the iPod, it seems to me as if your iPod is formatted using the HFS+ filesystem, which is not fully supported in Linux. If you want to confirm this you can check your /etc/mtab. The easiest way to fix this issue is to format it with the FAT filesystem, and the easiest way to do that is to grab a Windows machine, plug in your iPod, and simply go through the install process. The install software will do it automatically. If you don't have a Windows machine handy... things get tricky. [This]("http://people.csail.mit.edu/people/adonovan/hacks/ipod.html") guide is a good place to start. You might also find [GNUpod]("http://www.gnu.org/software/gnupod/") helpful.

One final note, when you get your iPod working, [GTKpod]("http://www.gtkpod.org/about.html") is definitely worth taking a look at. It's, more or less, iTunes for Linux.

---

### Post by Gijith on 2006-02-17
Thanks for the response

ipod is already formatted to FAT. Any other ideas?

Gijith

---

### Post by Gijith on 2006-02-17
I think I might have figured out why amaroK isn't working with my ipod. For whatever reason, when I press 'connect' in amaroK, it's reaching over into my mounted windows partition and accessing a folder there (something like /media/windows/Ipod_Control/.....) instead of actually accessing my ipod, which is mounted as /media/sdb2... Does anyone know how to fix this? I didn't see an easy way to configure it in amaroK gui. 

Thanks

Gijith

---

