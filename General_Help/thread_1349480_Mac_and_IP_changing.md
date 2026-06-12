---
title: "Mac and IP changing?"
date: 2009-12-08
forum: General Help
---

### Post by Alseimik on 2009-12-08
I'm new to ubuntu, and the hole unix system at all. My school is categorising our computers in something like "he may this, but not this" for example are all IM protocols banned for me. This is only for us pupils computers, all other are allowed to do all. So, a friend figured out that if he on boot changed his IP and MAC addresses, he was free on the internet.

I know something like this can be done on ubuntu, because i found a Danish distribution of Kubuntu, named "Polippix" which is designed to let the user be "invisible" on the net. (Dynamic IP, changing Mac on boot, uses the TOR system" etc.) But unlucky this isn't a very well made distribution. Many futures doesn't work optimally, and the media players doesn't work at all on my little Eee. (at least for me)

I've had a EasyPeasy distribution, which is just a redesign of the ubuntu netbook version. But i't works great.

So, how can I, or what to install to make EasyPeasy, or the normal ubuntu netbook, changing/lying about is MAC address and have a Dynamic IP for sure? just so it make up a random IP and MAC on boot, that would be perfect! help?

---

### Post by lisati on 2009-12-08
Careful: working WITH the administrators of a network is always preferable to trying to bypass their rules.

---

### Post by EndPerform on 2009-12-08
> **lisati said:**
> Careful: working WITH the administrators of a network is always preferable to trying to bypass their rules.

Agreed.  If you get caught, you may end up with no net at all, period.

---

### Post by Alseimik on 2009-12-08
Sorry for not making clear of this, theres no rule say i may not, the admins/school neither say we may not. They only say that we may not on their Windows laptops which we have. Thats because of a agreement with Microsoft when they bought their license (Its a bit ******, I dont understand that one, but I am sure that the rules say this) And know I'm on a unix laptop, so i will not break any rule. But the school has to make sure that im not dual booting or what they are afraid of, so my mac and IP is banned. Thats why I want it changed.

So I'm breaking no rules here/makes no angry admins.

---

### Post by i.r.id10t on 2009-12-08
man ifconfig

---

### Post by dullard on 2009-12-08
A few things...

If you need to ask how to do it, you're probably not as clued up as your admin(s) ;o)

I'd doubt very much that your school network policy is as simple as you think either.

And anyway, if you succeed. How good are you at keeping it a secret? (that's a multi-faceted question there. Give it some intelligent consideration...) :-)

---

### Post by doas777 on 2009-12-08
there is a script in the repos that is called macchanger. you may find it useful.

---

### Post by pricetech on 2009-12-08
If you don't like the restrictions on your school network, go somewhere else to connect.  The restrictions are there for a reason.

---

### Post by dullard on 2009-12-08
...also it might be worth mentioning the old adage that states: "There's no such thing as ignorance in the eyes of the law". Just because you haven't been told whether something is against the rules, it doesn't mean that it isn't.

This is especially worth noting at school or in the workplace.

Go on. Admit you do actually know you want to be a bit naughty here ;o)

---

### Post by Alseimik on 2009-12-08
how do i use ifconfig to change it? (I aint no pro with the terminal)

dullard; funny question! Well, i may seem a bit of a noob to you, but it aint that bad.

So okay, lets assume that i may not use anything than windows, may not change ip or mac. We'll. at this point it will be a bit more difficult, because I wanted to use IM. And i wouldn't anymore, because logging in with my account on the different IM would maybe let my account been "recorded" (is there any pro word for that?) and leave a trace to me. Neither i can use a forum log in, facebook, mail, anything at all. Make sure that my Mac and IP is changed on every boot up. be ready to shut down the netbook if the admin come in my class. use a hidden drive (truecrypt) to hide my files and maybe the ubuntu OS in a hidden drive too, keep an enormous keyfile on an Ironkey or similar, depending of how much i have to hide. And i could put the OS on an USB too, so it could be removed/hidden if necessary. At extreme, no friends at all may know of this.

Yes my network rules ARE this simple, read it all over last week. :P

You'd have to ask for this one time too! maybe not of the same reason, and maybe not on a forum, but once you maybe read it or something, i dont know, and before that, you was asking too somehow.

**edit to dullard last**: I am NOT told to, not do this! i know because of theres no law say that i may not drive into houses making the roof collaps and kill people, then im allowed to do it. I know it doesn't work like this :oP

And no, no naughty here... and back to the game of your question, wouldn't it be a wrong move, after written all the methods to stay invisible, to create a poste were here, saying i would do it of the dirty reasons?:P that could be used against me u know, so even if the reason was this, i wouldn't write it:P

---

### Post by StuartN on 2009-12-08
> **Alseimik said:**
> dullard; funny question! Well, i may seem a bit of a noob to you, but it aint that bad.

You do realise that despite changing your IP address and MAC, the network administrators will still have a unique identifier for your transactions? And that this unique identifier will link every IP address and MAC that you use back to your computer, and you? And that you do not know what that identifier is or how to hide it?

Sorry to say that you are heading down a path to trouble for your self, when it would be so easy just to ask your network administrators how to obtain the services you want.

---

### Post by Alseimik on 2009-12-08
> the network administrators will still have a unique identifier for your transactions?What does that mean? isn't these the only types of identification? will you explain it?

---

### Post by doas777 on 2009-12-08
> **Alseimik said:**
> What does that mean? isn't these the only types of identification? will you explain it?
I'd like some clarification on that as well. do you mean a transaction with, perhaps, a proxy server? if so, how does the proxy know you from a whole in the ground? assuming that experimenter reboots between mac/ip changes, there would be no open connections that would cross over more than one IP. 

> "recorded" (is there any pro word for that?)
it's "Captured" or "Logged".

---

### Post by dullard on 2009-12-08
Admin: Ooh. There's a strange and unique new mac address on MY network.

Alseimik: Tra la la. Oh what fun. *giggles*

Admin: Gotcha, sonny boy. Get out!

---

### Post by Alseimik on 2009-12-09
dullard: Yeah, i thought about that, but i am expecting that with over 4000 computers using that net, and its open for everyone who enters the building, that it wouldn't be THAT visible, of course, if I'm starting to play around with pirate bay, and use their 100 mb upload connection, they may yell after me.

---

### Post by lisati on 2009-12-09
> **Alseimik said:**
> dullard: Yeah, i thought about that, but i am expecting that with over 4000 computers using that net, and its open for everyone who enters the building, that it wouldn't be THAT visible, of course, if I'm starting to play around with pirate bay, and use their 100 mb upload connection, they may yell after me.

You can almost take it to the bank that sooner or later (probably sooner) they'll notice, and pull the plug on you. It's not worth the hassle.

---

### Post by doas777 on 2009-12-09
> **lisati said:**
> You can almost take it to the bank that sooner or later (probably sooner) they'll notice, and pull the plug on you. It's not worth the hassle.

what makes you say that? I work on a network 1/10th the size of the one mentioned, and no, our admins would not have a clue that a new mac address was added (happens legitimately 10+ times a week), unless it was misbehaving. 
you have to have huge amounts of money and human resources just lying around to investigate every mac that gets added to a closed network, let alone an open one? 
the true trick to anonymity, is to look just like everyone else, so Op, no pbt. that would make you a target.

---

### Post by StuartN on 2010-01-27
> **doas777 said:**
> I'd like some clarification on that as well. do you mean a transaction with, perhaps, a proxy server? if so, how does the proxy know you from a whole in the ground? assuming that experimenter reboots between mac/ip changes, there would be no open connections that would cross over more than one IP.

You could not do much better than [this site]("http://panopticlick.eff.org/") for an explanation of statistical identifiers and the uniqueness of your own personal (single-visit) identifying data. Just click "Test Me" - the site is the Electonic Frontier Foundation.

---

