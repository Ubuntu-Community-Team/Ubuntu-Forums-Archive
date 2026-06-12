---
title: "ddrescue image file trouble"
date: 2012-06-28
forum: General Help
---

### Post by Dave Vader on 2012-06-28
Hello Ubuntu experts,
I have clearly done something wrong.
I had an old scratchy DVD with some old band footage i transferred from VHS, it wouldn't rip into the computer properly, so I decided after some judicious googling to use ddrescue to fix it.
The program seemed to go well, and after 2 and a half days, I had a rescued file on my HDD. However, i didn't specify a filetype for the output file when I ran it, and the subsequent result is not recognised by archive manager.
I'm running ubuntu 11.04 on my old laptop for this, anybody got any experience at extracting the data from unknown image files? Anybody got another way of getting the files out? (disc is a RW done on an old LG that automatically copy protected it, and made it very difficult to get at the video, which is the notorious .VRO awkward file type).
I have been using ubuntu on and off for a good 3 years or so now, but am still not terribly good with bash, so please treat me as a total novice, thanks.

---

### Post by sudodus on 2012-06-28
I think that you should basically reverse the dd or ddrescue operation. Do you remember the command you ran?

Source: device or file?
Target: file or compressed file?

If it was device (DVD) to file, you might try ddrescue

1. file to device (USB might work)

or more probably

2. rename the file to [FONT="Courier New"][SIZE="3"]file.iso[/SIZE][/FONT]

a. Use for example ***brasero*** to burn a DVD from the iso image file, or

b. Open it with the archiver program ***file-roller*** and extract the video files directly, using drag-and-drop in the GUI.

*. If it was compressed, uncompress it first, then do the above.

---

### Post by zero2xiii on 2012-06-28
EDIT: snap sudodus beat me to it hahaha.
Also try 7z to try and "extract" the contents, it works on ISO files no prob:

```
sudo apt-get install p7zip-full
```

Hay,

I assume it will use an ISO or Loop or fuse image for the created image.

To mount it, might be a difficult task in terminal. I recommend downloading and installing "furius ISO mount" (it is in the repro's). Try both mounting options on the left hand side (Fuse and Loop). Note that loop requires sudo privs to mount.

If non of them work, then we can start and try mounting things manualy with various parameters.

If the above failed, please run the file command on the image file generated and post the output here:
```
file /path/to/created/image
```
example
```

file ubuntu-12.04-desktop-amd64.iso 
ubuntu-12.04-desktop-amd64.iso: # ISO 9660 CD-ROM filesystem data 'Ubuntu 12.04 LTS amd64          ' (bootable)


```

This should give us a better indication of the file type we are working with.

Cherz

---

### Post by Soodiarof on 2012-06-28
Recent U.S. data has been erratic, via how the latest report on Thursday posting each of our number out of Americans lining up concerning contemporary jobless benefits fell last week intended for the main initially  a while since April. Payrolls wearing May contracted sharply, sparking a complete sell-off very sent assets tumbling across unquestionably the board. ï»¿[longchamp le pliage](http://longchamp-uk.livejournal.com/) About his prepared comments, this Fed chairman didn?Â¡Â¥t call for many consideration as to additional stimulus, that contrast from this speech earlier this important week into which may Vice Chairman Janet Yellen said the exact economy ?Â¡Ã£remains vulnerable to assist you to setbacks?Â¡Ã€ as well as , may warrant more accommodation. ï»¿[longchamp le pliage](http://longchamp-uk.livejournal.com/) Virtually any week after Republican presidential candidate Mitt Romney disclosed another fortune worth as much as $250 million, his campaign said Wednesday that a lot of they plans in the market to put his holdings to the actual federal blind trust if that she would be elected president. ï»¿[http://longchamp-uk.livejournal.com/](http://longchamp-uk.livejournal.com/)

---

### Post by Dave Vader on 2012-06-28
None of the archive managers will recognise it as a viable filetype. I tried 7zip, and file-roller. I am loathe to run ddrescue in reverse on it, as it took 3 days to run last time, and I would rather not run it unless it is my last option.

If I recall correctly the command I ran was

```
ddrescue /sda1 /home/dvd
```

Which is a little unsophisticated, but as I mentioned I am a bit noobish at terminal, and this was my 4th attempt to get the filetype right in the first place.

Here is the output from my file probe. Not helpful, I suspect I may have to start again.


```
dave@dave-Latitude-D620:~$ file-roller dvd
dave@dave-Latitude-D620:~$ file dvd
dvd: data

```

---

### Post by zero2xiii on 2012-06-28
Hay,

Wow that's weird. Have you tried mounting it with furious?

I think your syntax MIGHT cause the issue here. but we will get to that just now.

Running the command in reverse will not take as long, it will take only as long as the write speed for the data.. In other words the stream from the file to the drive. Since the first run (from drive to file) was done numerous times to try and "recover" the data.

Please post the output of the "ls" of the location. I am wondering if ddrescue created a file, or a drive.. Seems strange.

What is the output of:
```
du -h /path/to/image
```

I am having a truelly hard time duplicating the issue. I took a cd and ddrescue it to /home/$USER/recover.img and it opens fine in archive manager with 7zip support and also mounts fine under furius ISO mount.

The lack of an extention might be what is causing the "issue"..

Maybe try to copy the data again with dd just to another location:
```
dd if=/path/to/data of=/new/path/to/file.img
```
Please make sure so append an extension in the DD command so as not to create a raw "nothing" if you wish.

I really am at a loss here. Maybe someone else has some more insight or have experienced something similar before. Because I can not reproduce the problem.

Cherz

---

### Post by Dave Vader on 2012-06-28
> **zero2xiii said:**
> Hay,


What is the output of:
```
du -h /path/to/image
```


Cherz

```
dave@dave-Latitude-D620:~$ du -h dvd
4.4G	dvd
dave@dave-Latitude-D620:~$ 

```

Will try the other commands and stuff in a minute....

---

### Post by Dave Vader on 2012-06-28
Oh, forget everything, furius seems to have done it in loop mode.
Thanks a lot to both of you, hopefully I can hack out the bits of this video I actually want now.

---

### Post by sudodus on 2012-06-28
> **Dave Vader said:**
> Oh, forget everything, furius seems to have done it in loop mode.
Thanks a lot to both of you, hopefully I can hack out the bits of this video I actually want now.
That's great :KS

I think that if you had moved=renamed the file to file.iso, file-roller would also have been able to read it, or you would have been able to burn it to a DVD, but one solution is enough.

If more obstacles in the rest of the task: please come back and ask for help, otherwise click on **Thread Tools** at the top of this page and mark this thread as SOLVED

---

### Post by Dave Vader on 2012-06-29
I did move and rename it to .iso and file-roller still didn't like it, but furius suddenly sprang into action.
I now have my 3.5 Gb .VRO video file, it is now making all video editing software crash. But that is a seperate issue, which i think I might be able to solve myself.
Thanks all.

---

