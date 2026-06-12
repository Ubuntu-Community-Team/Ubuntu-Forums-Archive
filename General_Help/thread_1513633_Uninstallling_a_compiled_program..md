---
title: "Uninstallling a compiled program."
date: 2010-06-19
forum: General Help
---

### Post by Grandma_DOG on 2010-06-19
I got a little too advanced for my own good. I thought I needed to compile ffmpeg in order to read some specialty codec. I did that months ago. However, after I did that, it broke several other programs like mplayer and devede.

To get rid of the compiled ffmpeg, I deleted ffmpeg from my /(user)/ffmpeg.

If i command line type 'ffmpeg' i get:
bash: /usr/bin/ffmpeg: No such file or directory

so I think I have a symlink issue. This is over my head. How do I fix this so I can install the normal ffmpeg? Synaptic installs something but it won't run (symlink issue again).

---

### Post by utnubuuser on 2010-06-19
Not sure as to the correct procedure, but you could have a look through the files with 'locate' ie: locate ffmpeg

---

### Post by jonobr on 2010-06-19
looks like when you type ffmpeg your path is set to look for the executable in /usr/bin

I have not worked on this myself, but what I would is to try and recompile/reinstall the program and then remove sudo apt-get remove ffmpeg
as outlined on the [wiki page]("https://wiki.ubuntu.com/ffmpeg")

---

### Post by rtimai on 2010-06-19
If you're running Ubuntu 10.04 it comes with a default installation of Computer Janitor. I'm not sure if it will remove broken packages, but it claims to remove packages you don't need, and to "suggest configuration changes that might benefit you." 

Also, try Synaptic Package Manager. Sort by Status, select "Not Installed (Residual Config)." Compiled programs should appear in the "Installed (Manual)" group, possibly broken compiled installations in the Residual Config group. If ffmpeg is listed, it should remove residual traces that manual deletion missed. BTW, software removal is always best removed by a package manager, which seems to work automagically. Few installations go away just by deleting their files. I get you with ffmpeg, though, it's hard to know what you need. 

Good luck...

---

### Post by Grandma_DOG on 2010-06-20
All I really want to do here is install ffmpeg.  Normally I'd use synaptic and install and all would be right.

But because I did some build, there is a symlink issue and ffmpeg won't work which breaks all the programs dependent on it.

apt-get purge ffmpeg followed by an apt-get install ffmpeg doesn't fix it.
Somewhere there is a link that has the newly installed ffmpeg program looking for the binaries in the wrong place.

So how do I look for the broken symlink and fix it?

---

### Post by nothingspecial on 2010-06-20
Use find

```
find / -type l -name *ffmpeg*
```

so the -type l means sym link and the -name bit means any string containing the string ffmpeg.

However, my self compiled ffmpeg is in /usr/bin as you would expect.

Type man find if you want to read a huge instruction manual that makes little sense.

[[COLOR="Magenta"]This[/COLOR]]("http://www.softpanorama.org/Tools/Find/find_mini_tutorial.shtml") is a good find tutorial.

---

### Post by bruno9779 on 2010-06-20
It is a bit late, but the right approach would have been:

```
make uninstall
```

in the build directory for ffmpeg. (unless stated differently in the documentation).

On a different note, have you tried reinstalling ffmpeg from repos?

If that fails as well, I personally would download the same .tar.gz for ffmpeg, compile it and then "make uninstall"

---

### Post by Grandma_DOG on 2010-06-23
when I type in "whereis ffmpeg" i get
ffmpeg: /usr/bin/ffmpeg /usr/share/ffmpeg /usr/share/man/man1/ffmpeg.1.gz

when I got type in ffmpeg -help
I get "ffmpeg: relocation error: ffmpeg: symbol av_destruct_packet, version LIBAVFORMAT_52 not defined in file libavformat.so.52 with link time reference"

sudo apt-get purge ffmpeg and then reinstall doesn't work.

any ideas?

---

### Post by Grandma_DOG on 2010-08-18
I hate compiling.

---

### Post by FakeOutdoorsman on 2010-08-25
Are you still having this issue?  This [thread](http://ubuntuforums.org/showthread.php?t=1560374) had a similar error (...*LIBAVFORMAT_52 not defined*...) and the OP seems to have resolved it.

---

