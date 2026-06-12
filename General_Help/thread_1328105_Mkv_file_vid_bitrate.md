---
title: "Mkv file vid bitrate"
date: 2009-11-16
forum: General Help
---

### Post by satish_j on 2009-11-16
Is there anyway to find the video bitrate used by mkv file???

---

### Post by arnab_das on 2009-11-16
[LEFT][http://mediainfo.sourceforge.net/en/Download/Ubuntu](http://mediainfo.sourceforge.net/en/Download/Ubuntu)

install the app by first locating ur ubuntu edition and then installing all downloading all the files under the category.

remember, install **libzen0, libmediainfo0, GUI** necessarily in that order!

after the complete installation of all the three files just locate ur mkv file, right click on it and open it with mediainfo. 

thats it! :)
[/LEFT]

---

### Post by 3rdalbum on 2009-11-16
Right-click the file, choose Properties, and then click on the Audio/Video tab. If the bitrate can be detected by Gstreamer, then it will be shown here.

---

### Post by satish_j on 2009-11-16
Thanks for the link..i will try it..

---

### Post by satish_j on 2009-11-17
Frnds,iam facing a peculiar issue with mkv to avi conversion.The video and audio duration of avi file created by converter are not same.Video duration is actually twice that of audio duration,whereas audio duration is ok.This increase is causing the size of avi file to 2.2GB,whereas the original mkv file size is around 400MB.
Can anyone explain me what is the cause of this aud and vid duration difference??

---

### Post by arnab_das on 2009-11-17
> **satish_j said:**
> Frnds,iam facing a peculiar issue with mkv to avi conversion.The video and audio duration of avi file created by converter are not same.Video duration is actually twice that of audio duration,whereas audio duration is ok.This increase is causing the size of avi file to 2.2GB,whereas the original mkv file size is around 400MB.
Can anyone explain me what is the cause of this aud and vid duration difference??

its better to start another thread on this.

btw, have you solved your video bitrate issue? if yes, do plz mark this thread as solved.

---

### Post by satish_j on 2009-11-18
Well,i used the tool and it gave me the _average_ bitrate of mkv file.I guess may be it is due to matroska codec that is is not showing vid bitarate separately.
For the new issue,you are right.I should open a new thread..

---

