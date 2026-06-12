---
title: "Record stream, increment file name output"
date: 2009-10-16
forum: General Help
---

### Post by ajgreeny on 2009-10-16
I am using a shell script to time and record radio streams, but have occasionally overwritten one output file with the new one when cron timing more than one event.  How can I change my script to increase the output file name with a number each time to avopid overwriting in future.

Here is my script file
```
#!/bin/bash
mplayer -cache 2048 <URL> -vc null -vo null -ao pcm:fast:waveheader:file=outfile.wav
```I'm sure it must be possible to change the file output each time, ie outfile.wav, outfile1.wav, outfile2wav, etc etc. with a simple variable, but a google and forum search has not enlightened me, I'm afraid, so I'm asking the experts directly.

---

### Post by andrew.46 on 2009-10-16
Hi ajgreeny,

> **ajgreeny said:**
> How can I change my script to increase the output file name with a number each time to avoid overwriting in future.

I suspect that use of 'date' might be the best way. There are many, many variations but perhaps the following might help:
```

mplayer -cache 2048 <URL> -vc null -vo null -ao pcm:fast:waveheader:file=**[COLOR="Red"]`date +%F-%R`[/COLOR]**.wav
```

This usage of date should show something like the following:

```
andrew@skamandros~$ date +%F-%R
2009-10-17-09:13
```

but you can of course easily cook up your own variation. Not sure how this would fit in with the rest of your script though?

Andrew

---

### Post by ajgreeny on 2009-10-17
Hi again andrew.46, and thanks for trying, but unfortunately all that new version of the script does is call the new file exactly that, ie
**`date +%F-%R`.wav**
and no variable entered, so I am no further forward at the moment.  I have tried all variation of the placing of the **`date +%F-%R`** in the pathway of the output file and all seem to do the same thing, so I'll keep looking, and also try to remember to rename any files I do record before overwriting occurs

---

### Post by andrew.46 on 2009-10-17
Hi ajgreeney,

If the script is using the *literal* string I wonder if you have accidentally used the single apostrophe mark --> **[COLOR="Red"]'[/COLOR]** <-- instead of the backtick mark --> **[COLOR="Red"]`[/COLOR]** <-- underneath the Esc key? 

Andrew

---

### Post by ajgreeny on 2009-10-17
Yes, you are correct, I did use apostrophes, but changing them to the required backtick just makes mplayer bail out, ie disappear, with no error messages when the cache has filled and the file is about to be made and dumped to the chosen folder.

Thanks again for your help and interest in this, it's much appreciated.  I think I'll just have to keep looking and see if I can figure it out some other way, though I'm surprised it is not so simple that it would take just a minor change somewhere in the script for it to work as I want.

---

### Post by andrew.46 on 2009-10-17
Hi ajgreeny,

My apologies or feeding you a bit of dud advice:

> **ajgreeny said:**
> Yes, you are correct, I did use apostrophes, but changing them to the required backtick just makes mplayer bail out, ie disappear, with no error messages when the cache has filled and the file is about to be made and dumped to the chosen folder.

Normally I test every piece of syntax I recommend but not in this case where I assumed the syntax I suggested was perfectly correct. The shell was choking on the ':' character introduced by my date string. In some mortification I have gone back to the drawing board, cleaned up the date syntax and eliminated the backticks as well which have a reputation of causing confusion. The following is tested on my machine and definitely works:

```
mplayer -cache 2048 <URL> -vc null -vo null -ao pcm:fast:waveheader:file=**[COLOR="Red"]$(date +%F-%I%M).wav[/COLOR]**
```

This produces a filename similar to: 2009-10-18-1023.wav, which is YYYY-MM-DD-HHMM.wav. My apologies for not testing the original syntax properly and I hope this is now a bit more useful...

Andrew

---

### Post by ajgreeny on 2009-10-18
Hi Andrew.

No need to apologise, I assure you, I'm just so pleased that I can now record without worrying that I will lose something already recorded.  Many thanks for your time and effort spent on my behalf.  Tested and works brilliantly.  I did try to change the % variables to %D-%T, but as that puts forward slashes (/) in date part of the file name it was not successful, but that is a very minor point.

This is just one of the many things that seem to make this wonderful OS as wonderful as it is; you ask a question and most times you get an answer. You might eventually get one if you asked on a forum about Windows & its applications, but my experience of that was never as great as this, which has to be the best forum I have ever used.

Thank goodness I am now able to help other people who have queries about Ubuntu, though not perhaps quite as difficult a question as mine was.

Many thanks again.

---

