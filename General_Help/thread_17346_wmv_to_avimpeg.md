---
title: "wmv to avi/mpeg"
date: 2005-02-27
forum: General Help
---

### Post by Phosphoros on 2005-02-27
Hi, hope this question is remotely in the right section.  I looked around and did some searching with no real results. So I thought I'd ask here.

I'm wanting to convert some wmv files to well, **any** format other than wmv.  avi or mpeg will work but heck even mov files would be fine.  Avi would be ideal as I can use kino to edit them.

Anyone have any ideas on some software that could do this for linux?  I guess I'm to much a newbie to know good places to look.

Thanks  :smile: 

Phosphoros

---

### Post by quino on 2005-02-28
check out:

[http://tovid.sourceforge.net/](http://tovid.sourceforge.net/)

it's only a front end and you'll have to install several packages yourself, and it'll convert to VCD-ready mpegs (which does mean much larger file sizes -- so I'm not sure if this is exactly what you're looking for).  With this you can covert your video clips to VCDs, which may also be of use to you.

the exact commands to use (and their programs) is fairly complicated AFAIK, but maybe the scripts that tovid uses can be of use to you to see how the programs are called to convert from one type of video to another.

---

### Post by Phosphoros on 2005-02-28
[QUOTE=quino]check out:

[http://tovid.sourceforge.net/](http://tovid.sourceforge.net/)

it's only a front end and you'll have to install several packages yourself, and it'll convert to VCD-ready mpegs (which does mean much larger file sizes -- so I'm not sure if this is exactly what you're looking for).  With this you can covert your video clips to VCDs, which may also be of use to you.

the exact commands to use (and their programs) is fairly complicated AFAIK, but maybe the scripts that tovid uses can be of use to you to see how the programs are called to convert from one type of video to another.[/QUOTE]
 Thanks, I have to say though that's probably the biggest pain in the butt I've ever read.  hehe
Quite the nightmare to install.

The vids I'm trying to convert are rather small (smaller than 5 megs), but sadly they are all in wmv format.

I'll give this a try but being that I'm such a newbie to linux I doubt I'll get it to work.  But, can't learn until you break something and try to fix it.

Thanks again quino

---

### Post by bored2k on 2005-02-28
there is an easier way for n00bs

get repositories found in [http://ubuntuguide.org/#gettingstarted](http://ubuntuguide.org/#gettingstarted)

follow this instructions

i am tired of doing it so it works [after installing w32codecs and mplayer

[http://www.videohelp.com/forum/viewtopic.php?t=242455](http://www.videohelp.com/forum/viewtopic.php?t=242455)

---

### Post by quino on 2005-02-28
Avidemux looks cool!

How did you get it to install?  synaptic complains about needing newer versions than are available (it sees Ubuntu specific packages which are older).

I have
[ftp://ftp.nerim.net/debian-marillat/](ftp://ftp.nerim.net/debian-marillat/)
[http://apt.cerkinfo.be/](http://apt.cerkinfo.be/)
and ubuntu warty multiverse in my repositories ...

which repositories did you use?  did you force-install?

---

### Post by bored2k on 2005-02-28
I'm not sure how to actually get it to work on Ubuntu  i recently ported from Debian and dont know their repositories that much .

U can still get the binaries in  [http://avidemux.sourceforge.net/](http://avidemux.sourceforge.net/) .


It is exactly like virtualDUB for windows, only gtk and cuter  :lol:

---

### Post by ixus_123 on 2005-02-28
mencoder (included with Mplayer will probably do the job.  It's command line but dont let that put you off - there are plebty of howto's on the subject if you google.

If you don't already have Mplayer there is a good howto in the Ubuntu Howto section of the forums.  You might want to read the whole thread & get the script with the latest mplayer & codec pack.

When you are done installing that, open up a terminal and type something like:

```
kieren@Mesh:~/Movies$ mencoder -ovc lavc Thailand_2003.mpeg -oac mp3lame -o Thailand_2003.avi
```

^ that's from a text file I saved from my diving holiday.  

You will need to to need to change to the directory the file is first, or to make things simple just have the file you want to convert in your  /home directory.  Change the first filename for you wmv filename, & the 2nd one (Thailand_2003.avi) to what ever you want the uotput file to be called.

There are also options to resize the video resolution:
```
kieren@ubuntu:~/Video $ mencoder Thailand_2003.avi -ovc lavc -lavcopts vcodec=mpeg4 -vop expand=220:180,scale=220:-2 -o Thailand_spv.avi -oac mp3lame
```

In this example I am downsizing the converted file to a resolution of 220x180 for playing on my mobile phone.

It's worth noting that it's actually bad form to resise to the resolution that I did becuase mpeg resolutions should be able to divide by 8 so 176x144 probably would have been better for my phone.

(the avi container file that is produced above contains mpeg4 for video & mp3 @ 128kbps for sound)

---

### Post by quino on 2005-03-01
thanks for the help:  I'm not unfamiliar with the command line, but I am completley lost when it comes to the commands I need to run to convert a particular file type to another (I had been trying to create VCDS, which is how I came across the tovid script).

Examples are good to study!

Thanks!

---

### Post by Phosphoros on 2005-03-01
Well I guess I'm to much of a newbie because none of these suggestions will install.
I'm obviously in dependency hell and it gets rather old fast.  #-o 

I managed to get mplayer installed after about 40 minutes fighting it.  Had tons of warnings but it seems to run fine.  But I can't get tovid nor abidemux.  I gave up on tovix but decided to go with avidemux.  

I suppose, and I hate to say this at the risk of getting falmed, I'll just burn the stuff to cd and do it in windows. :(

Thanks for all the suggestions, I do appreciate it.  I've just been fighting Linux to much over the last couple days to want to deal with it.

---

### Post by Phosphoros on 2005-03-01
[QUOTE=ixus_123]mencoder (included with Mplayer will probably do the job.  It's command line but dont let that put you off - there are plebty of howto's on the subject if you google.

If you don't already have Mplayer there is a good howto in the Ubuntu Howto section of the forums.  You might want to read the whole thread & get the script with the latest mplayer & codec pack.

When you are done installing that, open up a terminal and type something like:

```
kieren@Mesh:~/Movies$ mencoder -ovc lavc Thailand_2003.mpeg -oac mp3lame -o Thailand_2003.avi
```

^ that's from a text file I saved from my diving holiday.  

You will need to to need to change to the directory the file is first, or to make things simple just have the file you want to convert in your  /home directory.  Change the first filename for you wmv filename, & the 2nd one (Thailand_2003.avi) to what ever you want the uotput file to be called.

There are also options to resize the video resolution:
```
kieren@ubuntu:~/Video $ mencoder Thailand_2003.avi -ovc lavc -lavcopts vcodec=mpeg4 -vop expand=220:180,scale=220:-2 -o Thailand_spv.avi -oac mp3lame
```

In this example I am downsizing the converted file to a resolution of 220x180 for playing on my mobile phone.

It's worth noting that it's actually bad form to resise to the resolution that I did becuase mpeg resolutions should be able to divide by 8 so 176x144 probably would have been better for my phone.

(the avi container file that is produced above contains mpeg4 for video & mp3 @ 128kbps for sound)[/QUOTE]
 I'll give that a try ixus.  Thanks.  I'm about at my wits end with multimedia in linux right now.  :P

---

