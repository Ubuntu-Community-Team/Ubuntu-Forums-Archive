---
title: "Unable to burn mp3s into audio CD"
date: 2011-01-21
forum: General Help
---

### Post by BunnyDee on 2011-01-21
Hello.

I am running Ubuntu 10.10 (Maverick Meerkat), and am trying to burn a collection of mp3s into an audio CD. 

I have tried both Brasero and k3b, and none of these do this for me. They require that I first transform these files from .mp3 myself.

Looking this up online, I 'told' the Terminal to ```
sudo apt-get build-dep k3b
``` and then ```
sudo apt-get install libk3b2-extracodecs
``` but it tells me that it is ```
Unable to locate package libk3b2-extracodecs
``` and still doesn't 'know' how to do this for me.

Is there some way for me to make this audio CD from the .mp3 files I want to burn, without converting the format myself first?

---

### Post by Sylos on 2011-01-21
Hello.
What you want is to install some of the extra packages from the medibuntu repository.

Follow the guideance here to add the medibuntu repo

[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

Then reload synaptic - Then add the w32codecs package (I think this is the one you need).

If that doesnt do it then post back.

---

### Post by nomko on 2011-01-21
> **BunnyDee said:**
> Hello.
 
I am running Ubuntu 10.10 (Maverick Meerkat), and am trying to burn a collection of mp3s into an audio CD. 
 
I have tried both Brasero and k3b, and none of these do this for me. They require that I first transform these files from .mp3 myself.
 
Looking this up online, I 'told' the Terminal to ```
sudo apt-get build-dep k3b
``` and then ```
sudo apt-get install libk3b2-extracodecs
``` but it tells me that it is ```
Unable to locate package libk3b2-extracodecs
``` and still doesn't 'know' how to do this for me.
 
Is there some way for me to make this audio CD from the .mp3 files I want to burn, without converting the format myself first?
 
I think you have to search for **libk3b6** in synaptic and install that codec file

---

### Post by ghostborg on 2011-01-21
There is a script by Robbie Ferguson called perfectbuntu that helps you install common things to make your system run like it should.

The website is Category5.tv [http://www.category5.tv/]("http://www.category5.tv/")

The link for perfecbuntu is down on the left under awesome links.

The direct link is [http://perfectbuntu.category5.tv/]("http://perfectbuntu.category5.tv/")

It's a good show to learn and interact.

---

### Post by BunnyDee on 2011-01-21
Thanks for the answers!

I added both libk3b6, and the w32codecs package which is supposed to be under 'Non-free codecs' according to Synaptic. Thanks to both of you, not sure which one of the two actually did it.

I guess it's OK now (doesn't see the empty CD, for some reason, so I haven't really done it yet to be 100% sure), but will also check out the perfectbuntu script, read up on it to see what it's all about - thanks for the tip.

---

