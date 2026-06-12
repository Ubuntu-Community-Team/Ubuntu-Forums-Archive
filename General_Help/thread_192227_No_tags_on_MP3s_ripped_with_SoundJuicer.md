---
title: "No tags on MP3s ripped with SoundJuicer"
date: 2006-06-08
forum: General Help
---

### Post by Farthing-or-less on 2006-06-08
MP3s ripped and encoded by SoundJuicer (Dapper) don't have MP3 tags - well, just the name and title. If i look at the files in Easytag, for example, I find nothing. Tags appear for other formats. Any fixes?

---

### Post by soze on 2006-06-08
[QUOTE=Farthing-or-less]MP3s ripped and encoded by SoundJuicer (Dapper) don't have MP3 tags - well, just the name and title. If i look at the files in Easytag, for example, I find nothing. Tags appear for other formats. Any fixes?[/QUOTE]

They sorta-kinda do.
What it appears that SoundJuicer does is put a V1 id3 tag (with good data) in the file, and then adds a *blank * V2 tag.

Lot's of programs will use the V2 tag if it's there, so you are seeing what looks like no tagging at all.

You can either:
1. Strip off the V2 tags
2. Copy the V1 tag data to the V2 tag (what I do).

I'm kind of hoping they fix this soon, since it's a bit of a pain.

---

### Post by grendelkhan on 2006-06-08
I just ripped a couple of songs for a mix cd the other day and I noticed they looked odd in Serpentine, but now that I'm checking them you're absolutely right.

What gives?

---

### Post by eyesonly on 2006-06-09
Yep I have the same problem.  Still searching for a ripper that do both compression and add a tag

---

### Post by yopnono on 2006-06-10
Give banshee a try

---

### Post by eyesonly on 2006-06-11
banshee doesn't work either

---

### Post by Max Roswell on 2006-06-19
I'm having the same problem with Sound Juicer and Banshee; anyone find a solution yet?  Or can someone recommend yet another ripper/encoder?  I just ripped a bunch of new CDs, and my MP3 player can't do anything unless there are ID3v1 tags!

---

### Post by roberto73 on 2006-06-23
add  **id3v2mux** to your Gstreamerpipeline!
see [https://help.ubuntu.com/community/CDRipping]("https://help.ubuntu.com/community/CDRipping")
my tags are fine now... :cool:

---

### Post by dpm on 2006-06-23
[quote=roberto73]add  **id3v2mux** to your Gstreamerpipeline!
see [https://help.ubuntu.com/community/CDRipping]("https://help.ubuntu.com/community/CDRipping")
my tags are fine now... :cool:[/quote] 
Err, this does not seem to work in Soundjuicer...

I had seen that link some time ago and even having

```
audio/x-raw-int,rate=44100,channels=2 ! lame name=enc bitrate=128 ! id3v2mux
``` 
as a pipeline for my mp3 encoding profile, the tags are not there. Neither Beep Media Player nor EasyTag can find any tags in songs encoded from SoundJuicer with this profile.

If SoundJuicer writes only ID3v1 tags as it apparently does, why the hell do programs not fall back to using the ID3v1 tags if they are present? ](*,) It's not that ID3 tags were invented yesterday...

Cheers.

---

### Post by roberto73 on 2006-06-23
:oops: shame on me :( 
I didn't check carefull enough!
The tracks I ripped look good using rhythmbox and amarok! Even iTunes can read out all the informations correctly.

> If SoundJuicer writes only ID3v1 tags as it apparently does, why the hell do programs not fall back to using the ID3v1 tags if they are present?  It's not that ID3 tags were invented yesterday...

I don't know if soundJuicer really writes ID3v1... Using audio tag tool or easytag the tracks ripped with soundjuicer seem not to have any ID3tags at all!

Cheers

---

### Post by doclivingston on 2006-06-25
[QUOTE=roberto73]I don't know if soundJuicer really writes ID3v1... Using audio tag tool or easytag the tracks ripped with soundjuicer seem not to have any ID3tags at all![/QUOTE]

It's quite possibly a ID3 version problem: GStreamer-based applications write tags in ID3 version 2.4 format, and many other application can't read 2.4, only 2.3.

---

### Post by Patsoe on 2006-06-25
For an old-school ripper/encoder frontend: I'm quite fond of "jack", which I discovered just yesterday. It's console based, but has all the right features as far as I'm concerned...
> Jack  transforms your audio-CDs to FLAC, MP3 or Ogg Vorbis files. It uses several helper programs in order to achieve things like ripping, encoding and ID3-tagging. Ripping is either done via cdparanoia (in which case the ripping status is displayed by Jack as well) or cdda2wav. Jack works with several encoders, namely oggenc, flac, lame, gogo, bladeenc, l3enc, mp3enc and xing. Any time during operation (and even when everything is finished and the original CD lost) you can let Jack look up the track names at freedb.org and rename the tracks accordingly. ID3-tagging of MP3s (or insertion of equivalent comment fields in Ogg Vorbis files) is performed as well.
You'll find that it's quite a bit slower than Soundjuicer - partly because the ripping is in a secure mode (which is good), and partly because it can't always put the wave stream in a direct pipe to the encoder (it may do so for lame, but oggenc doesn't support it), so there's a lot of disk writing going on...

Oh and it's in the universe repository...

---

### Post by doclivingston on 2006-06-25
> partly because it can't always put the wave stream in a direct pipe to the encoder (it may do so for lame, but oggenc doesn't support it), so there's a lot of disk writing going on...

