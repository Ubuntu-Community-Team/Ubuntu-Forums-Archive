---
title: "Is  there any mkv converters for ubuntu?"
date: 2010-02-17
forum: General Help
---

### Post by colobix on 2010-02-17
Hey
I need a tool or a script or something that can help me convert mkv files into vob or avi format. Can anyone help me here please?

---

### Post by VertexPusher on 2010-02-17
Avidemux.

---

### Post by colobix on 2010-02-17
Thanks but it Avidemux messes with the frames plus it can't compress the videos down to divx avi.
Any other solutions?

---

### Post by mimor on 2010-02-17
I would like to know this as well.

---

### Post by colobix on 2010-02-17
Well. i found a few programs that works together with Wine, but, 
for 1> I think an OS should have all the software I need withut any help from a windows software, and I think its wrong talking about windows software you can use in linux. It's like convincing people to think that windows is a better alternative.
I don't say Wine is wrong but shouldn't be mentioned too much in a linux forum.
And 2>, the 2 programs I found didn't do the job as good as they should.

ANyway, please help me out folks.
I really need a software or a script o do this

---

### Post by VertexPusher on 2010-02-18
> **colobix said:**
> Avidemux messes with the frames
Nonsense. Avidemux is the most frame-accurate cutting tool you will find, because that's one of its main goals. And if you don't cut but recompress, you need not worry about frame accuracy anyway.

> it can't compress the videos down to divx avi.
Of course it can. If you don't know that Xvid and DivX are basically the same thing (i.e. MPEG-4 ASP codecs), you must have been living under a rock for the past 9 years.

> Any other solutions?
Yes, but they are less idiot-friendly than Avidemux. So you might want to stick with that and maybe invest two or three minutes reading the manual to get a clue. Good luck.

---

### Post by colobix on 2010-02-18
> **VertexPusher said:**
>  Of course it can. If you don't know that Xvid and DivX are basically the same thing (i.e. MPEG-4 ASP codecs), you must have been living under a rock for the past 9 years.
Or I am not a pc geek.
Look it doesnt matter to me if its xvid or divx or xdiv or whatever it is.
I just need a good program that can convert my videos without freezing and at the same time compress it down a bit like divx does.

---

### Post by whitethorn on 2010-02-18
You might want to try using ffmpeg or mencoder.  Here's a link to installing ffmpeg with all the different encoding options

