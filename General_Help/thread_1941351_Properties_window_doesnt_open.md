---
title: "Properties window doesnt open"
date: 2012-03-15
forum: General Help
---

### Post by mayur.shetye on 2012-03-15
Hi! 
I use Ubuntu 11.10.When I right click on a flv video file and go to properties it does'nt open.It gives the message "**Creating properties window" - 'You can stop this operation by clicking cancel'.** For other files and video types the properties window opens.Also,I am able to play flv videos in VLC and even in Movie Player.

---

### Post by TeoBigusGeekus on 2012-03-15
Must be a nautilus thing, I don't know.
Alternatively, you could use the file command
```
file /path/name.flv
```
or, even better, ffmpeg to get more info
```
ffmpeg -i /path/name.flv
```

---

### Post by mayur.shetye on 2012-03-16
Hi! I used both the commands given above but I cannot understand what they are used for.I mean,ffmpeg does give information of the flv file.But it would be better if it was possible to fix this bug somehow. :)

---

