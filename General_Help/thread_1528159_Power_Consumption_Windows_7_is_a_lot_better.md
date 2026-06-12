---
title: "Power Consumption Windows 7 is a lot better"
date: 2010-07-10
forum: General Help
---

### Post by KristinaK on 2010-07-10
Power Consumption Windows 7 is a lot better

I have a new HP netbook, which came with Windows 7 Starter. I just installed Ubuntu Netbook on there as well to give it a go.

At the moment I am getting over 3 hours of light use out of it on windows and just over 2 hours on Ubuntu. This is basically just web browsing and using the wireless.

Are there any ways of getting more battery life out of the Ubuntu install?

---

### Post by DanPaulCiocan on 2010-07-10
Maybe you could turn the screen lower (there is a button on your keyboard), also you can reduce your CPU frequency by using the CPU Frequency Scaling Monitor: [http://www.ubuntugeek.com/howto-change-cpu-frequency-scaling-in-ubuntu.html](http://www.ubuntugeek.com/howto-change-cpu-frequency-scaling-in-ubuntu.html)

---

### Post by mike555 on 2010-07-10
go to System > preferences > Startup apps , and uncheck ones you don't use , like bluetooth , file sharing , etc.

---

### Post by Jim_in_Omaha on 2010-07-10
I have a new Dell 11z. I'm also finding that Ubuntu draws the battery down faster than Win7. I am working with some of the different app's that control power. So far I have not found a great improvement. 

I have the 3-cell battery and it lasts around 2 hours. I will probably pick up a 6-cell from Ebay.

---

### Post by NertSkull on 2010-07-10
I'm not sure there is much you can do about it, I've messed with things for months and not changed much.

On a full charge, when booted to Win7 I can get 3hrs 50 min of use.  But only barely over 2 hours with ubuntu (after turning off lots of stuff I don't use).

If you do find a way to increase ubutnu bat life, I'd love to hear as well.

---

### Post by Jim_in_Omaha on 2010-07-12
I found Powertop. It shows some of the most active things running that use power. Shows an approximate wattage use also. Seems pretty handy. Still testing. I can get my 11z to run around 10 watts according to powertop.

---

### Post by yossell on 2010-07-12
Make sure that the cpu governor is on, and scaling down your cpu - otherwise ubuntu may be running the chips full speed the whole time which has a bad affect on battery life. An app for this can be added and enabled on the panels.

Check you've got the right driver installed for your graphics card/chip. Default nvidia driver far worse at power saving than the proprietary one. 

Whether you'll get equivalent battery life as windows can depend on components and drivers for them - normally, sadly, windows drivers are better and more carefully designed by manufacturers. 

But I second powertop as a way of really cutting down power. When I began with linux, my laptop battery's life was 2/3 what i got in windows and computer was hot. With tweaking, and learning, I made adjustments to make my battery life *better* than windows.

---

### Post by Jim_in_Omaha on 2010-07-12
> **yossell said:**
> Make sure that the cpu governor is on, and scaling down your cpu - otherwise ubuntu may be running the chips full speed the whole time which has a bad affect on battery life. An app for this can be added and enabled on the panels.

Check you've got the right driver installed for your graphics card/chip. Default nvidia driver far worse at power saving than the proprietary one. 

Whether you'll get equivalent battery life as windows can depend on components and drivers for them - normally, sadly, windows drivers are better and more carefully designed by manufacturers. 

But I second powertop as a way of really cutting down power. When I began with linux, my laptop battery's life was 2/3 what i got in windows and computer was hot. With tweaking, and learning, I made adjustments to make my battery life *better* than windows.

Is that the CPU Frequency Scaling Monitor app? I have that running. Dumb question of the hour. Do I need two of those app's because of a dual core cpu? As I work with it, it gives the impression that it is only controlling one cpu.

---

### Post by cascade9 on 2010-07-12
> **Jim_in_Omaha said:**
> Is that the CPU Frequency Scaling Monitor app? I have that running. Dumb question of the hour. Do I need two of those app's because of a dual core cpu? As I work with it, it gives the impression that it is only controlling one cpu.

No, you only need one instance of cpu-freq. I dont think its even possible to install more than one. ;)

---

### Post by yossell on 2010-07-12
Jim - 

that's an interesting question - cascade9 may be right but when working in gnome, I do run two applets of the cpu frequency scaling monitor on the gnome-panel, setting one to cpu0 and one to cpu1 for the two cores. You don't have to - you can run one from the panel and set cpu1, then right-click - preferences and change monitored cpu. To me, they also give the impression of being independent, with the two running different plans and reporting different speeds. It could just be some strange glitch of the panel interface.

On the other hand, setting things from the suggestions of powertop, which I do when I'm not running gnome environment, seems to set both cores to the right plan.

So it may just all depend on how exactly you're setting the clock speeds  - I should look into it more closely.

---

### Post by mortalapeman on 2010-07-12
Ok so here is an easy solution. This program put Unbuntu back on par with Windows 7 on my laptop and with no observable loss of speed or usability.
 
[http://grano.la/help/?os=linux](http://grano.la/help/?os=linux)
 
It is one of the things I install right away with a fresh install of Ubuntu.

---

### Post by isecore on 2010-07-12
FWIW, my mom's little Asus eeePC with a completely vanilla Ubuntu 10.04 has better battery-time than the Windows 7 Home Premium that came with it. 

She'd get something like 5-6 hours with Windows 7 (she's not an intense user, mostly web-browsing, listening to a little music and checking her email) and about an hour or so more with Ubuntu.

---

### Post by cascade9 on 2010-07-14
> **yossell said:**
> Jim - 

that's an interesting question - cascade9 may be right but when working in gnome, I do run two applets of the cpu frequency scaling monitor on the gnome-panel, setting one to cpu0 and one to cpu1 for the two cores. You don't have to - you can run one from the panel and set cpu1, then right-click - preferences and change monitored cpu. To me, they also give the impression of being independent, with the two running different plans and reporting different speeds. It could just be some strange glitch of the panel interface.

On the other hand, setting things from the suggestions of powertop, which I do when I'm not running gnome environment, seems to set both cores to the right plan.

So it may just all depend on how exactly you're setting the clock speeds  - I should look into it more closely.

You can run multipule cpu-freq-monitors, but only one instance of cpu-freq. AFAIK anyway.

---

### Post by Jim_in_Omaha on 2010-07-14
> **mortalapeman said:**
> Ok so here is an easy solution. This program put Unbuntu back on par with Windows 7 on my laptop and with no observable loss of speed or usability.
 
[http://grano.la/help/?os=linux](http://grano.la/help/?os=linux)
 
It is one of the things I install right away with a fresh install of Ubuntu.

I will try this. 

For what its worth Powertop has improved my 11z to around 3 hours now while listening to online streaming radio through the speakers on the laptop.

---

### Post by KristinaK on 2010-07-23
Will it be solved in Ubuntu 10.10 ?

---

