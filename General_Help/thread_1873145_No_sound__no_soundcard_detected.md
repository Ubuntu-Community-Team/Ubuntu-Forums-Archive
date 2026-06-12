---
title: "No sound / no soundcard detected"
date: 2011-10-31
forum: General Help
---

### Post by agzt on 2011-10-31
Hello there!

I'm new to ubuntu, and found my first problem :(

$ aplay -l
aplay: device_list:240: no se encontraron tarjetas de sonido...

(that means "no soundcards detected")

I have sound on Windows, it detects my ALC883 (Realtek)

can you help me? :p

Thanks

---

### Post by agzt on 2011-11-01
help?

---

### Post by agzt on 2011-11-01
sudo lspci -v

80:01.0 Audio device: VIA Technologies, Inc. VT8237A/VT8251 HDA Controller (rev 10)
    Subsystem: Foxconn International, Inc. Device 0cf4
    Flags: bus master, fast devsel, latency 0, IRQ 17
    Memory at fd00000000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: [50] Power Management version 2
    Capabilities: [60] MSI: Enable- Count=1/1 Maskable- 64bit+
    Capabilities: [70] Express Root Complex Integrated Endpoint, MSI 00
    Capabilities: [100] Virtual Channel
    Kernel driver in use: HDA Intel
    Kernel modules: snd-hda-intel

---

### Post by agzt on 2011-11-01
Updated kernel to 3.1 from 3.0

the problem persist

---

### Post by agzt on 2011-11-01
update: here is the alsa-info

