---
title: "HELP!!!!!! my graphicks don't work anymore!"
date: 2010-05-08
forum: General Help
---

### Post by soulchaos0 on 2010-05-08
i am currently using an acer aspire one netbook and i saw the port on the side for a moniter. so i figured 'why not?'. i discovered why not. i restarted my system and the screen is all wierd:cry: i think if i can restore the default settings i'll be fine... i managed to log in but i can't see what i'm doing... i am running the most current stable release of ubuntu... can anyone help please!!!! im desperate:cry::cry::cry:

---

### Post by TheNerdAL on 2010-05-08
What Video card do you have?

---

### Post by dino99 on 2010-05-08
> **soulchaos0 said:**
> i am currently using an acer aspire one netbook and i saw the port on the side for a moniter. so i figured 'why not?'. i discovered why not. i restarted my system and the screen is all wierd:cry: i think if i can restore the default settings i'll be fine... i managed to log in but i can't see what i'm doing... i am running the most current stable release of ubuntu... can anyone help please!!!! im desperate:cry::cry::cry:

karmic , lucid ?

---

### Post by soulchaos0 on 2010-05-08
i honestly have no idea. i got it used. but i think it's the factory model, i don't think the guy i got it from changed anything in it

---

### Post by soulchaos0 on 2010-05-08
i think it's 9.0 or something like that

---

### Post by TheNerdAL on 2010-05-08
I assume you don't have access to the terminal, right? Do you have a Live CD?

---

### Post by soulchaos0 on 2010-05-08
i don't have a disk drive at all. it's a netbook.

---

### Post by soulchaos0 on 2010-05-08
not a cd drive anyway i have a usb drive and a card reader.

---

### Post by TheNerdAL on 2010-05-08
> **soulchaos0 said:**
> not a cd drive anyway i have a usb drive and a card reader.

I'm guessing you used a USB Drive to install Netbook Remix?

---

### Post by soulchaos0 on 2010-05-08
my older sister's fiance put everything on it for me when i first got it. but i'm assuming he used a usb to instal everything.

---

### Post by dino99 on 2010-05-08
> **soulchaos0 said:**
> not a cd drive anyway i have a usb drive and a card reader.

[http://ubuntuforums.org/showpost.php?p=9216264&postcount=14](http://ubuntuforums.org/showpost.php?p=9216264&postcount=14)

---

### Post by TheNerdAL on 2010-05-08
Can you describe the screen after you boot up to me? Does it have Vertical lines that are green or purple or some other color?

---

### Post by soulchaos0 on 2010-05-08
> **dino99 said:**
> [http://ubuntuforums.org/showpost.php?p=9216264&postcount=14](http://ubuntuforums.org/showpost.php?p=9216264&postcount=14)
 i'm sorry this doesn't really help me... :(

---

### Post by soulchaos0 on 2010-05-08
> **TheNerdAL said:**
> Can you describe the screen after you boot up to me? Does it have Vertical lines that are green or purple or some other color?
 my screen flashes yellow and then gets a red strip and then it almost shows the login screen, only is in lines that go horizontally and don't line up in the least, so it makes colored bands.

---

### Post by TheNerdAL on 2010-05-08
So you connected a monitor to your netbook? Is it still connected?

---

### Post by soulchaos0 on 2010-05-08
> **TheNerdAL said:**
> So you connected a monitor to your netbook? Is it still connected?
 no it isn't, i did try reconnecting it to see if that helped but it didn't.

---

### Post by TheNerdAL on 2010-05-08
Sorry, I can't find a solution.

EDIT: It may be a hardware problem. Try to reinstall and see if it still has the problem after you reinstall.

---

### Post by soulchaos0 on 2010-05-08
oh... okay thanks anyway...

---

### Post by dino99 on 2010-05-08
> **soulchaos0 said:**
> i'm sorry this doesn't really help me... :(

see post #10 that will help if you check your brain

---

### Post by soulchaos0 on 2010-05-08
so how di i reinstall?

---

### Post by pqwoerituytrueiwoq on 2010-05-08
boot a live usb it is very obvious from there

---

### Post by Catharsis on 2010-05-08
Booting from Recovery Mode should fix it.

1) Hold down Shift as you boot to get you to the GRUB menu.
2) Select the newest kernel that has "(recovery mode)" after it. Should be the second one.
3) Select the graphics option; I forget exactly what it's called. "Fix Graphics", "Low-graphics mode", something like that. Then follow any "fix graphics", "reconfigure graphics" "Fix X", "Reconfigure X Server" or anything like that.

---

### Post by sdowney717 on 2010-05-08
If you can get it booting then run terminal and type in

lspci

this will list out the items including the video card. Then you will know what it is and what driver it can use.

---

### Post by soulchaos0 on 2010-05-08
> **Catharsis said:**
> Booting from Recovery Mode should fix it.
 
1) Hold down Shift as you boot to get you to the GRUB menu.
2) Select the newest kernel that has "(recovery mode)" after it. Should be the second one.
3) Select the graphics option; I forget exactly what it's called. "Fix Graphics", "Low-graphics mode", something like that. Then follow any "fix graphics", "reconfigure graphics" "Fix X", "Reconfigure X Server" or anything like that.
 my reovery menu doesn't have a graphics option...

---

### Post by soulchaos0 on 2010-05-08
is there a command i can use in the root promt to reinstall the system?

---

### Post by Catharsis on 2010-05-08
> **soulchaos0 said:**
> my reovery menu doesn't have a graphics option...

The option in the recovery menu is "failsafeX".

You can also try:
At the recovery menu, select "root" which should send you to a root shell. Then reconfigure the X server:
```
dpkg-reconfigure xserver-xorg
```
Then reboot:
```
reboot
```

---

### Post by soulchaos0 on 2010-05-08
> **Catharsis said:**
> The option in the recovery menu is "failsafeX".
 
You can also try:
At the recovery menu, select "root" which should send you to a root shell. Then reconfigure the X server:
```
dpkg-reconfigure xserver-xorg
```
Then reboot:
```
reboot
```
 
i just tried that... it didn't work, is there anyway i can upload a video of what it's doing so you guys have a better understanding of what it's doing?

---

