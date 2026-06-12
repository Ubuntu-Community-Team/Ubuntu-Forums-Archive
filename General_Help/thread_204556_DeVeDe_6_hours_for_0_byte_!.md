---
title: "DeVeDe: 6 hours for 0 byte !"
date: 2006-06-27
forum: General Help
---

### Post by joe343 on 2006-06-27
Hi I'm trying to create a dvd from avi files using DeVeDe.  I choose the avi I want and select "create iso" and start the process... 6 hours later it says "Processing complete" and I get no error but the .iso file is zero byte ! I also tried creating "dvd structure" instead of an iso with the same result: the video_ts folder is empty.

The target folder is in my /home.  I'm using DeVeDe 2.0 and Ubuntu 6.06.

Thanks for your help.

---

### Post by PapaWiskas on 2006-06-27
This happened to me once.  I checked the properties of the .avi file and the only difference I could find versus other avi files that did work, was the audio stream was AC3 and not MP3.

So I had to use avidemux to convert the avi file with the AC3 audio to a DVD compatible mpg, once I did that and did my DVD project again it worked fine.

You right click on the avi file and go to the last tab to view the properties of the file such as audio stream and framerate etc.

Also on another note, I use Tovid, because it seemed to me Devede had some serious issues with audio not syncing to the picture.  I just prefer Tovid.

---

### Post by joshrobinson on 2006-06-27
[QUOTE=PapaWiskas]

Also on another note, I use Tovid, because it seemed to me Devede had some serious issues with audio not syncing to the picture.  I just prefer Tovid.[/QUOTE]

yes devede had terrible audio sync for me also, are you the one papa that had trouble getting your dvd's to play? did you burning the dvd with makedvd work?

---

### Post by joe343 on 2006-06-27
Ok I'll try that thanks.  
I also tried tovid but there's something that I don't like about it (or maybe it's me who's not using it right), it's that you cannot reduce the quality of the video as you like because there a minimum of 1691k/sec.  In devede, you can go as low as you like (with quality loss of course).  Is there a way to tell tovid "I want a 4.3 gig dvd with all those videos so reduce the quality accordingly" ?

---

### Post by PapaWiskas on 2006-06-27
[QUOTE=joshrobinson]yes devede had terrible audio sync for me also, are you the one papa that had trouble getting your dvd's to play? did you burning the dvd with makedvd work?[/QUOTE]


yes josh, that was me, and I made sure I thanked you in that post for your assistance.  I have since burned 10 DVDs with no problem.
[http://www.ubuntuforums.org/showthread.php?t=200590&page=2](http://www.ubuntuforums.org/showthread.php?t=200590&page=2)

As for your question joe, I am not certain about that, but if you go to the tovid forums they should be able to answer that for you.  
[http://www.createphpbb.com/tovid/](http://www.createphpbb.com/tovid/)
I mainly use tovid for making DVDs of avi files of television shows.

---

