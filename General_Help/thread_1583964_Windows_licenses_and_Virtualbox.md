---
title: "Windows licenses and Virtualbox"
date: 2010-09-28
forum: General Help
---

### Post by ufugu on 2010-09-28
Hi all,

Sorry if this is an obvious question, but I either don't understand something that is obvious to everyone else about Windows or else I just can't find the answer I'm looking for...

Background: I'm a 20+ year Mac user, switched four years ago to Linux.  I have NO experience with Windows to speak of.  Whenever I've gotten a new box, it's either been home-built or a Mac.

Now I have a new Acer Aspire AS7551 laptop, and although I have not yet booted into Windows, it comes with a Windows 7 Home Premium license. I've been running it with Ubuntu 10.04 off a flash drive and everything works perfectly. 

What I want to do: I want to wipe the disk, install Lucid, and run Windows in Virtualbox (for the sole purpose of watching some Netflix and learning a little bit about Windows 7). 

For the purpose of this question, please accept that I DO NOT want to dual boot.  

The problem: From what I can find, I can't use the "recovery discs" that came with my laptop to create a virtual machine. This is confusing, because it seems like I paid for a legitimate Windows license for use with this laptop.  

Questions:

1. Would MS exchange my recovery discs for a regular install disc to go with my license code if I explained this to them?  Have any of you tried this (the "reasonable approach")?

2. If not, is there a source for Windows ISOs that I can safely use with my license? (I am aware that the legitimacy of that approach is questionable, but I am quite comfortable with the ethics since I paid for Windows 7, own the license, and only want to use it on the same computer.  If you disapprove, I agree to disagree with you and maybe you can help with the next question).

3. If not, is there any way in heck I can use my recovery disc to create something Virtualbox can work with?

4. If not, how are all of you people getting your Windows virtual machines going??

Thanks.

