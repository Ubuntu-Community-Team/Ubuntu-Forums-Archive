---
title: "Any Tips??? Rip CD collection (&amp; share w/computer in practice room)"
date: 2011-01-29
forum: General Help
---

### Post by tptmrk on 2011-01-29
I can never find the CD I want! But my mp3s are at my fingertips. With the cost of big hard drives being low I'm going to rip 100s of CDs to lossless mp3s (assume FLAC).

***ANY TIPS? ***This is going to take a while and if you can make this more efficient/effective I'd appreciate it!

*1) Is there any program that would be easiest for the ripping? *I want to be sure to get good tags and to double check them before ripping.

2) I figure I'll just *put them all in one big folder* on the new hard drive and let the player organize it all. I've scratched the surface of Amarok and RhythmBox and it seems I should be able to tell any player all my files are in that folder and then I'll be able to browse them by artist, album, etc. in the player.

3) I have to *share the hard drive between computers*. I somehow did this last summer before the hard drive on my computer in the practice room died. I found some easy workaround thing online, but I'd like to do it the "right" way if there is one. I'd like to even be able to rip mp3s in the practice room to the mp3 hard drive in the office.

:guitar:

---

### Post by cjhabs on 2011-01-29
I use "abcde" with a configuration file. It looks up the tags and gives you a chance to edit them.
It also saves the files in a folder structure that you define in the conf file. If you have a lot of music, storing it all in 1 flat folder will have performance implications.

If you are sharing music between Ubuntu machines, then sharing the drives using nfs works well. Sharing with windows can also be done using samba.

I am not sure if ripping across the network will work well - if the network can't keep up with the ripping process you may lose some data.

---

### Post by Nixarter on 2011-01-29
There just isn't any way to speed up the process, unfortunately, as it is primarily mechanical.  Most of your time will be in waiting.  With that any cd's to rip, you might end up killing a drive unless you read at a reduced rate.  Instead of max at 48x or whatever, do it at 16x.  It will take longer, but it will only cause a small fraction of the wear-and-tear vs ripping at max (maybe only 10% as much, if not less).

I would rip the CD's locally, then copy to the desired drive (then, if it worked, delete originals to save space).  That way there are no delayed write/latency errors (because the network is slower than you're ripping speed).

as for performance issues... many players have an option to index the folder, which would eliminate that concern.

---

### Post by HermanAB on 2011-01-30
BTW, ripping lossless is not really worth the effort.  The sad fact is that as you get older, your hearing deteriorates, so eventually even 64bit MP3 are good enough.  So you can just as well save some disk space and make it more convenient to copy files to your portable players.

---

### Post by tptmrk on 2011-01-30
Looked at nfs and that'll do it. Will mess with that.

Will rip locally. What program will automatically move files from the practice room computer to the mp3 hard drive on a schedule?

Didn't think about burning out the drive, thnx. I know it'll take a while. I figured I'll burn them while doing other tasks.

---

### Post by dirghrabadia on 2011-01-30
> **HermanAB said:**
> BTW, ripping lossless is not really worth the effort.  The sad fact is that as you get older, your hearing deteriorates, so eventually even 64bit MP3 are good enough.  So you can just as well save some disk space and make it more convenient to copy files to your portable players.

:lolflag:

---

### Post by cascade9 on 2011-01-30
IMO, do it once, get it right, forget about anything after that (aside from abackup of course, who wants to lose all that work ripping to a HDD failure, or power spike, etc. 
 
 I only use one of 2 tools for .flac rips. EAC, on windows, and rubyripper on linux. They both can do 2 pass rips, when the track in ripped towce and compared. If there is a difference in the rips, somethign ahs gone wrong, if they are the same then it should be a perfect rip.  
 
 The only problem is that rubyripper is that in most cases (including ubuntu up to 10.10) is that it uses ruby 1.8. It works, but there is a huge pause between tracks (not an audio pause). Its fixable by installing ruby 1.9. 

I really wouldnt dump all the .flacs in one big folder. Its almost as easy to create at least artist and/or album folders. It makes naviation easier, and you dont have to be so careful with naming. If everything is  in one big folder, a naming scheme like Artist- Album- Tracknumber- Track Name is the best way to do it, or else things get messy. Navigation is easier with artist and/or album folders. But if you really want everything in one big folder, you can do it that way, its your filesystem. ;) 
 
 > **HermanAB said:**
> BTW, ripping lossless is not really worth the effort. The sad fact is that as you get older, your hearing deteriorates, so eventually even 64bit MP3 are good enough. So you can just as well save some disk space and make it more convenient to copy files to your portable players.
 
64k MP3s 'god enough'? *blinks* Too much loud music for you. Or you are using those crappy 'PC speakers' with a response range thats a joke. Or both. I'm yet to meet anyone who cant pick the difference between MP3s of 128K or less and better quality rips, given decent audio equipment. Even my mum, who admits to being partially deaf. 
 
 As for disk space, who gives a proverbial when you can get 2TB dries are under $100 US.... 
 
 Lossless isnt just about audio quality, its also a defacto backup of the CDs if done right.

---

### Post by tptmrk on 2011-01-30
Rubyripper is what I've used so there's no learning curve there. Thanks for telling about running two passes!!!

I'll go with a /mp3s/Artist/Album file structure. Looks like it's a better idea than all in one folder.

I'm running it all through a Behringer mixer, PV900 power amp, and Peavey SP2s (the newer, lighter, great sounding ones). It's not top of the line audiophile stuff, but it sounds great (and functions well as a practice PA). I can tell a *huge* difference between 128k and CDs. Costco advertised a 2TB external hard drive for $100, which is what made me think about this. I'll also be able to use the drive to backup everything else and have tons of space left. MP3 players already have 40gb flash memory and they're just going to get bigger. 

If I'm going to the trouble to rip everything I figure flac will keep me from ever doing it again. I mean, down the road when we switch to some other file format there will be a utility to convert all those files without loss, right?

---

### Post by cascade9 on 2011-01-31
> **tptmrk said:**
> Rubyripper is what I've used so there's no learning curve there. Thanks for telling about running two passes!!!

No problem. ;) 

> **tptmrk said:**
> If I'm going to the trouble to rip everything I figure flac will keep me from ever doing it again. I mean, down the road when we switch to some other file format there will be a utility to convert all those files without loss, right?

You should be able to unless  RIAA or somebody else manages to push everything to a codec that is totally closed and has no tools for conversion. There are other ways that your .flac collection could be stuck with no current support or ability to transcode to a current codec, but most of them involve governments becoming even more facist than they are now.......and are fairly unlikely.

---

