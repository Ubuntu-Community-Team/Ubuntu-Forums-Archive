---
title: "Ekiga on Breezy ... yes!!!"
date: 2006-03-18
forum: General Help
---

### Post by damu on 2006-03-18
There has been few thread about Ekiga recently, including an how to install Ekiga 2.0.1, but the result was the instalation of a snapshot, not the final realease. 

So, here is the simple way to do it :

1) **Open a terminal window**, through applications/accessories/Terminal

2)in the terminal window, 
**copy** > sudo gedit /etc/apt/sources.list 

3)**paste it**(not ctrl V, but in the edit menu, choose "paste", or right click/paste) in the terminal window.

4)**enter your password** and click enter -> A text file opens : sources.list

5) **copy** > deb [http://pkg-voip.buildserver.net/ubuntu](http://pkg-voip.buildserver.net/ubuntu) breezy main


6)Paste it at the end of the sources.file

7) Save your sources.file and close

8)Open System/Administration/Synaptic

9) It might tell you that something like "some sontents have not been validated..." -> click OK

10) Search "Ekiga"

11) Mark the box Ekiga to install

12) Click Apply

13) Once synaptic has finish the job, close, and go to Applications/Internet/Ekiga

14) Enjoy

15)Eventually suscribe an account to a provider like sipdiscount ,Ekiga, etc to make "PC to Phone" calls.
6)

---

### Post by Zhukov on 2006-03-19
Have you managed to use SIPDiscount trial? I cant get it to work and would really like to do so, since i can phone for free to Portugal :D

Thanks for the thread! :D

---

### Post by Typhoon on 2006-03-22
Nobody seems to be able to get the SipDiscount free trials to work. It seldom registers properly and never permits calls. The Ekiga mailing list has had reports of users who tried not just Ekiga but also other softphones. There is some problem at the SipDiscount end.

Typhoon

---

### Post by damu on 2006-03-23
I am using sipdiscount every day with Ekiga and it works fine ... if, I use another stun than the default sipdiscount (or Ekiga's default which is down).

I personally use   > stun.voxgratia.org

I have a registered sipdiscount account, but I have read threads on Gnomemeeting mailing list in which guys could use the free trial with no probs.
Of course, the free trial doesn't really make sens, as your free phone call will jsut last 1 minute !

Another issue with sipdiscount is the fact that when you want to open an account and buy some credits, they ask you downloqd a script that only works on Windows ( very naf init !! ] (*,) ) . Not a big deal for me. I still dual boot to Windows few times in the year...enough to buy some credit for the sipdiscount ;)

---

### Post by Typhoon on 2006-03-23
Sorry - you are right in that people with registered accounts report flawless performance. My reading of it, however, is that the free test account generally does not work. And it is not an Ekiga thing since the reports talk about different clients.

As to the value of a test account: point taken, but it would be nice to test the sound and connections before signing up. And, yes, the Windows requirement for signing up and charging up is a great PITA.

Cheers,
Typhoon

---

### Post by antenagora on 2006-03-24
For this kind of error:
W: GPG error: [http://pkg-voip.buildserver.net](http://pkg-voip.buildserver.net) breezy Release: [snipped] NO_PUBKEY 2A5E3A5A52ABFCB1


You may import the missing key, in this way:

$ gpg --recv 2A5E3A5A52ABFCB1
$ gpg --armor --export 2A5E3A5A52ABFCB1 | sudo apt-key add -

This should fix the authentication.

---

### Post by Typhoon on 2006-03-24
Has anyone tried Phil Zimmermann's new Zfone encryption with Ekiga? I am having trouble getting it to compile on Breezy.

[http://www.philzimmermann.com/EN/zfone/index.html](http://www.philzimmermann.com/EN/zfone/index.html)

Cheers,
Typhoon

---

### Post by sprinkles on 2006-03-24
Does anyone know the SIP settings for VOIP Stunt?

---

### Post by Unicast on 2006-03-25
[QUOTE=sprinkles]Does anyone know the SIP settings for VOIP Stunt?[/QUOTE]
These are my settings in X-Lite:

[IMG]http://unicast.entityonline.net/forums/voipstunt.jpg[/IMG]

---

### Post by tschaboo on 2006-04-20
[QUOTE=damu]
9) It might tell you that something like "some sontents have not been validated..." -> click OK

10) Search "Ekiga"
[/QUOTE]

There should be a "press Reload-Button" between 9 and 10, because synaptic doesn't reload automatically after changes of sources.list .

---

### Post by wvelez on 2006-04-21
Thanks a bunch for the instructions...I was really looking forward to trying out Ekiga but was reluctant to switch to Dapper.

Best regards,
-will

---

### Post by brallan on 2006-04-26
> Another issue with sipdiscount is the fact that when you want to open an account and buy some credits, they ask you downloqd a script that only works on Windows ( very naf init !! ] (*,) ) . Not a big deal for me. I still dual boot to Windows few times in the year...enough to buy some credit for the sipdiscount 
Actually, they have a web interface which lets you buy credit, so all you need is to start the account. amazing to me that they don't have a web interface for this, too.

btw - it looks like a simple exe, so wine might work, if anyone is able, see if you can get sipdiscount to post it on the site.

I wound up trying (and giving up on) ekiga, wengophone and linphone before finally getting some success with xtensoftphone. It should have been easy, but the number of options in each configuration is surprising. The vocabulary used also varies considerably from program to program. And sipdiscount washes their hands with the most vague and general advice on how to use the various sipphone clients.

---

### Post by dapperjohndoe on 2006-05-05
[QUOTE=Typhoon]Has anyone tried Phil Zimmermann's new Zfone encryption with Ekiga? I am having trouble getting it to compile on Breezy.

[http://www.philzimmermann.com/EN/zfone/index.html](http://www.philzimmermann.com/EN/zfone/index.html)

Cheers,
Typhoon[/QUOTE]
Same problem here, I would therefore be very happy about a Zfone repository.

John

---

### Post by nwillis on 2006-05-24
I replied on this issue in the other zfone thread, but for the sake of completeness, I'll mention it here, too -- zfone's license forbids you from redistributing the binary.  And the source, too, if I recall correctly.  So it can't be put into a repository.  It's not under an open source license at all; Phil Z has just posted the code for "security" review by other crypto experts.

There were some suggestions in some articles I read that he intended to open source it, but I could not find positive verification of that -- no quotes; only speculation from other parties.

What we really need is for someone to build a real open source module that implements the ZRTP protocol (which is an IETF draft).

N

---

### Post by avilella on 2007-01-07
hi, I noticed the servers don't have the breezy ekiga anymore, but only dapper, edgy and feisty.

Is there anyone that can post the debs somewhere so I can install them on a breezy machine I have?

Cheers,

    Albert.

---

