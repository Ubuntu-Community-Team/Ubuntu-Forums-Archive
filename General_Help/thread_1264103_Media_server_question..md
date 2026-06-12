---
title: "Media server question."
date: 2009-09-11
forum: General Help
---

### Post by Krupski on 2009-09-11
Sorry this isn't an "Ubuntu / Linux" topic... but I figure this is the best place to ask.

OK... I have a headless file server with a bunch of hard drives running Ubuntu 64 bit server in a RAID-5 configuration. Works fine.

One of the things I have stored on the server is decrypted rips of all of my DVD and Blu-Ray movies (they are all legal backups since I purchased the original disks).

Anyway, over the network I can play any movie I wish in a media player (using a PC), but what I would LIKE to to is have some kind of "box" that I can connect to my TV and view the video right on the TV without using a computer.

I imagine that there would be some kind of "menu" that I could use to browse the media content of the remote drive and select whatever media I wanted to watch.

Note that the "box" would have to connect to the media server via the ethernet network, NOT by USB.

Is there such a device available and, if so could someone point me to it?

Thanks so much!

-- Roger

---

### Post by HobbDogg on 2009-09-11
I don't know if this is much help, but the only thing that comes to mind, is a very very small computer that can run a front end that can access the media from your server. such as XBMC, mythbuntu, etc. The front end can have very very low specs because the server is playing the media. I hope it helps. :)

---

### Post by Krupski on 2009-09-11
> **HobbDogg said:**
> I don't know if this is much help, but the only thing that comes to mind, is a very very small computer that can run a front end that can access the media from your server. such as XBMC, mythbuntu, etc. The front end can have very very low specs because the server is playing the media. I hope it helps. :)

Thanks for the input. Yes that would work, but I was hoping to find a *commercially* made "box" that does what I'm looking for.

If there is no such thing... then I'll have to build my own box!  :)

Thanks!

-- Roger

---

### Post by HobbDogg on 2009-09-12
Well what about some setup like this.

