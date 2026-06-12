---
title: "Please help: internet connection very slow on ubuntu but fast in XP"
date: 2010-03-23
forum: General Help
---

### Post by Chromagnum on 2010-03-23
Like the title, that is my problem. I'm using cable modem with 3mbps. It is Linksys Docsis, wired networking. When I download a file using ubuntu 9.10, my latency time (ping time) sky rocketed to 2000ms average, while in XP none of this happens; I tried to download the same file from the same website. 

In ubuntu 9.10 my network setup will be, well... nothing. I'm using DHCP automatic detection. Same thing in XP. Please help me, I really like ubuntu. I don't want to go back and forward using XP for the internet. 

Funny thing though, none of this happens while I first started ubuntu 9.10. I didn't configure anything with networking. It is the way it is from the beginning. The only thing I tried was ubuntuone. But that like months ago, and the problem I have with slow internet connection only appear this March.

Please help me, I didn't know what to do.

---

### Post by Chromagnum on 2010-03-24
Already remove --purge ubuntuone*, also disable Ipv6 in grub. The problem still appear. Still got the huge latency problem while downloading file using ubuntu 9.10. While XP, no problem at all.

In idle condition, both OS have the same average latency. Only happened if downstream being use.

I still need some help, please. Thanks.

---

### Post by DeMus on 2010-03-24
Did you get involved in using Samba lately? I did some time ago and with the wrong settings my dns "host lookup time" was gigantic. Download speed was normal, but the time it took before a webpage was found took like forever.

---

### Post by Chromagnum on 2010-03-24
> **DeMus said:**
> Did you get involved in using Samba lately? I did some time ago and with the wrong settings my dns "host lookup time" was gigantic. Download speed was normal, but the time it took before a webpage was found took like forever.

Now that you mentioned samba, all I know was there were some Sambas update from ubuntu — that's it. I didn't do anything, except for enabling file share, but that's like, months ago. Yeah, the only thing involved samba was ubuntu update manager told me to upgrade.

Man... right now I'm looking on downstream power and noise; 0.00 dBmV and SNR 37dB. It supposed to be perfect. Why I still get this huge latency. Sometimes, I only used, like, 40KB/sec and the latency goes up to 1000ms. I practically can't do anything while downloading. None of this happen in XP.

If the problem in Samba setting, how do I fix it? 

Thanks.

EDIT TO ADD: 
I tried to disable Samba using
```
sudo /etc/init.d/samba stop
```
Still the same result.

---

### Post by Chromagnum on 2010-03-24
Okay, I noticed something different. The Ip address and Default Route (Default gateway) different in both ubuntu and xp, while the primary and secondary DNS the same. But, no matter how many times I reboot the system or shut down completely, I get the same settings from ISP. 

In ubuntu (ip address): xxx.xxx.31.xxx
In Xp (ip address): xxx.xxx.1.xxx

In ubuntu (default route): xxx.xxx.31.xxx
in Xp (default route): xxx.xxx.1.xxx

xxx = same number for both. 

Could it be the problem rely on ISP?

And also, I tried to reinstall Network Manager in synaptic, won't help either.

ps: I'm about to smack my head on the wall -.-

---

### Post by Laxman_prodigy on 2010-03-24
> **Chromagnum said:**
> Okay, I noticed something different. The Ip address and Default Route (Default gateway) different in both ubuntu and xp, while the primary and secondary DNS the same. But, no matter how many times I reboot the system or shut down completely, I get the same settings from ISP. 

In ubuntu (ip address): xxx.xxx.31.xxx
In Xp (ip address): xxx.xxx.1.xxx

In ubuntu (default route): xxx.xxx.31.xxx
in Xp (default route): xxx.xxx.1.xxx

xxx = same number for both. 

Could it be the problem rely on ISP?

And also, I tried to reinstall Network Manager in synaptic, won't help either.

ps: I'm about to smack my head on the wall -.-


Don't worry. Though I can't help; the members here are very knowledgeable.

---

### Post by Chromagnum on 2010-03-24
> **Laxman_prodigy said:**
> Don't worry. Though I can't help; the members here are very knowledgeable.

Thanks. I hope the knowledgeable one set me some light in the darkness of downstream confusion. 

I should add more data to this problem. 

The gigantic latency time, only happened from some servers I downloaded. Let's say server A, I won't have a problem — the ping time seems normal, while on server B, I get, like 2000ms. But it was only happened in ubuntu 9.10. I didn't encountered any problem at all in Xp.

