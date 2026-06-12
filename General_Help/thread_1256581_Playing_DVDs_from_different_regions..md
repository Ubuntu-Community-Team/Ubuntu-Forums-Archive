---
title: "Playing DVDs from different regions."
date: 2009-09-02
forum: General Help
---

### Post by RabbitWho on 2009-09-02
I've an Irish Dell Inspiron 1545 here, it's playing DVDs from this region but i have a few from America I'd like to play. . . I've read the help page on this already and tried a few things.

i've already downloaded libdvdread4
 mpeg2-video isn't in the synaptic package.. is it somewhere else or is the help section out of date? 

So movie player says "could not read DVD from source"
VLC player gets the first 2 screens of the dvd and then says cannot read
and 
Mplayer says "seek failed" 

Any suggestions? 

On a slightly related note.. the DVD player is uber-sensitive and won't play anything with the slightest scratch, I take it this is a hardware problem and not something I can fix?

---

### Post by jmszr on 2009-09-02
RabbitWho,

If you haven't already, install:[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu) and then: ```
sudo apt-get install libdvdcss2
```.
The Medibuntu documentation also contains instructions for just the libdvdcss2 installation, if you'd prefer.

It's odd that VLC won't work for you as it doesn't usually care about regions.

---

### Post by fluffman86 on 2009-09-02
Both are probably hardware.  AFAIK, DVD-ROM drives are hard coded to only play DVDs from the region they are designed for, unless they are Region 0 (no/all regions).  You can change the region on the drive a limited number of times, but that's limited by the drive's firmware, so it's hard coded and can't be changed.

While there may be hacks to get around all of this, the easiest thing would be to find a region 0 dvd drive.

edit: this site might be of use:
[http://forum.rpc1.org/portal.php](http://forum.rpc1.org/portal.php)

---

### Post by mc4man on 2009-09-02
Go in a terminal 
```
sudo lshw -C disk
```

If you have a matshita dvd drive (which dell uses among others), then you cannot play dvds when there is a region mismatch. 

If it's not a matshita, then you should be able to play disks from other regions, open-source players don't enforce region coding, nor do most dvd drives, the most notable exception being matshita laptop drives.

If it's not a matshita then ck. that you have a region set (2 will be fine), if it is then just forget about it. (or if the laptop is still under warranty hope the drive dies, it's probably 40 -60 you'd get a different manu. as a replacement

---

### Post by RabbitWho on 2009-09-02
rabbit@penguincounter:~$ sudo apt-get install libdvdcss2
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package libdvdcss2 is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package libdvdcss2 has no installation candidate
rabbit@penguincounter:~$ 


Hmm.. I've nothing open that could be using it, not that I can see anyway, I'll restart and try again. 



> **mc4man said:**
> Go in a terminal 
```
sudo lshw -C disk
```If you have a matshita dvd drive (which dell uses among others), then you cannot play dvds when there is a region mismatch. 

If it's not a matshita, then you should be able to play disks from other regions, open-source players don't enforce region coding, nor do most dvd drives, the most notable exception being matshita laptop drives.

If it's not a matshita then ck. that you have a region set (2 will be fine), if it is then just forget about it. (or if the laptop is still under warranty hope the drive dies, it's probably 40 -60 you'd get a different manu. as a replacement

It doesn't say anything about matshita there (why would anyone name themselves something with the word **** in it? )

  *-disk                  
       description: ATA Disk
       product: WDC WD3200BEVT-7
       vendor: Western Digital
       physical id: 0
       bus info: scsi@0:0.0.0
       logical name: /dev/sda
       version: 11.0
       serial: WD-WX70A7961296
       size: 298GiB (320GB)
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=5 signature=55ca70e7
  *-cdrom
       description: DVD-RAM writer
       product: DVD+-RW AD-7560S
       vendor: Optiarc
       physical id: 1
       bus info: scsi@1:0.0.0
       logical name: /dev/cdrom
       logical name: /dev/cdrw
       logical name: /dev/dvd
       logical name: /dev/dvdrw
       logical name: /dev/scd0
       logical name: /dev/sr0
       logical name: /media/cdrom0
       version: SD05
       capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
       configuration: ansiversion=5 mount.fstype=udf mount.options=ro,nosuid,nodev,utf8 state=mounted status=ready
     *-medium
          physical id: 0
          logical name: /dev/cdrom
          logical name: /media/cdrom0
          configuration: mount.fstype=udf mount.options=ro,nosuid,nodev,utf8 state=mounted
  *-disk
       description: SCSI Disk
       physical id: 0.0.0
       bus info: scsi@6:0.0.0
       logical name: /dev/sdb
  *-disk
       description: SCSI Disk
       product: Cruzer Micro
       vendor: SanDisk
       physical id: 0.0.0
       bus info: scsi@12:0.0.0
       logical name: /dev/sdc
       version: 8.01
       serial: u
       size: 3839MiB (4025MB)
       capabilities: removable
     *-medium
          physical id: 0
          logical name: /dev/sdc
          size: 3839MiB (4025MB)
          capabilities: partitioned partitioned:dos


So I should be able to play them? 
Anyone have any ideas how I can go about that since I've already tried a few players so something must be wrong.. hmm

---

### Post by mc4man on 2009-09-02
> why would anyone name themselves something with the word **** in it? They're made by panasonic and i quess they used an apt description of their drive and it's behavior.

The Optiarc is probably a sony,nec and should have no issues with other regions other than the drive's individual problem reading disks that you mentioned.

For starters maybe start vlc in a debug mode and see if any add. info shows up.
From terminal
```
vlc -vv
```
And then go about opening the disk  from media-> open disk (do it once normally and once with No DVD menus checked.

---

### Post by RabbitWho on 2009-09-02
> **mc4man said:**
> They're made by panasonic and i quess they used an apt description of their drive and it's behavior.

The Optiarc is probably a sony,nec and should have no issues with other regions other than the drive's individual problem reading disks that you mentioned.

For starters maybe start vlc in a debug mode and see if any add. info shows up.
From terminal
```
vlc -vv
```And then go about opening the disk from media-> open disk (do it once normally and once with No DVD menus checked.

 With no dvd: [00000369] main playlist debug: processing request item dvd:///dev/sr0 node null skip 0 [00000369] main playlist debug: resyncing on dvd:///dev/sr0 [00000369] main playlist debug: dvd:///dev/sr0 is at 0 [00000369] main playlist debug: creating new input thread [00000407] main input debug: Creating an input for 'dvd:///dev/sr0' [00000407] main input debug: waiting for thread initialization [00000407] main input debug: thread started [00000407] main input debug: thread 2938108816 (input) created at priority 10 (input/input.c:370) [00000407] main input debug: `dvd:///dev/sr0' gives access `dvd' demux `' path `/dev/sr0' [00000407] main input debug: creating demux: access='dvd' demux='' path='/dev/sr0' [00000408] main demux debug: looking for access_demux module: 2 candidates libdvdnav: Using dvdnav version 4.1.3 libdvdread: Encrypted DVD support unavailable. ************************************************ ** ** ** No css library available. See ** ** /usr/share/doc/libdvdread4/README.Debian ** ** for more information. ** ** ** ************************************************ libdvdread: Could not open input: No medium found libdvdread: Can't open /dev/sr0 for reading libdvdnav: vm: failed to open/read the DVD [00000408] dvdnav demux warning: cannot open dvdnav libdvdread: Encrypted DVD support unavailable. ************************************************ ** ** ** No css library available. See ** ** /usr/share/doc/libdvdread4/README.Debian ** ** for more information. ** ** ** ************************************************ libdvdread: Could not open input: No medium found libdvdread: Can't open /dev/sr0 for reading [00000408] dvdread demux error: DVDRead cannot open source: /dev/sr0 [00000408] main demux warning: no access_demux module matching "dvd" could be loaded [00000408] main demux debug: TIMER module_Need() : 15.994 ms - Total 15.994 ms / 1 intvls (Avg 15.994 ms) [00000407] main input debug: creating access 'dvd' path='/dev/sr0' [00000411] main access debug: looking for access module: 0 candidates [00000411] main access error: no access module matched "dvd" [00000411] main access debug: TIMER module_Need() : 0.294 ms - Total 0.294 ms / 1 intvls (Avg 0.294 ms) [00000407] main input error: open of `dvd:///dev/sr0' failed: could not create access: no access module matched "dvd" [00000369] main playlist debug: finished input [00000369] main playlist debug: dying input [00000407] main input debug: thread ended [00000369] main playlist debug: dead input [00000407] main input debug: thread 2938108816 joined (playlist/engine.c:244) [00000407] main input debug: TIMER input launching for 'dvd:///dev/sr0' : 74.628 ms - Total 74.628 ms / 1 intvls (Avg 74.628 ms) [00000369] main playlist debug: starting new item [00000369] main playlist debug: changing item without a request (current 0/1) [00000369] main playlist debug: nothing to play [00000404] qt4 interface debug: New item: dvd:///dev/sr0 [00000369] main playlist debug: adding item `dvd:///dev/sr0' ( dvd:///dev/sr0 ) [00000369] main playlist debug: rebuilding array of current - root Playlist [00000369] main playlist debug: rebuild done - 2 items, index 0 [00000369] main playlist debug: starting new item Somewhere around here is what came up after i inserted the dvd and tried again: [00000369] main playlist debug: processing request item dvd:///dev/sr0 node null skip 0 [00000369] main playlist debug: resyncing on dvd:///dev/sr0 [00000369] main playlist debug: dvd:///dev/sr0 is at 1 [00000369] main playlist debug: creating new input thread [00000412] main input debug: Creating an input for 'dvd:///dev/sr0' [00000412] main input debug: waiting for thread initialization [00000412] main input debug: thread started [00000412] main input debug: thread 2938108816 (input) created at priority 10 (input/input.c:370) [00000412] main input debug: `dvd:///dev/sr0' gives access `dvd' demux `' path `/dev/sr0' [00000412] main input debug: creating demux: access='dvd' demux='' path='/dev/sr0' [00000413] main demux debug: looking for access_demux module: 2 candidates libdvdnav: Using dvdnav version 4.1.3 libdvdread: Encrypted DVD support unavailable. ************************************************ ** ** ** No css library available. See ** ** /usr/share/doc/libdvdread4/README.Debian ** ** for more information. ** ** ** ************************************************ [00000404] qt4 interface debug: Updating the stream status: 3 libdvdnav: DVD Title: THE_OFFICE libdvdnav: DVD Serial Number: 36e2b18c libdvdnav: DVD Title (Alternative): SEASON_THREE_DISC_1_R0 libdvdnav: Unable to find map file '/home/rabbit/.dvdnav/THE_OFFICE.map' libdvdnav: DVD disk reports itself with Region mask 0x00fe0000. Regions: 1 [00000413] dvdnav demux debug: trying to go to dvd menu [00000414] main generic debug: thread 2929716112 (dvdnav event thread handler) created at priority 0 (dvdnav.c:352) [00000413] main demux debug: using access_demux module "dvdnav" [00000414] main generic debug: thread started [00000413] main demux debug: TIMER module_Need() : 2836.891 ms - Total 2836.891 ms / 1 intvls (Avg 2836.891 ms) [00000412] main input debug: `dvd:///dev/sr0' successfully opened [00000413] dvdnav demux debug: DVDNAV_HOP_CHANNEL [00000412] main input debug: control type=1 [00000413] dvdnav demux debug: DVDNAV_VTS_CHANGE [00000413] dvdnav demux debug: - vtsN=1 [00000413] dvdnav demux debug: - domain=8 [00000413] dvdnav demux debug: DVDNAV_CELL_CHANGE [00000413] dvdnav demux debug: - cellN=1 [00000413] dvdnav demux debug: - pgN=1 [00000413] dvdnav demux debug: - cell_length=3396000 [00000413] dvdnav demux debug: - pg_length=3396000 [00000413] dvdnav demux debug: - pgc_length=3396000 [00000413] dvdnav demux debug: - cell_start=0 [00000413] dvdnav demux debug: - pg_start=0 [00000413] dvdnav demux debug: DVDNAV_SPU_CLUT_CHANGE [00000413] dvdnav demux debug: DVDNAV_SPU_STREAM_CHANGE [00000413] dvdnav demux debug: - physical_wide=0 [00000413] dvdnav demux debug: - physical_letterbox=0 [00000413] dvdnav demux debug: - physical_pan_scan=1 [00000413] dvdnav demux debug: buttonUpdate not done b=1 t=0 [00000412] main input debug: selecting program id=0 [00000415] main decoder debug: looking for decoder module: 30 candidates [00000404] qt4 interface debug: New Event: type 1103 [00000404] qt4 interface debug: Updating the stream status: 3 [00000404] qt4 interface debug: New Event: type 1108 [00000415] main decoder debug: using decoder module "spudec" [00000415] main decoder debug: TIMER module_Need() : 31.532 ms - Total 31.532 ms / 1 intvls (Avg 31.532 ms) [00000415] main decoder debug: thread 2909375376 (decoder) created at priority 0 (input/decoder.c:217) [00000413] dvdnav demux debug: DVDNAV_AUDIO_STREAM_CHANGE [00000413] dvdnav demux debug: - physical=0 [00000415] main decoder debug: thread started [00000413] dvdnav demux warning: cannot get next block (Error reading NAV packet.) [00000413] dvdnav demux debug: jumping to first title [00000413] dvdnav demux debug: DVDNAV_HOP_CHANNEL [00000413] dvdnav demux debug: DVDNAV_VTS_CHANGE [00000413] dvdnav demux debug: - vtsN=1 [00000413] dvdnav demux debug: - domain=2 [00000415] main decoder debug: removing module "spudec" [00000415] main decoder debug: thread ended [00000415] main decoder debug: thread 2909375376 joined (input/decoder.c:248) [00000415] main decoder debug: killing decoder fourcc `spu ', 0 PES in FIFO [00000412] main input debug: Program doesn't contain anymore ES [00000413] dvdnav demux debug: DVDNAV_CELL_CHANGE [00000413] dvdnav demux debug: - cellN=1 [00000413] dvdnav demux debug: - pgN=1 [00000413] dvdnav demux debug: - cell_length=11550000 [00000413] dvdnav demux debug: - pg_length=11550000 [00000413] dvdnav demux debug: - pgc_length=119178000 [00000413] dvdnav demux debug: - cell_start=0 [00000413] dvdnav demux debug: - pg_start=0 [00000413] dvdnav demux debug: DVDNAV_SPU_CLUT_CHANGE [00000413] dvdnav demux debug: DVDNAV_SPU_STREAM_CHANGE [00000413] dvdnav demux debug: - physical_wide=128 [00000413] dvdnav demux debug: - physical_letterbox=128 [00000413] dvdnav demux debug: - physical_pan_scan=128 [00000413] dvdnav demux debug: buttonUpdate not done b=1 t=1 [00000413] dvdnav demux debug: DVDNAV_AUDIO_STREAM_CHANGE [00000413] dvdnav demux debug: - physical=0 [00000413] dvdnav demux debug: buttonUpdate not done b=1 t=1 [00000413] dvdnav demux warning: cannot get next block (Error reading from DVD.) [00000404] qt4 interface debug: New Event: type 1103 [00000404] qt4 interface debug: Updating the stream status: 9 [00000404] qt4 interface debug: New Event: type 1103 [00000369] main playlist debug: finished input [00000369] main playlist debug: dying input [00000369] main playlist debug: dying input [00000404] qt4 interface debug: Updating the stream status: 8 [00000414] main generic debug: thread ended [00000414] main generic debug: thread 2929716112 joined (dvdnav.c:368) [00000412] main input debug: Program doesn't contain anymore ES [00000369] main playlist debug: dying input [00000369] main playlist debug: dying input [00000413] main demux debug: removing module "dvdnav" [00000412] main input debug: thread ended [00000369] main playlist debug: dead input [00000412] main input debug: thread 2938108816 joined (playlist/engine.c:244) [00000412] main input debug: TIMER input launching for 'dvd:///dev/sr0' : 2842.257 ms - Total 2842.257 ms / 1 intvls (Avg 2842.257 ms) [00000369] main playlist debug: starting new item [00000369] main playlist debug: changing item without a request (current 1/2) [00000369] main playlist debug: nothing to play 

