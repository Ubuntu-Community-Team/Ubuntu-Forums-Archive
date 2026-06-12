---
title: "Upgrade Graphics Card?"
date: 2011-08-16
forum: General Help
---

### Post by Levitys on 2011-08-16
Hey guys, 

As some of you know, I have been getting help here for my HTPC. I was having big issues with screen tearing. It wasn’t even watchable. After about 3 days of reading tuts, help forums and such I was finally able to get rid of the screen tearing in ubuntu. It was really just dumb luck. I went into the compiz settings manager and disabled everything desktop effects related and for some reason that ended up taking care of the screen tearing :) YAY!

Now onto my next issue........Lag. 
I have an AMD Black Phenom II x2 3.3Ghz Processor and an Asus MB with integrated ATI Radeon HD 4250. During the watching of a movie in XBMC (or any other play) The movie will pause, go really slow and then attempt to catch up by going really fast. At first it was funny because of the actors faces but the fourth time it happened it wasn’t funny anymore. 

So to my question...
Will upgrading my GPU to say a Nvidia GTX 550 Ti get rid of this problem?
I don’t want to spend the money but i will if I have to.
I know its pry overkill but I’m tired of video issues guys....

Let me know what you think...

Thanks,
Levitys

---

### Post by Vakman on 2011-08-16
What version of Ubuntu are you running?
How did you install your graphics drivers/did you?
Also please post the output of:
```
fglrxinfo
```

---

### Post by pqwoerituytrueiwoq on 2011-08-16
that should be able to run graphic/movies on the integrated gpu
try this befroe getting a new gpu
```
sudo add-apt-repository ppa:ubuntu-x-swat/x-updates;sudo apt-get update;sudo apt-get upgrade
```if you are using the open source drive try the proprietary one and vice versa

My GT 430 works fine only issue i have had is a couple tracks in supertuxcart lag a little (using dvi as i don't have a hdmi screen and i am not getting a hdmi cord and lugging this oversized box to the other end of the house)

---

### Post by Levitys on 2011-08-16
I have installed/reinstalled ubuntu about 4 times now.
I started with 11.04 and now I am currently at 10.04. (less issues)
I am using the proprietary driver. 
I tried installing the open source driver but i kept having problems.
See my htpc is directly connected to my tv via HDMI.....Its my only monitor and unless I install the proprietary driver my screen is all jacked and cut off.
When I installed the open source driver the ubuntu screen at startup was MASSIVE and It wouldnt load the os. i followed a wiki. but the second i install fglrx my screen is great.

Im not at home right now but i will get that info as soon as i can :D
Thanks for your help guys :)

one more note:
For some reason my 1080p doesnt look very good. its VERY pixely. 
almost like watching tv :/ 720p is great.

Thanks guys :D

I will get back to you ASAP. :D

---

### Post by pqwoerituytrueiwoq on 2011-08-16
i know when i made my mom's computer (integrated ati 3000) the resolution is best with vga and worst with hdmi while my discrete graphics card is the opposite
since you are on 10.04 the command i gave you should be very useful

---

### Post by Levitys on 2011-08-16
> **pqwoerituytrueiwoq said:**
> i know when i made my mom's computer (integrated ati 3000) the resolution is best with vga and worst with hdmi while my discrete graphics card is the opposite
since you are on 10.04 the command i gave you should be very useful

i am a little scared to run this code lol could it bring the screen tearing back or worse?

> **Thisislaw said:**
> What version of Ubuntu are you running?
How did you install your graphics drivers/did you?
Also please post the output of:
```
fglrxinfo
```

here is the ouput you asked for:
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Radeon HD 4250
OpenGL version string: 3.2.9756 Compatibility Profile Context

---

### Post by pqwoerituytrueiwoq on 2011-08-16
it will just update the video driver
if it screws up 
```
sudo apt-get install ppa-purge
sudo ppa-purge ppa:ubuntu-x-swat/x-updates
```

