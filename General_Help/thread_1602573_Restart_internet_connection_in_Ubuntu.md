---
title: "Restart internet connection in Ubuntu?"
date: 2010-10-21
forum: General Help
---

### Post by cAlpha on 2010-10-21
I did a bit of searching, but I guess I'm not sure of the terminology associated with what I'm trying to do.

I'm currently connected via ethernet port (NOT wireless) to my DSL modem.

Every so often my connection gets 'saturated', typically after or during a lot of bittorrent activity that maxes out my bandwith, and my speeds drop markedly, even if the bandwith isn't currently being maxed out.  I'm not sure whether it's my ISP throttling my connection or something else, but as a work around, I typically just disconnect my modem from the outlet and then replug to restore normal speeds.

Is there a way to 'restart' my modem from the command line in a similar way without having to physically turn off my modem to get the desired effect?

---

### Post by 3Miro on 2010-10-21
If your modem has a web interface that you can connect to, you may be able to restart it from there (depends on the modem/setup). In Ubuntu you can either disable/re-enable wired connections (form the network manager icon) or you can type in a terminal:
```
 services NetworkManager restart 
```
(I am not 100% sure about the command)

If it is not a ISP issue, the above should work, otherwise it is something about modem/isp. You can also adjust the torrent client to not use 100% of your network speed and that may help keep things more stable.

---

### Post by cAlpha on 2010-10-21
> **3Miro said:**
> If your modem has a web interface that you can connect to, you may be able to restart it from there (depends on the modem/setup). In Ubuntu you can either disable/re-enable wired connections (form the network manager icon) or you can type in a terminal:
```
 services NetworkManager restart 
```
(I am not 100% sure about the command)

If it is not a ISP issue, the above should work, otherwise it is something about modem/isp. You can also adjust the torrent client to not use 100% of your network speed and that may help keep things more stable.

Thanks for your reply.  The command you suggested didn't work, but I *think* the combination of manually turning off networking via the NetworkManager applet AND disconnecting via my modem web interface will achieve the desired effect.  I guess I'm wondering if there's a command that can do both though--perhaps I'm being overly optimistic.

Regarding my BT settings, I've currently got my torrent client to max out at 90% of my bandwith (per speedtest), so I don't think it's a BT issue really, more something related to my ISP/modem/something else.

---

### Post by ammoun on 2010-10-21
What is you DSL modem? There should be a script to reboot it :)

---

### Post by cAlpha on 2010-10-21
> **ammoun said:**
> What is you DSL modem? There should be a script to reboot it :)

It's an Actiontec GT701-WG.

---

### Post by ammoun on 2010-10-22
[http://www.slyck.com/forums/viewtopic.php?f=36&t=16042](http://www.slyck.com/forums/viewtopic.php?f=36&t=16042)
[http://www.dslreports.com/forum/remark,13388402~days=9999](http://www.dslreports.com/forum/remark,13388402~days=9999)

Check these two links and tell me if you had any improvements.

---

### Post by cAlpha on 2010-10-22
> **ammoun said:**
> [http://www.slyck.com/forums/viewtopic.php?f=36&t=16042](http://www.slyck.com/forums/viewtopic.php?f=36&t=16042)
[http://www.dslreports.com/forum/remark,13388402~days=9999](http://www.dslreports.com/forum/remark,13388402~days=9999)

Check these two links and tell me if you had any improvements.

I'd seen the first but was somewhat hesitant running an exe I found on a random site off the internet--the second site, however, gave the process and resolved (at least temporarily) my problem.  Perfect, thanks!  

FWIW, "telnet 192.168.0.1 --> reboot" was the answer to the specific question I posed originally, but the rest is helpful as well.  Thanks, all!

---

