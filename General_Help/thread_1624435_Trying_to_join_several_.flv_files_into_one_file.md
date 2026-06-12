---
title: "Trying to join several .flv files into one file"
date: 2010-11-17
forum: General Help
---

### Post by t0p on 2010-11-17
I have 5 .flv files that I want to join together into 1 file.  Following the advice in [this thread]("http://ubuntuforums.org/showthread.php?t=956769"), I issued this command and got this output:

```

t0p@deimos:~$ mencoder -forceidx -of lavf -oac copy -ovc copy -o output.flv A_Death_in_Tehran_-_Part_1_0f_5_PBS.flv A_Death_in_Tehran_-_Part_2_of_5_PBS.flv A_Death_in_Tehran_-_Part_3_of_5_PBS.flv A_Death_in_Tehran_-_Part_4_of_5_PBS.flv A_Death_in_Tehran_-_Part_5_of_5_PBS.flv
[output that I can't copy and paste as the terminal won't scroll back far enough, but I think it's mostly like the following]
[flv @ 0x87211e8]Unsupported video codec (7)
[flv @ 0x87211e8]Unsupported video codec (7)
[flv @ 0x87211e8]Unsupported video codec (7)
[flv @ 0x87211e8]Unsupported video codec (7)
[flv @ 0x87211e8]Unsupported video codec (7)
[flv @ 0x87211e8]Unsupported video codec (7)
[flv @ 0x87211e8]Unsupported video codec (7)
[flv @ 0x87211e8]Unsupported video codec (7)
[flv @ 0x87211e8]Unsupported video codec (7)
[flv @ 0x87211e8]Unsupported video codec (7)
[flv @ 0x87211e8]Unsupported video codec (7)
[flv @ 0x87211e8]Unsupported video codec (7)
[flv @ 0x87211e8]Unsupported video codec (7)
[flv @ 0x87211e8]Unsupported video codec (7)
[flv @ 0x87211e8]Unsupported video codec (7)
[flv @ 0x87211e8]Unsupported video codec (7)
[flv @ 0x87211e8]Unsupported video codec (7)
[flv @ 0x87211e8]Unsupported video codec (7)
[flv @ 0x87211e8]Unsupported video codec (7)
[flv @ 0x87211e8]Unsupported video codec (7)
[flv @ 0x87211e8]Unsupported video codec (7)
[flv @ 0x87211e8]Unsupported video codec (7)
[flv @ 0x87211e8]Unsupported video codec (7)
[flv @ 0x87211e8]Unsupported video codec (7)
[flv @ 0x87211e8]Unsupported video codec (7)
[flv @ 0x87211e8]Unsupported video codec (7)
[flv @ 0x87211e8]Unsupported video codec (7)
[flv @ 0x87211e8]Unsupported video codec (7)
[flv @ 0x87211e8]Unsupported video codec (7)
[flv @ 0x87211e8]Unsupported video codec (7)
[flv @ 0x87211e8]Unsupported video codec (7)
[flv @ 0x87211e8]Unsupported video codec (7)
[flv @ 0x87211e8]Unsupported video codec (7)
[flv @ 0x87211e8]Unsupported video codec (7)
[flv @ 0x87211e8]Unsupported video codec (7)
[flv @ 0x87211e8]Unsupported video codec (7)
[flv @ 0x87211e8]Unsupported video codec (7)
[flv @ 0x87211e8]Unsupported video codec (7)
[flv @ 0x87211e8]Unsupported video codec (7)
[flv @ 0x87211e8]Unsupported video codec (7)
[flv @ 0x87211e8]Unsupported video codec (7)
[flv @ 0x87211e8]Unsupported video codec (7)
[flv @ 0x87211e8]Unsupported video codec (7)
[flv @ 0x87211e8]Unsupported video codec (7)
[flv @ 0x87211e8]Unsupported video codec (7)
[flv @ 0x87211e8]Unsupported video codec (7)
[flv @ 0x87211e8]Unsupported video codec (7)
[flv @ 0x87211e8]Unsupported video codec (7)
[flv @ 0x87211e8]Unsupported video codec (7)
[flv @ 0x87211e8]Unsupported video codec (7)
[flv @ 0x87211e8]Unsupported video codec (7)
[flv @ 0x87211e8]Unsupported video codec (7)
[flv @ 0x87211e8]Unsupported video codec (7)
[flv @ 0x87211e8]Unsupported video codec (7)
[flv @ 0x87211e8]Unsupported video codec (7)
[flv @ 0x87211e8]Unsupported video codec (7)
[flv @ 0x87211e8]Unsupported video codec (7)
[flv @ 0x87211e8]Unsupported video codec (7)
[flv @ 0x87211e8]Unsupported video codec (7)
[flv @ 0x87211e8]Unsupported video codec (7)
[flv @ 0x87211e8]Unsupported video codec (7)
[flv @ 0x87211e8]Unsupported video codec (7)
[flv @ 0x87211e8]Unsupported video codec (7)
[flv @ 0x87211e8]Unsupported video codec (7)
[flv @ 0x87211e8]Unsupported video codec (7)
[flv @ 0x87211e8]Unsupported video codec (7)
[flv @ 0x87211e8]Unsupported video codec (7)
[flv @ 0x87211e8]Unsupported video codec (7)
[flv @ 0x87211e8]Unsupported video codec (7)
[flv @ 0x87211e8]Unsupported video codec (7)
[flv @ 0x87211e8]Unsupported video codec (7)
[flv @ 0x87211e8]Unsupported video codec (7)
[flv @ 0x87211e8]Unsupported video codec (7)
[flv @ 0x87211e8]Unsupported video codec (7)
[flv @ 0x87211e8]Unsupported video codec (7)
[flv @ 0x87211e8]Unsupported video codec (7)
[flv @ 0x87211e8]Unsupported video codec (7)
[flv @ 0x87211e8]Unsupported video codec (7)
[flv @ 0x87211e8]skipping flv packet: type 97, size 7627016, flags 0
[flv @ 0x87211e8]skipping flv packet: type 6, size 8893801, flags 0
[flv @ 0x87211e8]skipping flv packet: type 139, size 4340476, flags 0
[flv @ 0x87211e8]skipping flv packet: type 138, size 7429098, flags 0
[flv @ 0x87211e8]skipping flv packet: type 141, size 4929325, flags 0
[flv @ 0x87211e8]skipping flv packet: type 214, size 16043793, flags 0
[flv @ 0x87211e8]skipping flv packet: type 160, size 33453, flags 0
[flv @ 0x87211e8]skipping flv packet: type 0, size 284, flags 0
[flv @ 0x87211e8]skipping flv packet: type 102, size 1192527, flags 0
[flv @ 0x87211e8]skipping flv packet: type 149, size 15790717, flags 0
[flv @ 0x87211e8]skipping flv packet: type 253, size 11302580, flags 0
[lavf] Video stream found, -vid 0
[lavf] Audio stream found, -aid 1
VIDEO:  []  0x0  0bpp  29.970 fps    0.0 kbps ( 0.0 kbyte/s)
[V] filefmt:44  fourcc:0x7  size:0x0  fps:29.97  ftime:=0.0334
** MUXER_LAVF *****************************************************************
REMEMBER: MEncoder's libavformat muxing is presently broken and can generate
INCORRECT files in the presence of B frames. Moreover, due to bugs MPlayer
will play these INCORRECT files as if nothing were wrong!
*******************************************************************************
OK, exit
videocodec: framecopy (0x0 0bpp fourcc=7)
audiocodec: framecopy (format=a chans=2 rate=44100 bits=16 B/s=0 sample-0)
[flv @ 0x87211e8]Unsupported video codec (7)
VIDEO CODEC ID: 0
AUDIO CODEC ID: 0, TAG: 0
Writing header...
[flv @ 0x87211e8]dimensions not set
Floating point exception
t0p@deimos:~$

```

Anyone know why this doesn't work?  Can anyone tell me how I *can* get it to work?

---

