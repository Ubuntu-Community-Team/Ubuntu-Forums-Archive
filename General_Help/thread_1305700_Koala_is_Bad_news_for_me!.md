---
title: "Koala is Bad news for me!"
date: 2009-10-30
forum: General Help
---

### Post by Plumtreed on 2009-10-30
Did an upgrade but ended up with KK that doesn't have audio, lost my touch-pad and things are getting slower. Just a big 'Fail'!

With 9.04 there were no probs so i thought the upgrade would be a piece of cake, nope.

Does anybody have any suggestions or do I have 3 bugs?

---

### Post by muhannadfa on 2009-10-30
ubuntu is somehow wierd OS
i don't know i was happy with 8.10 & upgraded to 9.04 and many problems came to surface >>> 
I ended up using Win 7 >>> which is amazing OS from Microsoft till now

---

### Post by keplerspeed on 2009-10-30
I am back to using 9.04 due to big wireless issues. If that is all that works, then that will have to do! In that case you will have to install 9.04 from scratch..

If need be, stick with 8.04-9.04 versions until karmic stuff is resolved.

---

### Post by blazemore on 2009-10-30
If you need perfect stability I'd always recommend waiting a couple of weeks until all the updates have come out.

---

### Post by P4man on 2009-10-30
Try the livecd before doing the upgrade. I guess thats too late now, but I would still try booting the livecd. If you dont have those issues in a live session then its a problem with the upgrade. If the problems persist in the livecd, head to launchpad

---

### Post by Plumtreed on 2009-10-30
I thought Ubuntu was at the top and that the upgrade would work correctly, so, against my better judgment and for the first time, I tried the upgrade.

Live and learn!

Looks like it will be pretty good when the final release is out.

I tried to select an earlier kernel in grub but that throws up an error.

---

### Post by hikaricore on 2009-10-30
**If you want stability stay with an LTS release.**

Karmic is not this.

---

### Post by P4man on 2009-10-30
> **Plumtreed said:**
> I thought Ubuntu was at the top and that the upgrade would work correctly, so, against my better judgment and for the first time, I tried the upgrade.

Live and learn!

Frankly, with barely a week between the RC and the release, I cant see how one could expect a bug free release. Some of the bugs I posted for 9.10 beta havent even been properly looked at yet, let alone fixed. Still it seems to work for most people.

I like ubuntu, but trying to adhere to its 6 month update scheme no matter what means you better try before you "buy", especially for non LTS releases.

Anyway that doesnt mean your issues as per se unfixable, but it would help if you could boot a live cd and verify the problems there.

---

### Post by Primefalcon on 2009-10-30
> **tacky said:**
> Well now i cannot help you but when i get the solution i will definitely post it.
I would stay say just stay wth LTS versions, but just wait 2 weeks or even a month after a a version is released before upgrading, and you'll have a a pretty solid system

---

### Post by Plumtreed on 2009-10-30
All very good advice but if a OS is deemed 'final' it should be ready for use!

In any event, it needs to be 'used' in order to determine if it is right. 

To take this aspect a bit further it looks very much like a fault with Grub because I have found that 9.10 doesn't show in Grub. Perhaps I am running on the old kernel and need to repair or get Grub re-installed any suggestions?

---

### Post by leandromartinez98 on 2009-10-30
If you can, do a clean 9.10 install. I have upgraded with
relative success on two machines, and my clean installs were
much better.

---

### Post by Barafu Albino Cheetah on 2009-10-30
Well, Karmic is a first Kubuntu with PulseAudio support where sound works out of the box for me. The only thing I needed to do is to install padevchooser, configure sound server, add my user to pulse-access group, configure phonon, and configure sound cards. Perfect user-friendlyness!

---

### Post by randwyck on 2009-10-30
I guess the best option is to use new release in virtual mode for some time (VirtualBox etc). This way you can have the best of two worlds.

---

### Post by P4man on 2009-10-30
> **Plumtreed said:**
> All very good advice but if a OS is deemed 'final' it should be ready for use!

If its ready for 99.9% of the users, should it be released or not?
No OS ever released worked on every hardware and for every user, and linux never will. At least you can test it easily and you dont need to apply for a refund if it doesnt work for you :)
 
> 
To take this aspect a bit further it looks very much like a fault with Grub because I have found that 9.10 doesn't show in Grub. Perhaps I am running on the old kernel and need to repair or get Grub re-installed any suggestions?

Are you using grub legacy or grub 2 ?

---

### Post by Plumtreed on 2009-10-30
> **P4man said:**
> If its ready for 99.9% of the users, should it be released or not?
No OS ever released worked on every hardware and for every user, and linux never will. At least you can test it easily and you dont need to apply for a refund if it doesnt work for you :)
 


Are you using grub legacy or grub 2 ?

 I suspect that I am using grub 2. I ran 'sudo update-grub2' and it did, including the 9.10 kernel but it failed to show when I re-booted, which takes me into my old grub menu which has 9.04. I think that I need to sort out Grub but don't know how....Nothing on 'menu.lst'

