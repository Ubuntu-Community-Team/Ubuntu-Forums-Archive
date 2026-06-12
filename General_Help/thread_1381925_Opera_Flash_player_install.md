---
title: "Opera Flash player install"
date: 2010-01-15
forum: General Help
---

### Post by squid69 on 2010-01-15
Hi there 

  I've just installed Ubuntu and everything is fine,but i prefer using opera to firefox,can someone tell me in layman's terms what to type in the terminal to install the libflashplayer.so,as i cannot seem to find the appropriate info for such a newbie like me !!!

I've already downloaded and extracted the libflashplayer.so !

 Any help would be appreciated  

  Thanks in advance 

     Dave

---

### Post by kellemes on 2010-01-15
A little info, also about installing the Flash Plugin.
[https://help.ubuntu.com/community/OperaBrowser]("https://help.ubuntu.com/community/OperaBrowser")

If you need help, just post back.

---

### Post by squid69 on 2010-01-15
> **kellemes said:**
> A little info, also about installing the Flash Plugin.
[https://help.ubuntu.com/community/OperaBrowser]("https://help.ubuntu.com/community/OperaBrowser")

If you need help, just post back.

Sorry i forgot to say i have 9.0 not 8.04 and that nearly made sense ??

---

### Post by squid69 on 2010-01-15
64 bit Ubuntu 9.10,i have downloaded flash player and it's in the Downloads folder,can anyone help me by telling me in noobieidiot terms how to install it ???

Because i will not go back to windoze even if it kills me i will get it installed 


Thanks for anything !!!

---

### Post by pricetech on 2010-01-15
Not sure where your downloads folder is, but here's what you need to do:

```
sudo cp /current_location_of_download_folder/libflashplayer.so /usr/lib/opera/plugins/
```

You'll be prompted for your password, just type it in.

You're using sudo since you can't copy it there without super user powers.

---

### Post by squid69 on 2010-01-15
Is this right ?


sudo cp /home/dave/Downloads/libflashplayer.so /usr/lib/opera/plugins/

I pasted this into the terminal and i got no error message but neither did i get any conformation ??

Sorry for being a pain !!!

---

### Post by kellemes on 2010-01-15
That's fine..
You're no pain.

And? You have Flash now?

---

### Post by mkvnmtr on 2010-01-15
I do not recall doing anything to install flash in Opera. I believe it picked up my Flash installation and just uses it. At least You Tube works fine. My other browsers just use it also.

---

### Post by squid69 on 2010-01-15
> **kellemes said:**
> That's fine..
You're no pain.

And? You have Flash now?

Well sort of ???

I no longer get the message saying i need to get the latest flash BUT i only get sound on you tube and no picture ?

I'll try a reboot !!

---

### Post by squid69 on 2010-01-15
Hmmmmmmmmmm

  Some websites work but i'm only getting sound on you tube ??

Any suggestions ? are there any "Players" that come with a codec pack aswell ??

---

### Post by squid69 on 2010-01-15
Anyone ??

---

### Post by amdalex on 2010-01-15
This works for installing flash 10 in all browsers for me. 

```
sudo apt-get install adobe-flashplugin
```

---

### Post by pricetech on 2010-01-15
> **amdalex said:**
> This works for installing flash 10 in all browsers for me. 

```
sudo apt-get install adobe-flashplugin
```

That only works for 32 bit.  OPs system is 64 bit.  The installers don't work.

---

### Post by pricetech on 2010-01-15
> **squid69 said:**
> Hmmmmmmmmmm

  Some websites work but i'm only getting sound on you tube ??

Any suggestions ? are there any "Players" that come with a codec pack aswell ??

Strange.  No there aren't any codecs to load.  Have you updated Java ??  Not sure if that's your problem, but worth a try.  I don't remember if that was in the repo or not for 64 bit.  I may have downloaded from Sun.  I honestly don't remember.

Check the repos first.  If you don't find 64 bit Java listed there, go to java.sun.com and get it directly from them.

---

### Post by pricetech on 2010-01-15
> **squid69 said:**
> Is this right ?


sudo cp /home/dave/Downloads/libflashplayer.so /usr/lib/opera/plugins/

I pasted this into the terminal and i got no error message but neither did i get any conformation ??

Sorry for being a pain !!!

No pain at all.  You won't get a confirmation, just an error if for some reason it doesn't work.

Let's put that same library in a couple of other places as well:

```
sudo cp /home/dave/Downloads/libflashplayer.so /usr/lib/mozilla/plugins
```

and

```
sudo cp /home/dave/Downloads/libflashplayer.so /home/dave/.mozilla/plugins/
```

That may or may not change the behaviour in Opera, but it should make it work in other browsers.

---

### Post by stinkeye on 2010-01-15
If flash is installed properly it shouldn't require setting up in opera.
You can make opera use the adobe folder for the plugin just to make sure your using the adobe version and not the open source one.

---

### Post by pricetech on 2010-01-15
> **stinkeye said:**
> If flash is installed properly it shouldn't require setting up in opera.
You can make opera use the adobe folder for the plugin just to make sure your using the adobe version and not the open source one.

64 bit Flash is not installed.  The library is copied to the proper locations once unzipped.

Opera's own instructions say to put the library in the /usr/lib/opera/plugins/ folder, so that's what I did and that's what I'm passing along.

---

### Post by stinkeye on 2010-01-15
> **pricetech said:**
> 64 bit Flash is not installed.  The library is copied to the proper locations once unzipped.

Opera's own instructions say to put the library in the /usr/lib/opera/plugins/ folder, so that's what I did and that's what I'm passing along.
Geez, a bit sensitive. Didn't say anything you said was wrong.
Just showing other options and what is working for me.

---

### Post by pricetech on 2010-01-15
> **stinkeye said:**
> Geez, a bit sensitive. Didn't say anything you said was wrong.
Just showing other options and what is working for me.

Didn't mean to appear sensitive.  My response was a bit terse, more so than I meant.  My apologies.

---

### Post by squid69 on 2010-01-16
Thanks for all your help guys,

I am still trying things java is being installed as i type (Hopefully)then we will see what happens !!!!

---

### Post by squid69 on 2010-01-16
Right java has installed but according to java website i only have update 15 not 17 but i got the download from there site so i can only presume the linux version is lagging behind the widoze version ???


Also when i go to manager i get this message:

 "W: GPG error: [http://ftp.debian.org](http://ftp.debian.org) etch Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 9AA38DCD55BE302B"

How do i obtain the key ?

---

### Post by squid69 on 2010-01-16
Well i reinstalled Ubuntu and (fingers crossed) all seems fine i've downloaded flash from software centre among mplayer and other codecs,you tube will be the one though................


will get back to you when i test it proper like ???

---

### Post by squid69 on 2010-01-16
Well i think that can be called a success all is well and i did not use the terminal once,this is a wonderful OS 


Thanks guy's for being so patient with me

---

### Post by pricetech on 2010-01-18
Glad you got it fixed.  I beginning to think the process is different in Karmic from previous versions.  Long story as to why.

Welcome to Ubuntu and much success to you.

---

