---
title: "PDF viewer to play embedded videos"
date: 2010-12-12
forum: General Help
---

### Post by sylph on 2010-12-12
Hi all,

I'm currently working on a presentation using the Beamer Latex class and  I would like to embed a video in the presentation. The problem is that I  cannot seem to find a PDF viewer that allows me to play these videos.  Does anyone have any suggestions for a PDF viewer that does let me play  videos, ideally within the PDF?

I've tried using Evince and Acrobat Reader 9, but I've had issues with both.

Evince doesn't allow you to play embedded videos in the PDF, but it does  allow you to open an external media player by clicking a link. However,  this doesn't work in presentation mode, which sort of defeats what I'm  trying to do. I know a bug report has been filed on Launchpad for this  problem, but it doesn't seem to be going anywhere.

Acrobat 9 also doesn't allow me to play embedded videos. It *does* allow  me to open an external player in fullscreen mode, but the video always  opens up behind the presentation, which means I have to alt-tab to the  video. Kind of unprofessional.

 I've heard some people have had success with Okular. Can anyone confirm  this? I'd rather not have to install all the KDE dependencies only to  find Okular doesn't work :razz:

Alternatively, does anyone know of any workarounds for either the issues in Acrobat or in Evince?

Thanks for your help!

---

### Post by vladimir.v on 2011-07-25
This might be old, but... I have the same question and I still haven't found a solution. Anyone?

---

### Post by sylph on 2011-07-25
Apparently Evince has released a bug fix for this issue, but unfortunately, it doesn't seem to have trickled down to Ubuntu yet...

[https://bugs.launchpad.net/ubuntu/+source/evince/+bug/626142](https://bugs.launchpad.net/ubuntu/+source/evince/+bug/626142)

I just set up my video files to display a still in the pdf with a link to open the video using an external media player. I still haven't had an opportunity to test a recent version of Okular, so I can't confirm how it works either.

---

### Post by sevonne on 2012-08-30
Hello!
I managed to read a video embedded within a pdf file with okular.
The pdf was created with latex beamer and the video was .flv format.
I do not know if other format will be readable as well.

The only default is that the still picture that was in my presentation (i.e. the picture you click on to start the video) shows up as a black rectangle. This is a minor problem, because what I really want is the video.

---

