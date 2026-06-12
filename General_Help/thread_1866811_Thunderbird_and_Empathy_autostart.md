---
title: "Thunderbird and Empathy autostart?"
date: 2011-10-22
forum: General Help
---

### Post by paperclip on 2011-10-22
I'm not sure if this is a bug, but I feel like once configured Thunderbird and Empathy should launch in the background when a user logs in.  At the very least there should be an option somewhere.

I've enabled this for Empathy with
```
/usr/bin/empathy -h
```
in the Startup Applications menu.

Is there a similar command line option to launch Thunderbird in the background?

---

### Post by paperclip on 2011-10-22
This is something like what I am looking for, but I'd rather have Thunderbird start minimized.

[http://superuser.com/questions/298795/start-thunderbird-in-the-background-to-fetch-email-and-close-it-a-few-minutes-la](http://superuser.com/questions/298795/start-thunderbird-in-the-background-to-fetch-email-and-close-it-a-few-minutes-la)

Also Alltray doesn't seem to work with AppIndicators.
[https://bugs.launchpad.net/alltray/+bug/812068](https://bugs.launchpad.net/alltray/+bug/812068)

---

### Post by paperclip on 2011-10-23
Well.. no obvious solution.. Since we're using google apps company wide.  I've simply installed gm-notify and blacklisted thunderbird (and gwibber) on the messaging menu.

Wish I could figure out a simple way to push those changes to my users.. *sigh*

---

