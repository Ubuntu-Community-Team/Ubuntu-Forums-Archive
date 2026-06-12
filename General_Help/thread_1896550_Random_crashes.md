---
title: "Random crashes"
date: 2011-12-17
forum: General Help
---

### Post by saxmax on 2011-12-17
Hi to all,
I'm pretty new to linux, i have a old acer travelmate 2600 into which i installed the xubuntu version 11.10.
I am experiencing some random and inexplicable crash/freezings.
I have just installed it, i did not install other programs, i just did all the updates the update manager said to try to solve things (yes, it freezed even "out of the box" right after installation).
I have installed on the same pc other versions of linux (lubuntu, puppy, mint) but these other versions did not freeze. Are there known issues which cause freezing i could solve? 
Is there some terminal output i should post so that someone could figure what's happening?

Thanks in advance for any help [-o<

---

### Post by BC59 on 2011-12-17
Sometimes the crashes occur because of a bad installation. 
Check if you left enough space for your system partition. 
Install if you didn't do it already, the proprietary ATI Radeon driver.

---

### Post by saxmax on 2011-12-17
The partitition in which i installed it has some 13gb space free left, i suppose it is enough to make it work. I'll try to install the ati drivers..

---

### Post by saxmax on 2011-12-17
Ehrm..
sorry for it, but.. I can't figure what there is to do. :-(

Here ([https://help.ubuntu.com/community/RadeonDriver#Removing_the_proprietary_fglrx_driver](https://help.ubuntu.com/community/RadeonDriver#Removing_the_proprietary_fglrx_driver))
it says many things i don't understand.

It seems, if i'm right, that my card is supported fully with 3d acceleration.. Is there a need for proprietary drivers? Where do i get them?

Here is the output of the teminal for lspci -nn | grep VGA :
01:05.0 VGA compatible controller [0300]: ATI Technologies Inc RS300M AGP [Radeon Mobility 9100IGP] [1002:5835]

Sorry for this, but i'm not so expert with linux..

---

### Post by BC59 on 2011-12-17
Why don't you try to install the driver from the recommended drivers? Open the application **additional drivers** and activate ATI (not the updates only the driver). Reboot and check if it's better.

---

### Post by saxmax on 2011-12-17
In additional drivers there is no option for ati drivers..

The fglrxinfo command does not function, it says 
fglrxinfo: command not found

So i suppose there is no proprietary driver installed.

I'll try to follow this guide to see if i can install them manually:
[https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)

If you or others know a better way please tell me, i'll gladly appreciate any help (this way seems a bit complicated :-) )!

---

### Post by BC59 on 2011-12-17
You can install the application Synaptic from Ubuntu Software center. Open it and search for fglrx. Install the driver corresponding for your computer, 32 or 64 bits. The 32bits is the fglrx:i386.

---

### Post by saxmax on 2011-12-18
After the installing of the drivers you pointd to everything now seems ok. I don't know if is the driver change or the fact i put 2 gb ram instead of 512 mb into the pc but for now i have no freeze. I'll keep updated tomorrow, i hope. Thanks for your help!! :-D

---

### Post by saxmax on 2011-12-19
Nope, it is not working.. The desktop screen now has no background, icons and all are present, but the configuration program (catalyst) tells me no driver is installed... Is there a way to know what kind of driver is the system using?

---

### Post by BC59 on 2011-12-19
```
lspci | grep VGA
```

---

### Post by saxmax on 2011-12-19
Ok, seems the correct driver is installed:

01:05.0 VGA compatible controller: ATI Technologies Inc RS300M AGP [Radeon Mobility 9100IGP]

But why catalyst control center is not working? When i try to start it i t says :

"There was a problem initializing Catalyst Control Center Linux edition. The causes could be the following.

 Without an installed graphics driver or the driver AMD AMD does not work properly.
 Please install the controller to suit your AMD AMD hardware or configure using anticonfig. "
anticonfig does not seem to be a valid command,and fglrxinfo
gives the following output.. 
Dunno... What's happening?

X Error of failed request:  BadRequest (invalid request code or no such operation)
  Major opcode of failed request:  136 (GLX)
  Minor opcode of failed request:  19 (X_GLXQueryServerString)
  Serial number of failed request:  12
  Current serial number in output stream:  12

---

### Post by BC59 on 2011-12-19
> **saxmax said:**
> Ok, seems the correct driver is installed:

01:05.0 VGA compatible controller: ATI Technologies Inc RS300M AGP [Radeon Mobility 9100IGP]

But why catalyst control center is not working? When i try to start it i t says :

"There was a problem initializing Catalyst Control Center Linux edition. The causes could be the following.

 Without an installed graphics driver or the driver AMD AMD does not work properly.
 Please install the controller to suit your AMD AMD hardware or configure using anticonfig. "
anticonfig does not seem to be a valid command,and fglrxinfo
gives the following output.. 
Dunno... What's happening?

X Error of failed request:  BadRequest (invalid request code or no such operation)
  Major opcode of failed request:  136 (GLX)
  Minor opcode of failed request:  19 (X_GLXQueryServerString)
  Serial number of failed request:  12
  Current serial number in output stream:  12

The command should be aticonfig not anticonfig

---

### Post by BC59 on 2011-12-19
You can follow the instructions from [here]("http://http://ubuntuforums.org/showpost.php?p=10950714&postcount=334)")

---

### Post by saxmax on 2011-12-27
I'm still pretty unsure if the correct drivers are installed, anyway the pc after a good upgrade of ram, has not showed signs of previous symptoms so i'll put this tread closed. Thanks for your help!

---

