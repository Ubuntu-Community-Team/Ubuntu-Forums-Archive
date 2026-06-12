---
title: "syslog-ng &quot;Number of allowed concurrent connections exceeded&quot;"
date: 2010-11-05
forum: General Help
---

### Post by herta on 2010-11-05
ubuntu server 10.4
syslog-ng '2.0.9'

I'm setting up a central syslog server.  It seems to be working, but when I start syslog-ng, I get a bursts of

Nov  5 15:08:39 hm-syslog syslog-ng[26897]: Number of allowed concurrent connections exceeded; num='10', max='10'

According to a number of posts on the web, you need to increase the number of connections for the unix-stream, which is set to 10 by default.  I meanwhile set it to 50, but it still claims it only has 10.

This is the source section that has the unix-stream definition:

[INDENT]source s_local {
  # messages from syslog-ng
  internal();

  # standard Linux log source
  # this is the default place for the syslog() function to send logs to
  unix-stream("/dev/log" max-connections(50));

  # messages from the kernel
  pipe("/proc/kmsg");
};
[/INDENT]
Anyone any ideas?

Kind regards,

Herta

---

### Post by herta on 2010-11-05
FWIIW, I did first reload, and even restart syslog-ng after making the change.

---

### Post by herta on 2010-11-05
Ah, found it.  Apparently "tcp" has a max-connections option as well.

Case closed. :-)

---

