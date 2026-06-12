---
title: "having issuse with my laptop freezing more and more frequently"
date: 2010-04-24
forum: General Help
---

### Post by inoh on 2010-04-24
hi, i have an compaq cq60

lately while converting video to dvd with ffmpeg or devede, watching multiple videos online, or restarting dbus from command, my laptop freezes and cannot recover.  i simple have to do a hard shutdown and restart the laptop.  sometimes when it freezes, the and hdd led will steadily blink once per second.

any ideas on how to fix this or find out whats causing it?

thanks in advance

---

### Post by KeyserSoze93 on 2010-04-24
Do the power / capslock / scroll lock and numlock lights flash when it freezes?

If they do flash, then it could well be the RAM.

I know someone who had this issue, and when I ran the Ubuntu memtest86 (found on the GRUB menu below all your kernels), it show a ton of errors.

---

### Post by inoh on 2010-04-24
that has only happened once.  my laptop boots with all them unlit, and when it freezes none of those keys respond/light up.

ill try running that memtest latter tonight.  maybe i need something new?!?

I just tried encoding with devede and when i cam back three hours later my computer had crashed and simply shut itself down.

---

### Post by shaka_zulu on 2010-04-24
Maybe you should tell us your laptop configuration. Do you have SWAP memory? How much RAM do you have? Does your laptop overheating?

---

### Post by inoh on 2010-04-24
dont know what swap memory is. 2 gigs ram. i use a cooler pad to prevent overheating.

just tried to run memtest86 and memtest86 serial console. both crashed.

im going to shut this down till tomorrow and try the test again just incase it is overheating.

---

### Post by shaka_zulu on 2010-04-24
Look if you start few flash application, video coding and something third CPU goes to 100% for sure. There is also possibility da if you do not have SWAP memory all your processes take more then your 2GB RAM and system crashes.

---

### Post by tgalati4 on 2010-04-24
Laptops are not meant for doing real work.  Encoding video gets the CPU super hot.  You are probably getting thermal safety shutdowns.  Boot into your BIOS and look for thermal shutdown settings.  Take note of them.

Install a temperature monitor on your task bar so you can watch the temperature of your CPU and GPU while you encode.  If the temps get close to the shutdown temperature then you know what is going on.

It could also be a battery problem.  High CPU and heat loads increase current draw.  It could be your power circuitry shutting down with a resettable current fuse.

Get a big-asse fan and blow on your computer while using it for desktop work.

---

### Post by inoh on 2010-04-25
ok.  i get what is being said, but i have done this stuff for a while with no problems.  then the problems begin occurring and getting more frequent.

now i understand the issue doing too much at once, therefore i only do one of these big tasks at a time to prevent using too much resource.  the cooling pad basically stopped any overheating issues, which had been a problem in the past.

i have shutdown and let sit for hours to insure everything had indefinitely cooled off.  then tried several times to run memtest86.  dont see how there could be an issue just running a basic system test.  i walk away for some time knowing its going to be a while, and upon returning about a little over a half hour later the laptop has shutdown and i have no results to view.  i watch everything start ok.  it doesn't seem to shut down all the way because when i press the power button again it loads directly to grub.  no bios info and what not at the bottom.  could i be doing something wrong?

now im going to look into the thermal settings and how to get the monitors.

one more thing, what is SWAP memory and can i just use it? (something like setting up a ram drive or virtual memory?!?)

---

### Post by shaka_zulu on 2010-04-25
SWAP is basically what the virtual memory on WIndows is. But SWAP is separated partition and not the part of exciting one. How old is that computer?

---

### Post by inoh on 2010-04-25
roughly 20 months.  know of any good guides to setup SWAP???

i turned off compiz and restarted.  everything is fast again, my computer seemed to slow down with each kernel upgrade after 2.6.31-14.  i saw so many other people with issues from the kernel i assumed it was the kernel.  anyways im currently a little past 75% with devede.  monitoring cpu speed and temp.  temp is a bit high 96C TZS0 and 87C TZS1.  looks like i need a better cooling pad.

no freezing or slow down with anything though i am scarred to push any more.

thanks for the help.

cant believe compiz did this.

going to try memtest86 again when devede is done.

---

### Post by shaka_zulu on 2010-04-25
type in terminal: top and make print screen and put it here.

---

### Post by inoh on 2010-04-25
ss is attached. just finished devede, all went smoth

according to top i do have swap

---

### Post by shaka_zulu on 2010-04-25
> **inoh said:**
> ss is attached. just finished devede, all went smoth

according to top i do have swap

If i am not wrong everything seems just fine. I am almost positive that if you start a lot of processes, especially demanding ones, and since you have laptop it is possible that you have just exaggerated. Video rendering, video manipulation, burning huge file is just to much for laptop. So slow down a bit and everything should be fine. :)

---

### Post by inoh on 2010-04-26
ok, i just finished attempting memtest86 and the bios diagnostics memory test.

both crashed half way through.  now i know i have issues overheating, cant use compiz, and need new memory.  going to make a trip to the store and have them check the memory too.  everything is still under warranty so they might replace it.

thanks again for all the help. (hopefully the hdd checks out fine when i run those tests.0

---

### Post by shaka_zulu on 2010-04-26
No problem. There is always possibility that hardware has some bad moments.

---

### Post by inoh on 2010-04-26
yup, hdd check sucessful from live cd, crashed from bios diagnostics.

i do have one more question if you dont mind.  i have been looking into the samsung r580.  even though it is a laptop, is it capable of handling what i want to do?

---

### Post by shaka_zulu on 2010-04-26
I really do not know how to help. Try with reinstalling whole OS but this time use some other CD and use new one. Always be aware that Flash applications are extremely resource consuming like all other stuff you want to do at once. Might be problem with RAM or maybe some video card failure or maybe neither of this :)

---

### Post by Mark Phelps on 2010-04-26
If you're regularly exposing your laptop internals to temps like 96 Centigrade, it's likely you're damaging the hard drive as well.

Hard drives, especially those in laptops, are sensitive to overheating.  This will damage the drive over time, causing bad sectors, and those will cause the drive writes to fail. The effect will be one of your drive slowing to a crawl because of repeated attempts to write to failing sectors.

---

### Post by inoh on 2010-04-27
ok, now i understand one way to avoid this is to simply get a gaming laptop, since they are designed not to get as hot when put under a real demand.  are there any cooling pads that will significantly prevent overheating?

thanks again for all the help.  turned out the heat sink needed to be replaced.

---

