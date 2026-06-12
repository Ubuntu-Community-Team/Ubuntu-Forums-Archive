---
title: "Running Garmin Mapsource (6137) under Ubuntu with GPS access"
date: 2010-05-15
forum: General Help
---

### Post by foobar66 on 2010-05-15
Just posting this as it maybe useful for other people. There are some  other topics related to running Garmin MapSource under ubuntu. I've got  Garmin MapSource (version 6137) working under Lucid with a working GPS  link to a Garmin 60CSx handheld.

Actually, since I have this  running, I have completely erased Vista and Win7 from my hard disk as  MapSource was the one and only application which sort of kept me  sticking to Windows.

Here's a brief ;-)  instruction. First install  wine:

> sudo apt-get install wine
> wine --version
wine-1.1.42

Then  run winecfg (as normal user); this will create a .wine directory:

>  winecfg
(just click OK when the dialog shows)

Now you can  install MapSource. The executable is named MapSource_6137.exe. Copy it  into your home dir.

Now do the following (otherwise  MapSource_6137.exe will not work):

> cd ~/.wine/drive_c
>  mkdir Garmin
> touch Garmin/MapSource.exe

Now run the  executable using wine:

> chmod +x ~/MapSource_6137.exe
>  wine ~/MapSource_6137.exe

Follow on screen instruction, accept  the license and it will install. At the end of the install you can  launch MapSource => DON't do this! Uncheck the checkmark and just  exit the installation.

Now you should be able to run MapSource:

>  cd ~/.wine/drive_c/Garmin/
> wine ./MapSource.exe

It will  give you the following error message:

"MapSource could not find  any install MapSource map products"

This is because you don't  have any maps yet.

Personally, I already had a lot of maps that  were originally installed under Windows on a Windows D: drive (separate  partition). The procedure below described how you can use these maps  directly under the Ubuntu/wine MapSource without doing any additional  map installation.

First, mount the partition containing the maps.  In my case:

> sudo mkdir /WinD
> sudo mount -t ntfs  /dev/sdb1 /WinD

Make it appear as if this is also the "d:" drive  for wine:

> cd ~/.wine/dosdevices
> ln -s /WinD "d:"

This  will give you a "d:" drive under wine which is linked to my original D:  disk which existed under Windows.

My maps were located in  /WinD/Garmin. Here you will find the map directories which were created  in the original Windows installation.

I will just give one  example of a map => CNEUR9, this is the City Select Europe version 9  (routable) maps.

> ls /WinD/Garmin/CNEUR9
=> this will  pop up a lot of .img files

Run "regedit.exe" under wine:

>  cd ~/.wine/drive_c/windows
> wine ./regedit.exe

Now go to  HKEY_LOCAL_MACHINE > Software > Garmin > MapSource

You  will see that this is empty. Now you should create the proper keys to  access your maps. This depends a little bit from map to map. For the  CNEUR9, the keys are (adapted to my configuration on the old D: drive  which is now mapped throug /WinD under Ubuntu).

REGEDIT4
[HKEY_LOCAL_MACHINE\Software\Garmin\MapSource\Families\City  Navigator Europe v9]
"ID"=hex:c6,00
"IDX"="D:\\Garmin\\CNEUR9\\CNEuro_v9.mdx"
"MDR"="D:\\Garmin\\CNEUR9\\CNEuro_v9_mdr.img"
[HKEY_LOCAL_MACHINE\Software\Garmin\MapSource\Families\City  Navigator Europe v9\1]
"Bmap"="D:\\Garmin\\CNEUR9\\CNEuro_v9.img"
"Loc"="D:\\Garmin\\CNEUR9\\"
"Notice"="D:\\Garmin\\CNEUR9\\eula_ENU.txt"
"Tdb"="D:\\Garmin\\CNEUR9\\CNEuro_v9.tdb"

You  can copy these keys from the old Windows MapSource installation (via  registry export keys). And then you can import the .reg file exported  from Windows in the wine registry. Make sure though that the top line of  the .reg file reads: REGEDIT4 (manually edit it after having exported  it from Windows).

Now run MapSource.

> wine  ~/.wine/drive_c/Garmin/MapSource.exe

Now it should start by  showing the maps. However ... the maps will be "locked".
Now comes  the tricky bit. The unlock wizard which is part of the mapsource  installation does not work under wine-1.1.42 ... bummer.

