---
title: "how to download videos from you tube"
date: 2009-07-06
forum: General Help
---

### Post by roquin on 2009-07-06
Hi, guys. I'm new in ubuntu (9.04)  and im trying download videos from youtube but  the browser does not give the options, i can't download any videos as i could in window with internet Explorer. Does any body can help please. thanks

---

### Post by Jesus_Valdez on 2009-07-06
In order to download videos from youtube I use youtube-dl
In terminal:
```
sudo apt-get install youtube-dl
```

then just 
```
 youtube-dl httpblabla.youtube.com/jadajadjad
```

Downloads the video to the home folder.

Other option is check out the tutorial on the proper section within forum where theres tons of other options.

---

### Post by Bigtime_Scrub on 2009-07-06
Getting youtube videos in Linux is very easy, it is just a little different than windows.

If you want to save a youtube video. 

Let the video finish loading all the way. Minimize Firefox.

Then go to

Places -> Computer -> Filesystem -> TMP

Look for a flash video in there and drag it to your desktop. Change the name to whatever you like and thats it!

---

### Post by Bradj47 on 2009-07-06
[http://ubuntuforums.org/showthread.php?t=1203901](http://ubuntuforums.org/showthread.php?t=1203901)

---

### Post by kuldeepsidhu on 2009-07-06
you can insatll firefox addon "easy youtube downloader"..it is easy to insatll..you can downlaod videos in mp4,HD format with only single click.....

---

### Post by Ra-Hoor-Khuit on 2009-07-06
Get the **Video DownloadHelper** plugin for Firefox.  

With well over forty-two MILLION downloads it must be doing something right.

[https://addons.mozilla.org/en-US/firefox/addon/3006](https://addons.mozilla.org/en-US/firefox/addon/3006)

---

### Post by dhughes on 2009-07-06
The easiest way is to use pwnyoutube just put the letters pwn in front of youtube in any url of any youtube video, couldn't be easier.

---

### Post by JimBuntu on 2009-07-24
just used both the clik and drag method and the youtube-dl both worked but I'm wondering what the point is with the slower youtube-dl if you can just go to the tmp folder and drag the vid to desktop? anyone?

---

### Post by Bigtime_Scrub on 2009-07-24
> **JimBuntu said:**
> just used both the clik and drag method and the youtube-dl both worked but I'm wondering what the point is with the slower youtube-dl if you can just go to the tmp folder and drag the vid to desktop? anyone?

Because you can use youtube-dl from the command line and sometimes if you are not in a gui (for example you are using a server) you can still snatch up the video.

---

