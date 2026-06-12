---
title: "Freezing mouse pointer"
date: 2011-12-19
forum: General Help
---

### Post by elite4seth on 2011-12-19
So yeah, i really don't understand it, but it usually happens when im web browsing, though i can't say that it only does it then because i'm pretty much always on the Internet. When it happens, my mouse just stops moving. I can still use two fingers to scroll (i'm on an aluminum macbook) and i can still right click. I've navigated to my terminal, but to be honest, i don't even know what to look for being a linux noob. This has been happening for a week or two, and it fixes itself on a restart, but that's kind of annoying. Any help?

---

### Post by pretty_whistle on 2011-12-19
Have you tried cleaning the mouse pad really good and being sure your surfing finger is the same?

These things are really sensitive to grime.

---

### Post by elite4seth on 2011-12-19
yeah i cleaned it, but i don't really think that would make the movement on the mouse stop, would it?

---

### Post by tgalati4 on 2011-12-19
Open a terminal and right-click (Keep on Top).

dmesg | tail -f

Do some browsing and wait for a freeze.  Write down any messages that pop up.

---

### Post by elite4seth on 2011-12-19
> **tgalati4 said:**
> Open a terminal and right-click (Keep on Top).

dmesg | tail -f

Do some browsing and wait for a freeze.  Write down any messages that pop up.


Thanks, i have a gauke window open as im browsing google for some help using touchegg, can i ask for an explanation of the cmd you gave me? i'm still learning =]

---

### Post by pretty_whistle on 2011-12-20
> **elite4seth said:**
> yeah i cleaned it, but i don't really think that would make the movement on the mouse stop, would it?
It could if the grime was there in the right way.

But you cleaned it so that rules that out.

---

### Post by elite4seth on 2011-12-24
So i've noticed when this seems to happen. Whenever i'm in firefox and i use a google image search, while i'm scrolling through the pictures, it almost never fails to freeze up. Can anyone help, given this new info?

---

### Post by elite4seth on 2011-12-24
> **elite4seth said:**
> So i've noticed when this seems to happen. Whenever i'm in firefox and i use a google image search, while i'm scrolling through the pictures, it almost never fails to freeze up. Can anyone help, given this new info?

Actually, my mouse just froze again, i have the dmesg | tail -f thing that somone suggested open in terminal, how do i copy and paste that log here without a mouse?

---

### Post by kalfusisagod on 2011-12-24
you can output any terminal to with the > character. I would run:

dmesg | tail -f > ~/Desktop/dmesg.txt

This should put a "dmesg.txt" file onto your desktop and then you can open it and paste the message into your browser

Hope this helps and remember learning the command line will be essential to any Linux distro

---

### Post by elite4seth on 2011-12-24
> **kalfusisagod said:**
> you can output any terminal to with the > character. I would run:

dmesg | tail -f > ~/Desktop/dmesg.txt

This should put a "dmesg.txt" file onto your desktop and then you can open it and paste the message into your browser

Hope this helps and remember learning the command line will be essential to any Linux distro
  

Thanks sir =] i actually have read up enough to know how to do that command,  just couldn't recall the information, so thank you very much =] the simplicity of it kind of amazed me. i'm still pretty new as you can tell. 

I have one more question, i've seen ppl post their command in a nice grey box on these forums, how do i do that for the dmesg output so it doesn't look so sloppy?

---

### Post by kalfusisagod on 2011-12-24
That's a good question. I think you have to wrap CODE tags in brackets around them. I'm note sure if I can do it. Lets see.

```

Blah Blah
Blah

```So you type [ CODE ] code goes here [ / CODE ] 

But without the spaces. Then click preview post on bottom to verify before you post. Hope this helps. Also, if you're in the rich text editor on the forum (the one with all the buttons and smiley faces) then you can hoover your mouse over the # sign to insert the code tags automatically. The buttons are not there in the quick reply box, but i think the code tags still work.

---

### Post by elite4seth on 2011-12-24
Welp this is what i came up with. heres my output after the mouse freeze


