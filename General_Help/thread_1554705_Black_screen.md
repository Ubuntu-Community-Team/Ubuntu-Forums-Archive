---
title: "Black screen"
date: 2010-08-17
forum: General Help
---

### Post by yahrou on 2010-08-17
Hi everyone,

I'm new with ubuntu, I have installed it on my laptop few months ago. It was working fine since then. But yesterday, it started bugging really bad !

After a few minutes, the screen gets black and the computer seems dows. Anyway, i can still reach the console by doing ctr+alt+F1 and I can see this error : 

[ 574.384057][drm:i915_hangcheck_elapsed] *ERROR* Hangckeck timer elapsed... GPU hung
[ 574.384119] render error detected, EIR: 0x00000000
[ 574.384203] [drm:i915_do_wait_request] *ERROR* i915_do_wait_request returns -5 (awaiting 58844 at 58743)

Then I have to log on the console and Ubuntu is saying : 

Your CPU appears to be lacking expected security protections.
Please check your BIOS settings,or for more information, run: /usr/bin/check-bios-nx --verbose

And when I run the command, it says :

Segmentation Fault

This is stopping me from working with my laptop whereas this is my only linux computer : and I need it badly ! So please, someone help !

---

### Post by yahrou on 2010-08-17
No one ?

---

### Post by ryu kun on 2010-08-17
You can check your BIOS settings at boot time to see if you can enable NX.

---

### Post by yahrou on 2010-08-17
I can't find anything about NX in the BIOS, where would it be ?

---

### Post by ryu kun on 2010-08-17
It depends on your BIOS. Please read following for information.

> NX BIOS Control

Common Options : Enabled, Disabled

Quick Review

This BIOS feature is actually a toggle for the processor's No Execute feature. In fact, the acronym NX is short for No Execute and is specific to AMD's implementation. Intel's implementation is called XD, short for Execute Disable.

When enabled, the processor prevents the execution of code in data-only memory pages. This provides some protection against buffer overflow attacks.

When disabled, the processor will not restrict code execution in any memory area. This makes the processor more vulnerable to buffer overflow attacks.

It is highly recommended that you enable this BIOS feature for increased protection against buffer overflow attacks.

Source: [http://www.techarp.com/showFreeBOG.aspx?lang=0&bogno=329]("http://www.techarp.com/showFreeBOG.aspx?lang=0&bogno=329")

---

### Post by yahrou on 2010-08-17
I don't think I have this feature, I can't find it anywhere on the BIOS...

Thank's anyway, do you have antoher idea of where this might come from ?

---

### Post by yahrou on 2010-08-17
Can someone help ? Still unresolved !

---

### Post by yahrou on 2010-08-17
up...

---

### Post by QIII on 2010-08-17
If you have an Intel machine, you may be looking for "XD" in the BIOS which stands for "eXecute Disable".

Please don't bump so often.  The forum policy is about 24 hours.  Remember that we are here voluntarily on our own time.  It is possible that the person who has just the right answer for you lives in Bangalore -- and he may be at work or asleep right now.

---

