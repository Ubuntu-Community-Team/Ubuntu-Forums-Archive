---
title: "Convert CDDA to MP3 or ogg."
date: 2006-04-16
forum: General Help
---

### Post by chris_andrew on 2006-04-16
Hi,

I would like to make a back-up of one of my CD's.  Is there a tool available that will convert the CDDA format to MP3, or perhaps .ogg?  I can do .wav, but the file size is huge.  I know I can use Konqueror to do this job, but if I install it, it relies upon dependencies from half of KDE!!

Many thanks,

Chris.

---

### Post by sYs^ on 2006-04-16
Hi,

I didn't try it before but I hope it'll help:

[https://wiki.ubuntu.com/CDRipping](https://wiki.ubuntu.com/CDRipping)

---

### Post by hentaidan on 2006-04-16
Sound juicer comes installed by default with gnome AFAIK?

---

### Post by sYs^ on 2006-04-16
Well, I think yes.
or at least it's in the main repos.

[http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=juicer&searchon=names&subword=1&version=all&release=all](http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=juicer&searchon=names&subword=1&version=all&release=all)

---

### Post by jazzmuzik on 2006-04-16
Here's a command line approach. Open up a terminal (Applications, Accessories, Terminal). Make sure you are on a mount that has about 700 meg of free space. Run "df -h" to check. Next insert the CD and run:

cdparanoia -wB -d/dev/cdrom

This will give you a bunch of wav files. Each represents one track on the cd. Then run:

for i in *.wav; do lame -b 192 $i `basename $i .wav`.mp3; done

Now you've got a bunch of mp3 files. Change the 192 to a higher or lower figure to get better or smaller mp3 files. That's it. You may want to tag the files (puts the artist, album, track info into the mp3 and can also rename the files) with easytag. So look how simple this three step process is:

1. rip
2. encode
3. tag

Note that you will need to install the cdparanoia, lame and easytag deb packages for this to work, but these steps are a one time thing:

apt-get install cdparanoia
apt-get install lame
apt-get install easytag

If something still doesn't work it's because a certain repository needs to be included and I'm not sure which one that is. Maybe somebody can remind me and I'll edit this message. ;)

---

### Post by jazzmuzik on 2006-04-16
[QUOTE=chris_andrew]I would like to make a back-up of one of my CD's.  Is there a tool available that will convert the CDDA format to MP3, or perhaps .ogg?  I can do .wav, but the file size is huge.  I know I can use Konqueror to do this job, but if I install it, it relies upon dependencies from half of KDE!![/QUOTE]

Oops. I realize your question was even simpler since the files are already in wav format. First, install lame:

apt-get install lame

Then run this in the directory of your wav files:

for i in *.wav; do lame -b 192 $i `basename $i .wav`.mp3; done

Then tag the files with easytag and you're done.

---

### Post by ncappel1 on 2006-04-16
just a note, mp3 is a proprietary audio format, whereas ogg is open!
Not that i'm trying to sway your decision or anything. ;)

---

### Post by jazzmuzik on 2006-04-16
[QUOTE=ncappel1]just a note, mp3 is a proprietary audio format, whereas ogg is open!
Not that i'm trying to sway your decision or anything. ;)[/QUOTE]

If open formats are the goal, I think it's better to bypass ogg and compress to flac.

---

### Post by ncappel1 on 2006-04-16
>  If open formats are the goal, I think it's better to bypass ogg and compress to flac.

As much as I hate to admit it, size **does** matter (no pun intended?). flac file sizes are bigger than ogg. a 3:30 long file in ogg is approx. 3.4 mb, in flac the same track is 9.8 mb, the difference is really apparent when the music library gets to be in the gigabytes range. For people with small drives it can get to be a problem pretty fast!

---

### Post by jazzmuzik on 2006-04-17
Flac files are bigger because they are lossless, unlike ogg or mp3. Mp3 and ogg compress music by throwing away data that is irretrievable. That's why mp3 and ogg are smaller: they are missing a lot of information, subtleties like overtones and reverb for example. If you uncompress an mp3 you never get back the original data. OTOH, if you uncompress a flac file you do get back the original data as if you just ripped it from the cd. Flac, being lossless, gives the highest quality possible.

Hard disk space is an issue though. But it always has been. And we continue to get bigger drives.

---

### Post by chris_andrew on 2006-04-24
Thanks, all.

Originally, I wanted to encode in MP3, because I needed to be able to play on standard CD players.  Ogg is my preferred format , as it is free.  Is flac free, too?  If so, are there flac players for other OS'sd, too, eg Windoze?  I guess I can't play a flac in a regular CD player (eg car)?

Cheers,

Chris.

---

### Post by hentaidan on 2006-04-24
FLAC = Free Lossless Audio Codec :)

Not wanting to sound rude but there is a lot of information on their website: [http://flac.sourceforge.net/]("http://flac.sourceforge.net/") :rolleyes:

---

### Post by ncappel1 on 2006-04-24
> are there flac players for other OS'sd, too, eg Windoze

I believe winamp will play flac files, in addition to oggs too, and a variety of other audio formats.

---

### Post by chris_andrew on 2006-05-04
Hentaidan,

Thanks for your reply.  I checked out the FLAC site, before I posted.  I found the site to be poorly laid out, so thought I would ask a straight question, in order to receive a straight answer.  <rollseyes>Hope this doesn't sound rude!</rollseyes>

Thanks,

Chris.

---

