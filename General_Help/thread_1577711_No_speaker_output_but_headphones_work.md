---
title: "No speaker output but headphones work"
date: 2010-09-19
forum: General Help
---

### Post by studystand on 2010-09-19
I'm currently running Ubuntu Netbook Remix on my HP Mini 110-3000 and I get no speaker output but the sound works when I plug my headphones in. I downloaded Alsamixer and played with the setting but nothing helped so now I turn to you guys.

---

### Post by blueridgedog on 2010-09-19
Run aslamixer from the command line and see if have any output muted or turned down.

---

### Post by studystand on 2010-09-19
> **blueridgedog said:**
> Run aslamixer from the command line and see if have any output muted or turned down.

sorry i'm new to ubuntu, how would I do this?

---

### Post by Frogs Hair on 2010-09-19
Type alsamixer into the terminal.

---

### Post by blueridgedog on 2010-09-19
Launch a terminal via applications, accessories, terminal. Then enter 


```
alsamixer
```

---

### Post by PsychoElixir on 2010-09-19
After I enter that what do I do? I dont know what I'm looking at

---

### Post by blueridgedog on 2010-09-19
Use the left and right arrows to select an output and the up and down arrows to change the volume level.  Look for something that is zero or low and experiment to see if you get audio from your speakers...you should have the headphones unplugged as the speakers can be muted when headphones are plugged in.

---

### Post by PsychoElixir on 2010-09-19
According to alsamixer it says that s/pdif is off...I can't figure out out to turn it on or if it's even important

---

### Post by studystand on 2010-09-19
i played around with the settings and got nothing, any other suggestions?

---

### Post by PsychoElixir on 2010-09-19
Seems as though we are suffering from the same issues

---

### Post by PsychoElixir on 2010-09-19
So i fixed my issue...I dont know how I did it but now my speakers work..but guess what? my HEADPHONES dont work now...

So in a way I won the battle but am still losing the war...

---

### Post by blueridgedog on 2010-09-20
> **studystand said:**
> i played around with the settings and got nothing, any other suggestions?

Without headphones plugged in, what was the volume for the other channels and what were they?  Did you have one called "front" or "PCM"?

---

### Post by studystand on 2010-09-20
> **blueridgedog said:**
> Without headphones plugged in, what was the volume for the other channels and what were they?  Did you have one called "front" or "PCM"?

I had one called PCM which constantly went from 99-100 and back again

---

