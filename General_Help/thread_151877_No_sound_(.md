---
title: "No sound :("
date: 2006-03-28
forum: General Help
---

### Post by xXx 0wn3d xXx on 2006-03-28
I am not getting sound on my Gateway MX7118 notebook. I doesn't bother me too much but it would be nice to have.

My lspci
> chris@ubuntu:~$ lspci
0000:00:00.0 Host bridge: ATI Technologies Inc: Unknown device 5950 (rev 01)
0000:00:01.0 PCI bridge: ATI Technologies Inc: Unknown device 5a3f
0000:00:06.0 PCI bridge: ATI Technologies Inc: Unknown device 5a38
0000:00:13.0 USB Controller: ATI Technologies Inc: Unknown device 4374
0000:00:13.1 USB Controller: ATI Technologies Inc: Unknown device 4375
0000:00:13.2 USB Controller: ATI Technologies Inc: Unknown device 4373
0000:00:14.0 SMBus: ATI Technologies Inc: Unknown device 4372 (rev 11)
0000:00:14.1 IDE interface: ATI Technologies Inc: Unknown device 4376
0000:00:14.3 ISA bridge: ATI Technologies Inc: Unknown device 4377
0000:00:14.4 PCI bridge: ATI Technologies Inc: Unknown device 4371
**0000:00:14.5 Multimedia audio controller: ATI Technologies Inc: Unknown device 4370 (rev 02)**
0000:00:14.6 Modem: ATI Technologies Inc: Unknown device 4378 (rev 02)
0000:00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 NorthBridge
0000:00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 NorthBridge
0000:00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 NorthBridge
0000:00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 NorthBridge
0000:01:05.0 VGA compatible controller: ATI Technologies Inc: Unknown device 5955
0000:02:00.0 Ethernet controller: Marvell Technology Group Ltd.: Unknown device 4351 (rev 10)
0000:08:05.0 CardBus bridge: ENE Technology Inc CB1410 Cardbus Controller (rev 01)
0000:08:07.0 Network controller: Broadcom Corporation: Unknown device 4318 (rev 02)
0000:08:0e.0 FireWire (IEEE 1394): VIA Technologies, Inc. IEEE 1394 Host Controller (rev 80)
chris@ubuntu:~$


I'm assuming that the pci adress that I put in bold is my Sound card. Could someone give me a tutorial/help me to get it working.

---

### Post by xXx 0wn3d xXx on 2006-03-28
[QUOTE=MasterChief1234]I am not getting sound on my Gateway MX7118 notebook. I doesn't bother me too much but it would be nice to have.

My lspci


I'm assuming that the pci adress that I put in bold is my Sound card. Could someone give me a tutorial/help me to get it working.[/QUOTE]
Can anyone help me with this ?

---

### Post by xXx 0wn3d xXx on 2006-03-28
[QUOTE=MasterChief1234]Can anyone help me with this ?[/QUOTE]
Anyone ?

---

### Post by trent dillman on 2006-03-28
I know this sounds silly, but did you check to see if your sound is muted?

Damn MasterChief, you've been having a hell of a time with that laptop, eh?

---

### Post by xXx 0wn3d xXx on 2006-03-28
[QUOTE=trent dillman]I know this sounds silly, but did you check to see if your sound is muted?

Damn MasterChief, you've been having a hell of a time with that laptop, eh?[/QUOTE]
Yeah, but I got most of the problems fixed and I'm enjoying ubuntu. And no I don't have it muted :)

---

### Post by xXx 0wn3d xXx on 2006-03-28
[QUOTE=MasterChief1234]Yeah, but I got most of the problems fixed and I'm enjoying ubuntu. And no I don't have it muted :)[/QUOTE]
Alright, let's see if I got it working. Does anyone have a sound that I can test to see if it works.

---

### Post by trent dillman on 2006-03-28
/usr/share/sounds/

---

### Post by xXx 0wn3d xXx on 2006-03-28
[QUOTE=trent dillman]/usr/share/sounds/[/QUOTE]
Nope :( I'll try some other things.

---

### Post by xXx 0wn3d xXx on 2006-03-28
Can anyone help ?

---

### Post by xXx 0wn3d xXx on 2006-03-29
Anyone got any ideas to help me get this fixed ? I've been trying for 2 days :)

---

### Post by souteneur3190 on 2006-03-29
look for the model of your sound card.

---

### Post by xXx 0wn3d xXx on 2006-03-29
[QUOTE=souteneur3190]look for the model of your sound card.[/QUOTE]
It's a 

AC ’97 2.3 Compliant Audio
Built-in Stereo Speakers

---

### Post by DOtSlaSHuCantCME on 2006-03-29
[QUOTE=MasterChief1234]Anyone got any ideas to help me get this fixed ? I've been trying for 2 days :)[/QUOTE]

type  "alsamixer" in your terminal, adjust things(if needed).
Go to system /preferences/Multimedia System Selector and test things.
Remenber PCM and Master can control Volume make sure none are muted.

---

### Post by xXx 0wn3d xXx on 2006-03-29
[QUOTE=DOtSlaSHuCantCME]type  "alsamixer" in your terminal, adjust things(if needed).
Go to system /preferences/Multimedia System Selector and test things.
Remenber PCM and Master can control Volume make sure none are muted.[/QUOTE]
Nope, I tried all of that. All my things are set at 100 %. I still can't hear a thing. ](*,)

---

### Post by swmiller6 on 2006-03-30
I have the same laptop did you ever get this working? I am on dapper drake and I get sound once and awhile. Varies each time I boot up, some times it woks the next time it may not.
Really hope I can find a fix...

---

