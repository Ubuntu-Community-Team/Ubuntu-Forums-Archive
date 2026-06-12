---
title: "Sagem My C4-2"
date: 2006-03-22
forum: General Help
---

### Post by dumbbeatnix on 2006-03-22
Help Needed

Any ideas on how to connect a Sagem My C4-2 to linux through a cable.

The cable is a USB one.

Some technical stuff:

I installed bluetooth and followed commands given to me by the ubuntu community.  Here are a few things:

lsusb (originally)
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 002: ID 1241:1503 Belkin
Bus 001 Device 001: ID 0000:0000

lsusb (mobile in computer via usb cable)
Bus 002 Device 007: ID 067b:2303 Prolific Technology, Inc. PL2303 Serial Port
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 002: ID 1241:1503 Belkin
Bus 001 Device 001: ID 0000:0000

hcitool scan
Device is not available: No such device

You can see my problem, the phone obviously isn't bluetooth compatible.  I am wondering just what needs to be done.

Thanks in Advance
dumbbeatnix [-(

---

### Post by dumbbeatnix on 2006-03-24
Hello Again

I forgot to include my dmesg (when the device is connected), it is attached.

Its a bit long and I dont seem to understand it.  Has anyone successfully used the PL2303 converter.  What package would I need?  I have WinCE plug in for MultiSync and am still puzzled.  I created the link ln -b ttyUSB0 ttyS2 to try and get the thing to recognise the driver.

Going around in circles :-k 
Peter Greenfield

---

### Post by dumbbeatnix on 2007-05-30
Hello Everyone and Those Who Read New Posts

Success at last.  Yes I have nailed this one.

[As usual dumbbeatnix rambles on]

I was flicking through some magazine and came accross something interesting.  Ericsson was taking over Sagem, this intrigued me because I have had numerous problems with Sagem and Linux.  Most people have, it is documented on several web sites and I do believe some out of the way blogs.

Wait you say, dumbbeatnix is going to tell me to buy an Ericsson phone.  Come on, you know old skin flint dumbbeatnix wouldn't dream of spending his hard money.  So I aint goin' to tell you to buy a new phone, simply to install KMobileTools and do the following [for a sagem my c4-2]:

If you dont have a screen asking you for options look for the options in the menu's.  Then simply ask for defaults, then tell the program you have an Ericsson phone.  Go to the Phone section [as I said tell it it's an ericsson] and then goto Device and put /dev/ttyUSB0 into the Mobile phone device.

The functionality is limited and I will go through some more options later, hopefully if I can get other programs to behave like this one.  But, you can get Phone Book and SMS, I haven't tried Dialling but will and let everyone know.

Cheers  :popcorn:
dumbbeatnix

---

### Post by dumbbeatnix on 2007-06-06
Hello Everyone Interested

Since looking into Ericsson and its similarity to Sagem I have been able to get Wammu to work for the Sagem my c4-2.  Its a little bit complicated, and all you get is basic address book stuff.  Later I hope to get in and get dirty with some of the code for Gammu and change this.  Why?  Because KMobileTools uses an initiation string that I haven't been able to get with Gammu or Wammu.

Anyway I have attached a .gammurc which you place in your /home/[user] directory.  Then you need to specify the following in Wammu:

Goto Wammu -> Settings
Device:             /dev/ttyUSB0
Connection:      fbuspl2303
Model:             at
Check the box Automatically connect phone at startup

Then you should be able to get your address book.  Currently other methods don't work, such as SMS.  I hope to get in and work on these to get something going.

If anyone out there tries this, can I offer this advice (that I offered someone emailing me about this issue):

Please! Please! Please!
If you are Windows dependant, ie. you use Windows exclusively or you have a partition dedicated to it.  Use the Live CD and install what you need, or if you dont have it use Peanut Linux or something like that to see if it works on your computer.  But everything I have done here, I have reproduced.  In other words, I have got rid of the software and reconfigured it upon its return.

Happy days for those using mobile devices are coming .......... Soon.

Cheers
dumbbeatnix:p

---

### Post by ashlakim on 2008-01-31
Just what im looking for! Wrks like a charm for myNokia 7600!

---

