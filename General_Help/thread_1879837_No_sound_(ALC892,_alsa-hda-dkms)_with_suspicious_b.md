---
title: "No sound (ALC892, alsa-hda-dkms) with suspicious boot error"
date: 2011-11-12
forum: General Help
---

### Post by quequotion on 2011-11-12
Something, somewhere in the boot process is putting out this:

"egrep: Unmatched ( or \("

I suspect this is related to having no sound output, although it was working this morning (with alsa-hda-dkms module from ppa because i have a realtek hda card and the kernel drivers are broken). I don't know if it's related to gnome-system-log having no logs, but I have that problem too. Also, when I get this message, lightdm fails to load. Lightdm fails to load pretty often actually, both with and without cause.

Allow me to reiterate: the boot error and lightdm not starting is an intermittent problem.

Oh, about sound, in pavumeter pulseaudio shows sound going through the card as if everything was working. Increasing the volume increases the levels shown, just as muting the sound blanks them out, but in any case no sound of any kind is coming out of the speakers.

I'll clarify this as well: no sound coming out of the speakers while ubuntu thinks the soundcard works was a constant problem and also the main problem.

I thought the boot message had something to do with it. Having reconfigured numerous packages and resolved the issue, I will never really know.

---

### Post by Matti L on 2011-11-12
For that LightDM problem check this thread and post #7 might be the answer:
[Upg from 11.04 to 11.10 - LightDM fails to load]("http://ubuntuforums.org/showthread.php?t=1859951")

---

### Post by techvish81 on 2011-11-12
> **quequotion said:**
> No one's replied to a post of mine for quite a while now.

I'm starting to feel invisible.

Every day Ubuntu gives me new grief.

Today, something, somewhere in the boot process is putting out this:

"egrep: Unmatched ( or \("

I suspect this is related to having no sound output, although it was working this morning (with alsa-hda-dkms module from ppa because i have a realtek hda card and the kernel drivers are broken). I don't know if it's related to gnome-system-log having no logs, but I have that problem too. Also, when I get this message, lightdm fails to load. Lightdm fails to load pretty often actually, both with and without cause.

Oh, about sound, in pavumeter pulseaudio shows sound going through the card as if everything was working. Increasing the volume increases the levels shown, just as muting the sound blanks them out, but in any case no sound of any kind is coming out of the speakers.

I need help. I really need help. **Please** someone help me.


u can try a different version, i mean 11.10 or the 10.04 lts, if your hardware is not compatible with the version u have.
or simply try and reinstall the one you have, tweaking too much can cause system collapse, so try to keep what is default if not much necessary. to keep it stable. and always do a clean install, u will be saved from many problems.

don't get me wrong, u said that everyday u face several problems, so in my opinion it is better to backup data and do a clean install then to solve each problem, everyday..
good luck

---

### Post by quequotion on 2011-11-12
> **techvish81 said:**
> u can try a different version, i mean 11.10 or the 10.04 lts, if your hardware is not compatible with the version u have.
or simply try and reinstall the one you have, tweaking too much can cause system collapse, so try to keep what is default if not much necessary. to keep it stable. and always do a clean install, u will be saved from many problems.

don't get me wrong, u said that everyday u face several problems, so in my opinion it is better to backup data and do a clean install then to solve each problem, everyday..
good luck


*i did that less than a week ago*

This is not the way things should be done in linux.
Especially it is not the way things should be done in a Debian based linux.

I can't understand why Ubuntu upgrades break everything so completely.
I mean, not that I'm fully fluent in bash or anything, but it's not like I'm a complete noob who has no idea what's happening.

I don't understand why upgrading ubuntu causes so many dependency chains to be broken and why so many programs can't figure out what to do with old vs new configuration file conflicts or why installing one kernel breaks all the modules of another kernel. Those things shouldn't happen. But that's not the point of this post.

The point of this post is to get help fixing my (re)broken sound system and a solve a boot-error mystery.

Any ideas how I can find out what's going wrong at boot?

---

### Post by quequotion on 2011-11-12
After dpkg-reconfigure of a whole lot of packages (everything related to the kernel and init) lightdm seems to be starting at the right time and I haven't seen the "egrep: Unmatched ( or \(" for a few boots now (not to say I think that problem is dealt with, but it's out of the way).

I still have no audio.

This was working this morning.

I installed the alsa-hda-dkms package and sound started working.

Now it will not.

5 hours ago there was an update to also-hda-dkms. I have tried the older version since then, neither work.

When audio was still working, I installed a lowlatency kernel (3.x) which worked except for loading nvidia. Since that wasn't my taste, I purged the lowlatency kernel.

After rebooting I noticed that sound was gone.

The kernel module is loaded properly.

Pulseaudio reports sound going through the card.

Nothing comes out of the speakers.

I purged pusleaudio and some alsa packages and reinstalled.

