---
title: "How to know to what corresponds the /dev/snd sounds?"
date: 2010-09-28
forum: General Help
---

### Post by honeybear on 2010-09-28
Hello,

I have several USB mic, and would like to which one correspodn to which /dev/ from command line. Is it possible under ubuntu?

---

### Post by HermanAB on 2010-09-28
Run dmesg after you plug a mic in.

---

### Post by HermanAB on 2010-09-28
Another solution:
cat /dev/sndx | /dev/dsp

for x = 1 to n

Then tap the mic and listen to the speaker.

---

### Post by honeybear on 2010-10-01
> **HermanAB said:**
> Another solution:
cat /dev/sndx | /dev/dsp

for x = 1 to n

Then tap the mic and listen to the speaker.

not working :(

```
$ cat /dev/snd/ | /dev/dsp
by-id/     by-path/   controlC0  controlC1  pcmC0D0c   pcmC0D0p   pcmC0D1c   pcmC0D2c   pcmC0D3c   pcmC0D4p   pcmC1D0c   seq        timer  
```



> **HermanAB said:**
> Run dmesg after you plug a mic in.
nothing as /dev/dsp appears: :(

> 
[  985.450248] usb 3-1: configuration #1 chosen from 1 choice
[  985.960684] usbcore: registered new interface driver snd-usb-audio
[  990.391335] [drm] nouveau 0000:01:00.0: Setting dpms mode 0 on lvds encoder (output 0)
[  990.391349] [drm] nouveau 0000:01:00.0: Calling LVDS script 2:
[  990.391360] [drm] nouveau 0000:01:00.0: 0xBAC4: Parsing digital output script table
[  990.540064] [drm] nouveau 0000:01:00.0: Calling LVDS script 5:
[  990.540074] [drm] nouveau 0000:01:00.0: 0xB9AC: Parsing digital output script table
[ 1689.392814] sphinx2-continu[7433]: segfault at 7deaecc9 ip 7deaecc9 sp 7deaecc9 error 4




---

