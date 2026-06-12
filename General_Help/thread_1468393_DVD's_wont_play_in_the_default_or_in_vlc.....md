---
title: "DVD's wont play in the default or in vlc...."
date: 2010-05-01
forum: General Help
---

### Post by Adrienk on 2010-05-01
I put in a dvd into my portable dvd player because I have a net book and so ubuntu 10.4 (this also happened in 9.10) sais - would you like to play this with: movie player. I say yes it sais your missing packages to play this type of media, i tell it to search it fails to find anything.....

So i right click and open with vlc media player. the player opens and the play list opens with the words Floppy 00:00

I wait for a few seconds and click play it goes from the play simple to the pause back to the play in a matter of seconds with out playing the dvd...

onw windows VLC will play this dvd....

why not in linux?
How do I fix this?

---

### Post by 2hot6ft2 on 2010-05-01
You need the codecs to decode the dvd and since the next question you'll have is how to play web videos like youtube....

Let's just cut to the end and install it all at once so you can play pretty much everything.

I could spend a half hour saying go here click this open that  yada yada yada instead do this.

Open a terminal
Applications > Accessories > Terminal
and run these commands one at a time and your password wont be shown when you type it in just type it in and hit enter.
This first one enables the medibuntu repository for restricted codecs and such
```
sudo wget --output-document=/etc/apt/sources.list.d/medibuntu.list http://www.medibuntu.org/sources.list.d/$(lsb_release -cs).list && sudo apt-get --quiet update && sudo apt-get --yes --quiet --allow-unauthenticated install medibuntu-keyring && sudo apt-get --quiet update
```
Remove any browser media player plugin you currently have installed (totem-mozilla is installed by default, but you may have installed mozilla-mplayer or mozilla-plugin-vlc) like this:
```
sudo apt-get remove totem-mozilla mozilla-mplayer mozilla-plugin-vlc
```
then for all the multimedia, mp3's, divx web player, and dvd playback
```
sudo apt-get install ubuntu-restricted-extras libdvdcss2 gecko-mediaplayer
```
Oracle Java is part of the ubuntu-restricted-extras package so use your arrow keys and Tab key to select and Enter to accept the Java terms of use since Oracle now owns Sun.
And to get rid of one package in the restricted extras that causes problems:
```
sudo apt-get purge ttf-mscorefonts-installer
```
ttf-mscorefonts-installer bug report
[https://bugs.launchpad.net/debian/+source/msttcorefonts/+bug/431217](https://bugs.launchpad.net/debian/+source/msttcorefonts/+bug/431217)

[And to install Flash (the same as going to the adobe website) just click this link if using 9.04 or up, then on OK]("apt:adobe-flashplugin?channel=$distro-partner")

And you're done.

---

### Post by Adrienk on 2010-05-01
So I followed all of your instructions to a T and insalled everything with out a hitch. but why is the dvd drive called floppy 0? - is it mounted as such? How do I mount it as a dvd drive?

next up I still can't play dvd's still have the same issue in the movie player (Download pakages that it cant find) and in vlc media player - still does the play pause play thing...

---

### Post by Adrienk on 2010-05-01
Bump Need help please

---

### Post by 2hot6ft2 on 2010-05-01
> **Adrienk said:**
> So I followed all of your instructions to a T and insalled everything with out a hitch. but why is the dvd drive called floppy 0? - is it mounted as such? How do I mount it as a dvd drive?

next up I still can't play dvd's still have the same issue in the movie player (Download pakages that it cant find) and in vlc media player - still does the play pause play thing...
Beats me as to why it's seeing it as floppy0.
Is the DVD  a HDDVD or Blu-Ray? It's not the same as a standard DVD.

[Playing Blu-Ray and HD DVD Video]("https://help.ubuntu.com/community/RestrictedFormats/BluRayAndHDDVD")

The only other way I know of is this
> **wojox said:**
> You should be able with:

```
sudo apt-get install libdvdread4
```

```
sudo /usr/share/doc/libdvdread4/install-css.sh
```

---

### Post by Adrienk on 2010-05-01
This is a regular dvd 

so after doing that, I get it to play in Vlc media player except you know how a dvd when in vlc will give you like the chapters to click on and "click play to play the movie" all those options that come on dvds...ya./..no.....it just starts to play but all choppy and theirs no image just sound

what happens is vlc starts up gives me some error about cant set the dvds title and then it goes into playing, but its like vbo8, and vbo7 instead of "Charmed season 6"


how do i fix this?

---

### Post by 2hot6ft2 on 2010-05-01
Sounds strange. Do you have desktop effects enabled and have you tried disabling them?
System > Preferences > Appearance > Visual Effects
Set it to None
I'll have to throw a DVD in and see about the menus I'm pretty sure they should work normally in VLC.

---

### Post by Adrienk on 2010-05-01
no desktop effects.
Yours will work i am sure of it.

in windows mine even works and vlc has no isse playing dvds and what not but in linux it dosent work, how ever if I play videos off my ipod or off the harddrive they play fine, no issue - its just with the dvd drive. which works as a normal dvd drive, for burning and installing and bla...

but not when it comes to movies....

---

### Post by 2hot6ft2 on 2010-05-01
You're right. The menus worked fine on mine. I'm not sure what the problem is. Someone else will have to figure it out, I'm n not sure how to fix it.
Sorry I couldn't be more help. If I come across a fix I'll post back here.

---

### Post by 2hot6ft2 on 2010-05-01
Might try this
> **wolfen69 said:**
> let's try removing and reinstalling a couple things.
```
sudo apt-get purge libdvdread
```
```
sudo apt-get purge libdvdcss2
```
```
sudo apt-get clean
```
```
sudo apt-get autoremove
```
```
sudo apt-get install libdvdread libdvdcss2
```

---

### Post by Adrienk on 2010-05-01
```
adam@adam-laptop:~$ sudo apt-get purge libdvdread
[sudo] password for adam: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package libdvdread
adam@adam-laptop:~$ sudo apt-get purge libdvdcss2
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  libdvdcss2*
0 upgraded, 0 newly installed, 1 to remove and 2 not upgraded.
After this operation, 111kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 126187 files and directories currently installed.)
Removing libdvdcss2 ...
Purging configuration files for libdvdcss2 ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
adam@adam-laptop:~$ sudo apt-get clean
adam@adam-laptop:~$ sudo apt-get autoremove
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 2 not upgraded.
adam@adam-laptop:~$ sudo apt-get install libdvdread libdvdcss2
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package libdvdread
adam@adam-laptop:~$ 

```I don't think anything happened
I am not very good at reading this but i can tell that some things never existed and don't exist.
and here I took operating systems for four months....no wonder i almost failed....

so whats your prognosis of this?

---

### Post by 2hot6ft2 on 2010-05-01
> **Adrienk said:**
> [CODE]
**E: Couldn't find package libdvdread**

**E: Couldn't find package libdvdread**

I think that's the problem. It needs that to read DVD's.
What version of ubuntu are you using?
10.04 would be my guess.

---

### Post by 2hot6ft2 on 2010-05-01
Did you try this it seems to be replaced with libdvdread4
> **wojox said:**
> You should be able with:

```
sudo apt-get install libdvdread4
```

```
sudo /usr/share/doc/libdvdread4/install-css.sh
```

---

### Post by Adrienk on 2010-05-01
```
adam@adam-laptop:~$ sudo apt-get install libdvdread4
[sudo] password for adam: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
libdvdread4 is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 2 not upgraded.
adam@adam-laptop:~$ sudo /usr/share/doc/libdvdread4/install-css.sh
--2010-05-01 12:22:49--  http://packages.medibuntu.org/dists/lucid/free/binary-i386/Packages
Resolving packages.medibuntu.org... 88.191.82.11
Connecting to packages.medibuntu.org|88.191.82.11|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 8068 (7.9K) [application/octet-stream]
Saving to: `/tmp/dvdcss-yVaAzo/Packages'

100%[======================================>] 8,068       41.2K/s   in 0.2s    

2010-05-01 12:22:50 (41.2 KB/s) - `/tmp/dvdcss-yVaAzo/Packages' saved [8068/8068]

--2010-05-01 12:22:50--  http://packages.medibuntu.org/pool/free/libd/libdvdcss/libdvdcss2_1.2.10-0.3medibuntu1_i386.deb
Resolving packages.medibuntu.org... 88.191.82.11
Connecting to packages.medibuntu.org|88.191.82.11|:80... connected.
HTTP request sent, awaiting response... 503 Service Temporarily Unavailable
2010-05-01 12:22:50 ERROR 503: Service Temporarily Unavailable.

Dynamic fetch failed; Falling back to static fetch
--2010-05-01 12:22:50--  http://packages.medibuntu.org/pool/free/libd/libdvdcss/libdvdcss2_1.2.10-0.2medibuntu1_i386.deb
Resolving packages.medibuntu.org... 88.191.82.11
Connecting to packages.medibuntu.org|88.191.82.11|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 36812 (36K) [application/x-debian-package]
Saving to: `/tmp/dvdcss-yVaAzo/libdvdcss.deb'

100%[======================================>] 36,812      65.6K/s   in 0.5s    

2010-05-01 12:22:51 (65.6 KB/s) - `/tmp/dvdcss-yVaAzo/libdvdcss.deb' saved [36812/36812]

Selecting previously deselected package libdvdcss2.
(Reading database ... 126180 files and directories currently installed.)
Unpacking libdvdcss2 (from .../dvdcss-yVaAzo/libdvdcss.deb) ...
Setting up libdvdcss2 (1.2.10-0.2medibuntu1) ...

Processing triggers for libc-bin ...
ldconfig deferred processing now taking place

```apparently its the newest version and yes I am running the latest version of ubuntu 10.4

upon trying to play the video I get:

   [COLOR=#ff0000]Playback failure:[/COLOR]
 [COLOR=#000000]VLC cannot set the DVD's title. It possibly cannot decrypt the entire disc.[/COLOR]

---

### Post by 2hot6ft2 on 2010-05-01
Looks like it may work with xine
```
sudo apt-get install xine-ui
```
then it will be in
Applications > Sound & Video > xine

There seems to be a problem with dvdnav as reported here:
[http://ubuntuforums.org/showthread.php?t=1442299&page=2](http://ubuntuforums.org/showthread.php?t=1442299&page=2)
But xine uses it's own dvdnav, not the same one as vlc and Mplayer

If that doesn't work the only other option I've found so far is to download and compile the latest xine and install it
[xine download link]("http://prdownloads.sourceforge.net/xine/xine-lib-1.1.18.1.tar.bz2")

[Instructions for compiling and installing it]("http://www.xine-project.org/faq#id628636")

Still looking.

Might even try re-installing dvdnav with
```
sudo aptitude reinstall libdvdnav4
```

---

### Post by Adrienk on 2010-05-01
So Xine Playes the dvd with no video all the sound is their....

and reinstalling the "library....pakage....w/e" gave me the same error and basically did nothing

---

### Post by 2hot6ft2 on 2010-05-01
Found something for the floppy0 here:
[http://ubuntuforums.org/showthread.php?t=1467649](http://ubuntuforums.org/showthread.php?t=1467649)

Might try the instructions here: (but I think you already did all that).
[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

---

### Post by Adrienk on 2010-05-01
```
adam@adam-laptop:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=b58198ba-5569-4215-8014-e203124a26fb /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=764b09a8-4eec-46df-9d47-8b94116060e1 none            swap    sw              0       0
/dev/scd0       /media/floppy0  auto    rw,user,noauto,exec,utf8 0       
```

I cannot tell if I can comment out the /dev/scd0 /media/floppy0 auto line or not

---

### Post by 2hot6ft2 on 2010-05-01
> **Adrienk said:**
> ```
adam@adam-laptop:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=b58198ba-5569-4215-8014-e203124a26fb /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=764b09a8-4eec-46df-9d47-8b94116060e1 none            swap    sw              0       0
**# **/dev/scd0       /media/floppy0  auto    rw,user,noauto,exec,utf8 0       
```

I cannot tell if I can comment out the /dev/scd0 /media/floppy0 auto line or not
That's where they're saying to comment it. You can give it a try and if it doesn't fix it then undo it. Might want to check the BIOS too like was said in the thread.

---

### Post by Adrienk on 2010-05-01
installing those pakages didnt realy do anything.... >_< i still got the same error.
rebooting now.

- i dont have a floppy controller on here because its a net book. so i cant disable floppy from the bios

OMG were making progress, so I commented out that line and when I rebooted I got vlc to play the video or reconize the disck as Charmed season 6.
BUT the time line is at the end and the video dosent play but vlc is reconizing the disk.

---

### Post by 2hot6ft2 on 2010-05-01
> **Adrienk said:**
> installing those pakages didnt realy do anything.... >_< i still got the same error.
rebooting now.

- i dont have a floppy controller on here because its a net book. so i cant disable floppy from the bios
My laptop doesn't have a floppy drive either but it has floppy listed in the BIOS still.

Good thing we made some progress because I'm fresh out of ideas at this point.

Well one more idea. There was one person that found out the contrast was set all the way down in VLC and that's why he didn't have any video.

---

### Post by rahmi.guldahl on 2010-09-22
In fact, you may install *ubuntu*-*restricted*-*extras, but I don't recommend it. For instance I don't want all packages that are included in this meta-package, instead I'd rather go to [http://packages.ubuntu.com/jaunty/ubuntu-restricted-extras](http://packages.ubuntu.com/jaunty/ubuntu-restricted-extras) and see what is included in this package, then I do apt-get install *[libavcodec-unstripped-52]("http://packages.ubuntu.com/jaunty/libavcodec-unstripped-52") [ttf-mscorefonts-installer]("http://packages.ubuntu.com/jaunty/ttf-mscorefonts-installer") [flashplugin-nonfree]("http://packages.ubuntu.com/jaunty/flashplugin-nonfree") and to the matter, in order to make your machine successfully play dvd's do the following in a terminal: sudo /usr/share/doc/libdvdread4/install-css.sh this should cover everything at least on 10.04.1.

you don't have to install flashplugin-nonfree, but in my case I did since I enjoy youtube.

---

