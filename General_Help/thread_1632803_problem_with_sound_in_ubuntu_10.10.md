---
title: "problem with sound in ubuntu 10.10"
date: 2010-11-28
forum: General Help
---

### Post by majed_19845 on 2010-11-28
hi all

plz help me to solve my problem
actually the sound works when i install ubuntu in virtalbox but if i install ubuntu as a main operating system in my pc the sound didn't work

plz help me as soon as

sorry about my englsih

best regards,
Majed[EMAIL="majed_19845@hotmail.com"]
[/EMAIL]

---

### Post by sikander3786 on 2010-11-28
Welcome to the forums :-)

Please post your hardware specs so we at least know the sound card which isn't working well with Ubuntu :-)

And please remove your e-mail address from the above post or you are opening doors to spam bots....

---

### Post by majed_19845 on 2010-11-28
thxx [sikander3786]("http://ubuntuforums.org/member.php?u=806649") 4 your reply,
i removed my email

and plz see this :

matrix@matrix-GF7050VT-M5:~$ _[COLOR=Red]lspci[/COLOR]_
00:00.0 Host bridge: nVidia Corporation Device 07c3 (rev a2)
00:00.1 RAM memory: nVidia Corporation nForce 630i memory controller (rev a2)
00:01.0 RAM memory: nVidia Corporation nForce 630i memory controller (rev a1)
00:01.1 RAM memory: nVidia Corporation nForce 630i memory controller (rev a1)
00:01.2 RAM memory: nVidia Corporation nForce 630i memory controller (rev a1)
00:01.3 RAM memory: nVidia Corporation nForce 630i memory controller (rev a1)
00:01.4 RAM memory: nVidia Corporation nForce 630i memory controller (rev a1)
00:01.5 RAM memory: nVidia Corporation nForce 630i memory controller (rev a1)
00:01.6 RAM memory: nVidia Corporation nForce 630i memory controller (rev a1)
00:02.0 RAM memory: nVidia Corporation nForce 630i memory controller (rev a1)
00:03.0 ISA bridge: nVidia Corporation MCP73 LPC Bridge (rev a2)
00:03.1 SMBus: nVidia Corporation MCP73 SMBus (rev a1)
00:03.2 RAM memory: nVidia Corporation MCP73 Memory Controller (rev a1)
00:03.4 RAM memory: nVidia Corporation MCP73 Memory Controller (rev a1)
00:04.0 USB Controller: nVidia Corporation GeForce 7100/nForce 630i USB (rev a1)
00:04.1 USB Controller: nVidia Corporation MCP73 [nForce 630i] USB 2.0 Controller (EHCI) (rev a1)
00:08.0 IDE interface: nVidia Corporation MCP73 IDE (rev a1)
00:09.0 Audio device: nVidia Corporation MCP73 [COLOR=red]_High Definition Audio_[/COLOR] (rev a1)
00:0a.0 PCI bridge: nVidia Corporation MCP73 PCI Express bridge (rev a1)
00:0b.0 PCI bridge: nVidia Corporation MCP73 PCI Express bridge (rev a1)
00:0c.0 PCI bridge: nVidia Corporation MCP73 PCI Express bridge (rev a1)
00:0d.0 PCI bridge: nVidia Corporation MCP73 PCI Express bridge (rev a1)
00:0e.0 IDE interface: nVidia Corporation MCP73 IDE (rev a2)
00:0f.0 Ethernet controller: nVidia Corporation MCP73 Ethernet (rev a2)
00:10.0 VGA compatible controller: nVidia Corporation C73 [GeForce 7050 / nForce 610i] (rev a2)
matrix@matrix-GF7050VT-M5:~$

---

### Post by sikander3786 on 2010-11-28
Post the output of this one also.

```
aplay -l
```

---

### Post by majed_19845 on 2010-11-28
thxx [sikander3786]("http://ubuntuforums.org/member.php?u=806649") 4 your speed

> matrix@matrix-GF7050VT-M5:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 0: VT1708B Analog [VT1708B Analog]
  Subdevices: 2/2
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
card 0: NVidia [HDA NVidia], device 1: VT1708B Digital [VT1708B Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
matrix@matrix-GF7050VT-M5:~$ 


---

### Post by majed_19845 on 2010-11-28
my friend [sikander3786]("http://ubuntuforums.org/member.php?u=806649"),

if you wanna enter to my pc i downloaded teamviewer

---

### Post by sikander3786 on 2010-11-28
No. I will advise not to give access to your computer to any strangers, not from the forums at least :-)

From the output above, Linux does detect your sound card properly.

Can you see the Volume Icon in notification area? Can you unmute it?

---

### Post by majed_19845 on 2010-11-28
thxx 4 your advise, but i trust you :)

> Can you see the Volume Icon in notification area? Can you unmute it?
yes i see it and its unmute

---

### Post by majed_19845 on 2010-11-28
i know its a strange problem, but i made a stupid stage by tried fix this problem by reinstall ubuntu, but the problem still there

---

### Post by sikander3786 on 2010-11-28
From Terminal,

```
alsamixer
```

And see if that has any effect.

---

### Post by majed_19845 on 2010-11-28
plz see the screenshot , cause I'm new 4 using linux :


[IMG]http://img219.imageshack.us/img219/8057/alsamixerx.png[/IMG]

---

### Post by majed_19845 on 2010-11-28
plz check this :

[IMG]http://img152.imageshack.us/img152/2938/newa0.png[/IMG]

---

### Post by sikander3786 on 2010-11-28
From what I see, I feel like everything is working fine there.

Might be a time to re-check your speaker/headphone connections/jacks.

I don't see any problem with Alsa.

---

### Post by majed_19845 on 2010-11-28
thxx 4 your trying to help me, and i know its a strange problem,
but if i download a windows xp then download the same ubuntu from the same cd the sound works fine
but i do not wanna use windows, i love ubuntu and hate windows
i wnaa ubuntu the main OS in my PC
plz help me

you can enter to my PC and see the problem & i think you can help me

and thxx again 4 everything

---

### Post by sikander3786 on 2010-11-28
> you can enter to my PC and see the problem & i think you can help me

I know from your command outputs nearly everything I needed to know :-)

You can continue to wait and some other mate might jump in and might be able to spot the issue here.

I am stumped by that one. Seems ok...

---

### Post by majed_19845 on 2010-11-28
ok my friend sikander3786 no problem
and thxx very very much 4 your trying to help me
and pleased to meet you

thxx again
and i am waiting 4 any help

---

