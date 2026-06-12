---
title: "Abiword is driving me nuts"
date: 2010-03-21
forum: General Help
---

### Post by Spaceman9 on 2010-03-21
Every time I try to do anything with Abiword it crashes. I installed everything for it and in versions of Ubuntu before 9.10 it worked fine. How do I get Abiword in Ubuntu 9.10 to stop crashing? Thanks for any help.

---

### Post by darolu on 2010-03-21
Open a terminal (applications - accessories - terminal) and run abiword from there:
```
$ abiword
```
And post the info displayed there, hopefully it will print the error.
You can try re-installing it too I guess.

---

### Post by Spaceman9 on 2010-03-21
Ok, I typed in abiword and got this:

matrix@matrix-desktop:~$ abiword
Assertion 'pthread_setspecific(t->key, userdata) == 0' failed at pulsecore/thread-posix.c:200, function pa_tls_set(). Aborting.
Aborted
matrix@matrix-desktop:~$ 

It looks like it might be a problem with pulsaudio. How do I disable pulsaudio?

---

### Post by darolu on 2010-03-21
Seems to be a bug: [https://bugs.launchpad.net/ubuntu/+source/abiword/+bug/430870](https://bugs.launchpad.net/ubuntu/+source/abiword/+bug/430870)
You may want to post your case at launchpad.

In the mean time, you may try killing pulseaudio with:
```
$ sudo killall pulseaudio
```
If it resist to die, type:
```
$ ps -e
```
and look for "pulseaudio", you will see a number to its left, use it with:
```
$ sudo kill -kill <numericID>
```

---

### Post by Spaceman9 on 2010-03-21
Ok, I tried those commands and and don't seem to be working. I'm going to reboot and see if that helps. May be I should check Synaptic to see if all the stuff for ALSA is installed.

UPDATE: I rebooted and Abiword still crashes every time I click on a menu. I have to eat dinner. Everyones in the dinning room already. I'll have to get back to this later. Thanks very much for the help darolu.

---

### Post by darolu on 2010-03-21
I actually have no idea what pulseaudio has to do with a word processing application, I can't think anything (out of killing pulseaudio) to solve it. It seems that nothing "normal" can be done to fix it in Ubuntu 9.10 right now, but I read this in the Bug report and may help you:
> Abiword 2.8.2 from sid to ubuntu works and does not fall
"Sid" refers to the development-state version of Debian, you can download the package from this link: [http://packages.debian.org/sid/abiword](http://packages.debian.org/sid/abiword)

The weird thing about this bug, is it doesn't affect everyone, I also use Abiword and it works fine in my Karmic, but it crashes on a friend's machine (he now uses OOo) so I suppose it only happens with certain audio drivers (modules), then again I have no idea how pulseaudio and a word processing application are linked.

Consider posting your case (and hardware specs) in the bug report at launchpad, as rmais96 (in the bug report) said this should be solved for karmic users.

---

### Post by Spaceman9 on 2010-03-21
I uninstalled pulsaudio and for the first time I heard a window and button sound. That uninstall though also uninstalled the ubuntu-desktop. At this point I'm not sure that's really a bad thing. I'm typing this in Abiword. It's working now. The downside is when I reboot there won't be an ubuntu-desktop to boot into.  

I installed everything for ALSA I could find in Synaptic so I'll reboot and if I have to I'll reinstall the ubuntu-desktop. 

If it doesn't affect everyone then it might be something about the installation of Ubuntu. I've installed Ubuntu 9.10 3 times in the last 3 months. The first time the panels locked up sometimes when I booted up Ubuntu. Then I replaced Ubuntu with Pardus to try it out. After a month I replaced Pardus with Ubuntu and the problem with the panels didn't happen once. A month later I replace Ubuntu with Mandriva. Then a month later I replaced Mandriva with Ubuntu and the problem with the panels in Ubuntu was back and this problem with Abiword started. 

So may be it's from Ubuntu not installing it's self perfectly or something? I don't know.

---

### Post by Spaceman9 on 2010-03-21
UPDATE: I don't believe this! Everything is working now and I still have a desktop! Ubuntu hasn't played the strartup sound before and this time it played it and the windows and button sounds are working and the panels didn't lock up! 

So, the answer is uninstall pulseaudio. Thanks again for the help darolu.

---

