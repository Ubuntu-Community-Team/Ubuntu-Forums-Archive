---
title: "I think the update manager froze..."
date: 2012-08-15
forum: General Help
---

### Post by Scozzar on 2012-08-15
It froze.  It's been on the same thing for about 10 minutes now.  I don't know what to do!  This is what I'm stuck with...

EDIT:  I can type whatever where the cursor is...It's not supposed to be like that.

---

### Post by irv on 2012-08-15
During updates I have seen something like this, but I just waited it out and it continued again and completed.

---

### Post by Scozzar on 2012-08-15
I get the following when I run "ps aux | grep http"
```
(name)     3018  0.0  0.0 382076  5328 ?        Sl   15:13   0:00 /usr/lib/gvfs/gvfsd-http --spawner :1.6 /org/gtk/gvfs/exec_spaw/2
(name)     4557  0.0  0.0  13596   936 pts/6    S+   15:45   0:00 grep --color=auto http

```

---

### Post by irv on 2012-08-15
Open a terminal and run
```
top
```
to see what is happening.
[ATTACH]222757[/ATTACH]

---

### Post by Scozzar on 2012-08-15
Here ya go.

---

### Post by Scozzar on 2012-08-15
So I ended up restarting and it totally screwed up the update manager.  So do I just do a reinstall?

EDIT:  I logged out in the middle of a "partial upgrade" and it works now....I'm still thinking of a reinstall, but if it works, it works lol

---

### Post by irv on 2012-08-16
I am sorry, I had to leave last night and didn't get back with you. I see from your screen shot that you are using Unity 2D. What are you running Ubuntu on? (Your hardware). Does it have low specs that you are running in 2D?
If this was a new install not long ago, you might be better off doing a fresh install. It seem I have been installing a couple times a month lately. Day before yesterday I installed Black Opal which is Ubuntu 12.04 with some extra effects and apps. It ran a little slow so I had to turn off some of the effects.

---

### Post by bogan on 2012-08-17
Hi!, **Scozzar**,

I had a similar hang-up with Update Manager, yesterday, including a long delay whist trying to download the Adobe Flash update. Eventually I had to close it.

On re-running Update Manager I got offered a partial update, which I refused.

I re-booted to recovery, ran fsck to set Read/Write and went to the Root shell:```
apt-get update # then following error prompts:
apt-get -f install
dpkg --configure -a # this effectively, did a full update
apt-get upgrade
```And after a re-boot everything was restored to normal and fully updated; though I had to reinstall the nvidia driver for the new kernal.

Chao!,** bogan.**

---

### Post by Scozzar on 2012-08-18
Okay, so I am going to do a fresh install.  Everything works fine, but just to be safe.  I don't want it to crash when I am in college and lose valuable data.  I'm gonna be majoring in Computer Engineering so we do a lot of programming through Linux...

So plug in the LiveCD, go to Gparted and just delete the partitions?

---

### Post by bogan on 2012-08-19
Hi!, **Scozzar,**

Yes, but I would format the relevant partitions, rather than 'delete' them.

If you have a separate Home partition there is no need to clean that, if not I would create one in the new installation: it can save disasterous consequences of a possible future crash.

Otherwise back-up any important files, preferably to an external drive or USB.

**@All**,  - [COLOR=Blue]Re UM wanting to remove 'language-support-en':[/COLOR]

On running Update Manager again today,18/08/12, the two Netscaqpe libraries were again listed, this time 'Ticked'. They installed correctly, without problems.

Strangely, on my other 12.04, running a direct install of the pae kernal, equally updated, on the same computer, UM only offered the libnspr4 file. Synaptic showed both installed, as well as listing the Debug versions, but the others were already updated to 4.8.9-1ubuntu2.3.

For those who can understand it, the UM Change description is as follows: [Currently installed at this time: 4.8.9-1ubuntu2.2:] > Version 4.8.9-1ubuntu2.3: 

  * language-support-LANG was still around in 11.04 so the previous change
    is requiring a dist-upgrade for any user who upgraded from 11.04 to 11.10
    and then to 12.04, instead of being limited to machines that were
    originally installed with 9.04 as was planned.
    Removing language-support-LANG from the Breaks, which should resolve the
    issue for these users while still removing language-support-translations
    on systems. (LP: #1036794)**Update: 19/08/12.**
 Update manager still showed libnspr4 as an available update, despite having updated it to the same version 2 days ago; but Synaptic showed libnspr4-0d updated but no longer installed.

So there is clearly something wrong with the system somewhere.

Chao!, **bogan**.

---

### Post by Scozzar on 2012-08-19
Too late!  I did a fresh install yesterday morning :confused:

---

### Post by irv on 2012-08-19
> **Scozzar said:**
> Too late!  I did a fresh install yesterday morning :confused:

How did everything go with the fresh install?
If everything is running great why not mark this thread solved.

---

### Post by bogan on 2012-08-19
Hi!,** Scozzar,**

With the fresh install, are you still getting the 'Broken Pipe' messages??

Chao!,** bogan**.

---