This can  be fixed by running an older version of wine (wine_1.1.188). You can  download the .deb file from  [http://wine.budgetdedicated.com/archive/index.html](http://wine.budgetdedicated.com/archive/index.html)

Download  wine_1.1.18 appropriate for your architecture.

Now do the  following:

> sudo apt-get purge wine wine1.2
(this will  remove your existing wine; install the wine_1.1.18)
> sudo dpkg -i  ~/Desktop/wine_1.1.18~winehq0~ubuntu~9.04-0ubuntu1_amd64.deb
(select  appropriate file which you downloaded)

After installation of  this package, run the unlock wizard.

> wine  ~/.wine/drive_c/Garmin/UnlockWizard.exe

Now unlock your maps. My  unlock codes were already stored in a file, you can restore them from  the file (follow instructions from unlock wizard).

After having  unlocked your maps, remove the wine_1.1.18 version:

> sudo  apt-get purge wine

And the reinstall the latest wine version  (1.1.42)

> sudo apt-get install wine

This will say:
"Unpacking  wine1.2 (from .../wine1.2_1.1.42-0ubuntu4_amd64.deb)"

> wine  --version
wine-1.1.42

Now you can run MapSource with your  unlocked maps:

> wine ~/.wine/drive_c/Garmin/MapSource.exe

---  accessing the GPS ---

I have a Garmin GPSmap 60CSx GPS. You can  use it directly under MapSource as follows:

> sudo modprobe  garmin_gps
> lsmod | grep garmin

And you should see  something like:

garmin_gps             12482  0 
usbserial               24955  1 garmin_gps
usbcore               111843  6  garmin_gps,usbserial,btusb,usbhid,ehci_hcd,uhci_hcd

Turn on the  GPS and connect it to the USB port. Then do:

> ls /dev/tty*

You  should see a device called "ttyUSB0".

Now we have to make this  device visisble as "com1" port under wine:

> cd  ~/.wine/dosdevices
> ln -s /dev/ttyUSB0 "com1"

Restart your  MapSource using:

> wine ~/.wine/drive_c/Garmin/MapSource.exe

In  the "Transfer" menu, select "Receive from device". You should now see  your device and can transfer tracks, waypoints from your GPS into  MapSource.

Good luck! After I got this working, I erased Windows  from my PC ;-)

---

### Post by MrWylbur on 2010-05-19
Any reason for not using the latest mapsource files from Garmin (6.16.1 at this time)?

I will be using OpenStreetMap and Minnesota Topo maps, so no need to unlock these files.  This should make my install a little easier.  

I am also running a 60csx receiver.

Thanks!

---

### Post by foobar66 on 2010-05-19
> **MrWylbur said:**
> Any reason for not using the latest mapsource files from Garmin (6.16.1 at this time)?

I will be using OpenStreetMap and Minnesota Topo maps, so no need to unlock these files.  This should make my install a little easier.  

I am also running a 60csx receiver.

Thanks!

Two reasons:
1) I could not get newer versions to work (I did not investigate why)
2) Even on XP, newer version did not want to open all of my maps

Therefore, I am sticking to 6137 version.

---

### Post by skarfur on 2010-05-30
Hi foobar66, thanks for the info, it was indeed very useful

---

### Post by gabak on 2010-06-04
here it explain how to do it

