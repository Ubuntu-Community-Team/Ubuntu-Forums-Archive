---
title: "Some help/Questions"
date: 2010-08-07
forum: General Help
---

### Post by zelcrim on 2010-08-07
Okay, So theres a few questions i have (i JUST installed ubuntu)

1.) On Kdenlive, i used gtk-recordmydesktop to record videos, but on kdenlive i cant get a preview box, its just audio. and some wierd distorted thing like lots of different colors messed up.

2.) similar to question 1, if i have a video i want to upload to youtube, its either all green, black, or distorted colors. (I've read i need codecs, which ones?)

3.) I want some really cool things to use ubuntu for, as wierd as that sounds, before  i had a dock but i thought that it looked way too much like mac and i didnt want to use it. anything similar to this? How about some ubuntu-only features i dont know about. I already know about the toolbar at the top and stuff, and also, i already know compiz 


:popcorn::popcorn::popcorn::popcorn:So cmon you ubuntu guys, help me. :popcorn::popcorn::popcorn::popcorn:

---

### Post by Ozymandias_117 on 2010-08-07
> **zelcrim said:**
> Okay, So theres a few questions i have (i JUST installed ubuntu)

1.) On Kdenlive, i used gtk-recordmydesktop to record videos, but on kdenlive i cant get a preview box, its just audio. and some wierd distorted thing like lots of different colors messed up.

2.) similar to question 1, if i have a video i want to upload to youtube, its either all green, black, or distorted colors. (I've read i need codecs, which ones?)

3.) I want some really cool things to use ubuntu for, as wierd as that sounds, before  i had a dock but i thought that it looked way too much like mac and i didnt want to use it. anything similar to this? How about some ubuntu-only features i dont know about. I already know about the toolbar at the top and stuff, and also, i already know compiz 


:popcorn::popcorn::popcorn::popcorn:So cmon you ubuntu guys, help me. :popcorn::popcorn::popcorn::popcorn:

Have you installed the ubuntu-restricted-extras package? ```
sudo aptitude install ubuntu-restricted-extras
```

It gives you support for all the media types that Ubuntu doesn't support out of the box.

---

### Post by zelcrim on 2010-08-07
Thanks :) Didnt know. 


(BTW...Nice avatar, i play halo 3 too :D only i got recon, xD.  GT - toXic craZe)

---

### Post by Ozymandias_117 on 2010-08-07
> **zelcrim said:**
> Thanks :) Didnt know. 


(BTW...Nice avatar, i play halo 3 too :D only i got recon, xD.  GT - toXic craZe)

Really old pic :D I don't like the new background Bungie uses for avatars on their site, so I've stuck with this one.

---

### Post by zelcrim on 2010-08-07
Oh, haha.

---

### Post by lovinglinux on 2010-08-07
> **zelcrim said:**
> 2.) similar to question 1, if i have a video i want to upload to youtube, its either all green, black, or distorted colors. (I've read i need codecs, which ones?) 

This is a known issue with ogv videos and recordmyDesktop. You need to convert the videos to another format like avi before uploading. You can use mencoder to do that:

```
mencoder source.ogv  -o output.avi -oac mp3lame -lameopts fast:preset=standard -ovc lavc -lavcopts vcodec=mpeg4:vbitrate=4000
```

---

