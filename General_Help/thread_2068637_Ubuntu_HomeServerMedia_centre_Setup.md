---
title: "Ubuntu HomeServer/Media centre Setup"
date: 2012-10-09
forum: General Help
---

### Post by BStrizzy on 2012-10-09
Hey guys, Im trying to make my homeserver that I made yesterday (10.04) into a elaborate homeserver.

What I have:

1.) Laptop, DuelBooted with Win7 and Ubuntu 11.10. (usually on ubuntu :)) 
2. ) Another Laptop with ubuntu server 10.04
3.) Xbox 360

What I want:
1.) For my xbox 360 to to be able to stream my movies, music, pictures, ect.. from that home server. The research I have found led me to believe MediaTomb is probably the best option. Now will be putting media tomb on my ubuntu desktop or on the server. Also will I even need to use mediatomb? should the xbox automatically be able to look up files on the server if I connect it to it?

2.) Ability to access to my server from another location. For example, school. If i need a file and its on the server, what are the steps and programs i need to make this happen? weather its from another computer or a mobile phone(soon to be rooted). 

3.) can somebody tell me if samba will be neccessary and a rundown of its main purpose. the research ive done led me to believe that I will need samba, but I was not sure If i needed it on my personal laptop with ubuntu desktop or do i put it on the home server its self.

4.) lastly, I have only configured the server on my Win7 and use putty and another program similar to file zilla, I want to access it on my ubuntu desktop. Do I simply go to file and connect to server or are there better programs I can use

---

### Post by gavinjb on 2013-01-30
Hi,

Not sure if you have this answered by now.

1) I personally haven't used media tomb, but for streaming media it will depend on what you want to do with the media and what your XBox Player supports. e.g. do you want to transcode your movies to 720p, 1080p... if you  do you will need a reasonable processor and a fair amount of ram, I do this with my Movies and currently use PLEX Media Server for this, it does need a bit in processing/RAm requirements but is very good.

2) To be able to access any of your server from outside your network you will need to forward the relevant ports from your Router to the Server, but to be able to download files you have a couple of options 1 is to setup either an FTP server or Webdav on your Server, 2 is to install AjaxExplorer which gives you a web file browser and is fairly good.

3) If you install Samba you will be able to make shares avaialble to Windows/Linux desktops (there might be other ways, but this is the only way I know of), setting up sharing is not always the easiest, as you need to make sure that the folder you are sharing has the correct permissions (I had problems lastnight when I forgot to chmod +x to a new share!).

You might also want to consider install Webmin which gives you an Web Admin interface to do many common tasks or alternatively you could look at Amahi which when installs gives you a nice web interface and similar functionality to a NAS Box and will mean you will be able to do most of the above from within it.

Hope some of this helps.

---

### Post by BStrizzy on 2013-02-05
> **gavinjb said:**
> Hi,

Not sure if you have this answered by now.

1) I personally haven't used media tomb, but for streaming media it will depend on what you want to do with the media and what your XBox Player supports. e.g. do you want to transcode your movies to 720p, 1080p... if you  do you will need a reasonable processor and a fair amount of ram, I do this with my Movies and currently use PLEX Media Server for this, it does need a bit in processing/RAm requirements but is very good.

2) To be able to access any of your server from outside your network you will need to forward the relevant ports from your Router to the Server, but to be able to download files you have a couple of options 1 is to setup either an FTP server or Webdav on your Server, 2 is to install AjaxExplorer which gives you a web file browser and is fairly good.

3) If you install Samba you will be able to make shares avaialble to Windows/Linux desktops (there might be other ways, but this is the only way I know of), setting up sharing is not always the easiest, as you need to make sure that the folder you are sharing has the correct permissions (I had problems lastnight when I forgot to chmod +x to a new share!).

You might also want to consider install Webmin which gives you an Web Admin interface to do many common tasks or alternatively you could look at Amahi which when installs gives you a nice web interface and similar functionality to a NAS Box and will mean you will be able to do most of the above from within it.

Hope some of this helps.


hey man thanks for the response. I did end up getting everything figured out and loving it! i am currently using media tomb to hold my media files and share to devices. I also opened port 22, but considering vpn, for security purposes. still need to look in to that. actually, any suggestions about vpn? I have a static lan and my cable provider provides me an ip. (not static)

---

