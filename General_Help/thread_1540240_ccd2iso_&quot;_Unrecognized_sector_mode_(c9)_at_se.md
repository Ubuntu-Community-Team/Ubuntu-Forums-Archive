---
title: "ccd2iso &quot; Unrecognized sector mode (c9) at sector 0! &quot;"
date: 2010-07-27
forum: General Help
---

### Post by krizanand on 2010-07-27
[FONT="Arial"]Hello guys good day.
                     Title says it all, I get that "un..." when trying to convert an .img file to .iso, am I doing anything wrong here?. Any help would be much appreciated as I am very new to Ubuntu. I am running Lucid Lynx on my laptop. 

Thanks for all your replies.
[/FONT]

---

### Post by AceofAzrogoth on 2010-09-20
I've been having the same problem, and after searching around it seems that converting a "multiple-session" disc does not work yet in ccd2iso, causing an "Unrecognized sector mode" error so I think we are out of luck.:(

---

### Post by MrSnowmiss on 2011-01-29
When trying to convert an .img to .iso I experience almost the same error.

Here it says: Unrecognized sector mode (**0**) at sector 0!

So I just bumped this topic, to see if anyone found solutions yet ;)

---

### Post by sepo on 2011-04-28
You can try with bchunk:

```
sudo apt-get install bchunk
```then

```
bchunk <image.img> <image.cue> <outfile>
```

---

