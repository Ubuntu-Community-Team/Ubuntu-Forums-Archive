---
title: "M3U from NTFS directory needed"
date: 2006-01-31
forum: General Help
---

### Post by ahave2005 on 2006-01-31
I've done searches in synaptic, Ubuntu, google, debian.
I've tried to learn bash scripts, with some success, since I've helped a good few.
Mostly in danish forums.(never mind the politics)

But I just cant figure out how to make a m3u file. Especially the duration thing. I've searched, but can't find a command line that would give me the the duration of a track.

There might be a program GNOME/KDE/terminal, that will do the trick, but I can't find it.
I've encoded my huge cd collection in my windows days, on a NTFS drive. More than one, but one of my M0 maxtors was too much of a grave(not the first time) Anyways I'm on a warranty of maxtor.com. I'm aware about beeing a sissy, since I do backups, but I haven't got a clue about what to do now.

I need to make playlists, and have these to reside on my ext2drive, since my players apparently don't reconize winamp playlists.

I would like to make playlists in my home partition, and I need script to do the trick. It shouldn't be a problem, but I've tried about everything I know of.

A script that make playlist of all my mp3's to a another directory than my partition where my mp3's are.

What would you do?

I've no idea, tried all that I know, and You might have an idea.

/ahave

---

### Post by ahave2005 on 2006-02-07
Don't tell me no one, have tried this or have an idea?
/ahave

---

### Post by aeiah on 2006-02-20
if your m3u files are pointing to mp3s that have a relative path (ie, just a few directories up the tree eg: "audio\album\song.mp3") then totem should be able to figure out your windows slashes and replace them with audio/album/song.mp3, but i havent found another player that'll do this as of yet.

if your playlists are pointing to songs like "c:\audio\album\song.mp3" then you will have to create new playlists from scratch, or use a mass converging tool.

im in a similar situation to you and due to the ammount of songs i have, im reluctant to just create new playlists, id much rather my preferred media player could read the windows m3u files. beep media player is set out very similar to winamp and you can create playlists easy enough with that and save them to your /home directory, but it has no batch processing.

i found fapg last night but havent had time to check it out, it might be able to help you: [http://royale.zerezo.com/fapg/](http://royale.zerezo.com/fapg/) 

its located in the synaptic package manager for an easy install

---