### Post by CharlesA on 2013-02-05
You shouldn't need a VPN as long as you have SSH secured with a strong password or keys.

---

### Post by collisionystm on 2013-02-05
I know you have it already figured out but I just wanted to share. 

I made a media server about 2 weeks ago. Used a 9 year old compaq laptop that had an AMD Sempron, 512mb of ram and a 60GB HD. I installed Ubuntu server 12.04 and attached my 1TB usb hard drive for media storage.

I wanted something that I could listen to music remotely, from xbox, ps3 and windows media player.

I tried media tomb. I had success with everything but remote. 

I then discovered PLEX. Seriously, PLEX is a godsend. I installed PLEX, brought up its nice web interface and.. wow, It was great! I loved it so much I paid 4.99 for the iphone app so I could access all my stuff remotely from my iPhone and iPad lol. All I had to do was setup the port forward in my router.

Long story short... tried mediatomb and fell in love with PLEX instead. It is truly amazing.

Also, PLEX integrates with Amazon instant video and Netflix, but you need silverlight for Netflix to work so that part is better left to running it on a Windows box instead of ubuntu (unfortunately).

Good luck and congrats on your server!

---

### Post by BStrizzy on 2013-02-09
> **collisionystm said:**
> I know you have it already figured out but I just wanted to share. 

I made a media server about 2 weeks ago. Used a 9 year old compaq laptop that had an AMD Sempron, 512mb of ram and a 60GB HD. I installed Ubuntu server 12.04 and attached my 1TB usb hard drive for media storage.

I wanted something that I could listen to music remotely, from xbox, ps3 and windows media player.

I tried media tomb. I had success with everything but remote. 

I then discovered PLEX. Seriously, PLEX is a godsend. I installed PLEX, brought up its nice web interface and.. wow, It was great! I loved it so much I paid 4.99 for the iphone app so I could access all my stuff remotely from my iPhone and iPad lol. All I had to do was setup the port forward in my router.

Long story short... tried mediatomb and fell in love with PLEX instead. It is truly amazing.

Also, PLEX integrates with Amazon instant video and Netflix, but you need silverlight for Netflix to work so that part is better left to running it on a Windows box instead of ubuntu (unfortunately).

Good luck and congrats on your server!

awesome man, Do you have a good guide for the plex install on ubuntu server?

---

### Post by kgr132 on 2013-02-10
Thanks for the tip about PLEX. I've been searching for something just like it.

> **collisionystm said:**
> ...but you need silverlight for Netflix to work so that part is better left to running it on a Windows box instead of ubuntu (unfortunately).
For Netflix, try Netflix Desktop. It requires Wine and some dependencies, but didn't seem too bulky overall.
"...includes the Windows version of Mozilla Firefox and Microsoft Silverlight v4. The package also includes some convenience settings to integrate Netflix Desktop into Firefox in such a way that everything feels like a native Ubuntu application..."
The package seems to have regular updates and in the 6 months I've been using it, it's been great.

---

### Post by collisionystm on 2013-02-10
> **BStrizzy said:**
> awesome man, Do you have a good guide for the plex install on ubuntu server?


Its already in the software center...

sudo apt-get install plex

Once its up, access it from the web.

[http://x.x.x.x:32400/web](http://x.x.x.x:32400/web)

---

### Post by collisionystm on 2013-02-10
> **kgr132 said:**
> Thanks for the tip about PLEX. I've been searching for something just like it.


For Netflix, try Netflix Desktop. It requires Wine and some dependencies, but didn't seem too bulky overall.
"...includes the Windows version of Mozilla Firefox and Microsoft Silverlight v4. The package also includes some convenience settings to integrate Netflix Desktop into Firefox in such a way that everything feels like a native Ubuntu application..."
The package seems to have regular updates and in the 6 months I've been using it, it's been great.


The thing about the Netflix plugin for Plex is that it will actually download the entire movie from netflix for you to view at a later date. So essentially you can bring up plex on your iPad or other tablet and watch the netflix movie from an airplane or car ride.
It needs silverlight for the transcoding though...

---

### Post by BStrizzy on 2013-02-13
> **collisionystm said:**
> Its already in the software center...

sudo apt-get install plex

Once its up, access it from the web.

[http://x.x.x.x:32400/web](http://x.x.x.x:32400/web)

 will be trying this out

---

