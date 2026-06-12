---
title: "Ubuntu on a HTC Mogul? Ubuntu on smartphones?"
date: 2010-05-09
forum: General Help
---

### Post by Nick_Djinn on 2010-05-09
If there is a better board for this, please redirect it after I get some replies. Thanks.


So I am poor....I finally got a smart phone, an HTC mogul which was pretty neat in its day but an older generation device these days.

So this device has a 400 mhz microprocessor, and only 64 mb ram.....not great, but better than any 'phone' I have ever owned. It does have an additional 246mb ROM (read only memory)...so I actually have 310mb of memory?

The cool thing is that I can get Wifi internet.....so even if I dont pay for a data plan I can still check email and keep up with my customers (I sell body jewelry like plugs and hand carved balicrafts and Thai stonework) at my school and other hotspots.

The battery life sucks on this, so I got the expanded battery that doubles its life if not more. 3000 mah..


So here are some questions.....


1. Can I install an Ubuntu or linux based operating system on this over windows mobile 6? Are there any obvious advantages to doing so? I would like to try it at least, as long as I wont loose too much functionality....and I dont really give a **** about sprint TV or music stores....I dont pay for music except small independent artists. I do want to be able to connect to wifi and log into social networking sites and ebay or etsy.com. I would like to avoid advertising pop ups and stuff like that.....and Ubuntu is my favorite but are there some alternatives? Ubuntu mobile is gone now?

2. I hear there is a cult following for this device, especially in the open source world....So how can I tweak this to improve performance and battery life....I will get more life with the new battery, but I would like to increase it further...make wifi easier to turn on and off? Avoid connecting to the net via Sprint when I have wifi, or ONLY allowing wifi? Getting rid of needless apps? Adding open office? Turn off GPS? I do want messenger on.

3. Can I use this device to connect my computer to the internet? There are 2 ways I would like to do this...one would be if I get the data plan, the other would be dialup with free nights and weekend minutes.....I would probably use the data plan because its a better deal, but knowledge of both would be helpful.

4. Can I get Ubuntu to play nice with this device when I synch it with windows mobile? Can I do the same if I use a linux OS?

5. Are hardware upgrades possible for this device?

Any other tips and tricks for this device?

---

### Post by Nick_Djinn on 2010-05-09
Is there a better board than this one for this? I think it will get buried and left unanswered here. 


Anyone have any experience with Linux on any smartphone?

---

### Post by Nick_Djinn on 2010-05-09
Does the quick reply button work for anyone else? It doesnt for me.



Anyone know anything? Is this the right board??

:guitar:

---

### Post by fsubartender on 2010-11-08
Ok. I got zubuntu to boot, but need help to get the touchscreen to calibrate.

I think I need the proper default.txt or startup.txt

I have been using a colaboration of things.

The default.txt from the android titan-full-23.03.2009.....

# set RAMSIZE 0x06400000
# set RAMADDR 0x1000000
set MTYPE 1463 
set KERNEL zImage
set initrd initrd.gz
#
# The following kernel parameters are useful
# ppp.nostart				 - Set ppp.nostart=1 to disable starting the ppp connection on boot
# msm_sdcc.msmsdcc_fmax      - The maximum frequency (in Hz) used by the SD controller
# pm.sleep_mode              - The mode used when the phone is off 
#                              0=Power Collapse Suspend, 1=Power Collapse, 2=Apps Sleep, 
#                              3=Slow Clock and Wait for Interrupt 4=Wait for Interrupt
#                              Default is 3, use 0 for best power savings
# board-htcvogue.panel_type  - Panel type used to power the panel off and on
#                              1=Hitachi 2=Topoly 3=Samsung
# clock-7x00.mddi            - MDDI clock (try 0xa51 or 0xe2c)
# clock-7x00.ahb_div         - Advanced Host Bus divider, default is 4 
#                              2 is faster but uses more power
# clock-7x00.a11             - ARM11 clock speed in MHz, best to leave this alone
# lcd.density                - Defaults to 160, 128 shows more on screen
# vogue-ts.XMIN              - xmin value for the touchscreen calibration. Also YMIN, XMAX, YMAX, PMIN, PMAX.
#
# Probably the only one of these you will need to change is the panel type, NZ Vogues seem to all have type 1
# US Sprint vogues usually have type 2 or 3 I think.
# Make sure you add these between the quotes on the following line and that your editor hasn't split the line up.
set cmdline "ppp.nostart=0 mddi.width=240 mddi.height=320 lcd.density=110 msm_sdcc.msmsdcc_fmax=32000000 pm.sleep_mode=0 clock-7x00.ahb_div=2 no_console_suspend"
boot
# board-htctitan.panel_type=4

The haret version 0.5.2

The initrd.gz from heck I dont know...it is the 1.8mb version

The rootfs.img is the zubuntu 

and the zImage from kaiser-buntu.

I am a noob to this stuff. I do have a dual booting laptop(win7/linuxmint) if work needs to be done in either system.


Any help?

---