Like couple of minutes ago, I tried speedtest.net. I get full max bandwitdh like it supposed to. But, in ubuntu 9.10 while speedtest, the latency time around 800ms. In Xp only about 100ms tops. 

Now I'm confuse. Is it my ISP or Ubuntu or... I don't know anymore.

---

### Post by cjhabs on 2010-03-24
> **Chromagnum said:**
> Thanks. I hope the knowledgeable one set me some light in the darkness of downstream confusion. 

I should add more data to this problem. 

The gigantic latency time, only happened from some servers I downloaded. Let's say server A, I won't have a problem — the ping time seems normal, while on server B, I get, like 2000ms. But it was only happened in ubuntu 9.10. I didn't encountered any problem at all in Xp.

Like couple of minutes ago, I tried speedtest.net. I get full max bandwitdh like it supposed to. But, in ubuntu 9.10 while speedtest, the latency time around 800ms. In Xp only about 100ms tops. 

Now I'm confuse. Is it my ISP or Ubuntu or... I don't know anymore.

How about manually setting your IP settings to match what the XP box receives through DHCP, and vice versa for the XP box to see if the different IP settings are the issue?

---

### Post by Chromagnum on 2010-03-24
> **cjhabs said:**
> How about manually setting your IP settings to match what the XP box receives through DHCP, and vice versa for the XP box to see if the different IP settings are the issue?

Why didn't I think of that before. Good point!

I'll try it right away and get back in here soon with the result. Thanks cjhabs.

---

### Post by Chromagnum on 2010-03-24
So I did what cjhabs advice and the result still the same. So I can now rule out the ISP causing this problem. This is definitely because ubuntu. The question is: what causing ubuntu behaviouring like this? Gigantic latency time, packet loss... 

...sigh.

---

### Post by Chromagnum on 2010-03-24
Tried replacing Network Manager with Wicd, still the same. So now, I'm back to Network Manager again. 

Strange. If I'm not download anything, everything works great. But the minute I download something and the gigantic latency appear again, as the result I can't do a simple google. But none of this had happened in xp. 

Oh also, I'm not using any wubi at all. This is standalone ubuntu on the standalone Hdd. Xp also the same. So I'm using 2 physical Hdd.

What causing this problem. Is it kernel? :shock: I'm confuse...

---

### Post by Chromagnum on 2010-03-24
I tried boot from live cd and access internet from there. You know, narrow it down the problem. And the result still the same!! Crap!

(Okay I need to do some yoga first, calm down)

So basicly this is the NIC problem. Strange though, why XP didn't pick up the same problem on the same NIC?

I need a cold shower, be back later with some series of tests.

---

### Post by cjhabs on 2010-03-24
> **Chromagnum said:**
> I tried boot from live cd and access internet from there. You know, narrow it down the problem. And the result still the same!! Crap!

(Okay I need to do some yoga first, calm down)

So basicly this is the NIC problem. Strange though, why XP didn't pick up the same problem on the same NIC?

I need a cold shower, be back later with some series of tests.

Yeah, I've taken up Yoga since switching to Ubuntu also :-)
But I love it and only use Windows at work.

Are there any messages in /var/log/syslog that shed any light on the problem?

---

### Post by Chromagnum on 2010-03-25
> **cjhabs said:**
> Yeah, I've taken up Yoga since switching to Ubuntu also :-)
But I love it and only use Windows at work.

Are there any messages in /var/log/syslog that shed any light on the problem?

The syslog is fine. There is nothing unsual, I even compared to old syslog, pretty much the same. 

Okay, so I changed NIC, using a bunch of cards laying around in my tools drawer and the result still the same. So the problem not in NIC. My ISP even contacted me back about the problem. He told me, the signal and all is fine. He would check on ubuntu himself. I'm still waiting for his call.

Ubuntuone remove. IPv6 disabled. Tried internet on live cd. Using different type of NIC cards. Modem downstream power and noise are normal. ISP don't have any problem. Still the same result. So what the hell is the problem?

I even search google and this forum for the same problem, and I stumbled a couple of threads discussing the same thing back in 2007. But there is no solution. 

I thought if this never gonna be solve I just do a clean install again, since first time I started ubuntu none of this had happened. But, since I'm already tried on live cd as well with no victory either — I mean, live cd is the most clean installation ever. Now there is doubt.

What should I do? Go back to xp? Oh man...

---

### Post by cjhabs on 2010-03-25
Looks like you have eliminated everything!

