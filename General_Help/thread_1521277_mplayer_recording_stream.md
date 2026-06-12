---
title: "mplayer recording stream"
date: 2010-06-30
forum: General Help
---

### Post by shane2peru on 2010-06-30
I have a little script that I have developed over some time to record internet radio so I can listen to it and later delete it.  The pertinent line in the script is this:

```

mplayer -cache 1024 -dumpstream -dumpfile $name.mp3 $STREAM &
sleep $DURATION # Length of the program being recorded as background. 
kill -9 $!         # End the most recently backgrounded job = mplayer
exit

```
There are variables that are set.  The problem I have is that mplayer hogs the internet connection.  The first few moments it is running, no problem, it is fine, however the longer it runs, the more it uses!  Before long it is using up all my 90k download ability I have, making my web browser run extremely slow, and my internet phone worthless.  I have tried the -bandwidth option, but that didn't seem to help.  Any ideas would be greatly appreciated!  

Shane

---

### Post by ajgreeny on 2010-06-30
With a 90k (kilobytes or kilobits?) download speed, I'm not sure there is anything you can really do to help things along.  Many streams will be streaming at rates above that figure, if it is in kilobits.

I hope I'm wrong, however, for your sake.

---

### Post by shane2peru on 2010-06-30
> **ajgreeny said:**
> With a 90k (kilobytes or kilobits?) download speed, I'm not sure there is anything you can really do to help things along.  Many streams will be streaming at rates above that figure, if it is in kilobits.

I hope I'm wrong, however, for your sake.

Well, for as much of a 'geek' as I am, I must confess I don't know that much about internet speeds.  When I scroll over the panel where I have the monitoring things, it tells me 90KB/sec  so I'm assuming that would be kilobytes, not kilobits.  I do have dsl, however it isn't that fast here in South America.  

Shane

---