---

### Post by P4man on 2009-10-30
> **Plumtreed said:**
> I suspect that I am using grub 2. I ran 'sudo update-grub2' and it did, including the 9.10 kernel but it failed to show when I re-booted, which takes me into my old grub menu which has 9.04. I think that I need to sort out Grub but don't know how....Nothing on 'menu.lst'

Are you sure you are installing grub on the same drive that you are booting from? Try disconnecting all drives except that one that contains karmic, reinstall grub and see if that works.

---

### Post by Plumtreed on 2009-10-30
My system monitor tells me that my release is 9.10 Karmic and the Kernel is 2.6.28-15 This must be at least part of the problem.

This is a laptop with only one drive.

Erm, how does one reinstall grub

---

### Post by P4man on 2009-10-30
> **Plumtreed said:**
> My system monitor tells me that my release is 9.10 Karmic and the Kernel is 2.6.28-15 This must be at least part of the problem.

This is a laptop with only one drive.

Erm, how does one reinstall grub

Yep definately that aint right. Here is all the info you could ever want on grub2:
[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

Scroll down to the reinstall from livecd part.

---

### Post by rockstarrem on 2009-10-30
> **Barafu Albino Cheetah said:**
> Well, Karmic is a first Kubuntu with PulseAudio support where sound works out of the box for me. The only thing I needed to do is to install padevchooser, configure sound server, add my user to pulse-access group, configure phonon, and configure sound cards. Perfect user-friendlyness!

Haha. I laughed at that :P. I had a lot of trouble with PulseAudio as well.

---

### Post by Plumtreed on 2009-10-30
Thanks P4Man, after doing 'grub-install -v' it shows that I am running the old version of Grub, ie (GNU GRUB 0.97)

None of this is my choice but it was what evolved after upgrading to Karmic. 

The thread you directed me to gives some info on Grub 2 but it appears that it is possible to use either Grub or Grub2. My old version of Grub should work if I could get the 9.10 kernel to appear. It now appears on the 'menu.lst',perhaps because I did 'update-grub' but it fails to show at boot-up. 

Is there a way to get the Grub to boot up with the 9.10 kernel as a choice?

I remembered an old 'Super-Grub Disk' in that drawer and when I tried it, I booted very happily and briskly to Grub and 9.10.....everything works the way should and it is brilliant!

Now I have to fix Grub to work the way it should!

---

### Post by Roasted on 2009-10-30
> **Plumtreed said:**
> All very good advice but if a OS is deemed 'final' it should be ready for use!


That would be true in a perfect world. But unfortunately, we don't live in a perfect world.

> 
In any event, it needs to be 'used' in order to determine if it is right. 


Absolutely. There's so many different hardware combinations out there, and there's only a certain amount Ubuntu developers can test with.

Even though I'm guilty of installing new versions of Ubuntu the day they come out, I still know I'm taking a risk. It's like this with any operating system.

I think it's important to know that things could be much much worse, and we should be happy that we don't have to wait a year for it to be semi-stable, like some of our unfortunate system32 colleagues. :P 

In a few short weeks, I'm sure all of us will be rockin out with a stable Karmic release.

---

### Post by P4man on 2009-10-30
> **Plumtreed said:**
> Thanks P4Man, after doing 'grub-install -v' it shows that I am running the old version of Grub, ie (GNU GRUB 0.97)

None of this is my choice but it was what evolved after upgrading to Karmic. 

The thread you directed me to gives some info on Grub 2 but it appears that it is possible to use either Grub or Grub2. My old version of Grub should work if I could get the 9.10 kernel to appear. It now appears on the 'menu.lst',perhaps because I did 'update-grub' but it fails to show at boot-up. 

Is there a way to get the Grub to boot up with the 9.10 kernel as a choice?

I remembered an old 'Super-Grub Disk' in that drawer and when I tried it, I booted very happily and briskly to Grub and 9.10.....everything works the way should and it is brilliant!

Now I have to fix Grub to work the way it should!

This is all very odd. Do you have more than one grub installed perhaps? You can only have one grub stage 1 bootloader per disk (it sits on the MBR) but  perhaps you made a boot partition and now you also have a /boot and /boot/grub folder in your root partition? Or more than one root partition?

Anyway Im not a grub expert at all, I hope someone can give you better advice than me. My specialty is having hunches :D

---

### Post by Plumtreed on 2009-10-30
Thanks Roasted, we seem to be sorting out my problem which appears to centre around Grub/Grub2.

Booting via 'Super-Grub' has established a Grub menu containing 9.10 as the dominant menu. So now I boot into Karmic and everything appears perfect.

My only problems now are: 

-I don't use Windows so the other OS on my puter was a Ubuntu based and the upgrade didn't take that into consideration. 

-I am not running on Grub2

---

### Post by Plumtreed on 2009-10-30
Thanks for your hunches Pac4man, your handholding seems to be getting me through:p

I was very anxious to make the 'upgrade' work and except for the Grub problem it has. The Grub problem may be something very specific to my laptop.

I'll check out your theory and get back later.

---

### Post by Slim Odds on 2009-10-30
> **Plumtreed said:**
> All very good advice but if a OS is deemed 'final' it should be ready for use!

Please name ONE OS that was 100% FLAWLESS as a FINAL release.

...........  I'm waiting  ...........

---

### Post by jdunn on 2009-10-30
True on posts #4 and #5.  I downloaded Koala and burned a CD today but I don't plan on installing it for a couple weeks.  I tried out the live CD though...works fine on my system.  Also, I don't do upgrades.  A clean install may be more work, but its worth it.

---

### Post by Plumtreed on 2009-10-30
> **Slim Odds said:**
> Please name ONE OS that was 100% FLAWLESS as a FINAL release.

...........  I'm waiting  ...........


Is this a bit like Road Rage?:(

---

### Post by Plumtreed on 2009-10-30
> **jdunn said:**
> True on posts #4 and #5.  I downloaded Koala and burned a CD today but I don't plan on installing it for a couple weeks.  I tried out the live CD though...works fine on my system.  Also, I don't do upgrades.  A clean install may be more work, but its worth it.

I did an upgrade and, except for Grub, it is 'brilliant! Upgrading to a new release is the ultimate for an operating system and unless people have a go it may never be achieved. 

I have a 'stable' desk-top computer running LTS so I can afford to play on my Laptop.

If you can chance it, try upgrading to help establish the practise and contribute in a small way to the development  of the OS. It may also contribute to your own learning experience;)

---

### Post by beacon on 2009-11-08
I like Ubuntu and use it exclusively. While I agree with the arguments put forward that one can't expect perfection from the outset, I would suggest following the advice of others; i.e., unless you are much more advanced than I, stick with 9.04 for the moment. I upgraded and had to spend hours on the forums and seeking outside help for a number of difficulties without much luck. So I got rid of Koala and reinstalled 9.04.

---

### Post by P4man on 2009-11-08
> **beacon said:**
> I like Ubuntu and use it exclusively. While I agree with the arguments put forward that one can't expect perfection from the outset, I would suggest following the advice of others; i.e., unless you are much more advanced than I, stick with 9.04 for the moment. I upgraded and had to spend hours on the forums and seeking outside help for a number of difficulties without much luck. So I got rid of Koala and reinstalled 9.04.

I dont think thats sound general advice. I think the better advice is to try 9.10 from a livecd, and see if it all works with your hardware before installing or upgrading. As with every new release where some things are changed fundamentally (like a new xorg with new intel drivers in this case) it will solve problems for many users and introduce new issues to others. Im still convinced 9.10 is a step forward for far more users then a step backward, although its clear this doesnt apply to everyone.

In short: try before you "buy" :)

