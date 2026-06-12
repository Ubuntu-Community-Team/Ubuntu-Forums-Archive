---
title: "logs in but no Monitor"
date: 2009-10-27
forum: General Help
---

### Post by stryvya on 2009-10-27
Having a problem with my UBUNTU 9.04 Installation, can anyone help please??
I went to watch an*.MPEG on Full Screen by double clicking the viewing area and the screen went blank, normally if this happens I press ctrl+alt+del and this brings up a log-in page (light blue background) and I can continue. This time instead of loging-on I chose to "shut down"
On next day when booting the computer got as far as installing correctly until the log-in music played and then presented a blank screen stating "no input to monitor" has anyone any clues to fixing this please.
everything works fine with live cd,s for UBUNTU and Mandriva, so its not a Monitor problem.
would like to repair existing installation, but when trying to run install option of cd it asks do I want to install over existing installation and that  there is no going back???

Len Gill

---

### Post by martrn on 2009-10-27
You should be able to boot into a terminal using the recover disc.  Grub should give you the option to boot into a terminal window, where you can type a few commands.  This is just the command line enviroment where you can fix things until you get Xwindows back.  Logon using your username and password and you will need find ot who your video card manufacturer is! Run the following in the terminal, to find this ```
lspci | grep VGA
```.This will return information about the video card such as its manufacturer, model and revision number.

From that line you should be able to install your graphics card kernel modules where you can set your display / resolution and be able to retreive the correct monitor settings.

[https://help.ubuntu.com/community/Video]("https://help.ubuntu.com/community/Video").
Check your Xorg.conf files and not the horizontal refersh rates and virtical refresh rates shouldn't be set too high or else your monitor might switch off and will not be able to see anything on the screen.

---

### Post by stryvya on 2009-10-27
reply to terminal query:- 01:05.0 VGA compatible controller: ATI Technologies Inc Radeon HD 3200 Graphics
ubuntu@ubuntu:~$

could you point me in the right direction,please, sorry not sure how to proceed
and if Iget the right drivers how implement them if i have no screen on bootong?

---

### Post by martrn on 2009-10-27
You should be able to boot into a terminal using the recover disc. Grub should give you the option to boot into a terminal window, where you can type a few commands. This is just the command line environment where you can fix things until you get Xwindows back. Logon using your username and password and first begin by installing the needed packages:

```
sudo apt-get install dpkg-dev debhelper libstdc++5 dkms build-essential cdbs fakeroot
```

You will then need to build the installation packages with the downloaded ATi drivers (ensure the ATi drivers have the execute flag set first):
For 64 bit version of ubuntu.
```
wget https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/ati-driver-installer-9-10-x86.x86_64.run
./ati-driver-installer-9-10-x86.x86_64.run --buildpkg Ubuntu/intrepid 
```
You can replace intrepid in the above with the codename for the version of Ubuntu you are running eg (gutsy, hardy, intrepid).

For 32 bit version of ubuntu.
```
wget https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/ati-driver-installer-9-10-x86.x86_64.run
./ati-driver-installer-9-10-x86.x86_64.run --buildpkg Ubuntu/intrepid 

```
You can replace intrepid in the above with the codename for the version of Ubuntu you are running eg (gutsy, hardy, intrepid).

Then install the binary drivers:

```
sudo dpkg -i fglrx-kernel-source_intrepid.deb
```

Run the following command to install the Xorg driver

```
sudo dpkg -i xorg-driver-fglrx_intrepid.deb
```

Finally run aticonfig to build your new xorg.conf if you have not done so before:

```
sudo aticonfig --initial
```

Reboot and X.Org should start with the ATi binary drivers fully functional. To confirm the drivers are working from a terminal run:

```
fglrxinfo
```

You should get output similiar to the following:

```
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Radeon HD 3200
OpenGL version string: 2.1.7170 Release
```

If you see any mention of the "MESA" in the output the drivers have not installed correctly. Look at url below for possible fixes. 
[https://help.ubuntu.com/community/RadeonDriver]("https://help.ubuntu.com/community/RadeonDriver")

---

### Post by stryvya on 2009-10-28
sorry martyn have been to busy to use your help, maybe able to try tomorrow

---

