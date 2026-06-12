---
title: "Extreme Frustration w/Linux in general (mini rant)"
date: 2010-02-12
forum: General Help
---

### Post by Pres B on 2010-02-12
Hey everyone.  I haven't posted much... But lately I have been trying to get help with my Mint 7 KDE system.

I have tried Debian, Ubuntu, Linux Mint (Gnome and KDE) and have had problems with each one of them.  

My Mint Gloria KDE is crashing all the time now.  I understand that there may be some tweaking to do in order to get everything working properly, but this is getting ridiculous.  

Most recently all of my browsers crash...Konqueror, Firefox (all the time), Chrome (constantly), Opera (only a couple times, but still).  

X or KDM or whatever controls my environment has been having fits lately for reasons I can't explain.  I even kill compiz every time I boot up, but that doesn't seem to help anymore.  

I can't close my laptop or put it to "sleep" b/c when I try to get started again I get I/O errors and have to hard reset anyway.

I keep seeing these posts about Linux "just working."  I haven't experienced that...ever.  And I would like to, but I find myself trying to get the OS to work far far more than actually getting work done.  

Worst part, I booted into Windows to post this. I didn't want to do that but I feared I would launch my laptop across the room if Linux crashed again.  

All I would like to do is some web development (I installed XAMPP, and Wordpress and learned while doing so) and listen to music while I do it.  That's all.  Maybe some video editing and DVD authoring later on....

I don't need my laptop to do back-flips....I just don't want it to crash.  

Is this a typical experience?

---

### Post by lykwydchykyn on 2010-02-12
> **Pres B said:**
> 

Is this a typical experience?

Well, not for me, or else I wouldn't be here still using Kubuntu.  I suspect others would say the same.

Seeing as you're talking about several different distros having several different problems, it's a little hard to address things specifically; but I would suggest to you the common denominator here is your laptop.  Some hardware just does not play nicely with Linux.  This could possibly be the root of the problems.

I'm personally OK with Kubuntu's KDE implementation (apart from the package manager), but a lot of people say it's not the best, and Debian's has it's own issues.  Maybe OpenSuse is worth a try; everything you've tried so far is pretty much in the same family, it might be time to branch out to find something more suited to your hardware and usage habits.

---

### Post by jken146 on 2010-02-12
It doesn't sound like a typical experience.

You mentioned I/O errors. Check your hard disk, and check your RAM for errors (the GRUB menu contains a memtest option).

---

### Post by Pres B on 2010-02-12
> **lykwydchykyn said:**
> I would suggest to you the common denominator here is your laptop.

I have considered this.  I had issues with NVIDIA drivers when I first got started with Linux... And wireless issues, too.

Is there generally anything that I should look out for as far as processors, video or wireless cards for when I look for another laptop.  (I may just give my wife this one and buy one that would "play nice" with Linux.)  

> **lykwydchykyn said:**
> Maybe OpenSuse is worth a try; everything you've tried so far is pretty much in the same family, it might be time to branch out to find something more suited to your hardware and usage habits.

I thought about that, too.  I really liked openSUSE when I sampled the Live CD.  I might have to give it another shot.

---

### Post by Pres B on 2010-02-12
> **jken146 said:**
> It doesn't sound like a typical experience.

You mentioned I/O errors. Check your hard disk, and check your RAM for errors (the GRUB menu contains a memtest option).

Thanks, jken.  I'll look into that.

---

### Post by lykwydchykyn on 2010-02-12
> **Pres B said:**
> I have considered this.  I had issues with NVIDIA drivers when I first got started with Linux... And wireless issues, too.

Is there generally anything that I should look out for as far as processors, video or wireless cards for when I look for another laptop.  (I may just give my wife this one and buy one that would "play nice" with Linux.)  


Well, the fool-proof method is to buy a laptop with Linux pre-installed.  Nvidia is usually pretty good as far as video performance once you get the proprietary drivers loaded, but as for wireless and network stuff I couldn't say.

