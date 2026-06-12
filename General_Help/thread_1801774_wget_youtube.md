---
title: "wget youtube"
date: 2011-07-11
forum: General Help
---

### Post by spilner on 2011-07-11
hi,i download direct link from youtube by using wget.it isnt working.
can someone help?

example : wget "youtube directlink"

thanks

---

### Post by lovinglinux on 2011-07-11
I suppose you need the original video url, which is not the address you see in the address bar when viewing a video.

You could try youtube-dl package.

Personally, I prefer an add-on like Video [Download Helper]("https://addons.mozilla.org/en-US/firefox/addon/3006/").

---

### Post by spilner on 2011-07-11
> **lovinglinux said:**
> I suppose you need the original video url, which is not the address you see in the address bar when viewing a video.

You could try youtube-dl package.

Personally, I prefer an add-on like Video [Download Helper]("https://addons.mozilla.org/en-US/firefox/addon/3006/").

im running it through server.im doin it via ssh.

i use idm to get the original download link.

youtube link example [http://www.youtube.com/watch?v=KlyXNRrsk4A](http://www.youtube.com/watch?v=KlyXNRrsk4A)

below is the original download link

```
http://v15.lscache7.c.youtube.com/videoplayback?sparams=id%2Cexpire%2Cip%2Cipbits%2Citag%2Cratebypass%2Coc%3AU0hQRVRMTl9FSkNOMF9MRlJJ&fexp=907062&itag=37&ip=0.0.0.0&signature=48789770F2AA04A9E1D714ECB1BCF7C6CFB283B5.82DC9145940E359BEB157A0EFE813B518F0C228E&sver=3&ratebypass=yes&expire=1310410800&key=yt1&ipbits=0&id=2a5c97351aec9380&ptchn=KatyPerryVEVO&ptk=vevo
```i try wget the above original link but it doesnt work.

i get

```

[1] 7277
[2] 7278
[3] 7279
[4] 7280
[5] 7281
[6] 7282
[7] 7283
[8] 7284
[9] 7285
[10] 7286
[11] 7287
[12] 7288
[2]   Done                    fexp=907062
[3]   Done                    itag=37
[4]   Done                    ip=0.0.0.0
[5]   Done                    signature=48789770F2AA04A9E1D714ECB1BCF7C6CFB283B5.82DC9145940E359BEB157A0EFE813B518F0C228E
[6]   Done                    sver=3
[7]   Done                    ratebypass=yes
[8]   Done                    expire=1310410800
[9]   Done                    key=yt1
[10]   Done                    ipbits=0

           => `videoplayback?sparams=id,expire,ip,ipbits,itag,ratebypass,oc:U0hQRVRMTl9FSkNOMF9MRlJJ'
Resolving v15.lscache7.c.youtube.com... 208.117.224.99
Connecting to v15.lscache7.c.youtube.com|208.117.224.99|:80... connected.
HTTP request sent, awaiting response... 400 Bad Request
14:40:57 ERROR 400: Bad Request.


[1]   Exit 1                  wget http://v15.lscache7.c.youtube.com/videoplayback?sparams=id%2Cexpire%2Cip%2Cipbits%2Citag%2Cr
atebypass%2Coc%3AU0hQRVRMTl9FSkNOMF9MRlJJ
[11]-  Done                    id=2a5c97351aec9380
[12]+  Done                    ptchn=KatyPerryVEVO


```

do i need to install somethin to download the youtube video?

---

### Post by lovinglinux on 2011-07-11
> **spilner said:**
> im running it through server.im doin it via ssh.

i use idm to get the original download link.

youtube link example [http://www.youtube.com/watch?v=KlyXNRrsk4A](http://www.youtube.com/watch?v=KlyXNRrsk4A)

below is the original download link

```
http://v15.lscache7.c.youtube.com/videoplayback?sparams=id%2Cexpire%2Cip%2Cipbits%2Citag%2Cratebypass%2Coc%3AU0hQRVRMTl9FSkNOMF9MRlJJ&fexp=907062&itag=37&ip=0.0.0.0&signature=48789770F2AA04A9E1D714ECB1BCF7C6CFB283B5.82DC9145940E359BEB157A0EFE813B518F0C228E&sver=3&ratebypass=yes&expire=1310410800&key=yt1&ipbits=0&id=2a5c97351aec9380&ptchn=KatyPerryVEVO&ptk=vevo
```i try wget the above original link but it doesnt work.

i get

```

[1] 7277
[2] 7278
[3] 7279
[4] 7280
[5] 7281
[6] 7282
[7] 7283
[8] 7284
[9] 7285
[10] 7286
[11] 7287
[12] 7288
[2]   Done                    fexp=907062
[3]   Done                    itag=37
[4]   Done                    ip=0.0.0.0
[5]   Done                    signature=48789770F2AA04A9E1D714ECB1BCF7C6CFB283B5.82DC9145940E359BEB157A0EFE813B518F0C228E
[6]   Done                    sver=3
[7]   Done                    ratebypass=yes
[8]   Done                    expire=1310410800
[9]   Done                    key=yt1
[10]   Done                    ipbits=0

           => `videoplayback?sparams=id,expire,ip,ipbits,itag,ratebypass,oc:U0hQRVRMTl9FSkNOMF9MRlJJ'
Resolving v15.lscache7.c.youtube.com... 208.117.224.99
Connecting to v15.lscache7.c.youtube.com|208.117.224.99|:80... connected.
HTTP request sent, awaiting response... 400 Bad Request
14:40:57 ERROR 400: Bad Request.


[1]   Exit 1                  wget http://v15.lscache7.c.youtube.com/videoplayback?sparams=id%2Cexpire%2Cip%2Cipbits%2Citag%2Cr
atebypass%2Coc%3AU0hQRVRMTl9FSkNOMF9MRlJJ
[11]-  Done                    id=2a5c97351aec9380
[12]+  Done                    ptchn=KatyPerryVEVO


```

do i need to install somethin to download the youtube video?

I suppose it could be a cookie issue. I develop an extension, called FlashVideoReplacer, that gets the url from YouTube and replace the video with the original source using a different video object, so you can play without flash. The extension also offers the possibility of opening the video with an external player. When opening with an external player, I need to programatically delete a YouTube cookie before fetching the real video url, otherwise the signature comes with a different value and the url doesn't work.

---

