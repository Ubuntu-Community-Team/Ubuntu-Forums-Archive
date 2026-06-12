---
title: "Trying to get 3D effects in Ubuntu..."
date: 2010-02-04
forum: General Help
---

### Post by MooseyMcMan on 2010-02-04
Okay, a few days ago my friend installed VirtualBox and Ubuntu on his computer, and he had all these cool effects like a 3D cube. So, I followed suit, and did everything he's done, except the 3D effects won't work on my computer. I have 3D acceleration enabled, and compiz just tells me that a software rasterizer is in use. 
 
And the thing that really confuses is that the 3D screensavers work, even though when I try to turn the 3D effects on it says it can't. 
 
Any suggestions? Please?!?

---

### Post by howefield on 2010-02-04
What make/model of graphics card are you using ?

---

### Post by MooseyMcMan on 2010-02-04
My computer's an HP, and it has "Mobil Intel(R) 4 Series Express Chipset Family" for the graphics. I know my computer can run things like Google Earth in flight simulator mode, so it should be powerful enough.

---

### Post by rudeboyskunk on 2010-02-04
I wonder if it's because of the poor 3D graphics support that Intel cards have, or the lack of a good enough linux driver for Intel cards.

---

### Post by MooseyMcMan on 2010-02-04
I certainly hope that isn't it. I mean, I've run other 3D programs.

---

### Post by howefield on 2010-02-04
Try running this command in terminal


```
sudo dpkg-reconfigure -phigh xserver-xorg
```

Once that is done, follow it with this, which will restart your desktop. Then try compiz again.

```
sudo /etc/init.d/gdm restart
```

If it doesn't work, can you post the outputs from 

```
lspci | grep VGA
``` 
```
glxinfo | grep -i renderer
```

---

### Post by MooseyMcMan on 2010-02-04
That didn't work, it still said the software rasterizer is in use. Then I tried the other thing(lspci | grep VGA) , and it says, "00:02.0 VGA compatible controller: InnoTek Systemberatung GmbH VirtualBox Graphics Adapter" 
 
Then when I input the last suggestion it said, "OpenGl renderer string: Software Rasterizer"

---

### Post by howefield on 2010-02-04
> **MooseyMcMan said:**
> Then I tried the other thing(lspci | grep VGA) , and it says, "00:02.0 VGA compatible controller: InnoTek Systemberatung GmbH VirtualBox Graphics Adapter"

Sorry, I now realise that you are running Ubuntu inside Virtualbox.
  
It isn't the computer graphics card that's giving you the problem but the Virtualbox graphics card driver.

Can I check you have installed guest additions (for the improved graphics driver)

---

### Post by MooseyMcMan on 2010-02-04
I think there's something there, and now my roommate is suggesting that I re-install it. I'll try doing that (unless someone else has a better idea).

---

### Post by MooseyMcMan on 2010-02-04
Okay, It tried re-installing the guest addition, but now the VirtualBox crashes when I try running compiz, because (according to my roommate), I had installed the wrong guest addition (I'm starting to doubt his judgement right now though). It did have a whole bunch of different guest additions in the list, so I'll try a different one.

---

### Post by howefield on 2010-02-04
> **MooseyMcMan said:**
> because (according to my roommate), I had installed the wrong guest addition.

It's likely one of these that you need, depending on whether you are on 32 bit or 64 bit.

```
sudo sh ./VBoxLinuxAdditions-x86.run
sudo sh ./VboxLinuxAdditions-amd64.run
```

---

### Post by MooseyMcMan on 2010-02-04
The amd one isn't working, so I'm trying the x86 one right now. It didn't crash this time at least, but it still says the software rasterizer is in use.

---