I can't make heads nor tails of any of this.

and the first time i submitted it decided to quash everything in together and ruin the lovely formatting so it's completely unreadable. lovely.

---

### Post by Seq on 2009-09-02
> **RabbitWho said:**
> rabbit@penguincounter:~$ sudo apt-get install libdvdcss2
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package libdvdcss2 is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package libdvdcss2 has no installation candidate
rabbit@penguincounter:~$ 

I'd say this is your problem. Did you add the medibuntu repository before attempting to install? libdvdcss2 is not provided by Ubuntu due to silly DMCA things in the US (perhaps similar reasons elsewhere).

Anyway, from my understanding normally vlc (or any other media player) justs asks the drive to decrypt the disk. The drive's firmware typically does a region check and if the region matches, the drive itself provides the unencrypted data for playback. Else it fails (which is what you're seeing).

Another option is to use a libdvdcss2. It is a library to break the "Content Scramble System" on dvds. Media players (like vlc) will hook into it when available to instead instruct the drive just to dump raw data back and then use this library to decode the video. This will work on any drive (except Matshita, apparently. Probably fails to return anything on region mismatch. I've got one in my Macbook, but only have discs for region 0/1, so I can not test.)

---

### Post by mc4man on 2009-09-02
Sorry, missed something in an earlier post, I thought you said you had libdvdcss2 installed, but the debug shows

> Encrypted DVD support unavailable. 
so either run this in a terminal

```
 sudo /usr/share/doc/libdvdread4/install-css.sh
```

or go directly here to download and install (most likely the i386 version (32 bit install

[http://packages.medibuntu.org/jaunty/libdvdcss2.html](http://packages.medibuntu.org/jaunty/libdvdcss2.html)

or follow instr. to add medibuntu as a source (wget command for release of ubuntu you're using, followed by the get key command, and then the command from post 2

[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

---