(I have read that Acer is a major hassle to get a refund from for the "Windows tax" so I might as well be able to use it--this is MS' chance to win over a fan if only they will let me!)

---

### Post by rbc on 2010-09-28
I haven't tried either of these, so I cannot vouch for them, but here's two that Google turned up:
[http://serverfault.com/questions/33603/creating-a-virtual-machine-in-virtualbox-from-a-physical-one](http://serverfault.com/questions/33603/creating-a-virtual-machine-in-virtualbox-from-a-physical-one)
[http://www.virtualbox.org/wiki/Migrate_Windows](http://www.virtualbox.org/wiki/Migrate_Windows)

---

### Post by colin.p on 2010-09-28
I have downloaded this and burnt to DVD, but have not tried it yet:
[http://forum.notebookreview.com/windows-os-software/428068-legal-windows-7-download-links-just-like-vista-before.html](http://forum.notebookreview.com/windows-os-software/428068-legal-windows-7-download-links-just-like-vista-before.html)

---

### Post by wilee-nilee on 2010-09-28
Call the manufacturer get a straight install ISO or DVD, that will activate with your oem key and install in Vbox.

You don't want the oem disc or recovery it is set up for extras you don't need and drivers that will be unavailable in Vbox.

---

### Post by ufugu on 2010-09-29
rcb, i'd seen that approach here on the forums about creating from an existing install.  it's an option but it looks like a nightmare.

colin.p, just what i'm looking for.  if it works, i'll mark as solved.

wilee, a reasonable next step.

thank you.

---

### Post by Mark Phelps on 2010-09-29
> **ufugu said:**
> ...The problem: From what I can find, I can't use the "recovery discs" that came with my laptop to create a virtual machine. This is confusing, because it seems like I paid for a legitimate Windows license for use with this laptop.  


You GOT a "legitimate Windows license" -- an OEM license.

ALL they are required to so is provide you the MEANS of restoring the PC to its original condition -- which they do through a combination of Restore CDs (which are usually little more than WinRE boot CDs) and an OEM Win7 image stored on the hard drive.

They are NOT required to provide you an installation DVD.

Sure, it won't hurt to ask them for an installation DVD, but don't be surprised if they (1) say no, or (2) want to charge you full price for one.

---

### Post by spillage2 on 2010-09-29
I would just download an iso of that version of windows. At the end of the day I see this a legal act as you dont pay for the os but the os licence key which you own and have paid for.

I did this with xp as I only had my xp key and no disc to run on vbox.

---

### Post by ufugu on 2010-09-29
Well, the Windows 7 ISO method was pretty good.  I was able to remove the cfg file from the ISO, and super easy to install in Virtualbox and worked great once I installed the sound driver and GuestAdditions and Silverlight. Netflix (which was the one thing I really wanted it for) worked very well full screen.

But my activation key wouldn't work--apparently a key for the OEM version of Home Premium and the retail version of the same exact thing are not interchangeable.

After spending a good ten hours on trying to figure all this out  I've come to the conclusion (at least for now!): 

If they are so paranoid that they won't even let me use something I paid for, scr3w 'em.  So I won't get one thing I wanted, big deal, I didn't really miss it when I was 100% Ubuntu so that's what I'll stick with.

I've never had feelings for MS either pro or con. But no wonder they have so many "pirates" if they penalize even honest users with such drastic paranoia. That goes for you too Netflix! Buh bye!

---

### Post by snowpine on 2010-09-29
A virtual machine "counts" as a different computer so far as Microsoft is concerned. The OEM license applies only to the original hardware, not to "virtual" hardware. You need to purchase an additional license for each virtual machine to be in strict compliance with the Microsoft EULA.

---

### Post by madverb on 2010-09-29
snowpine is correct. That license is only for use on that particular notebook. You may not use it in a virtual machine.
Don't you just adore Microsoft licensing?

---

### Post by snowpine on 2010-09-29
> **madverb said:**
> snowpine is correct. That license is only for use on that particular notebook. You may not use it in a virtual machine.
Don't you just adore Microsoft licensing?

Their licensing strategy is correct from the point of view of maximizing sales and profits.

---

### Post by ufugu on 2010-09-30
Thanks for all the information. I guess in all my years using other OSes I gave them the benefit of the doubt that it could be as crazy as people said--I never had any idea their licensing was restrictive to that degree.  

It's really not a big deal though, they've got a billion other customers--they don't need me and I'm fine without them. It just seems so...  silly. 

Not an analogy per se, but for some reason it makes me think of the scene in the movie A Hard Day's Night where the Beatles are running around on an unused field having a lark, and a grumpy old man goes over and says they are not allowed and must get off immediately. One of the lads says "Sorry if we hurt your field, mister."

It's certainly anyone's prerogative to be a grumpy old man and/or to protect their field, but it's also kind of sad and foolish to kick people off it when it's just sitting there not even being used.

---

### Post by JedMeister on 2010-09-30
Whilst what others have said about Windows OEM licensing is true AFAIK, it actually comes down to your country's consumer law. MS can put whatever they like into a EULA but if it doesn't comply with local consumer law then its not technically legal and therefore unenforceable.

I have encountered a somewhat similar situation to yours. I live in Australia and know of an IT guy who had Server 2k3 OEM installed and then migrated the OS to a Linux based hypervisor with the Win OS as a VM (on the same hardware). Obviously it wouldn't activate so he rang MS to active it and they refused. I don't recall the intricacies but basically MS' OEM license doesn't comply with Australian consumer law and so is not enforceable by them. It took them a bit of convincing but they came through eventually. One fundamental difference though, this was a DIY PC, with a retail OEM copy of Win. A retail notebook is purchased as a single unit (with OEM OS preinstalled) so those sort of laws may not apply the same way under that circumstance?

Check out your local laws and/or try speaking with consumer affairs type people.

---

### Post by epsolon77 on 2010-09-30
Small correction.  The facts given are for the EULA from Vista PREVIOUS.  Personally I think all this is crap, but what can you do.

An OEM install, which shipped with your machine, is tied to that hardware.  However, Windows 7 ships with 2 liscences, a regular and a virtual.  They both are tied to the hardware though, so you could never use either liscence on any other machine, however Microsoft does not care if you are installing virtually or not.  So installing Ubuntu and running your copy of Win 7 on the hardware it was originally installed on is legal.  The question is how to do it.

OEM install disks are different from any other install disk and use different keys, so there is no way you are going to be able to use another CD to run. However the easiest thing to do is likely to convert your current hard drive to an ISO image and load that in VBOX.  One big note, Windows installs are keyed to the IDE controller they were installed on.  There is a registry change that needs to be made to before the ISO is created that will allow the windows iso to boot.

I don't have a ton of time to give you links, but let me know if your interseted in going this route and I will try to give you links ASAP.

sorry for spelling, really rushed

---

### Post by snowpine on 2010-09-30
Alternately, an OEM retail version of Windows is relatively inexpensive (around $100) and will allow you to fully comply with the Microsoft EULA (if you fear prosecution under the laws of your home country).

An analogy that may help you understand Microsoft's thinking on this issue: When you purchase a home (your computer), it comes with a gas stove in the kitchen (the OEM Windows license) that allows you to cook meals. If you want to cook meals out on your deck (the virtual machine), you need to purchase a grill (an additional Windows license). You could theoretically disconnect the gas range in your kitchen and drag it out to the deck (never activate the Windows license on your HDD but rather try to use it in the VM), but this may not be permitted under the zoning laws or building codes of your home town.

Please understand I am not endorsing or defending Microsoft, merely helping to clear up a confusing issue. It is important to realize that Microsoft does not actually make money by selling the Windows operating system, but rather by selling licenses to install/use that operating system on a particular machine (physical or virtual). Seen in this light, their EULA is a logical business decision to maximize sales and profit.

It is also important to understand that Ubuntu uses a completely different business model, and you are free to install Ubuntu on as many virtual machines as you like, at no charge. :)

---

### Post by JedMeister on 2010-09-30
Sorry this post is a little frivolous but I couldn't help myself.> **snowpine said:**
> An analogy that may help you understand Microsoft's thinking on this issue: When you purchase a home (your computer), it comes with a gas stove in the kitchen (the OEM Windows license) that allows you to cook meals. If you want to cook meals out on your deck (the virtual machine), you need to purchase a grill (an additional Windows license). You could theoretically disconnect the gas range in your kitchen and drag it out to the deck (never activate the Windows license on your HDD but rather try to use it in the VM), but this may not be permitted under the zoning laws or building codes of your home town.Very nice analogy! I like it lots and I think it fits quite well.

> **snowpine said:**
> Please understand I am not endorsing or defending Microsoft, merely helping to clear up a confusing issue. It is important to realize that Microsoft does not actually make money by selling the Windows operating system, but rather by selling licenses to install/use that operating system on a particular machine (physical or virtual). Seen in this light, their EULA is a logical business decision to maximize sales and profit.Boo for MS!

> **snowpine said:**
> It is also important to understand that Ubuntu uses a completely different business model, and you are free to install Ubuntu on as many virtual machines as you like, at no charge. :)Yay for Ubuntu! :)

---

