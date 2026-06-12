---
title: "problem with &quot;cat&quot; command"
date: 2009-12-25
forum: General Help
---

### Post by shaon3343 on 2009-12-25
[SIZE=2][B]hi I'm using ubuntu 9.10 . I've converted some movie file to .mkv format ( from .vob) with "handrbrake" . now when i want to merge those 2 .mkv file with cat command they are showing that they ar merged in one file but actually they are not. when i play that merged movie file i noticed that its actually the first .mkv file!! The 2nd file just lost!!! but cat command is working with .VOB files ( those are not converted)! So can anyone say whats the wrong? 
I used this command:
            > cat VTS_03_1.mkv VTS_03_2.mkv >muvie.mkv[/B][/SIZE]

---

### Post by chewearn on 2009-12-25
VOB files are MPEG2 stream, where a simple "cat" command could merge two files without requiring anything else.

However, because of the way the mkv container is structure, I don't think you could simply join two mkv files by the same "cat" command.

To properly join two mkv files, you could use the mkvtoolnix utility.  The tool plus GUI front-end can be installed by:

```
sudo apt-get install mkvtoolnix-gui
```
.

Or click this link: [apt://mkvtoolnix-gui](apt://mkvtoolnix-gui)

.

---

### Post by andrew.46 on 2009-12-28
Hi shaon3343,

I could not see clearly in the mkvtoolnix gui where to append files but it looks pretty straightforward from the commandline. If you have file1.mkv and you wish to join it to file2.mkv and you wish to append these to produce output.mkv you would run:

```
mkvmerge -o output.mkv file1.mkv + file2.mkv
```

with the important reservation that mkvmerge is a little fussy about which files it will actually append in this fashion. Hopefully yours will join neatly :).

All the best,

Andrew

---

### Post by chewearn on 2009-12-28
[1] Click to add the first file.
[2] Click to append the second file to the first file.

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=141442&stc=1&d=1261991546[/IMG]

---

### Post by andrew.46 on 2009-12-28
Hi chewearn,

> **chewearn said:**
> [1] Click to add the first file.
[2] Click to append the second file to the first file.

I hang my head and shame and go to clean my glasses ......

Andrew

---

### Post by chewearn on 2009-12-28
No worries, I missed the "Append" button the first time too. :p

---

### Post by sleepee on 2010-01-18
interesting... i seem to be having the same problem with the cat command too..
i used to use it for merging all types of video files together all the time..  avi, mpg, ogv, etc
now it won't work with any kind of video..
i get the exact same result as shaon...
but i'd actually prefer to fix this cat command instead of using a gui...  i just find it easier to use the terminal for this type of thing..
i wonder if shaon's found a way to fix it or just ended up using the mkvmerge program

---

### Post by llama320 on 2010-01-18
> **sleepee said:**
> interesting... i seem to be having the same problem with the cat command too..
i used to use it for merging all types of video files together all the time..  avi, mpg, ogv, etc
now it won't work with any kind of video..
i get the exact same result as shaon...
but i'd actually prefer to fix this cat command instead of using a gui...  i just find it easier to use the terminal for this type of thing..
i wonder if shaon's found a way to fix it or just ended up using the mkvmerge program

As far as I can tell, it's not as if cat is somehow "broken" in need of fixing. The mkv format just needs to be processed at a higher level than a simple appending of bytes. If you want to use the CLI, mkvmerge seems to have that option. Try that

---

### Post by sleepee on 2010-01-18
> **llama320 said:**
> As far as I can tell, it's not as if cat is somehow "broken" in need of fixing. The mkv format just needs to be processed at a higher level than a simple appending of bytes. If you want to use the CLI, mkvmerge seems to have that option. Try that
hmm...  well, i don't know much about video, but i know i used to use cat before and it worked...
but is there another program you could recommend that works with more file types??  because i usually don't use mkv that much..

---

### Post by chewearn on 2010-01-18
1. For mpg, a cat command should work.  mpg file does not have a container; it's merely the muxed bitstream.

2. For avi, the cat command would create an improper avi.  But many media player is smart enough to ignore the error.  If you would like to join avi files and create a proper output, you can use *avidemux*

I have no idea about ogv.

---

### Post by sleepee on 2010-01-19
> **chewearn said:**
> 1. For mpg, a cat command should work.  mpg file does not have a container; it's merely the muxed bitstream.

2. For avi, the cat command would create an improper avi.  But many media player is smart enough to ignore the error.  If you would like to join avi files and create a proper output, you can use *avidemux*

I have no idea about ogv.

thanks..
i'm trying out avidemux now..  :grin:

---