[http://www.alsa-project.org/db/?f=7beb9b56a03d7075db4ffec6a8194693fdba9431](http://www.alsa-project.org/db/?f=7beb9b56a03d7075db4ffec6a8194693fdba9431)

---

### Post by agzt on 2011-11-02
Well now I installed Ubuntu 11.10 32bits (I was previously using the 64-bit version) and the problem persist... please can someone post something? thanks

---

### Post by veko on 2011-11-02
I had a similar problem with HP 630 laptop. I can't check if it had the same sound card, but I did spend some time with that (as you probably have too) and found various solutions, though I didn't test all of them. Here are some, for example:

[http://www.linuxquestions.org/questions/linux-hardware-18/no-sound-ubuntu-10-04-hp-mini-110-a-798751/](http://www.linuxquestions.org/questions/linux-hardware-18/no-sound-ubuntu-10-04-hp-mini-110-a-798751/)


However, this solution worked for me (instructions are in German, but you can read the commands)
[http://www.it-muecke.de/node/577](http://www.it-muecke.de/node/577)

In short, install Linux-Alsa-Driver-Module from ubuntu-audio-dev/ppa:[FONT=courier new]

[/FONT]```
$ sudo add-apt-repository ppa:ubuntu-audio-dev/ppa
$ sudo apt-get update
$ sudo apt-get install linux-alsa-driver-modules-$(uname -r)

```And restart.

I can't promise it works for you, of course.

---

### Post by agzt on 2011-11-02
> **veko said:**
> I had a similar problem with HP 630 laptop. I can't check if it had the same sound card, but I did spend some time with that (as you probably have too) and found various solutions, though I didn't test all of them. Here are some, for example:

[http://www.linuxquestions.org/questions/linux-hardware-18/no-sound-ubuntu-10-04-hp-mini-110-a-798751/](http://www.linuxquestions.org/questions/linux-hardware-18/no-sound-ubuntu-10-04-hp-mini-110-a-798751/)


However, this solution worked for me (instructions are in German, but you can read the commands)
[http://www.it-muecke.de/node/577](http://www.it-muecke.de/node/577)

In short, install Linux-Alsa-Driver-Module from ubuntu-audio-dev/ppa:[FONT=courier new]

[/FONT]```
$ sudo add-apt-repository ppa:ubuntu-audio-dev/ppa
$ sudo apt-get update
$ sudo apt-get install linux-alsa-driver-modules-$(uname -r)

```And restart.

I can't promise it works for you, of course.

I appreciate your help but it didn't work

---

### Post by agzt on 2011-11-04
recompiled alsa but it didnt work

---

### Post by agzt on 2011-11-15
bump

---

### Post by lidex on 2011-12-31
Maybe you should go back to the stock kernel:
```
Kernel release:3.1.0-030100-generic
```

My kernel on 11.10:
```
3.0.0-15-generic #24-Ubuntu SMP Mon Dec 12 15:23:55 UTC 2011 x86_64 x86_64 x86_64 GNU/Linux

```

Alsa is not recognizing your hardware. Could be borked. Have you tried re-install:
Using a Terminal="Applications->Accessories->Terminal"
```
sudo aptitude --purge reinstall linux-sound-base alsa-base alsa-utils linux-image-`uname -r` linux-ubuntu-modules-`uname -r` libasound2
```
**Reboot.**

For a 'command not found' error simply install aptitude:
```
sudo apt-get install aptitude
```

---

### Post by tariquex on 2011-12-31
Could try restart alsa audio driver and check if you get any error
```
sudo alsa force-reload
```

---

### Post by agzt on 2012-07-12
> **lidex said:**
> Maybe you should go back to the stock kernel:
```
Kernel release:3.1.0-030100-generic
```My kernel on 11.10:
```
3.0.0-15-generic #24-Ubuntu SMP Mon Dec 12 15:23:55 UTC 2011 x86_64 x86_64 x86_64 GNU/Linux

```Alsa is not recognizing your hardware. Could be borked. Have you tried re-install:
Using a Terminal="Applications->Accessories->Terminal"
```
sudo aptitude --purge reinstall linux-sound-base alsa-base alsa-utils linux-image-`uname -r` linux-ubuntu-modules-`uname -r` libasound2
```**Reboot.**

For a 'command not found' error simply install aptitude:
```
sudo apt-get install aptitude
```

Hey, thanks for your help, I tried but it did not work.

I get this:

```
andres@agzt-desk-pc02:~$ sudo aptitude --purge reinstall linux-sound-base alsa-base alsa-utils linux-image-`uname -r` linux-ubuntu-modules-`uname -r` libasound2
No se pudo encontrar ningún paquete cuyo nombre o descripción coincida con «linux-ubuntu-modules-3.0.0-16-generic»
No se pudo encontrar ningún paquete cuyo nombre o descripción coincida con «linux-ubuntu-modules-3.0.0-16-generic»
Se REINSTALARÁN los siguientes paquetes:
  alsa-base alsa-utils libasound2 linux-image-3.0.0-16-generic 
  linux-sound-base 
0 paquetes actualizados, 0 nuevos instalados, 5 reinstalados, 0 para eliminar y 1184 sin actualizar.
Necesito descargar 0 B de archivos. Después de desempaquetar se usarán 0 B.
E: No se pudo localizar un archivo para el paquete libasound2. Esto puede significar que necesita arreglar manualmente este paquete.
E: No se pudo bloquear /var/lib/apt/lists/lock - open (11: Recurso no disponible temporalmente)
E: No se pudo bloquear el directorio de listas...¿es el administrador?
```Translating:

```
andres@agzt-desk-pc02:~$ sudo aptitude --purge reinstall linux-sound-base alsa-base alsa-utils linux-image-`uname -r` linux-ubuntu-modules-`uname -r` libasound2
Could not find any package whose name or description matched «linux-ubuntu-modules-3.0.0-16-generic»
Could not find any package whose name or description matched «linux-ubuntu-modules-3.0.0-16-generic»
The following packages will be REINSTALLED:
  alsa-base alsa-utils libasound2 linux-image-3.0.0-16-generic 
  linux-sound-base 
0 upgraded, 0 newly installed, 5 reinstalled, 0 to remove and 1184 not upgraded.
Need to get 0 B files. After unpacking 0 B used.
E: Could not locate file for the package libasound2. This may mean you need to manually fix this package.
E: Could not lock / var / lib / apt / lists / lock - open (11: Resource temporarily unavailable)
E: Could not lock the directory of lists... are you the administrator?
```

What now?



> **tariquex said:**
> Could try restart alsa audio driver and check if you get any error
```
sudo alsa force-reload
```

Tried but it did not work...


Why Linux/Ubuntu is not recognizing my sound card?

---

### Post by agzt on 2012-07-12
updated to ubuntu 12.04, the problem persist...

---

### Post by agzt on 2012-07-13
installed snd-hda-dkms but nothing...

---

### Post by jmfal on 2012-07-13
Try this
```
 sudo apt-get install --reinstall libasound2  
```

Restart
Make sure all speaker volumes PCM are not muted in alsamixer
If you are going to play a cd unmute cd in the mixer
Play some music

---

### Post by agzt on 2012-07-13
> **jmfal said:**
> Try this
```
 sudo apt-get install --reinstall libasound2  
```

Restart
Make sure all speaker volumes PCM are not muted in alsamixer
If you are going to play a cd unmute cd in the mixer
Play some music

Thanks for the reply, my sound card is NOT detected... so if i type in the terminal -alsamixer, nothing happens....

I can not mute or un-mute because there is nothing to mute/un-mute D:

---

### Post by jmfal on 2012-07-13
Take a look at this if you haven't already , enter commands for your version (12.04,11.10, etc...) if specified.

[https://help.ubuntu.com/community/SoundTroubleshootingProcedure](https://help.ubuntu.com/community/SoundTroubleshootingProcedure)

---

### Post by agzt on 2012-07-13
> **jmfal said:**
> Take a look at this if you haven't already , enter commands for your version (12.04,11.10, etc...) if specified.

[https://help.ubuntu.com/community/SoundTroubleshootingProcedure](https://help.ubuntu.com/community/SoundTroubleshootingProcedure)

Thanks, i'll try it.

---

### Post by agzt on 2012-07-13
> **jmfal said:**
> Take a look at this if you haven't already , enter commands for your version (12.04,11.10, etc...) if specified.

[https://help.ubuntu.com/community/SoundTroubleshootingProcedure](https://help.ubuntu.com/community/SoundTroubleshootingProcedure)

I tried but it did not work....

BUT, GOOD NEWS, i updated alsa driver, lib and utils to 1.0.25 (compiling the source) and now i can run alsamixer!!! but still not detecting my soundcard...

```
andres@agzt-desk-pc02:~$ cat /proc/asound/version
Advanced Linux Sound Architecture Driver Version 1.0.25.
Compiled on Jul 13 2012 for kernel 3.2.0-26-generic (SMP).
andres@agzt-desk-pc02:~$ cat /proc/asound/cards
--- no soundcards ---

```

```
andres@agzt-desk-pc02:~$ aplay -l
aplay: device_list:252: no se encontraron tarjetas de sonido...

```
("no soundcards found", or "no soundcards detected", i do not know english good)


```
andres@agzt-desk-pc02:~$ lspci -v
80:01.0 Audio device: VIA Technologies, Inc. VT8237A/VT8251 HDA Controller (rev 10)
    Subsystem: Foxconn International, Inc. Device 0cf4
    Flags: bus master, fast devsel, latency 0, IRQ 11
    Memory at <ignored> (64-bit, non-prefetchable)
    Capabilities: <access denied>
    Kernel modules: snd-hda-intel

```

---

### Post by rcayea on 2012-07-13
Try lspci -tv to get more detailed info regarding your hardware.

---

### Post by agzt on 2012-07-13
> **rcayea said:**
> Try lspci -tv to get more detailed info regarding your hardware.

ok, i'll try it.

with "lspci -v" i just copied the audio-related output...
the output of that command is longer

---

### Post by jmfal on 2012-07-13
Hopefully this will make sound card detectable

```
  [COLOR=#ffffff][FONT=Courier New]echo  "Sound cards recognized by the system:"; lspci -nn | grep --color=none  '\[04[80][13]\]'; echo "Sound cards recognized by ALSA:"; lspci -nn |  grep '\[04[80][13]\]' | while read line; do lspci -nnk | grep -A 3  '\[04[80][13]\]' | grep -e 'Kernel modules: ..*' -e '\[04[80][13]\]' |  grep --color=none -F "$line"; done; echo "Sound cards recognized by  ALSA, and activated:"; lspci -nn | grep '\[04[80][13]\]' | while read  line; do lspci -nnk | grep -A 3 '\[04[80][13]\]' | grep -e 'Kernel  drivers in use: ..*' -e '\[04[80][13]\]' | grep --color=none -F "$line";  done[/FONT][/COLOR]   
```You can copy/paste this into terminal.

Please enter bios an make sure the onboard sound is enabled before you run this command.

---

### Post by jmfal on 2012-07-13
Sorry copy/paste not working from link.
Scroll down to--
**[COLOR=#274E13][FONT=Arial][B]Procedure Ac (Make the system/ALSA recognize the sound card(s))**[/FONT][/COLOR][/B]

you will have to copy/paste usung the edit menu in tool bar(mouse will not work)::


[https://docs.google.com/document/d/1iTlJ8BfqXUjaHO__TEdlkvuqB1WLOkGaudngc5SFLMI/edit?pli=1#](https://docs.google.com/document/d/1iTlJ8BfqXUjaHO__TEdlkvuqB1WLOkGaudngc5SFLMI/edit?pli=1#)

---

### Post by agzt on 2012-07-14
> **jmfal said:**
> Sorry copy/paste not working from link.
Scroll down to--
**[COLOR=#274E13][FONT=Arial][B]Procedure Ac (Make the system/ALSA recognize the sound card(s))**[/FONT][/COLOR][/B]

you will have to copy/paste usung the edit menu in tool bar(mouse will not work)::


[https://docs.google.com/document/d/1iTlJ8BfqXUjaHO__TEdlkvuqB1WLOkGaudngc5SFLMI/edit?pli=1#](https://docs.google.com/document/d/1iTlJ8BfqXUjaHO__TEdlkvuqB1WLOkGaudngc5SFLMI/edit?pli=1#)

thank you! i ran the command and i get:

```
andres@agzt-desk-pc02:~$ echo  "Sound cards recognized by the system:"; lspci -nn | grep --color=none  '\[04[80][13]\]'; echo "Sound cards recognized by ALSA:"; lspci -nn |  grep '\[04[80][13]\]' | while read line; do lspci -nnk | grep -A 3  '\[04[80][13]\]' | grep -e 'Kernel modules: ..*' -e '\[04[80][13]\]' |  grep --color=none -F "$line"; done; echo "Sound cards recognized by  ALSA, and activated:"; lspci -nn | grep '\[04[80][13]\]' | while read  line; do lspci -nnk | grep -A 3 '\[04[80][13]\]' | grep -e 'Kernel  drivers in use: ..*' -e '\[04[80][13]\]' | grep --color=none -F "$line";  done
Sound cards recognized by the system:
80:01.0 Audio device [0403]: VIA Technologies, Inc. VT8237A/VT8251 HDA Controller [1106:3288] (rev 10)
Sound cards recognized by ALSA:
80:01.0 Audio device [0403]: VIA Technologies, Inc. VT8237A/VT8251 HDA Controller [1106:3288] (rev 10)
Sound cards recognized by  ALSA, and activated:
80:01.0 Audio device [0403]: VIA Technologies, Inc. VT8237A/VT8251 HDA Controller [1106:3288] (rev 10)

```

but with aplay -l

```
andres@agzt-desk-pc02:~$ aplay -l
aplay: device_list:252: no se encontraron tarjetas de sonido...

```

( no soundcards detected )

---

### Post by jmfal on 2012-07-14
Your best bet is to follow that howto from that point.

I used and it works, I'm just pulling commands from it,

Post back here if there are any problems or to mark as solved.

---

### Post by agzt on 2012-07-14
> **jmfal said:**
> Your best bet is to follow that howto from that point.

I used and it works, I'm just pulling commands from it,

Post back here if there are any problems or to mark as solved.


thanks for the reply, i do step Ac... and because aplay -l does not work, i follow step Aa, and then it says me to jump to Ac... its a infinite loop.... something is wrong here....

---

### Post by agzt on 2012-07-14
> **rcayea said:**
> Try lspci -tv to get more detailed info regarding your hardware.

with that the output is:

```
andres@agzt-desk-pc02:~$ lspci -tv
-+-[0000:80]---01.0  VIA Technologies, Inc. VT8237A/VT8251 HDA Controller

```

(the output is largest, but no sound-related)

---

### Post by jmfal on 2012-07-14
Go ahead and follow Ab 

You'll have to experiment with alsamixer and sound settings every time the howto send you to alsamixer

---

### Post by agzt on 2012-07-14
> **jmfal said:**
> Go ahead and follow Ab 

You'll have to experiment with alsamixer and sound settings every time the howto send you to alsamixer

ok i did all the steps again, here is something wrong, with step Ac alsa detects my soundcard and it says its activated... and with aplay -l it says no...

---

### Post by agzt on 2012-07-14
Here is a screenshot of alsamixer

---

### Post by jmfal on 2012-07-14
Enter this in a terminal
```
 [SIZE=2]sudo modprobe snd-[/SIZE]  
```
Press and hold down tab key and press enter, this will give you a list of drivers
Look for:
#1--vt8251
#2--vt8237a
#3--via82c686
#4--via8233
#5--via8233a
#6--via8235
#7--via8237
If one of these are listed enter it after "sudo modeprobe snd-"  as you see it in list

Press enter then try some music, this will load driver(kernal) till you restart
If no sound restart and try another from list

make sure sound is unmuted and that card is selected in alsamixer

---

### Post by agzt on 2012-07-14
> **jmfal said:**
> Enter this in a terminal
```
 [SIZE=2]sudo modprobe snd-[/SIZE]  
```Press and hold down tab key and press enter, this will give you a list of drivers
Look for:
#1--vt8251
#2--vt8237a
#3--via82c686
#4--via8233
#5--via8233a
#6--via8235
#7--via8237
If one of these are listed enter it after "sudo modeprobe snd-"  as you see it in list

Press enter then try some music, this will load driver(kernal) till you restart
If no sound restart and try another from list

make sure sound is unmuted and that card is selected in alsamixer

```
andres@agzt-desk-pc02:~$ sudo modprobe snd-
[sudo] password for andres: 
FATAL: Module snd_ not found.
```

something is wrong

---

### Post by jmfal on 2012-07-14
Yes something is wrong.

I fear that all the configuring and advice from all directions has really screwwed things up!!

If it were my pc, I would reinstall and start over, then try to get sound working.

Read the stickies in the multimedia section, one is the link I gave you.

---

### Post by agzt on 2012-07-14
> **jmfal said:**
> Yes something is wrong.

I fear that all the configuring and advice from all directions has really screwwed things up!!

If it were my pc, I would reinstall and start over, then try to get sound working.

Read the stickies in the multimedia section, one is the link I gave you.

ok, thank you very much for your help

---

### Post by tokyobadger on 2012-07-22
when you see
```
$ sudo modprobe snd-
Display all 229 possibilities? (y or n)
```
choose y and hit enter to see more (scroll down)

I saw the following
```
 snd-via82xx
 snd-via82xx-modem
```
so I'm wondering if you tried
```
sudo modprobe snd-via82xx
```

---

### Post by oscarivera9 on 2012-07-22
> **jmfal said:**
> Yes something is wrong.

I fear that all the configuring and advice from all directions has really screwwed things up!!

If it were my pc, I would reinstall and start over, then try to get sound working.




Try using a Live CD to find out if you're getting sound working in a Live environment.  If trying a new distro (Ubuntu 12.04, Xubuntu 12.04, etc. or even Linux Mint 13) works, then do a fresh install of a good working distribution that you like.  Usually that works.  If it doesn't work when you try a Live CD, then there's no point doing a fresh install.

---

### Post by agzt on 2012-07-27
> **tokyobadger said:**
> when you see
```
$ sudo modprobe snd-
Display all 229 possibilities? (y or n)
```
choose y and hit enter to see more (scroll down)

I saw the following
```
 snd-via82xx
 snd-via82xx-modem
```
so I'm wondering if you tried
```
sudo modprobe snd-via82xx
```

thanks for the reply, now i am not on my PC, but if i try ```
sudo modprobe snd-
```

i get:
```
andres@agzt-desk-pc02:~$ sudo modprobe snd-
[sudo] password for andres: 
FATAL: Module snd_ not found.
```



> **oscarivera9 said:**
> Try using a Live CD to find out if you're getting sound working in a Live environment.  If trying a new distro (Ubuntu 12.04, Xubuntu 12.04, etc. or even Linux Mint 13) works, then do a fresh install of a good working distribution that you like.  Usually that works.  If it doesn't work when you try a Live CD, then there's no point doing a fresh install.

thanks for the reply, no sound with live cd.

---

