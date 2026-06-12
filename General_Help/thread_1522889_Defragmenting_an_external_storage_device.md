---
title: "Defragmenting an external storage device"
date: 2010-07-02
forum: General Help
---

### Post by Chamillion02 on 2010-07-02
Are there any tools in Ubuntu that could defragment my MP4 player (Sansa E280R)?

One of the songs on my MP4 player isn't showing its Album Name or Artist Name. I know I have the artist and album name tagged onto the MP3 because I set them both & double checked using mp3tag.

---

### Post by VeeDubb on 2010-07-02
You're barking up the wrong tree.

I have no idea what is causing your problem, but I can guarantee you it has nothing to do with fragmentation.

1. Fragmentation couldn't cause the problem you've described.

2. Fragmentation is irrelevant on flash storage like you would hav in an MP3 player.  Not only is fragmentation not relevant to flash media, but defragmenting flash media reduces it's life span because of the huge number of writes involved with defragmenting.

---

### Post by Chamillion02 on 2010-07-03
After I defragmented my Sansa in Virtualbox Windows XP it fixed the album name and artist name. You obviously don't know what defragmentation is for, poster #2. And Defragmenting can't hurt anything. I know that for sure lol, but thanks for the funny comment, poster #2  :)

---

### Post by MooPi on 2010-07-03
Any corrections after a defrag can be only be coincidental and not attributed to the process. Veedubb was correct with the initial response. I would not recommend trying to defrag your flash drive.You don't have to take my word on this but just do a simple search on the web to confirm. I would suggest you delete all data or format and replace all the songs from backup.
[http://ask-leo.com/should_i_defragment_my_usb_flash_drive.html]("http://ask-leo.com/should_i_defragment_my_usb_flash_drive.html")
[http://www.worldstart.com/tips/tips.php/4663]("http://www.worldstart.com/tips/tips.php/4663")

---

### Post by howefield on 2010-07-03
> **Chamillion02 said:**
> After I defragmented my Sansa in Virtualbox Windows XP it fixed the album name and artist name. You obviously don't know what defragmentation is for, poster #2. And Defragmenting can't hurt anything. I know that for sure lol, but thanks for the funny comment, poster #2  :)

Why don't you explain how defragmenting sorted your album out ?

I'd look forward to your supposition ;-)

---

### Post by nacho32 on 2010-07-03
I knew defrag had another use to it
</sarcasm>

---

### Post by SoFl W on 2010-07-03
Silly silly poster #2.

---

### Post by sgosnell on 2010-07-03
How, exactly, did the songs on the player get fragmented in the first place?  Splain me that, Lucy.

---

### Post by bhuvi on 2010-07-03
> **Chamillion02 said:**
> After I defragmented my Sansa in Virtualbox Windows XP it fixed the album name and artist name. You obviously don't know what defragmentation is for, poster #2. And Defragmenting can't hurt anything. I know that for sure lol, but thanks for the funny comment, poster #2  :)

you are very WRONG ,defragmentation is only for mechanical storage devices to keep the various parts of same files closer to each other so it can be accessed quickly, but for electronic storage the same parts of files can be stored anywhere since the time required to access it is very small and practically there is no gain in defragmenting. Also there is a limit to no of times the data can be written in a particular location and a technology called wear levelling is used to prevent same location from being over used and failing prematurely.

And defragging only moves the data around and it does not introduce any changes or correct errors, only disk checking can fix data errors and corruptions.

---

### Post by VeeDubb on 2010-07-03
lol, sorry OP.  Like they're all telling you, you fail.

defrag has nothing to do with this, and if you think it does, you clearly have no idea what disk fragmentation is or how it works.  The fact that your album art is not working is coincidental.

---

### Post by demosthenese on 2010-07-03
> **Chamillion02 said:**
> I know I have the artist and album name tagged onto the MP3 because I set them both & double checked using mp3tag.

As well as checking the artist/name in mp3tag exist, also check the id3 version. You need the 'Tag' column to be displayed. You probably want to have the settings ticked for write IDv3.1 and IDv3.2.

I have seen some mp3 players unable to read the tag information if it is not the version they expect.

---

### Post by ov3rcl0ck on 2010-07-11
> **Chamillion02 said:**
> Are there any tools in Ubuntu that could defragment my MP4 player (Sansa E280R)?

One of the songs on my MP4 player isn't showing its Album Name or Artist Name. I know I have the artist and album name tagged onto the MP3 because I set them both & double checked using mp3tag.

Fragmentation isn't an issue, especially since its flash based memory, so it won't fragment, and if it does, not a big deal.

The music info was either Lost during a format conversion, or not stored in the music file, but rather a database in your music player.

---

### Post by ov3rcl0ck on 2010-07-11
> **Chamillion02 said:**
> After I defragmented my Sansa in Virtualbox Windows XP it fixed the album name and artist name. You obviously don't know what defragmentation is for, poster #2. And Defragmenting can't hurt anything. I know that for sure lol, but thanks for the funny comment, poster #2  :)
&
[jailed quote removed]

Fragmentation is when the HD writes data scattered around in different locations on the disk, making it slow to read because the harddrive has to spin every where to get the data. Defragmentation takes these chunks and organizes them, so files aren't split up in different blocks on the hard drive, so the Hard drive can read the file off the disk in one swift spin.

Seems the only one who doesn't know what there talking about is you. If you want to argue, read the links below first, and see whos right and whos wrong. And don't call anyone a <snip>, that will get you banned.

[http://en.wikipedia.org/wiki/Fragmentation_(computer](http://en.wikipedia.org/wiki/Fragmentation_(computer))

[http://en.wikipedia.org/wiki/Defragmentation](http://en.wikipedia.org/wiki/Defragmentation)

---

### Post by Schrute Farms on 2010-07-11
Hey original poster,
I have the same Sansa player you have & I know what's wrong:
Read the quote below:
> **demosthenese said:**
> As well as checking the artist/name in mp3tag exist, also check the id3 version. You need the 'Tag' column to be displayed. You probably want to have the settings ticked for write IDv3.1 and IDv3.2.

I have seen some mp3 players unable to read the tag information if it is not the version they expect.

He is 100% right about the id3 version of your tags.  If it isn't correct it will not show up correctly.  I used to fight with this with my player until I figured it out.  It has to be IDv3.2 or better or it will not work.

And also, everyone else is 100% right about defragmenting; it will not help your problem.
So why don't you listen when many different people tell you something & quit being a douche.  We are all not making up a bunch of stuff just to pi$$ you off, we are really trying to help.

---

### Post by Iowan on 2010-07-11
OK, this one seems to be going nowhere...
Closed.

---