If it only happens on download, do any extra processes start up during a download - a download manager of some kind? How are you doing your downloads?

---

### Post by Chromagnum on 2010-03-25
> **cjhabs said:**
> Looks like you have eliminated everything!

If it only happens on download, do any extra processes start up during a download - a download manager of some kind? How are you doing your downloads?

All downstream connection. It could be download a file, browsing, anything. Doesn't matter if I use firefox to download or jdownloader or wget, still the same. Some sites (servers) won't give me such gigantic latency, but some does. But all servers won't have any problem at all while in Xp. Strange isn't it? 

Like I said in page 1, when I did speedtest from speedtest.net, ubuntu gave me 800ms average, some packet loss as well. Ubuntu Live CD gave the same result. Xp on the other hand, only gave 100ms tops. No packet loss.

---

### Post by cjhabs on 2010-03-25
You said that you disabled ipv6 in grub - did you double check that it hasn't loaded with "modprobe -l"?

---

### Post by DeMus on 2010-03-25
Just got home from work, sorry for the delay.
I had host lookup times in both Firefox and Chrome of more than 10 seconds. It was caused by a line in the file:
```
/etc/samba/smb/conf
```

In this file you can see the following line:
```
name resolve order = bcast host lmhosts wins

```
Make sure the word wins is at the end of the line. If not the computer will start to look for the webpage you want to see on your local computer, or your local network before it starts looking on the net.
This helped me a lot. I hope it will help you to.

---

### Post by Chromagnum on 2010-03-25
> **cjhabs said:**
> You said that you disabled ipv6 in grub - did you double check that it hasn't loaded with "modprobe -l"?

I use this
```
ip a | grep inet6
```
to check if IPv6 disable or not. And there is no output, so I guess disable must have been working.

I did what you say and this is the result as far as contained any word of ipv6. Does that mean ipv6 still enable?
```
kernel/net/ipv6/netfilter/ip6_tables.ko
kernel/net/ipv6/netfilter/ip6table_filter.ko
kernel/net/ipv6/netfilter/ip6table_mangle.ko
kernel/net/ipv6/netfilter/ip6_queue.ko
kernel/net/ipv6/netfilter/ip6table_raw.ko
kernel/net/ipv6/netfilter/ip6table_security.ko
kernel/net/ipv6/netfilter/nf_conntrack_ipv6.ko
kernel/net/ipv6/netfilter/ip6t_ah.ko
kernel/net/ipv6/netfilter/ip6t_eui64.ko
kernel/net/ipv6/netfilter/ip6t_frag.ko
kernel/net/ipv6/netfilter/ip6t_ipv6header.ko
kernel/net/ipv6/netfilter/ip6t_mh.ko
kernel/net/ipv6/netfilter/ip6t_hbh.ko
kernel/net/ipv6/netfilter/ip6t_rt.ko
kernel/net/ipv6/netfilter/ip6t_LOG.ko
kernel/net/ipv6/netfilter/ip6t_REJECT.ko
kernel/net/ipv6/ah6.ko
kernel/net/ipv6/esp6.ko
kernel/net/ipv6/ipcomp6.ko
kernel/net/ipv6/xfrm6_tunnel.ko
kernel/net/ipv6/tunnel6.ko
kernel/net/ipv6/xfrm6_mode_transport.ko
kernel/net/ipv6/xfrm6_mode_tunnel.ko
kernel/net/ipv6/xfrm6_mode_ro.ko
kernel/net/ipv6/xfrm6_mode_beet.ko
kernel/net/ipv6/sit.ko
kernel/net/ipv6/ip6_tunnel.ko

```

---

### Post by Chromagnum on 2010-03-25
> **DeMus said:**
> Just got home from work, sorry for the delay.
I had host lookup times in both Firefox and Chrome of more than 10 seconds. It was caused by a line in the file:
```
/etc/samba/smb/conf
```

In this file you can see the following line:
```
name resolve order = bcast host lmhosts wins

```
Make sure the word wins is at the end of the line. If not the computer will start to look for the webpage you want to see on your local computer, or your local network before it starts looking on the net.
This helped me a lot. I hope it will help you to.

I tried to gksudo gedit that but there is no conf file on my ubuntu. In there only 3 files: dhcp.conf, gdbcommands, smb.conf — all files in /etc/samba/ 
there is no /etc/samba/smb/

EDIT TO ADD:
I edited smb.conf anyway. Still no help.

---

