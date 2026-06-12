---
title: "I Need a script please"
date: 2006-03-07
forum: General Help
---

### Post by chronusdark on 2006-03-07
i was wondering if its possible/can someone make a script to allow me to select some mp3 files then i can right click and click a script from the scripts menu and it will do a 

```
cat "all the files i select" > "Prompt for filename"
```

i seems easy enough im just not sure on how to go about it myself or i would

---

### Post by aysiu on 2006-03-07
Cat just lists things, as far as I know.
If you want to rename MP3s *en masse*, use TagTool or EasyTag.

---

### Post by chronusdark on 2006-03-07
cat in this case joins my mp3 files into whatever is after ">" im using it right now to orginize my audiobook cd's into chapters but its very time consuming

the script would make it much easier

---

### Post by aysiu on 2006-03-07
EasyTag and TagTool can help with this--believe me. I renamed about 8000 of my MP3s with EasyTag, and it saved me weeks of work.

They don't just work with tags--they work with filenames, too. TagTool is easier to use (ironically enough), but EasyTag is more sophisticated.

Unless you're talking about actually combining MP3s...? You're just talking about mass-renaming, right?

---

### Post by chronusdark on 2006-03-07
im using it to combine mp3 files....the books come as like 150 or so tracks and i want to consolidate them to like 30 mp3's named after each chapter and tagged accordingly
im using tag tool to tag and the cat command to combine and its taking forever

---

### Post by aysiu on 2006-03-07
Have you looked at mp3wrap? It's in the Universe repositories. This is the description from Synaptic Package Manager: > **Utility for MP3 wrapping (rolling multiple MP3s into one)**
Command-line utility that wraps multiple MP3 files into a a single, playable MP3, without losing filenames or ID3 information, and without reencoding. Also supports archiving non-audio data such as playlists, info files, and cover images inside the MP3. These files can be unpacked later (using mp3splt, e.g.); ordinary MP3 decoders can play the entire audio stream as one long track.

This is a free, independent alternative to AlbumWrap:
[http://www.infamus.com/albumwrap/](http://www.infamus.com/albumwrap/)

Homepage: [http://mp3wrap.sourceforge.net/](http://mp3wrap.sourceforge.net/)

---

### Post by chronusdark on 2006-03-07
i got that the idea is tho i want to do it from in nautilus like with a gui the typing is driving me crazy

---

### Post by aysiu on 2006-03-07
You don't have to do that much typing.

Get all the MP3s you want joined together into a folder (using Nautilus) and then *cd* to that folder and then ```
mp3wrap -v album.mp3 file*.mp3
```

---

### Post by chronusdark on 2006-03-07
this will (i assume) wrap the files in incremental order?

---

### Post by aysiu on 2006-03-07
[QUOTE=chronusdark]this will (i assume) wrap the files in incremental order?[/QUOTE] I don't know. Let me test it out.

---

### Post by aysiu on 2006-03-07
It did it incrementally. Unfortunately, I didn't do a scientific enough test to see whether it was incrementally by filename or by tag title, as both the tags and filenames had numbers in them. Here's my output: ```
user@ubuntu:~$ sudo apt-get install mp3wrap
Reading package lists... Done
Building dependency tree... Done
Recommended packages:
  mp3splt
The following NEW packages will be installed:
  mp3wrap
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 18.1kB of archives.
After unpacking 94.2kB of additional disk space will be used.
Get:1 http://archive.ubuntu.com breezy/universe mp3wrap 0.5-1 [18.1kB]
Fetched 18.1kB in 1s (11.6kB/s)

Preconfiguring packages ...
Selecting previously deselected package mp3wrap.
(Reading database ... 68306 files and directories currently installed.)
Unpacking mp3wrap (from .../mp3wrap_0.5-1_i386.deb) ...
Setting up mp3wrap (0.5-1) ...
user@ubuntu:~$ cd Desktop
user@ubuntu:~/Desktop$ mp3wrap keane.mp3 Keane*.mp3
Mp3Wrap Version 0.5 (2003/Jan/16). See README and COPYING for more!
Written and copyrights by Matteo Trotta - <matteo.trotta@lib.unimib.it>
THIS SOFTWARE COMES WITH ABSOLUTELY NO WARRANTY! USE AT YOUR OWN RISK!

  9 %   --> Wrapping Keane - 01 - Somewhere Only We Know.mp3 ... OK
  18 %  --> Wrapping Keane - 02 - This Is the Last Time.mp3 ... OK
  27 %  --> Wrapping Keane - 03 - Bend and Break.mp3 ... OK
  36 %  --> Wrapping Keane - 04 - We Might As Well Be Strangers.mp3 ... OK
  45 %  --> Wrapping Keane - 05 - Everybody's Changing.mp3 ... OK
  54 %  --> Wrapping Keane - 06 - Your Eyes Open.mp3 ... OK
  63 %  --> Wrapping Keane - 07 - She Has No Time.mp3 ... OK
  72 %  --> Wrapping Keane - 08 - Can't Stop Now.mp3 ... OK
  81 %  --> Wrapping Keane - 09 - Sunshine.mp3 ... OK
  90 %  --> Wrapping Keane - 10 - Untitled 1.mp3 ... OK
  100 % --> Wrapping Keane - 11 - Bedshaped.mp3 ... OK

  Calculating CRC, please wait... OK

keane_MP3WRAP.mp3 has been created successfully!
Use mp3splt to dewrap file; download at http://mp3splt.sourceforge.net!
``` I even did a test play to make sure it played in order--it did.

It seemed there was about a three-second gap between songs (or, in your case, book chapters?), but I'm not sure if that was part of the wrapping process or just dead space at the end of the song.

---

### Post by phuturism on 2007-06-26
Have to say that script rocks.  Great for merging dj mix albums split into separate tracks into one long mp3.

Confirm there is no gap between tracks - so for the original poster the silences must have built in to the original CD tracks.

And its about 20 times faster than any windows gui app I have used for this purpose.

---

