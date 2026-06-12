---
title: "Linux softphones: all bad sound quality"
date: 2009-07-13
forum: General Help
---

### Post by UranUtan on 2009-07-13
Hi,

All softphones I have tried under Linux gave a mediocre sound, Sometimes so choppy that I don't understand the message as roughly 80% of the incoming message is lost. Especially when the correspondent has an IVR system with speech recognition. When running the same tests on a low end Windows machine. The sound is crystal clear on every test.

**[COLOR="Blue"]Linux TEST (Core2 E8400, 8 GB Ram, Ubuntu 9.04 x64)[/COLOR]**
1- Zoiper 2.10
2- Twinkle, version 1.2
3- SJphone v1.65
4- Ekiga 3.20

[B][COLOR="Blue"]Windows Test (Pentium3, 768 MB Ram, WinXP SP3)
[/COLOR][/B]- Using a softphone supplied by the VoIP Provider (VBuzzer.com in Canada: [http://www.vbuzzer.com/download.php](http://www.vbuzzer.com/download.php))

The Linux machine has the sound system working OK. It plays music and video OK. In spite of its powerful hardware, none of the softphones tested could not reach the quality of the Windows softphone.

What is the reason? Is there anything wrong with my Ubuntu / Sound device configuration or is it a known issue?

Thanks in advance for any help.

---

### Post by UranUtan on 2009-07-13
Issue (may be solved):

Tech support from my VoIP provider suggested to try other codecs. For each of the program above. Among the available codecs, I selected each one and placed it on the highest priority. Then made a test call each time. One by one until I find the right codec. Turned out that there is only one combination that work for me:

**Ekiga 3.20, using Codec "G722, 16 Khz, H.323, SIP"**.

How strange, Ekiga was the program I was the least confident. And which has the least convenient GUI. But somehow it manages to work better than other specialized softphone programs. Go figure!

---

