---
title: "crtl + alt + f9 killed my system?"
date: 2011-03-12
forum: General Help
---

### Post by steaksauce on 2011-03-12
So I pressed crtl + alt + f9 on my system and it went to a blank screen. I tried to get it to go back but it wouldn't so I rebooted. Now no matter which kernel I select from the GRUB, even in recovery mode I get the same blank screen and after a few minutes it says
```
41.665010] Kernel panic - not syncing: Attempted to kill init!
``` followed by a long list of other stuff.

I tried to use the "Rescue a broken system" option on my live cd but as far as I can tell its just a text installer and I can't fix this problem with it. Anyone have any ideas? :(

---

### Post by WlaadDyaab on 2011-03-12
I done the same as you Lol. I know it's stupid to do, but that way I found out how to get back my screen after it rebooted

Here's what I done:

-I pressed Ctrl+Alt+F9
-Screen went black
-I tried pressing different buttons
-I pressed Ctrl+Alt+delete

Then my Laptop rebooted and started normally again

I use Ubuntu 10.10 - I don't know if that helps

---

### Post by steaksauce on 2011-03-12
I press crtl + alt + delete 600 times and the only thing I can do is a hard shutdown -_-

---

### Post by WlaadDyaab on 2011-03-12
[http://ubuntuforums.org/archive/index.php/t-903007.html](http://ubuntuforums.org/archive/index.php/t-903007.html)

I'm also reading this. I hope you solve your problem, I'm also trying to assist you by doing more research :)

---

### Post by WlaadDyaab on 2011-03-12
A user on that forum called "ubuntu" is saying:

"If you press Ctrl-Alt-F9 and get the blank screen, it was because no X session was running there. You can press Ctrl-Alt-F7 to get back to your regular X session."

Does Ctrl+Alt+F7 work?

---

### Post by WlaadDyaab on 2011-03-12
[http://ubuntuforums.org/showthread.php?p=6316851](http://ubuntuforums.org/showthread.php?p=6316851)

This user "Zorael" is saying that F7 alone worked for him/her

---

### Post by steaksauce on 2011-03-12
I stumbled upon that before posting--it didn't work. The only thing I can do from this screen is a hard shutdown. From my understanding its a kernel problem

---

### Post by WlaadDyaab on 2011-03-12
[http://www.thinkwiki.org/wiki/Problem_with_display_remaining_black_after_resume](http://www.thinkwiki.org/wiki/Problem_with_display_remaining_black_after_resume)

Could you try looking at the "Solutions" section, see if anything works from it?

---

### Post by WlaadDyaab on 2011-03-12
[http://ubuntulinuxtipstricks.blogspot.com/2009/01/since-we-all-know-x-is-nowhere-near.html](http://ubuntulinuxtipstricks.blogspot.com/2009/01/since-we-all-know-x-is-nowhere-near.html)

This one?

---

### Post by steaksauce on 2011-03-12
```

40.915957 Kernel panic - not syncing: Attempted to kill init!
40.916028 Pid: w, comm: init Not tained 2.635-22-generic #35-Ubuntu
40.916075 Call Trace:

```
It goes on for 15 more lines

---

### Post by steaksauce on 2011-03-12
> **WlaadDyaab said:**
> [http://ubuntulinuxtipstricks.blogspot.com/2009/01/since-we-all-know-x-is-nowhere-near.html](http://ubuntulinuxtipstricks.blogspot.com/2009/01/since-we-all-know-x-is-nowhere-near.html)

This one?

As far as I can tell, that article has nothing to do with my problem, sorry :/

---

### Post by WlaadDyaab on 2011-03-12
[http://www.youtube.com/results?search_query=kernel+problems+on+ubuntu&aq=f](http://www.youtube.com/results?search_query=kernel+problems+on+ubuntu&aq=f)

I normally learn from YouTube, I just typed "kernel problems on ubuntu", I hope there's something useful there

---

### Post by WlaadDyaab on 2011-03-12
You don't have to say sorry to me. I should say that to you: sorry :)

I was in a hurry so I never noticed. But check out the YouTube link I posted before this one

---

### Post by steaksauce on 2011-03-12
Right now I'm using my phone, but I did a little searching and one fix on another site suggests going down to 9.10 using a recovery shell. I'll look into it tomorrow after I can finally go to sleep. But I'm still open to suggestions

---

### Post by WlaadDyaab on 2011-03-12
If you're not trying to back up, or recover your files from the current version you're using that has this problem. Why not do the easiest thing: insert the ISO CD and start from the beginning?

---

### Post by steaksauce on 2011-03-12
> **WlaadDyaab said:**
> If you're not trying to back up, or recover your files from the current version you're using that has this problem. Why not do the easiest thing: insert the ISO CD and start from the beginning?

Too easy, that's what I have to do with most of my installs for whatever reason. I want to learn something from this xD

---

### Post by sandyd on 2011-03-12
a) have you been partitioning your computer lately?
b) if you did, I hope you didn't use partition magic.
c) boot up from a livecd and check the contents of the partition, it could be corrupted and/or missing some system folder such as /dev , or /boot or something else due to the fact that you hard-shutof your computer

---

### Post by steaksauce on 2011-03-12
No I haven't and the hdd reads fine I pressed crtl + alt + f9 and that's it.

---

### Post by sandyd on 2011-03-12
> **steaksauce said:**
> No I haven't and the hdd reads fine I pressed crtl + alt + f9 and that's it.
so everything (i.e., the /boot /dev /lib) folder is intact? (as in, there should be files in it)

---

### Post by steaksauce on 2011-03-12
> **sandyd said:**
> so everything (i.e., the /boot /dev /lib) folder is intact? (as in, there should be files in it)

Yeah, I got the idea to use the live cd and copy the files from the live cd to the folder but its not working. Since I need root privileges I used the command ```
sudo cp (folder name) /media/(hdd path)
``` but then it keeps saying ```
(folder name) omitted 
```

---

### Post by steaksauce on 2011-03-16
I did a fresh install and found the problem:
it's an update. 

All I did to my fresh install before rebooting was run the updates through the update manager and i got the same errors.
I did another fresh install, did the same thing, with the same result.
I'm on my third fresh install and I'm going to do the updates one by one until I find the one causing my problems. It'll be a long task I'm sure XD

---

### Post by steaksauce on 2011-03-16
Okay, I have installed of the the updates except for everything that involves the kernel and so far so good.

One kernel package seems suspicious enough to be my problem, but I'm not for sure:
the update is "Complete Generic Linux Kernel"
FYI: I'm running and Intel dual core processor.

In the description it says:
> 
  * LBM generic-pae packages are only built for i386
    - LP: #720139
  * LBM server packages are only built for amd64
    - LP: #720139


The file size is 5KB, and there is another update with this name that seems exactly the same as far as the changes and description. However, the second one addresses different bug numbers on the LP line but the LBM lines are the same

Also, another package is suspicious:

Linux Kernel Headers for version 2.6.35 on x86/x86_64 (two packages one for -22 and one for -27)
and the Image files for both of those headers.


I'm sure one or all of these is breaking my system, does anyone have any clue which one it could be since I'm running an i386 system? I figured I would ask so I don't have to keep breaking my system until I figure out which one it is

---

