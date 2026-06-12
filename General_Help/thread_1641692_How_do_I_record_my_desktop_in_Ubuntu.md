---
title: "How do I record my desktop in Ubuntu?"
date: 2010-12-09
forum: General Help
---

### Post by madmax.santana on 2010-12-09
Is there any software for recording your desktop in Ubuntu?
I am not talking about a screenshot... I am talking about desktop video.

---

### Post by tajiknomi on 2010-12-09
> **madmax.santana said:**
> Is there any software for recording your desktop in Ubuntu?
I am not talking about a screenshot... I am talking about desktop video.

[SIZE=2]In my opinion , ***gtk-recordmydesktop*** is best for it , you can install it via ***software-center***[/SIZE].

[SIZE=2]Moreover, if you want more to test others > [/SIZE][http://www.linux.com/archive/feature/141593](http://www.linux.com/archive/feature/141593)

---

### Post by madmax.santana on 2010-12-09
Thanks a lot.
I chose gtk-recordmydesktop above all. XVidCap ended second. But I need one with the ability to zoom in and out while creating video... With the above mentioned tools, if I resize the capture window the resulting video is smaller (or larger) than the resolution I want.
Is there such a tool? What do those guys on Youtube use to create tutorials and stuff?

---

### Post by HermanAB on 2010-12-09
Also try Istanbul.

---

### Post by tajiknomi on 2010-12-09
> **madmax.santana said:**
> Thanks a lot.
I chose gtk-recordmydesktop above all. XVidCap ended second. But I need one with the ability to zoom in and out while creating video... With the above mentioned tools, if I resize the capture window the resulting video is smaller (or larger) than the resolution I want.
Is there such a tool? What do those guys on Youtube use to create tutorials and stuff?

[SIZE=2]I don't know about the Zoom-in feature in that, but you can do it another way >via Compiz...check out the attached pic,

In addition, if you desire to upload video to youtube and you are going to take recording via record-my-desktop, the output formate will be [I].ogv
You can convert it to .avi by the following command
[/I][/SIZE]```
[SIZE=3]mencoder foo.ogv -o foo.avi -oac mp3lame -lameopts fast:preset=standard -ovc lavc -lavcopts vcodec=mpeg4:vbitrate=4000
[/SIZE]
```

[SIZE=2]1st of all , paste your .ogv file in Home-directory with the name "foo",because in the above "code" the input & output are named both as "foo"... and then run the following command in terminal, it will Convert that to .avi and you can then upload it to youtube.
[/SIZE]

---

