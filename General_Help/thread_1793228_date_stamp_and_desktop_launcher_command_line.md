---
title: "date stamp and desktop launcher command line?"
date: 2011-06-29
forum: General Help
---

### Post by maclenin on 2011-06-29
Hello!

I am trying to coax the following bit of desktop launcher command code into appending a date stamp (in the indicated format) to "log_file_"...

```
**Comm_a_nd:** sh -c "/path/to/script.sh | tee log_file_`date +"%m%d%Y_%H%M"`"
```
...without much success....

I have also tried...```
"...log_file_$(date +"%m%d%Y_%H%M")"
```...which yields "**log_file_[COLOR="DarkOrange"]_[/COLOR]**"...and...

```
"...log_file_$(date)"
```...which simply appends a 3 letter abbr. of today's day of the week - i.e. "**log_file_[COLOR="DarkOrange"]Wed[/COLOR]**"....

Thanks for any suggestions!

---

### Post by ajgreeny on 2011-06-29
I would have expected your second version shown to work, assuming that the tee syntax is correct, but never having used it I am not at all sure about that.

I have a shell script I use with cron to record BBC Radio2 occasionally and in that I use a variable in the file name as follows:-
file=/home/*user*/Radio/$(date +%F_%H-%M)-BBCR2.wav
and that works beautifully producing a file named
/home/*user*/Radio/2011-06-29_12-23-BBCR2.wav
so the only other thing I can suggest is using the full pathway to tee in your script, ie /usr/bin/tee, or double checking the tee syntax used inn the script.

---

### Post by Toz on 2011-06-29
Doesn't look like its possible. See: [http://www.linuxquestions.org/questions/linux-desktop-74/xfce-could-not-use-$-command-in-a-launcher-command-836329/]("http://www.linuxquestions.org/questions/linux-desktop-74/xfce-could-not-use-$-command-in-a-launcher-command-836329/")

Shell scripts may be the way to go.

---

### Post by maclenin on 2011-06-29
Thanks **ajgreeny** and **Toz**!

The ticket - in my case - was (indeed) to create a "script_log.sh" shell script... 
```
/path/to/script.sh 2&>1 | tee script_log_`date +"%m%d%Y_%H%M"`
```

...which addresses the "dating" issue as it calls "script.sh" - all of which I am still able to kick-off via the desktop launcher, like so...

```
Exec=/path/to/script_log.sh
```

Win win!

It's a modular approach (multiple files) - but I am enjoying the "scripted" flexibility!

Thanks for the help!

---

