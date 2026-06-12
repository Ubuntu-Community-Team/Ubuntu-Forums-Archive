---
title: "Get windows back?"
date: 2011-09-17
forum: General Help
---

### Post by jonny5015 on 2011-09-17
I downloaded Ubuntu three months ago, and while doing so I guess I deleted Windows completely. I've searched all over the forums and Google and could not find any help. I want windows back. Can anyone shine some light on how to get it back?

thanks
-Jonathan

---

### Post by haqking on 2011-09-17
> **jonny5015 said:**
> I downloaded Ubuntu three months ago, and while doing so I guess I deleted Windows completely. I've searched all over the forums and Google and could not find any help. I want windows back. Can anyone shine some light on how to get it back?

thanks
-Jonathan


that depends on how you installed Ubuntu.  If it is still on your system then an entry should exist in your grub menu if you are dual booting.

If you removed it completely then you will need to do a factory restore if you have a hidden partiton which allows you to, or reinstall using your Windows CD/DVD or using your restore discs.

All this will depend on what you have, the factory restore wil depend on your machine and whether one is built in, usually pressing f8 during boot brings up the menu.

LIke i said, depends on what you have to restore windows.

however this question might be better posed in a Windows Forum.

---

### Post by jonny5015 on 2011-09-17
> **haqking said:**
> that depends on how you installed Ubuntu.  If it is still on your system then an entry should exist in your grub menu if you are dual booting.

If you removed it completely then you will need to do a factory restore if you have a hidden partiton which allows you to, or reinstall using your Windows CD/DVD or using your restore discs.

All this will depend on what you have, the factory restore wil depend on your machine and whether one is built in, usually pressing f8 during boot brings up the menu.

LIke i said, depends on what you have to restore windows.

however this question might be better posed in a Windows Forum.

I don't have a windows disck, how else can I get it back!?

---

### Post by overdrank on 2011-09-17
> **jonny5015 said:**
> I don't have a windows disck, how else can I get it back!?

Contact the system manufacture and request cd's. :)

---

### Post by JC Cheloven on 2011-09-17
> **jonny5015 said:**
> I don't have a windows disck, how else can I get it back!?

You should have a license number in a sticker at the back of you pc. Use any windows disc (same version of what you have the license for), and put your license number when asked.

---

### Post by jonny5015 on 2011-09-17
> **JC Cheloven said:**
> You should have a license number in a sticker at the back of you pc. Use any windows disc (same version of what you have the license for), and put your license number when asked.

I don't have a CD andthe barcode has been scratched off lol
i dont know how that happens

---

### Post by Rasa1111 on 2011-09-17
you can't. unless you buy a new windows disc.

---

### Post by WorMzy on 2011-09-17
In that case, I think that following overdrank's suggestion is the best course of action left available to you: Contact your system's manufacturer and explain the situation, they may be able to provide you with a new CD and license code.

Rasa's suggestion of buying a new Windows disk would be another option. You can probably pick up an OEM of Win XP or Vista pretty cheaply these days, considering Win 8 is on the way.

---

### Post by JC Cheloven on 2011-09-17
Just out of curiosity: Did you have any particular problem with ubuntu? It seems you haven't been using windows since months... what do you miss?

That would be a more suitable question for an Ubuntu help forum ;)

---

### Post by Triblaze on 2011-09-17
Just wondering, are you sure you deleted windows completely? I'm having a similar problem, but for me it's that I can't boot into windows, all the stuff is still there. The way you said "I guess", it sounds like you aren't completely sure it's gone. In the filemanager, can you find another filesystem, probably something like "[#] GB filesystem", which contains the windows files?

Just wondering, you probably did lose it, I just recognize that I have a similar issue and you don't seem completely sure that it's gone, and there's a possibility it may just be hidden in the computer from you.

---

### Post by Rasa1111 on 2011-09-17
> **WorMzy said:**
> 
Rasa's suggestion of buying a new Windows disk would be another option. You can probably pick up an OEM of Win XP or Vista pretty cheaply these days, considering Win 8 is on the way.


another option, for sure..
but I don't encourage it! lol :P

---

### Post by jonny5015 on 2011-09-17
> **JC Cheloven said:**
> Just out of curiosity: Did you have any particular problem with ubuntu? It seems you haven't been using windows since months... what do you miss?

That would be a more suitable question for an Ubuntu help forum ;)

I miss how simple it was to play games on my machine. If it were easier to set up games, I would never look back at windows again.

---

### Post by cryptotheslow on 2011-09-18
It really does depend how you installed Ubuntu. If you took the "use whole disc" option then it will most likely have obliterated your windows install. If you took the "side by side" option then your windows partition will have been shrunk and Ubuntu installed in another partition next to it.

Please open a Terminal and issue this command and paste back the response:

```

sudo fdisk -l

```

It will ask you for your password as it is a "sudo" command.

Alternatively, find GParted in your admin menu and screenshot what partitions your drive(s) have. In GParted you can use the dropdown to the top right to select a drive if you have more than one.

All may not be lost - your windows install could still be there in a withered/shrunken state or failing that we may discover a recovery partition that you can restore from (more likely on a laptop or pad).

---

