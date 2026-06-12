---
title: "Torrent speeds"
date: 2010-08-22
forum: General Help
---

### Post by rodney_blue on 2010-08-22
I am at a loss here.  I have been using torrents for a few years now, yes I know that if you have no seeds you get no speed. 

10.04 clean install 
torrent clients tried: transmission 
ktorrent and bittorent
no router, 

in ubuntu I barely get 20Kbs downloads. in windows I can get 200kbs. 
yes the ports for the clients have been opened, even disabled the ufw, left everything open, still only 20 if that, lot of time getting only 50bs.. not even a K... sigh. 

so having opened all the ports, tried public torrents, couple different clients, I am still not achieving the speeds that most on here say they are getting using ubuntu. 

if anyone has any **real **suggestions please help! I would like to ditch windoze completely but not if I have to wait for a day and half to get a 20 minute publicly broadcast tv show. 

once again, **yes the ports have been opened, yes the torrents have 1000+ seeds. **
Thx, 
one really frustrated new user. ):P

---

### Post by techunit on 2010-08-22
You could be running into problems with the networking settings in place. Check out downloadthemall for firefox. try downloading to Iso for Ubuntu not the torrent with download them all. If you get good speeds say 200kps, then there is some other problem. If you get 20kbs, then the network parameters set in Ubuntu are wrong.

---

### Post by amauk on 2010-08-22
This could be an differences in how torrent clients report speed

Some will report kilo-**bits** per second
Others kilo-**bytes** per second

Purely guessing, here
but suppose your Windows torrent client did kilo-bits, and your Linux torrent client reported kilo-bytes per second

200 kilobits/sec * 1000 = 200,000 bits/sec

200,000 bits/sec / 8 = 25,000 bytes/sec

25,000 bytes/sec / 1024 = 24.4 kilobytes/sec

*edit*
so yeah, just make sure you're comparing like-for-like

you're likely to only encounter kilobits/sec (kbps) or kilo(kibi)bytes/sec (KiB/s)

Little b = bits
Big B = bytes

---

### Post by partloer on 2010-08-22
I would suggest you try some bandwidth meters on Ubuntu to get a baseline of what you internet speed is with Ubuntu.  Compare Ubuntu speed with Windows to make sure that there is nothing wrong.  Once you know that the internet with Ubuntu is work fine then look into bittorrent.

---

### Post by rodney_blue on 2010-08-23
Thanks for the responses:  chk'd into a couple things,  clients on ubuntu and windows both show speed in KB/s   windows clients still give me between 150KB/s and 170KB/s this is with bitdefender and peerblock both running as well as the windoze firewall. 

ubuntu using both transmission and ktorrent will only get as high as 20KB/s nothing more. yet uploads get into the 100s of KB/s this is with the ufw enabled and disabled and yes again the ports are all opened with the firewall client and verified.

also chk'd network setting in both they are identical and use the same wireless connection.  All setting appear to be the same. 
when I run speed tests I get the same results using windows and ubuntu. 

so now I am more at a loss.

is there an indepth tutorial on how to the network settings I can read ? found some but they were rather simplistic and offered little to no info that would help me out. 
thanks again. 
glad there is a support function here ;)

---

### Post by 3Miro on 2010-08-23
I can get full speed on both Transmission and KTorrent under *ubuntu. The issue is somewhere in your specific setup, not Ubuntu in general. Also, you are not using both clients at the same time, right? You should use only one at a time.

In the past I have used several setups and my experience is that wireless tends to be worse than wired in terms of torrents, however, I have been able to get 2MB/s on good connection. My current setup is: Cable modem -> Router -> Redirect ports to the default Transmission port -> Wired Desktop.

One more note, if you have high out rate vs in rate, you may want to limit the out rate a bit. This helps sometimes on connections with disproportionate in/out rates.

---

### Post by amauk on 2010-08-23
are you using the same torrent on both systems?
and are you getting the same (or similar) numbers of peers on both systems?

---

