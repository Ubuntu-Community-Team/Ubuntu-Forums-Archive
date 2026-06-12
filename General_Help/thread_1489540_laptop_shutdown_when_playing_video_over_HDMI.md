---
title: "laptop shutdown when playing video over HDMI"
date: 2010-05-21
forum: General Help
---

### Post by shlomi on 2010-05-21
Hi, 
I have a weird problem, i have an LG LCD screen that i connect to my laptop via HDMI through nVidia. I was watching full length movies and everything worked perfectly. So, i got myself a new, slightly bigger LG LCD, and now, when I play a movie, about 20-60 minutes into the movie, my machine just turns off. doesnt even shutdown properly, just turns itself off, as if the power ran out (which it didnt..)

I thought maybe i had too many things installed, or mabe i should wait for a new version.. so i waited till i reinstalled a fresh 10.4 on a new partition, played a movie, and again, the machine just suddenly turned itself off.

i tried looking in the system log viewer, but between shutdown and startup, i see nothing special (besides ALOT of "rt_ioctl_giwscan. 1(1) BSS returned, data->length = 105")..

i tried running 64bit & 32bit and it has the same error...

any ideas?? :confused:

---

### Post by warfacegod on 2010-05-21
My guess is that the GPU is overheating forcing the computer to shut itself off to save itself from damage. With HDMI, I assume you're watching High Def movies and that can be very taxing on your hardware. Try reducing the refresh rate or resolution.

---

### Post by warfacegod on 2010-05-21
By the way, you might consider updating your User profile. If your using 10.04 and your profile says 6.06 that can be confusing for every one. The solution to a problem in 6.06 won't likely be the same as 10.04.

---

### Post by shlomi on 2010-05-21
hehehe, i updated my profile! you see, i didnt have any problems since 6.06! thats a good thing :)

anyhow, i assume it is heat related, my laptop is pretty much melting there on the bottom.. although it would be nice if there was anything logged about it in the syslog! 

i dont watch HD, just regular video, but perhaps ill attempt reducing the resolution for the LCD screen... 

thank you for your advice!

---

### Post by warfacegod on 2010-05-21
Sounds like its time to clean the fans and heatsinks. If you remove the heatsink, be sure to clean off the old thermal grease and replace it with fresh grease. If you use compressed air to clean the fans out don't let the fans spin, hold them with your finger or something. The spinning can create a static charge: 

Old Thermal grease + CPU = Broken Laptop

Static + Electronics = Broken Laptop

I came up with those equations myself, Stephen Hawking would be so proud!

No problems since 6.06, very cool. Did you do upgrades through to 10.04 or fresh installs?

---

### Post by obscurant1st on 2010-05-21
^^ this same issue happened to me also. GPU over heat was the cause! :)

---

### Post by shlomi on 2010-05-21
> **warfacegod said:**
> Sounds like its time to clean the fans and heatsinks.

Now that is a good idea!! now i just gotta look for some thermal grease.. 

Your equations are completely mathematically proven, I personally think Mr. Hawking can learn a thing or two ;) hehe

It was a fresh install.. I usually dont like the upgrades, i have my /home on a separate partition, and i like to reinstall fresh versions of all the software i *actually* use.. so its good cleanup time, with saving all your desktop and settings!

Thanks for the advice, ill do a little open-sink surgery later today, and ill get some thermal grease next week! 

10x!

---

### Post by shlomi on 2010-05-21
Hey,
I need some assistance with my little laptop-surgery, i opened it up, cleaned the vent, but iam not so sure where i should put the thermal grease.. 

I attached a picture of my patient, you can notice the heat dent marks on the top right.. :)

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=157770&stc=1&d=1274455188[/IMG]

so I have these big orange wires going across these pieces of metal with blue sponge-like thing underneath.. where should i apply the grease in this complex? 

THANKS!!!!!!

---

### Post by warfacegod on 2010-05-21
Skip the grease. Those tubes are liquid cooling of some kind. The purple thing poking out from under that metal plate looks to be the CPU socket clamp. Normally you'd put thermal grease between the CPU and that plate. Unfortunately it looks like some serious surgery involved in getting to it. Unless you want to disassemble all of that stuff (potentially causing a coolant leak), you should leave it alone. Just do a thorough dusting.

---

### Post by shlomi on 2010-05-21
Thanks warfacegod!

I just wanted to say, that i dusted my machine before you sent your reply, and the effect is absolutely remarkable!! my cpu & gpu temp has dropped more then 20 degrees Celsius!

I will try playing a movie soon, and ill post the results, :popcorn:

to everyone who has heating problems: **DUST YOUR DEVICES!!!!** the effect is remarkable!  :guitar:

many thanks!

---

### Post by warfacegod on 2010-05-21
Glad to hear the temperature went down. Assuming you have no further issues with the computer shutting down then you can mark this as "Solved". Cheers.

---

