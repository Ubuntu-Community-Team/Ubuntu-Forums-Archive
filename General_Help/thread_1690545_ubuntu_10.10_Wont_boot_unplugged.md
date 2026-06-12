---
title: "ubuntu 10.10 Wont boot unplugged"
date: 2011-02-18
forum: General Help
---

### Post by Ger5 on 2011-02-18
Im very new to  this.However i have got rid of  windows 7 of my laptop and installed  ubuntu 10.10 So for the past week  or so have done a lot o testing and  stuff.laptop i have is hp pavilion  tx 2000 model tx 2130ea.
Problem i have is laptop wont boot when unplugged but boots when plugged   in.When it  starts up you can hear the logo music but screen remains   black.
Now i have found what the problem is after hours of fault finding.But dont know how to fix
Ubuntu detects the additional drivers to download wireless driver etc   and a couple of nvidia 2d/3d drivers so its when one these nvidia  drivers  are in stalled is what causes the problem when booting up  unplugged.No  problem when plugged in.At the moment i just have not  installed these  nividia drivers and all is good just wondering is there  a fix for this.
 Graphics Card Nvidia Geforce Go 6150

---

### Post by jerrrys on 2011-02-20
i don't understand the connection between power supply and drivers

---

### Post by Ger5 on 2011-02-20
either do i and 			 		   		 		 		yes it is a  strange one.when unplugged it boots shows the ubuntu screen little dots  changing colour loading fine, just when its about to switch to the logon  screen the screen goes blank.However i can hear the logon music and  even dough its a blank screen i type my user name and password and the  screen still stays blank but i can hear it loading up to the desktop  screen.

Now when i boot plugged in no problem at all . when its fully booted up  removing the power cord has no effect stiil ok and even when it goes  into hibernation and i log back on no problem. i have tryed a lot of  basic stuff. i do have all power setting  ie dim etc to a minimum.i also  have tryed  reinstalled ubuntu no joy also i tryed updating and  even  not updating just loading the basic os still no joy . .this only accrues  when i install the nvidia driver. if i dont install the driver it boots  fine both unplugged and plugged i have also tryed other os ie linux  mint and the same problem happens.

i reinstalled the nvidia driver today and still the same ie when  unplugged it boots shows the ubuntu screen  little dots changing colour  loading fine, just when its about to switch  to the logon screen the  screen goes blank.However i can hear the logon  music in tne back ground  now at this stage if i hold down the (fn) function button along with  the f5 botton( which its second function is to put the laptop into  hibernate) and when both buttons  are released about one second later  the laptop goes into sleep mode fine and then i hit any key to bring it  out of sleep mode ok. now the interesting bit.when it comes out of sleep  mode i can see the logon screen type in password and every thing works  fine .a rather long way round to boot laptop unplugged from mains  strange.

---

### Post by jerrrys on 2011-02-21
would you please to pull up 'hardware drivers' and post a pic of what your options are

---

### Post by aeiah on 2011-02-21
the only thing i can think of is that your graphics card goes into a power saving mode when on battery power, and this power saving mode isn't fully compatible with the nvidia drivers. perhaps there's an option in nvidia-settings for turning off the power saving mode? it may not be ideal, but should help troubleshoot the problem

---

### Post by Ger5 on 2011-04-01
here is pic of options on drivers

---

### Post by Ger5 on 2011-04-01
Cant seem to find any setting on the nvidia card

---

### Post by veggen on 2011-04-01
I had the exact same problem with Hp EliteBook 8730w and Win7. I solved it by installing some diagnostic software (!) from Hp. I never ran it or used it, just installed it.
I think it can hardly help with Ubuntu, but I'm just saying it's some issue with Hp.
And yes, it seems to be related to graphic card somehow... Try tinkering with it in any way you can come up with.

---

