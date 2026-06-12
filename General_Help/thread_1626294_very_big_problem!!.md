---
title: "very big problem!!"
date: 2010-11-20
forum: General Help
---

### Post by Askalade on 2010-11-20
i got a big problem!! always when i try to install ubuntu 64 bit to my pc it doesn't work. but yesterday i tried again and then tried running it in safe graphic mode. then it worked FINALLY!! but my resolution was 1280x720 i think and my desktop (wallpaper) was not spread over my whole tv. like when you watch a movie, then somethimes you got those black edges. i got the same! but still it was installed so till so far no real problem... but then i tried connecting my internet and it didn't work! (wireless).
my pc stats:
processor: amd phenom 2 3,4 ghz quad core
memory: 8 GB 1333-777 D3
motherboard: asus m4a79XTD evo
graphics: ATI radeon 5970 2GB sapphire
wireless adapter: sitecom Wireless PCI Card 300N-XR WL-181 XR

---

### Post by pete1983 on 2010-11-20
HI Askalade 

In my experience ATI Has bad support for Linux I had to switch to a card that supported open gl standards befor my problem was solved.
But here is something to try go to 

system 
administration 
additional drivers

Then wait for it it should search for a graphics driver for your computer. When it finishes you can select a driver if there is one then reboot and see if that works for you. I am currently looking for a solution for you if you don't hear from me for a while its because I need to leave for a while but I will keep looking.

Good luck
Pete

---

### Post by Askalade on 2010-11-20
yeah i thought of that too but i got no internet connection so i cant do that

---

### Post by Askalade on 2010-11-22
damn i need help!! :(

---

### Post by justin whitaker on 2010-11-22
If you cannot see any wireless networks, then you need to connect to get the drivers for that as well. 

Did you try connecting directly to your router? Most wireless routers have an Ethernet jack on the back in case you want to connect to it directly.

---

### Post by pete1983 on 2010-11-22
Ok i have been looking all over and finally emailed AMD They said and I quote 

" At this time we do not support Linux on most of our products and have no plans to ,we thank you for your interest."

  Sincerely
  Janis A. 

Ok really anyone in the community who can help that would be great and if AMD is reading this I will no longer buy your products YOU CANT EVEN GIVE ME A FULL LAST NAME. GOSH :lolflag:

I will continue to look I am going to inlist a friend who is a open source guru and see what he can find as well.

---

### Post by pete1983 on 2010-11-22
[http://support.amd.com/us/psearch/Pages/psearch.aspx?type=2.4.1&product=2.4.1.3.42&contentType=GPU+Download+Detail&ostype=Linux+x86&keywords=&items=20](http://support.amd.com/us/psearch/Pages/psearch.aspx?type=2.4.1&product=2.4.1.3.42&contentType=GPU+Download+Detail&ostype=Linux+x86&keywords=&items=20)

Ok apparently they saw my anger on there forum Janis A. just emailed me this link the ATI catalyst Drivers for Linux I hope this helps They so lied lol ;)

Good Luck 
Pete

---

### Post by Askalade on 2010-11-24
thanks for the quick response, gonna test the drivers now. but i think it hasn't much to do with amd cause ubuntu runs smooth on my notebook with a amd athlon dualcore. think it's just the ATI graphic card. srry if my english is bad :oops:

---

### Post by blueridgedog on 2010-11-24
Many systems need to be connected to a wired network in order to download drivers for certain wireless network hardware.  I recommend connecting your system to an Ethernet port on your router and then checking for hardware drivers for your display adapter and your wireless Ethernet adapter.

---

### Post by pete1983 on 2010-11-24
AMD owns ATI that was my main frustration, don't worry I am from an English speaking country and still struggle with my own language lol. as for the video issue I have discovered more than once that the video driver screws with other hardware on the computer if it doesn't work right. Here is the Ubuntu wiki for NVIDIA.  

[https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia)

Good luck 
Pete

---

