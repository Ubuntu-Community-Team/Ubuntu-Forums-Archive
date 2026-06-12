---
title: "Computer Freezeing up Over Night After Updates"
date: 2011-05-02
forum: General Help
---

### Post by Nasair on 2011-05-02
So I have no idea what is happening but I started getting a problem after some updates and then I decided to upgrade to 11.04 from 10.10 to see if this fixed the problem, then I just did a clean install last night and I'm still having problems. I'm always asleep when it happen or not around so I'm not sure what is happening right before this screen, but I can say I usually will only have VLC open (at this point I'm sure it stopped playing videos) and maybe Transmission in the background, nothing else. The computer won't respond to the Ctr+Alt+B+PrtScn or to the power button, or to Crt+Alt+F2 or the like, seems completely frozen...

Problem:

[IMG]http://i1129.photobucket.com/albums/m502/Nasairk/IMG_20110502_062421.jpg[/IMG]

&

[IMG]http://i1129.photobucket.com/albums/m502/Nasairk/IMG_20110502_062415.jpg[/IMG]

Any ideas?

---

### Post by keithpeter on 2011-05-02
> **Nasair said:**
> I'm always asleep when it happen or not around so I'm not sure what is happening right before this screen, but I can say I usually will only have VLC open (at this point I'm sure it stopped playing videos) and maybe Transmission in the background, nothing else.

Any ideas?

Hello Nasair

I've never experienced this, but the 

```
unable to handle kernel paging request at fffffffc
```

in your second screen photo is a kernel crash. 

How about running the computer disconnected from the Internet and with nothing running to see if that is ok? (eliminates random hardware problems).

---

### Post by Nasair on 2011-05-02
Thank you for that. I updated some minor fixes today so I'm hoping that helps, but I'll check it when I get home tonight to see if it bugged out and if it did I'll try letting it be on all night from a reboot to see if it still has issue.

Since you mention hardware issues I'm thinking it could be that because sometimes when I boot up machine from a powered off situation, and I mean powered off as I have it unplugged from the wall when I'm not using it to conserve as much power as possible, some times it doesn't see the second hard drive unless I either pause in the POST or reboot again, but I haven't seen this issue since formatting to 11.04.

Cheers,

Nasair

---

### Post by NormanFLinux on 2011-05-02
More of those freezes... lots of reports on them on 11.04. This isn't a good sign.

---

### Post by Nasair on 2011-05-02
> **NormanFLinux said:**
> More of those freezes... lots of reports on them on 11.04. This isn't a good sign.

That is a troubling sign indeed.

---

### Post by K_45 on 2011-05-02
Can you run some basic tests to prod your hardware and ensure its running properly?

First, a Memtest iso:

[http://www.memtest.org/#downiso](http://www.memtest.org/#downiso)

Burn to CD and boot like a LiveCD. Leave it running for a few hours

Next, an HDD diagnostic:

[http://www.hitachigst.com/support/downloads/#DFT](http://www.hitachigst.com/support/downloads/#DFT)

You want the CD image, same process as memtest.

If there any freezes, errors, or crashes, post as then it could be hardware related. I've never seen a kernel crash in any distro (until now). Radeon is also coming up, so if these pass, it may be your GPU.

---

### Post by Nasair on 2011-05-02
I still need to do the diagnostics, but I did in fact come home to a frozen computer again see the below pics...what I did find interesting is that it seems to be exactly the same issue. Will run Diagnostics tonight while sleeping.

[IMG]http://i1129.photobucket.com/albums/m502/Nasairk/IMG_20110502_192420.jpg[/IMG]

&

[IMG]http://i1129.photobucket.com/albums/m502/Nasairk/IMG_20110502_192432.jpg[/IMG]

&

[IMG]http://i1129.photobucket.com/albums/m502/Nasairk/IMG_20110502_192443.jpg[/IMG]

---

### Post by K_45 on 2011-05-02
You may have to get up to run the second .iso - its two separate tests. Run the first for 2 or 3 hours, the second will depend on what tests you choose.

---

### Post by Nasair on 2011-05-03
So those two tests on RAM and Hard Drives turned up nothing. Ideas? I still think it has something to do with Xubuntu its self and maybe a hardware conflict? But Something to do with Xubuntu because I didn't have these problems until after an update and then the issue stuck around even after a format to 11.04...but I'm gonna let it run by its self tonight to see if an issue still...and if it is maybe try unplugging some things? :confused: IDK :(

---

### Post by Nasair on 2011-05-03
Just saw a swarm of updates...here is hoping they help.

---

### Post by Nasair on 2011-05-03
> **K_45 said:**
> You may have to get up to run the second .iso - its two separate tests. Run the first for 2 or 3 hours, the second will depend on what tests you choose.

Not sure if some how running the diagnostics or uninstalling GMusicBrowser and installing Banshee helped? (Figure highly unlikely)
Or if the updates helpped from last night but I'm not seeing the freeze up issue this morning (left actual programs running like I usually do), will have to monitor it and am testing it more now...so I don't want to be premature but I think this is solved.

---

### Post by K_45 on 2011-05-03
The diagnostics passed with no errors? Probably not hardware then.

---

### Post by Nasair on 2011-05-03
> **K_45 said:**
> The diagnostics passed with no errors? Probably not hardware then.

Correct no errors, and I did a full test on both hard drives and let the memtest run for about 4 passes before stopping.

---

### Post by K_45 on 2011-05-03
Did Memtest stop because of errors or did you stop it?

---

### Post by Nasair on 2011-05-03
I stopped it, after a few hours but checked and it said 0 errors and had completed 3 passes while about 70% though the 4th.

---

### Post by K_45 on 2011-05-03
Hardware looks good then. You could stress test the GPU, but I'd wait and see if there are any further crashes. Updates may have helped too.

---

### Post by Nasair on 2011-05-03
> **K_45 said:**
> Hardware looks good then. You could stress test the GPU, but I'd wait and see if there are any further crashes.

I thought about it last night but agree with you on waiting for more crashes. Didn't crash last night and hoping it is still good when I come home to it today. :)

---

### Post by Nasair on 2011-05-04
Poop on a stick crashed while I was out again, like the previous crashes almost identical with only a few subtle differences but still in the kernel. :confused:
How do I stress test my GPU? ...but I think looking at my hardware is a dead end but I'll do it to eliminate it as an issue. The only other things I want to try is an older version (last resort) &/Or if the system will crash after a boot if untouched.

---

### Post by Nasair on 2011-05-04
New update, I found playing Portal & CounterStrike for a while (finally got them working as well) had no issues and I turned the video settings to the max so I think that should count as a GPU test.

I did notice last night My system froze twice while I was using it, but no errors. It seemed to happen in the exact same situation: I was viewing multiple videos from my extra hard drive. I tried a SMART test on it but it crashed with the same type of errors I originally posted (saw it in the morning). I think it might actually be the hard drive after all. I've unplugged it, and will let my computer run for the day again.

:popcorn: Will just have to sit back and wait again.

---

### Post by Nasair on 2011-05-16
Haven't had the Kernel error after several updates, but do see lockups, mostly when playing videos (usually multiple), but no obvious root cause as I've tried different hardware, well except my CPU and ram, but since the kernel issue isn't happening, I'll consider this "solved"

---

