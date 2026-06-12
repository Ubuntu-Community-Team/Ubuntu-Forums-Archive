---
title: "Problems playing audio CDs in 10.04 LTS Lucid"
date: 2012-03-30
forum: General Help
---

### Post by Scooby-2 on 2012-03-30
As a newbie to Linux I originally wanted to rip my CD collection to MP3, for which I tried ripperX. While IT thought it was working (CD spins, ripping and encoding progress bars activate and it fairly accurately counts down from 20 minutes to complete a CD) it didn't actually produce any MP3 files. I also tried the "RIP to WAV" radio button but this met with the same degree of failure. Even the CDDB lookup fails with "Error code 20. Could not connect to CDDB server" even though I was connected to the Internet at the time. No errors are reported to the dmesg file so I wrote ripperX off and uninstalled it. 

I then installed and tried to use Asunder CD ripper. At least the CDDB lookup works on this program! However, this program produces WAV files when MP3 is selected!!!

So I figured I have a more basic problem here - maybe it'd be best to just try to play an audio CD first.

So, I tried to use Movie Player just to play an audio CD. When I told Movie Player to select the CD it requested to search for a missing plugin: Audio CD Source. It searched, then it said "No packages with the requested plugins found. The requested plugins are: Audio CD Source." (I make sure I'm connected to the Internet during this time.) Movie Player does play MP3s which I ripped in Windows, though.

Next I tried Exaile. It simply does nothing when the play key is pressed although it does list the CD's tracks and their duration.

Finally, I used VLC Player which does play individual tracks but only after I press <ctrl-d> to get to the CD menu and then change the "Starting Position" option from 0 to whichever track I want to start playing. This is only marginally better because it only plays the selected start track - the "Next media in playlist" button restarts the same track. To play the next track I have to go back into the CD menu again and select the one I want next. As it doesn't have a "Next track" button, only a "Next media in playlist" button I can't understand why anyone would bother with it. I certainly don't want to have to manually create playlists for every CD I might want to play!

BTW when I type dmesg | tail 50 I get 50 lines of the following:
[ 5632.272833] sr 0:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 5632.272845] sr 0:0:0:0: [sr0] Sense Key : Illegal Request [current] 
[ 5632.272854] ILI
[ 5632.272858] sr 0:0:0:0: [sr0] Add. Sense: Illegal mode for this track
[ 5632.272872] sr 0:0:0:0: [sr0] CDB: Read(10): 28 00 00 00 00 00 00 00 02 00
[ 5632.272891] end_request: I/O error, dev sr0, sector 0
[ 5632.275503] sr 0:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 5632.275513] sr 0:0:0:0: [sr0] Sense Key : Illegal Request [current] 
[ 5632.275522] ILI
[ 5632.275526] sr 0:0:0:0: [sr0] Add. Sense: Illegal mode for this track
[ 5632.275539] sr 0:0:0:0: [sr0] CDB: Read(10): 28 00 00 00 00 00 00 00 02 00
[ 5632.275558] end_request: I/O error, dev sr0, sector 0

The PC triple boots into Ubuntu, XP or Vista, where the exact same hardware plays/rips audio CDs under Windows with no problems. The problem exhibits in Linux with all my audio CDs, even my really old ones which are not mixed mode, and even home-burnt CDs with just WAV files on them.

I'm running Ubuntu 10.04.4 LTS 32-bit as shown here:
$lsb_release -a
LSB Version:    core-2.0-ia32:core-2.0-noarch:core-3.0-ia32:core-3.0-noarch:core-3.1-ia32:core-3.1-noarch:core-3.2-ia32:core-3.2-noarch:core-4.0-ia32:core-4.0-noarch
Distributor ID:    Ubuntu
Description:    Ubuntu 10.04.4 LTS
Release:    10.04
Codename:    lucid
$
Also, I've installed LAME 32bits version 3.98.2.

I figured that the Ubuntu LTS version would have most of the irritating bugs ironed out but disappointingly this appears not to be the case. My hardware is an old HP NX-6325 laptop with 1GB RAM and an AMD Sempron Mobile CPU. I'm trying hard to learn Linux and don't want to have to keep going into Windows just to run Media Player to play CDs or CDex to rip them to MP3 (this program is excellent. Pity it's not available for Linux!)

So I have two problems - I can't play audio CDs easily and I can't rip them to MP3 at all (under Linux). I guess I'm missing some software/plugin(s) which VLC player doesn't need, but VLC lacking the ability to just play an entire audio CD when inserted it's too awkward to use as a player. I assume as well that whatever it is that's missing is also preventing the ripping from taking place, so if I can get CDs to play I think it's likely that the ripping will also burst into life.

Why is this so difficult? Any help would be appreciated.

P.S. I found a similar(ish) problem regarding playing audio CDs here:
[http://ubuntuforums.org/showthread.php?t=1751589](http://ubuntuforums.org/showthread.php?t=1751589)
This had different symptoms but showed similar errors in dmesg. The solution was to reinstall Brasero but when I did this it made no difference to my problem.

---

### Post by immerohnegott on 2012-03-30
This should pretty much just work out of the box (aside from needing to install the mp3 encoder, of course).

I found an old post from '08 that recommends installing libcdio-utils, maybe that will help.

---

### Post by plucky on 2012-03-30
Have you installed **Xubuntu-restricted-extras**?

I use sound-juicer to rip CD's to MP3 in 10.04

---

### Post by Scooby-2 on 2012-03-30
> **immerohnegott said:**
> This should pretty much just work out of the box (aside from needing to install the mp3 encoder, of course).

I found an old post from '08 that recommends installing libcdio-utils, maybe that will help.

Hi immerohnegott

Thanks for the suggestion. I installed libcdio-utils, which is a collection of command-line utilities. The text-based CD player appears to work - i.e. it shows the tracks on the screen and starts playing from track 1 but there is no sound! I've checked that all mixer controls are selected and that none are muted. The arrow keys to RW/FFW and skip to next/previous tracks work OK. But with no sound! (I can hear the CD drive seeking.)

I think what I'm missing is a plugin or a library of some sort but thanks for the response.

---

### Post by Scooby-2 on 2012-03-30
> **plucky said:**
> Have you installed **ubuntu-restricted-extras**?

I use sound-juicer to rip CD's to MP3 in 10.04

Hi plucky

I tried installing **ubuntu-restricted-extras **- but  I still can't play audio CDs in Movie Player. I think this is what I need to get working first - if I can't play them there's little hope of ripping them (seems logical to me).

Thanks for the suggestion.

---

### Post by plucky on 2012-03-31
> **Scooby-2 said:**
> Hi plucky

I tried installing **ubuntu-restricted-extras **- but  I still can't play audio CDs in Movie Player. I think this is what I need to get working first - if I can't play them there's little hope of ripping them (seems logical to me).

Thanks for the suggestion.

What is Xubuntu use for a Music Player.

Audio CD's use .WAV files and I have to select each file before it will play in Movie Player.Try using the Xubuntu music player in the Sound menu.

Good Luck

---

### Post by Scooby-2 on 2012-03-31
> plucky said:
Try using the Xubuntu music player in the Sound menu.
Thanks for the response, plucky. I don't have the xubuntu music player in my menu but I have found xine works OK with audio CDs and WAV files. My ripping problems remain unresolved so I'm going to wait for the release of 12.04 LTS on April 26th. I'm sure this problem isn't going to be fixed with a new release due so soon, I just hope that the major issues have been resolved in the new release...

](*,)

---

