---
title: "File permissions"
date: 2010-10-24
forum: General Help
---

### Post by stallvalds on 2010-10-24
Before I ask my question, I would like to say that this could go in the programming section but I say the underlying cause if a file permissions issue. If I placed this incorrectly, then move it.

OK,
I am working on a website and am trying to embed mp4 videos. I am using jw player as my media player. Here is my code:
```

<object classid="clsid:D27CDB6E-AE6D-11cf-96B8-444553540000" width="480" height="270" id="player1" na
<param name="movie" value="jwmed53/player.swf">
<param name="allowfullscreen" value="true">
<param name="allowscriptaccess" value="always">
<param name="flashvars" value="file=video.mp4&autostart=true">
<embed id="player1"
name="player1"
src="jwmed53/player.swf"
width="480"
height="270"
allowscriptaccess="always"
allowfullscreen="true"
flashvars="file=video.mp4&autostart=true"
/>
</object>
```

This code is working properly. It tells the player to play a sample file that came with jw player. This is just fine. The problem is when I try to play other mp4 files I get a message saying "File not found or access denied." The vid I want to embed is a video downloaded from youtube and converted to mp4. It is in the same directory as the sample file that plays correctly, so I know my code is correct.
So I guess my question is do I need to adjust some sort of setting in the properties of my downloaded file in order for it to be played in a browser? I hope that this isn't too long and drawn out.
Thanks in advance<
~stallvalds

---

### Post by Hippytaff on 2010-10-24
if you need to change permissions you can you chmod - [https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)

---

### Post by stallvalds on 2010-10-24
Thanks for the suggestion, but no dice. I opened up the file with the command ```
chmod 777 sm3.mp4
``` (I renamed my downloaded file sm3.flv) and still the same result. I have to figure out what the difference is between the sample file that plays and my downloaded video.

I downloaded the file with download helper. Then I used ffmpeg to convert it from flv to mp4 format. I am utterly confused as to why this will not work. I have been struggling with it since last night. Any other suggestions??

---

### Post by efflandt on 2010-10-24
Files on a webserver should usually have 644 permission -rw-r--r--.  Server side scripts (like cgi) typically need 755 permission -rwxr-xr-x.

If the file was on a FAT32 file system (without any concept of file permissions) it might end up with 777 permissions (anybody can read, write, execute) and many webservers may refuse to serve such content because it is totally insecure.

In a terminal type: **man chmod**

To see permissions and owner/group of the file that works do: **ls -l** (small L)

---

### Post by stallvalds on 2010-10-24
efflandt-
I tried your 644 permission suggestion for the sm3.mp4 file and I still am not able to play it in any browser. Its just confusing that I can play the sample mp4 that came with the player but not any other file. I might try it in Windoze (eewww) and see if I have any better luck.

---

### Post by stallvalds on 2010-10-24
SOLVED!! Mental error. Sorry for the waste of time everyone.

---

### Post by Hippytaff on 2010-10-24
> **stallvalds said:**
> SOLVED!! Mental error. Sorry for the waste of time everyone.

What was the problem? just so it's here for future reference, and because I like to know :-)

---

### Post by stallvalds on 2010-10-24
Of course it was just stupidity on my part. My mp4 was in the wrong directory. I learned HTML in windows and I find that linking files is slightly different in Ubuntu.

---

