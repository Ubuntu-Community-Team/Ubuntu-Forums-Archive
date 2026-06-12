---
title: "Rosetta Stone not loading :/ Plz help"
date: 2010-12-13
forum: General Help
---

### Post by Mindswap1 on 2010-12-13
Hi Guys! I really need Rosetta Stone so I can get an extra aide while I study Japanese in university, however it doesn't seem to be working for me. It worked perfectly in 9.10 and 10.04, but in 10.10 it doesn't work. After I click my account name it just leads me to a blank page. How can I fix this :/.

---

### Post by Keypel on 2010-12-13
I also study Japanese with Rosetta Stone. Which Rosetta Stone version do you use? I use them both but actually prefer the older v2 better than the v3.

Anyways, I have Ubuntu 10.10 and wine 1.2.1 and v2 runs 99% perfect. I havn't tried v3 on Ubuntu yet.

EDIT

After reading your post, I installed v3. I get the same blank screen.

I saw a few people with the same blank screen problem >> [here]("http://appdb.winehq.org/objectManager.php?sClass=version&iId=18861") << in the comment section

but no one says how to fix it or what causes it.

EDIT

I tried upgrading wine from 1.2.1 to 1.3.9 and that didn't work, then I tried installing winetricks and DirectX via winetricks and that didn't work. Still same blank screen after user name login. It seems other people can get it running so I'm stumped for now. If you figure it out, let me know.

EDIT

I also tried 

./winetricks flash

Still blank screen, Uggg, I give up.

[SIZE="4"]**UPDATE:**

**[COLOR="Red"]As of 04-15-2011 Rossetta Stone is working with 2.6.35-28-generic and wine 1.3[/COLOR]** **Wine 1.2 no longer works with the newer kernels.**[/SIZE]

---

### Post by Mindswap1 on 2010-12-14
I have version 3, and it Used to work flawlessly before on 10.4 idk why thats changed. If I figure something out I'll let you know.

---

### Post by Spyderkid on 2010-12-14
version 3.0, 3.2, 3.3 or 3.4.5?

[and have a look at this]("http://appdb.winehq.org/appview.php?appId=1867")

---

### Post by Keypel on 2010-12-14
> **Spyderkid said:**
> version 3.0, 3.2, 3.3 or 3.4.5?

[and have a look at this]("http://appdb.winehq.org/appview.php?appId=1867")

I'm having the same blank screen problem as Mindswap1.

I'm using 3.4.5 which has a gold rating. I already saw your link (see post #2 of this thread)

> **Keypel said:**
> 
I saw a few people with the same blank screen problem >> [here]("http://appdb.winehq.org/objectManager.php?sClass=version&iId=18861") << in the comment section


I tried flash and DirectX for winetricks which are both suggested on WineHQ, Do you have any other suggestions?

_EDIT_

I just installed msxml4 for winetricks as well, that didn't work either. So all together I installed flash, DirectX and msxml4. Everything but the kictchen sink.

Any Sugestions Welcome.

[PS]("http://ubuntuforums.org/attachment.php?attachmentid=178429&stc=1&d=1292366445") Here is a screen shot of the Rosetta Stone Blank Screen:

(I assume this is the same blank screen as the OP is getting.)

---

### Post by Keypel on 2010-12-26
It's been a week, Just wanted to Bump this. I'm curious as to what a solution could be.

---

### Post by CapnSchmitty on 2011-01-02
I've got the exact same problem.  I click my name, and it doesn't work.  Using v3 under Maverick, have everything I should need installed in Wine.

---

### Post by energybeing on 2011-01-09
Ok guys, I figured out where the problem is.  It's the kernel.  For some reason, kernel 2.6.35-24 kernel does not work, but the 2.6.35-22 kernel works fine.  Boot with this kernel and it will work.  As for the actual cause, I have no idea, as I'm not a programmer.  If anyone can submit a bug report as I also have not done that before, that would be cool.

---

### Post by Keypel on 2011-01-10
> **energybeing said:**
> Ok guys, I figured out where the problem is.  It's the kernel.  For some reason, kernel 2.6.35-24 kernel does not work, but the 2.6.35-22 kernel works fine.  Boot with this kernel and it will work.  As for the actual cause, I have no idea, as I'm not a programmer.  If anyone can submit a bug report as I also have not done that before, that would be cool.

Just wanted to confirm energybeing's findings. 

