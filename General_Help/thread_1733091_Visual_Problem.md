---
title: "Visual Problem"
date: 2011-04-18
forum: General Help
---

### Post by El3mentGamer on 2011-04-18
So, I have installed Ubuntu on two of my friend's computers. And I have the EXACT same computer as them. But for some reason, when I get to the install screen: this is what it looks like...
[IMG]http://i1211.photobucket.com/albums/cc434/El3mentGamer/download.jpg[/IMG]
Idk, what would cause this. But it seems i's something specific wrong with my computer. Someone on another forum said it was an LCD error. Is this fixable? If so how? Please help. I loved Ubuntu when i've used it, but I can't get it for myself.

---

### Post by coffee412 on 2011-04-18
Is this a laptop? If so who makes it and whats the model number?

Do you have this problem booting from the install cd and running a live session?

---

### Post by El3mentGamer on 2011-04-18
> **coffee412 said:**
> Is this a laptop? If so who makes it and whats the model number?

Do you have this problem booting from the install cd and running a live session?

Yes it's a Laptop its an HP Pavilion dv6500.
This picture IS from the boot CD. I took a picture of it with my phone. Im scared to continue on with the installation because im scared it'll screw up my entire my computer. And yes, that is a live session.

---

### Post by coffee412 on 2011-04-18
> **El3mentGamer said:**
> Yes it's a Laptop its an HP Pavilion dv6500.
This picture IS from the boot CD. I took a picture of it with my phone. Im scared to continue on with the installation because im scared it'll screw up my entire my computer. And yes, that is a live session.

Well, I have seen that before on laptops of the HP nature. I have fixed quite a few of them. NEW motherboard. The video chipset is releasing from the motherboard.

Its kinda common with those. I bet you have a NVIDIA chipset right?

To be sure, Does it do it when you go into bios? (F2 or something like that at boot time)

---

### Post by El3mentGamer on 2011-04-18
Yes I have Nvidia lol. Is this fixable through the computer tho? I mean like i said 2 of my friends (2 seperate EXACT same laptops) have had ubuntu installed on them and they work perfect. is there anything that won't cost a heck load of money?

Edit: Wait whats Bios? F2 during the Ubuntu boot screen or the computer HP bootscreen?

---

### Post by coffee412 on 2011-04-18
> **El3mentGamer said:**
> Yes I have Nvidia lol. Is this fixable through the computer tho? I mean like i said 2 of my friends (2 seperate EXACT same laptops) have had ubuntu installed on them and they work perfect. is there anything that won't cost a heck load of money?

Edit: Wait whats Bios? F2 during the Ubuntu boot screen or the computer HP bootscreen?

Im sorry, But it is the kiss of death. The lead they use on the MBs is not lead based by law now. It has a lower melting point of about 100 F. WHere as regular leaded soldier melts about 168F. So, The video chip is seperating its connections to the MB. 

Its a real kicker. Motherboards are kinda pricy

---

### Post by El3mentGamer on 2011-04-18
Are you 200% sure it's the motherboard?

---

### Post by coffee412 on 2011-04-18
> **El3mentGamer said:**
> Are you 200% sure it's the motherboard?

To be sure, Boot into the bios and see if you get the same effect.

---

### Post by El3mentGamer on 2011-04-18
Yes sir. Stay checking this post if you will. You seem to be the only one who will help me. Kudo's for trying but wait for me lol..

---

### Post by coffee412 on 2011-04-18
> **El3mentGamer said:**
> Yes sir. Stay checking this post if you will. You seem to be the only one who will help me. Kudo's for trying but wait for me lol..

Not a problem. Ill be here a bit. Just let me know.


coffee

---

### Post by El3mentGamer on 2011-04-18
Ok so i got too the bios. And i didnt really know what to do. I ran the Hard Disk Scan and it said "replace", and the other scan said "passed" (cant remember what for tho). what exactly am i supposed to do in the PheonixBIOS
?

---

### Post by coffee412 on 2011-04-19
Suppose to see if you still have the problem on the bios screens. If the bios screens look ok then you might be ok.

Might just be the driver in Ubuntu for the video that is causing the problem with the card. What version of Ubuntu are you trying to load? 10.04, 10.10, 11.04 ?

Try a different version or when booting from cd hit F6 and choose nomodeset and run the cd live. See if you still have the problem.

---

### Post by El3mentGamer on 2011-04-19
Let me try this then I'll get back to you!

Edit: **THANK YOU COFFEE!** I made it through the installation and it looked perfect but when i restarted it (installation requirement) It went back to normal.... Luckily (and frustratingly) I was able to make it to the Ubuntu Admin Panel (while the screen still looked like crap) and i change the resolution lower. For some reason it it was set to 2000xwhatever. So now Ubuntu looks good on my computer and runs fine. However, i cant connect to wireless. 

The options to connect are:
Wired (disconnected)
Wireless Networks (device not ready--firmware missing)
VPN CONNECTIONS (which is the only one i can open)

How can I get the corrext firmware and allow myself to connect wirelessly?

---

### Post by coffee412 on 2011-04-19
> **El3mentGamer said:**
> 
  However, i cant connect to wireless. 

The options to connect are:
Wired (disconnected)
Wireless Networks (device not ready--firmware missing)
VPN CONNECTIONS (which is the only one i can open)

How can I get the corrext firmware and allow myself to connect wirelessly?

> Look in the menu in your top toolbar (panel) for system/administrator/ (something?)drivers

YOu want to install the firmware and driver for your wireless thats all. Ubuntu can do this automatically if you choose the above option.

Glad you got your video problem figured out. Im really happy it wasnt a hardware issue. Just keep an eye on that lappy and make sure you dont overheat it. 

coffee

---

### Post by El3mentGamer on 2011-04-19
Well, I've on and off tried to get Ubuntu over about a years period. And you helped me :D btw the nodemoset thing is what got it to work. Now about that driver thing. I clicked it but It can't find any drivers because im not connected to the internet :/ (im on a different computer replying to this thread) ... so how else can i do this? I don't have an ethernet cords available here...

Edit: Now it says...
**Wireless Networks (*[COLOR="Red"]Wireless is Disabled[/COLOR]*)**

---

### Post by coffee412 on 2011-04-19
Really the easiest way is to find somewhere to plugin a cat5 cable and get online. Perhaps a friends house? I dont know your internet access situation where you are at but thats what you have to do. 

I had to do that with a laptop once but it was kinda easy as they had a router hooked to their dsl modem.

---

