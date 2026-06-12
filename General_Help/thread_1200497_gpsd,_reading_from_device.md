---
title: "gpsd, reading from device"
date: 2009-06-30
forum: General Help
---

### Post by Legomaniac25 on 2009-06-30
Hello Everyone,

I am not sure if this is the right place to post this, but hopefully someone can point me in the right direction.

I am running Ubuntu 9.04 netbook remix on my acer aspire one.

I recently bought a Microsoft GPS-360 (manufactured by Pharos) unit, and decided to try to get it to work with my awesome netbook.

I downloaded tangogps through the synaptic package manager, it installed and the program seems to be running fine. I saw that it gets its gps data from gpsd, so I ran the program in the terminal, and it told me that it would not run without a device.

The gpsd website says it will autodetect the device when plugged in, but I read somewhere that this feature of the program didn't work 100% of the time, so I had to manually tell gpsd to find the device my running: 
```
gpsd /dev/ttyUSB0
```

After executing that command I do not receive any error messages and communication appears (from what I know) to have been established.

However, when I try to run tangogps or xgps, neither of them can retreive any data from gpsd.

Does anyone around here have experience with getting gpsd to work? I am a ubuntu noob so there's a good chance i'm just looking over something obvious.

Any ideas? Thanks in advance, I really appreciate your time.

Legomaniac25

---

### Post by jamb on 2009-07-09
Hi,
This is the way I did it on my ASUS Eee PC 1000HE netbook (xubuntu 9.04), and with both Haicom GPS (204E) and Globalsat GPS (BU-353 USB). The latter receiver has the SirfIII chip set.

To view what happens behind the scen, and make sure we know the device assignment to your GPS, open a terminal, and type
> 
$> tail -f /var/log/messages

Plug in your GPS-USB cable into the netbook USB port.
With my GPS, I got a lot (only a few shown) kernel messages like:
> 
Jul  9 17:06:49 warp kernel: [ 7914.636000] pl2303 1-6:1.0: pl2303 converter detected
Jul  9 17:06:49 warp kernel: [ 7914.636000] usb 1-6: pl2303 converter now attached to **ttyUSB0**
Jul  9 17:06:49 warp kernel: [ 7914.636000] usbcore: registered new interface driver pl2303


Note that the GPS is connected to *ttyUSB0* device.

The gpsd service is not started automatically, thus we need to reconfigure it. Open another terminal and type.
> $> sudo dpkg-reconfigure gpsd

Four windows will ask: 1. start at boot - yes, 2. device: /dev/ttyUSB0 -yes, 3 and 4: use defaults, just hit enter twice after this. Now gpsd is started.
> 
 * Stopping GPS (Global Positioning System) daemon gpsd                  [ OK ] 
 * Starting GPS (Global Positioning System) daemon gpsd                  [ OK ]


Other good commands to be aware of are:
> 
$> sudo /etc/init.d/gpsd start|stop
$> netstat -a | grep gpsd
$> cat /etc/default/gpsd

The first command start or halt the gpsd daemon, netstat shows that gpsd is LISTEN, and the last one, just echo the content of gpsd 'configuration file'.

Try this:
> 
$> netstat -a | grep gpsd
tcp        0      0 *:gpsd      *:*                     LISTEN  


If everything is OK at this point, start xgps to test your set-up.
> 
$> xgps


Now you should have your fix. I have found that GPS receivers with the SirfIII chip is often better than devices that xgps consider as 'generic NMEA' (look at the application title bar).

After this you can start 'Tango GPS' from the menu - and it works nice for me for both GPS receivers. Another package is 'GPS drive'.

I hope this is to some help, and let me know if you need hints on udev rules, such that the GPS always have the same device assignment or use your own defined name.

---

### Post by michaelayland on 2009-10-27
Thank you to the contributors of this tread
I am using a USGlobalsat  BU-353 USB GPS Mouse and by following this tread now have Tango GPS and GPSDrive working but also by using wine The GPS will plot onto United Kingdom Memory Map  Ordnance Survey Maps

Thanks folks!

---

