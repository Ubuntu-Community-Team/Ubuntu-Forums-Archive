---
title: "RAM dead? Motherboard dead? CPU dead?"
date: 2010-05-05
forum: General Help
---

### Post by ubunterooster on 2010-05-05
I used my old RAM in my new PC. The RAM was rated for 533mhz but the motherboard could not run it below 667mhz.

Today I was using tdfsb (3D file system browser) in my music folder (which has a lot of files/folders) the PC froze. After 20min I pulled the plug and it started back up properly. After some updates later that day, I tried to reboot. All it did was shut down and light up the fanlights instead of restarting. I tried resetting the battery. With the old motherboard, bad RAM would cause beeps and I hear no beeps. The board is a Gigabyte GA-MA785GM-US2H. The CPU an Athlon II x2 255. Could someone please find out if RAM failure would cause beeps or not.

---

### Post by ubunterooster on 2010-05-05
When I press the power button power goes to the HDD (I hear it spin), CPU (if I turn the computer off the heat-sink is slightly warm), motherboard (the Ethernet lights come on), and fans. There is not the usual beep it makes as it enters BIOS.

I swapped the RAM out with some other sticks so this appears not to be the problem; I also swapped the CPU, no difference. And of course I reset the battery again.

---

### Post by realzippy on 2010-05-05
Would run a LiveCd....

---

### Post by Ad@m on 2010-05-05
I would suggest you power the pc on with the bare minimum hardware and see if it works.

CPU + motherboard
1 stick of memory
onboard gfx
power supply

Fully disconnect everything else.

Btw what is your hardware, it would help to know and remember to include the power supply.

Are you able to enter the bios?

---

### Post by pricetech on 2010-05-05
You said you swapped in other RAM.  Known good ??

The symptoms you're describing come down to either motherboard or CPU.  The CPU could be heating up without doing its job.

I'm making a couple of assumptions here;
Onboard sound, video, NIC, right ??
You said no beeps, but I've seen some motherboards that don't have a speaker on them.  Yours does, and you've heard it beep before right ??

Probably not the power supply, but I wouldn't rule it out just yet.

Try disconnecting everything but the MoBo and see if you get any response then.

Good luck with it.

---

### Post by ubunterooster on 2010-05-05
Still not entering bios


> [Patriot Torqx M28 Series  PTX128GS25SSDR 2.5" 128GB SATA II Internal Solid State Drive (SSD)]("http://www.newegg.com/Product/Product.aspx?Item=N82E16820220412")
 2              [SAMSUNG Spinpoint F3EG HD203WI 2TB  5400 RPM SATA 3.0Gb/s 3.5" Internal Hard Drive -Bare Drive]("http://www.newegg.com/Product/Product.aspx?Item=N82E16822152202") 
 [GIGABYTE GA-MA785GM-US2H  AM3/AM2+/AM2 AMD 785G HDMI Micro ATX AMD Motherboard]("http://www.newegg.com/Product/Product.aspx?Item=N82E16813128394")
[COOLER MASTER Silent Pro 600  RS-600-AMBA-D3 600W ATX12V V2.3 SLI Certified CrossFire Ready 80 PLUS  Certified Modular Active ...]("http://www.newegg.com/Product/Product.aspx?Item=N82E16817171036")
 [AMD Athlon II X2 255 Regor 3.1GHz  Socket AM3 65W Dual-Core Desktop Processor Model ADX255OCGQBOX]("http://www.newegg.com/Product/Product.aspx?Item=N82E16819103844")


---

### Post by 3rdalbum on 2010-05-05
Did you follow the instructions in the manual for how to reset the CMOS memory? Just pulling out the battery doesn't always do the trick; you often have to remove the battery and move a jumper for ten seconds, replace the jumper where it was and put the battery back in.

Try booting with only one RAM stick in. If it doesn't boot, then move the stick to a different slot, or even to a different channel. If you get results, then one of the slots is faulty.

And remove all PCI and PCI-E cards except for your graphics card, and try again.

---

### Post by ubunterooster on 2010-05-05
I removed everything including CPU. Same as before.

So I stuck the CPU in and pressed the button. The familiar "bad RAM/ Missing RAM" beep. So I turned it off and stuck the RAM in and it entered BIOs.

I then rebooted with everything stuck back in and I am typing from said computer

:popcorn:

Could it have been a mis-seated CPU?

---

### Post by Ad@m on 2010-05-05
A partially in memory module could also cause the same type of issue.

At least you fixed the problem :-)

---

### Post by ubunterooster on 2010-05-05
The new memory is due to arrive this week already so I hope that is what it was. Which reminds me I also need a sata drive enclosure in case I need to access the files when the desktop is not working. Off to newegg.

Thanks to all of you.

---

### Post by pricetech on 2010-05-10
> **ubunterooster said:**
> Off to newegg.

Can you pick up a couple of things for me while you're there ??  (grin)

Seriously, glad you got it working.  Mis seated components are always frustrating.

---

### Post by ubunterooster on 2010-05-10
Thanks, Pricetech

---

### Post by pricetech on 2010-05-10
Not sure how I helped, but you're more than welcome Rooster.

---

