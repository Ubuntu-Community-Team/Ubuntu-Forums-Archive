---
title: "Lost the 'Network Icon' from within Ubuntu 10.04?!"
date: 2010-08-10
forum: General Help
---

### Post by Saurabhdua on 2010-08-10
Hello There!

Posting this one through Ubuntu 9.04(Thank God, I retained it!).

I somehow accidently deleted the 'Network Icon' from the panel of Ubuntu 10.04. Now Iam unable to find a way to recover that back!?

'Add to Panel' do not shows up Network icon & neither the 'Volume Button'.

Please walk me through the method to get both back within the panel.

Help will be sincerely appreciated.:(

---

### Post by BlazeFire247 on 2010-08-10
The network icon, I believe, is the Notification Area, and the volume is in the Indicator Applet.

---

### Post by Saurabhdua on 2010-08-10
I cannot follow what you tried to convey? How do I recover the 'Network' & the 'Volume' buttons, previously showing up in the panel at the top?

---

### Post by elliotn on 2010-08-10
Try add to panel then choose notification area, restarting the pc use to work for me and I only loose the Icon if I fail to connect a couple of times

---

### Post by dineshs on 2010-08-10
Right click on the top panel-click add to panel-select notification area -click add

---

### Post by Saurabhdua on 2010-08-10
Hello to you all!

Yes Iam able to recover the 'N/W' icon, but what about the 'Volume' button?
Please refer to the attached screenshot & you'll probably find the outcome of my struggle/juggle with 'Add to Panel' & 'Remove from Panel'!:)

---

### Post by Vaphell on 2010-08-10
volume is a part of the indicator applet or whatever it's called. Add that to panel.

---

### Post by Saurabhdua on 2010-08-11
Heartiest Thanks to each one of you!

Ubuntu 10.04 is causing trouble on changing the 'Screen Resolution'.By default, it is set to 1440X900(16:10), text appears so small.

Changing it to 1024X768 causes 'Screen Blackout' in a sporadic fashion.

9.04 so far is the BEST in all aspects. Love it..really!

---

### Post by makecashonline on 2010-08-11
[SIZE=3]
[/SIZE] 	 		 		 		  		   		[SIZE=3]You should check what your interfaces are called with **sudo ifconfig**[/SIZE] [SIZE=3]
Do not make any changes to the **lo**cal interface

[/SIZE]   	[SIZE=3]Quote:[/SIZE]
 	 	 		[SIZE=3] 			 				ken@taylor12:~$ sudo /etc/init.d/networking restart
* Reconfiguring network interfaces... Ignoring unknown interface eth0=eth0. 			 		[/SIZE] 	 	 
[SIZE=3]Network-Mangler should _not_ be running if you prefer to use the **interfaces**  file method. In my experience NM currently causes more problems than it  solves, except for managing "USB mobile phone dongles", which it does  well.

Please confirm that your router is at 192.168.0.1[/SIZE] [SIZE=3]

I can confirm that 10.04 honours a properly constructed [/SIZE] [SIZE=3]**interfaces** file. Spelling mistakes will not be tolerated though.[/SIZE]
 		 	 		 		 		 		 		 		 		 		 		 	 	[SIZE=3]
[/SIZE]

---

### Post by kmcderm133 on 2010-09-07
I have this same problem in 10.04. I'm running on a laptop, so it's important to me to be able to switch to different networks easily. As far as I can tell the Notification Area is working correctly, there's just no icon for the Network Manager. (Another reason this is useful is for wifi signal strength.) Here are my system specs:

  Toshiba Satellite A75-S226
  ~875 MB RAM
  100 GB hard drive
  Atheros "Super G" wireless card
  ATI Mobility Radeon 9000


PS- The battery/power indicator has also disappeared, I can't seem to add it to the NA or    the regular part of the panel.

---

