---
title: "Laptop overheating"
date: 2009-09-01
forum: General Help
---

### Post by Megatron3000 on 2009-09-01
Hello, Since a few weeks, my laptop gets a lot hotter then it used to do. This started when i was still using XP (that is, up to last week), and persists in Ubuntu. I haven't gotten any warning messages, but it's a worrying amount of heat that gets produced. I don't use it on a bed or anything that blocks the air flow to the fan (though i have in the past). Does anyone have some tips about cooling it down (in a more permanent way then using the fridge). I would not like to see it go up in flames. thanks!   my machine is a Toshiba Sattelite A200 1H2 with an Intel Duo Core 1,66GHz processor, 2GB ram, 180 GB HD

---

### Post by P4man on 2009-09-01
I suppose you're only joking, but do not put it in a fridge! Condensation will kill the hdd (if not the rest).

Can you add the "CPU Frequency Scaling Monitor" to your gnome panel and see if cpu scaling is still working?

---

### Post by CaesarLike on 2009-09-01
Hi Megatron,

For serious notebook cooling you need a cooling stand or pad.
Take a look at the link for an Australian online store which sells them.  I assume an online store in your country would sell similar devices.


[http://www.pccasegear.com/index.php?main_page=index&cPath=207_142]("http://www.pccasegear.com/index.php?main_page=index&cPath=207_142")

Of all the models on that page this is the one I would get if I needed one.

[http://www.pccasegear.com/index.php?main_page=product_info&cPath=207_142&products_id=12081](http://www.pccasegear.com/index.php?main_page=product_info&cPath=207_142&products_id=12081)

---

### Post by earthpigg on 2009-09-01
hi,

take it apart and clean the dust out. that will help it out quite a bit.

if you want to install software needed to detect the temperature:

> sudo apt-get install lm-sensors

to configure it:

> sudo sensors-detect

to read the temps:

> sensors

---

### Post by Megatron3000 on 2009-09-01
cpu scaling frequency seems to be doing fine, sits on 1GHz mostly, and occasionally pops to 1,67

---

### Post by hockeytux on 2009-09-01
Opening it up and cleaning the dust out should make a real difference. Especially if you notice a gradual change of it getting hotter and hotter that is most likely contributing to it.

---

### Post by Megatron3000 on 2009-09-01
I have installed the sensors thingy, but it does not seem to work. The adapter packages are loaded, and the command line inserted    
i got this     
 
Now follows a summary of the probes I have just done.
  Just press ENTER to continue:   
Driver `coretemp' (should be inserted):  
  Detects correctly:    
 * Chip `Intel Core family thermal sensor' (confidence: 9) 

  I will now generate the commands needed to load the required modules. Just press ENTER to continue:   
To load everything that is needed, add this to /etc/modules:  
#----cut here----  
#Chip drivers 
 coretemp 
#----cut here---- 
 Do you want to add these lines automatically? (yes/NO) 
 jef@Megatron3000:~$ sudo gedit /etc/modules 
jef@Megatron3000:~$ sensors 
No sensors found! 
Make sure you loaded all the kernel drivers you need. 
Try sensors-detect to find out which these are. 
jef@Megatron3000:~$   

I'll try cleaning the fan thanks! oh, and sorry for the non-using of quick reply, something won't cooperate

---

### Post by Megatron3000 on 2009-09-01
Sensors does function by now, while not doing anything too fancy (just having firefox open), the temperature reads 62°C for CPU0 and 63 for CPU1 (it's an Intel Duo Core 1.67GHz). According to the program, 85 is my death point. I've tried opening and cleaning, but there's no access point for the fan, and one for the processor that does not really seem to offer a lot of access. The only option is taking it all apart, and because that didn't go to fluently, i haven't continued. I did vacuum the fan area from outside, but it still seems to run more or less continually, breathing out hot air. I suppose the only option is to have it cleaned out by someone who knows how to take this kind of machine apart, unless someone here has experience with opening up a Toshiba Satellite. And otherwise the cooling base, but since it's a relatively new issue, i'd rather just find a way to undo it.

---

### Post by P4man on 2009-09-01
if it "breaths out" so much hot air, that seems to suggest the fan is working well. Your temperatures are also not too terrible, though a tad high. Can you check the temps of your videocard? If its an nvidia card and you installed the drivers, you can check it in System > administration > nvidia x server settings > thermal monitor

another thought: is it possible its the battery that is heating up?

---

### Post by Megatron3000 on 2009-09-01
the battery is quite cool, the main points of heat are around the ram and around the processor. but the whole top feels rather warm and the bottom much more, and both of them much more than a few months ago. I don't know about the graphics card, it's an older Ati Radeon and i haven't figured out what the good driver for that is yet. I'm on the standard Xorg driver now, and there's no 3D support, which is another inconvenience (if anyone has a tip here...)

---

