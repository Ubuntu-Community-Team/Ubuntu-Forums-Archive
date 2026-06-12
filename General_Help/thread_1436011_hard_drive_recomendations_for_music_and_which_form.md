---
title: "hard drive recomendations for music and which format"
date: 2010-03-22
forum: General Help
---

### Post by polar11 on 2010-03-22
I need a new external hard drive for my music laptop - the hard drive will only be used under linux, are there any brands that are seen as more reliable than others (either 500gb or 1tb)?? 
I will be storting about 500 cd's worth of FLAC or ogg vorbis music (is one better than the other?).

I assume that usb will be fine to stream from? or should i pay extra and use firewire?

finally - which format would be best to format in?? 

ps: if at a later date i need to shift my data to a mac with a new external HDD- is this possible?

---

### Post by gordintoronto on 2010-03-22
I have no suggestion about brand and model of external hard drive. There is a web site called "Ask Leo" which does have a suggestion.

I prefer flac for audio because it is not "lossy". It does take more space. And it might not be supported on other operating systems. Also, it might not be supported 20 years from now.

USB is more than fast enough for audio.

I would format an external drive as ntfs to keep the greatest flexibility.

---

### Post by srs5694 on 2010-03-22
For Linux-only use, NTFS has some significant drawbacks. Specifically, if you ever shut down uncleanly, you won't be able to use the drive again until it's been checked by a Windows system; and it doesn't support Linux-style ownership and permissions. Since polar11 specified Linux-only use, IMHO s/he should use a Linux-native filesystem. For music files, just about anything will work. Ext3fs is supported by almost every Linux system and is more than adequate, but ReiserFS is comparable in most features. Ext4fs, JFS, and XFS are better for big files, but these benefits aren't important for music files; only if videos were being stored would this become much of an issue. Ext4fs is still new enough that I personally would avoid it, but it's starting to become quite popular since it's the default for several recent distributions, including the most recent versions of Ubuntu.

---

### Post by cascade9 on 2010-03-23
If you've got the HDD space, go for flac- lossless -> lossy (like flac-> ogg vorbis) conversions are easy and are the same quality as ripping from the original source to lossy

---

### Post by c0nfusedami on 2010-03-23
being an audio guy i would have to say its well worth the money to spring for the fire wire drive especially if your doing any kind of recording. fire wire is much better at handling the tranfer of larger files. i have a western digital and seagate external and they both work fine. im not sure about hard drive format but i would do flac for the audio files or if you realy wnt to get on a mac apple has a lossless encoder i think its called alc or something like that.

---

### Post by cascade9 on 2010-03-23
I wouldnt bother with firewire myself, its good but outclassed by eSATA IMO. 

eSATA is becomign far more common, a lot of low-end boards that dotn have firewire are getting eSATA these days.

---

### Post by audiomick on 2010-03-23
Don't buy Samsung. I have four, bought all at once because they were a bit cheaper. Turns out it was not such a great saving. They work, but  are stubbornly recalcitrant.

On the desktop, which has 2 of them in it, I have periodic "drive not found" messages at startup. The problem is definitely the drive just not being ready when it is looked for. There is  nothing as such worng with them, nothing broken, no "fast start" options, nothing to fix. The drives are just a pain.

The other two are in an NAS. That seems to all be working now, but only after a board update in the NAS. Sure, it was also a "construction error" in the NAS, hence the board update, but it was an issue that only came up with Samsung drives.

I wont be swapping them out, the niggles aren't that bad, but next time I will buy Seagate or WD or something like that.

---

### Post by polar11 on 2010-03-23
Thanks all for the replies most helpful...

i have decided to get a seagate HDD- either 500gb or 1tb
rip with grip - everything into flac
tag with easy tag
play in rhythmbox

then i understand that rhythmbox can encode the flac into ogg vorbis files for my portable music player

 regarding file formats - it will only be used on linux so i will look into the following Ext3fs, Ext4fs, JFS, and XFS

cheers all

---

