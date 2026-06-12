---
title: "Remote Access Needed"
date: 2010-03-19
forum: General Help
---

### Post by Vossy on 2010-03-19
Hello Guru's, 
Hopefully someone can help me I am very new to Ubuntu, Have just migrated from windows XPs on all 4 of my machines, it is a steep learning curve and I am doing OK, but I have one major hurdle to overcome. I work away overseas and I take my laptop with my and I need to log in to my home PC to add more torrents etc whilst I am gone, for the life of me I am getting super confused with everything that is out there to be used and I was hoping someone could give a uber newbie a step by step guide through how to set this up??
Please help as I have found Ubuntu and Linux in general to be awesome :p and don't ever want to go back to Win. Any help please.

---

### Post by phildini on 2010-03-19
Could you describe your problem a bit more? Are all your machines running Ubuntu now? Do you have particular torrent software you're using, and do you just want to add torrents or are you interested in full remote control of your computer?

---

### Post by dandnsmith on 2010-03-19
I think, first off, that you need to work out (or post) what you have in your home internet provision - are you on fixed IP address(es), or will you need to register with a dynamic provider which can track any change of IP address so you can still access the machine.
Then you can work out whether to go for a simple login, a secure login, a VPN ...

---

### Post by Vossy on 2010-03-19
Hey Guys,
Thanks so far, I only want to access one PC at home that and the laptop are running Ubuntu 9.10. The torrent program I use is utorrent running under wine, will find something better later. I basically need full control over the pc to add more torrents to download list or occasionally find a file word file or something like that. So ideally fully control but for now would be super happy with just adding torrents?  Sorry not to up to date on the IP address stuff I guess whatever is the standard you get from your ISP.

---

### Post by Vossy on 2010-03-19
Anyone got any ideas for me??

---

### Post by Vossy on 2010-03-20
Just wondering if anyone can help me out here??

---

### Post by jrssystemsnet on 2010-03-20
The first thing you need is dynamic dns, so that you can get to your home computer even if your ISP changes your IP address.  Check noip.org for that; if you don't like them, google around - there are plenty of providers.

After that, you need to forward the remote control port through your router to your home PC.  If you don't know how to do that... the answer is going to vary DRASTICALLY depending on your equipment; we probably can't help you directly with configuring your router.

After that, you can decide what remote control application you want to use.  Your best bet for what you want to do is xrdp, and lucky for you, I've got an xrdp how-to guide [here](http://ubuntuwiki.net/index.php/Xrdp,_installing).

(A note to the kibitzers out there: no, FreeNX will not work for what the OP wants, because he's going to want to control his LOCAL session, not a new session by way of NX.)

---

### Post by dandnsmith on 2010-03-20
With a fixed IP, my understanding is that you could address the PV directly - only need the dynamic dns if you want domain name associated with the address.
Could be a security benefit to not having the name association.

There is also the situation where the ISP doesn't assign a routable IP address - you see this with mobile phone setups, but also the odd ISP - so the external IP is something like:
192.168.xxx.yyy
If so, good luck with your endeavours, as I've no idea how you get round that one.

---

