---
title: "View Script Output?"
date: 2010-12-12
forum: General Help
---

### Post by csharpplus on 2010-12-12
A friend, using a remote machine, **SSH**ed to my machine and ran the following python script: 
_________________
[COLOR=#0000ff]while[/COLOR] (1):
    [COLOR=#0000ff]....print[/COLOR] "hello world"
_________________

(this script simply prints 'hello world' continuously).

I am now logged in to my machine. How can I see the output of the script my friend was running? 

if it helps, I can 'spot' the script my friend is using:

________________________________________________
me@home:~$ ps aux | grep just
[COLOR=DarkRed]friend      7494 12.8  0.3   7260  3300 ?        Ss   17:24   0:06 python TEST_AREA/justprint.py[/COLOR]
friend      7640  0.0  0.0   3320   800 pts/3    S+   17:25   0:00 grep --color=auto just
________________________________________________

what steps should I take in order to view the "hello world" messages on my screen?

---

### Post by papibe on 2010-12-22
[http://ubuntuforums.org/showthread.php?t=1644479]("http://ubuntuforums.org/showthread.php?t=1644479")

---

