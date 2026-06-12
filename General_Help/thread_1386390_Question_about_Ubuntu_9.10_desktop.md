---
title: "Question about Ubuntu 9.10 desktop"
date: 2010-01-20
forum: General Help
---

### Post by cdanderson04 on 2010-01-20
Hey all:

I am recent converter to Ubuntu and I am enjoying it. I screwed up my computer once though, but I plead ignorance.

My question is:

I like how Ubuntu has the multiple desktop thing by default. I have software that I want to start on startup but I usually put them on different desktops. Is there a way to have them start on a certain desktop? Example is that I use 4 desktops and one is for email, can I have Thunderbird open on Desktop 4?

Thanks in advance.

---

### Post by zollie on 2010-01-20
```
thunderbird --help
Usage: /usr/lib/thunderbird/thunderbird-bin [ options ... ] [URL]
       where options include:

X11 options
        **--display=DISPLAY **              X display to use

```

So.  :0.0 is your primary desktop.  :0.1 is the secondary.

you would then run

--display=:0.1 to point to the 2nd desktop.

---

### Post by paradox_qu on 2010-01-20
Thanks that is great.  I was wondering that too.

---

### Post by cdanderson04 on 2010-01-20
Thank you very much!  Is this just native to Thunderbird or could I use that with any program?

---

### Post by zollie on 2010-01-20
> **cdanderson04 said:**
> Thank you very much!  Is this just native to Thunderbird or could I use that with any program?

no, not with ANY program **natively** but most do support this functionality.

both tbird and firefox support it.  

HOWEVER.  You can manipulate the $DISPLAY environment variable BEFORE you launch an Xwindows application to set it to suit your needs and in that case, yes -- ALL X11 application will conform.  Messing with $DISPLAY env var quickly gets to be a pain in the ***, however as the setting from the command line would apply for all subsequently launched applications.

You would need to wrap this sequence in a shell script to set the $DISPLAY to a new setting and then launch your program.  Then it would apply to just this instance.

---

### Post by lidex on 2010-01-20
Or you can use compiz to place the windows for you. WFM.
Some links to explain:
[http://www.5min.com/Video/How-to-Place-Windows-in-Compiz-Fusion-161769731]("http://www.5min.com/Video/How-to-Place-Windows-in-Compiz-Fusion-161769731")
[http://www.go2linux.org/forums/installing-and-using-compiz-on-ubuntu-t-9.html]("http://www.go2linux.org/forums/installing-and-using-compiz-on-ubuntu-t-9.html")
[http://wiki.compiz.org/Plugins/Place]("http://wiki.compiz.org/Plugins/Place")

---

### Post by arvevans on 2010-01-20
Zollie

Good info...but I put this in _System/Preferences/Startup Applications_ under Firefox

    "firefox --display=:0.7"

rebooted, and it did not work.

I'll try the scripting thing next.

Thanks,

Arv
_._

---

