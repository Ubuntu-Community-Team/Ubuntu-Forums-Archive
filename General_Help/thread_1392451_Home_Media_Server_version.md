---
title: "Home Media Server version"
date: 2010-01-28
forum: General Help
---

### Post by giantjoebot on 2010-01-28
I have played around with this idea for a while. I'm going to make a home media server version of Linux, and one of the main features is going to be XBMC. So I would really like some input. Any help is more than welcome. 

I have put together a couple basic systems, and to get everything working takes a lot of time. It would be much easier, simpler, and faster if everything was already setup and ready to go on a ISO. Burn it, throw it in, a little configuring, and away you go.

The basic idea is to have computer that not only plays your media, but also acquires it, and allows you to access your media over your home network and an internet connection. I call it a Home Media Server. Everything is already there, its just a matter of putting it all together.

So here is my plan

Start out with Ubuntu. Take off unnecessary programs, like open office. Then start adding and configuring things. Some things I'm sure about, something I'm not so sure about. 

Here are things that I'm sure about
[LIST=1]
[*]XBMC
[*]Vuze
[*][AzSMRC]("http://azsmrc.sourceforge.net/")
[*]Amule
[*]Apache webserver
[*]MySQL
[*]PHP
[*]Ampache
[*]SMB
[*][COLOR=Black][XBMC HTTP-R]("http://xbmc.org/forum/showthread.php?t=40958")[/COLOR]
[/LIST]

Now for the things that I'm not so sure about

[WebShare]("http://en.webshare.fr/") - for accessing files. It has the best interface that I have found, and it uses FTP instead of http, which I like, but I haven't played around with it at all. So hopefully I can get it to work right.

[MyDisk]("http://www.mydisk.co.uk/") or [PHP Navigator]("http://navphp.sourceforge.net/") - if WebShare doesn't work out.

[Glype proxy]("http://www.glype.com/") - For secure browsing in public unsecured places, and getting past filters
 
[Zenphoto]("http://www.zenphoto.org/") - if I can get it to change the location of the photo gallery folder

**XBMC remote for iphone and Android** - XBMC HTTP-R seems like it will work for everything. Not sure if I should add these or just leave them for people to install on their own. I don't have either so it will also be hard for me to test them.

**XBMC Streamer for iphone** - again might leave this for people to install on their own.

**MediaTomb** - not sure if its necessary since XBMC has a upnp server built in.  I don't really have any use for it, but if people want it

Notes
Listed above is SMB, going to set it up with an SMB server (workgroups) out of the box.  

Also want to try and get some sort of bandwith shaping going on.  Even if its just limiting the both P2P's to a set limit.  

If your wondering about video over the internet, like orb, then here is what I do - Start downloading with ftp, and start playing it with VLC. As long as the download speed is faster than the play lenght, and you can always wait a few minutes until it is, then you can play videos over the internet. Problem with transcoding to a lower bitrate and then streaming, like orb does, is it takes a lot of resources, and I'm not aware of any program does this ,simply, in linux. If you get it working and people want it, then tell me how you did it, and I'll see if I can add it.

**If anyone has any ideas on something that would like to add, or that might be better than what I listed, I'm all ears**

---

### Post by cry8wolf9 on 2010-01-28
i wouldnt mind seeing something that can transcribe videos and has support for ps3 and xbox

---

### Post by head2head on 2010-01-28
Can't Mediatomb do that already?

---

### Post by giantjoebot on 2010-01-28
Yes Media Tomb can do that.  I guess I'll add it.

Anything else?

I could really use some input on what to use for a file browser, MyDisk, WebShare, or PHP Navigator.  Anyone have an opinion on that one?

That and FTP, use to use filezilla in windows, but not really familiar as to what the best option in Linux would be.

Do I have this in the right section of the forum?  I wasn't sure where to post it.

---

