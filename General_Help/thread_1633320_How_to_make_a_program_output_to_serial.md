---
title: "How to make a program output to serial?"
date: 2010-11-29
forum: General Help
---

### Post by Quazzy on 2010-11-29
Hello!

I've made a LED gadget, which can light up LED patterns. It connects to serial port with RS232 protocol and receives messages which contain desired patterns. My friend wrote a python program which generates patterns and writes them to terminal. Everything is fine this far.
I've made a bash script to run this program:
[FONT=Arial][SIZE=2]#!/bin/bash
python gen.py[/SIZE][/FONT]
and set it to autostart with:

[FONT=Arial][SIZE=2]chmod 755 scr.sh
mv scr.sh /etc/init.d/scr.sh 
sudo update-rc.d scr.sh defaults[/SIZE][/FONT]

What I don't understand is - how do I redirect it's output to ttyS0 so that my device could catch generated data?

I've heard that in Linux every data stream can be redirected anywhere with '>>' in bash script. How do I do that? Can I, dunno, write something like this: python gen.py >> ttyS0 in shell script?

Also I probably need to autologin ttyS0 at autostart?

Any help appreciated.

---

### Post by wt8008 on 2010-11-29
For writing terminal output of the python file to ttyS0 you can try to use
```
python gen.py > /dev/ttyS0
```

I am not too familiar with the autostart setup in Ubuntu.

---

