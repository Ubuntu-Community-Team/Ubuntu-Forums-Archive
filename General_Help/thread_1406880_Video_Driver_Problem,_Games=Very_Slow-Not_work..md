---
title: "Video Driver Problem, Games=Very Slow-Not work."
date: 2010-02-14
forum: General Help
---

### Post by Zolbad on 2010-02-14
[CENTER][B]Sorry I didn't know where to post this thread, so I put it in General Help
[/B]
[LEFT]
  Hello, I'm having some problems with my video drivers I think :(. 
        Before i get into detail here's some info about my _laptop_:

[LIST]
[*]It's a Laptop, yes.
[*]Graphics Card = ATI Mobility Radeon X2300
[*]Model: ASUS F3KE (the 1 without the Camera, just a mic)
[*]Ubuntu Version: 9.10
[/LIST]
  So yea, as I was saying I believe the problem is with my Video Driver. I can Set Visual effects on high without any trouble, but when running games (Even Java Games) that I can run flawlessly when running under Vista are almost impossible to run on Ubuntu, extremely low FPS and well it's just pointless to even try! 

  Examples of games are:

[LIST]
[*]Guild Wars running (Well not really *running*) with wine.
[*]Saga with wine
[*]Wurm Online (Java)
[*]Alien Arena
[*]And even Glest!
[/LIST]
  Well I tried even more, but yea...I've googled the problem about 5,000 times in the last few months and found no helpful results!
  So yea now I'm here hoping that one of you can help me...

Please Help,
  Zolbad
[/LEFT]
[/CENTER]

---

### Post by Zolbad on 2010-02-15
I'd really appreciate some support....

---

### Post by flippo on 2010-02-15
Do you get any complaints when launching 3d games from the terminal (wine complains a lot, pick a linux native like nexuiz)?

---

### Post by Zolbad on 2010-06-24
Sorry about my late response. But I just gave up on ubuntu for a while since nobody would respond.... But yea I reinstalled ubuntu and I've been having the same, and more problems. After installing a few updates and packages. I can't seem to set visual effects back up, I have a feeling that I replaced or removed my Graphics Driver without my knowledge. And would like to know how to get the old one again. Could you help with that?

  But now for the answer to your question. No I have not tried running a game with the terminal, But i will try now. Although I don't think I would get any errors... Since the games run... but barely... and very very slowly even with settings to the minimum.

---

### Post by Mark Phelps on 2010-06-24
You're NOT going to get any improvement because ATI dropped fglrx driver support for your card over a year ago.  The only driver that work now are the open source drivers, and while they provide good 2D support, they provide little or no 3D acceleration needed in games.

The only way you're going to get good 3D games response is to upgrade to a more modern HD card.

BTW, Wine uses the same drivers, so it will not offer any improvement in game performace.

---

### Post by Zolbad on 2010-06-24
Well thanks for giving me an answer. But ATI** Mobility** Radeon X2300, Is a Laptops card... So I can't really update without getting a new computer... Are you sure there isn't some open source 3D driver that I could use?

Oh and anyway I could get the driver that came with Ubuntu back? Cause now i can't use visual effects, and yesterday I could...

Or maybe get an outdated  fglrx driver From over a year ago, and see if it would work?

---

### Post by VH-BIL on 2010-06-24
Try contacting ATI and see if there is a link to an older fglrx driver that does support your card.

---

### Post by Zolbad on 2010-06-24
> **VH-BIL said:**
> Try contacting ATI and see if there is a link to an older fglrx driver that does support your card.  

Hmm.. It is a good idea and I will try it. But I can't seem to find a Live support or Even email for ATI On their website... Maybe I'm looking in the wrong places.. But do you know what it is?


EDIT: Nvm...Found one, Surprisingly hidden

---

