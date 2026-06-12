---
title: "Terminate linux command after 5 seconds"
date: 2009-08-12
forum: General Help
---

### Post by pieter333 on 2009-08-12
Hi,

I have a radio stream that also sends metadata of the song that is playing to the command line with mplayer [http://url-to-radio-stream/](http://url-to-radio-stream/).

With PHP I would like to execute the command "mplayer http://url-to-radio-stream/" and collect the output buffer.

But if I execute this like the way above, it will offcourse keep streaming.
Is there a way to execute a linux command that terminates after for example 5 seconds?

Greetings,
Pieter

---

### Post by Tibuda on 2009-08-12
```
mplayer http://url-to-radio-stream/ &
PID=$!
sleep 5
kill $PID
```

---

### Post by andrew.46 on 2009-08-12
Hi pieter333,

A *slight* variation on the syntax suggested by danielrmt which saves one line:

```
mplayer http://url-to-radio-stream/ &
sleep 5
kill $!
```

Andrew

---

