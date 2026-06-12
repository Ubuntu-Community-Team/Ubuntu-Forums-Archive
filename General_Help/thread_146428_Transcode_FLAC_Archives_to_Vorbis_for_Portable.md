---
title: "Transcode FLAC Archives to Vorbis for Portable?"
date: 2006-03-18
forum: General Help
---

### Post by dpaint4 on 2006-03-18
When I was still a Windows user, I archived my whole CD collection of a few thousand FLAC files. My friends thought I was crazy, and it took a long time, but I chose the format so that I'd have the freedom to move to another OS down the road.

The day, obviously is here, and I'd like to encode some of my FLACs to Vorbis for use on my portable.

But all the programs I can find in the repositories, and even online, seem geared towards encoding straight from disc to whatever you want. I like Grip a lot, as far as a ripping program is concerned.

I don't want to have to burn my FLAC files to audio cd and encode from that.

What programs do you guys use to transcode from one format to another?

FLAC is lossless, so don't give me the standard 'transcoding is evil' talk. :rolleyes:

---

### Post by firecat53 on 2006-03-18
Check the repositories for soundconverter.  Works great!

Scott

---

### Post by dpaint4 on 2006-03-18
[QUOTE=firecat53]Check the repositories for soundconverter.  Works great!

Scott[/QUOTE]

Thanks Scott. This is really stable and convenient, and gets the job done for now, but I'd prefer an application that would allow me to use my own binary encoders, like for instance, instead of the standard version of Vorbis that Gstreamer uses, I'd like to be using aoTuV's Beta4.51.

Not to be ungreatful. I'm totally impressed with how easy this app is. I would like something extendable though, in the same way that Grip allows me to point it to my own binarys and specify my own encoding switches.

So anyone got an answer for that?

---

### Post by dpaint4 on 2006-03-18
I'm bumping because it's a top need of mine.

Anyone know of a Transcode/Encode application that allows the use of stand-alone encoder binaries such that I could encode my FLAC archive to the latest aoTuV Vorbis without modifying Gstreamer or making other system-wide changes?

Grip allows what I'm talking about, but only encodes from disc.

---

### Post by steve.horsley on 2006-03-18
Enable the multiverse and universe repositories and then search synaptic for "transcide". There is a transcode package and a gtranscode front-end. I've never used them, so can't comment on quality etc.

---

### Post by bionnaki on 2006-03-18
I use crip for converting flac to ogg - it's a commandline app & works well.

---

### Post by dpaint4 on 2006-03-18
[QUOTE=steve.horsley]Enable the multiverse and universe repositories and then search synaptic for "transcide". There is a transcode package and a gtranscode front-end. I've never used them, so can't comment on quality etc.[/QUOTE]

I'm interested in trying this. Funny thing is I do have my universe and multiverse sources enabled, and a search for 'transcide' in Synaptic turns up nothing for me. Are you sure that's where it's coming from? Do you have other sources added as well that it might have come from?

---

### Post by dpaint4 on 2006-03-18
Did you mean 'Transcode'? That's only one letter off. I've already got that but was under the impression that it was only for (or taylored to) video.

---

### Post by bugmenot on 2006-03-19
I guess you're used to graphical apps -and prefer them- but oggenc (the vorbis binary) reads FLAC as input file. I do this all the time, because my FLAC collection doesn't fit onto my laptop anymore.
If you just need one directory of flacs, use:

```
oggenc -q6 *.flac
```

For a recursive conversion you'd have to come up with a simple loop (depending on your dir. structure). There's no real need for a sophisticated app because oggenc retrieves all tags from the flac files (even the replaygain which is usually a bit different after encoding).

BTW, aotuv binaries can be compiled with aoyumis patch applied to the Breezy source package. If you want to know how, tell. (The advantage is that aotuv is then used everywhere, including Gstreamer apps.)

---

### Post by dpaint4 on 2006-03-19
[QUOTE=bugmenot]I guess you're used to graphical apps -and prefer them- but oggenc (the vorbis binary) reads FLAC as input file. I do this all the time, because my FLAC collection doesn't fit onto my laptop anymore.
If you just need one directory of flacs, use:

```
oggenc -q6 *.flac
```

For a recursive conversion you'd have to come up with a simple loop (depending on your dir. structure). There's no real need for a sophisticated app because oggenc retrieves all tags from the flac files (even the replaygain which is usually a bit different after encoding).

BTW, aotuv binaries can be compiled with aoyumis patch applied to the Breezy source package. If you want to know how, tell. (The advantage is that aotuv is then used everywhere, including Gstreamer apps.)[/QUOTE]

It's not that I prefer graphical apps. I'm also excited about the command you just taught me, and plan to use it. The only thing is, I'd like to be able to use different encoders without modifying my system.

If you want the truth, I've already patched my installation with aoTuV, but that's not really the point. The point for me is flexibility so that I can use the latest aoTuV on a whim, and then Lancer, and then suddenly switch to some crazy version of Musepack, and Lame 3.98a. In each of those situations, I could assign the codec to be *the* codec that Gstreamer uses for that type of file, but I'd rather not be modifying my system for case-by-case scenarios like this.

The reason is that I like to cross test codecs and I like to stay ridiculously up to date as well.

Still. Thanks for letting me know I can use oggenc from the command line. That's pretty spif and beeing a n00b, I didn't know that.

---

### Post by bugmenot on 2006-03-19
[QUOTE=dpaint4]Still. Thanks for letting me know I can use oggenc from the command line.[/QUOTE]

I saw in your other thread that you use fb2k via wine. I don't think you'll find anything as powerful as foobar on linux for encoding and tagging, but what it does is basically just call these CLI encoders in the same way.

I actually also keep foobar ready for the occasional reencode (in vmware though) because stuff like images with cuesheet isn't supported anywhere.

---

