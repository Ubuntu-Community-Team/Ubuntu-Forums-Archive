---
title: "Kubuntu 8.10 from HDD to DVD"
date: 2009-07-10
forum: General Help
---

### Post by ShadeS_07 on 2009-07-10
Hi and greetz to all the members of this forum... I would like to ask help from you peepz for something I want to be done.... :cool: :)

As the title says.... I would like to have my Kubuntu 8.10 distro which is installed right now into my HDD be compressed and transferred into a DVD.. If that's possible...

I am using a 32-bit Kubuntu 8.10 Intrepid Ibex... (Thanks for Canonical again for sending me the distro for free... :popcorn: ) 
Just when I got it in my mail box, I opened the package, turned my PC on, popped the CD in my CD drive, and have it installed right a way into my HDD. After the installation, I made some configurations, then made it suit my satisfactions, my needs, etc... 

After all those configurations and set ups... I checked my disk space, and found out that I occupied no more than the maximum size that a DVD's storage capacity would have... So I began thinking if it would be possible to compress all my configs, settings, etc., and then put it into a DVD, so that later on, if I want to reinstall my pre-configured Kubuntu 8.10 distro, I would not have to go all over those configurations again....

Well... if, that would be possible, I hope so...
I think there's a way for that, I do believe, especially when "**Ubuntu Ultimate Edition**" comes in my mind... If I am not mistaken, it's a modded Ubuntu distro... So, I do really think that I can also make my own modded distro,, only that in my case, I am using Kubuntu 8.10 Intrepid Ibex.... :)

If there's a way, please tell me how.... Thanks in advance... More power to this community.... God bless.... :) :KS


~ShadeS_07 :popcorn: :guitar:

---

### Post by ShadeS_07 on 2009-07-10
Hi and greetz to all the members of this forum... I would like to ask help from you peepz for something I want to be done.... :cool: :)

As the title says.... I would like to have my Kubuntu 8.10 distro which is installed right now into my HDD be compressed and transferred into a DVD.. If that's possible...

I am using a 32-bit Kubuntu 8.10 Intrepid Ibex... (Thanks for Canonical again for sending me the distro for free... :popcorn: ) 
Just when I got it in my mail box, I opened the package, turned my PC on, popped the CD in my CD drive, and have it installed right a way into my HDD. After the installation, I made some configurations, then made it suit my satisfactions, my needs, etc... 

After all those configurations and set ups... I checked my disk space, and found out that I occupied no more than the maximum size that a DVD's storage capacity would have... So I began thinking if it would be possible to compress all my configs, settings, etc., and then put it into a DVD, so that later on, if I want to reinstall my pre-configured Kubuntu 8.10 distro, I would not have to go all over those configurations again....

Well... if, that would be possible, I hope so...
I think there's a way for that, I do believe, especially when "**Ubuntu Ultimate Edition**" comes in my mind... If I am not mistaken, it's a modded Ubuntu distro... So, I do really think that I can also make my own modded distro,, only that in my case, I am using Kubuntu 8.10 Intrepid Ibex.... :)

If there's a way, please tell me how.... Thanks in advance... More power to this community.... God bless.... :) :KS


~ShadeS_07 :popcorn: :guitar:

---

### Post by lisati on 2009-07-11
You might want to check out "Remastersys": [http://howtoforge.com/ubuntu-linux-mint-livecd-with-remastersys](http://howtoforge.com/ubuntu-linux-mint-livecd-with-remastersys)

---

### Post by ShadeS_07 on 2009-07-11
Wow,, Thank you very much dude! Hehe, that's the one I've been looking for! 

Hmmmmmm, is this the proper way for me to make myself a modded/custom Kubuntu 8.10 distro with Remastersys for the first time?

1. Once Kubuntu successfully starts up, I should go to my Konsole, and enter:

```
sudo vi /etc/apt/sources.list
```

..then append:

```
# Remastersys
deb http://www.remastersys.klikit-linux.com/repository remastersys/
```

...then save and exit the file

2. I should update the source list with:

```
sudo apt-get update
```

3. Then install Remastersys...

```
sudo apt-get install remastersys
```

4. After Remastersys was successfully installed, I would start using it then...

I'd start with:

```
sudo remastersys dist
```

to make myself a modded/custom Kubuntu 8.10 distro which I can distribute to others, such as friends and relatives, either as a LiveCD or an installable distro...

According to what I've read on how I can use Remastersys, The "dist" option will create an ISO image called customdist.iso in the /home/remastersys directory. The dist option makes that my personal folder (e.g. /home/shades) will not be included in the ISO image.

So with the "dist" option, only my personal folder would be omitted from being part of the ISO image that Remastersys creates...

What if I want it included? And how does **sudo remastersys backup** differ from **sudo remastersys dist**?

5. Then, I would clean temporary files Remastersys used with:

```
sudo remastersys clean
```

6. Then burn it into a CD/DVD as a LiveCD/DVD or as an installable distro... K3b's the tool I should use, right?

Hmmmmmmm, Can I have the CD/DVD's name (you know, the name of CD/DVD that you would see when you insert the CD/DVD into the drive...) renamed according to my preference? ..something like "Kubuntu-8-10-Cust" or like "shades-dist-kubuntu-8-10"? lol, I don't want to have my new dist simply named as "customdist"... xD :lolflag:




Well... Thanks again for your help... I really appreciate it... More power to this community... God bless... :popcorn:  :)

~ShadeS_07,, :popcorn: :guitar: :lolflag:

---

### Post by ShadeS_07 on 2009-07-12
*bump* :popcorn:

---

### Post by TeamJ on 2009-07-12
I am obviously not as wise as all these guys but it depends on the details. to move it to DVD I would suggest getting a disk imager or partition cloner, make an ISO of your HDD then burn it to your DVD.

---

