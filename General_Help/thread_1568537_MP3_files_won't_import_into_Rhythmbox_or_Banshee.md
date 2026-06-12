---
title: "MP3 files won't import into Rhythmbox or Banshee"
date: 2010-09-05
forum: General Help
---

### Post by jereece on 2010-09-05
I have a Sansa mini-clip MP3 player.  Now that I am using Ubuntu I wanted to totally redo my play lists.  So using the Sansa menu, I formatted the MP3 player to start fresh.  Then I opened Rythmbox and was going to import my MP3 files from my hard drive.  Only problem is all of my MP3 files are grayed out on the import files menu.  Then I installed Banshee and tried to import the MP3 files and they are grayed out in that program too.  

I did a quick search of this forum and it did not find anything.  Can anyone tell me why my MP3 files won't import into Rythmbox or Banshee?

Thanks,
Jim

---

### Post by cottfcfan on 2010-09-05
Hi Jereece,
You dont say which version of Ubuntu or Banshee you are using.
I'm using 10.04 & Banshee 1.74.
Ive just plugged my Sansa Clip in and it comes up in Banshee on the left.
If I right click "Sansa Clip" theres an option to import to Library.
Works fine for me although i'm not using the "mini" version.

Just an edit, are you transferring music from your Sansa clip to your hard drive or the other way round?

---

### Post by jereece on 2010-09-05
Sorry...I am using Ubuntu 10.4 and Banshee 1.61.  Also, my Sansa is the Clip not mini-clip.  Sorry for the confusion.  I can't get any of my MP3 files imported into Banshee.  When I click on Media and then Import Media and go to my hard drive where my backup files are located, all my MP3 files are grayed out.  I am trying to import my MP3s into Banshee and then from Banshee to my Sansa Clip.

---

### Post by cottfcfan on 2010-09-05
Try adding the Banshee ppa to your sources list, and upgrade to 1.74.
Its a long shot but it may work.

---

### Post by jereece on 2010-09-05
I guess it's time for me to learn something new.  How do I add the Banshee ppa to my sources list?  I don't have a clue.

I appreciate the help.
Jim

---

### Post by cottfcfan on 2010-09-05
Open a terminal and paste the following commands one at a time:

sudo add-apt-repository ppa:banshee-team/banshee-unstable

sudo apt-get update

sudo apt-get upgrade

you should now have the latest Banshee.
As i say it may or may not do what you want, but it wont do any harm.

---

### Post by jereece on 2010-09-05
I may have solved the problem.  I added all of my MP3 files from my external drive to my "Music" folder in Ubuntu.  Then in Banshee I clicked on Tools>Rescan Music Library.  This imported the MP3s into Banshee.  Then in Banshee I clicked on Sync From Favorites and then clicked Sync.  That appears to have worked.  I am unsure however why it would not let me import the MP3s from my external drive however.  But at least this works.

Thanks,
Jim

---

### Post by cottfcfan on 2010-09-05
Nice to hear your sorted.
you could still give the Banshee thing a try, it may be more compatible with you Sansa, being more upto date.

---

### Post by old ben knobi on 2011-01-18
There are actually 2 parts to solving this problem:
First is the MTP support for Ubuntu; second is the [FONT=Fixedsys].is_audio_player[/FONT] file that gets
placed on the MP3 player itself.  I have recently tested this out on both Rhythmbox
and Banshee using a Sony NWZ-E444 Digital Media Player, using Ubuntu Lucid (10.04 LTS) with Banshee 1.80.

In Banshee,  press F1 for Contents Help;
there is an entry heading "Sync your media with a portable music player" - 
which links to this:
1.4.2.&#8195;MTP Media Players

A number of MP3 players, such as those produced by Samsung use Media Transfer Protocol (MTP). These devices, when used with the correct driver, often appear in Windows as a media device but can be accessed as a USB device.

Ubuntu supports these devices but requires two steps:

   1. Install the mtpfs and mtp-tools packages.
   2. Open Applications &#9656; Sound & Video &#9656; Rhythmbox Music Player.
   3. Click Edit &#9656; Plugins
   4. Tick the Portable Players - MTP plugin.
   5. Click Close.

Your device will now be displayed in the left-hand pane under Devices when connected

In fact there is a bit missing: the .is_audio_player file.
Using an editor and/or Nautilus create the file with these entries:

audio_folders=MUSIC/,RECORD/
folder_depth=2
output_formats=audio/ogg,audio/x-ms-wma,audio/mpeg,audio/wav,audio/mp3
[FONT=Verdana]
You may need to restart Banshee or Rhythmbox.  You can then sync your music
to the MP3 device.

There is a help list for the settings for .is_audio_player on this link:[/FONT]
[http://www.floccinaucinihilipilification.net/wiki/index.php/.is_audio_player_file_format](http://www.floccinaucinihilipilification.net/wiki/index.php/.is_audio_player_file_format)
so experiment to fine tune the settings.  It should be possible to sync playlists also
but I've not tested for that.

---