HDMI: [http://www.newegg.com/Product/Product.aspx?Item=N82E16856107032]("http://www.newegg.com/Product/Product.aspx?Item=N82E16856107032")

No HDMI: [http://www.newegg.com/Product/Product.aspx?Item=N82E16856107034]("http://www.newegg.com/Product/Product.aspx?Item=N82E16856107034")

Then a very small HDD: [http://www.newegg.com/Product/Product.aspx?Item=N82E16822136099]("http://www.newegg.com/Product/Product.aspx?Item=N82E16822136099")

 Has enough space for a full/minimal install of ubuntu/fedora then a front end of your choice. boxee,xbmc,geexbox etc.

Again, hope this helps.

--hobbdogg

---

### Post by Krupski on 2009-09-12
> **HobbDogg said:**
> Well what about some setup like this.

HDMI: [http://www.newegg.com/Product/Product.aspx?Item=N82E16856107032]("http://www.newegg.com/Product/Product.aspx?Item=N82E16856107032")

No HDMI: [http://www.newegg.com/Product/Product.aspx?Item=N82E16856107034]("http://www.newegg.com/Product/Product.aspx?Item=N82E16856107034")

Then a very small HDD: [http://www.newegg.com/Product/Product.aspx?Item=N82E16822136099]("http://www.newegg.com/Product/Product.aspx?Item=N82E16822136099")

 Has enough space for a full/minimal install of ubuntu/fedora then a front end of your choice. boxee,xbmc,geexbox etc.

Again, hope this helps.

--hobbdogg

Sure, I could build a tiny PC with a solid state disk drive (or a compact flash drive) with Ubuntu on it, stick in a decent video card with an HDMI output and be all set.

As I said, I was hoping that there was a commercial version of the "box" I want available.

It might end up, though, being more fun to build one... :D

---

### Post by P4man on 2009-09-12
Bluray might be a problem, but there are a gazillion of network media players, so im sure one of them can do it

[http://www.newegg.com/Product/ProductList.aspx?Submit=ENE&N=2012810484&bop=And&SpeTabStoreType=1&ActiveSearchResult=True&Pagesize=100](http://www.newegg.com/Product/ProductList.aspx?Submit=ENE&N=2012810484&bop=And&SpeTabStoreType=1&ActiveSearchResult=True&Pagesize=100)

---

### Post by Krupski on 2009-09-12
> **P4man said:**
> Bluray might be a problem, but there are a gazillion of network media players, so im sure one of them can do it

[http://www.newegg.com/Product/ProductList.aspx?Submit=ENE&N=2012810484&bop=And&SpeTabStoreType=1&ActiveSearchResult=True&Pagesize=100](http://www.newegg.com/Product/ProductList.aspx?Submit=ENE&N=2012810484&bop=And&SpeTabStoreType=1&ActiveSearchResult=True&Pagesize=100)

Blu-ray is no problem... I decrypt the disks before I save them. They play in an ordinary media player with no decoder required.

---

### Post by StuartN on 2009-09-12
> **Krupski said:**
> I was hoping to find a *commercially* made "box" that does what I'm looking for

I have an Iomega Screenplay which is 150 dollars of 500 mb drive and remote-controlled player in a tiny black box. It plays copied DVD folders, decrypted rips, mpeg4 etc. It also displays and slide-shows photographs, plays MP3s and handles playlists of any media type. Mostly I use it for random play of music genre playlists and for watching episodes of TV series. It is NTFS-formatted and I fill it up over USB from my Linux box without any proprietary software. They do much bigger discs and HD video output now.

---

### Post by spillin_dylan on 2009-09-12
Wouldn't you just be as well off to get a HD-video card for your media server, and run a video cable straight to the TV?  Since the media server is doing all the work any how, couldn't you just run the output right from there to the display?

---

### Post by HobbDogg on 2009-09-12
@Krupski, Alright. Hey can I ask you what you used for your bluray discs? Also if all the hardware is HDCP compliant then will it be able to play bluray straight from the disc? also about how long does it take for you to decrypt the bluray disc and how big is the file?

---

### Post by Krupski on 2009-09-12
> **spillin_dylan said:**
> Wouldn't you just be as well off to get a HD-video card for your media server, and run a video cable straight to the TV?  Since the media server is doing all the work any how, couldn't you just run the output right from there to the display?

Yes I could.... but my file server is used for other things too and it's in a different room, doesn't have a large enough power supply for an HDMI compliant video card... lots of reasons.

One thing I DID just try tonight is connect my wife's laptop to the TV via the HDMI cable. It worked. I was able to connect to the file server and stream a DVD movie to the TV.

So, I know it will work.

It seems as though a commercial product such as what I'm looking for isn't available, so I might build one.

I found that NVidia makes a board called a "Mgpu" which is a motherboard with an NVidia GPU on board. All I would need to add would be some ram, a compact flash card with Linux on it and a wireless mouse.

I've been researching "HTPC" (home theater PC) cases but they all seem either too gaudy or too small with not enough power supply.

Also (sadly) is seems like Windows has a lot more support for a "Multimedia PC"... for example I can play a ripped blu-ray disk in Windows just fine... but not in Linux.  :(

Oh well... more research to do before I find what I'm looking for.

---

### Post by Krupski on 2009-09-12
> **HobbDogg said:**
> @Krupski, Alright. Hey can I ask you what you used for your bluray discs?

A blu ray drive (of course) and "AnyDVD" by Slysoft.

---

### Post by ntginson on 2009-09-13
There are several commercially available media streamers. I live in the Philippines so I am not sure if they are available in your location.

I currently have one like this:

[http://www.mediagateusa.com/](http://www.mediagateusa.com/)

and plan to upgrade it to either this:

[http://www.popcornhour.com/onlinestore/](http://www.popcornhour.com/onlinestore/)

or this:

[http://www.midte.com/Home/Home.html](http://www.midte.com/Home/Home.html)

or this:

[www.roku.com/netflix](www.roku.com/netflix)

Most if not all can stream videos, music and photos to your TV without the use of a computer. Connections to your network are done via LAN or WiFi.

Some of these products have an option of plugging in a hard disk internally or by connecting it via builtin USB port

Video outputs are composite, HDMI, RCA, DVI

Audio outputs are stereo, optical, cable

HTH

---

### Post by Krupski on 2009-09-13
> **ntginson said:**
> 
[http://www.popcornhour.com/onlinestore/](http://www.popcornhour.com/onlinestore/)


WOW! That "popcorn hour" device looks like EXACTLY the thing I was searching for! Thanks!

-- Roger

---

### Post by x C0MMAND0 x on 2009-09-13
That popcorn hour device does look pretty sweet...but about the same cost as a cheap computer with an hdmi out card to your TV...

---

### Post by 4Orbs on 2009-09-14
These look cool but seem overpriced. The new Playstation 3 costs only a little more and can be [easily set up]("http://arkold.com/602-super-mega-fast-way-to-setup-a-media-server-on-ubuntu-jaunty") to stream via wireless from a PC / media server.

---

### Post by Chris Riley on 2009-09-14
I just bought a Raidsonic IcyBox MP308 which has all the bells & whistles. Connects via wireless to your network, streams media content (music, jpeg, movies in various formats) to the tv via component, composite, or hdmi. It can connect to Shoutcast via your LAN Internet access for radio. I also purchased a 1Tb HDD which mounts internally in the IcyBox, you copy files to it only when connected via USB. All in all, does everything I want and more. Check it out.

Chris:guitar:

---

### Post by Krupski on 2009-09-19
> **4Orbs said:**
> These look cool but seem overpriced. The new Playstation 3 costs only a little more and can be [easily set up]("http://arkold.com/602-super-mega-fast-way-to-setup-a-media-server-on-ubuntu-jaunty") to stream via wireless from a PC / media server.

Thank you for the post. I HAVE a PS3! I didn't know until recently that it would work for what I wanted. 

I have finally figured it all out and got it working. I'm using the Java based "PS3 Media Server" on a headless Ubuntu 9.04 file server and got it working great.

In case anyone wishes to set one up, here's how:

* Download the media server package [[COLOR="Blue"]**LINK**[/COLOR]]("http://code.google.com/p/ps3mediaserver/") (see "featured downloads" on the right).

* Install the following packages on your server, using "sudo apt-get -V install..."

- sun-java6-jre <-- must accept license during install
- mplayer-nogui
- mencoder
- ffmpeg

* Install the PS3 media server package into any directory you wish (a sensible place might be "/usr"). To unpack/install, do this:

```

sudo cd /usr
sudo tar -xf pms-linux-1.10.5.tgz
sudo mv pms-linux-1.10.5 pms-linux

```

(the last command makes the directory name non-version dependent).

Now, create a file named "PMS.conf" (uppercase "PMS" important) with the following contents:

(ASSUMING your DVD rips are located in "/home/files/dvd-videos"...)

```

thumbnails = true
mencoder_*** = true [COLOR="Red"]**<== see IMPORTANT note below**[/COLOR]
folders = \/home\/files\/dvd-videos
use_mplayer_for_video_thumbs = true

```

Be sure you get the backslashes and forward slashes right!

Now, place the PMS.conf file in the same directory as the PS3 video player. The directory should now look like this:

```

root@storage:/usr/pms-linux# ls -laF
total 17188
drwxr-xr-x  3 root root     4096 2009-09-19 17:13 ./
drwxr-xr-x 12 root root     4096 2009-09-19 14:51 ../
-rw-r--r--  1 root root    11004 2009-03-08 10:50 CHANGELOG
-rw-r--r--  1 root root     6311 2008-12-29 07:35 FAQ
drwxr-xr-x  2 root root     4096 2009-09-19 14:29 linux/
-rw-r--r--  1 root root       99 2009-09-19 14:40 PMS.conf
-rw-r--r--  1 root root 17497615 2009-03-08 15:04 pms.jar
-rw-r--r--  1 root root     1023 2008-12-29 07:35 PMS.sh
-rw-r--r--  1 root root     6513 2009-02-18 20:24 README
-rw-r--r--  1 root root      596 2009-09-19 14:56 WEB.conf

```

Normally, with a GUI installation of Ubuntu, you get a PMS window which allows you to configure the paths to the DVD files. On a text only headless server, there is no way to generate the "PMS.conf" file - hence you have to do it yourself.

Now, run the PS3 video server:

```

sudo sh PMS.sh

```

[COLOR="Red"]**** IMPORTANT NOTE: The "smut filter" on this board modified the text of the required data. The *** is replacing the text "a-s-s" (sorry... but that's what it is!). The three letters - no dashes.**[/COLOR] 

If all is well, your server should show up in the Playstation, you should be able to browse and play all of your video and media content.

Good luck!

-- Roger

---

