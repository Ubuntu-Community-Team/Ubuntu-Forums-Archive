---
title: "CRON scheduling &amp; scripting"
date: 2009-12-22
forum: General Help
---

### Post by EdGy28376 on 2009-12-22
I have program that I can run in a terminal window. It reads a text file to dial a modem and record the results. The terminal can be used for user input however I normally just let it run. I have been trying to get it to run from CRON. 

After much research I have been unsuccessful. I have tried exporting to xterm, and export display with no luck. Is it even possible?

---

### Post by VCoolio on 2009-12-22
When using crontab, try adding a line "SHELL=/bin/bash" on top and also specify the exact path to everything; so "/path/to/script -a -b  /path/to/file". Unless you also specify "HOME=/home/<you>" and "PATH=/bla:/bla/2:/bla/bla/3". Hope that helps a bit. Display shouldn't matter if it's a cli script.

---

### Post by EdGy28376 on 2009-12-22
Ok I 'fingered' it out!!

First in crontab or webmin when you call your script i.e. /usr/local/etc/myscript.sh 

it should end with >/dev/null (google ">/dev/null" it will help you understand)

So it would look like this:
  /usr/local/etc/myscript.sh >/dev/null

Then in the script itself it should start with something like:
#!/bin/sh
export TERM=xterm
then the command line and switches

Hope this helps someone save a little time and hair :guitar:

Merry Christmas!!

---

### Post by EdGy28376 on 2009-12-24
Update- Since I was calling a bash script I had to preference the command with bash in the crontab file.

---

