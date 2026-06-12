---
title: "Install Tor"
date: 2012-04-23
forum: General Help
---

### Post by gurrunaki on 2012-04-23
Hi all, I'm running ubuntu 11.10 in a Toshiba portege Z830 64 bits and I try install Tor browser following this tutorial I found [http://www.youtube.com/watch?v=cXOEA8rXdew](http://www.youtube.com/watch?v=cXOEA8rXdew) the think is when I finished install tor and follow the second that is sudo gedit  /etc/polipo/config  the window that appear is empty and in the terminal say that is not such file or directory, any sugestion?

Thanks in advance!!!

---

### Post by jim_deadlock on 2012-04-23
That tutorial is WRONG! Firstly, the Tor FAQ has always said NOT to install Tor from the repositories because the package is permanently out of date. Secondly, it is no longer necessary to install Tor, all you need to do is download the Tor browser bundle and run it, no installation is necessary.

[Tor Browser Bundle]("https://www.torproject.org/download/download-easy.html.en")

---

### Post by gurrunaki on 2012-04-23
Thanks jim_deadlock for your fast reply, I did what u said, and I have already installed. Now when I'm  going to the folder and double click in start tor browsing, give me an error telling vidalia exited abnormally, not idea, I  think I should read much more about it. I used run it in Windows, but now I see with linux is much more different, and I'm newbie with it :(

---

### Post by gurrunaki on 2012-04-23
Thanks jim_deadlock for your fast reply, I did what u said, and I have  already installed. Now when I'm  going to the folder and double click in  start tor browsing, give me an error telling vidalia exited abnormally,  not idea, I  think I should read much more about it. I used run it in  Windows, but now I see with linux is much more different, and I'm newbie  with it :sad:

---

### Post by zombifier25 on 2012-04-23
Try running
```
sudo apt-get remove tor
```in the terminal and then restart Vidalia from the bundle.> **jim_deadlock said:**
> That tutorial is WRONG! Firstly, the Tor  FAQ has always said NOT to install Tor from the repositories because the  package is permanently out of date. Secondly, it is no longer necessary  to install Tor, all you need to do is download the Tor browser bundle  and run it, no installation is necessary.

[Tor Browser Bundle]("https://www.torproject.org/download/download-easy.html.en")
Actually, the repo provided by torproject.org itself is up to date. This is useful if you don't want to use Tor but want to use your computer as a relay to help others (like my case)

---

### Post by techsupport on 2012-04-23
> **gurrunaki said:**
> Hi all, I'm running ubuntu 11.10 in a Toshiba portege Z830 64 bits and I try install Tor browser following this tutorial I found [http://www.youtube.com/watch?v=cXOEA8rXdew](http://www.youtube.com/watch?v=cXOEA8rXdew) the think is when I finished install tor and follow the second that is sudo gedit  /etc/polipo/config  the window that appear is empty and in the terminal say that is not such file or directory, any sugestion?

Thanks in advance!!!

Tor isn't recommended anymore. You have sniffers at the ends of all of those anonymous servers worldwide. Why don't you use VPN instead?

---

### Post by jim_deadlock on 2012-04-23
[QUOTE=11866860]
Actually, the repo provided by torproject.org itself is up to date.[/QUOTE]

Yes indeed but the guy in the video was installing from the Ubuntu repo which is a classic schoolboy error.

---

### Post by fara on 2012-04-23
> **techsupport said:**
> Tor isn't recommended anymore. You have sniffers at the ends of all of those anonymous servers worldwide. Why don't you use VPN instead?

Well free VPNs are not usually much safer, are they? By the way do you know any good ones? free or not very expensive.

Cheers

---

### Post by techsupport on 2012-04-23
> **fara said:**
> Well free VPNs are not usually much safer, are they? By the way do you know any good ones? free or not very expensive.

Cheers

They are low profile, which is your best bet now.. If you want to be serious about what you are doing, it won't be free. CISCO business routers with VPN around 200 us dollars. You will need remote hosts too. Those aren't free unless you have access to a edu org server somewhere because you installed it for them.

---

### Post by fara on 2012-04-23
> **techsupport said:**
> They are low profile, which is your best bet now.. If you want to be serious about what you are doing, it won't be free. CISCO business routers with VPN around 200 us dollars. You will need remote hosts too. Those aren't free unless you have access to a edu org server somewhere because you installed it for them.

Thanks

---

### Post by gurrunaki on 2012-04-23
Just a small say about VPN, I&#7743; getting crazy try find a good one, actually I have vpntunnel which I can not install in my distro from ubuntu and I can only run in windows. Just few days ago I read that Sweden is not anymore a safety country like used to be about protection of data. Iceland looks to be the perfect one at the moment, many blogers with political problems are there, so I tried find a VPN wich company is hosted in Iceland, with the option pay with paysafecard, ufff, I asking much????

---

### Post by |{urse on 2012-04-23
> **techsupport said:**
> Tor isn't recommended anymore. You have sniffers at the ends of all of those anonymous servers worldwide. Why don't you use VPN instead?
 
On whose authority was this conclusion arrived at? Yes, exit nodes can potentially be sniffed, this does not mean "You have sniffers at the ends of all of those anonymous servers worldwide". 
 
VPN's cost money, therefore tying you to payment data.. unless you go nuts and do a prepaid card at a gas station that you are sure has no security cameras (totally being sarcastic here but you get the point) you could have that prepaid card sent to a p.o. box (oh lord, you need a faked ID to do that anonymously), you can set up a p.o. box online You do the math on that.
 
For my money ($0), tor-browser on a live-cd is full of win. Proxy chains browsed via a live-cd with a spoofed MAC = even better.

---

### Post by zombifier25 on 2012-04-24
> **techsupport said:**
> Tor isn't recommended anymore. You have sniffers at the ends of all of those anonymous servers worldwide. Why don't you use VPN instead?
Yes, but that doesn't mean ALL nodes are bad. In fact, even if bad nodes can read your information, they still don't know where that traffic originated from.
I would choose Tor over VPNs everyday, because Tor is really hard to take down.

---

### Post by gurrunaki on 2012-04-24
I have another question, running a IRC client like kvirc or XChat under Tor? Will keep your connexion hidden?

---

### Post by |{urse on 2012-04-24
Yes it is possible to set it up.. it isn't automatically going to work that way, but its much easier to install the chatzilla plugin to tor browser.

---

### Post by techsupport on 2012-04-24
> **|{urse said:**
> On whose authority was this conclusion arrived at? Yes, exit nodes can potentially be sniffed, this does not mean "You have sniffers at the ends of all of those anonymous servers worldwide". 
 
VPN's cost money, therefore tying you to payment data.. unless you go nuts and do a prepaid card at a gas station that you are sure has no security cameras (totally being sarcastic here but you get the point) you could have that prepaid card sent to a p.o. box (oh lord, you need a faked ID to do that anonymously), you can set up a p.o. box online You do the math on that.
 
For my money ($0), tor-browser on a live-cd is full of win. Proxy chains browsed via a live-cd with a spoofed MAC = even better.

I'm not going to teach someone how to set up secured tunneling with VPNs on a public forum to be truly anonymous. This is for new Ubuntu users. Besides, I would rather use my own installed VPNs and private tunneling and my own blackboxes bouncing it securely around the world first instead of TOR that is already on their gov/org watch lists. That's crazy. TOR is not anonymous anymore guys. Be real. That's how you go to jail eventually or find yourself in some dungeon somewhere - and debugging code for the rest of your lives in a basement in some "unknown" location. ha ha ha no thank q.

over and out!

---

### Post by |{urse on 2012-04-24
You are clearly misinformed and irresponsibly paranoid. Can you offer up some evidence of tor's insecurity? Jail? A dungeon? Are you high? All the best!

---

### Post by techsupport on 2012-04-24
> **|{urse said:**
> You are clearly misinformed and irresponsibly paranoid. Jail? A dungeon? Are you high? All the best!

I'm not using TOR for anything except to show users a history lesson about internet privacy, and what not to use anymore. Thanks though. :) 

Have fun debugging code in basement somewhere after you get busted.

Cheers! 

:lolflag:

---

### Post by |{urse on 2012-04-24
Busted doing what? What are you insinuating? You left out the part where you prove your contention.

---

### Post by techsupport on 2012-04-24
> **|{urse said:**
> Busted doing what? What are you insinuating? You left out the part where you prove your contention.

Ha ha ha..  Right, not doing nothing. That might work with them, not me. NIMBY. 

I love your sense of humour.  You got some secret agent man sitting at the end of those TOR servers reading about your latest adventures in the world reading celebrity gossip web sites or something. I bet you guys sure keep boris badenov entertained. lol

Cheers!

---

### Post by |{urse on 2012-04-24
techsupport

Last Activity: 1 Minute Ago
Current Activity: Modifying Post

^ lol

I'm just gna ride this till I reach 1k beans wo0

---

### Post by |{urse on 2012-04-24
> Ha ha ha.. Right, not doing nothing. That might work with them, not me. NIMBY. lol

Who exactly are "they" and what on earth have they done to you? It's ok you're using a vpn, you can tell me. They can't hurt you **anymore**

---

### Post by techsupport on 2012-04-24
> **|{urse said:**
> Who exactly are "they" and what on earth have they done to you? It's ok you're using a vpn, you can tell me. They can't hurt you **anymore**

You can post with the lag on tor right now? You must be a very patient user. lol

You are lucky right if you can view one page per minute during load time on Tor, right?

Boris is giggling to himself right now reading this while you post with TOR. 

just messing with you man..  

Cheers

---

### Post by |{urse on 2012-04-24
I'm not using tor at the moment, are you okay? If you need to argue with someone there's always 4chan?


1k beans, the last 4 were ill-gotten but at the very least entertaining.

---

### Post by techsupport on 2012-04-24
> **|{urse said:**
> I'm not using tor at the moment, are you okay? If you need to argue with someone there's always 4chan?

But you might be detected? You're no longer cloaked. kee kee kee

---

### Post by |{urse on 2012-04-24
I'd gladly hand you my ip as I'm fairly certain you couldn't hack your way out of a paper bag with a script and a vpn. Muah <3

---

### Post by techsupport on 2012-04-24
> **|{urse said:**
> I'd gladly hand you my ip as I'm fairly certain you couldn't hack your way out of a paper bag with a script and a vpn. Muah <3

Besides TOR you can always just use some nice sturdy couch cushions and build a fort. lol

Just kidding. 

Cheers!

---

### Post by zombifier25 on 2012-04-25
techsupport: As far as I know, you're bashing the Tor network without any proof at all.
Yeah, Tor is unsafe, nothing is safe, including VPNs. Yet the [Silk Road](https://en.wikipedia.org/wiki/Silk_Road_%28website%29) website is still up and running. And don't even mention the Hidden Wiki. If Tor is not anonymous, the feds would have booked thousand of drug users and pedobears now.
(I know these two are bad uses of Tor, really, really BAD uses of Tor, but I just want to point that out)

---

### Post by gurrunaki on 2012-04-25
I downloaded Tor from the link was posted here, after it, I go to the tor folder and double click in the icon start tor browsing, they give some options and I choose run, after it gave me an error telling

Vidalia exited abnormally. Exit Code 2

Any idea what I&#7743; doing wrong?

Thanks in advance!!!

---

### Post by jim_deadlock on 2012-04-25
Did you do the following?

> **zombifier25 said:**
> Try running
```
sudo apt-get remove tor
```in the terminal and then restart Vidalia from the bundle.

Your original installation of Tor/Vidalia may be conflicting with your browser bundle so you should make sure the installation is removed.

---

### Post by techsupport on 2012-04-25
> **zombifier25 said:**
> techsupport: As far as I know, you're bashing the Tor network without any proof at all.
Yeah, Tor is unsafe, nothing is safe, including VPNs. Yet the [Silk Road]("https://en.wikipedia.org/wiki/Silk_Road_%28website%29") website is still up and running. And don't even mention the Hidden Wiki. If Tor is not anonymous, the feds would have booked thousand of drug users and pedobears now.
(I know these two are bad uses of Tor, really, really BAD uses of Tor, but I just want to point that out)

You want me to provide you proof that they have monitors at the ends of those anonymous Tor servers worldwide to intercept the IPs of users using TOR for illegal activity?  Are you kidding me? This is a new user forum to help people use Ubuntu. Get it? I'm telling you what I was told by the blackhat/whitehat technicians I went to school with years and years ago. Their job now is exactly what I am telling you is happening, and I just can't get into that subject on a public forum. That's dumb. I'm not bashing. It's not personal, and I am just trying to help point new users in the right direction. If you want to be truly anonyous, TOR isn't the way to do it. That's all.  Period. If you use TOR expect to be monitored at the other ends of where those TOR anonymous servers are connected - around the clock. Yes, it wasn't like that years and years ago, but trust me, it is now.

Cheers

:guitar:

---

### Post by gurrunaki on 2012-04-25
Thanks techsupport, my idea was surf under tor and vpn together under ubuntu, but now... I really don know what is better for surf anonymous on internet, what do you suggest???

I really will appreciate some advice cos maybe I&#7743; going in the wrong direction.

Cheers!!!

---

### Post by techsupport on 2012-04-25
> **gurrunaki said:**
> Thanks techsupport, my idea was surf under tor and vpn together under ubuntu, but now... I really don know what is better for surf anonymous on internet, what do you suggest???

I really will appreciate some advice cos maybe I&#7743; going in the wrong direction.

Cheers!!!

I think you need to find a better forum, not a public forum for what you want to do. 

That's crazy.

---

### Post by gurrunaki on 2012-04-25
I catch it, but anyway, even like that, I still a bit lost :confused: if you can be kind, pls feel free give me  some clue here or by PM, really, really will be much appreciate and a big help, if you understand what I mean...

---

### Post by techsupport on 2012-04-25
> **gurrunaki said:**
> I catch it, but anyway, even like that, I still a bit lost :confused: if you can be kind, pls feel free give me  some clue here or by PM, really, really will be much appreciate and a big help, if you understand what I mean...

No, this is a public forum for new Ubuntu users. You are in the wrong place dude.

Keep it up and you will be flagged. Careful. ):P

---

### Post by jim_deadlock on 2012-04-25
@gurrunaki - why don't you just ignore the troll and go ahead and do what you originally intended to do, which is to use Tor in the same way that millions of other people are happily doing without any problem.

---

### Post by gurrunaki on 2012-04-25
Yeap!!! I completely understand, but understand my try :p I will search in other places and I hope will be trusted the advices I can get get from there.
I will close this thread cos like I see, I think I&#7743; not much interested in Tor anymore.

Thousands of thanks to all of you that was trying help with it.

;) :p ):P

BTW I will find how to mark like solved and I will do, I need check it, I&#7743; newbie here!!!

---

### Post by techsupport on 2012-04-25
> **jim_deadlock said:**
> @gurrunaki - why don't you just ignore the troll and go ahead and do what you originally intended to do, which is to use Tor in the same way that millions of other people are happily doing without any problem.

a.) I'm not a troll.

b.) I'm a cert technician 15 years now.

c.) if you want to hang around in a new user forum not intended for this kind of help, you probably aren't going to find it. Actually, you will probably get nailed. 

But don't listen to me. Listen to the guy with the KISS acid trip avatar to tell you everything is cool. Riiiight.

TOR is obsolete today.  Find out the hard way if you wish. Fine by me. 


:lolflag:

---

### Post by |{urse on 2012-04-25
I have 15yrs employed tech exp also, and that guy up there is fullovit. Tor is good, it works. Notice how he didn't offer you an alternate solution at all? The issue you mentioned with tor browser is due to the deprecated tor package being installed. Remove it and your issue will likely disappear.

By using an anonymous network you are not breaking any laws and that guy is assuming a LOT by saying you WILL be flagged.

---

### Post by oldos2er on 2012-04-26
Closed. 

Everyone take a deep breath, and review the forum's CoC: [http://ubuntuforums.org/index.php?page=policy](http://ubuntuforums.org/index.php?page=policy)

---