```

[ 1664.106478] [UFW ALLOW] IN= OUT=eth2 SRC=192.168.1.7 DST=192.168.1.1 LEN=57 TOS=0x00 PREC=0x00 TTL=64 ID=13346 DF PROTO=UDP SPT=38371 DPT=53 LEN=37 
[ 1664.118699] [UFW ALLOW] IN= OUT=eth2 SRC=192.168.1.7 DST=192.168.1.1 LEN=54 TOS=0x00 PREC=0x00 TTL=64 ID=13349 DF PROTO=UDP SPT=50788 DPT=53 LEN=34 
[ 1664.133880] [UFW ALLOW] IN= OUT=eth2 SRC=192.168.1.7 DST=192.168.1.1 LEN=57 TOS=0x00 PREC=0x00 TTL=64 ID=13353 DF PROTO=UDP SPT=36323 DPT=53 LEN=37 
[ 1664.146842] [UFW ALLOW] IN= OUT=eth2 SRC=192.168.1.7 DST=192.168.1.1 LEN=65 TOS=0x00 PREC=0x00 TTL=64 ID=13356 DF PROTO=UDP SPT=57593 DPT=53 LEN=45 
[ 1664.163799] [UFW ALLOW] IN= OUT=eth2 SRC=192.168.1.7 DST=192.168.1.1 LEN=60 TOS=0x00 PREC=0x00 TTL=64 ID=13360 DF PROTO=UDP SPT=59365 DPT=53 LEN=40 
[ 1676.064166] [UFW AUDIT] IN= OUT=eth2 SRC=192.168.1.7 DST=204.9.163.163 LEN=60 TOS=0x00 PREC=0x00 TTL=64 ID=15150 DF PROTO=TCP SPT=46518 DPT=80 WINDOW=14600 RES=0x00 SYN URGP=0 
[ 1676.064179] [UFW ALLOW] IN= OUT=eth2 SRC=192.168.1.7 DST=204.9.163.163 LEN=60 TOS=0x00 PREC=0x00 TTL=64 ID=15150 DF PROTO=TCP SPT=46518 DPT=80 WINDOW=14600 RES=0x00 SYN URGP=0 
[ 1677.292945] [UFW AUDIT] IN=eth2 OUT= MAC=ff:ff:ff:ff:ff:ff:00:21:00:aa:6d:5b:08:00 SRC=192.168.1.70 DST=255.255.255.255 LEN=42 TOS=0x00 PREC=0x00 TTL=128 ID=18358 PROTO=UDP SPT=63222 DPT=3289 LEN=22 
[ 1700.128149] [UFW AUDIT] IN= OUT=eth2 SRC=192.168.1.7 DST=204.9.163.163 LEN=60 TOS=0x00 PREC=0x00 TTL=64 ID=15151 DF PROTO=TCP SPT=46518 DPT=80 WINDOW=14600 RES=0x00 SYN URGP=0 
[ 1700.128162] [UFW ALLOW] IN= OUT=eth2 SRC=192.168.1.7 DST=204.9.163.163 LEN=60 TOS=0x00 PREC=0x00 TTL=64 ID=15151 DF PROTO=TCP SPT=46518 DPT=80 WINDOW=14600 RES=0x00 SYN URGP=0 
```

---

### Post by elite4seth on 2011-12-30
any help on this would be greatly appreciated, I have been tending not to use xubuntu as my main browser lately because of this freezing issue, an that really makes me sad since i'm trying to learn it.

---

### Post by tgalati4 on 2011-12-31
Those are firewall messages, so they are not helpful.  Try
cat .xsession-errors

---

### Post by elite4seth on 2012-01-01
> **tgalati4 said:**
> Those are firewall messages, so they are not helpful.  Try
cat .xsession-errors

should i wait till my mouse freezes and try that? or just try it now, when things are working fine?

---

### Post by LinuxCharms on 2012-01-01
Do both, just try it with the frozen first.

I was thinking you could try changing the mouse settings. And make sure the USB port that you're using isn't screwed up, because I've had the same thing happen just simple because the mouse/and or port was bad.

The mouse settings are in: Settings>Settings Manager>Mouse

---

