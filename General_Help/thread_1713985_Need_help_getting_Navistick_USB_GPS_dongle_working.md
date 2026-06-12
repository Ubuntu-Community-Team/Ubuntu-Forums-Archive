---
title: "Need help getting Navistick USB GPS dongle working in Ubuntu 10.04"
date: 2011-03-24
forum: General Help
---

### Post by Pigstealer on 2011-03-24
Hi, I am new to Ubuntu (4 mos) and recently purchased a Navistick LE GPS dongle to use with Viking and/or Tango. One of the reasons I chose the Navistick is that it was advertised as being Linux compatible. The device came with a CD with drivers and such for Windows and Linux. I tried to follow the instructions included on the CD to create a RPM (which I was going to try to convert to .DEB with alien) to install the driver. I entered the commands but could not find an RPM file anywhere. I contacted the manufacturer who gave me the link to an updated driver. The file referenced in the link turned out to not be a valid archive file so I was unable to unarchive it. I was also instructed to look for posts in forums about "CP210x USB to UART bridge VCP drivers". I didn't find anything except stuff about modems not working.

I have kernel 2.6.32-30-generic running on a Toshiba satellite notebook. I have used a different GPS device with both Tango and Viking and that works pretty well. The link given for the driver is: [http://www.silabs.com/products/mcu/pages/usbtouartbridgevcpdrivers.aspx](http://www.silabs.com/products/mcu/pages/usbtouartbridgevcpdrivers.aspx) which is different than the original link I got off the CD so I think this might be their vendor. I am not sure what other information is needed.

Is there a difference between RPM based distros and Ubuntu such that I can't even create the RPM in the first place? Do I need this driver, or will it work without it? I am not sure I want to just plug it in for fear of frying something.

Thanks in advance if anyone can point me in the right direction.

---

### Post by Cheesehead on 2011-03-24
Welcome to Ubuntu.

Before diving into drivers, let's make sure we really need to go that route - often the solution is much easier. 'Drivers' don't mean quite the same thing in Linux that they do in Windows, and 'Linux-compatible' often means that hardware support is already in the kernel you have.

1) Have you installed the 'gpsd' package from the Ubuntu Software Center? It's one of the programs that takes information from the dongle and makes it available to applications. gpsd has been able to talk to every dongle I tried. Without mucking with any extra drivers.

2) If it's installed, is the gpsd process running? If not, start it with the command 'gpsd'. Um, take a look at 'man gpsd' before starting it manually...or else you'll wind up starting and stopping it a few times.

3) If gpsd is up and running and still cannot talk to the dongle, then it's time to visit the pros at the gpsd website (listed in 'man gpsd'). Try the command 'lsusb -v' to get better detail on the chipset. That's often more helpful than the brand name. Dongles-not-working often show up on the gpsd website first.

4) gpsd comes with simple connectivity tests (instructions are on the gpsd website) to see if the correct /dev/gps_device got created and the dongle is actually sending data on it. See if the dongle is really working.

5) After failing at those four steps, then it's time to look at compiling those drivers.

---

### Post by paulysa1969 on 2011-03-25
Hi there. Thanks for the pointers.

I looked on the gpsd website. Here is my USB GPS:

[GT-730F]("http://www.canmore.com.tw/pdf/English%20user%20manual_GT-730F_L.pdf") mouse SKYTRAK USB 2.33[IMG]http://gpsd.berlios.de/star.png[/IMG][IMG]http://gpsd.berlios.de/star.png[/IMG][IMG]http://gpsd.berlios.de/star.png[/IMG] 3.01  Reported by Rene Warren <warrenlr@gmail.com>.
I did try to read device from GPSPrune under Ubuntu 10.10 but it could not.

Had a look for gpsd but was not running and also not able to find in Ubuntu SW centre.
So must I try a sudo apt-get install gpsd?

---

### Post by paulysa1969 on 2011-03-25
Installed gpsd under synaptic package manager in Ubuntu 10.10.
'man gpsd' suggested using this:

gpsd /dev/ttyUSB0 (for lowest USB Port - but lsusb will confirm no doubt).

---

### Post by Cheesehead on 2011-03-25
Very good!
That's a great example of the right way to get GPS dongles to work.

---

### Post by Pigstealer on 2011-04-09
Thanks for the info Cheesehead. Somehow after reading the docs from the manufacturer I got the idea this thing was not sending standard NEMA strings and needed the driver to translate so gpsd could use the data. After reading your post where you stated that most dongles work I tried to just plug it in and see what happened. Still no luck. So I installed the driver and a monitor program provided onto a Win XP notebook and went to where there was a clear view of the sky and tried it out. Thing wouldn't work in Win with the manufacturers software so I sent it back and got a replacement (which is why nothing has been happening for a while). I got the replacement yesterday and took it to the same location and tried it out in Win XP again. It worked (kind of) until I clicked on the "Cold Start" button, then it quit working. I rebooted and it started working again. So enough with the Win XP stuff, I don't ever plan on using it with that. So I hooked in to my GNU/linux laptop and fired up xgps to see if it was sending NEMA strings. Everything seemed to be ok there so I started up Viking to see if I could track to my house. It lost the lock twice in about 1/2 mile so I am not so sure how happy I am with the dongle but thanks for pointing me in the right direction to figure it out. Oh, I took all of the driver stuff I could find off of my computer while waiting for the replacement. One of the lessons learned is not to get so tied up in what the manufacturer says about linux, they are not the experts. I also learned about xgps which is pretty danged cool. I do still have one thing I can't figure out. You mentioned checking to see if gpsd is running, and I can't figure out how to do that, and can't find anything in the forums about checking to see if a daemon is running.

---

