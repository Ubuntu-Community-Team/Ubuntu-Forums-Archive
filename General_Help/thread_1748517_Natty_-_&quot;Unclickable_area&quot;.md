---
title: "Natty - &quot;Unclickable area&quot;"
date: 2011-05-03
forum: General Help
---

### Post by crisvm on 2011-05-03
Hi,
I'm using Ubuntu 11.04 and I'm experiencing a strange behavior: sometimes I'm not able to click within a certain area of the screen.
There's an invisible rectangle more or less at the center of the screen where it's not possible to click... It seems like there's a "ghost window" that can't be closed...
I've posted a video on youtube showing this: [http://www.youtube.com/watch?v=53rmkm6UIP4](http://www.youtube.com/watch?v=53rmkm6UIP4)
You can see that when I pass the mouse over these "invisible rectangle" the cursor changes... In this area I can't do anything!
Did anyone else get this same problem?

PS: Sorry if my english was not clear enough...

---

### Post by Quackers on 2011-05-03
Welcome to UF.
Your English is fine!
Had you just run an update when this happened?

---

### Post by crisvm on 2011-05-03
Actually, I'm running Natty from a USB stick... So I didn't install it and didn't run any update.

Thanks for replying...

---

### Post by Quackers on 2011-05-03
This kind of thing happened a few times during the testing phase with Natty. It appeared to have more than one cause but on my system I found that it was sometimes due to a "ghost" window being there (but invisible) during or just after running updates.
Obviously this is not happening in your case.
I'll keep my eye open for similar occurrences and maybe you should do the same. Sadly I can't help any further for the moment. Good luck :-)

---

### Post by trippin on 2011-05-03
I also am having this same issue. The rectangle is towards the lower half of the screen, only maybe about 100px (estimate) high, and probably about half the width of my screen (a little right of center).

My screen res is 1280 x 1024 if it matters.

I haven't restarted since this happened, and probably won't if anyone has any ideas of troubleshooting or logs I could give to help identify the "ghost window", otherwise I can restart and see if it goes away. It's not a total annoyance, but it definitely gets in the way.

Also running 11.04 with the unity desktop.

Edit-- This is a fresh installation through the WUBI installer also, just thought I'd mention.

---

### Post by crwcomposer on 2011-05-03
Same issue here. Unclickable area(s) on Ubuntu 11.04

I upgraded from 10.10 (which did not have this issue).

---

### Post by blime45 on 2011-05-04
Happing to me as well. Very odd, and very obnoxious.

---

### Post by NSDragon on 2011-05-04
I've seen it happen a few times to me, one towards the middle of the screen (1920x1080 viewport) and sometimes another one right over the indicator area in Unity on a clean install.

xwininfo says it's a nameless window. I've changed my pointer to DMZ black, but when hovering over those phantom areas it appears white as if I still had the default cursor theme. Running unity --replace to restart Unity fixes this for me.

---

### Post by elimartin on 2011-05-08
Hi I had the same issue, but it seems that it is solved now for me.

In additional drivers I allowed:
nVidia graphic cards driver(version 173)

instead of:
nVidia graphic cards driver(version current)[recommended]

And the unclickable area is gone!

---

### Post by up2early on 2011-05-08
My 11.04 Ubuntu Classic started to do this yesterday, but mine is more than a small unclickable area, it is the whole desktop. When I reboot into Unity everything works fine.

---

### Post by panosss on 2011-05-12
> **elimartin said:**
> Hi I had the same issue, but it seems that it is solved now for me.

In additional drivers I allowed:
nVidia graphic cards driver(version 173)

instead of:
nVidia graphic cards driver(version current)[recommended]

And the unclickable area is gone!