### Post by DeMus on 2010-03-26
> **Chromagnum said:**
> I tried to gksudo gedit that but there is no conf file on my ubuntu. In there only 3 files: dhcp.conf, gdbcommands, smb.conf — all files in /etc/samba/ 
there is no /etc/samba/smb/

EDIT TO ADD:
I edited smb.conf anyway. Still no help.

Sorry, typo. The file name should be **/etc/samba/smb.conf**
After changing it did you do a restart? The conf file has to be re-read to use the latest settings.

---

### Post by lien_meat on 2010-03-26
@Chromagnum: This seems odd to me.  I just tested my ubuntu 9.10 64bit to see if I was having a similar issue and just never realized it, but using speedtest.net I had a ping of only 32ms...which I think is pretty decent. (I live in WA, USA)

So this got me thinking.  Are you perhaps under a router?  I'd suppose you have a cable modem or something, correct?  POSSIBLY there is some odd issue between ubuntu and your router firmware or your modem firmware, and this is not an issue in XP for some reason.  I'm no network expert by any means, but it makes sense to me at least.  Possibly when this started your ISP changed the firmware on your modem or something...I don't know.

A test that might help some(but probably not):
If you have another computer around that you can set up to serve something to you (a webpage since it seems your trouble is mostly over http...) like a webpage or a large file via apache or something.  Run that computer on your local network, and download something from it and see if your ping is still worse in ubuntu.  If not, then maybe it's something with your modem or router firmware...  If not, I'm completely out of ideas for you.

---

### Post by somnus520 on 2010-03-26
Looks like you have eliminated everything!

