---
title: "conky:  Offset Phenom II temperature"
date: 2012-02-24
forum: General Help
---

### Post by QIII on 2012-02-24
Something I've just dealt with, but which has always nagged me...

I have a machine with a Phenom II x6 1100T.  Everyone knows that AMD on-die sensors report low, so with gkrellm one just sets an offset to get a more realistic readout.  I hear everything from 6 to 15 degrees.  I've always used 10.

Anyway, I decided I'd finally get conky right on that machine.  Right now, I'm using something like this (and I realize there are a lot of ways to do this.  This is an example.)

```
${execi 1 cat /sys/module/k10temp/drivers/pci:k10temp/0000:00:18.3/temp1_input|cut -c  1,2}°C
```Where the heck to I put the "+= 10" to get the value I'm looking for?  That is, instead of reading 19 degrees, I want conky to say 29.

---

### Post by TeoBigusGeekus on 2012-02-25
```
initial_value=$(cat /sys/module/k10temp/drivers/pci:k10temp/0000:00:18.3/temp1_input|cut -c  1,2)
corrected_value=$(( initial_value+10 ))
echo $corrected_value
```
Save it as whatever and use it in conky like this:
```
${execi 1 /path/whatever}°C
```

---

### Post by QIII on 2012-02-25
Thanks.

I knew I could do it outside of my .conkyrc, but had hoped there was something easier in-line.

Alas.

Edit --

It may go without saying, but for those of you who happen by this, remember to put

```
#!/bin/sh
```

at the top of the script TeoBigusGeekus suggested.

---