[http://ubuntuforums.org/showthread.php?t=786095](http://ubuntuforums.org/showthread.php?t=786095)

As for mencoder it usually comes with mplayer, I'm not on my ubuntu machine atm I think all you need is

```
sudo apt-get install mencoder
```

To figure out how to use the programs, just give the man pages a small read.

```
man ffmpeg
```

---

### Post by VertexPusher on 2010-02-18
> **colobix said:**
> compress it down a bit like divx does.
The MKV files you are trying to convert have already been compressed using [a much more efficient codec](http://en.wikipedia.org/wiki/H.264/MPEG-4_AVC). DivX/Xvid cannot make them smaller without severely degrading their picture quality.

---

### Post by LintonHanes on 2010-02-18
so i googled: mencoder mkv to avi
and the fourth down was this [http://tuxarena.blogspot.com/2009/07/tip-of-day-convert-mkv-to-avi-using.html](http://tuxarena.blogspot.com/2009/07/tip-of-day-convert-mkv-to-avi-using.html)

so i googled a bit more: it looks like mkvtoolnix is what you're after: it's in synaptic -

looks like I'll be using this too maybe

---

### Post by colobix on 2010-02-18
> **LintonHanes said:**
> so i googled: mencoder mkv to avi
and the fourth down was this [http://tuxarena.blogspot.com/2009/07/tip-of-day-convert-mkv-to-avi-using.html](http://tuxarena.blogspot.com/2009/07/tip-of-day-convert-mkv-to-avi-using.html)

so i googled a bit more: it looks like mkvtoolnix is what you're after: it's in synaptic -

looks like I'll be using this too maybe

Thank you VERY MUCH :)
I must take a look at the toolnix thing.
It had some great tools but I couldnt find a converter tool.
But I will look into it.
I think i'll do some more research on this and try to find a solution.

---

### Post by colobix on 2010-02-18
Ok so I have installed the Mencoder.
Is there a command I can use to convert a whole folder full of mkv files into avi files?

---

### Post by VertexPusher on 2010-02-18
That tip of the day is total nonsense, clearly a case of the blonde trying to teach the blind. It basically says that if you convert _any_ MKV file to a 1800 kb/s Xvid AVI, the result will be 35% of the original size.

It doesn't take a degree in mathematics to realize that this statement only applies if the input file has a bitrate of ~5000 kb/s.

As to your question: Yes, it's possible to batch-encode a folder of MKV files with MEncoder, but again, it's easier to do with a job list in Avidemux unless you are a shell script wizard, which I assume you are not.

---

### Post by FakeOutdoorsman on 2010-02-19
> **VertexPusher said:**
> As to your question: Yes, it's possible to batch-encode a folder of MKV files with MEncoder, but again, it's easier to do with a job list in Avidemux unless you are a shell script wizard, which I assume you are not.

Here's an excellent use for the *find* command.  Luckily there is a decent guide that shows some of the basics of the powerful utility.  The last two examples can be used as a basis for a MEncoder batch command:

[Linux Basics: A gentle introduction to 'find'](http://ubuntuforums.org/showthread.php?t=1128937)

---

### Post by cong06 on 2010-02-19
> **VertexPusher said:**
> As to your question: Yes, it's possible to batch-encode a folder of MKV files with MEncoder, but again, it's easier to do with a job list in Avidemux unless you are a shell script wizard, which I assume you are not.

hehe. You really don't like the idea of him using anything OTHER then Avidemux... do you?
Actually it doesn't take much learning to become a "shell script wizard" and there are plenty of people around who'd help.

Just for the sake of it, I figure I might as well post the script that I was (trying) to get working:

```

find /folder -iname "*.flv" -or -iname "*.avi" -or -iname "*.mp4" -exec mencoder {} -oac mp3lame -ovc lavc -o {}.out \;

```
I think that the problem with it (I don't remember the exact error) was that it had two sets of '{}'

So I replaced it with an uglier version:
```

for i in `find find /folder -iname "*.flv" -or -iname "*.avi" -or -iname "*.mp4"`; do
    mencoder $i -oac mp3lame -ovc lavc -o $i.out
done

```

If the folder only contains avi files and other formats that mencoder can encode, then you can just do:
```

for i in `ls /folder`; do
...

```
Of course this wouldn't be recursive though. It'd just go down one folder.

With mencoder, you might have to run:
```

mencoder -oac help
mencoder -ovc help

```
to see available audio and video codecs, respectively.

Finally, the '-o' option is for the output file.

---

### Post by VertexPusher on 2010-02-19
> **cong06 said:**
> hehe. You really don't like the idea of him using anything OTHER then Avidemux... do you?
I don't think he's capable of using anything else. It's obvious that he's one of those guys looking for one-click instant gratification. If you tell him *"Look, it's easy! All you need is this script that I'll write for you"*, the next thing he'll do is tell his friends that all the stereotypes about Linux being command line driven are true.

Video encoding is a complex topic, even on Windows. This guy is trying to convert H.264 MKVs to DivX AVIs because he thinks that will make them smaller. But the truth is: It won't, because there is currently no codec more efficient than H.264.

How do I know that his MKVs contain H.264 video? When he loaded them into Avidemux, he saw the frame accuracy warning. This warning only appears with H.264 videos.

---

### Post by cong06 on 2010-02-19
> **VertexPusher said:**
> Video encoding is a complex topic, even on Windows. This guy is trying to convert H.264 MKVs to DivX AVIs because he thinks that will make them smaller. But the truth is: It won't, because there is currently no codec more efficient than H.264.
Good point.
I guess even if there was, it wouldn't save the amount of space he wants. I'm not entirely familiar with the 'code' required for mencoder to resize the video. Granted it's probably right there in the man page.

I'm terrible at reading people, so I refuse to make that kind of judgment about the OP. In any case if he wants to go down the path of command lines, more power to him. We'll be here to help.

---

### Post by colobix on 2010-02-19
Well, I could use other things then Avidemux, but Avidemux is the quickest way to do this I guess. But it still decompresses the video alot. That's the problem.
I am looking for a quick way to do this coz I don't want this to be an all day job.
But the problem with Avidemux is that I have to use safe mode but the safe mode happens to skip many frames.

---

### Post by colobix on 2010-02-19
OK so in Avidemux, how do I add a folder with mkv files to be converted to avi files. adding one and one file after eachother takes forever.
I tried the joblist thing but when I click on add to joblist nothing happens. so how?

---

### Post by colobix on 2010-02-20
This is so frustrating.
I've been trying forever now but I can't find a way to convert mkv into avi without decompressing the video format to double size.
And nether a program to convert a whole folder of mkv files at the same time.
Is there really no solution out there?
Because, in windows there are many programs for things like this.

---

### Post by aarons6 on 2010-02-20
i too am having a problem with this.. i am trying to make a dvd from mkv files..

if i put the mkv files right into devede the audio loses sync.
here is the process i am using but i would like to find a way to semi automate it.
first i have to use the mkvtool to make a new mkv file with no chapters, no subtitles and only one lang, english.

then i have to use the mkv2avi.kmdr program to make the avi file.. i just leave it default, dvix and 3000..

then then can be put into devede and converted into a dvd with no audio issues..

i know somehow the mkv2avi uses mencoder, but every command line i tried has audio issues.. im not sure how he made it work.. 

i made a script that would convert a whole dir into avi but i cant make the mencoder work.. 
it drops a ton of frames and leaves the audio faster then the video..

---

### Post by aarons6 on 2010-02-20
i think i got it colobix, try this

#!/bin/sh
for f in *.mkv;
do
echo "Processing $f" 
mencoder -mc 0 -noskip -skiplimit 1 "$f" -ffourcc xvid -ovc lavc \
-lavcopts vcodec=mpeg4:vbitrate=3000:vpass=1 -oac mp3lame \
 -o "${f%.mkv}.avi"
done

it will convert all the mkv files in a folder to avi.
they look as good but just a tad larger..

be sure to strip the chapters, subtitles and extra languages first.. i use the mkvtoolsnix program.

---

