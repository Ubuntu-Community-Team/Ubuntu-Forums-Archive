---
title: "Cinelerra"
date: 2011-08-27
forum: General Help
---

### Post by mksundaram on 2011-08-27
Hello,
I,am new to linux and have no knowledge of programming. Recently after dumping windows XP i installed ubuntu 11.04. My profession is independent film maker. I produce low budget short films and documentaries etc. So I was looking for video editing and compositing software like After effects and Adobe premier pro.  While searching for it i found cinelerra, but I am not able to install it. Please help me getting this done. Or how to install premier pro in ubuntu 11.04.

Please note that i don't have any programming knowledge.

Thanks

---

### Post by saltmarshlamb on 2011-08-27
[https://launchpad.net/~cinelerra-ppa/+archive/ppa](https://launchpad.net/~cinelerra-ppa/+archive/ppa)

Why would you think you need programming knowledge? Using a terminal to do 'stuff' to your system is not programming :)

Once you've added the ppa and updated your sources it will be available to install from whatever GUI you use to install apps with.

---

### Post by Enigmapond on 2011-08-27
Open the terminal and do:

```
sudo add-apt-repository ppa:cinelerra-ppa/ppa
```

Then:

```
sudo apt-get update && sudo apt-get install cinelerra
```

Great programme BTW..:)

---

### Post by mksundaram on 2011-08-27
> **saltmarshlamb said:**
> [https://launchpad.net/~cinelerra-ppa/+archive/ppa]("https://launchpad.net/%7Ecinelerra-ppa/+archive/ppa")

Why would you think you need programming knowledge? Using a terminal to do 'stuff' to your system is not programming :)

Once you've added the ppa and updated your sources it will be available to install from whatever GUI you use to install apps with.

Thanks :-) giving me confidence of handling Linux without programming knowledge.

I did the first step that is adding ppa to repositary and then updated through up-date manager. But still I am not able to find the installer. If you can guide me it will be helpful.

Please note till yesterday I had Windows , which was very much easy to install other softwares etc ...

Keeping this in mind guide accordingly, I don't want to switch back to Windows.

Thanks :-)

---

### Post by saltmarshlamb on 2011-08-27
If you've done the first step - adding the repos and have updated then you can just do the last bit of the second step which is part of what enigmapond posted

The apt-get install part will install it

```
sudo apt-get install cinelerra
```

Does it not appear in either the software centre or synaptic? If it's not there then you'll not be able to install it. 

You'll get used to it - bear in mind that you didn't learn windows in one day either :)

This thread has a lot of information in it - too much to read in one go - but worth a look as you wander along. 

[http://ubuntuforums.org/showthread.php?t=801404](http://ubuntuforums.org/showthread.php?t=801404)

Instead of thinking that you need to learn everything in one go - you don't - just learn what you need as you need it :)

Another source of information is the wiki

[https://help.ubuntu.com/community](https://help.ubuntu.com/community)

Edit - one I forgot - [https://help.ubuntu.com/11.04/ubuntu-help/index.html](https://help.ubuntu.com/11.04/ubuntu-help/index.html)

For what it's worth I've been using only linux for 4 years or so and as far as programming is concerned I have no idea how to do that voodoo. But I've not got myself in too many tight corners not being a programmer :)

---

### Post by Mark Phelps on 2011-08-27
Adobe Premier (at least, any recent versions) is NOT going to work in Ubuntu.

The WineHQ page below lists the results of trying to use Adobe Premier -- and as you can see, everything since 2007 is rated Garbage: 

[http://appdb.winehq.org/objectManager.php?sClass=application&iId=128]("http://appdb.winehq.org/objectManager.php?sClass=application&iId=128")

---

### Post by mksundaram on 2011-09-02
Thanks :-)
Cineleraa installed in my Ubuntu 11.04. Now please tell me  how do I import mod files in it ?

---

