---
title: "Need help with ventrilo"
date: 2010-07-30
forum: General Help
---

### Post by nkdnaskdn on 2010-07-30
HEy i downloaded ventrilo and it opens and runs well n stuff just.. i get no sound... with or without mic... i mean my laptop sound works.. it has a built in mic.. but ventrilo has no sound.. help plz.. btw my friends can hear me.

---

### Post by akoskm on 2010-07-30
> **nkdnaskdn said:**
> HEy i downloaded ventrilo and it opens and runs well n stuff just.. i get no sound... with or without mic... i mean my laptop sound works.. it has a built in mic.. but ventrilo has no sound.. help plz.. btw my friends can hear me.

Which sound system are you using?
Try various sound systems in
```

winecfg

```
Audio tab.

---

### Post by Jazzy_Jeff on 2010-07-30
I don't think you will be able to get it working. I have had no luck with it in the past and neither have any of my friends that have tried it.

---

### Post by akoskm on 2010-07-31
> **Jazzy_Jeff said:**
> I don't think you will be able to get it working. I have had no luck with it in the past and neither have any of my friends that have tried it.

Interesting, I used it about 1 years in the previous version of Ubuntu.
I'll post the configuration as soon as I get working it under 10.04 too.

---

### Post by akoskm on 2010-07-31
Make sure that you have selected the right device for input:
*System > Preferences > Sound > Input*.
I have 3 input devices here: Microphone 1, Microphone 2, Line-In. Slide the scrollbar from Unamplified to 100% (actually you can leave it on Unamplified and start singing into the microphone to test it but in 100% you have enough noise around your laptop what makes change in the *Input level*) and switch between the devices.
If you see that the *Input level* is changing with the current *Connector*, that one is your build-in mic (if you have to much noise in Ventrilo later change the input volume).
Download these files
```

MSVCP60.DLL
msgsm32.acm

```
and move them to
```

~/.wine/drive_c/windows/system/

```.
Now start Ventrilo. In Setup set the test codec to GSM 6.10 and the format to 11025 Hz, 16 bit (this is my configuration I hope that it works for you too), hit the Test button and make some noise :).

Important: Ventrilo need to own your sound card first, so start it and then start the other applications using your sound card. Ventrilo won't work if you have Rythmbox playing some music while you are starting it or if you already started World of Warcraft and after Ventrilo.

---

