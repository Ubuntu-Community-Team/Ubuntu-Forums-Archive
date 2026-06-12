---
title: "Youtube Downloader issue"
date: 2010-12-20
forum: General Help
---

### Post by DavidG24 on 2010-12-20
Hi guys,

Recently the Youtube Downloader plugin for Mozilla, Chrome have not been working for me as is a the native command line youtube-dl app. I'm assuming its either (1) something to do with my internet conf or (2) youtube has changed something to render those plugins useless at present (less likely I know).

Anyways I've scoured the net trying to find new youtube downloader apps that I can use and found this one :

[http://youtubedownload.altervista.org/](http://youtubedownload.altervista.org/)

Now when I installed it via wine it required VB Runtime 6 + Adobe Flash for windows, which was simple enough via winetricks.

So the installation went fine. The problem arose when I tried to run the application. After you enter a url for a youtube clip wine crashes out. I rattled my brain for a couple of hours trying to get it to work and thought I would test it out on a virtual windows xp (running through virtual box). I believe I have found the source of the problem, once you have inputed a youtube url and click 'Download' it opens a windows file navigator to select the destination to install...which I'm not sure works directly in wine...

Does anyone have any ideas on how to overcome this? is there a simple conf to allow for a windows file navigator?

Cheers

David

---

### Post by BbUiDgZ on 2010-12-20
I noticed my youtube downloader for firefox stopped working lastweek.
I think youtube have changed the site

---

### Post by ajgreeny on 2010-12-20
I've just tried the Firefox add-on called Download-helper, which used to work, but that is not working now either, so I can only assume youtube has made changes to its flash videos which prevent this.

I also looked in /tmp while the video was playing in the flash plugin, and it does not appear there either, which is unusual for streamed flash, or any other video types.

I suspect it is no longer possible to download some if not all youtube videos.

---

### Post by s.fox on 2010-12-20
From the [Youtube Terms of Service]("http://www.youtube.com/t/terms"):

> You agree not to access Content or any reason other than your personal,  non-commercial use solely as intended through and permitted by the  normal functionality of the Service, and solely for Streaming.  "Streaming" means a contemporaneous digital transmission of the material  by YouTube via the Internet to a user operated Internet enabled device  in such a manner that **the data is intended for real-time viewing and not  intended to be downloaded** (either permanently or temporarily), copied,  stored, or redistributed by the user.

Thread Closed.

---

