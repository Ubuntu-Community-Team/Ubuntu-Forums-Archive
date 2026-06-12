---
title: "Crontab in Ubuntu Server with ESpeak"
date: 2011-04-25
forum: General Help
---

### Post by GraysonPeddie on 2011-04-25
I have this in cron as root for testing only:

```
* * * * * (echo it is now;date +%I:%M%p )|espeak --stdout|sox -q -V0 -t wav - -
```

...but it's not working

I am running Ubuntu Server 10.04 and ALSA is already installed. Plus, my speakers are connected to my sound card and I can test my speakers by executing as root:

```
espeak "This is a test."
```

That is working, but in cron, it does not, even as root.

Is there a way to work around my problem? I'm going to set the task to run every hour once it's working, but right now, it's not.

Update: I find a way to get espeak to work with cron. First, when I did:

```
*/1 * * * * espeak "This is a test."
```

ESpeak speaks every minute.

But if I do this:

```
*/1 * * * * espeak "The time is $(date '+%l %p')."
```

It won't work. So, I created a script that is located in /fileserver/shell_scripts/, chmod a+x, and then put the path containing a script in crontab, like so:

```
0 * * * * /fileserver/shell_scripts/saytime
```

saytime:

```
#!/bin/bash
# Say time
DATE=$(date '+%l %p')
padsp espeak "The time is $DATE";
```

And now it works! :)

I don't know why espeak won't speak if there's a $(date '+%l %p') within quotes in my crontab, though.

---