That sounds odd, as oggenc can read from stdin is '-' is passed as the file name (same as most programs).

---

### Post by Patsoe on 2006-06-25
[QUOTE=doclivingston]That sounds odd, as oggenc can read from stdin is '-' is passed as the file name (same as most programs).[/QUOTE]

That's what I was thinking too, but jack refuses to work with oggenc if I set the switch --otf=true ("on the fly"), saying that oggenc can't do it. Maybe that was true in 2004 (when jack was last worked on I think)?

---

### Post by aysiu on 2006-06-25
Goobox may be worth a shot.

Or, if you don't mind KDE libraries, KAudioCreator isn't too shabby.

---

### Post by dpm on 2006-06-26
[quote=doclivingston]It's quite possibly a ID3 version problem: GStreamer-based applications write tags in ID3 version 2.4 format, and many other application can't read 2.4, only 2.3.[/quote] 
I think that's the key. You were spot on on your observation. Just to complement the information, an extract of the id3v2mux documentation
> 
id3v2mux — Adds an ID3v2 header to the beginning of MP3 files using taglib 

This element adds ID3v2 tags to the beginning of a stream using the **taglib** library. More precisely, the _tags written are ID3 version 2.4.0 tags (which means in practice that some hardware players or outdated programs might not be able to read them properly_). 
To recap, after some investigation:

1. **SoundJuicer,** when used with the following gstreamer pipeline
```
audio/x-raw-int,rate=44100,channels=2 ! lame name=enc bitrate=128 ! id3v2mux
``` is encoding a song with **lame** + the **id3v2mux** gstreamer plugin through **gstreamer.** The effect is that the song is correctly encoded and an **ID3 v2.4** tag is added. 

The **id3v2mux** plugin uses the **taglib** library for actually writing the tag.

2. The **ID3 v2.4** tag is relatively new and just a few players can display it. Among other things, an ID3 v2.4 tag supports Unicode/UTF-8, something that previous versions did not could not handle. Since the **taglib** library supports ID3 v2.4, players that make use of this library (**juk**, **amarok**, **streamtuner**, amongst others) for displaying tag information are the only ones which will actually display the tag. Players that make use of the **libid3tag** (e.g. **Rhythmbox**) can also manipulate ID3 v2.4 tags.

3. For those of you who want to keep using SoundJuicer as a ripping tool you can either use players which support ID3v2.4 tags (**juk**, **amarok**, **Rhythmbox**, **Listen**, **muine**, **banshee**, etc.) or add ID3v1 tags to your songs by copying the ID3v2.4 information.

Note: AFAIK there are 3 main projects (libraries) for reading/writing ID3 tags. Namely:

