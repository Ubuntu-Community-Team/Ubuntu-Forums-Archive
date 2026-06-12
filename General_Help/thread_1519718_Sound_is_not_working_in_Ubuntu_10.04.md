---
title: "Sound is not working in Ubuntu 10.04"
date: 2010-06-28
forum: General Help
---

### Post by rajiv1096 on 2010-06-28
Hello, I have a newly installed Ubuntu 10.04 Operating system. As soon as i booted it up, i realized that my sound was not working, for anything (movies, youtube videos, music, etc.) How do Make the sound work?

---

### Post by gtmarks on 2010-06-28
It might be dependent on what hardware you're running Ubuntu on (e.g. many laptops have a mute button in a panel above the keyboard).  In the System menu, under Preferences, if you open the "Sound" application, do you see anything amiss in the output volume or output device?

---

### Post by cmcanulty on 2010-06-28
I had same problem and installed Gnome Alsa Mixer. When I unchecked external amplifier I got sound, worth a try.

---

### Post by rajiv1096 on 2010-06-28
Could you please show me how you did that?

Thanks

---

### Post by cmcanulty on 2010-06-29
Go to synaptic or software center and type gnome alsa mixer and install. Then it appears under Applications-sound and video. Open it and uncheck external amplifier. Also check the other settings and make sure they are on or off as desired. Mine I have to uncheck every boot. But also you can try clicking speaker icon on top panel then click sound preferences and under output tab see that connector is set to analog output/no amplifier.Since I did the panel option mine stays set

---

### Post by fairy._.queen on 2010-07-12
Hi all!
I have Kubuntu 10.04 installed on my laptop and sound doesnt work as well. as i dont think i can install GNOME alsa mixer on a KDE environment, could you please suggest me something else that might work?
Thanks in advance!

---

### Post by nss0000 on 2010-07-12
No sound no surprise in LL_10.04:

The "secondary" sys-functions: sound/login/vidcam/printer are all subject to erratic and variable behavior in LL_10.04. I run modern quad-kit. About half-time one of those items is mis_behaving for me. Every software update brings an "un_date" for one of those functions. 

My personal opinion ... having run Linux for 10-years and unix for 20 ... is that LL_10.04 was a "code too far" over_reach by Cannonical, attempting to generate an industrial strength desktop from usrland U_9.xx code. The usrland base was very impressive -- just not ready for what was asked.

---

### Post by cmcanulty on 2010-07-13
I think you can install it on KDE as I have installed a few KDE applications on gnome.

---

### Post by cefola on 2010-08-21
> **cmcanulty said:**
> Go to synaptic or software center and type gnome alsa mixer and install. Then it appears under Applications-sound and video. Open it and uncheck external amplifier. Also check the other settings and make sure they are on or off as desired. Mine I have to uncheck every boot. But also you can try clicking speaker icon on top panel then click sound preferences and under output tab see that connector is set to analog output/no amplifier.Since I did the panel option mine stays set

That solved my problem as well:
Box: Gateway Laptop MX3228
OS:  Debian Lenny

Thanks a million!
Ray

---

