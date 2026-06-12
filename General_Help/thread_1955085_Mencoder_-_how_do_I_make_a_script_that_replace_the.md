---
title: "Mencoder - how do I make a script that replace the implements filenames automatically"
date: 2012-04-09
forum: General Help
---

### Post by AlexOnVinyl on 2012-04-09
So I've been doing some studying on Mencoder, it is actually a really good useful program.

So I made a command for hardcoding subs, but the only issue is I want to make this a script that can be used in Nautilus and will automatically fill in the input file names and create an output file name based on the input file name.

Here's what I have so far:

```
mencoder movie.avi -sub moviesubs.srt -subfont-text-scale 3.3 -subpos 96 -o /dev/null -oac copy -ovc lavc -lavcopts vcodec=mpeg4:vpass=1 -o movieWithSubs.avi

```

Can someone add some tweaks to it for me? thanks in return and its much appreciated.

---

### Post by Paddy Landau on 2012-04-09
Are you saying that you want to be able to right-click a file in Nautilus and call the script?

If so, open Nautilus. Go to File > Scripts > Open Scripts Folder > Show more details. (If you don't see that menu item, you need to place a script (any script) in [FONT=Lucida Console]~/.gnome2/nautilus-scripts[/FONT] first).

---

### Post by Vaphell on 2012-04-09
install nautilus-actions that allows you to create custom entries and fine tune their properties (files or dirs, filetypes, single or multiple selection)

as for script part

assuming that your script gets movie file as a parameter - name will be stored in $1

```
#!/bin/bash

mencoder "$1" -sub moviesubs.srt -subfont-text-scale 3.3 -subpos 96 -o /dev/null -oac copy -ovc lavc -lavcopts vcodec=mpeg4:vpass=1 -o "${1%.*}WithSubs.${1##*.}"
```
there is some voodoo just in case you want to preserve file extension, but not necessarily hardcoded avi
${1%.*} = everything from $1 except shortest possible '.<anything>' on the right -> extension is out, name stays
${1##*.} = everything from $1 except longest possible '<anything>.' on the left -> whole name is out, extension stays

i don't know if the subs file should be dependent on movie name so i left it untouched

---

### Post by AlexOnVinyl on 2012-04-09
> **Paddy Landau said:**
> Are you saying that you want to be able to right-click a file in Nautilus and call the script?

If so, open Nautilus. Go to File > Scripts > Open Scripts Folder > Show more details. (If you don't see that menu item, you need to place a script (any script) in [FONT=Lucida Console]~/.gnome2/nautilus-scripts[/FONT] first).

Yes, I've already completed that, I understand how to install scripts to work with Nautilus. but thank you for the information :)

> **Vaphell said:**
> install nautilus-actions that allows you to create custom entries and fine tune their properties (files or dirs, filetypes, single or multiple selection)

as for script part

assuming that your script gets movie file as a parameter - name will be stored in $1

```
#!/bin/bash

mencoder "$1" -sub moviesubs.srt -subfont-text-scale 3.3 -subpos 96 -o /dev/null -oac copy -ovc lavc -lavcopts vcodec=mpeg4:vpass=1 -o "${1%.*}WithSubs.${1##*.}"
```
there is some voodoo just in case you want to preserve file extension, but not necessarily hardcoded avi
${1%.*} = everything from $1 except shortest possible '.<anything>' on the right -> extension is out, name stays
${1##*.} = everything from $1 except longest possible '<anything>.' on the left -> whole name is out, extension stays

i don't know if the subs file should be dependent on movie name so i left it untouched

Thank you for explaining how the '$1' parameter works, that's what's been puzzling me.  I've been trying to figure out how I can create a script that will work universally for any movie file I want to add subs to without having to go in and edit the code each time.  

Now as far as the rest of the code, was I on the right track or no? because this is the first time I've really went and used the CLI for Mencoder.



----UPDATE-----

Also, is there a way I could possibly edit the bash script to include a sort of progress bar, if you will? like say a GUI progress bar to show how much/close it is to being done?

---

### Post by AlexOnVinyl on 2012-04-09
Bump

---

### Post by Vaphell on 2012-04-10
if you need gui for your script, look at zenity with --progress parameter. Unfortunately i have no experience with it. I'd just run the script from terminal without bothering with useless bling ;-)

---

### Post by AlexOnVinyl on 2012-04-11
> **Vaphell said:**
> if you need gui for your script, look at zenity with --progress parameter. Unfortunately i have no experience with it. I'd just run the script from terminal without bothering with useless bling ;-)
for some reason I'm running into the issue where the subbed video has lower quality than the original video.

I'll show you: 

Original: [IMG]http://i.imgur.com/zmVcP.png[/IMG]

Sub encoded: [IMG]http://i.imgur.com/xfRIB.png[/IMG]

is there something wrong with the code?

---

### Post by Vaphell on 2012-04-11
no idea, i think you should ask in the Multimedia & Video subforum

---

### Post by SeijiSensei on 2012-04-11
It's probably smaller because you're using a more efficient codec to store the re-encoded file.  That would be true if, for instance, the original is in MPEG2, and you're encoding to MPEG4. If you want an exact copy, use "-ovc copy".

---

### Post by AlexOnVinyl on 2012-04-12
> **SeijiSensei said:**
> It's probably smaller because you're using a more efficient codec to store the re-encoded file.  That would be true if, for instance, the original is in MPEG2, and you're encoding to MPEG4. If you want an exact copy, use "-ovc copy".

I'm going to give that a shot right now - thanks, I'll let you know what I get.

Do I replace the ```
-lavcopts vcodec=mpeg4
``` line as well? with a simple ```
-ovc copy
```?

---

### Post by SeijiSensei on 2012-04-12
Yes, if you're not using lavc then there are no lavcopts.

That said, I'm not advocating preserving ancient MPEG2 encodings. MPEG2 dates back to the late 1990's and is pretty much only used on traditional DVDs and by some terrestrial HD broadcasters.  MPEG4 is considerably more efficient, as your size comparison indicates, and I doubt you could see the difference in video quality on-screen.

These days the codec of choice is H.264, a variant of MPEG4, which achieves even better compression at equivalent quality.  Most streaming sites like YouTube are encoded with H.264 as are most unauthorized video rips out there on the Internet. The drawback of using H.264 is its higher computational demands for decoding.  Older hardware with slower CPUs generally can't decode HD H.264 encodes in real time.  Modern video cards often include hardware H.264 decoders these days, in particular NVIDIA cards which offer the VDPAU interface.  You'll see postings here from time to time complaining that they can't play modern video files on their computers.  Usually they're trying to play a 720p or 1080p H.264 encode on computers whose CPUs aren't up to the task. 

I suggest you watch a few minutes of the two files you mentioned above and see if you can detect any obvious quality differences.  If not, then I'd stick to MPEG4 or use H.264.  [Handbrake]("https://launchpad.net/~stebbins/+archive/handbrake-releases") is a GUI-based DVD ripper and video converter that makes creating H.264 encodes pretty painless.  It also handles things like multiple audio and subtitle tracks with ease.

---

### Post by imachavel on 2012-04-12
when I open nautilus and go to file I don't see scripts, would gksu nautilus show me this menu? But all that would change is permissions, unless that changes what you are allowed to see with the interface. I'm not sure.. gksu nautilus seems it would get you deeper in there, wondering why scripts isn't in file. Let me re read this to see if OP got what he needed solved. I'm not great at writing scripts though, just using higher level code that utilizes already written scripts, I don't know much about writing them but want to get into that

---

### Post by imachavel on 2012-04-12
> **SeijiSensei said:**
> Yes, if you're not using lavc then there are no lavcopts.

That said, I'm not advocating preserving ancient MPEG2 encodings. MPEG2 dates back to the late 1990's and is pretty much only used on traditional DVDs and by some terrestrial HD broadcasters.  MPEG4 is considerably more efficient, as your size comparison indicates, and I doubt you could see the difference in video quality on-screen.

These days the codec of choice is H.264, a variant of MPEG4, which achieves even better compression at equivalent quality.  Most streaming sites like YouTube are encoded with H.264 as are most unauthorized video rips out there on the Internet. The drawback of using H.264 is its higher computational demands for decoding.  Older hardware with slower CPUs generally can't decode HD H.264 encodes in real time.  Modern video cards often include hardware H.264 decoders these days, in particular NVIDIA cards which offer the VDPAU interface.  You'll see postings here from time to time complaining that they can't play modern video files on their computers.  Usually they're trying to play a 720p or 1080p H.264 encode on computers whose CPUs aren't up to the task. 

I suggest you watch a few minutes of the two files you mentioned above and see if you can detect any obvious quality differences.  If not, then I'd stick to MPEG4 or use H.264.  [Handbrake]("https://launchpad.net/%7Estebbins/+archive/handbrake-releases") is a GUI-based DVD ripper and video converter that makes creating H.264 encodes pretty painless.  It also handles things like multiple audio and subtitle tracks with ease.

I was looking into this a bit:

[https://help.ubuntu.com/community/MEncoder](https://help.ubuntu.com/community/MEncoder)

adequately do the same task to convert and export a file into this format?(as you said):

[http://en.wikipedia.org/wiki/H.264/MPEG-4_AVC](http://en.wikipedia.org/wiki/H.264/MPEG-4_AVC)

---

### Post by SeijiSensei on 2012-04-12
I don't often recommend GUI-based programs for tasks that I can accomplish easily from the command prompt or with a bash script.  That said, I think Handbrake is still the better option.  You can queue up multiple conversions, then have them execute sequentially.

That said, a simple script to iterate over all the .AVI files in a directory and add the subs would look something like this:

```

#!/bin/bash

mkdir -p subs

for f in *.avi
do
   MOVIE=$(basename $f)
   mencoder $MOVIE.avi -sub $MOVIE.srt -subfont-text-scale 3.3 -subpos 96  -oac copy -ovc lavc -lavcopts vcodec=mpeg4:vpass=1 -o subs/$MOVIE.avi
done


```

This script iterates overall all .avi files in the current directory, creates a "subs" directory below that, and puts the re-encoded files there.  It also assumes that the SRT file for "movie.avi" is called "movie.srt".  Massage as needed.

OP, I lost track of the original intent here.  You cannot use "-ovc copy" if you want to add hard subtitles.  You do need to re-encode the video so the subtitles can be "burned in."  If you want to add soft subtitles like .ssa or .()ss (damn content filter), you'd need to put the output into a different container that supports subtitle streams like MP4 or, better, Matroska (.MKV).  This would be easier to accomplish with Handbrake.

For a quick overview of encoding strategies with mencoder, I recommend this [howto from Gentoo]("http://en.gentoo-wiki.com/wiki/Mencoder"), and the complete manual from the mplayer folks [here](http://www.mplayerhq.hu/DOCS/HTML/en/encoding-guide.html).

---

### Post by imachavel on 2012-04-12
right...

!/bin/bash
/bin/bashlis
bash: /bin/bashlis: No such file or directory
danel@danel-Dimension-4700:~$ 
danel@danel-Dimension-4700:~$ mkdir -p subs
danel@danel-Dimension-4700:~$ 
danel@danel-Dimension-4700:~$ for f in *.avi
> do
>    MOVIE=$(basename $f)
>    mencoder $MOVIE.avi -sub $MOVIE.srt -subfont-text-scale 3.3 -subpos 96  -oac copy -ovc lavc -lavcopts vcodec=mpeg4:vpass=1 -o subs/$MOVIE.avi
> done

now OP will have to be familiar with this prompt? Interesting I wonder what that converted if it didn't cd into bin then bash correctly. Good advice though lot's to learn


well never mind that last part, I got my answer:

mencoder: Symbol `ff_codec_bmp_tags' has different size in shared object, consider re-linking
MEncoder SVN-r33713-4.6.1 (C) 2000-2011 MPlayer Team
File not found: '*.avi.avi'
Failed to open *.avi.avi.
Cannot open file/device.

Exiting...

---

### Post by Vaphell on 2012-04-12
basename sucks and is imo borderline useless, builtin parameter expansion all the way baby

```
$ for f in movie1.avi movie2.mp4 music1.mp3; do echo "${f%.*} /// ${f##*.}"; done
movie1 /// avi
movie2 /// mp4
music1 /// mp3
```

---

### Post by AlexOnVinyl on 2012-04-13
> **Vaphell said:**
> basename sucks and is imo borderline useless, builtin parameter expansion all the way baby

```
$ for f in movie1.avi movie2.mp4 music1.mp3; do echo "${f%.*} /// ${f##*.}"; done
movie1 /// avi
movie2 /// mp4
music1 /// mp3
```

> **SeijiSensei said:**
> Yes, if you're not using lavc then there are no lavcopts.

That said, I'm not advocating preserving ancient MPEG2 encodings. MPEG2 dates back to the late 1990's and is pretty much only used on traditional DVDs and by some terrestrial HD broadcasters.  MPEG4 is considerably more efficient, as your size comparison indicates, and I doubt you could see the difference in video quality on-screen.

These days the codec of choice is H.264, a variant of MPEG4, which achieves even better compression at equivalent quality.  Most streaming sites like YouTube are encoded with H.264 as are most unauthorized video rips out there on the Internet. The drawback of using H.264 is its higher computational demands for decoding.  Older hardware with slower CPUs generally can't decode HD H.264 encodes in real time.  Modern video cards often include hardware H.264 decoders these days, in particular NVIDIA cards which offer the VDPAU interface.  You'll see postings here from time to time complaining that they can't play modern video files on their computers.  Usually they're trying to play a 720p or 1080p H.264 encode on computers whose CPUs aren't up to the task. 

I suggest you watch a few minutes of the two files you mentioned above and see if you can detect any obvious quality differences.  If not, then I'd stick to MPEG4 or use H.264.  [Handbrake]("https://launchpad.net/~stebbins/+archive/handbrake-releases") is a GUI-based DVD ripper and video converter that makes creating H.264 encodes pretty painless.  It also handles things like multiple audio and subtitle tracks with ease.
I'm not new to Handbrake, I just switched over to Ubuntu in August and ever since then I had to make a huge change in how I understood the way cli ties into the system as compared to simple point and click gui - I'm satisfied with my experience in Linux so far, and am much more educated at how the CLI works than I ever was - Handbrake was great, still is to an extent - and back on Windows - when I was using it, I used Handbrake, DvdDecrypter, Slysoft, and then also GordianKnot - so switching to more CLI based programs is a learning experience and I've found does a better job than a fancy GUI - and faster as well, or perhaps thats because it's linux.

[B]The only thing that I'm unsure of is how change the video codecs I use to encode the videos and incorporate them into common video containers - eg: Using MPEG4 and VBR AAC audio in an .avi container.  I know .avi is outdated due to the inventions of .mkv and .mp4 with the H.264 codecs but a lot of multi-media consoles, eg: the Playstation 3 cannot read an .mkv file unless streamed through a media server, where in which it would be encoding in real-time as streaming, or you're running a CFW that allows the format to be ran.

and at this point in time, I cannot afford a Boxee media box. :([/B]

---

### Post by SeijiSensei on 2012-04-13
Your best bet for creating files for the AVI container is to use XviD and MP3.  Take a look at that Gentoo howto I linked to above for details on the options needed to do this in mencoder.  You won't be able to include soft subs in an AVI container though.  You'll have to burn them into the image during re-encoding.

The Playstation 3 plays .mp4 files with MPEG4 and AAC.  Sony, like many media companies, ignores the Matroska container, despite its clear superiority over competing formats, probably because they see it as the preferred choice of those bloody pirates.  Not to mention that it wasn't developed by a cartel of media companies the way most codecs and containers have been.

---

