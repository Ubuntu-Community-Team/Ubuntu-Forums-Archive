---
title: "Best Recording Application?"
date: 2011-10-25
forum: General Help
---

### Post by dave2001 on 2011-10-25
I am interested in recording audio as close to the soundcard as I can. That way the "source" of the recorded audio doesn't really matter, and one recording application will do any job I'd like it to. This has become impossible with recent versions of Windows due to overzealous worries about copyright infringement.

So (of course) I've come looking for a solution in the Linux world. I'm just not sure where to start. Any suggestions for a good audio recording application? 

I am looking for: 
-The ability to record ANY audio processed by the soundcard.
-The ability to record in multiple audio formats, both lossless and lossy
-A "smart" recording ability which will auto-shutoff or at least auto file-split upon silence.

Any suggestions or thoughts appreciated!

---

### Post by oldtimer7777 on 2011-10-25
I have a soundcard that is supported in Ubuntu and I use Audacity for everything. 

To install the latest version:

```
sudo add-apt-repository ppa:audacity-team/daily 
sudo apt-get update 
sudo apt-get install audacity lame libmp3lame0
```

Make sure you install the rest of the codecs you will need too:

[https://debianhelp.wordpress.com/2011/09/12/to-do-list-after-installing-ubuntu-11-10-aka-oneiric-ocelot/](https://debianhelp.wordpress.com/2011/09/12/to-do-list-after-installing-ubuntu-11-10-aka-oneiric-ocelot/)

Ubuntu Studio for 11.10 should be able to handle what you want to do very well.

> **dave2001 said:**
> I am interested in recording audio as close to the soundcard as I can. That way the "source" of the recorded audio doesn't really matter, and one recording application will do any job I'd like it to. This has become impossible with recent versions of Windows due to overzealous worries about copyright infringement.

So (of course) I've come looking for a solution in the Linux world. I'm just not sure where to start. Any suggestions for a good audio recording application? 

I am looking for: 
-The ability to record ANY audio processed by the soundcard.
-The ability to record in multiple audio formats, both lossless and lossy
-A "smart" recording ability which will auto-shutoff or at least auto file-split upon silence.

Any suggestions or thoughts appreciated!

---

