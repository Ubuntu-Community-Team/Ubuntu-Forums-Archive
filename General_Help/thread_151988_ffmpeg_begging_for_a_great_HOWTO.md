---
title: "ffmpeg: begging for a great HOWTO"
date: 2006-03-28
forum: General Help
---

### Post by dartmusic on 2006-03-28
Seriously...I have a bunch of ALAC (Apple Lossless)  files left over from when I was still using XP and iTunes and want to convert them to FLAC, but I canNOT seem to get ffmpeg to compile correctly.  

I've tried things suggested here as well as other sites found through our old pal Google, but they mostly pertain to video...not that that should really effect what *I'm* trying to achieve, BUT, all I want is to be able to convert these files.

I know that I could simply boot into XP and do this, but I want to a) learn how to do things in Linux, and b) I want to keep the XP install pristine for audio recording.  This is yet another thing I would love to try to do in Ubuntu, but there are no drivers for my audio hardware (RME Fireface800).

Any input would be supremely appreciated.

Thanks!

ps:  I've seen references made to an alac-decoder, but can't seem to find it!

---

### Post by Barrakketh on 2006-03-29
ffmpeg has the Apple Lossless decoder built in.  The input filetype is (normally) automatically detected, so you don't have to worry about specifying it (though there is an option to force the format).

This should do the trick:
```
ffmpeg -i input.alac -f wav - | lame --preset standard - out.mp3
```
The argument following i is the input file name, -f tells it to force the output to be a wav file (it automagically picks a few options based on the input file), and the lone hyphen represents standard output.  For lame, the lone hyphen represents standard input.  Normally the first hyphen is stdin, the second is stdout.  Anyway....

For ffmpeg, arguments that work on the input file come before the file name.  After the input arguments and file name are the arguments that work on the output file, then the output file name.

A pipe ("|") connects two programs that can read and write to/from stdin/stdout.  We're writing the decoded file (in wav format) to stdout, passing it through a pipe, and feeding it in to lame's stdin.  I just picked a convenient setting to use for lame -- if you're familiar with it's arguments you can tell it to encode your MP3s however you want.



By the way, you need to enable the universe repositories to install ffmpeg.  I'm using Dapper, so I'm going to tell you the hard way because I'm not sure whether our package manager (Adept) still works the same ;)

There's a line in the file /etc/apt/sources.list that contains the line you need to uncomment.  Open it with nano:
```
sudo nano -w /etc/apt/sources.list
```
or Kate:
```
kdesu kate /etc/apt/sources.list
```

Find the line that says:
```
deb http://us.archive.ubuntu.com/ubuntu breezy universe
```
And uncomment it (remove the # before it).  You might want to do the same for the restricted and multiverse repositories.

Now you should be able to run "sudo apt-get update && sudo apt-get install ffmpeg" to install ffmpeg.

If you decide that the command-line method of encoding them is a bit slow I'm sure one of us can find something a bit more convenient :)

---

### Post by dartmusic on 2006-03-29
Thanks for the reply.  Great info, but...I DO have ffmpeg installed from the universe repos, but I cannot play any ALAC files, nor can I transcode them.  So far I have only tried transcoding with SoundKonvertor, which gives me an error stating something along the lines of "no codec available to open the file."  The tracks show correct tags in whichever program I view them in, but no program can play them.

When I get home, I'll try the command line stuff above and report back.

Thanks again!

---

