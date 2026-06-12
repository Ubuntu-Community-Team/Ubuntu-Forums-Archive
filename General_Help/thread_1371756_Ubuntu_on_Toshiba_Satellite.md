---
title: "Ubuntu on Toshiba Satellite"
date: 2010-01-03
forum: General Help
---

### Post by msohn88 on 2010-01-03
I have previous used Ubuntu for a week, literally, on Thinkpad.

Now, I got a laptop from my sister which is Toshiba Satelite A135-S4527 with Vista installed.

It's tad annoying for everything, (Why IE and WMP?)

I am thinking about changing to Ubuntu, but I have a few questions. (I don't have much experience with it)

1)I have to install with Desktop Version with 32 bit? (This computer says it's 32 bit, but I am not sure about Desktop Version)

2) I need to use Skype, but when I was using it, the other person can see me, but I was not able to see myself while I can see their face.

3) Which webcam should I get in order to install webcam easily?

4) I only need to use it for -- writing reports, Webcam chat with my family and friends. (AIM & Skype), Ubuntu is fine?

5) Can I type Asian languages - Korean?

Thank you in advance.

---

### Post by 73ckn797 on 2010-01-03
You will need 32 bit. I cannot help with your other questions. Ubuntu works great on my Toshiba (see signature at bottom).

---

### Post by howefield on 2010-01-04
> **msohn88 said:**
> It's tad annoying for everything, (Why IE and WMP?)

Even with windows you have a choice. It needn't be IE and WMP.

> 1)I have to install with Desktop Version with 32 bit? (This computer says it's 32 bit, but I am not sure about Desktop Version)

Not sure I understand this, but you are probably safer with the 32 bit version if you are unsure whether or not your computer supports 64 bits.

Boot with the Live cd and open a terminal, you can type

```
lshw -C cpu | grep width
```

If the width returns 64, then your processor will support 64 bit Ubuntu as well as 32 bit.

> 2) I need to use Skype, but when I was using it, the other person can see me, but I was not able to see myself while I can see their face.

Don't know.

> Which webcam should I get in order to install webcam easily?

One which supports UVC. Here is a list that appears fairly recent.

[http://linux-uvc.berlios.de/#devices](http://linux-uvc.berlios.de/#devices)

> I only need to use it for -- writing reports, Webcam chat with my family and friends. (AIM & Skype), Ubuntu is fine?

Absolutely marvellous :)

Skype is your biggest challenge, but very much solvable.

> Can I type Asian languages - Korean?

Yes, if it isn't installed by default, you can add it with Synaptic Package Manager.

---

