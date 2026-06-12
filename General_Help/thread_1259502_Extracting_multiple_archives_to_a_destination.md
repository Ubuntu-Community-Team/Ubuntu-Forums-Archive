---
title: "Extracting multiple archives to a destination"
date: 2009-09-06
forum: General Help
---

### Post by second.exodous on 2009-09-06
I'm backing up multiple DVDs and extracting the .iso images to another folder where I can encode them with Handbrake.  So in one external HD I copy the DVD's and then want to extract them to another HD.

File roller wants to open a new 'instance' with every DVD, I think it would be easier to do it through the command line but can't really find any how-tos to do this.  I want to do something like this:

```
cd /media/mediawithisofiles
extract --verbose one.iso two.iso three.iso /media/externalHD
```

And then go to /media/externalHD and have a folders one, two, three with /video_ts and /audo_ts in them.  Does this make sense?  I always have trouble explaining things like this.  File Roller just doesn't seem to cut it in in the command line.

I'm doing this to like 20 iso images at a time, hence the need to do this through the terminal.  I have them all ripped, but Handbrake wants me to extract them, it can't work with iso images.

---