If it only happens on download, do any extra processes start up during a  download - a download manager of some kind? How are you doing your  downloads?
--------------------------
[oakley](http://*************************)  [oakley sunglasses](http://*************************)  [cheap oakley sunglasses](http://*************************)

---

### Post by Chromagnum on 2010-03-26
@DeMus
Yes, twice. Still doesn't help. I edited the line you suggested right under the smb.conf

@lien_meat
Don't have any router. I connect directly to cable modem. As far as firmware, I don't know much about this. I use Linksys BEFCMU10 version 1. Like this picture.
[IMG]http://i42.tinypic.com/2eofdk7.jpg[/IMG]
Only support USB & Ethernet. I'm using RJ-45. And sadly this is the only computer I have.

Maybe you were right; the problem in my modem. To be honest... I don't know anymore. I even tried disable all the HDD from bios and boot from live cd, just to see how the internet connection from there. Still the same result. So yeah, perhaps it is my modem or... ISP. 

@somnus520
Normally just click and let the browser handle it. Either Chromium or Firefox. For larger file, I use Jdownloader. Sometimes I use wget.

---

### Post by lien_meat on 2010-03-26
@Chromagnum: I'd actually be surprised if it was your modem.  If you were using a router, then I would probably say it was your router, but you aren't using one.  Modems are pretty simple, and I wouldn't think that it would be the cause, but unless there is something about your motherboard that ubuntu doesn't like(not even sure this is a valid idea), then I don't know what else it could be (besides your ISP), because it seems you've ruled everything else out.  I'm pretty much stumped.

Because you said you changed nics, I'm assuming you are using a desktop, so this idea might not be feasible:
Possibly you could take your computer somewhere where it connects to a different ISP using a different modem or over a lan and see if speed differs there.

You sir, have found the oddest little bug I think I have heard in a while. You should be proud...

---

### Post by Chromagnum on 2010-03-26
You know what... I gave up. I don't know what to do anymore. 2 days I've been roaming around here and there with no solution. Of course I learned a lot. A plus there I suppose.

Sorry for my bad English. I know lots of grammar mistakes.

Perhaps when Lucid release, everything will be okay. Almost April anyway. Hopefully. 

I still need suggestion, though. 

Anyway, thanks to all who help me.

---

### Post by cjhabs on 2010-03-26
> **Chromagnum said:**
> You know what... I gave up. I don't know what to do anymore. 2 days I've been roaming around here and there with no solution. Of course I learned a lot. A plus there I suppose.

Sorry for my bad English. I know lots of grammar mistakes.

Perhaps when Lucid release, everything will be okay. Almost April anyway. Hopefully. 

I still need suggestion, though. 

Anyway, thanks to all who help me.

I am at a loss also - how about unloading those ipv6 modules that show up via modprobe? I don't know too much about this, but recall reading another post where this was a solution to a similar problem.

---

### Post by Monotoko on 2010-03-26
Thats quite a strange little bug you have there...

Have you tried using another version of Ubuntu? Tis the only suggestion i can make, If that doesnt work, try Fedora or something and see if that works.

There is currently a Beta release of 10.04 you could try, Google "Ubuntu Lucid Beta 1"

---

### Post by john newbuntu on 2010-03-26
Just in case you have not stumbled upon this article by caljohnsmith, would you be interested in trying it out to see if you get any improvement at all?
[http://www.uluga.ubuntuforums.org/showthread.php?p=7098253](http://www.uluga.ubuntuforums.org/showthread.php?p=7098253)

Edit: Here's the launchpad bug: [https://bugs.launchpad.net/ubuntu/+bug/433972](https://bugs.launchpad.net/ubuntu/+bug/433972)

---

### Post by jshadwell on 2010-03-26
> **john newbuntu said:**
> Just in case you have not stumbled upon this article by caljohnsmith, would you be interested in trying it out to see if you get any improvement at all?
[http://www.uluga.ubuntuforums.org/showthread.php?p=7098253](http://www.uluga.ubuntuforums.org/showthread.php?p=7098253)


For the record the "TCP Receive Window (RWIN)" section of that article/post did the trick for me (thanks!). I'd been experiencing very similar issues (when downloading or downloading largish packages I couldn't get any other sites to respond - usually with DNS errors). When I tweaked the settings as per the instructions there the problem was resolved. I had disabled ipv6 too but that didn't make a difference.

---

### Post by 2hot6ft2 on 2010-03-26
I've seen 2 people that had winbind installed and removing it fixed their issues. So see if you have it installed and whether or not you need it. They were still able to use samba without it.

Also if I don't set my wifi to not connect automatically in network manager and I connect to a wired connection then my connection is awful. It seems that the network manager doesn't mind getting IP Addresses for both adapters but then it doesn't know which it wants to use and gets confused.

You can check if they both have IP Addresses with
```
ifconfig
```
and if the wifi has an IP Address while you're using a wired connection you can disable it temporarily using
```
sudo ifconfig wlan0 down
```
or whatever you wlan# is.

---

### Post by Chromagnum on 2010-03-27
@2hot6ft2 
I don't have any wifi. I'm using wired connection. But I will look into winbind, thanks.

@Monotoko
I'm thinking about it. Perhaps. I don't know... quite happy with Karmic. I read somewehere lucid has a problem with Network Manager so I kinda hesitate to upgrade.

@john newbuntu & jshadwell
I've read caljohnsmith article, I might do that. Thank you for the link. Since it has alot of testing and configuration, I thought perhaps tommorow due to some works I have to finish (I'm graphic designer, and yes I'm using gimp and inkscape for almost one and a half year now. Used to be Xp but now Ubuntu).

Anyway, recently keep an eye on system monitor network history and while downloading a file, the upstream connection is not like it used to be. Pretty huge. I figure this is the source of the problem. Not torrent, just normal download from a website. How do one lower the upstream connection?

---

### Post by smircopus on 2010-03-27
I upgraded my AT&T DSL connection from 785K to 6mps. Immediately downloads were screaming fast, but web pages took forever and sometimes not at all.

After jumping through a 1000 hoops trying to figure out this problem, I went to AT&T.  They had a powerpoint walk-through. The first suggestion was to turn off my modem and computer, then restart everything.

Walla! Now web pages load very quickly.

Hope that helps.

---

### Post by Chromagnum on 2010-04-06
After a week trying to set up RWIN, looking in to this and that (still with no satisfying result), I finally gave it a shot at Lucid Beta. (This was a desperate attempt). 

After upgrade from Karmic everything when smooth with minor exception; unable to load X server display configuration. But since I don't use twin monitor, everything went well (except for the boot splash gave me low resolution). But that another story. I already looking in to how to set it up the splash screen.

Verdict: I'm happy.

Everything went well. Don't have any problem with slow internet connection anymore. Everything working exactly just like it supposed to be. 2 days now since upgrade and I'm glad I decided to upgrade.

But I was curious, why Karmic behave like that and Lucid don't. I popped up Karmic Live CD again and booted from there. Surprisingly, Karmic on live CD gave me the same problem. 
This is my spec incase you guys wondering:
```
P4 3ghz
P5PE-VM mainboard
1 GB DDR 
Nvidia FX5500
Onboard LAN gigabit
```

Even more strange is, back then when I first install Karmic, none of this had ever happened. 

Oh well, anyway, problem solved. Lucid solves it.

Thanks to you guys all, I really do appreciated for helping me.

Regards,
Eric W.

---

