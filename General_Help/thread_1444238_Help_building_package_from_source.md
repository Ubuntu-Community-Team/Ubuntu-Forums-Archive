---
title: "Help building package from source"
date: 2010-04-01
forum: General Help
---

### Post by me13221 on 2010-04-01
I have a problem with pulseaudio: it fills my logs with these messages:

```

Mar 31 22:03:46 poppy pulseaudio[16578]: ratelimit.c: 16 events suppressed
Mar 31 22:03:51 poppy pulseaudio[16578]: ratelimit.c: 15 events suppressed
Mar 31 22:03:56 poppy pulseaudio[16578]: ratelimit.c: 16 events suppressed
Mar 31 22:04:16 poppy pulseaudio[16578]: last message repeated 3 times
Mar 31 22:04:16 poppy pulseaudio[16578]: ratelimit.c: 15 events suppressed
Mar 31 22:04:21 poppy pulseaudio[16578]: ratelimit.c: 16 events suppressed
Mar 31 22:05:22 poppy pulseaudio[16578]: last message repeated 12 times
Mar 31 22:06:27 poppy pulseaudio[16578]: last message repeated 12 times
Mar 31 22:06:27 poppy pulseaudio[16578]: ratelimit.c: 15 events suppressed
Mar 31 22:06:32 poppy pulseaudio[16578]: ratelimit.c: 16 events suppressed

```

These messages seem to be harmless-- everything works normally-- but they're incredibly annoying.

So.. being an enterprising open-source user, I downloaded the source, commented out the line that leads to that comment (in src/pulsecore/ratelimit.c, lines 54-55), compiled the code, and ran 'sudo make install'.  Then I killed all instances of pulseaudio and 

Except the messages keep coming.  How could this be? the line that writes to the log has been commented out.  I observe that my version of pulseaudio was installed in /usr/local/bin/pulseaudio; the system keeps using the version in /usr/bin/pulseaudio.

How do I get the system to use my newly-built version?

Thanks in advance.

---

