---
title: "Capturing command output response"
date: 2011-08-05
forum: General Help
---

### Post by Kissell on 2011-08-05
Okay, so I run a 3rd party command line utility and it works fine, but sometimes it says "Error blah blah blah... Connection timed out"

I want to script this utility, but I need to not execute the commands in the script if it gives me that connection timeout error.  

Can someone help me with the bash code to capture that response from the utility?  Something along the lines of:

> 
#!/bin/bash

3rdpartyutil > /tmp/temp.txt

if [ ! -f /tmp/temp.txt]; then
  echo no error, run whatever you need to man
fi
rm /tmp/temp.txt


Unfortunately, that doesn't work because the utility outputs non-error information to the screen even when it is successful, so it always outputs something, I never need to see it, but I do need to be able to act upon if some of that text says "error" or "connection timed out":confused:

---

### Post by dandnsmith on 2011-08-05
You could grep the file for the specific text, but first you need to know whether it will be captured for the test (you may need to modify the script to capture stderr as well as stdout - I'm weak on this, and haven't the requisite info to hand, I'm afraid)

---

### Post by sisco311 on 2011-08-05
If it's a well written utility, then in case of an error should quit with a non-zero exit status.
```
command || exit 1
```

---

### Post by Kissell on 2011-08-05
thanks, i'll have to give that a try.

I found another workaround by using wget to fetch a file from a webserver at the other site and then testing for the existence of that file, it at least makes sure the link is up a few seconds before the utility tries to run, should solve my problem...  the site link has been unreliable recently and so have the servers on the other end, something's always down these days, so what used to be something I scripted and forgot about forever has become a hassle lately "why didn't that work, i added correction for their server being down...  you gotta be kidding, now the site link is down"  hence the need to add in some error protection.  It seems I can't blindly rely on everyone else anymore.  But thankfully the people on this site are really helpful.

I need to go back and get a book on scripting and go through it, its been a long time...  there should be some sort of way to capture the stdout or something like that if I recall.  Might as well keep beating the horse, this is stuff I shouldn't have forgotten in the first place.

---

