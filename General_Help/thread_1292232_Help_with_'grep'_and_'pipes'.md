---
title: "Help with 'grep' and 'pipes'"
date: 2009-10-15
forum: General Help
---

### Post by tosszyx on 2009-10-15
Hi there, I'm trying to make this command run, but I'm not getting the expected results:

```
$ mplayer test4.mp3 | grep -e "Title:" -e "Artist" > out.txt
```

What happens is that the file 'out.txt' remains empty until the song finishes playing. Then it gets the expected information.

```
$ cat out.txt
 Title: Fee
 Artist: Phish

```

But when I *not* redirect the output:

```
$ mplayer test4.mp3 | grep -e "Title:" -e "Artist"
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.
 Title: Fee
 Artist: Phish
AO: [pulse] Failed to connect to server: Connection refused
```

The information is shown immediately, can someone help me out to figure out what am I doing wrong? How could I get the information on the file immediately ?

Thanks !

---

### Post by sisco311 on 2009-10-15
The output of mplayer is piped to grep when mplayer exits.

I would use mp3info
```
mp3info -p "Title:  %t\nArtist: %a\n" /path/to/file > file
```

---

### Post by tosszyx on 2009-10-15
But why then, I can grep the output of mplayer when it is still playing the file ?

---

### Post by sisco311 on 2009-10-15
> **tosszyx said:**
> But why then, I can grep the output of mplayer when it is still playing the file ?

yep, you are right.

grep is writing to stdout (standard output),
stdout is redirected to the file when grep exits.

---

### Post by andrew.46 on 2009-10-15
Hi tosszyx,

> **tosszyx said:**
> Hi there, I'm trying to make this command run, but I'm not getting the expected results:

```
$ mplayer test4.mp3 | grep -e "Title:" -e "Artist" > out.txt
```

What happens is that the file 'out.txt' remains empty until the song finishes playing. Then it gets the expected information.

It is a little ugly but you could try:

```
mplayer test4.mp3 **[COLOR="Red"]-ao null -endpos 1[/COLOR]** | grep -e "Title:" -e "Artist" > out.txt
```

and this works well enough on my system...

Andrew

---

### Post by sisco311 on 2009-10-15
or:
```

mplayer file.mp3 | while read line; do echo $line | grep Title >> out.txt; done
```

---

### Post by Giblet5 on 2009-10-15
> **sisco311 said:**
> yep, you are right.

grep is writing to stdout (standard output),
stdout is redirected to the file when grep exits.

Almost.

mplayer writes to stdout which is a buffered stream. If the ouput exceeds about 4KB, grep will catch some output. Otherhow, the output won't be physically written until the stream is flushed, which occurs as exit(2) closes the stdio streams for mplayer.

Pipes work best when the stream source exits quickly and shoves its output through the pipeline (like mp3info, although it doesn't require any pipes to do what you want).

---

### Post by sisco311 on 2009-10-15
> **Giblet5 said:**
> Almost.

mplayer writes to stdout which is a buffered stream. If the ouput exceeds about 4KB, grep will catch some output. Otherhow, the output won't be physically written until the stream is flushed, which occurs as exit(2) closes the stdio streams for mplayer.

Pipes work best when the stream source exits quickly and shoves its output through the pipeline (like mp3info, although it doesn't require any pipes to do what you want).

Thanks for the clarification!

---

### Post by tosszyx on 2009-10-15
@andrew.46: Thanks a lot, unfortunately I'm trying to reencode some non-mp3 files to mp3 so I do need for the file to play, otherwise it was a nice hack ! 

@sisco311: Great trick !! It works excellent. Thank you for your help.

@Giblet5: Thanks a lot for sharing with us, it is very interesting.

---

### Post by tosszyx on 2009-10-16
Hi, what I'm trying to do is to reencode some files to mp3 trying to obtain the information from the tags information from mplayer (that I'm already using to decode the files).

Right now I have: 

```

mplayer test4.mp3 | while read line; do echo $line | grep -e "Title: " -e "Artist: " | awk -F ": " '{print $2}'; done

```

And from that I get the output like: 

```

mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.
AO: [pulse] Failed to connect to server: Connection refused
[B]Fee
Phish[/B]

```

But I can not find a way to assign that output inside a script to some variables, because all the piping. Any ideas?

---

