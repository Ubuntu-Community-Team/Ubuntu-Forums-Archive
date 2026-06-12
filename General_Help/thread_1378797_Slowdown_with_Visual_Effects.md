---
title: "Slowdown with Visual Effects"
date: 2010-01-11
forum: General Help
---

### Post by slickg on 2010-01-11
Hello I am pretty new to Ubuntu 9.10 64 Bit and I am having a bad slowdown issue when I enable Visual Effects with the Ati proprietary drivers that come with the installation.  Everything runs very slow maximizing and minimizing take about 3-5 seconds per click and the effects get all choppy and don't look right like they did on my x1950 video card.  I have tried downloading the current drivers from the ATI site but they don't seem to be initialising correctly after I perform the install.  

I also know that the graphics card is not the culprit as it works perfectly fine on my Windows 7 64 bit install.  There is no reason that my video card cannot handle the Visual Effects as it is a 1GB 4890 should have more than enough horsepower.  

My machine is:
AMD Phenom II 965 Black Edition
8 GB G. Skill 1600 DDR3 Memory
1 TB Western Digital Caviar hard drive
1 GB 4890 Graphics Card ATI.

Any help would be greatly appreciated so that I could get the Visual Effects, thanks!

---

### Post by slickg on 2010-01-12
Also, I have run all updates and I now got the current ATI drivers from ATI's site and am still having the same problem.  If I disable visual settings the machine runs perfectly normal it's just when I enable visual settings that it starts to freak out and act all slow.  Does anyone else have a 4890 and figure this out?

---

### Post by slickg on 2010-01-13
Is anybody using a 4890 with Ubuntu 9.10 and gotten it to work? Thanks!

---

### Post by akakingess on 2010-01-13
> **slickg said:**
> Is anybody using a 4890 with Ubuntu 9.10 and gotten it to work? Thanks!

Have you tried uninstalling the drivers from ATI and use the built-in ones from Ubuntu, I have better results from the built-in ones than I do straight from the manufacturer. Maybe because Ubuntu has had the time to fine-tune it and incorporate it directly within the kernel? Anyways, that would be what I would try first, other than that, I would just have to say that until all of the companies make their respective drivers open source there will be a lag behind as far as the most recent cards running as they should.

---

### Post by warfacegod on 2010-01-13
When you installed the drivers you downloaded, did you deactivate the preinstalled drivers? Another question is whether or not you've had a kernel upgrade since the new drivers? Sometimes compiled drivers don't do well with kernel updates.

---

### Post by slickg on 2010-01-13
> **akakingess said:**
> Have you tried uninstalling the drivers from ATI and use the built-in ones from Ubuntu, I have better results from the built-in ones than I do straight from the manufacturer. Maybe because Ubuntu has had the time to fine-tune it and incorporate it directly within the kernel? Anyways, that would be what I would try first, other than that, I would just have to say that until all of the companies make their respective drivers open source there will be a lag behind as far as the most recent cards running as they should.
 
I've tried to enable the extra settings without any drivers installed...it would not let me even do that.  Then I tried enableing the restricted drivers that are inside the Hardware Drivers section that come with Ubuntu.  That allows me to enable the Extra settings but the machine gets all slow at that point.  If I click on something down in the task bar it takes about 5 seconds to come back and also the effects get all jittery, etc.  If I put it back on none then everything gets back to being "fine".  
 
If I run ubuntu in a Virtualbox while in Windows 7 The effects can be enabled and work without a hitch so I'm pretty sure it's a driver issue.  When I put my old x1950 vid card in I am allowed to enable the settings perfectly fine.
 
@warfacegod - Yes I actually completely purged and removed the existing drivers then installed the ones from ATI's site as well as downloading the most recent kernel image.  I didn't have any luck with either unfortunately.

---