ATI has had a lot of problems with Linux, but it's improving.

Intel generally works very well with Linux, but their hardware isn't always so great for high-intensity usage.

Overall, I've had good luck with Dell stuff and Linux, but you always have a weird model here and there.

---

### Post by t4thfavor on 2010-02-12
The sleep problem is common on laptops with Nvidia and ATI cards, I have intel GMA945, which sleeps and unsleeps perfectly. I can leave it on for days, witn no problems.


As for the io errors, I would suggest checking ram/hdd, but it still could be caused by the graphics drivers, as sometimes weird things happen.


I would try disabling desktop effects as they are still young, and tend to cause problems.

Best advice is to pick a decent linux distro such as ubuntu, and stick with it, eventually you will get it all ironed out.


Also if you feel you really have a bug, report it, and be part of the solution.

It feels great, when a bug you reported is squashed, and lots of people are happy because of it.

---

### Post by jwbrase on 2010-02-12
> **t4thfavor said:**
> 
As for the io errors, I would suggest checking ram/hdd, but it still could be caused by the graphics drivers, as sometimes weird things happen.


He says he's getting I/O errors from trying to come out of sleep mode.

---

### Post by Pres B on 2010-02-12
> **lykwydchykyn said:**
> Well, the fool-proof method is to buy a laptop with Linux pre-installed... Overall, I've had good luck with Dell stuff and Linux, but you always have a weird model here and there.

Thanks for the advice.  I had looked at Dell's laptops with Ubuntu installed when I first started trying out distros.  I will definitely revisit.  

On a side note, I just finished downloading the OpenSUSE 11.2 ISO.  Hope that goes well.

---

### Post by QIII on 2010-02-12
You might try Fedora 12, too.
 
Hey.  Whatever works for you is good.

---

### Post by Pres B on 2010-02-12
> **t4thfavor said:**
> As for the io errors, I would suggest checking ram/hdd, but it still could be caused by the graphics drivers, as sometimes weird things happen.
Wouldn't something have been detected with the "routine" disk checks on start up?  Mint ran one after a crash yesterday, and didn't report anything... ?


> **t4thfavor said:**
> I would try disabling desktop effects as they are still young, and tend to cause problems.
When I boot up, the first thing I do is kill the compiz process.  I haven't disabled all the desktop effects, though.  I think I'll try that as well.


> **t4thfavor said:**
> Best advice is to pick a decent linux distro such as ubuntu, and stick with it, eventually you will get it all ironed out.


I hear you.  I've really been trying lately to get everything settled, but with some of the advice regarding possible hardware issues, I think I will try OpenSUSE, and if all else fails try a laptop with completely different chip sets / hardware, etc.

---

### Post by tcchris on 2010-02-12
Could be your hardware ,
But , I have noticed that friends coming from windows tend to install programs , etc from the internet .
We don't know your situation , but I would recomend , only install programs from the repos . Except maybe add medibuntu , if you need that .
You will have a much more stable system that way

---

### Post by Pres B on 2010-02-12
> **tcchris said:**
> Could be your hardware ,
But , I have noticed that friends coming from windows tend to install programs , etc from the internet .
We don't know your situation , but I would recomend , only install programs from the repos . Except maybe add medibuntu , if you need that .
You will have a much more stable system that way

I think the only things I installed from the net was Wordpress, and XAMPP.  Oh wait, I think Netbeans, too.  I can't remember.  Usually the only reason I'll download off the net is b/c a newer version is available online.  But I'll take your advice, though.

---

### Post by jwbrase on 2010-02-12
> **Pres B said:**
> Is this a typical experience?

To some degree, yes. Linux controls a fairly small minority of the desktop/laptop OS market, so vendors don't always release drivers for it for their hardware, and community written drivers are often very buggy. My desktop at home, which I first tried Linux out on, never ran it entirely smoothly. I hear that laptop hardware can be worse for this than desktop hardware. This machine that I have here I bought from System 76 with Ubuntu pre-installed, and it runs like a charm, without any of the major problems I had on the other one. 

