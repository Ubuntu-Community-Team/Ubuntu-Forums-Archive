---
title: "No audio on new Lucid install."
date: 2010-05-05
forum: General Help
---

### Post by sephirot_5 on 2010-05-05
I just installed Lucid, and everything seems fabulous, except for audio:

The sound control seems... well _dead_ (i don't know how to explain it so I attach a screenshot), and under "System>Preferences>Sound", under the "Hardware" tab, it does not show any device. I was using 9.10 before and had not this issue! even when booting my Windows partition everything isfine.

I'm lost here, can anyone help me?

---

### Post by arturhoo on 2010-05-05
Same thing here...

---

### Post by blueridgedog on 2010-05-05
What type of sound card/device do you have?  What is the output of:

```
lspci | grep Audio
```

---

### Post by sephirot_5 on 2010-05-05
> **blueridgedog said:**
> What type of sound card/device do you have?  What is the output of:

```
lspci | grep Audio
```

I get

```

$ lspci | grep Audio
00:04.0 Multimedia audio controller: nVidia Corporation CK804 AC'97 Audio Controller (rev a2)

```

---

### Post by lidex on 2010-05-05
Go to 'System>Preferences>Sound' and check your configuration.
Check your levels in alsamixer.
```
 alsamixer 
```
Press F6 to select the correct soundcard.
Press F3 to show playback levels. F4 selects capture levels [or use <Tab>]
Use the left/right arrow keys to select and up/down arrow keys to change levels. <M> to mute/unmute.

---

### Post by sephirot_5 on 2010-05-05
> **lidex said:**
> Go to 'System>Preferences>Sound' and check your configuration.
Check your levels in alsamixer.
```
 alsamixer 
```
Press F6 to select the correct soundcard.
Press F3 to show playback levels. F4 selects capture levels [or use <Tab>]
Use the left/right arrow keys to select and up/down arrow keys to change levels. <M> to mute/unmute.


I did it already and everything's the same... :(
Why I am the only one with this kind of problems?

---

### Post by lidex on 2010-05-05
> **sephirot_5 said:**
> I did it already and everything's the same... :(
Why I am the only one with this kind of problems?
Because you're special!! ;)
Can you post the output of these terminal commands for me please:
```
uname -a
aplay -l
cat /proc/asound/version
head -n 1 /proc/asound/card*/codec#*
```
Terminal="Applications->Accessories->Terminal"
Please post text output using code tags. Also helpful is the make/model of your PC/Laptop.

---

### Post by sephirot_5 on 2010-05-05
> **lidex said:**
> Because you're special!! ;)
Can you post the output of these terminal commands for me please:
```
uname -a
aplay -l
cat /proc/asound/version
head -n 1 /proc/asound/card*/codec#*
```
Terminal="Applications->Accessories->Terminal"
Please post text output using code tags. Also helpful is the make/model of your PC/Laptop.

Ok this is the output:

```

$ uname -a
Linux fabrizio-desktop 2.6.32-21-generic #32-Ubuntu SMP Fri Apr 16 08:10:02 UTC 2010 i686 GNU/Linux

$aplay -l
aplay: device_list:223: no se encontraron tarjetas de sonido...
(ok this means something like: "sound board not found...")

$ cat /proc/asound/version
Advanced Linux Sound Architecture Driver Version 1.0.21

$ head -n 1 /proc/asound/card*/codec#*
head: no se puede abrir «/proc/asound/card*/codec#*» para lectura: No existe el fichero ó directorio
(and this one says like: "can't open «/proc/asound/card*/codec#*» for reading: File or directory doesn't exist")

```

My computer is, kind of self made, though I know nothing about computers, teehee, but I guess that knowing the output of previous command can give you an idea of what my sound card is?

Oh, and I can't be thankfull enough for your help!

---

### Post by sephirot_5 on 2010-05-05
Ok, thanks a lot for your help. After making an upgrade, everything works fine :D

---

### Post by lidex on 2010-05-05
Great. Can you mark the thread as solved using 'Thread Tools up top please?

---

