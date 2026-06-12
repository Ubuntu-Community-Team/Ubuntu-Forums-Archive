---
title: "Install hangs"
date: 2012-02-20
forum: General Help
---

### Post by andywalkernz on 2012-02-20
I have been having some strange problems trying to install Mythbuntu on a new HTPC set up. I am usually pretty good with a bit of trouble shooting & have used Linux exclusivly since going cold turkey on Windows about 4 years ago. However this situation really has got me beat.  
 

 I am trying to install Mythbuntu from a CD onto my new hardware configuration. I get as far as an initial splash screen, then a blinking cursor and the system just seems to hang from there. Sometimes if I leave it long enough the mythbuntu logo comes up. It does not totally freeze because there is some intermittient CD-ROM activiity but I will just remain cycled in that state for hours until I do a hard reboot.
 

 I have tried so many things to find out what is happening, but 1st of here is my hardware profile. 
 

 Motherboard: Gigabye P35C=DS3R (no onboard graphics)
 CPU: Intel Core2 Duo
 8 GB DDR3 Ram
 1 x 2TB HDD
 Graphics: Nvidia 8500GT with HDTV out.  
 Operating system I am trying to load is Mythbuntu 11.10 64bit from a CD.
 

 I am trying to connect it to a HD Sony Wega CRT TV in 16:9 mode via the Y Pb Pr component  cables.
 

 So these are the things I have checked: 
 

 
[LIST]
[*]The CD is fine. I did a integrity 	check on the Mythbuntu CD, plus the disc loads fine on my desktop 	system.
[*]I can boot the whole system into a 	working Mythbuntu installation from an old 80GB back- up HDD that 	has Mythbuntu 10.10 installed. From this state the TV has a good 	clear picture & the DVD drive seems to work fine only there is 	an issue with the sound not working.  	
[*]I have tried connecting a monitor 	via the component HDTV port, the VGA port & the DVI port all 	with the same results.  	
[*]I have tried swapping out the 	graphics card with two other known to be working with Mythbuntu 	graphics cards, a Nvidia 9600GT and an Nvidia 8300GS with the same 	failed results.
[*]I tried installing Mythbuntu onto 	my 2TB HDD inside my desktop computer, then swapping the HDD back 	into my HTPC. It won't boot.   	
[/LIST]
 

 Observations:  
 

 If I press F2 and bring up the command line, I see the same activities repeating. Some of the messages in there I see it says it is skipping non exisistant files from on the CD. It can't access certain files in the /var/ directory and it fails to mount a networked file system. None of that makes any sence to me as I am only trying to do a fresh install from the live CD or run a live session. I can't even get the 1st language selection screen appear.
 

 When booting with the 8500GT graphics card there is less CD activity & the CPU fan stops. When booting with the other graphics cards installed the CD drive seems to get accessed more but the same basic hanging situation occurs.   
 

 I tried booting a Xubuntu 11.10 live CD with a similar result.  
 

 I guess this must be a hardware problem but I can't guess what piece of hardware is at fault.

---

### Post by andywalkernz on 2012-02-22
OK.. after a few days troubleshooting I finally figured this out. I had the wrong type of RAM in the system. My motherboard will only accept DDR3 1066 RAM but I had DDR3 1333 RAM installed. I had checked with the shop I got the RAM from & they told me 1333 RAM will be ok, it will just run at a lower speed. Well, they were wrong. It made my system totally unstable. Although it would sometimes boot & appear ok for some time it could not run the live CD and was ultra slow and prone to crashing. Once I put in some older RAM all the problems were gone & it ran beautifully.

---