### Post by VH-BIL on 2010-06-24
Try Here:
[http://support.amd.com/us/contacts/Pages/GraphicsTechnicalSupport.aspx](http://support.amd.com/us/contacts/Pages/GraphicsTechnicalSupport.aspx)

---

### Post by Zolbad on 2010-06-24
Yea I found an Email Support, I edited the Post above yours. Maybe you didn't see it...I'm hoping they reply.. It's taking fairly long to send a request..


Edit: Sent, Hope they reply in the next 24 hours.

---

### Post by VH-BIL on 2010-06-24
Try their forums as well.

---

### Post by clhsharky on 2010-06-24
Zolbad

The latest FGLRX drivers that support your card is CAT9.3, and only works in Ubuntu8.04.

There are fresher Open Source Drivers for your card. Here
[https://edge.launchpad.net/~xorg-edgers/+archive/ppa](https://edge.launchpad.net/~xorg-edgers/+archive/ppa)

Sharky

Add ppa read the whole page
then

> sudo apt-get update
sudo apt-get upgrade

---

### Post by Zolbad on 2010-06-24
> **clhsharky said:**
> Zolbad

The latest FGLRX drivers that support your card is CAT9.3, and only works in Ubuntu8.04.

There are fresher Open Source Drivers for your card. Here
[https://edge.launchpad.net/~xorg-edgers/+archive/ppa]("https://edge.launchpad.net/%7Exorg-edgers/+archive/ppa")

Sharky

Add ppa read the whole page
then

I'm not too experienced In the whole Linux Driver area either... Do these drivers have good 3D acceleration for my card? 

Well I did this so far (I want to make sure I'm doing things correctly...since I'm new to Linux) 
**In terminal:**
```
 **sudo add-apt-repository ****ppa:xorg-edgers/ppa**
```
Then
```
 sudo apt-get update
sudo apt-get upgrade 			 		
```

After sudo apt-get upgrade I got a warning:

```
WARNING: The following packages cannot be authenticated!
  libplist1 libusbmuxd1 usbmuxd
Install these packages without verification [y/N]? 

```

I said Yes...


Upgrade Finished... Reboot? Well I'll just reboot anyways to make sure....And send the Terminal Log to my email just incase.. I can't boot up again....Which has happened to me many times.....

---

### Post by VH-BIL on 2010-06-24
isn't there a FGLRX legacy driver that can be downloaded? I'm just asking as nVidia still has drivers for GForce1 and TNT cards.

---

### Post by Zolbad on 2010-06-24
Ok I did all that....and There doesn't seem to be a difference...Did I do something wrong?

Well I'm off for about 14 hours now...Hope someone can help..

---

### Post by Mark Phelps on 2010-06-24
> **VH-BIL said:**
> isn't there a FGLRX legacy driver that can be downloaded? I'm just asking as nVidia still has drivers for GForce1 and TNT cards.

Nvidia drivers have nothing whatsoever to do with ATI drivers.

The last fglrx drivers that will work with your card would only work with Ubuntu versions OLDER than 9.04. That's because (1) more recent drivers will NOT work with your card, and (2) the older driver versions that WILL work with your card will not work with the newer X-server versions in Ubuntu 9.04 or newer.

The ONLY drivers that will work with recent versions of Ubuntu are the open source drivers -- and those are installed by default.

---

### Post by Zolbad on 2010-06-25
hmm.. Okay then, Is there anyway that I can downgrade Ubuntu?(If not i'll just dual boot and delete the newer ubutnu later) And Once I have a lower version of it, how do I install the old Video Driver?

What version should I Get? 8.10?

Oh and are there any Other Linux OS's that have drivers that support my card and arn't too buggy??

---

### Post by Zolbad on 2010-06-25
Umm..I got 8.10 but it won't let me Connect to my wireless Internet....and it for some reason did not let me partion the drive...so I had to get rid of the new ubuntu.....
 
Sorry about my spelling, using a handheld device.
 
 
Hope someone may be able to help,
zolbad
 
 
EDIT: Ok, just reinstalled Windows Vista... Just so I can use the internet properly...Since I don't have my Ubuntu 9.10 or 10.04 Install anymore....
So yea... For some reason I have to try to connect to my wireless internet Manually on Ubuntu 8.10, And even when I type in the name and password It still will not connect....

---

### Post by Zolbad on 2010-06-25
Just got Ubuntu 8.04 And well I don't really get how I am Supposed to setup wireless internet on it.... Like I don't know why.... Can anyone help?
 
Or is there any other Linux OS's (Non ubuntu) that will work well with my Video Card?

---

### Post by Zolbad on 2010-07-02
Anyone? Please? I can't seem to get the wireless to work on Ubuntu 8.04 It doesn't even check for any and when i try to type It in manually all I can enter is the Network Name and I cannot type in any of the boxes underneath it....

Or are there any other more up to date Linux OS's that might work well with my Video Card??

---