WoW!! How did you ever figure this out? I tried everything under the sun but I never would have guessed kernel. Just as you said [COLOR="Red"]2.6.35-24 is no-go[/COLOR] but surprisingly **[COLOR="SeaGreen"]2.6.35-22 works[/COLOR]**!!

---

### Post by energybeing on 2011-01-10
Well, I remembered that it worked with Ubuntu 10.04, and also that I had it working with 10.10 in November.  I tried a fresh install of 10.10 with no updates, and lo and behold, it worked after installing wine.  Then I installed all the updates, rebooted, and it was broken.  So, I then did another fresh install, and started installing updates one by one, and when I patched the kernel and then rebooted, all of a sudden Rosetta Stone stopped working.  So, I quickly rebooted to the older kernel as it was still in my /boot directory, and it worked.  Took about a day and a half, and it was frustrating because if I had thought to simply reboot with the older kernel in the first place, I would have saved a ton of time.
EDIT: I also noticed that the 2.6.35-24 kernel was released on December 2nd, which explains why Rosetta Stone was working for me in November.

---

### Post by Mindswap1 on 2011-01-10
> **energybeing said:**
> Well, I remembered that it worked with Ubuntu 10.04, and also that I had it working with 10.10 in November.  I tried a fresh install of 10.10 with no updates, and lo and behold, it worked after installing wine.  Then I installed all the updates, rebooted, and it was broken.  So, I then did another fresh install, and started installing updates one by one, and when I patched the kernel and then rebooted, all of a sudden Rosetta Stone stopped working.  So, I quickly rebooted to the older kernel as it was still in my /boot directory, and it worked.  Took about a day and a half, and it was frustrating because if I had thought to simply reboot with the older kernel in the first place, I would have saved a ton of time.
EDIT: I also noticed that the 2.6.35-24 kernel was released on December 2nd, which explains why Rosetta Stone was working for me in November.


Kudos Energybeing you rock! This is going to help a lot of people so thanks mate! People like you make Ubuntu so much more usable ^.^.

---

### Post by Keypel on 2011-01-10
> **energybeing said:**
> Well, I remembered that it worked with Ubuntu 10.04, and also that I had it working with 10.10 in November.  I tried a fresh install of 10.10 with no updates, and lo and behold, it worked after installing wine.  Then I installed all the updates, rebooted, and it was broken.  So, I then did another fresh install, and started installing updates one by one, and when I patched the kernel and then rebooted, all of a sudden Rosetta Stone stopped working.  So, I quickly rebooted to the older kernel as it was still in my /boot directory, and it worked.  Took about a day and a half, and it was frustrating because if I had thought to simply reboot with the older kernel in the first place, I would have saved a ton of time.
EDIT: I also noticed that the 2.6.35-24 kernel was released on December 2nd, which explains why Rosetta Stone was working for me in November.

Wow!! you put allot of effort into figuring this out. I for one really appreciate it. Big Thank you!!

---

### Post by energybeing on 2011-01-10
> **Mindswap1 said:**
> Kudos Energybeing you rock! This is going to help a lot of people so thanks mate! People like you make Ubuntu so much more usable ^.^.

Thanks man!  That makes me feel warm and fuzzy inside :D!

---

### Post by energybeing on 2011-01-10
> **Keypel said:**
> Wow!! you put allot of effort into figuring this out. I for one really appreciate it. Big Thank you!!

Yeah, I really wanted to make it work.  You're welcome.  :-)

---

### Post by shatanas on 2011-01-22
> **energybeing said:**
> Ok guys, I figured out where the problem is.  It's the kernel.  For some reason, kernel 2.6.35-24 kernel does not work, but the 2.6.35-22 kernel works fine.  Boot with this kernel and it will work.  As for the actual cause, I have no idea, as I'm not a programmer.  If anyone can submit a bug report as I also have not done that before, that would be cool.
I have the same problem and was overjoyed to find it solved, but.....how do you change the kernel!??

---

### Post by shatanas on 2011-01-22
> **energybeing said:**
> Ok guys, I figured out where the problem is.  It's the kernel.  For some reason, kernel 2.6.35-24 kernel does not work, but the 2.6.35-22 kernel works fine.  Boot with this kernel and it will work.  As for the actual cause, I have no idea, as I'm not a programmer.  If anyone can submit a bug report as I also have not done that before, that would be cool.
I have the same problem and was overjoyed to find the solution, but.....how do you change the kernel!??

---

