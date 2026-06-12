---
title: "Create a script to log anther script?"
date: 2012-02-19
forum: General Help
---

### Post by royevans on 2012-02-19
Good afternoon everyone, My problem is a, hopefully, simple one, My start up script is as follows;

```
ezstream -c /mp3/ezstream_reencode_mp3.xml

screen vlc -I http
```named "streams.sh" and placed into /etc/init.d, I would like to know if it's at all possible to tell these commands to write a log of errors they have or things of that nature to separate files in a designated location.

For the record, this is on a VPS, so no GUI to speak of, just good ol' terminal.

---

### Post by TeoBigusGeekus on 2012-02-19
You could try redirecting the errors (2) to a file, ie something like
```
ezstream -c /mp3/ezstream_reencode_mp3.xml

screen vlc -I http 2>/path/logfile
```
Just a thought...

---

### Post by royevans on 2012-02-19
> **TeoBigusGeekus said:**
> You could try redirecting the errors (2) to a file, ie something like
```
ezstream -c /mp3/ezstream_reencode_mp3.xml

screen vlc -I http 2>/path/logfile
```Just a thought...

so...would I just put ```
2>/blah/blah/blah
``` at the end of the file? I'm sorry, I guess I neglected to mention that I'm only experienced with the basics of ubuntu.

---

### Post by azmyth on 2012-02-19
Replace your command in your streams.sh file

screen vlc -I http

with

screen vlc -I http 2>/path/logfile

Naturally change the /path/logfile to an actual file.

---

### Post by TeoBigusGeekus on 2012-02-19
^^^^ This.

Not at the end of the file, at the end of the command.

---

### Post by royevans on 2012-02-19
So the "2>/path/logfile" can it be placed at the end of both commands for separate files?

---

### Post by CharlesA on 2012-02-19
> **royevans said:**
> So the "2>/path/logfile" can it be placed at the end of both commands for separate files?
Yes.

---

### Post by royevans on 2012-02-19
Great, thank you all.

---