[http://jhau.maliwi.de/linux/gpssw.html](http://jhau.maliwi.de/linux/gpssw.html)

---

### Post by foobar66 on 2010-11-20
One other remark. You have to be a member of the group called "dialout".

Go to System > Admin > Users and Groups

Then add yourself to the "dialout" group.

Reason:

/dev/ttyUSB0 has permissions as:

0 crw-rw---- 1 root dialout 188, 0 2010-11-20 11:20 /dev/ttyUSB0

So if you add yourself to the dialout group you will have read/write access to the port.

---

### Post by surveyorsteve on 2010-12-03
Hi, I've managed to get the latest Mapsource 6.16.3 to run on WINE 1.3.8 perfectly but can't connect my Dakota GPSr. Tried the above but I get:

steve@steve-desktop:~$ lsmod | grep garmin
garmin_gps             14947  0 
usbserial              33019  1 garmin_gps
steve@steve-desktop:~$ ls /dev/tty*
/dev/tty    /dev/tty19  /dev/tty3   /dev/tty40  /dev/tty51  /dev/tty62
/dev/tty0   /dev/tty2   /dev/tty30  /dev/tty41  /dev/tty52  /dev/tty63
/dev/tty1   /dev/tty20  /dev/tty31  /dev/tty42  /dev/tty53  /dev/tty7
/dev/tty10  /dev/tty21  /dev/tty32  /dev/tty43  /dev/tty54  /dev/tty8
/dev/tty11  /dev/tty22  /dev/tty33  /dev/tty44  /dev/tty55  /dev/tty9
/dev/tty12  /dev/tty23  /dev/tty34  /dev/tty45  /dev/tty56  /dev/ttyS0
/dev/tty13  /dev/tty24  /dev/tty35  /dev/tty46  /dev/tty57  /dev/ttyS1
/dev/tty14  /dev/tty25  /dev/tty36  /dev/tty47  /dev/tty58  /dev/ttyS2
/dev/tty15  /dev/tty26  /dev/tty37  /dev/tty48  /dev/tty59  /dev/ttyS3
/dev/tty16  /dev/tty27  /dev/tty38  /dev/tty49  /dev/tty6
/dev/tty17  /dev/tty28  /dev/tty39  /dev/tty5   /dev/tty60
/dev/tty18  /dev/tty29  /dev/tty4   /dev/tty50  /dev/tty61

Wine configuration maps G: to /media/GARMIN

Anyone got any ideas?

Steve

---

### Post by foobar66 on 2010-12-04
Steve

I'm guessing a little bit here, but it may be your device is not recognized by udev.

As root, create a file called /etc/udev/rules.d/51-garmin.rules

In the file. put the following contents:

ACTION=="add", SUBSYSTEM=="usb", ATTR{idVendor}=="091e", ATTR{idProduct}=="0003", MODE="666", RUN+="/sbin/modprobe garmin_gps", ENV{GENERATE
D}="1"
ACTION=="remove", KERNEL=="ttyUSB*", RUN+="/sbin/rmmod -w garmin_gps", RUN+="/sbin/rmmod -w usbserial", ENV{GENERATED}="1"


vendor and product could be different for you (depending on GPS model). Above values work for a GPSMAP60CSX. With lsusb (while your device is plugged and turned on) you should see the values that you need in case you have a different model.

I am not sure how to restart udev ... just reboot.

Then in a terminal type:

> udevadm monitor

Now turn on and plug in your device, you should see something like:

KERNEL[1291441981.586718] add      /devices/pci0000:00/0000:00:1d.0/usb4/4-1 (usb)
KERNEL[1291441981.589642] add      /devices/pci0000:00/0000:00:1d.0/usb4/4-1/4-1:1.0 (usb)
KERNEL[1291441981.636640] add      /module/usbserial (module)
KERNEL[1291441981.636655] add      /bus/usb-serial (bus)
KERNEL[1291441981.636971] add      /bus/usb/drivers/usbserial (drivers)
UDEV  [1291441981.636982] add      /module/usbserial (module)
UDEV  [1291441981.636992] add      /bus/usb/drivers/usbserial (drivers)
UDEV  [1291441981.637002] add      /bus/usb-serial (bus)
KERNEL[1291441981.638149] add      /module/garmin_gps (module)
KERNEL[1291441981.638161] add      /bus/usb-serial/drivers/garmin_gps (drivers)
KERNEL[1291441981.638408] add      /devices/pci0000:00/0000:00:1d.0/usb4/4-1/4-1:1.0/ttyUSB0 (usb-serial)
UDEV  [1291441981.638418] add      /module/garmin_gps (module)
KERNEL[1291441981.638431] add      /devices/pci0000:00/0000:00:1d.0/usb4/4-1/4-1:1.0/ttyUSB0/tty/ttyUSB0 (tty)
UDEV  [1291441981.638441] add      /bus/usb-serial/drivers/garmin_gps (drivers)
KERNEL[1291441981.638451] add      /bus/usb/drivers/garmin_gps (drivers)
UDEV  [1291441981.638884] add      /devices/pci0000:00/0000:00:1d.0/usb4/4-1 (usb)
UDEV  [1291441981.639161] add      /bus/usb/drivers/garmin_gps (drivers)
UDEV  [1291441981.639176] add      /devices/pci0000:00/0000:00:1d.0/usb4/4-1/4-1:1.0 (usb)
UDEV  [1291441981.639385] add      /devices/pci0000:00/0000:00:1d.0/usb4/4-1/4-1:1.0/ttyUSB0 (usb-serial)
UDEV  [1291441981.676567] add      /devices/pci0000:00/0000:00:1d.0/usb4/4-1/4-1:1.0/ttyUSB0/tty/ttyUSB0 (tty)

The last 2 lines now show that udev has rec ognized it and created /dev/ttyUSB0

Check it with "ls /dev/tty*".

Let us know if it worked. -*- philip

---

### Post by foobar66 on 2010-12-04
I tried as well with wine-1.3.8 and Mapsource 6.16.3 and GPS transfer from/to my GPSmap60CSX is working (see all instructions in above thread).

---

### Post by foobar66 on 2010-12-04
Bye the way: all .exe files for Mapsource can be found here:
[http://www.gawisp.com/perry/mapsource/](http://www.gawisp.com/perry/mapsource/)

---

### Post by surveyorsteve on 2010-12-19
Thanks but ttyUSB0 doesn't seem to be created. After lsmod | grep garmin I get:

garmin_gps             15183  0 
usbserial              33100  1 garmin_gps

Tried editing 51-garmin.rules by adding those commands but still nothing.

udevadm monitor fails to return anything.

I'm using a Dakota 20.

I can't be far away from the solution?

---

### Post by foobar66 on 2010-12-19
> **surveyorsteve said:**
> Thanks but ttyUSB0 doesn't seem to be created. After lsmod | grep garmin I get:

garmin_gps             15183  0 
usbserial              33100  1 garmin_gps

Tried editing 51-garmin.rules by adding those commands but still nothing.

udevadm monitor fails to return anything.

I'm using a Dakota 20.

I can't be far away from the solution?

This procedure does not work with a Dakota.
The Dakota is mounted as a block device (it should appear on your desktop).

Also note that the vendor/product IDs in the 51-garmin.rules file do not match the Dakota. Dakota has "23c0" as product ID.

Anyway, even with changing the ID in the garmin.rules file, the device still gets mounted as a block device (accidently, I have a Dakota on loan for the weekend so I actually checked this).

I am not sure ... maybe there is a way to get it to mount as a char device ... but I am at the boundary of my linux knowledge here. Porbably with udev, there is a way to avoid it getting recognized as a block device ...

If you should ever get it working, let us know.

---

### Post by surveyorsteve on 2010-12-19
Thanks for that. I had change the product ID but no luck. Will post if I get it to work.

---

### Post by Nilleb on 2011-05-01
Ubuntu 10.10 64-bit with all updates.

I have been using MapSource since 2006 and for the moment using MapSource 6.16.2.0 under Vista. I have a Garmin Quest and terrain maps of North Sweden.

MapSource is the last barrier for me to moving completely to Ubuntu which I have been using since 7.10.

I followed Your informative instruction to the letter except for trying to use MapSource_6163, I don't have succeded in downloading 6137.

It all runs well until:

> **foobar66 said:**
> 
> chmod +x ~/MapSource_6137.exe
>  wine ~/MapSource_6137.exe

Follow on screen instruction, accept  the license and it will install.

In the terminal:
wine ~/MapSource_6163.exe
fixme:actctx:parse_depend_manifests Could not find dependent assembly L"Microsoft.VC80.CRT" (8.0.50608.0)

The installation program reports: No earlier MapSource-installation could be found. Installation will now be interrupted. (Excuse my translation from swedish ;)

The process is then stopped and klicking on OK in the dialog box => exit.

I have done some experiments with _61511 with the same result.

What to do?

1. Get the MapSource_6137 in some way, how?
2. A remedy for the error messages and continuing with MapSource_6163
   (or MapSource_61511)?

---

### Post by foobar66 on 2011-05-01
Only MapSource_6137.exe will work under wine. Newer versions don't work.

Download it from:
[http://www.gawisp.com/perry/mapsource/](http://www.gawisp.com/perry/mapsource/)

Then follow instructions from first post.

BTW: I am using wine-1.2.2 now, under 11.04.

```

sudo add-apt-repository ppa:ubuntu-wine/ppa
sudo apt-get update
sudo apt-get -y install wine

```

I also suggest that you remove your ~/.wine directory to avoid config clobber:

>  rm -rf ~/.wine
> winecfg

Then restart instructions from beginning.

---

### Post by Nilleb on 2011-05-01
Thank You foobar66 for the fast answer!

I am always impressed over the support in Ubuntu.

Now I have to do my home work and follow Your exellent instructions to the letter.
This time ;)

---

### Post by Nilleb on 2011-05-01
foobar66 "Then restart instructions from beginning."

Now I have MapSource 6137 running, and as You stated in the instructions:

"MapSource could not find any install MapSource map products"

I plan to get rid of Win Vista so I think it is better to install the maps in /home rather than use the alredy installed maps from Win.
 (The laptop has two HD and I don't know where they were installed in the first place C: or D: ?)

How do I install the maps from CD?

I have on original CD:
 City Navigator Europe v8
 A topo map "Friluftskartan pro Norra Norrland" North of Sweden.

With exported unlock codes .ucx on my desktop.

---

### Post by Nilleb on 2011-05-15
> **Nilleb said:**
> foobar66 "Then restart instructions from beginning."


 (The laptop has two HD and I don't know where they were installed in the first place C: or D: ?)

How do I install the maps from CD?

I have on original CD:
 City Navigator Europe v8
 A topo map "Friluftskartan pro Norra Norrland" North of Sweden.

With exported unlock codes .ucx on my desktop.

Now I managed to mount C: and there is the Garmin MapSource maps.

So what to do for the next step.
Wine is up and working, but I have not been able to install the maps directly in Wine. The installation program just shuts down.

---

### Post by Samloops on 2011-08-16
Greetings All...

I was able to get MapSource installed in 11.04 relatively easily using Wine 1.2.2 (which I guess is the latest from the standard Ubuntu repos as I just used the Software Center) and MapSource 6137 from [http://www.gawisp.com/perry/mapsource/](http://www.gawisp.com/perry/mapsource/) as noted above.  For the installation I followed the instructions found at [http://www.malsingmaps.com/wiki/index.php?title=Installing_Mapsource_in_Linux](http://www.malsingmaps.com/wiki/index.php?title=Installing_Mapsource_in_Linux) .  

There are a couple of confusing points in the instructions, but Malsingmaps seems to provide maps to Garmin for the Phillipines and provides on their website, unlocked MapSource map files of Malaysia, Singapore and Brunei for download.  It's a little awkward as you need to do a free registration, but after some hunting you can download a MapSource installer file that will run under Wine for installing one of their maps to MapSource.  Once that's done, MapSource will open and run under Wine.  You need to hunt around on their site to find a MapSource version of a map (MSM_MS version of the file and not a gmapsupp.img version)... then follow their instructions for opening the file with Wine.  Just right click on the file and Open with Wine is one of the options.   MapSource installs under Applications > Wine > Programs > Garmin. The only quirk I have found is that in order to get MapSource to display correctly, I have to get it to repaint by first minimizing it, then reopening the window.  Without doing that, it seems to have some transparent display issues.

I am stuck on the last step of their instructions however and cannot get MapSource to recognize my Nuvi 255 when connected to a USB port.  ttyusb0 is never created and so the symbolic link between it and COM1 is broken. MapSource cannot find the device.  From what I have read above and elsewhere, it seems that the Nuvi is being recognized by the OS as a block device... both the Garmin and the installed SD chip appear on the desktop.  Not sure if this is the case for all Garmins... but for the 255 it is.  I did the whole install in both Ubuntu 11.04 and Fedora 15 on two different boxes with the EXACT same results.... including the display issues.

It would be nice to find a solution to this, otherwise I may have to continue to use MapSource under a Windows XP VirtualBox guest (which does communicate with the GPS nicely)... but I'd love to get away from Windows altogether. MapSource and RosettaStone are my final two hurdles!!!  :D

Hope this helps those who are having install problems.  Maybe those with other Garmin models may not get stuck at the last step.???

Sam Longiaru
Kamloops, BC

---

### Post by jtappin on 2011-08-20
> **foobar66 said:**
> Steve

I'm guessing a little bit here, but it may be your device is not recognized by udev.

As root, create a file called /etc/udev/rules.d/51-garmin.rules

In the file. put the following contents:

ACTION=="add", SUBSYSTEM=="usb", ATTR{idVendor}=="091e", ATTR{idProduct}=="0003", MODE="666", RUN+="/sbin/modprobe garmin_gps", ENV{GENERATE
D}="1"
ACTION=="remove", KERNEL=="ttyUSB*", RUN+="/sbin/rmmod -w garmin_gps", RUN+="/sbin/rmmod -w usbserial", ENV{GENERATED}="1"


vendor and product could be different for you (depending on GPS model). Above values work for a GPSMAP60CSX. With lsusb (while your device is plugged and turned on) you should see the values that you need in case you have a different model.

I am not sure how to restart udev ... just reboot.



No joy with the GPSMAP 62S, I have tried the above recipe with the Product ID changed to 2459, as reported by lsusb. 

BTW to restart udev, you can use:
```
sudo service udev restart
```

But the unit is still treated as a block device. 

Currently I'm using the OpenStreetMap maps (for one thing I don't feel inclined to pay fpr maps until I know I can use them). I have also tried copying the version for use on the microSD card to the Custom Maps folder on the device (both zipped & unzipped) and extracting the mapsource installer direct to the device without any usable results.

The MapSource.exe program does recognize & display the maps produced by the MapSource installer, but can't find the device.

Does anyone have any suggestions?

---

### Post by jtappin on 2011-08-21
> **jtappin said:**
> 

But the unit is still treated as a block device. 


From the [FONT="Courier New"]udevadm monitor[/FONT] output (below), it appears to have recognized the udev rule and is loading the garmin_gps module, but then goes ahead and treats it as a block device anyway. (The device showed up as /dev/sdh (not /dev/sdh1)).

```
KERNEL[1313937277.287826] add      /devices/pci0000:00/0000:00:13.2/usb2/2-5 (usb)
KERNEL[1313937277.288088] add      /devices/pci0000:00/0000:00:13.2/usb2/2-5/2-5:1.0 (usb)
KERNEL[1313937277.288374] add      /devices/pci0000:00/0000:00:13.2/usb2/2-5/2-5:1.0/host7 (scsi)
KERNEL[1313937277.288524] add      /devices/pci0000:00/0000:00:13.2/usb2/2-5/2-5:1.0/host7/scsi_host/host7 (scsi_host)
KERNEL[1313937277.338981] add      /module/usbserial (module)
UDEV  [1313937277.339559] add      /module/usbserial (module)
KERNEL[1313937277.349084] add      /bus/usb-serial (bus)
KERNEL[1313937277.349131] add      /bus/usb/drivers/usbserial (drivers)
KERNEL[1313937277.349160] add      /bus/usb-serial/drivers/generic (drivers)
KERNEL[1313937277.349222] add      /bus/usb/drivers/usbserial_generic (drivers)
UDEV  [1313937277.349611] add      /bus/usb-serial (bus)
UDEV  [1313937277.350251] add      /bus/usb-serial/drivers/generic (drivers)
UDEV  [1313937277.350296] add      /bus/usb/drivers/usbserial (drivers)
UDEV  [1313937277.350819] add      /bus/usb/drivers/usbserial_generic (drivers)
KERNEL[1313937277.363191] add      /module/garmin_gps (module)
KERNEL[1313937277.363339] add      /bus/usb-serial/drivers/garmin_gps (drivers)
KERNEL[1313937277.363388] add      /bus/usb/drivers/garmin_gps (drivers)
UDEV  [1313937277.363803] add      /devices/pci0000:00/0000:00:13.2/usb2/2-5 (usb)
UDEV  [1313937277.363853] add      /module/garmin_gps (module)
UDEV  [1313937277.363946] add      /bus/usb-serial/drivers/garmin_gps (drivers)
UDEV  [1313937277.364136] add      /bus/usb/drivers/garmin_gps (drivers)
UDEV  [1313937277.366044] add      /devices/pci0000:00/0000:00:13.2/usb2/2-5/2-5:1.0 (usb)
UDEV  [1313937277.367600] add      /devices/pci0000:00/0000:00:13.2/usb2/2-5/2-5:1.0/host7 (scsi)
UDEV  [1313937277.368779] add      /devices/pci0000:00/0000:00:13.2/usb2/2-5/2-5:1.0/host7/scsi_host/host7 (scsi_host)
KERNEL[1313937278.288559] add      /devices/pci0000:00/0000:00:13.2/usb2/2-5/2-5:1.0/host7/target7:0:0 (scsi)
KERNEL[1313937278.288616] add      /devices/pci0000:00/0000:00:13.2/usb2/2-5/2-5:1.0/host7/target7:0:0/7:0:0:0 (scsi)
KERNEL[1313937278.288737] add      /devices/pci0000:00/0000:00:13.2/usb2/2-5/2-5:1.0/host7/target7:0:0/7:0:0:0/scsi_disk/7:0:0:0 (scsi_disk)
KERNEL[1313937278.288794] add      /devices/pci0000:00/0000:00:13.2/usb2/2-5/2-5:1.0/host7/target7:0:0/7:0:0:0/scsi_device/7:0:0:0 (scsi_device)
KERNEL[1313937278.288944] add      /devices/pci0000:00/0000:00:13.2/usb2/2-5/2-5:1.0/host7/target7:0:0/7:0:0:0/scsi_generic/sg8 (scsi_generic)
KERNEL[1313937278.289051] add      /devices/pci0000:00/0000:00:13.2/usb2/2-5/2-5:1.0/host7/target7:0:0/7:0:0:0/bsg/7:0:0:0 (bsg)
KERNEL[1313937278.289109] add      /devices/pci0000:00/0000:00:13.2/usb2/2-5/2-5:1.0/host7/target7:0:0/7:0:0:1 (scsi)
KERNEL[1313937278.289182] add      /devices/pci0000:00/0000:00:13.2/usb2/2-5/2-5:1.0/host7/target7:0:0/7:0:0:1/scsi_disk/7:0:0:1 (scsi_disk)
KERNEL[1313937278.289251] add      /devices/pci0000:00/0000:00:13.2/usb2/2-5/2-5:1.0/host7/target7:0:0/7:0:0:1/scsi_device/7:0:0:1 (scsi_device)
KERNEL[1313937278.289368] add      /devices/pci0000:00/0000:00:13.2/usb2/2-5/2-5:1.0/host7/target7:0:0/7:0:0:1/scsi_generic/sg9 (scsi_generic)
KERNEL[1313937278.289473] add      /devices/pci0000:00/0000:00:13.2/usb2/2-5/2-5:1.0/host7/target7:0:0/7:0:0:1/bsg/7:0:0:1 (bsg)
UDEV  [1313937278.289718] add      /devices/pci0000:00/0000:00:13.2/usb2/2-5/2-5:1.0/host7/target7:0:0 (scsi)
UDEV  [1313937278.290842] add      /devices/pci0000:00/0000:00:13.2/usb2/2-5/2-5:1.0/host7/target7:0:0/7:0:0:0 (scsi)
UDEV  [1313937278.291091] add      /devices/pci0000:00/0000:00:13.2/usb2/2-5/2-5:1.0/host7/target7:0:0/7:0:0:1 (scsi)
UDEV  [1313937278.295879] add      /devices/pci0000:00/0000:00:13.2/usb2/2-5/2-5:1.0/host7/target7:0:0/7:0:0:0/scsi_disk/7:0:0:0 (scsi_disk)
UDEV  [1313937278.297278] add      /devices/pci0000:00/0000:00:13.2/usb2/2-5/2-5:1.0/host7/target7:0:0/7:0:0:0/scsi_device/7:0:0:0 (scsi_device)
KERNEL[1313937278.298000] add      /devices/virtual/bdi/8:128 (bdi)
KERNEL[1313937278.298419] add      /devices/pci0000:00/0000:00:13.2/usb2/2-5/2-5:1.0/host7/target7:0:0/7:0:0:1/block/sdi (block)
UDEV  [1313937278.298667] add      /devices/pci0000:00/0000:00:13.2/usb2/2-5/2-5:1.0/host7/target7:0:0/7:0:0:1/scsi_disk/7:0:0:1 (scsi_disk)
UDEV  [1313937278.299177] add      /devices/virtual/bdi/8:128 (bdi)
UDEV  [1313937278.299215] add      /devices/pci0000:00/0000:00:13.2/usb2/2-5/2-5:1.0/host7/target7:0:0/7:0:0:1/scsi_device/7:0:0:1 (scsi_device)
UDEV  [1313937278.299254] add      /devices/pci0000:00/0000:00:13.2/usb2/2-5/2-5:1.0/host7/target7:0:0/7:0:0:0/bsg/7:0:0:0 (bsg)
UDEV  [1313937278.299782] add      /devices/pci0000:00/0000:00:13.2/usb2/2-5/2-5:1.0/host7/target7:0:0/7:0:0:0/scsi_generic/sg8 (scsi_generic)
UDEV  [1313937278.299925] add      /devices/pci0000:00/0000:00:13.2/usb2/2-5/2-5:1.0/host7/target7:0:0/7:0:0:1/bsg/7:0:0:1 (bsg)
KERNEL[1313937278.300207] change   /devices/pci0000:00/0000:00:13.2/usb2/2-5/2-5:1.0/host7/target7:0:0/7:0:0:1/block/sdi (block)
KERNEL[1313937278.300768] add      /devices/virtual/bdi/8:112 (bdi)
UDEV  [1313937278.301083] add      /devices/pci0000:00/0000:00:13.2/usb2/2-5/2-5:1.0/host7/target7:0:0/7:0:0:1/scsi_generic/sg9 (scsi_generic)
UDEV  [1313937278.301421] add      /devices/virtual/bdi/8:112 (bdi)
KERNEL[1313937278.307397] add      /devices/pci0000:00/0000:00:13.2/usb2/2-5/2-5:1.0/host7/target7:0:0/7:0:0:0/block/sdh (block)
UDEV  [1313937278.344572] add      /devices/pci0000:00/0000:00:13.2/usb2/2-5/2-5:1.0/host7/target7:0:0/7:0:0:1/block/sdi (block)
UDEV  [1313937278.371975] change   /devices/pci0000:00/0000:00:13.2/usb2/2-5/2-5:1.0/host7/target7:0:0/7:0:0:1/block/sdi (block)
UDEV  [1313937278.410003] add      /devices/pci0000:00/0000:00:13.2/usb2/2-5/2-5:1.0/host7/target7:0:0/7:0:0:0/block/sdh (block)

```

This is the relevant material from /var/log/syslog (I assume that /dev/sdi which is also in the log is where the microSD card would mount if there was one)

```
Aug 21 08:34:18 xena kernel: [  912.890133] usb 6-2: new full speed USB device using ohci_hcd and address 2
Aug 21 08:34:18 xena kernel: [  912.950138] hub 6-0:1.0: unable to enumerate USB device on port 2
Aug 21 08:34:37 xena kernel: [  931.170134] usb 2-5: new high speed USB device using ehci_hcd and address 4
Aug 21 08:34:37 xena kernel: [  931.322027] scsi7 : usb-storage 2-5:1.0
Aug 21 08:34:37 xena kernel: [  931.382877] usbcore: registered new interface driver usbserial
Aug 21 08:34:37 xena kernel: [  931.382911] USB Serial support registered for generic
Aug 21 08:34:37 xena kernel: [  931.382966] usbcore: registered new interface driver usbserial_generic
Aug 21 08:34:37 xena kernel: [  931.382971] usbserial: USB Serial Driver core
Aug 21 08:34:37 xena kernel: [  931.397082] USB Serial support registered for Garmin GPS usb/tty
Aug 21 08:34:37 xena kernel: [  931.397139] usbcore: registered new interface driver garmin_gps
Aug 21 08:34:37 xena kernel: [  931.397144] garmin_gps: v0.36:garmin gps driver
Aug 21 08:34:38 xena kernel: [  932.320921] scsi 7:0:0:0: Direct-Access     Garmin   GARMIN Flash     1.00 PQ: 0 ANSI: 5
Aug 21 08:34:38 xena kernel: [  932.321410] scsi 7:0:0:1: Direct-Access     Garmin   GARMIN SD Card   1.00 PQ: 0 ANSI: 5
Aug 21 08:34:38 xena kernel: [  932.322632] sd 7:0:0:0: Attached scsi generic sg8 type 0
Aug 21 08:34:38 xena kernel: [  932.323117] sd 7:0:0:1: Attached scsi generic sg9 type 0
Aug 21 08:34:38 xena kernel: [  932.332892] sd 7:0:0:0: [sdh] 3866624 512-byte logical blocks: (1.97 GB/1.84 GiB)
Aug 21 08:34:38 xena kernel: [  932.334391] sd 7:0:0:0: [sdh] Write Protect is off
Aug 21 08:34:38 xena kernel: [  932.334400] sd 7:0:0:0: [sdh] Mode Sense: 23 00 00 00
Aug 21 08:34:38 xena kernel: [  932.334408] sd 7:0:0:0: [sdh] Assuming drive cache: write through
Aug 21 08:34:38 xena kernel: [  932.336142] sd 7:0:0:1: [sdi] Attached SCSI removable disk
Aug 21 08:34:38 xena kernel: [  932.337371] sd 7:0:0:0: [sdh] Assuming drive cache: write through
Aug 21 08:34:38 xena kernel: [  932.339784]  sdh:
Aug 21 08:34:38 xena kernel: [  932.342649] sd 7:0:0:0: [sdh] Assuming drive cache: write through
Aug 21 08:34:38 xena kernel: [  932.342662] sd 7:0:0:0: [sdh] Attached SCSI removable disk

```

---

### Post by jtappin on 2011-08-23
Just a quick update: This [Thread]("http://ubuntuforums.org/showthread.php?t=1793977&highlight=garmin+gps") gives some useful hints on newer block devices.

A couple of things that I found though:
[LIST=1]
[*]The "floppy" option that is needed is not persistent at least for my 62s
[*]The drive MUST be mounted under Linux to be seen by wine.
[*]I eventually got it to work using the NMEA interface type (but it may just be that that was when I also got the mounting and type options right.
[/LIST]

With that combination I was able to get the routable OSM maps, and the Free Topo map of New Mexico from gpsfiledepot.com to load into the unit.

However although both appear to transfer (though there were some errors for the topo map) only the OSM map appears to be in Custom_Maps, and only the more recently uploaded (the topo) is accessible: Does anybody understand this?

The transfer errors:
```
fixme:ntdll:NtFsControlFile stub! return success - Unsupported fsctl 90018 (device=9 access=0 func=6 method=0)
fixme:ntdll:NtFsControlFile stub! return success - Unsupported fsctl 9001c (device=9 access=0 func=7 method=0)

```

---

### Post by jtappin on 2011-09-02
> **foobar66 said:**
> Two reasons:
1) I could not get newer versions to work (I did not investigate why)
2) Even on XP, newer version did not want to open all of my maps

Therefore, I am sticking to 6137 version.

I've been able to run 6157 with wine from the PPA (1.3.27). I think anything higher than that requires XP SP3 or later and wine is not recognized as satisfying that and so the install bails out.

---

### Post by handaxe on 2012-05-05
> **jtappin said:**
> No joy with the GPSMAP 62S, I have tried the above recipe with the Product ID changed to 2459, as reported by lsusb. 


A very stale thread but a small correction: the id 2459 is the mass storage Product ID for the GPSMap 62s. The "live" usb Product ID is 0003. Due to modeswitching - usb modems (GSM,UMTS,LTE) do it too...

---

