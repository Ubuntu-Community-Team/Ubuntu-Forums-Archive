---
title: "dvdstyler+subtitles"
date: 2010-03-27
forum: General Help
---

### Post by toolapc on 2010-03-27
Please help i add the srt file as stated in other popsts but get the following error message

DVDAuthor::spumux, version 0.6.14.
Build options: gnugetopt magick iconv freetype
Send bugs to <dvdauthor-users@lists.sourceforge.net>
INFO: Locale=en_GB.UTF-8
INFO: Converting filenames to UTF-8
INFO: Detected subtitle file format: subviewer
INFO: Opened iconv descriptor. *UTF-8* *ISO8859-1*
INFO: Read 1175 subtitles
ERR: New_Face failed. Maybe the font path is wrong.
Please supply the text font file (arial.ttf).
WARN: subtitle font: load_sub_face failed.
STAT: 0:03:08.390
Failed

---

### Post by rabec on 2010-03-27
I'm a new to linux but thought I'd pass this along as it worked for me after finding it at [http://www.transcoding.org/transcode?Tutorials/Authoring_PC_Media_To_DVD](http://www.transcoding.org/transcode?Tutorials/Authoring_PC_Media_To_DVD)
they recommended creating a .spumux directory in your home directory, then copy your font from your font directory. Mine was in /usr/share/fonts/truetype

---

### Post by ddefillo on 2010-03-31
Hi, I was having the same problem, so I copied the fonts folder into my home folder and that fixed my problem, I now have my videos subtitled.

---

### Post by FrankSvan on 2010-07-27
Hey Guys (and Girls)

I have this same problem as toolapc and have tried copying the font folder to my home directory (/home/frank) but still dvdstyler claims that the font is missing.

Is it possible to see where dvdstyler is looking for the font used ?

Regards

Frank

---

### Post by VH-BIL on 2010-07-27
I had this same problem not long ago, the solution I found was to use Avidemux to render the video and subtitles to a new video file and then use dvdstyler to create the dvd.

---

### Post by FrankSvan on 2010-07-27
aaaaaaaah.......

Unfortunately that did not help either (but i used work time - therefore OK)

I can preview in Avidemux, but the text lines is just some blurry stuff.

Anyway thanx to vh-bil :-)

anyone with any idea

---

### Post by VH-BIL on 2010-07-27
what do you mean blurry stuff? :)

---

### Post by FrankSvan on 2010-07-27
hehe...Blurry ... like lines with no characters 

Frank

---

### Post by VH-BIL on 2010-07-27
You can adjust the font etc.

---

### Post by FrankSvan on 2010-07-28
Gooooooodmorning ...

Now - i did not try adjusting the font (more than i allready had been trying)

However, i actually got dvdstyler working, by creating af .spumux directory within my home directory and copying the arial.ttf font to the directory.

Now, i got it working on my ubuntu 10.04 with dvdstyler 1.8XXX while im strugling to get it working on my mythbuntu 9.10 with dvdstyler 1.7XX - guess i have to upgrade the mythbuntu dvdstyler.

Anyway - thanx for the inputs here

regards

Frank

---

### Post by Apostolique on 2010-11-22
Just to clarify what was already said;

[LIST=1]
[*]Create a folder in your home directory called .spumux
[*]Copy the font called arial.ttf (Make sure it is **not** capitalized "Arial") from "/usr/share/fonts/truetype/msttcorefonts/Arial.ttf" to ".spumux"
[*]Now DVDStyler is happy :D
[/LIST]
Hope that helped the people that still had the font capitalized.

---

### Post by alegallo on 2011-01-19
Thanks everyone for the thread, I had the same problem and solved it.

One thing though is still unclear to me: DVDStyler always makes subtitles aligned to the left side of the screen, and just in Arial as far as I could see.
Is there any way to adjust it (e.g.: center and Times New Roman, for instance)?

---

### Post by alegallo on 2011-01-19
Thanks everyone for the thread, I had the same problem and solved it.

One thing though is still unclear to me: DVDStyler always makes subtitles aligned to the left side of the screen, and just in Arial as far as I could see.
Is there any way to adjust it (e.g.: center and Times New Roman, for instance)?

---

### Post by joeoshawa on 2011-03-30
I just thought i would mention since the font file is in the .spumux directory you could try puting the font you want in the directory and renaming it Ariel.ttf i have no idea if it will work but hey thats how i changed my login sound.

---

### Post by Ehknaton on 2012-05-27
> **alegallo said:**
> Thanks everyone for the thread, I had the same problem and solved it.

One thing though is still unclear to me: DVDStyler always makes subtitles aligned to the left side of the screen, and just in Arial as far as I could see.
Is there any way to adjust it (e.g.: center and Times New Roman, for instance)?

Hello,
I had the same problem, as described in this thread and I solved it thanks to the nice responses here. :guitar:
But still my subtitles appear aligned on the left hand side of the screen.
Anyone knows how to center them ?

---

### Post by oldos2er on 2012-05-27
Closed, please start a new thread for your question.

---