### Post by warfacegod on 2010-01-13
I just installed 9.10 netbook as a dual boot with 9.10 normal on my laptop. In my normal install, Compiz custom settings work fine (as long as I don't get too pushy with my 64 MB video card). However, in 9.10 netbook, when I turn on the Extra settings, my desktop slows to a crawl, similar to what you are experiencing (remember same hardware, same drivers). When I reboot and go back into 9.10 netbook settings are still enabled and everything runs smooth as silk.

---

### Post by slickg on 2010-01-14
I have tried rebooting while the settings are enabled as you said and unfortunately things still run slow.  Thank you for the suggestion though.  It's quite bizarre that they run fine when I am using them in a Virtualbox within Windows.

---

### Post by Saiko Berry on 2010-01-14
Solution: Don't use visual effects, theyre a waste of resources.

---

### Post by skymera on 2010-01-14
> **Saiko Berry said:**
> Solution: Don't use visual effects, theyre a waste of resources.

This is useless, he wants to enable them. He should decide himself if they're a waste of resources. 

I had a HD4870 and worked fine with Compiz (Although sometimes slow because of poor drivers).

I suggest Envy.

```
 sudo apt-get install envyng-core 
```
run it with 

```
 sudo envyng -t 
```

Good luck :)

---

### Post by warfacegod on 2010-01-14
> **Saiko Berry said:**
> Solution: Don't use visual effects, theyre a waste of resources.

It may or may not be wasteful. Wasteful is, in this situation, purely a matter of opinion. I am able to do this on an nVidia geforce FX Go5200 *64* MB card and I don't consider it a waste at all. Grant you, I'm really pushing my luck but hey, this stuff is fun.

---

### Post by Saiko Berry on 2010-01-14
I'm just notoriously efficient. That's all ;)

---

### Post by akakingess on 2010-01-14
> **Saiko Berry said:**
> I'm just notoriously efficient. That's all ;)

I am the same way, if something is slowing my system down and keeping from working/playing at the most efficient/fastest pace, then I would just assume do without it ;)

---

### Post by slickg on 2010-01-14
> **akakingess said:**
> I am the same way, if something is slowing my system down and keeping from working/playing at the most efficient/fastest pace, then I would just assume do without it ;)

Which I have been and that works well but just the fact that I know something is wrong and not working as it should bothers me as my hardware should be more than enough to handle it if I want to use it.  

Who knows if I will come across other problems 3D rendering because of this in the future as well.  

Thanks for the suggestions guys I will try those Envy drivers that were suggested when I get back home.

---

### Post by akakingess on 2010-01-14
> **slickg said:**
> Which I have been and that works well but just the fact that I know something is wrong and not working as it should bothers me as my hardware should be more than enough to handle it if I want to use it.  

Who knows if I will come across other problems 3D rendering because of this in the future as well.  

Thanks for the suggestions guys I will try those Envy drivers that were suggested when I get back home.
I agree with you, too slickg, but the fact is that the newer graphics cards don't always work as advertised within a linux environment, for the sole fact that the manufacturers won't make their drivers available (i.e. open source) and allow companies like Canonical to incorporate them into the kernel so that we could have full 3D support and all would be wonderful with the world. I also never use drivers from the manufacturers that are posted online after the fact, just because I have never had any luck with them. It's a matter for me that I am just willing to wait for the bells and whistles to become available within any Linux distro, just because I prefer even a less than perfect running (graphically anyway) Ubuntu over the newest Windows distribution anyday. It's all a matter of opinion in the long run, anyway, I hope the best of luck to you and hope that you get your card running to your satisfaction and I am always willing to assist if I can.  Good luck to you and happy learning :D

---

### Post by slickg on 2010-01-16
Well, I tried those envy drivers that were mentioned and unfortunately it does the same thing as far as hanging when the extra settings are enabled.  I was thinking about trying Linux Mint 8 to see if it makes a difference but I'm guessing that since it's based off Ubuntu I will have the same issue but I guess it's worth a try.  Mint looks pretty interesting anyways so I wanted to try it out.

---

### Post by warfacegod on 2010-01-16
> **slickg said:**
> Well, I tried those envy drivers that were mentioned and unfortunately it does the same thing as far as hanging when the extra settings are enabled.  I was thinking about trying Linux Mint 8 to see if it makes a difference but I'm guessing that since it's based off Ubuntu I will have the same issue but I guess it's worth a try.  Mint looks pretty interesting anyways so I wanted to try it out.

I imagine you'll end up with the same issue no matter what Linux flavor you try.

---