Still no sound.

What is going on?

If there is some log info or some command output that would help you understand my problem ***please tell me***.

I have looked for problems everywhere I know where to look and there's simply nothing wrong except the speakers make no sound.

---

### Post by techvish81 on 2011-11-12
have you got multimedia systems selector installed? if not, u can install it and see what it shows in audio, if it is set to autodetect, u can change and test your speakers.

---

### Post by quequotion on 2011-11-12
> **techvish81 said:**
> have you got multimedia systems selector installed? if not, u can install it and see what it shows in audio, if it is set to autodetect, u can change and test your speakers.

Installed, purged, and reinstalled.

Still no audio, although both ALSA and Pulseaudio recognise my sound cards.

I have three: a buggy emu10k1 which I plan to remove soon, an HDMI port on an nVidia card (can't use, no HDMI system), and a Realtek ALC892 (hda) which I want to use.

Do you have any idea about the error I'm getting on boot?
I that that's an important place to start. Is there some way to log the boot process? Some way to get egrep to tell me WHERE it encountered an unmatched parenthesis?

---

### Post by HermanAB on 2011-11-13
Howdy,

Something to think about:
Linux is only as stable as you make it.  Once your system is working, you have to stop doing updates (even security updates), since at that point, an update can only make it worse, not better.

By the looks of it, you are continuously experimenting on your machine, so you should expect to have problems.  If you don't want problems - then you got to stop experimenting - you got to make up your mind about that.

---

### Post by Cyclane on 2011-11-13
Well, I don't think it's right to advise to stop updating (especially security updates)...
Just don't update if you're in desperate need of your computer in the next few hours.

Updates sometimes do the most retarded things though, last week an update blacklisted my graphics drivers in /etc/modprobe.d/*
The longer you use linux the more adept you'll get at fixing these problems.


###EDIT
I'm sorry, back on topic.

I haven't read your whole thread yet, but I will return later to do that.

---

### Post by Cyclane on 2011-11-13
Have you tried to produce sound with speaker-test? (see man pages on how to do this, it's in the description section)

---

### Post by techvish81 on 2011-11-13
u can try to remove the drivers that u have installed manually, and try to run the system with default settings. and please give proper details, so that somebody can help you.. your system specifications, version of ubuntu ., details of how u installed it, i mean upgrade/ clean install, what drivers u installed afterwards,  etc....

---

### Post by mörgæs on 2011-11-13
If you feel that you don't get answers, maybe your question is wrong. Please read this:

[http://ubuntuforums.org/showthread.php?t=1422475](http://ubuntuforums.org/showthread.php?t=1422475)

Also a precise heading describing you problem would help. The present one does not say anything, so people simply don't click on it.

---

### Post by Zill on 2011-11-13
> **HermanAB said:**
> ...Linux is only as stable as you make it.  Once your system is working, you have to stop doing updates (even security updates), since at that point, an update can only make it worse, not better...
Excellent advice - too many users create problems for themselves by ignoring the old adage "if it ain't broke, don't fix it"!
> **mörgæs said:**
> ...Also a precise heading describing you problem would help. The present one does not say anything, so people simply don't click on it.
Again, great advice.

---

### Post by mörgæs on 2011-11-13
I missed this one before:

> **HermanAB said:**
> 
Linux is only as stable as you make it.  Once your system is working, you have to stop doing updates (even security updates), since at that point, an update can only make it worse, not better.


That is not good advice. 

There is no such thing as 'once your system is working'. It might be running without crashing, but that does not mean that the security is as strong as it can be.

An operative system is always flawed, and one should expect to find security bugs scattered around. The aim is to lower the number of bugs, and applying updates is absolutely necessary.

Updates should be installed as soon as possible, but best is to be some months late with upgrades.

---

### Post by quequotion on 2011-11-13
> **HermanAB said:**
> Howdy,

Something to think about:
Linux is only as stable as you make it.  Once your system is working, you have to stop doing updates (even security updates), since at that point, an update can only make it worse, not better.

By the looks of it, you are continuously experimenting on your machine, so you should expect to have problems.  If you don't want problems - then you got to stop experimenting - you got to make up your mind about that.

I understand what you're saying, but you've misinterpreted me a little.

I'm not experimenting on my machine; I'm trying to make it work within the standard I've set for it.

That standard is based on what I know the hardware is capable of and what I know GNU/Linux is capable of (based on continuous research) allowing for a reasonable gap.

Unfortunately there is often a gap between that standard and what *Ubuntu* is capable of, which is why I end up using various unsupported PPAs or compiling packages from source to get the full benefit of the linux community.

I don't mean to criticize Ubuntu. I like Ubuntu. With the exception of Canonical treating us like lab rats, as an operating system and a community it's pretty good. I would like to see Ubuntu have the functionality and stability of some other distributions out there, but Ubuntu (usually) happens to have a nice compromise between the two. It also has a name that people have actually heard of, which is very important when trying to impress people at parties. I hope that name can start sounding a little better with the next LTS release.

---

### Post by quequotion on 2011-11-13
> **mörgæs said:**
> If you feel that you don't get answers, maybe your question is wrong. Please read this:

[http://ubuntuforums.org/showthread.php?t=1422475](http://ubuntuforums.org/showthread.php?t=1422475)

Also a precise heading describing you problem would help. The present one does not say anything, so people simply don't click on it.

There are more replies in this thread than any other thread I have ever started.

If you beg and plead, people respond.

Most of my other threads are more direct and to the point and completely ignored.

Why?

---

### Post by quequotion on 2011-11-13
> **techvish81 said:**
> try to run the system with default settings

This is a much better idea than another full re-install (It takes days to get things set up how I need them after a fresh install. Un/fortunately hacking is *not* my life, just my hobby.)

To achieve this, the only sure method is **dpkg-reconfigure -a**

Unfortunately this is broken.

[Fortunately I fixed it]("http://ubuntuforums.org/showthread.php?p=11453698#post11453698"), sort of.

After reconfiguring nearly all the packages on my system (but perhaps most importantly cron, pulseaudio, and alsa) I now have functional audio.

I promise never to try to make it better again. (The alsa-hda-dkms driver works better than the kernel driver, which doesn't work at all, but still has some problems, especially high latency and low volume.)

I still have no idea exactly what was wrong or where.

---

### Post by quequotion on 2011-11-13
> **Cyclane said:**
> Have you tried to produce sound with speaker-test? (see man pages on how to do this, it's in the description section)

Yes.

---

### Post by mörgæs on 2011-11-13
> **quequotion said:**
> 
If you beg and plead, people respond.


I let it pass only this single time. Don't repeat - next time I will edit. 

Please stick to the facts and to the guidelines in the thread I posted.

---

### Post by mörgæs on 2011-11-13
> **quequotion said:**
> If you beg and plead, people respond.


Please don't repeat this. I let it pass this single time, but that does not mean that it is encouraged. 

Now I have edited the begging out, and it will be edited next time as well. 

Please stick to the facts and to the guidelines in the thread I posted.

---

### Post by Zill on 2011-11-13
> **mörgæs said:**
> ...There is no such thing as 'once your system is working'. It might be running without crashing, but that does not mean that the security is as strong as it can be.

An operative system is always flawed, and one should expect to find security bugs scattered around. The aim is to lower the number of bugs, and applying updates is absolutely necessary...
I suggest that there is no actual right or wrong answer to the question of applying updates as this really depends on the importance of the machine(s) in question.

If this is a "mission-critical" system then, once the system has proved reliable, IMHO it is not absolutely essential to have *all* the latest security updates applied unless the machine is particularly vulnerable to attack.  Yes, this is a risk but it is highly unlikely that the machine would be compromised by an attack that could only be avoided by using the very latest patches.  OTOH, a buggy update could potentially damage functionality of this (important) system.

If the system is not "mission critical" and the user is not too concerned by the occasional crash then regular updating is fine and will not *generally* cause too many problems.

In both cases the golden rule is, of course, to always ensure that backups are up to date so that if/when the worst does happen, it is a relatively quick job to reinstall the system and restore the latest backed-up data.

---

### Post by quequotion on 2011-11-13
> **mörgæs said:**
> Please don't repeat this. I let it pass this single time, but that does not mean that it is encouraged. 

Now I have edited the begging out, and it will be edited next time as well. 

Please stick to the facts and to the guidelines in the thread I posted.

I'm not saying it's the right way to do things or even the way I want to do things. No one likes to beg.

I think it's important to point out that following the guidelines far from guarantees any response.

Personally I think this reflects a decline in the community morale, where as during the Intrepid cycle discussions got rolling right away and problems were solved in days--lately a lot of threads (most of my threads at least) are just left out in the cold.

Bonus: Could you please not give my thread an arbitrary and irrelevant title?

I do not want to mark this thread [solved] and have google index it with a title that will never be found by anyone with the same problem.

I had a problem with no audio coming out of a card that Ubuntu reported as working accompanied by a suspicious boot error which was resolved by reconfiguring my system.

How about: "No sound (ALC892, alsa-hda-dkms) with suspicious boot error."

---

### Post by mörgæs on 2011-11-14
> **quequotion said:**
> Could you please not give my thread an arbitrary and irrelevant title?


I was trying to correct an arbitrary and irrelevant title.

Done.

---

### Post by quequotion on 2011-11-14
> **mörgæs said:**
> I was trying to correct an arbitrary and irrelevant title.

Agreed. Thank you for your help.

Thanks to everyone in the thread!

Hopefully my system will be running more smoothly for a while and I will be less distraught...

---

