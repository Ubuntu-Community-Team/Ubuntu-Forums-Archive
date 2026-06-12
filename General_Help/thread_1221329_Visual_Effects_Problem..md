---
title: "Visual Effects Problem."
date: 2009-07-23
forum: General Help
---

### Post by TheNerdAL on 2009-07-23
Okay so when I try to edit the Visual Effects In the Appearance Window and I go to the Extra Settings, It says that It is searching for Drivers, But it cannot find any. :( Can anyone help?

---

### Post by Daniel1994 on 2009-07-23
I had this problem too.

System>Administration>Hardware drivers

check if there are any not installed

---

### Post by TheNerdAL on 2009-07-23
> **Daniel1994 said:**
> I had this problem too.

System>Administration>Hardware drivers

check if there are any not installed

There is nothing there. :(


CAN ANYONE WHO IS READING THIS PLEASE HELP?!

---

### Post by synapsys on 2009-07-23
You need to have a video card with 3d acceleration to enable extra visual effects.

Said video card needs to have a driver installed in order to communicate with your operating system. What video card do you have?

If you are unsure, open up a terminal Applications >> Accessories >> Terminal
and type:

```
lspci | grep VGA
```

And post the results here.

---

### Post by TheNerdAL on 2009-07-23
> **synapsys said:**
> You need to have a video card with 3d acceleration to enable extra visual effects.

Said video card needs to have a driver installed in order to communicate with your operating system. What video card do you have?

If you are unsure, open up a terminal Applications >> Accessories >> Terminal
and type:

```
lspci | grep VGA
```And post the results here.

It Gave me this: "01:00.0 VGA compatible controller: Silicon Integrated Systems [SiS] 661/741/760 PCI/AGP or 662/761Gx PCIE VGA Display Adapter."

---

### Post by synapsys on 2009-07-23
> **TheNerdAL said:**
> It Gave me this: "01:00.0 VGA compatible controller: Silicon **Integrated** Systems [SiS] 661/741/760 PCI/AGP or 662/761Gx PCIE VGA Display Adapter."

You have an integrated graphics controller. This means that the VGA adapter is integrated into the motherboard. You do not have a seperate video card. You have two choices from here.

1. Forget about 'extra' effects.
2. Buy and install a graphics card.

---

### Post by TheNerdAL on 2009-07-23
> **synapsys said:**
> You have an integrated graphics controller. This means that the VGA adapter is integrated into the motherboard. You do not have a seperate video card. You have two choices from here.

1. Forget about 'extra' effects.
2. Buy and install a graphics card.

I will Forget about the Extra Effects, But How Much is Graphics Card?

---

### Post by RJARRRPCGP on 2009-07-23
I dunno about the onboard you have. But I do know that Nvidia is supported well.

---

### Post by TheNerdAL on 2009-07-23
> **RJARRRPCGP said:**
> I dunno about the onboard you have. But I do know that Nvidia is supported well.


Okay, I guess. :( One Reason I wanted Ubuntu was because of the Cool Effects.:( But Okay.:)

---

### Post by synapsys on 2009-07-23
> **TheNerdAL said:**
> I will Forget about the Extra Effects, But How Much is Graphics Card?

It depends on what type of connection you have on your motherboard. There are 4 different types AGP, PCI, PCIE, and PCIE2. You're going to have to figure out what type of slot you have and you can find a graphics card to match your configuration. This will involve opening up your computer case, if you are not comfortable in doing this, then find somebody who is. 

That being said, graphics cards can range anywhere from $25 - $3,000 depending on the type.

If all you care about is the effects (and not gaming or video editing) then you can probably pick one up for pretty cheap.

---

### Post by TheNerdAL on 2009-07-24
> **synapsys said:**
> It depends on what type of connection you have on your motherboard. There are 4 different types AGP, PCI, PCIE, and PCIE2. You're going to have to figure out what type of slot you have and you can find a graphics card to match your configuration. This will involve opening up your computer case, if you are not comfortable in doing this, then find somebody who is. 

That being said, graphics cards can range anywhere from $25 - $3,000 depending on the type.

If all you care about is the effects (and not gaming or video editing) then you can probably pick one up for pretty cheap.

Thanks, But will I still be able to use Blender?:(

---

### Post by synapsys on 2009-07-24
If I remember correctly, blender is a 3d rendering application. I would reccommend at least a 600 mb graphics card, nvidia chipsets seem to work the best with ubuntu.

PS if you can use blender now you will most definately be able to use it with a graphics card.

---

### Post by TheHustle on 2009-07-24
For a card probably think in the $100-$300 region.

---

