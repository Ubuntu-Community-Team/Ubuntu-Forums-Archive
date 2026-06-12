---
title: "Overheating problem when using Ubuntu."
date: 2012-07-17
forum: General Help
---

### Post by 25293Blaze on 2012-07-17
Hello. I enjoy using Ubuntu and Linux in general, and I would love to use it more often. Recently, after the 12.04 update my computer has been overheating when using my computer. The main problem is simply using Youtube and browsing the web. Youtube and Google Chrome run at about 70 to 100% CPU, while when I'm on Windows, the values are as low as 20 to 35% CPU. I have been trying to find a solution to this problem , and I even updated my AMD drivers. Help would definitely be appreciated since I am a big Linux fanatic. My computer is an HP Pavilion G series laptop with AMD Athlon II P360 Dual core procesor @ 2.3 GHz, a ATI Mobility Radeon HD 4250, and 3 gigs of DDR3 RAM.

---

### Post by QIII on 2012-07-17
Adobe arbitrarily decided to support hardware acceleration only with NVIDIA in the Linux version of Flash.  (Thanks, Adobe.)

Although you can add some hardware acceleration when you install the proprietary AMD/ATI driver, there still will be none with Flash.

Ironically, many NVIDIA users have to turn Flash hardware acceleration off due to the "smurfing" effect.  (Thanks again, Adobe.)

Because you are not getting hardware acceleration on your GPU, the task is dumped entirely on your CPU, and it is CPU intensive.

It's hard to know what that means with your particular CPU.  I can tell you that even on a Phenom II 1100T at 3.4GHz, it still can put me up to 5 - 10%.

---

### Post by trundlenut on 2012-07-17
Are you monitoring the temperatures on the laptop?

Are all the fans and vents clear and free of dust?

I just repaired a toshiba laptop and a quick blast with the vacuum cleaner reduced the normal cpu temperature by over 10 degrees celcius and stopped it overheating.

---

### Post by 25293Blaze on 2012-07-17
Well, thanks for the information. I have been planning to convert this laptop into a Linux machine after I build a dedicated gaming tower. Having all that video rendering put entirely on my CPU really turns me off using this laptop as a Linux machine. I wonder if Google may be able to work something out with their implementation of Flash on Chrome?

---