It's a bit less stable than XP, but not enough to be annoying, and there are a few minor instabilities in Opera that I suspect are just bugs in the way Opera wrote their browser for Linux. I still use Opera because it has a lot of nice features, and the problems (which seem to involve a memory leak) generally aren't problems as long as you close it out and restart it before they get a chance to cause a crash).

You may want to try LXDE. After I upgraded the desktop back home to Jaunty, GNOME stopped working for me, but I found that LXDE worked.

---

### Post by QIII on 2010-02-12
> **jwbrase said:**
> To some degree, yes. Linux controls a fairly small minority of the desktop/laptop OS market, so vendors don't always release drivers for it for their hardware, and community written drivers are often very buggy. 

To some degree in the same manner as learning German can be difficult for an English speaker.  Once you are familiar, it becomes more obvious how to get things done -- to "fix" things, if you like.

Bear in mind that the failure of OEMs to provide Linux drivers is not a fault in Linux itself.  OEMs are trying to make money, and they go to where the money is.  I can hardly fault them for that.  (The problem here is that one OS purveyor holds so much market share that they can bend an entire industry to their will.  Note that I am NOT saying Windows itself is a bad OS.  Simply pointing out something I do not like about a particular company's business practices.)

If open source drivers are "buggy", it is because the developers have to essentially reverse engineer to a black box.  I wouldn't call that "buggy".  I would call it making the best educated guess.  But the effect for the user is the same.  Some things are just a pain to get working.

---

### Post by jwbrase on 2010-02-12
> **QIII said:**
> To some degree in the same manner as learning German can be difficult for an English speaker.  Once you are familiar, it becomes more obvious how to get things done -- to "fix" things, if you like.

Certainly, although sometimes the hardware just won't cooperate. 

> 
Bear in mind that the failure of OEMs to provide Linux drivers is not a fault in Linux itself.

Certainly not. 

> OEMs are trying to make money, and they go to where the money is.  I can hardly fault them for that.  (The problem here is that one OS purveyor holds so much market share that they can bend an entire industry to their will.  Note that I am NOT saying Windows itself is a bad OS.  Simply pointing out something I do not like about a particular company's business practices.)

If open source drivers are "buggy", it is because the developers have to essentially reverse engineer to a black box.  I wouldn't call that "buggy".  I would call it making the best educated guess.  But the effect for the user is the same.  Some things are just a pain to get working.

Exactly. Although I would argue about the "I wouldn't call that buggy" part. "Buggy" just means that it doesn't work as intended. Since the developers are reverse engineering a black box, it's not their fault that the drivers are buggy, but they do not work as intended, and are thus buggy.

---

### Post by tcchris on 2010-02-12
I am not sure I would say less stable than xp .
No virus , malware etc 
My system runs 24/7 , doesn't crash unless I do something less than intelligent

---

### Post by QIII on 2010-02-12
> **jwbrase said:**
>  but they do not work as intended, and are thus buggy.

As a software developer, I guess I have a different notion of what a bug is.

If I provide an interface to someone else who develops against that, but do not make it clear to him what is expected as a valid range of values as arguments to pass in to the list, his code is not "buggy" if it doesn't work.

I'm at fault for not providing documentation.

If I write code that does not do what it is intended to do internally when passed valid arguments as specified, then I have produced a bug.

---

### Post by HappyFeet on 2010-02-12
No, your experience is not typical. If it was, no one would use linux. Some computers are just very proprietary in nature, and will only run the OS that it came with. Your computer is just not linux compatible, plain and simple. Get one that is, and you will have a great experience. For me, ubuntu is the best OS I have ever used, and I have used everything since win95.

 Good luck to you.

---

### Post by jken146 on 2010-02-13
> **HappyFeet said:**
> Your computer is just not linux compatible, plain and simple.

You don't know that. Please don't be so quick to tell the OP to go and shell out on new kit!

Pres B: Did you run the memtest?

---

