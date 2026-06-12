---
title: "Play music from audio CD .iso file"
date: 2009-09-25
forum: General Help
---

### Post by Gyrotwister on 2009-09-25
I'm looking for an application which can play directly from a .iso file taken from an audio CD.  
VLC can do this with Video DVD isos. 
Is there anything with similar capabilities for music CDs.

---

### Post by clonne4crw on 2009-09-25
Well, there is a way to mount the .iso as a filesystem:

```

# md /mnt/iso

# mount -o loop -t iso9660 <filename>.iso /mnt/iso

```

I'm pretty sure that's what VLC does in the background to play DVD images. 

Have you tried using VLC to do this?

---

### Post by gillespiea on 2009-09-25
I have to say that CD iso's are normally larger than if you were to make mp3's of the tracks...and much more of a pain to play (as you have found out). Ubuntu comes with software to make mp3's or .ogg files of the CD tracks. Applications>Sound and Video> Audio CD Extractor.

I understand that you might have other reasons for using iso's but thought i'd let you know this just in the smallest chance you never already knew.
Sorry if it's a pointless post i'm making lol

---

### Post by wojox on 2009-09-25
VLC should be able to play an audio .iso file.

---

### Post by Gyrotwister on 2009-09-26
Thanks. Yes I do know about compression both lossy and lossless.  
My reason for pursuing this is it seems to me that hard drives are so cheap now that there is no reason to compress anymore.  The .iso is a convenient way to backup a CD or DVD.  If only the CD .isos were playable then I could play all my videos and audio files off hard drive without having to handle the physical media.  A .iso contains all the original data so an identical copy of the original could be made if the original ever failed.  Another advantage of listening to CD rather than the ripped equivalent is that some artists (Frank Zapper for example) went to the trouble of writing musical interludes to link up tracks on an album.  When mp3s are played there always seems to be a gap inserted between songs which spoils the ambiance.  

Unfortunately I can't get VLC to play an audio CD iso.  
AcetoneISO won't do it either.  
The command line seems like a  painful way to access my music.  

Any other ideas or suggestions?

---

### Post by plutonium45 on 2009-09-26
I also think best way is to mount and then play

---

### Post by TheCelloFellow on 2009-09-26
For the record there are ways to record and playback gapless MP3 and Ogg Vorbis files so that when playing back the interlude tracks come through seemlessly.

For instance the cd ripper abcde when used with the -g flag will encode gappless MP3 files.

Few MP3 player devices support gappless playback, though the Rockbox firmware does and that works on many devices.

---

### Post by TheCelloFellow on 2009-09-26
For the record there are ways to record and playback gapless MP3 and Ogg Vorbis files so that when playing back the interlude tracks come through seemlessly.

For instance the cd ripper abcde when used with the -g flag will encode gappless MP3 files.

Few MP3 player devices support gappless playback, though the Rockbox firmware does and that works on many devices.

---

### Post by bobince on 2009-09-26
What is an audio .iso? CD-DA does not contain an ISO-9660 filesystem and isn't burned in the same mode as CD-ROM. I'm unaware of any standard way to put a CD-DA rip into .iso format; normally .bin/.cue is used instead.

But that's a very wasteful format (it even includes the CD-ROM error correction data). You can completely reproduce a ripped CD-DA with just FLAC for the audio tracks and a proper .cue file (which contains inter-track gaps and other information). This will be much smaller and easier to play. Gapless is a feature available on many players and not something you should need to use odd formats to get.

(DVD-Video, on the other hand, is built on top of the ISO-9660 and DVD-ROM standards, so there's no problem putting it in a .iso.)

---

### Post by clonne4crw on 2009-09-26
You are so much better off mounting the iso and just ripping the music. This seems to be more trouble than its worth.

---

### Post by Gyrotwister on 2009-09-29
Bobince asked.."What is an audio .iso?"

That is a good question.  I've got one sitting on my desktop at the moment and I've been experimenting with it for a couple of weeks.  
But now when I try to create another “.iso” of a CD using Brasero I discover I can only create .bin files.  Much to my embarrassment I can now remember where the .iso came from.  I renamed a .bin file to .iso to see if VLC would play it with that file extension.  
VLC didn't play it and I ceased experimenting.  By the time I revisited this problem a few days later I forgot how I created this file and came to assume Brasero had created it.  

A .iso of a CD is merely a figment of my imagination.  

My apologies to all who read this thread and tried to help me.  I've wasted too much of your time.  

So it looks like my best option is to use a lossless codec and be done with it.  

Thanks.

---

### Post by clonne4crw on 2009-09-29
An ISO is a a file containg an image of a volume, and the filesystem within it. 

[http://en.wikipedia.org/wiki/Disk_image](http://en.wikipedia.org/wiki/Disk_image)
for the proper definition.

---

