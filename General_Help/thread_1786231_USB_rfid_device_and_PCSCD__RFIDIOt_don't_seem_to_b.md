---
title: "USB rfid device and PCSCD / RFIDIOt don't seem to be working together"
date: 2011-06-19
forum: General Help
---

### Post by F.G. on 2011-06-19
hi folks,
i'm posting this regarding a crunchbang #! installation on one of my computers not ubuntu, so beware.  though i remember having a similar issue with ubuntu a while back (i got it sorted, though can't remember how), so thought i'd post here as well as the #! forum.  
I'm trying to get RFIDIOt to run with my rfid reader and can't for the life of me figure out what is wrong.  If anyone knows about configuring RFID readers / PCSCD / RFIDIOt i could do with some guidance.  It seems that it shows up in my computer yet PCSCD does not see it.

the output from /var/logs/messages is:

```
Jun 19 13:36:20 crunchbang kernel: usb 5-2: new full speed USB device using uhci_hcd and address 4
Jun 19 13:36:20 crunchbang kernel: usb 5-2: New USB device found, idVendor=0403, idProduct=dd20
Jun 19 13:36:20 crunchbang kernel: usb 5-2: New USB device strings: Mfr=1, Product=2, SerialNumber=3
Jun 19 13:36:20 crunchbang kernel: usb 5-2: Product: USB Converter
Jun 19 13:36:20 crunchbang kernel: usb 5-2: Manufacturer: ACG Austria
Jun 19 13:36:20 crunchbang kernel: usb 5-2: SerialNumber: 40521887
Jun 19 13:36:20 crunchbang kernel: ftdi_sio 5-2:1.0: FTDI USB Serial Device converter detected
Jun 19 13:36:20 crunchbang kernel: usb 5-2: Detected FT232BM
Jun 19 13:36:20 crunchbang kernel: usb 5-2: Number of endpoints 2
Jun 19 13:36:20 crunchbang kernel: usb 5-2: Endpoint 1 MaxPacketSize 64
Jun 19 13:36:20 crunchbang kernel: usb 5-2: Endpoint 2 MaxPacketSize 64
Jun 19 13:36:20 crunchbang kernel: usb 5-2: Setting MaxPacketSize 64
Jun 19 13:36:20 crunchbang kernel: usb 5-2: FTDI USB Serial Device converter now attached to ttyUSB0
```

and in /dev it shows up as: 
```
ttyUSB0
```

now if I run pcsc_scan I get this indefinitely:
```
Compiled with PC/SC lite version: 1.5.5
Scanning present readers...
Waiting for the first reader...

```

and if I try to run an RFIDIOt tool eg readtag.py i get:
```
bob@crunchbang:~/documents/RFIDIOt-1.0a$ ./readtag.py
There is no such reader #1, PCSC sees only 0 reader(s)

```

the relevant part of my RFIDIOtconfig.py file reads like this:
```
# ignored for PCSC
#line= "/dev/ttyS0"
#line= "/dev/ttyS1"
line= "/dev/ttyUSB0"
# for Windows
#line= "COM4"

# reader type (can be overridden with -R)
#readertype= RFIDIOt.rfidiot.READER_ACG
#readertype= RFIDIOt.rfidiot.READER_FROSCH
#readertype= RFIDIOt.rfidiot.READER_DEMOTAG
# READER_PCSC is a meta type. Actual subtype will be auto-determined.
readertype= RFIDIOt.rfidiot.READER_PCSC
#readertype= RFIDIOt.rfidiot.READER_NONE
#readertype= RFIDIOt.rfidiot.READER_LIBNFC
```

which I think makes sense, however if I change the readertype to RFIDIOt.rfidiot.READER_ACG rather than PCSC. which kind of makes sense (I have an ACG reader) then I get this error from readtag.py:
```
bob@crunchbang:~/documents/RFIDIOt-1.0a$ ./readtag.py
Could not open serial port /dev/ttyUSB0

``` 

so, I don't really see what the problem is? I can see ttyUSB0 is my ACG card reader, my computer knows that, yet it seems PCSCD does not, and trying to do it without PCSCD does not work either. and I think all the python deprndencies are met.  
sorry about the length of this post, I just wanted to be specific.  if anyone is still reading and has any ideas I would extreemly grateful. I'm about to start a MSc project on tag cloning/emulation and the security of the mifare classic, so it is somewhat critical that i do figure this out somehow at some point.
thanks for any help or advice.  
f.g.

ps oh yes, it also shows up under lsusb as:
```
Bus 005 Device 004: ID 0403:dd20 Future Technology Devices International, Ltd 

```

---

### Post by mensfort on 2011-06-24
Hi,

I also have RFID problems. Some ideas which may help:

Start terminal:

ps aux | grep pcscd
# then you will see 2 of them, one is your search. The other starts with a number, e.g. 1234

kill -9  1234 

#now start pcscd again:
sudo pcscd -df

#if this works, we can put it in udev rules.

---

### Post by F.G. on 2011-06-27
hey, 
thanks for the reply, i got my reader working without using pcscd (it is an acg reader and i configured it as a serial device without using pscsd), it is now working fine with RFIDIOt , rfdump and cutecom, I don't what the problem was before, so i don't have a solution. 
mensfort, if you do have rfid reader issues and post the problem specifics, i may have some ideas, as i spent a while figuring this out.
I did however try 'kill' the appropriate PID and restart it with sudo, though this didn't really make a difference.

---

