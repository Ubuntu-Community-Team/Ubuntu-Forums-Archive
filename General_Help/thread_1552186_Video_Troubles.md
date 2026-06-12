---
title: "Video Troubles"
date: 2010-08-13
forum: General Help
---

### Post by will22 on 2010-08-13
Hello,
I have Dell Inspiron 9400, and Ubuntu was running great until i tried the latest 10.04.
All i see is purple and black lines flickering and jumping around.
The same with the live disk.

I'd appreciate if anyone can tip me on how to solve this problem.
I'd really hate to walk away from ubuntu because of this.

Thank you

---

### Post by sydbat on 2010-08-13
> **will22 said:**
> Hello,
I have Dell Inspiron 9400, and Ubuntu was running great until i tried the latest 10.04.
All i see is purple and black lines flickering and jumping around.
The same with the live disk.

I'd appreciate if anyone can tip me on how to solve this problem.
I'd really hate to walk away from ubuntu because of this.

Thank youHave you tried the 'fix X' (or whatever it is called) in the recovery section during boot? Or the 'dpkg' fix?

However, I suspect that, because the LiveCd also has the same behaviour, you might not be successful with an install. Possibly too old of a video card? Although, according to the Googles (:P), your lappy came with the NVIDIA Go 7900 GS, which is supposedly still supported.

---

### Post by varunendra on 2010-08-13
> **sydbat said:**
> Have you tried the 'fix X' (or whatever it is called) in the recovery section during boot? Or the 'dpkg' fix?

It is 'failsafeX' :P

Press & hold 'shift' while booting to bring up advance boot menu, select 'Recovery mode', then what sydbat suggested.

---

### Post by will22 on 2010-08-14
> **varunendra said:**
> It is 'failsafeX' :P

Press & hold 'shift' while booting to bring up advance boot menu, select 'Recovery mode', then what sydbat suggested.

I'll try that, thank you

---

### Post by will22 on 2010-08-15
Looks like i'm just out of luck :(
Probably i'll stick with Mandriva, at least until next Ubuntu update

---

### Post by varunendra on 2010-08-15
> **will22 said:**
> Looks like i'm just out of luck :(
Probably i'll stick with Mandriva, at least until next Ubuntu update

O-O.., bad luck! But why so serius? :D

Good thing is that at least you are willing to stick with linux and you have a working choice for that. Besides, you said that "ubuntu was running great until 10.04". Then why don't you stick with the earlier version that worked for you?

It seems that the latest kernel still needs a lot of work to minimise those graphics problems and thus we may just need to wait until that happens (in Lucid or maybe in maverick). Till then, [Karmik]("http://releases.ubuntu.com/9.10/") is working great for most of us!

One more thing (I'm sure you must have already tried it, but since you haven't mention here....) that sometimes helps while cd booting:

Try [this]("http://ubuntuforums.org/showpost.php?p=9714016&postcount=5"). It is 'nomodeset' that sometimes helps in graphics issues.

---

### Post by will22 on 2010-08-16
I am getting somewhere with 10.10 Alpha 3, but with it i am having another issue :)
The screen on my laptop is pretty messed up (bunch of vertical lines). I haven't replaced it yet but using external monitor LG 24".
The issue is that the screen goes black for 1-2 seconds every 30 seconds (approximately)
Well, i'm lurking around the forums, hoping to find solution

---

### Post by will22 on 2010-08-16
My problem is solved!
If anyone interested, here is the solution that worked for me:

[http://beyondteck.blogspot.com/2010/05/flickering-monitor-in-ubuntu-1004-for.html](http://beyondteck.blogspot.com/2010/05/flickering-monitor-in-ubuntu-1004-for.html)

I'm running Ubuntu 10.10 Alpha 3 now without any problems (at least so far :) )

---

### Post by pndragon on 2010-08-16
What if you're stuck with an old e-machine desktop that is jumping to low graphics mode every time you turn around? This is getting incredibly frustrating.

---

### Post by will22 on 2010-08-17
> **pndragon said:**
> What if you're stuck with an old e-machine desktop that is jumping to low graphics mode every time you turn around? This is getting incredibly frustrating.

No arguments here....

---

