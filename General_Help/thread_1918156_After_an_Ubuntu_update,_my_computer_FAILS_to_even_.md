---
title: "After an Ubuntu update, my computer FAILS to even start up."
date: 2012-01-31
forum: General Help
---

### Post by Jerriy on 2012-01-31
My computer NO LONGER starts up when I shut down and (re)start. 

I have not installed even ONE program in the last couple of weeks/months (lately I've used the PC for internet only) which means the only thing that is screwing up my computer is Ubuntu's update  

Now what????????

Now I dread shutting it down!!!!!!!!

I'm at home so I don't want to keep the computer on 24/7

---

### Post by Bucky Ball on 2012-01-31
If you have already shut it down, how did you restart it? The last update may have been a new kernel and something's gone amiss (although this is odd for an old LTS release). Try dropping back to the previous kernel (should be third down on the grub list at boot) and see what happens.

---

### Post by Jerriy on 2012-01-31
> **Bucky Ball said:**
> If you have already shut it down, how did you restart it?...I don't know. All I know is that this time I tried to restart the pc half a dozen times and then it suddenly starts booting randomly.

> The last update may have been a new kernel and something's gone amiss...Oh something is definitely amiss. I have been using ubuntu from 2008 and I never had a boot issue before. 

> (although this is odd for an old LTS release).That's what I thought too. 

> Try dropping back to the previous kernel (should be third down on the grub list at boot) and see what happens.That sounds Chinese to me. 

I've never had this issue before so you might as well explain to me what those things mean.

---

### Post by Bucky Ball on 2012-01-31
Hold down shift or escape (not sure which for 10.04) at boot, before you get to the login screen. 

This should present you with a list of all installed kernels to choose from. The newest kernel is at the top, probably installed with the last update and giving you probs, so choose not the recovery kernel, which will be second down, but the previous kernel before the update, which will be third on the list.

Hope that makes more sense to you. I presume you normally boot to a login screen and bypass this bit ...

---

### Post by Jerriy on 2012-01-31
I see that list in a box is what's called kernel? 

Yes at startup it normally auto-chooses one of the list (the top one presumably) and starts booting unless I intervene.

---

### Post by Bucky Ball on 2012-01-31
Intervene. ;)

---

### Post by Jerriy on 2012-02-01
I intervened and used the recovery kernel and then went back to the default kernel (the only other kernels are memory test kernel and Windows kernels)

But now something else happened few hours after loging on and using the computer: it suddenly decided to auto-restart itself right in front of me while I was approaching it (without me even touching it!!!

Also Firefox has now suddenly shuts down almost every time I use full-screen on youtube and some other flash.

In other words I berely recognize my computer in the aftermath of the latest update

WTF is going on? Help!!!!!!!!!!!!!!

---

### Post by Jerriy on 2012-02-01
The problem has not gone away guys, HELP!

---

### Post by Jerriy on 2012-02-01
Here is what was on display one of the times it "hanged"```
[32.426691] Console:switching to colour frame buffer device 80x30
```

---

### Post by Jerriy on 2012-02-01
And at another time it hanged this:```
[14.839854] [COLOR=Red]BUG:Bad page[/COLOR] state in process ureadahead pfn:35e02
```

---

### Post by Jerriy on 2012-02-01
And aslo this:```
[14,839921] page:c1739040 flags:40000000 count:6094848 mpacount:0 mapping:(null) index:0
```

Help!

---

### Post by Jerriy on 2012-02-01
Now my computer "hanged" after it logged in and after I used it for an hr.

In other words this week's update of Ubuntu is nothing short of clusterf*ck
.

---

### Post by Jerriy on 2012-02-01
bump

---

### Post by iiiears on 2012-02-02
Hello,

I am wondering where the boot is stopped.

/var/logs

May have an answer for you.

 An uninformed guess would be the video card driver needs to be built against the new kernel.

---

### Post by Jerriy on 2012-02-02
> **iiiears said:**
> Hello,

I am wondering where the boot is stopped.

/var/**logs**

May have an answer for you.

 An uninformed guess would be the video card driver needs to be built against the new kernel.you mean /var/**log**? 

What file should I open in that folder?

---

### Post by Jerriy on 2012-02-02
bump

!!!!

---

### Post by Jerriy on 2012-02-02
This problem must be solved 

The latest crap of a login was in only after I tried it 6 times!

Also this time I tried to to boot via "recovery" kernel and that too failed to boot.

This was the last thing that booted in recovery kernel:```
Begin:Running /scripts/init-bottom ...
Done.
```

---

### Post by Jerriy on 2012-02-02
And the mess continues:

A minute ago the login (not the entire computer but only the GUI part beginning with my username and password input) decided to abruptly shut and restart (completely unprovoked by me I wasn't even touching any thing at that moment, just watching a video)
.

---

### Post by Jerriy on 2012-02-02
Strange how Ubuntu is beginning to act like a 10 year ago Windows-XP machine infected with malware

---

### Post by Jerriy on 2012-02-02
Browser just crashed multiple times in a row

Right now I am unable to continue using Ubuntu

Is this normal expected Ubuntu behavior?

---

### Post by Jerriy on 2012-02-02
Now half the programs can't even start 

I can't turn on update manager, synaptic etc etc, none of them even open. Terrific.

---

### Post by xyzzyman on 2012-02-02
First thing I would do is run memtest until it says it has passed or has failed. If it passes then we can go from there. 

Also, you said that grub shows windows on there. Are you able to successfully start windows? If not then I would definitely lean towards RAM or HDD failure with a very lost possibility of overheating/defective CPU.

---

### Post by Jerriy on 2012-02-02
Everything works perfectly in the windows part of my machine. It boots into it without a hint of a problem.

Only ubuntu fails and even that is not predictable or regular. And even that is strange because usually any problem I used to have is tracable to sound or flash issues or something new I installed or some firefox addon or the like. But now what happened is a bit strange cuz I have not installed a program in weeks! Was just using the pc for internet access. The only things being installed were via the automatic update of the already installed browser and other programs.

Anyway, I'll take your advice and run the memtest and see what that shows up.

---

### Post by Bucky Ball on 2012-02-03
Yea, weird. If Windows is working fine that leans away from hardware failure. Did Ubuntu work ok from the CD before you installed, if you tried that? Can you boot from the CD and 'Try Ubuntu' and see if that is problem free (preferably with an ethernet cable in). 

If all that fails you might want to try a more stable release if you are attempting this with 11.10. See if things work with the current LTS (long-term support) release, 10.04 LTS. If that works you could maybe go from there, upgrade and see what breaks.

If you have hard drive space you could install the various releases to different partitions so you will always have something to fall back on (presuming you find a release that is stable on your machine). The release you're using may just not be compatible with your computer's hardware configuration and may need some tweaking. Maybe vid.

You could try installing (or trying) Ubuntu setting the F6 (from memory) option at the first screen to 'nomodset' and see if that makes a difference.

A few suggestions ... good luck. ;)

---

