---
title: "OH GAWD it hurts"
date: 2010-06-04
forum: General Help
---

### Post by igf1 on 2010-06-04
So, wifi, it gradually improved until it was essentially perfected in Ubuntu 9.10 and regressed in 10.04. 

Seriously, my USB wireless worked in 9.10 and now it "works" but it's speed is marked in bits per second... 

I also tried another wireless USB and same thing. I boot to 9.10 and it's not a problem. So, I thought, maybe the installation hosed the driver... whatever.. I reinstalled this time 64 bit version and same thing.. I.. am so frustrated ... waiting 10 mins to submit a Google search <twitch twitch>

Anyone have any idea? I have Kernel .34 but I think it was the same with .32 .. I dont remember now.

---

### Post by wojox on 2010-06-04
Here's an idea. Keep 9.10 on there. A lot of people are still using it. Just because a new release comes out, doesn't mean you have to upgrade. 

Do a search on Launchpad and see if anyone has reported a bug for it and follow it.

---

### Post by darkworld on 2010-06-04
I fully simpathise with you. Ubuntu latest releases are such a pain sometimes.  The last time everything ran right on my machine was jaunty......sometimes the way forwards is to go backwards.

---

### Post by Martin_sensei on 2010-06-04
I too know what you mean, however I have been very pleasantly surprised  by 10.04.  My wifi worked out of the box, which was far from the case in 9.10.  

I know that doesn't help, I just wanted to say there have been improvements for some of us...

Fingers crossed for 10.10? ;-)

---

### Post by darkworld on 2010-06-04
that always seems to be the case on every release, some loose some gain..... just have to keep your fingers crossed that the gods smile on you in a new release.... Or is it a case of....if you have got the latest kit, your stuffed?

---

### Post by igf1 on 2010-06-04
Sigh, I ran an OS software company once, so I understand the complexity of managing near infinite use cases. I just wish that there were a better way forward than constant regression. Which; is arguably  one of the caveats with OS software. It's not necessarily Ubuntu, it's from the Kernel on up. I suspect, that we (the OSS community) need to rethink our upgrade strategy. Like DarkWorld said, the way forward isn't always ahead. A driver update that does not apply to my device, which is working, is an unnecessary risk. The only way to avoid these regressions is through hierarchical modularity. The problem is version nightmares and compatibility decay... hmmmmm LLVM....

Anyway, I'm using a Verizon CDMA card right now, but I'm almost out of bandwidth via my quota. the web without images takes me back.. maybe I should just use lynx :-)

My USB WIFI is Linksys WUSB54GC if anyone has overcome this problem.. please, save a man from cat5 cutting..:P

---

### Post by mrinehart93 on 2010-06-04
I don't know if this will help anyone or not, but I literally found the most hassle-free and easiest solutions for WiFi in Linux. The only drawback is that you will need to spend money... however it's worth it.

You need:
1x Linksys WRT54G router
1x cat5 ethernet cable
1x of DDWRT firmware
1x router to connect to 

Basically what you end up doing is putting the Linksys WRT54G into a "wireless ethernet bridge" mode. In this mode, the WRT54G is wired to your laptop/desktop via cat5 ethernet cable. This is where everything gets good. The laptop/desktop the WRT54G is wired to THINKS it is connected directly to the main router/modem/ethernet jack. Because of this, NO driver is required, and the connection is ALWAYS on as long as the WRT54G is on. I just eventually gave up getting wireless cards to work in Ubuntu. I would get them to work, but the speeds I would get would be terrible. With this new setup I have (and highly recommend), you get full speeds. Right now I am downloading some torrents at 1.2mb/s, which is what I get when I'm using Windows.

---

### Post by wojox on 2010-06-04
> **mrinehart93 said:**
> I don't know if this will help anyone or not, but I literally found the most hassle-free and easiest solutions for WiFi in Linux. The only drawback is that you will need to spend money... however it's worth it.

You need:
1x Linksys WRT54G router
1x cat5 ethernet cable
1x of DDWRT firmware
1x router to connect to 

Basically what you end up doing is putting the Linksys WRT54G into a "wireless ethernet bridge" mode. In this mode, the WRT54G is wired to your laptop/desktop via cat5 ethernet cable. This is where everything gets good. The laptop/desktop the WRT54G is wired to THINKS it is connected directly to the main router/modem/ethernet jack. Because of this, NO driver is required, and the connection is ALWAYS on as long as the WRT54G is on. I just eventually gave up getting wireless cards to work in Ubuntu. I would get them to work, but the speeds I would get would be terrible. With this new setup I have (and highly recommend), you get full speeds. Right now I am downloading some torrents at 1.2mb/s, which is what I get when I'm using Windows.


That's exactly my set up as well, except mine says WRT54G2

---

### Post by igf1 on 2010-06-04
> **mrinehart93 said:**
> I don't know if this will help anyone or not, but I literally found the most hassle-free and easiest solutions for WiFi in Linux. The only drawback is that you will need to spend money... however it's worth it.

You need:
1x Linksys WRT54G router
1x cat5 ethernet cable
1x of DDWRT firmware
1x router to connect to 

Basically what you end up doing is putting the Linksys WRT54G into a "wireless ethernet bridge" mode. In this mode, the WRT54G is wired to your laptop/desktop via cat5 ethernet cable. This is where everything gets good. The laptop/desktop the WRT54G is wired to THINKS it is connected directly to the main router/modem/ethernet jack. Because of this, NO driver is required, and the connection is ALWAYS on as long as the WRT54G is on. I just eventually gave up getting wireless cards to work in Ubuntu. I would get them to work, but the speeds I would get would be terrible. With this new setup I have (and highly recommend), you get full speeds. Right now I am downloading some torrents at 1.2mb/s, which is what I get when I'm using Windows.

I used to have that setup, I don't have the hardware anymore or patience for that :). Though I could use a repeater :). 

I think what I'll try now is a manual driver install, then if that fails I'll try NDIS.. and finally I'll do a mod build if all else fails. NDIS is a crap shoot, but if it works.. it's usually really stable stable.

---

