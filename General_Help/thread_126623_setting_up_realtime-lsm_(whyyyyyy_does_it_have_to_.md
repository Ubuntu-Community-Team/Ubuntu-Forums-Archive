---
title: "setting up realtime-lsm (whyyyyyy does it have to be so hard?)"
date: 2006-02-07
forum: General Help
---

### Post by jmxhgyZN8wK7 on 2006-02-07
i finally figured out why qjackctl wouldn't launch jack when i selected realtime - apparently, i needed to get realtime-lsm.

so, after much googling, i found [this page]("http://fort.xdas.com/~kor/oss2jack/install.html") and followed the directions:

```
sudo apt-get install linux-headers-2.6.12-9-386
``` (it responded with "linux-headers-2.6.12-9-386 is already the newest version.")

```
sudo apt-get install module-assistant
```

```
sudo module-assistant
```

update menu, prepare menu, blah blah blah...

...the first problem came when i went to the "select" menu and couldn't find realtime-lsm.  after a little more googling, i decided to do

```
sudo apt-get install realtime-lsm-source realtime-lsm
```

then i restarted module-assistant, and realtime-lsm was there!  i checked it and went on to the next step.  "get" finished without incident, but when i picked "build," i got a message that said

"The source package may not to be installed. Would you"

(yes, that is what it said, word for word.)

so i picked yes, and after a few scrolling lines and a little progress bar, it stopped and gave me

"Build of the package realtime-lsm-source failed! How do you wish to proceed?
[LIST]
[*]Examine the build file
[*]Skip and continue with the next operation
[*]Stop processing the build commands"
[/LIST]

so now i'm stuck.  can any of you linux wizards help me?  :(   (i'm using breezy, by the way.)

---

### Post by joft on 2006-02-07
Hi,

I'm not sure, but maybe you don't have the right gcc installed. Breezy's linux-image-2.6.12-9-* uses gcc-3.4 . But the build-essentials in breezy depend on gcc-4.0 (module-assistant depends on build-essentials).

So try again after doing:

```
apt-get install gcc-3.4
```

Did you "Examine the build file"?

BTW: Last week I noticed that, too, while writing this step by step HOWTO:
[http://www.ubuntuforums.org/showpost.php?p=695990&postcount=6](http://www.ubuntuforums.org/showpost.php?p=695990&postcount=6)
(Look at step 3, if you like ...).

---