---

### Post by stu500 on 2009-11-08
Its been bad news for me as well - some of the problems i have encountered.
  
wireless driver problems: wireless worked from liveUSB but for some reason the driver wasn't included with the HDD install  

slow internet: Something to do with ipv6 i gather (dont have a clue what ipv6 is)  

flash problems: some streaming sites not working for me.

hibernate/suspend problems: simply doesn't work.

Software centre not working correctly. 

To top it off ubuntu 9.10 wont boot any more.

This is my first serious go at linux and to be honest its left a bad taste in my mouth, at present i'm undecided, i might just delete the whole thing and go back to windows or maybe its worth giving Ubuntu 9.04 a try?  im reading alot of people who are suffering problems with 9.10 didn't have them with 9.04.

---

### Post by beacon on 2009-11-08
To Stu 500. Please don't give up. It sounds as if you have a number of problems, as I did. However, I would never use Microsoft in a million years, and Ubuntu has a lot going for it. I know my advice was not considered good by one poster, and I really don't disagree with that person, since different people will have different responses. By all means try the CD to see how you get on, or do as I did and return to 9.04 if you have upgraded. Or is this your first attempt to use Ubuntu? If so, you might find the more settled version easier to manage, and I think it would be worth a try.

---

### Post by stu500 on 2009-11-10
> **beacon said:**
> To Stu 500. Please don't give up. It sounds as if you have a number of problems, as I did. However, I would never use Microsoft in a million years, and Ubuntu has a lot going for it. I know my advice was not considered good by one poster, and I really don't disagree with that person, since different people will have different responses. By all means try the CD to see how you get on, or do as I did and return to 9.04 if you have upgraded. Or is this your first attempt to use Ubuntu? If so, you might find the more settled version easier to manage, and I think it would be worth a try.

Hi Beacon,
Vista is my main OS but it doesn't run so well on my laptop so that's why im trying linux hopefully to eventually swap completely over. I went ahead and tried 9.04 but i couldn't get it to boot from my USB thumb drive, i also tried Mint7 but suffered the exact same problem with that as well - right now im using PClinxusOS Zen but that to has problems. I don't know if im cursed or what but it seems linux is against me :(

---

