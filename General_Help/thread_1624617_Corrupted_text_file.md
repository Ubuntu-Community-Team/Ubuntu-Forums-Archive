---
title: "Corrupted text file"
date: 2010-11-18
forum: General Help
---

### Post by kwhatcher on 2010-11-18
I have a file that has become corrupted after a hard power off. The file was saved and the editor (Focus Writer) was closed when it happened. 

Now in Focus Writer, vim, and cat show a whole bunch of gibberish except for the last couple of paragraphs. 

gEdit throws a could not detect the character encoding. 

Scrivener and textedit on my iMac also had gibberish except for the last few paragraphs. 

I can provide both the most recent backup and the corrupted file. I would attach it, but it is too big. ~33,000 words. 

*Note* I do have daily email to self backups except for yesterday and today due to no internet. That, however, represents several thousand words lost.

Thanks,
Kerry

---

### Post by kwhatcher on 2010-11-18
If I need to provide some more details or something please let me know. 

Thanks,
Kerry

---

### Post by Mark Phelps on 2010-11-18
If the file was closed and the app was also closed when you powered off, based on what you've said, I would suspect a more generic total filesystem corruption problem than just this one file.

Folks here have had success using Testdisk and Photorec for restoring partitions and files.  You should search using those terms -- unless someone else stops by with direct links.

---

### Post by kwhatcher on 2010-11-18
There doesn't seem to be any other files that have issues. I ran photorec but I ran out of diskspace on my thumb drive (text files only). 

I ran "find . | xargs grep 'string' -sl" to try and find the file I needed but it wasn't there. I used some of the readable text at the end of the file for 'string'. 

So I guess my next step is to use a bigger thumb drive and try again. Is there any way to get photorec to ignore all of my php and xml files and just look for txt files? 

You can see the file at [http://netbluehosting.com/sites/default/files/nano2010.txt]("http://netbluehosting.com/sites/default/files/nano2010.txt")

Thanks,
Kerry

---

### Post by kwhatcher on 2010-11-19
So I did a photorec on the whole disk and couldn't find the txt file I was looking for. Maybe search command was wrong?

find /meda/crystal_usb/ | xargs grep "Definitely. We stopped" -sl

Any ideas?

---

