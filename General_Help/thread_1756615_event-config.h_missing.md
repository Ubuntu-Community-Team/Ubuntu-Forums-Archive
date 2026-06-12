---
title: "event-config.h missing?"
date: 2011-05-12
forum: General Help
---

### Post by Twizzle on 2011-05-12
I am trying to compile forked-daapd following one of the posts on this forum however run into a problem when I run make:

```
evhttp/http.c:28: fatal error: event-config.h: No such file or directory
compilation terminated.
make[3]: *** [forked_daapd-http.o] Error 1
make[3]: Leaving directory `/home/john/Source/forked-daapd/src'
make[2]: *** [all] Error 2
make[2]: Leaving directory `/home/john/Source/forked-daapd/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/john/Source/forked-daapd'
make: *** [all] Error 2

```


I can't seem to find much on event-config.h through Google or on this forum so am a bit stumped.

Can anyone enlighten me how I can try to fox this.

Thanks


I tried reinstalling from a different source and it just ran ok. Not sure what the problem was but it is fixed now.

---

