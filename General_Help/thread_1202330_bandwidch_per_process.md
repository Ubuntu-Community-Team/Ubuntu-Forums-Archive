---
title: "bandwidch per process"
date: 2009-07-02
forum: General Help
---

### Post by H4F on 2009-07-02
cpulimit - limit the cpu usage of a process (expressed in percentage, not in cpu time).
 I need same think for Network Bandwidth . so I can limit speed of FF etc.

---

### Post by polax on 2009-07-02
A wonderful tutorial answering your question is available [here]("http://ubuntuforums.org/showthread.php?t=992706")

Enjoy your Ubuntu

---

### Post by H4F on 2009-07-02
Did you read my question till the end?
I am giving cpulimit as an example. I know how to use it.

I need similar tool for network bandwidth

---

### Post by WRDN on 2009-07-02
Trickle sounds like the tool for you: [http://debaday.debian.net/2007/05/30/trickle-a-lightweight-userspace-bandwidth-shaper/](http://debaday.debian.net/2007/05/30/trickle-a-lightweight-userspace-bandwidth-shaper/)

---

### Post by H4F on 2009-07-02
Thanks for reply. I need to limit per process. for examle to limit network usage of  pidgin, skype or FF 
:(

---

### Post by WRDN on 2009-07-02
Thats what Trickle is used for. This is the usage information for it:

> Usage: trickle [-hvVs] [-d <rate>] [-u <rate>] [-w <length>] [-t <seconds>]
               [-l <length>] [-n <path>] command ...
	-h           Help (this)
	-v           Increase verbosity level
	-V           Print trickle version
	-s           Run trickle in standalone mode independent of trickled
	-d <rate>    Set maximum cumulative download rate to <rate> KB/s
	-u <rate>    Set maximum cumulative upload rate to <rate> KB/s
	-w <length>  Set window length to <length> KB 
	-t <seconds> Set default smoothing time to <seconds> s
	-l <length>  Set default smoothing length to <length> KB
	-n <path>    Use trickled socket name <path>
	-L <ms>      Set latency to <ms> milliseconds

So, for Pidgin, use:

```
trickle -d 30 -u 30 pidgin
```

This limits the download rate to 30kb/s and the upload to 30kb/s (give or take 1kb/s on average).

---

### Post by H4F on 2009-07-02
good. seems i did not look enough at tickle.
now the only problem remain is that you need to close pedgin and open it again to change limit. :(

any way thanks

---

