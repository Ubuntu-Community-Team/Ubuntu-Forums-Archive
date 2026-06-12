---
title: "Skype Mic problems"
date: 2010-05-08
forum: General Help
---

### Post by musdem on 2010-05-08
When I installed skype everyting worked fine the sound the video and the webcam, however the one thing that didnt work was the mic, I have no idea how to fix this ive tried to up the mic sensitivity all the way up and change the different mic inputs but nothing works. I you have any idea on how to fix this please tell me. I have a sennheiser PC 151 headset and im plugging it in through the mic input NOT a usb input.

---

### Post by lidex on 2010-05-08
Try this. Use a terminal="Applications->Accessories->Terminal"
Enter these commands, one line at a time:
```
sudo add-apt-repository ppa:ubuntu-audio-dev/ppa
sudo apt-get update
sudo apt-get install linux-alsa-driver-modules-$(uname -r)
```

---

### Post by musdem on 2010-05-08
Ahh thank you now it works perfectly. :)

---

### Post by lidex on 2010-05-08
Great. Please mark the thread as solved using 'Thread Tools' up top.

---

