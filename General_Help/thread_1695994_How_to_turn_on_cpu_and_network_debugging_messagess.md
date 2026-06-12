---
title: "How to turn on cpu and network debugging messages/syslogd to read via klogd/syslogd?"
date: 2011-02-26
forum: General Help
---

### Post by linux_question on 2011-02-26
For example: echo 1 > /proc/sys/vm/block_dump

turns on I/O debugging messages which I can then parse for process wise I/O operations. I want to do the same for CPU operations and network operations per process.

I know there are command line tools like top,ps, netstat etc and a lot of information available in /proc/ directory too. But this is for a research project and it is important for me to get kernel level timestamps.

Thanks a lot!

---