I also activated the 'nVidia graphic cards driver(version 173)'.
General behavior is better. 
Unclickable areas reduced BUT still exist. (just discovered that the last line of this message I 'm writing, is unclickable:P:P)! (if we divide the screen in 3 equal pieces, the lowest third is uncklicable. Not the whole of it, a piece).

---

### Post by zobayer1 on 2011-05-12
I don't have any unclickable areas, but invisible rectangles appear here and there randomly (specially when I Right Click to invoke some menu, when the menu disappears, it still leaves the blank box, which sometimes covers icons, taskbars, etc etc... also the right click is working abnormally, which works fine in fedora and win xp. I am having a strong feeling to switch back to 10.10.

---

### Post by harlequin_ on 2011-05-12
Hi,

I also (most of the time) have uclickable areas on my screen. 

I mean.. I really like Ubuntu including all the idea behind it and stuff, but what kind of testing is this? Of course I understand that there will and should be things that can only be corrected after the new version of an OS is released, but unclickable areas + systems that cannot wake up after suspension and hibernate? Are you kidding me? Are these people testing their new release on a single computer, using particular hardware?

Isn't is wise to check the new OS with some different popular hardware and then release it? What is this seriously, we can simply not CLICK on some areas unless we don't logout/login or restart? 

....
I mean, this is really a disgrace. The time we need to wait for appropriate fixes will almost be equal to the time in between two different releases. I cannot believe this.

---

### Post by panosss on 2011-05-13
> **panosss said:**
> I also activated the 'nVidia graphic cards driver(version 173)'.
General behavior is better. 
Unclickable areas reduced BUT still exist. (just discovered that the last line of this message I 'm writing, is unclickable:P:P)! (if we divide the screen in 3 equal pieces, the lowest third is uncklicable. Not the whole of it, a piece).

Today works perfectly, uncklickable areas are gone, I don't know why, I didn't update anything. I have turned off automatic updates.
Anyway, I'm glad this happened :).

---

### Post by harlequin_ on 2011-05-13
> **panosss said:**
> Today works perfectly, uncklickable areas are gone, I don't know why, I didn't update anything. I have turned off automatic updates.
Anyway, I'm glad this happened :).

Hi, is it possible that you describe step by step how I also can do this. Because I'm also using an NVIDIA card, and I'm afraid that what causes the problem. Would be really great if you can help me with instructions.

Thanks in advance..

---

### Post by panosss on 2011-05-13
What instructions? As I said I don't know how it got fixed.
But, unfortunatelly, I was wrong. It's NOT fixed.

---

### Post by harlequin_ on 2011-05-13
LOL. Sorry, I mixed your post with the quotation above it.

> **panosss said:**
> What instructions? As I said I don't know how it got fixed.
But, unfortunatelly, I was wrong. It's NOT fixed.

---

### Post by sistoviejo on 2011-05-13
Running:
unity --replace 
...on the console seems to fix the problem.

---

### Post by ubume2 on 2011-05-13
I've had that problem with my old laptop.

Just rebooting took care of the problem for me.

---

### Post by digismack on 2011-05-28
I am still having this problem and it is driving me BONKERS. I am using Classic Desktop instead of Unity, so I can't use "unity --replace". Anyone have a fix for my situation? Thanks!

---

### Post by madebyjordan on 2011-05-28
> **digismack said:**
> I am still having this problem and it is driving me BONKERS. I am using Classic Desktop instead of Unity, so I can't use "unity --replace". Anyone have a fix for my situation? Thanks!

I'm having the same issue in Ubuntu Classic - in fact I had to scroll your message to the upper half of the screen to make the Quote button clickable.

Any help for this recently converted Ubuntu-type-person would be great, thanks!

---

### Post by julovac on 2011-05-29
***unity --replace***     or   ***compiz --replace***    will solve it, but i dont know why does it keep happening.

---

### Post by kevpatts on 2011-05-30
I've got the same issue. Here's a video of it being there initially but disappearing when I change windows: [http://www.youtube.com/watch?v=HpvRqQvu-P0](http://www.youtube.com/watch?v=HpvRqQvu-P0)

---

### Post by ernz on 2011-06-07
I'm not the only one. Thought I was going crazy! On my screen there is an area about 660px wide and 40px high sitting roughly 70% of the way from the top of the screen. See attachment. The dead area has been highlighted as accurately as I could.

---

### Post by kevpatts on 2011-06-07
It's in exactly the same place for me.

---

### Post by panosss on 2011-06-08
> **sistoviejo said:**
> Running:
unity --replace 
...on the console seems to fix the problem.

Thank you very much, this fixed the problem for me! (at least till now, I hope it wont appear again).

---

### Post by Grenage on 2011-06-08
I've had this issue sporadically on 11.04, and I'm _not_ using Unity.  Restarting does fix it, and it's not that common.

---

### Post by panosss on 2011-06-10
> **sistoviejo said:**
> Running:
unity --replace 
...on the console seems to fix the problem.

> **panosss said:**
> Thank you very much, this fixed the problem for me! (at least till now, I hope it wont appear again).
The problem is that I have to give that command in the terminal every time I start the pc.

---

### Post by 3rdalbum on 2011-06-10
> **alimay said:**
> I mean.. I really like Ubuntu including all the idea behind it and stuff, but what kind of testing is this? Of course I understand that there will and should be things that can only be corrected after the new version of an OS is released, but unclickable areas + systems that cannot wake up after suspension and hibernate? Are you kidding me? Are these people testing their new release on a single computer, using particular hardware?

Isn't is wise to check the new OS with some different popular hardware and then release it?

It's very wise to test with as much different hardware as possible. It's also very wise for the user to do the testing before the release, so they know that any problems they run into during the testing are likely to be solved before the release.

I don't have the problem on my computers anymore; if you haven't already, run the updates. You might need to issue 'unity --reset' once too, but since then it's been peachy for me.

---

### Post by harlequin_ on 2011-09-08
> **3rdalbum said:**
> It's very wise to test with as much different hardware as possible. It's also very wise for the user to do the testing before the release, so they know that any problems they run into during the testing are likely to be solved before the release.

I don't have the problem on my computers anymore; if you haven't already, run the updates. You might need to issue 'unity --reset' once too, but since then it's been peachy for me.

Hmm. So what if someone is a Windows user,  finds that there is a *stable* release of some Ubuntu version and installs it and realizes that his/her computer cannot wake up after a suspension? He/she is unwise because he/she did not know about the upcoming of this stable version and had not tasted the Beta?

Please.. There are these situations where the user cannot be held responsible in any way, and I believe this was one of the cases. I was a bit frustrated at that time and eventually whined about the situation. 

Ubuntu 11.04 is also very peachy for me nowadays, one month before the newer version is released. And I still love Ubuntu and all that.

Also, I believe it is very unwise for inexperienced users (who have no idea about how to create a new partition, install the new version and try it) to go for alphas/betas before stable releases, as it can very easily lead to a disaster.

---

