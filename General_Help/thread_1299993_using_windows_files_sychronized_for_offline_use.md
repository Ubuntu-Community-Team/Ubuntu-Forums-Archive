---
title: "using windows files sychronized for offline use"
date: 2009-10-24
forum: General Help
---

### Post by mavros on 2009-10-24
Windows XP Pro offers the possibility to synchronize shared files or entire shared directories mapped as drives for off-line use. I use this functionality to keep my music and pictures between NAS, laptop and netbook synchronized. Pictures is mapped as Y: Music as Z:in Windows.

The plan: also use these files in Ubuntu (Karmic or Jaunty) in audio and graphics programs.

The problem: when I switch to Ubuntu my Windows partitions are there all normal files can be accessed but I can not find the offline drives and files even when still online. Any chance of accessing them on the Ubuntu "side"? I suppose they are somehow zipped in one of those random named (eg5tz6538jketsa..)  files on the Windows partitions.

Alternative would of course be using a classical synchronization program in the Windows environment but till now this has always proven slow and in particular for music files it usually requires a lot of manual corrections.

---

### Post by mavros on 2009-11-02
I may have posted this on the wrong froum as no-one seems to be interested this typical dual boot problem.

Coose to use the workaround.

---

### Post by Roasted on 2009-11-02
I don't know about you, but I find offline files to be a headache in Windows. Just recently we made the switch at work to ditch offline files all together.

If it's a laptop, we keep the files local on the computer, and use Synctoy to back them up to the file server.

If it's a desktop, their my documents folder is re-routed to the file server so they work right off of the actual server.

At home I use my Ubuntu computer as a backup/file server, using a free program known as SyncBack SE to synchronize the XP users "My Documents" folder to their password protected Samba share on my Ubuntu machine. This happens every day at 3 am. That way when the expected re-install of an XP computer in the house is needed, the data is already backed up.

I'm not sure if this helps or not, but I wanted to throw my situation out there on the table so you could at least hear what somebody else is doing and perhaps apply it to your own situation.

---

### Post by P4man on 2009-11-02
Have a look here:
[http://www.hardforum.com/showthread.php?t=1241381](http://www.hardforum.com/showthread.php?t=1241381)

Its pretty damn hard to access those files from a windows environment, I think you can forget about using it with ubuntu.

I would suggest a very neat crossplatform alternative:

[http://www.cis.upenn.edu/~bcpierce/unison/](http://www.cis.upenn.edu/~bcpierce/unison/)

unison.

---

### Post by mavros on 2009-11-03
Thanks for the input this looks too complicated indeed. Personally I have good experience with Windows XP pro at work with offline files. I never lost anything even in a 'disciplined' multiuser environment (meaning don't edit a none owned file but make a copy with a short name extension first). It is much faster then any dedicated open source or freeware synchronisation software I tried. 

I use Allway Sync now. It works but always make a fuss with all short of silly warnings and unexplained exclusions. I will give Unison a try.

This thread can be closed.

---

