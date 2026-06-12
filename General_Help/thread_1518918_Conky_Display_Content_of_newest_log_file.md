---
title: "Conky Display Content of newest log file"
date: 2010-06-27
forum: General Help
---

### Post by waynemeat on 2010-06-27
Hi there,

I've been messing about with conky and I would like to display the contents of some of my log files.

For the last 2 days I have been using the following command line to output the content of a log file:

/var/log/debug
e${exec tail -30 /var/log/debug | cat -n -E}
(Print last 30 lines of the debug log)


Today I realised that once a log has reached a certain size it will create a new one with .1 .2 .n extension on it.


I've modified the command line to find the newest log but it doesn't seem to work:

e${exec tail -30 | ls -t /var/log/ | grep -A 0 'debug' | tail -1 | cat -n -E}
(Print last 30 lines of newest log file with debug in its name)

Can someone help me please. Am I missing quotes somewhere?

---

