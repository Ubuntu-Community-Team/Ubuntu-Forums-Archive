---
title: "Huawei 3g modem e220 disconecting"
date: 2009-11-22
forum: General Help
---

### Post by deamosreapos on 2009-11-22
Hello,

Im pretty much an ubuntu noob so please help me through this.
I got an inspirion 2200, and I installed ubuntu 9.10 netbook remix. That all went fine I could isntall my wireless (yay for missing drivers there) And now I went on installing my 3G modem.

This went horrible. I can see the modem but not all the time its like the usb kicks it off or something. It will connect but then it will automaticly disconect me without further notice or anything.

So in essence it does seem to conect but once conected the modem disapears and the conection brakes.

So is there a solution? 

sudo modprobe option
[  965.003308] option1 ttyUSB0: GSM modem (1-port) converter now disconnected from ttyUSB0
[  965.003412] option1 ttyUSB1: GSM modem (1-port) converter now disconnected from ttyUSB1
[  965.255462] usb 2-1: GSM modem (1-port) converter now attached to ttyUSB0
[  965.267290] usb 2-1: GSM modem (1-port) converter now attached to ttyUSB1
[  977.842322] option1 ttyUSB1: GSM modem (1-port) converter now disconnected from ttyUSB1
[  977.842422] option1 ttyUSB0: GSM modem (1-port) converter now disconnected from ttyUSB0
[  978.094457] usb 2-1: GSM modem (1-port) converter now attached to ttyUSB0
[  978.099983] usb 2-1: GSM modem (1-port) converter now attached to ttyUSB1
[  978.497551] option1 ttyUSB1: GSM modem (1-port) converter now disconnected from ttyUSB1
[  978.497654] option1 ttyUSB0: GSM modem (1-port) converter now disconnected from ttyUSB0
[  993.106449] usb 2-1: GSM modem (1-port) converter now attached to ttyUSB0
[  993.108646] usb 2-1: GSM modem (1-port) converter now attached to ttyUSB1
[ 1019.003269] option1 ttyUSB0: GSM modem (1-port) converter now disconnected from ttyUSB0
[ 1019.003375] option1 ttyUSB1: GSM modem (1-port) converter now disconnected from ttyUSB1
[ 1019.367403] usb 2-1: GSM modem (1-port) converter now attached to ttyUSB0
[ 1019.370701] usb 2-1: GSM modem (1-port) converter now attached to ttyUSB1
[ 1031.992275] option1 ttyUSB1: GSM modem (1-port) converter now disconnected from ttyUSB1
[ 1031.992376] option1 ttyUSB0: GSM modem (1-port) converter now disconnected from ttyUSB0
[ 1032.247410] usb 2-1: GSM modem (1-port) converter now attached to ttyUSB0
[ 1032.260317] usb 2-1: GSM modem (1-port) converter now attached to ttyUSB1
[ 1032.659504] option1 ttyUSB1: GSM modem (1-port) converter now disconnected from ttyUSB1
[ 1032.659603] option1 ttyUSB0: GSM modem (1-port) converter now disconnected from ttyUSB0


This is what get when checking with modprobe (if im wrong with using this please say as I said im a total noob so I dunno.

If there is an solution it would be awesome if people can help me with it.

Greetings deamosreapos

---

### Post by Portable_Jim on 2009-12-12
Which company are you with?
Which country are you in?

My Modem (not sure whether it is the same version) if with Virgin, and I am in Australia. I have created a guide that might help, however without the company I cannot help you much. The guide: [http://portablejim.site-hosts.net/tips/90-setting-upvirgin-broadband-usb-modem.html](http://portablejim.site-hosts.net/tips/90-setting-upvirgin-broadband-usb-modem.html).

---

### Post by uidb4056 on 2010-01-04
I have the same USB modem  E220 that worked flawlessly with previous releases but didn't work with Karmic x64 on my Lenovo W500 (kernel 2.6.31.16-generic). Found in Launchpad that this can be solved updating the firmware of modem this link will show you the way and includes a link on Launchpad with explanations ( [http://azizan.aiskosong.net/?p=458](http://azizan.aiskosong.net/?p=458) ).

I've switched to XP where the modem runs without problems, downloaded the firmware and applied it (only the firmware not the dashboard because Launchpad says is not necessary), after the update of firmware in XP I've checked if still runs on it and Yes! it still works and get as a side benefit that the connection now is at 7.2 GB instead of previous 3.6 GB.

Going back to Karmic again now at connection of the USB the internal disk is showed in desktop but , when starts the modem it was started OK but I was not able to navigate ...

Searching for a solution (apparently the problem was no DNS) I edited the wideband connection starting from terminal 'sudo nm-connection-editor' and in the Tab 'Adjusting IPV4' fill the field DNS Servers with the DNS used by XP and then this was solved.

I hope this can help

---

