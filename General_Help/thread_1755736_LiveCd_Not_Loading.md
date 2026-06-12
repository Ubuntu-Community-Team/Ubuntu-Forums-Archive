---
title: "LiveCd Not Loading"
date: 2011-05-11
forum: General Help
---

### Post by WMUK on 2011-05-11
I insert my live cd, I restart Windows, I click F12, I click boot from CD Drive, and a purple screen with two icons appear on the bottom. Then about 1 second later, the screen becomes black, and a _ icon starts flashing for 10 minutes up in the top-left-hand corner. After that, my screen just becomes black! PLEASE Help!:(

---

### Post by Paddy Landau on 2011-05-11
> **WMUK said:**
> I restart Windows
Are you using WUBI? Or did you mean you restart your computer?

Assuming you are **not** using WUBI (because you pressed F12 and chose to boot from CD):

Two possibilities:

1. Your CD is not right.


[LIST]
[*] When you downloaded the ISO, did you check the MD5 sum?
[How to MD5 sum on Windows]("https://help.ubuntu.com/community/HowToMD5SUM#MD5SUM%20on%20Windows")
[The hash values to check]("https://help.ubuntu.com/community/UbuntuHashes")
[/LIST]

[LIST]
[*]When you burned the CD, did you verify the data?
[/LIST]

Do those steps first, because they're the most likely.

2. Your hardware is not compatible with Ubuntu (unlikely, but certainly possible).


[LIST]
[*]If you have verified the download and the CD, and it still doesn't work, try downloading the 10.04 (stable LTS), because 11.04 is not yet stable. That might work for you.
[/LIST]

---

### Post by WMUK on 2011-05-12
The Ubuntu 10.04 LTS is not working either! I verified the the MD5 sum (hash)! When I used the 10.04 LTS version, it said this time ubuntu failed or unexpectedly and then some "computer code"!

---

### Post by Paddy Landau on 2011-05-12
This sounds like a hardware incompatibility. Unfortunately, this is not an area I am strong in.

To double check, are you able to boot off this CD on a different machine (not the same manufacturer)?

What make and model are you using, and how old is the machine? How much memory does the computer have?

Can you take a snapshot (via a digital camera, perhaps) of the error messages and post it here?

---

### Post by WMUK on 2011-05-13
I am not able to boot off from another machine. I don't know the make, model, and age of the computer, but I know it runs Windows XP Professional. I don't know how much memory it has. I don't have a digital camera to take a picture with. Sorry.

---

### Post by Paddy Landau on 2011-05-13
How long have you waited? I know that my machine (which used to run Vista, and runs XP in a virtual box reasonably fast) takes a few minutes to boot from a USB, and a USB is somewhat faster than a CD.

Sorry, I'm not sure what else to say to help.

EDIT: If it can run XP Professional, then it can run Ubuntu or at least Lubuntu. My guess is that you have a hardware incompatibility.

SECOND EDIT: Try [Lubuntu]("http://lubuntu.net/"). It has much lower hardware requirements.

---

### Post by Topsiho on 2011-05-13
I too think it's a hardware problem. But what?
You say the computer runs Windows XP. Then I should think you can find out the amount of memory, and other hardware particulars, like processor and graphics card.
A possibility is that your player is not reading the LiveCD correctly. You should check the LiveCD for errors using that particular player. If it says that no errors are found you know that THAT is OK.

If your screen is OK first, but gets black or distorted in any way, you know that your graphics card is not working correctly, or not recognized at all.

You could also check the memory in your computer (memtest). Though, with bad memory Windows XP doesn't work too, I guess. But Linux uses memory better than Windows, so a bad spot might not be used by Windows, but IS used by Linux, and there you go. Maybe that's why you get a blue screen so often that you want to try Linux?

Just a few suggestions.

When burning the .iso disk as an image, try to do it at a low speed, such as 4x or so.

Succes,

Topsiho

---

### Post by Paddy Landau on 2011-05-14
One more idea. XP Professional can run on as little as 64Mb RAM. Ubuntu needs at least 512 (as I remember). Lubuntu needs 256Mb.

Find out the size of your memory in your computer. I forget how to do that in Windows; check the Windows help or forums.

If the memory is under 512Mg, you want Lubuntu. If it's under 256Mb, we can suggest lighter alternatives.

---

### Post by Naike on 2011-05-14
I'd like to see someone run Windows XP on 64MB ram lol.
Anyway, please tell us your system specs.
Graphics card, cpu and motherboard for starters.

---

### Post by Paddy Landau on 2011-05-14
> **Naike said:**
> I'd like to see someone run Windows XP on 64MB ram
I'm running XP Professional in a Virtual Box with 64Mb RAM on my Ubuntu machine. It runs reasonably, even when I turn off the host system's I/O caching.

---

### Post by n1ght5t4lk3r on 2011-05-14
Might be a stupid question but have you perhaps downloaded and burned a 64 bit version of ubuntu and trying to run it on a 32 bit only machine?

---

### Post by Paddy Landau on 2011-05-14
> **n1ght5t4lk3r said:**
> Might be a stupid question but have you perhaps downloaded and burned a 64 bit version of ubuntu and trying to run it on a 32 bit only machine?
I have tested this. The stick shows the purple screen for a short while, then gives this message:
```
This kernel requires an x86-64 CUP, but only detected an i686 CPU.
Unable to boot - please use a kernel appropriate for your CPU.
```Not exactly clear and meaningful to a newbie.

---

### Post by thevampire2604 on 2011-05-14
Hmm... check your hardware or try re-burning the cd if u used a CD/DVD-RW

---

### Post by n1ght5t4lk3r on 2011-05-14
> **Paddy Landau said:**
> 
```
This kernel requires an x86-64 CUP, but only detected an i686 CPU.
Unable to boot - please use a kernel appropriate for your CPU.
```


Basically the problem is as I asked about. you are trying to run a 64 bit version of ubuntu on a 32 bit only machine. 
i686 is intel's 32 bit architecture and x86_64 is 64 bit architecture(can also run 32 bit mode). You'll will need to re-download a 32 bit version of Ubuntu and burn the disk again then it should work (assuming the hardware you have is sufficient)

---

### Post by Paddy Landau on 2011-05-14
> **n1ght5t4lk3r said:**
> Basically the problem is as I asked about...
Uh, I'm not the OP. The OP's description shows a different symptom.

---

### Post by linuxuser12345 on 2011-05-14
Try different versions. Not all LiveCDs will be compatible with your system.

---

### Post by n1ght5t4lk3r on 2011-05-14
> **Paddy Landau said:**
> Uh, I'm not the OP. The OP's description shows a different symptom.

sorry wasn't paying attention to who the OP was, just saw the code posted an assumed it was the same person. apologies.

---

