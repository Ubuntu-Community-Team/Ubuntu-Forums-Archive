---
title: "Desktop Effects Problem's"
date: 2009-11-21
forum: General Help
---

### Post by jibby_1 on 2009-11-21
Hi,:D
 

 This is my first post and I have only been using Ubuntu 9.10 for 2 days so I hope I don't offend anyone if I use the incorrect terminology. Well the problem is that I what to get the cool visual's working so I looked at some guides online and they all suggested that I use conpiz, so I went ahead and installed it I tried to use some of the animations but they did not work. Then I went to visual affects and try to enable normal and extra settings but it came up with this message “Desktop effects could not be enabled”.  So I thought it might be a driver issue so I used envy-ng to get the right driver by the way I am using a 4200 on-board graphics ati and still the cool visuals do not work.
 

 I then ran compiz check and it came up with one error heres what it say:
 

 Gathering information about your system... 
  
  Distribution:          Ubuntu 9.10 
  Desktop environment:   GNOME 
  Graphics chip:         ATI Technologies Inc Device 9710 
  Driver in use:         vesa 
  Rendering method:      AIGLX 
  
 Checking if it's possible to run Compiz on your system...  [SKIP] 
  
  Checking for hardware/setup problems...           [SKIP] 
  
 At least one check had to be skipped: 
  Error: vesa driver in use  
 

 And that is where I am right now can anyone help me get the cool desktop effects lol

---

### Post by Uncle Spellbinder on 2009-11-21
After a quick Yahoo and Google search for 'Compiz vesa', I see the following statement a lot...

"Compiz can't be run using VESA or VGA divers."

---

### Post by Johnneylee on 2009-11-21
You can try this
```
sudo apt-get install xorg-driver-fglrx fglrx-control
```

---

### Post by jibby_1 on 2009-11-21
> **Uncle Spellbinder said:**
> After a quick Yahoo and Google search for 'Compiz vesa', I see the following statement a lot...

"Compiz can't be run using VESA or VGA divers."

  	 	 	 	 	 	  Thanx for the info. I got envy-ng to change the driver to fglrx which should be good to use with compiz, but now its says I have no rendering method, lol I dont know what that means sorry I am such a noob. Heres the code it gives me:
 

 Gathering information about your system... 
  
  Distribution:          Ubuntu 9.10 
  Desktop environment:   GNOME 
  Graphics chip:         ATI Technologies Inc Device 9710 
  Driver in use:         fglrx 
  Rendering method:      None 
  
 Checking if it's possible to run Compiz on your system...  [SKIP] 
  
  Checking for hardware/setup problems...           [SKIP] 
  
 At least one check had to be skipped: 
  Error: No rendering method in use (AIGLX, Xgl or Nvidia)  
  
 I have a few questions:


Which method should I use?
How should I install it?

---

### Post by jibby_1 on 2009-11-21
yes I got it workin thax for the help this os looks so cool now

---

### Post by Johnneylee on 2009-11-21
Try this maybe?
```
sudo apt-get update
sudo apt-get install linux-restricted-modules-$(uname -r)
sudo apt-get install xorg-driver-fglrx fglrx-control
```
Once the above packages are correctly installed, run these commands:

```
sudo aticonfig --initial
sudo aticonfig --overlay-type=Xv
```

Then go back and edit xorg.conf with your favorite editor, perhaps:

```
gksudo gedit /etc/X11/xorg.conf
```

and make sure that under the "Device" section, the Driver is set to

```
Driver "fglrx"
```

Reboot. 

Confirm it worked, by issuing the "fglrxinfo" command.

Something like this should be displayed
```
$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON 9700 Generic
OpenGL version string: 2.0.5755 (8.24.8)
```

98% of this post was stolen from [https://help.ubuntu.com/community/BinaryDriverHowto/ATI]("https://help.ubuntu.com/community/BinaryDriverHowto/ATI")

Another option is to download straight from ATI. I did this method with nvidia and haven't had a problem.

[Latest Ati Drivers from ATI how to]("https://help.ubuntu.com/community/BinaryDriverHowto/ATI#Install%20from%20ati.com%20(latest%20version%20of%20drivers)")

---

### Post by jibby_1 on 2009-11-23
> **Johnneylee said:**
> Try this maybe?
```
sudo apt-get update
sudo apt-get install linux-restricted-modules-$(uname -r)
sudo apt-get install xorg-driver-fglrx fglrx-control
```Once the above packages are correctly installed, run these commands:

```
sudo aticonfig --initial
sudo aticonfig --overlay-type=Xv
```Then go back and edit xorg.conf with your favorite editor, perhaps:

```
gksudo gedit /etc/X11/xorg.conf
```and make sure that under the "Device" section, the Driver is set to

```
Driver "fglrx"
```Reboot. 

Confirm it worked, by issuing the "fglrxinfo" command.

Something like this should be displayed
```
$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON 9700 Generic
OpenGL version string: 2.0.5755 (8.24.8)
```98% of this post was stolen from [https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)

Another option is to download straight from ATI. I did this method with nvidia and haven't had a problem.

[Latest Ati Drivers from ATI how to]("https://help.ubuntu.com/community/BinaryDriverHowto/ATI#Install%20from%20ati.com%20%28latest%20version%20of%20drivers%29")

thanx for the link dude i will try it latter on, lol just getting used to the system at the moment ;)

---

### Post by Johnneylee on 2009-11-23
Normally I'd encourage you to explore, but I'm rather sure that video drivers are a priority, at least for me.

It's kind of a first on the todo list for each operating system I install and intend to use for anything graphical.

But who am I to tell another person what to do, explore away.
if you ever have questions, let me know.

---