[SIZE=4]_**id3lib**_[/SIZE]
_[http://id3lib.sourceforge.net/](http://id3lib.sourceforge.net/)_
>                       id3lib is an open-source,           cross-platform software development library for reading, writing,           and manipulating ID3v1           and ID3v2tags.  It           is an on-going project whose primary goals are full compliance with           the ID3v2 standard, portability           across several platforms, and providing a powerful and feature-rich           API with a highly stable and efficient implementation. 
The version available from the Ubuntu repos, 3.8.3, supports up to ID3v2.3 and hence doesn't write UTF-8.

**EasyTag** uses this library for tag manipulation, and hence it cannot display/write ID3v2.4 tags -but it can handle ID3 up to version 2.3. Other projects using this library are: **grip**, **beep-media-player**.

[U][B][SIZE=4]libid3tag[/SIZE]
[/B][/U][http://sourceforge.net/project/showfiles.php?group_id=12349]("http://sourceforge.net/project/showfiles.php?group_id=12349")
[http://www.underbit.com/products/mad/]("http://www.underbit.com/products/mad/")> 
ID3 tag reading library from the MAD project.
ID3 tag manipulation library with full support for reading ID3v1, ID3v1.1, ID3v2.2, ID3v2.3, and ID3v2.4 tags, as well as support for writing ID3v1, ID3v1.1, and ID3v2.4 tags. 
Projects using this library are **muine** and **Rhythmbox**, which will therefore display ID3v2.4 tags correctly.

[SIZE=4]_**TagLib**_[/SIZE]
[http://developer.kde.org/~wheeler/taglib.html]("http://developer.kde.org/%7Ewheeler/taglib.html")
> TagLib is a library for reading and editing the meta-data of several popular audio formats. Currently it supports both ID3v1 and ID3v2 for MP3 files, Ogg Vorbis comments and ID3 tags and Vorbis comments in FLAC files. 
TagLib supports ID3 up to v2.4. Projects making use of this library are: **juk**, **amarok**, **streamtuner**, the **id3v2mux** gstreamer plugin.

I hope this helps clarifying things a bit. If I've reported anything incorrectly, please let me know and I'll update the post accordingly.

Cheers.

---

### Post by BigRod on 2006-07-03
How would one go about copying 2.4 tags to an earlier version?

---

### Post by soze on 2006-07-03
I whipped up a *very* quick-and-dirty Perl script to fix the id3 tags coming out of Soundjuicer.

```

#!/usr/bin/perl
require 5;
use strict;
use Image::ExifTool 'ImageInfo';
use MP3::ID3Lib;

my $trackdir = $ARGV[0];
opendir(DIR, $trackdir) || die("unable to open directory $trackdir");
my @tracks = grep { /.mp3/i } readdir DIR;
closedir DIR;
my $exifTool = new Image::ExifTool;

foreach (@tracks) {
    my $filename = "$trackdir/$_";

    $exifTool->ExtractInfo($filename);
    my $id3 = MP3::ID3Lib->new($filename);

    my $title = $exifTool->GetValue('Title');
    my $album = $exifTool->GetValue('Album');
    my $artist = $exifTool->GetValue('Artist');
    my $genre = $exifTool->GetValue('Genre');
    my $track = $exifTool->GetValue('Track');

    $track =~ /[^0-9]*([0-9]+)[^0-9]*/;
    $track = $1;

    print STDERR "$artist $album $title $genre $track\n";

    $id3->add_frame("TIT2", $title);
    $id3->add_frame("TPE1", $artist);
    $id3->add_frame("TALB", $album);
    $id3->add_frame("TRCK", $track);
    $id3->add_frame("TCON", $genre);

    $id3->commit;
    
}


```

Save the code above into a file (call it fixid3.pl)

Run it as:
```
fixid3.pl *dirname*
```

where *dirname* is the name of the directory containing the MP3 files on which you want to repair the tags. MAKE SURE YOU BACKUP YOUR MP3 FILES FIRST, AS THIS WILL MODIFY THEM IN PLACE!!!

Note: You will need to install a few packages first:
libimage-exiftool-perl
libid3-3.8.3-dev

You will also need to install the perl MP3::ID3Lib module, which does not seem to be packaged. You can install this with:
```
sudo perl -MCPAN -e 'install MP3::ID3Lib'
```

Enjoy!

---

### Post by Soarer on 2006-07-04
If yo want to rip, write tags & compress (normalize) then gnormalize ([http://gnormalize.sourceforge.net/](http://gnormalize.sourceforge.net/)) works fine for me.
I only use it for flac & ogg, so can't comment on how it handles mp3 tags mind. Also, no deb package is available so you have to use 'alien' to reformat it. Pretty easy though, and works well for me.

---

### Post by mannih2001 on 2007-07-12
> **desp said:**
> I think that's the key. You were spot on on your observation. Just to complement the information, an extract of the id3v2mux documentation


Right. But after some playing around on my system, I discovered id3mux which does the job. 

So the original pipeline could be changed to 
```
audio/x-raw-int,rate=44100,channels=2 ! lame name=enc bitrate=128 ! id3mux v1-tag=true v2-tag=false 
```

and you should be fine.

---

### Post by ebash on 2007-07-26
I also have a Sansa player and noticed that some MP3 tags can be read. After further investigation I found out that there are three types of MP3 tags ID3 v1, v2.3 and 2.4. The Sansa player is only able to understand ID3 tags v1 and v2.3. Gstreamer, the library used by amarok and sound-juicer can tag MP3 only in v1 and v2.4. Other software is able to encode in v2.3, for instance EasyTags can do it.

Since both the player and gstreamer can handle ID3 tags v1 one might think that the problem is solved. Well that could be far from the truth, v1 is a format clearly inferior to the v2.X, the major draw back being the lack of support for UNICODE.

I got annoyed by this and I started writing a gstreamer plugin that adds v2.3 tags. I have submitted the code to gstreamer and it's up for review, luckily it will be one day included in gstreamer. In the meanwhile you can try to compile the plugin in your own.

To compile the plugin download the three patches and follow the instructions in the bugzilla comments:
[http://bugzilla.gnome.org/show_bug.cgi?id=459226](http://bugzilla.gnome.org/show_bug.cgi?id=459226)

---

