---
title: "Editing large files..."
date: 2006-04-13
forum: General Help
---

### Post by CornMaster on 2006-04-13
This is probably not the best place to post this, but if someone wants to move it...be my guest. :)

Need some general programming help.  I have a huge xml file...like 10 MB that I download with TV Listings in it.

I wrote a perl script that goes through the file and adds one to the channel number (because tvtime (and all TV programs on linux actually) display the wrong channel number).  Basically the script is a loop that reads each line, and then adds one where needed, and then writes a new file when it's done. 

Now...this script takes hours to run.  I've tried to optimize it, but my programming is limited, as is my perl.  The part of the file I need to edit is actually only a few K.  Maybe 100 or 200 lines, and it takes roughly a second (when I create a test file) but looping through the rest of the file, and just outputting it takes a long time.

My questions are:
1) Is there a way to edit a perl file in it's place.  So my loop can update the numbers, and leave the rest of a file in tact...
OR
Is there a way to take every line after a point (identified with a regex) and output the whole thing in one command?
2) Since it's an XML file, I can probably use the XML modules in perl to edit the file more neatly...however, I read it over, and I got lost.  Anyone know any straight forward tutorials that could help out?  Or better yet, help walk me through some of it. :)
3) We could also fix my tvtime.  I've looked at the config file for the stations, and subtracted one from all the numbers, and saved the file...and reloaded tvtime, but the numbers are still off.  So I figured there must be a second source for the info.  Any help here can negate the programming. ;)

Thanks in advance for any insights.

---

