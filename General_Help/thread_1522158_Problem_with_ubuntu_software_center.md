---
title: "Problem with ubuntu software center"
date: 2010-07-01
forum: General Help
---

### Post by N8JDR-HAM on 2010-07-01
Before anyone says "I'm bashing the software center", I'm not. I just had been doing a bit of a download frenzy of software for both ham radio applications (as I am president of the radio club and we have ubuntu on our new machine ... err ... Win 2000-era new machine ... better than one from the days of 8-inch floppies and cassettes for storage) and engineering applications so we can use the computer for homework as well. Either way, one of the files I had tried to download apparently had some sort of download issue. 

[SIZE=2]Long story short, it seems every time I attempt to download something else, it gives an error that reads 

"**The package system is broken:** Check if you are using third party repositories. If so disable them, since they are a common source of problems.
Furthermore run the following command in a Terminal: apt-get install -f ......

under details, each time, it gives the same file: cjinfilter-common"[/SIZE]

The error message, and file under details, are all the same, regardless of what file I am actually trying to download. Using terminal/apt-get install *filename* gives the same error and same result, as well as the same culprit; cjinfilter-common. Tried restarting, hoping that might somehow reset this thing, but it still gives the same error. I know I fixed it before by resetting something, or something of that sort, but sadly I cannot remember anymore what I had done. Figured this is probably a common issue (as, in 6 months as a linux/ubuntu user, this has happened several times) and I hoped someone might know the fix for this.

THANKS ALL, and 73's

 - N8JDR

---

### Post by cariboo on 2010-07-01
Try using Synaptic's broken package filter to remove it. That is one of the capabilities that the Software Center doesn't have yet.

---

### Post by N8JDR-HAM on 2010-07-02
> **cariboo907 said:**
> Try using Synaptic's broken package filter to remove it. That is one of the capabilities that the Software Center doesn't have yet.

It couldn't be that simple, could it??? Wait ... it was. :p

Thanks!

 - N8JDR

---

### Post by axrl on 2010-08-26
Hi, 

I had the same problem since some days.

Thank you for the solution..  It worked fine !

Axrl

---