### Post by energybeing on 2011-01-22
> I have the same problem and was overjoyed to find the solution, but.....how do you change the kernel!??
When you first boot up your computer, you should see a menu called Grub.  You should be presented with at least 4 choices here.  The first choice, is the latest installed kernel.  The second choice is that same kernel with recovery mode.  You're going to want the third choice, which should be a different kernel.  Don't pick recovery mode.

---

### Post by shatanas on 2011-01-22
> **energybeing said:**
> When you first boot up your computer, you should see a menu called Grub.  You should be presented with at least 4 choices here.  The first choice, is the latest installed kernel.  The second choice is that same kernel with recovery mode.  You're going to want the third choice, which should be a different kernel.  Don't pick recovery mode.
you mean at the login screen? I get 4 options to choose from the bottom pane: Start Ubuntu Desktop Edition in recovery, normal, safe mode and "user defined"

If that's not it then imah confused

---

### Post by energybeing on 2011-01-22
> you mean at the login screen?
No, I mean the Grub boot menu.  You should see this before the login screen.  It will be a black background and there will be white text.

---

### Post by shatanas on 2011-01-22
> **energybeing said:**
> No, I mean the Grub boot menu.  You should see this before the login screen.  It will be a black background and there will be white text.
well I don't get that, but google says i need to hold down shift whilst booting to see it. Let me try...

---

### Post by shatanas on 2011-01-22
YAY!!! Works like a charm now! Thank you!!

---

### Post by energybeing on 2011-01-22
> YAY!!! Works like a charm now! Thank you!!
You're welcome.  I'm glad I was able to help you.

---

### Post by energybeing on 2011-03-16
It works again with the 2.6.35-28 Kernel!  Awesome.

---

### Post by Keypel on 2011-03-17
> **energybeing said:**
> It works again with the 2.6.35-28 Kernel!  Awesome.

I wanted to confirm this so I went to the update manager, refreshed the list. It says My system is up do date but I am still on 2.6.35-27 ?

---

### Post by energybeing on 2011-03-17
> **Keypel said:**
> I wanted to confirm this so I went to the update manager, refreshed the list. It says My system is up do date but I am still on 2.6.35-27 ?
I have the boxes checked for Pre-released (maverick-proposed) and Unsupported (mavarick-backports) updates.  I don't recommend these for everyone, but that is how I have the newer kernel.  There are other ways to install the newer kernel as well.  You can download the kernel from:
[http://kernel.ubuntu.com/~kernel-ppa/mainline/]("http://kernel.ubuntu.com/~kernel-ppa/mainline/")
 Again I don't recommend doing these things unless you know how to reverse the changes you make in case you break something.

---

### Post by Keypel on 2011-03-19
> **energybeing said:**
> It works again with the 2.6.35-28 Kernel!  Awesome.

2.6.35-28 just came down as a regular release for the rest of us.

2.6.35-28 is still a blank screen just as 2.6.35-23 thru -27 was.

```
user-01@pc-01:~$ uname -r
2.6.35-28-generic
user-01@pc-01:~$
```

2.6.35-[COLOR="Red"]22[/COLOR] is still the only one [COLOR="#ff0000"]working[/COLOR] here.

Is it possible that the pre-release -28 and the mass release -28 is somehow different?

---

### Post by energybeing on 2011-03-19
> **Keypel said:**
> 2.6.35-28 just came down as a regular release for the rest of us.

2.6.35-28 is still a blank screen just as 2.6.35-23 thru -27 was.

```
user-01@pc-01:~$ uname -r
2.6.35-28-generic
user-01@pc-01:~$
```

2.6.35-[COLOR="Red"]22[/COLOR] is still the only one [COLOR="#ff0000"]working[/COLOR] here.

Is it possible that the pre-release -28 and the mass release -28 is somehow different?

It's possible.  I have the same output for uname -r.  That's odd.

---

### Post by Keypel on 2011-03-19
It would be helpful if a few more people tried the new kernal and posted their results here. It's a no go for me.

---

### Post by energybeing on 2011-03-19
I have a couple other machines running Ubuntu 10.10 that I could try it out on.  I'll let you know how it goes.

---

### Post by Keypel on 2011-03-20
That would be great, thanks!

---

### Post by Keypel on 2011-04-15
@energybeing

I got it working on 2.6.35-28-generic.

I just upgraded wine to 1.3. Seems that Wine 1.2 no longer works with the newer kernels.

---

### Post by babusar on 2011-06-17
I upgraded wine to 1.3 in 2.6.32-32-generic and Rosetta Stone seems to be working perfect now.

---

