---
title: "Very choopy sound quality"
date: 2012-09-18
forum: General Help
---

### Post by tds787 on 2012-09-18
As the title says the sound quality on a newly installed laptop is horribly choppy. Probably need help finding and installing an audio driver. I know you'll need more information than this but it's a pavilion g7 Laptop with Ubuntu 10.04

---

### Post by raja.genupula on 2012-09-18
could you post output of 
```
lspci | grep Audio
```

and one more thing , open system settings and select additional drivers . is it listing you any drivers ?

---

### Post by tds787 on 2012-09-18
Output:

00:01.1 Audio device: ATI Technologies Inc Device 1714
00:14.2 Audio device: Advanced Micro Devices [AMD] Device 780d (rev 01)



And no, no additional drivers

---

### Post by raja.genupula on 2012-09-18
until i get back please refer this 
[https://wiki.ubuntu.com/DebuggingSoundProblems](https://wiki.ubuntu.com/DebuggingSoundProblems)
[http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)

---

### Post by tds787 on 2012-09-18
Adding the alsa repository and downloading new driver helped mostly and the audio is now clear 80% of the time but there are still periods of choppyness.

I tried the position fix, it didn't help

---

