---
title: "Timed sound recording"
date: 2005-02-21
forum: General Help
---

### Post by mtyndall on 2005-02-21
I'd like to use my Ubuntu PC as an audio time-shifter, ie to record stuff from the line-in (connected to a radio) while I'm away from it.

My first thought was to use **cron** and run a command from there, but AFAICT **Sound Recorder** can't be driven from the CLI.

My next thought was to use **oggenc** to record directly from the line-in, but I got frightened off by the number of entries in /dev/.  I still think this is a go-er, but this is where I'd like a bit of guidance.

Can I access my line-in from /dev/?

[list]
[*]Where would I find it?
[*]Is it dependent on my hardware -- a Via Epia M6000 which Ubuntu 4.10 is happy to use (installed without problems)?
[*]Is it a good idea?
[/list] 

A final question arises, that of stopping the recording at the end.  Another entry in **cron** to kill the recording process?

Or am I missing something incredibly easy, like Messer ([http://www.dago.pmp.com.pl/messer/](http://www.dago.pmp.com.pl/messer/)) for windows?

---

### Post by nemin on 2005-02-21
[QUOTE=mtyndall]I'd like to use my Ubuntu PC as an audio time-shifter, ie to record stuff from the line-in (connected to a radio) while I'm away from it.
[/QUOTE]
I guess you might find the "rec" command usefull. I don't know much about it, but I think it could be usefull. I justed googled for "linux schedule recording" and terms like that and a lot of prebuilt scripts and further explaination appeared, like this one for example: [http://gary.burd.info/2003/07/time-shifting-fm-radio.html](http://gary.burd.info/2003/07/time-shifting-fm-radio.html). You'll probably need to change it a bit to fit your needs.
Good luck.

---

### Post by mtyndall on 2005-02-22
[QUOTE=nemin]I guess you might find the "rec" command usefull. I don't know much about it, but I think it could be usefull.[/QUOTE]
Thanks.  I had a look round in the interim, and it seems that SoX (which contains rec) is certainly useful.  I found the Linux Radio Timeshift HOWTO ([http://osl.iu.edu/~tveldhui/radio/](http://osl.iu.edu/~tveldhui/radio/)) which is linked from the URL you posted; the scripts provided there get round the problem of how to stop recording (the script sleeps for the appropriate length of time and kills the PID created earlier).

However, I may be able to get there without SoX.  I played about with oggenc last night, and it was happy to record from /dev/dsp using (something like, this is from memory)
```
oggenc -q 6 -r --output=foo.ogg /dev/dsp
```
Unfortunately, the output, while a valid Ogg file, was just pops and squeaks; this leads me to believe that I've got a mismatch between the format of /dev/dsp and what oggenc expects in raw mode (-r), which is 2-channel 16bit 44.1 kHz audio.

Onwards and upwards...

---

