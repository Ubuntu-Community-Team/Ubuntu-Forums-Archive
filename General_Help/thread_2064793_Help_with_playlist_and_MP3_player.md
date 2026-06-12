---
title: "Help with playlist and MP3 player"
date: 2012-09-30
forum: General Help
---

### Post by AgentZ86 on 2012-09-30
Hi

I have never EVER been able to properly use an mp3 player

I download books or extract them from CD's but when you put them on the mp3 player they don't play in order and yet the file names are in order

I have to rename them with Gthumbs due to the ease of renaming files in bulk

I use easy tag to get rid of all the tags causing the mis play, then simply copy them over to the player and typically they will play in order of file name

This stinks there has to be a better way.

Also I had to change all the defaults for rhythmbox or clemintine etc. because no matter what I do evertime I plugin the device it deletes everything off the device automatically which is a real pain in the neck

So I have to make sure that when plugging in mp3 players that I select no action taken otherwise everything I did is lost.

It's always been that way on all versions of linux or windows I never understood or learned anything about playlists. I read everything that could be read on google about it.

All end the same way.

Additionally files with the same artist and file name do not create additional tracks when putting them on the MP3 player.

For some reason it just shows as the artist, artist, artist name all the same so I don't know which file to play or which order to play them on the player since I can't see any other information about it.

Why can't I just sort by file name. ? 
Rhythmbox or any other player, and/or mp3 player does not seem to let you sort by file name unless you remove all the tages which is totally stupid. At least you can select the file name

I really need some leasons on this or where to look to understand how the mp3 player works and how the application is suppose to work.

Thanks

---

### Post by The Cog on 2012-09-30
I think many cheap players simply play the files in the order they appear in the directory, which is the order they are copied onto the player. I had one like this and wrote a python utility to re-order the directory entries into alphabetical order (the player mounted as a USB drive).

Assuming you can mount the player to your PC, you can list the tracks in the order that they appear in the directory itself (i.e. un-sorted) with the -U option of the ls command, e.g. 
ls -U /media/player/Pink\ Floyd
just to check if this is the order the player is using.

I'll happily post my utility if you think it will be useful. Let me know.

---

### Post by AgentZ86 on 2012-09-30
> **The Cog said:**
> I think many cheap players simply play the files in the order they appear in the directory, which is the order they are copied onto the player. I had one like this and wrote a python utility to re-order the directory entries into alphabetical order (the player mounted as a USB drive).

Assuming you can mount the player to your PC, you can list the tracks in the order that they appear in the directory itself (i.e. un-sorted) with the -U option of the ls command, e.g. 
ls -U /media/player/Pink\ Floyd
just to check if this is the order the player is using.

I'll happily post my utility if you think it will be useful. Let me know.

Sounds like that might be it, but I actually renamed them so they would order by file name, and removed all tags with easy tag and that does partially work. 

But then about 40% of the time when I rename the file and try do to do this, the player says it's playing the correct file name and it's acting as though it's playing out of order even though it's playing the correct file.

As if it renamed the file incorrectly but actually it didn't because when I open the directory in rhythmbox and play the files they play in order and the files are correct.

This is actually not the biggest problem but I would prefer not to have to rename the files and remove the tags and process all this. but If I don't then there is no way to listen to even an audio book

The juicer extracts the files to mp3, and then names the files like 
Disc1-1-Track1.mp3 
Disc1-2-Track2.mp3 
etc etc. 

If I put those on the player without renaming and getting rid of tags then it sorts them sort of.

But what happens is that you will get Track1.mp3 a few times in a row first because it orders them in order of that track so in fact you get something like this

Disc1-1-Track1.mp3
Disc1-2-Track1.mp3
Disc1-3-Track1.mp3

Then skips to 
Disc1-1-Track10.mp3
Disc1-2-Track10.mp3

And weird crap like this.

Windows does something different but equally annoying. And deletes all the files everytime I plug in the device to either windows or linux system

Multiple issues but it's always been that way I just assumed I didn't know what I was doing but I can't tell you how many documents I read on this to figure it out.

Anyhow thanks for the reply, I would like toy with the -U command to see what it does I'll post back thanks.

---

### Post by AgentZ86 on 2012-09-30
One last thing which is really strange and yet a different subject

I have a music folder shared, and when viewing the mp3 files from the desktop they file names are as they should be

But when viewing that shared folder from another desktop there are file names that are completely wrong and some files are missing.

So in other words I assume that those files with the wrong names are actually the files that should be the missing files but yet they are not named correctly according to the desktop that is viewing the shared folder

This makes no sense to me at all. Could this be a virus on top of these other problems ?

---

### Post by AgentZ86 on 2012-09-30
Here is a screen of the computer accessing the shared music files of another desktop

all the files that look wrong are wrong, they actually are not even there on the other computer that is sharing those files

I have no idea why they are there or why they are showing on my desktop when viewing them

Notice the order of the Disc1 files etc. 

See how files are missing but they are there on the other computer

This could be why they are playing out of order if I renamed them and it actually used some other file in the renaming of them this would make sense that it would play something out of order or actually a completely incorrect file.

However, i don't know where those files are coming from or why they are there.

Paradox

---

### Post by AgentZ86 on 2012-09-30
New info

Transfering folder to another folder and sharing causes these files to yet have even more renamed files

I did not rename them they are randomly renaming themself

This is another problem not really related to my original post but now I'm really screwed

---

