---
title: "How do i disable/remove esd and dmix?"
date: 2006-05-01
forum: General Help
---

### Post by Intangir on 2006-05-01
im using Ubuntu Dapper drake flight 5 with updates

i have a creativelabs SBLive! and it supports playing more than one output by default, and it worked fine on my gentoo install without alsa's dmix and without esd, all my sound worked fine with multiple outputs at once (i mostly used alsa for everything)

on ubuntu i have noticed several weird sound issues:
1: sometimes i have sound on startup, sometimes i dont..

2: if i play music on xmms (which is using alsa) and then try to play music on cedega (which i have to use oss on now, on ubuntu, more on this later) the sound in cedega doesnt work.. whats more if i close the xmms app and nothing else is using sound, cedega still wont play sound, i have to reboot and run cedega FIRST and then it plays fine, after its running i can start xmms and it plays sound fine also.. very unusual..

3: i cant use alsa on cedega. on my gentoo install i set the hardware identifiers ("hw:1,0") in my config and it worked fine, also xmms was setup like this, oss also worked fine on teamspeak which used /dev/dsp1 they both worked fine together

on ubuntu i have to set xmms to 'default' nothing else works for alsa, and for cedega i have to set it to use oss. when i try to use hardware id it doesnt work says it cant open it, im guessing its cause something like esd already has it? i dont know.. cedega only seems to work with the hardware strings and doesnt understand stuff like 'default' for some reason, i think it somehow doesnt recognize anything in .asoundrc or any other alsa config that gives names to devices

4: sound in flash is delayed, watching movies in a flash player gets futher and futher out of sync, this wasnt the case on my gentoo install


i think alot of this probably has to do with either esd or alsa somehow hogging the soundcard

i tried to uninstall esd but if you try that it wants to uninstall TONS of other applications which it thinks depend on it.. but dont depend on it..

---

### Post by Intangir on 2006-05-01
^

---

### Post by Intangir on 2006-05-02
still having this problem

i have enable software mixing checked off, in the sound settings

---

