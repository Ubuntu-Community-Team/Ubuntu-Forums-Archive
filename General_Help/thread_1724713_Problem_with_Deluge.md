---
title: "Problem with Deluge"
date: 2011-04-08
forum: General Help
---

### Post by Gael33 on 2011-04-08
I cannot get the incoming port connections to work ... does anybody know how I should configure the port settings so I can "seed"? I have already used the program and downloaded what I wanted (work related), now I have added my contribution I would like to share my work with others using Deluge.

Any help will be appreciated.

---

### Post by seawolf167 on 2011-04-08
I don't use Deluge so I can't tell you exactly where to find these settings, but it's the same for all torrent programs

Open the setting menu and find the port settings section. Enter the port of your choice and hit apply/ok

Open your router config page and find the port forwarding section. Create a new rule and forward that port you just setup from above to be forwarded to your computer's LAN ip address

---

### Post by Gael33 on 2011-04-10
> **seawolf167 said:**
> I don't use Deluge so I can't tell you exactly where to find these settings, but it's the same for all torrent programs

Open the setting menu and find the port settings section. Enter the port of your choice and hit apply/ok

Open your router config page and find the port forwarding section. Create a new rule and forward that port you just setup from above to be forwarded to your computer's LAN ip address

To all intents and purposes Deluge looks a great program. It's clean and fast but impossibly difficult to set up. I made (what I thought) were the necessary adjustments in the Netgear wireless router and the Firewall program, Firestarter, and it still didn't work. I played around with it for over a hour without any success ... and gave up. I installed BITtorrent and it worked fully after I rebooted ... an old habit from my Windows days :)
I hate being beaten this way - so, if anyone knows how to install, setup a fully working version of Deluge I would probably give it another go. In the meantime, I will stick with something that works (metaphorically) out of the box.
I must say I am a little disappointed that more people didn't get involved with this topic as Deluge is a great program. I admit I am not very technically minded, so this was a bridge to far for me, but we do have wizz-kidz on here who could probably crack this nut within 10 minutes. Come on guys, help out an old Luddite and send me instructions that work.   :)

gael

---

### Post by Cas07 on 2011-04-18
For Deluge specific help you should visit our [forum]("http://forum.deluge-torrent.org/") but the incoming ports issue actually applies to every bittorrent client so you should read this thread: [http://ubuntuforums.org/showthread.php?t=1259923](http://ubuntuforums.org/showthread.php?t=1259923)

---

### Post by ThatGuyFromThatShow! on 2011-05-06
> **Gael33 said:**
> I must say I am a little disappointed that more people didn't get involved with this topic as Deluge is a great program. I admit I am not very technically minded, so this was a bridge to far for me, but we do have wizz-kidz on here who could probably crack this nut within 10 minutes. Come on guys, help out an old Luddite and send me instructions that work.   :)

I switched my laptop from windows to ubuntu last week and here's how I set up deluge network section (other stuff I left alone until I made sure things worked):

I just changed that top section regarding incoming settings

I had already set my router to forward **all** incoming traffic on ports 64610-64620 to  my computer (my westell router lets me specify the name of my computer  so ip address doesn't matter, yours may want a specific ip address) and  clicked the "test" button to make sure it worked.

[IMG]http://i30.photobucket.com/albums/c346/ThatGuyFromThatShow/deluge_network_set.jpg[/IMG]

I then went to [http://www.yougetsignal.com/tools/open-ports/](http://www.yougetsignal.com/tools/open-ports/) to double check that the port deluge was using was open and connecting correctly to my computer.

I hope that helps.  Actually, I found this post because I have a really bad issue with an otherwise excellent bittorent program...deluge won't seed once I've finished downloading a torrent and I haven't messing with ratio settings or anything like that.  To work around it, I have to download a torrent, move one large file out, recheck the torrent, and re-download the one file with a **very** slow download setting so the seeding works :cry:

---

### Post by PratterFak on 2011-05-06
> **Gael33 said:**
> I cannot get the incoming port connections to work ... does anybody know how I should configure the port settings so I can "seed"? I have already used the program and downloaded what I wanted (work related), now I have added my contribution I would like to share my work with others using Deluge.

Any help will be appreciated.

Hopefully you get this sorted out, but I didn't. Even though I had the port forwarded, it would still show blocked at times. I ended up just changing to qBittorrent and it works great- like it even better than Deluge anyway. I was originally using Transmission on 10.10 and prior, but after upgrade to 11.04, that wouldn't work. So, I had to find an alternate which I like better anyway. :)

---

### Post by Cas07 on 2011-05-10
> **PratterFak said:**
> I ended up just changing to qBittorrent and it works great- like it even better than Deluge anyway. I was originally using Transmission on 10.10 and prior, but after upgrade to 11.04, that wouldn't work. So, I had to find an alternate which I like better anyway. :)

You realise that qBittorrent and Deluge both use [libtorrent (rasterbar)]("http://www.rasterbar.com/products/libtorrent/") at their core so it makes no sense that switching would change anything unless you are using a newer version of libtorrent that fixed something specific to your setup.

---

### Post by Gael33 on 2011-05-10
> **Cas07 said:**
> You realise that qBittorrent and Deluge both use [libtorrent (rasterbar)]("http://www.rasterbar.com/products/libtorrent/") at their core so it makes no sense that switching would change anything unless you are using a newer version of libtorrent that fixed something specific to your setup.

I see your point :)
I've recently had another go with Deluge now that I've upgraded to Ubuntu 11.04 ... I can download and upload, but I still cannot get the incoming connections to work (Grrrrr). Very frustrating. I will probable go back to Transmission ... eventually :)

gael

---