[http://bigbrovar.aoizora.org/index.php/2010/01/10/how-to-safely-remove-ppa-repository-from-ubuntu/](http://bigbrovar.aoizora.org/index.php/2010/01/10/how-to-safely-remove-ppa-repository-from-ubuntu/)

---

### Post by Levitys on 2011-08-16
ok its doin its thing now..........................say a little prayer for me. lol

---

### Post by Levitys on 2011-08-16
ok it seems fine to me......i didnt notice any difference. didnt lag but it doesnt all the time.....
need long term testing........ill let u know,

still though my 1080p looks bad.......i dont want to say blurry but theres all these tiny little dots everywhere that u can see. i dont know how to describe it.........pixelated? almost like ur watchin a vhs or somethin lol.............. any suggestions?

not sure if it changes but heres the output after the update.....
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Radeon HD 4250  
OpenGL version string: 3.3.10362 Compatibility Profile Context

---

### Post by pqwoerituytrueiwoq on 2011-08-16
care to post your board model number?
```
sudo hwinfo --bios | grep "    Product: "
    Product: "System Product Name"
    Product: "**M4A79XTD EVO**"
```edit
the driver got you got a OpenGL bump 3.2 to 3.3
edit
if you upgrade to a nvidia card uninstall the ati driver (fglrx) before you plug the card in then install the nvidia driver (nvidia-current)

---

### Post by Levitys on 2011-08-16
> **pqwoerituytrueiwoq said:**
> care to post your board model number?
```
sudo hwinfo --bios | grep "    Product: "
    Product: "System Product Name"
    Product: "**M4A79XTD EVO**"
```edit
the driver got you got a OpenGL bump 3.2 to 3.3
 

 Product: "System Product Name"
    Product: "M4A88T-M LE"

---

### Post by Levitys on 2011-08-16
not sure if this helps but my catalyst version is 10.12
im pretty sure there at like 11 now but not sure how to update :/

---

### Post by pqwoerituytrueiwoq on 2011-08-16
> **Levitys said:**
> Product: "System Product Name"
    Product: "M4A88T-M LE"
asus has this info on the gpu
[QUOTE=http://www.asus.com/Motherboards/AMD_AM3/M4A88TM_LE/#specifications]Integrated ATI Radeon™ HD 4250 GPU
Multi-VGA output support : HDMI/DVI/RGB ports 
 - Supports HDMI with max. resolution 1920  x 1080  @ 60 Hz
 - Supports DVI with max. resolution 2560  x 1600  @ 60 Hz
 - Supports RGB with max. resolution 2048  x 1536  @ 85  Hz
Maximum shared memory of 1024  MB
Dual independent displays support with HDMI/DVI and D-Sub
Hardware Decode Acceleration for H.264, VC-1, and MPEG-2
Blu-ray playback support *1
Supports DirectX 10.1, OpenGL 2.0, Shader Model 4.1, Universal Video Decoder (UVD) 2.0[/QUOTE]

---

### Post by Levitys on 2011-08-16
do u see something in there that would point to my 1080p problem?

---

### Post by pqwoerituytrueiwoq on 2011-08-16
you can try it with graphic effects off but aside from that i don't know what else yuo can do 
off:
```
metacity --replace &
```on:
```
compiz --replace &
```toggle script:
```
#!/bin/bash
if [ 0`pidof metacity` -gt 0 ]; then
    compiz --replace &
else
    metacity --replace &
fi
exit
```
edit
may have better luck here (also check stickes)
[http://ubuntuforums.org/forumdisplay.php?f=334](http://ubuntuforums.org/forumdisplay.php?f=334)

---

### Post by Levitys on 2011-08-16
So after all this.... ;)

Do you think that upgrading my graphics card would take care of my problems?
Or do you think that I would be in the same boat?

---

### Post by Levitys on 2011-08-17
Bumperoo

---

### Post by pqwoerituytrueiwoq on 2011-08-17
you can upgrade it not sure what else you can do at this point
idk if this card will work for you but it is on sale you should research it before buying [Promo Code: EMCYTZT675]("http://%22http://www.newegg.com/Product/Product.aspx?Item=N82E16814102882") 5$ code expires early Friday

---

### Post by Levitys on 2011-08-17
> **pqwoerituytrueiwoq said:**
> you can upgrade it not sure what else you can do at this point
idk if this card will work for you but it is on sale you should research it before buying [Promo Code: EMCYTZT675]("http://%22http://www.newegg.com/Product/Product.aspx?Item=N82E16814102882") 5$ code expires early Friday

THANK you so much man you have been a huge help.......not quite sure what im going to do yet.
probably going to do like u said and do some more research and weigh my options.
i really appreciate your time.

oh and also the update u had me do totally took care of lag  issues. runs like a charm......just not 1080p.

thanks again!
levitys

---

