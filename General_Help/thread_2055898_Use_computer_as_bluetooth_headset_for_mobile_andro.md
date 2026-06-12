---
title: "Use computer as bluetooth headset for mobile android phone"
date: 2012-09-10
forum: General Help
---

### Post by disabled20191128 on 2012-09-10
Hi,
I would like to be able to use my pc (Ubuntu 12.04) as a bluetooth headset for my mobile phone(android) is it possible?

---

### Post by wayneoutthere on 2012-09-18
I absolutely need this as well.

It is a standard feature, apparently, with Windows: [http://www.mytechyard.com/2011/01/record-phone-conversation-in-pc-via-bluetooth/](http://www.mytechyard.com/2011/01/record-phone-conversation-in-pc-via-bluetooth/)

There is also this project that 'seemed' like it was going somewhere but based on my quick read it looks pretty old and not worth trying for me: [http://nohands.sourceforge.net/index.html](http://nohands.sourceforge.net/index.html)

Yet, here I am with a recent version of Ubuntu (11.04)(sorry I haven't done 12.04 yet, I"m busy) and an Android phone and I can't make the pc operate as the headset, even though I have a bluetooth dongle attached to the PC and have successfully paired the devices.  

The troubleshooting thoughts I've had so far are:

-My bluetooth dongle can't do it?
-I have to change some setting on my Android to allow the PC to control it like a phone
-Ubuntu can't do it. <--I doubt it!

Hope this helps someone and helps me. ;)

---

### Post by elliotn on 2012-09-18
I'd like that too

---

### Post by porec on 2012-10-01
Had any luck yet?
I've been looking for something like this for ages... (or it feels like it :))

I can give you a few tips dough..

[http://www.tuxgarage.com/2012/04/send-receive-sms-from-your-computer.html](http://www.tuxgarage.com/2012/04/send-receive-sms-from-your-computer.html)
Is for sending SMS.. but not quite what you are looking for.

[http://packages.ubuntu.com/search?keywords=kmobiletools](http://packages.ubuntu.com/search?keywords=kmobiletools)
Is probably what you are looking for, but is does not work with ubuntu 12.04.

[http://wammu.eu/](http://wammu.eu/)
is also somethink you could try, but it depends on what phone you have.. I use a galaxy s3, so it didn't worked for me..

[http://nohands.sourceforge.net/index.html](http://nohands.sourceforge.net/index.html)
Or, as you mentioned yourself, the nohands prosject.. But it does not work with Pangolin.. only with Lucid lynx.. So I am seriusly thinking of downgrading my computer to lucid lynx again..

If somebody else doesn't have a solution??

windows have a solution that is called 
[https://play.google.com/store/apps/details?id=justPhone.remotePhone](https://play.google.com/store/apps/details?id=justPhone.remotePhone)
But I've hated to go back to windows again..

I use ubuntu 12.04, and none of the things I've listed work in this..

Good luck bro... I'll be waching this site if anybody else come with a solution..




BTW
I've seen that you can use google voice to forward your cell phone calls to google, and answer the phone trough  google voice. But this is only if you live in the US...
I am fu**** since I live in scandinavia...:P

---

### Post by porec on 2012-10-30
You could try something called Phonedeck.
It won't alow you to call through the computer, but it's browser spesified, and you won't miss your call if you are listening to music..

It's not what you are looking for, but might give it a try?

---

### Post by Murz on 2012-11-21
I also interesting to find any soft for Ubuntu like "Remote Phone Call".

> **porec said:**
> You could try something called Phonedeck.
Can you provide link to Phonedeck app for Ubuntu? I can't find it.

---

### Post by bytie on 2013-03-23
I have managed to install hfp to 12.10 (quantal).

It also shall apply to pangolin, and other releases as well.

Firstly download libaudiofile0 package from debian packages ([http://packages.debian.org/search?keywords=libaudiofile0](http://packages.debian.org/search?keywords=libaudiofile0)), pkgs ([http://pkgs.org/download/libaudiofile0](http://pkgs.org/download/libaudiofile0)), etc regarding your architecture (such as i386, amd64, etc).

Then install it. I used gdebi for installing it. Of course you can use any other methods.

to install gdebi: 
[I]
sudo apt get install gdebi[/I] 

to install libaudiofile0, right click and select *Open With GDebi Package Installer*

Next add *ppa:sebastian-ruehl/nohands* via "Software Sources", then edit it (hit edit button) and change "Distribution" from *quantal* to *natty*. (or from *pangolin* to *natty*, if your distribution is pangolin, etc.)

And install hfconsole

*sudo apt-get install* *hfconsole*

That's all.

---

