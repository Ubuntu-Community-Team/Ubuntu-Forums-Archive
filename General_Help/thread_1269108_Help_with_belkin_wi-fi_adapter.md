---
title: "Help with belkin wi-fi adapter"
date: 2009-09-17
forum: General Help
---

### Post by timinator94 on 2009-09-17
Hello fellow ubuntuians, i seem to be having problems with my belkin model f5d6050 usb wi-fi interface. I cant connect to any access point. I may just be naive because im new to ubuntu. Oh by the way im running 9.04 if that helps.
Thanks,
           Timinator94

---

### Post by Vaphell on 2009-09-17
but it scans the networks just fine?

i had to solve connection problems once on a notebook with 8.04. My solution was quite dirty, but worked nevertheless.

i installed wpasupplicant and wpagui and used that wpagui to manage connections

---

### Post by timinator94 on 2009-09-18
Im totally new to the ubuntu thing so you will have to really be specific.

---

### Post by Vaphell on 2009-09-18
i assume that your wifi adapter is detected and shows some networks in a network manager?

goto synaptic
search wpasupplicant and wpagui, select them to install, apply

run wpagui from terminal

---

### Post by trash on 2009-12-27
wpa_gui, doesn't even see the adapter:(.. i'm posting here because this is the latest thread involving a belkin f5d6050 adapter... sad part is that this adapter has worked out of the box in previous releases.
Ubuntu network manager won't even show any signal strength but shows wireless networks available.
Kubuntu fares a bit better and actually shows theres a signal but refuses to aquire IP. It does however show that it is using at76c50x-usb driver but i have no clue if this driver is the right one or not.
anybody?

---

### Post by marshag63 on 2009-12-27
Timinator94, if you can make your way to a terminal type in:

ifconfig 

ifconfig should tell you if you have a wlan/wlan0 interface - if you do not, there is no driver installed.

lsusb

lsusb will tell you the usb devices connected to your computer - you should see your belkin usb device listed. 

I have a belkin usb device as well - I used ndiswrapper/ndisgtk and the windows XP *.inf file - easy to install via GUI.

Let us know what you come up with.

Marshag

---

### Post by trash on 2009-12-27
I would like to try the ndiswrapper but the driver i downloaded from the smc website is .exe and will not install.. what is the name of the required .ini file that i need.. I also don't have XP so getting the drivers seems impossible:(

> **marshag63 said:**
> 
I have a belkin usb device as well - I used ndiswrapper/ndisgtk and the windows XP *.inf file - easy to install via GUI.

Let us know what you come up with.
Marshag

---

### Post by marshag63 on 2009-12-27
Trash,
If the file ends in .exe - its meant to run in windows. 

To use ndiswrapper, you need the "*.inf" file - if you have the windows install CD, the driver would be on there possibly "Drivers > Windows XP directory - try the Windows XP driver.  

If you have access to a windows computer you can download the driver stuff there and then just copy the *.inf file to a USB stick and copy into linux.
(the "*" part equals file name such as rlt8180.inf) - you have to know what chipset is used in the adapter.

Remember, linux is not windows - things are done a bit differently.

MarshaG.

---

### Post by trash on 2009-12-27
Yes, i understand that, the driver i download was to get the .ini file i need.. sadly one has to run the setup.exe(i presume) to get at the .ini file needed. I did try running it in wine but it crashed before installing anything.
I asked for the filename because that way at least i have a chance of finding it on the net.

> **marshag63 said:**
> Trash,
If the file ends in .exe - its meant to run in windows. 

To use ndiswrapper, you need the "*.inf" file - if you have the windows install CD, the driver would be on there possibly "Drivers > Windows XP directory - try the Windows XP driver.  

If you have access to a windows computer you can download the driver stuff there and then just copy the *.inf file to a USB stick and copy into linux.
(the "*" part equals file name such as rlt8180.inf) - you have to know what chipset is used in the adapter.

Remember, linux is not windows - things are done a bit differently.

MarshaG.

---

### Post by marshag63 on 2009-12-27
Trash, 
Read the thread - I think you need to blacklist the at76c50x (see post #5) driver so it uses the old one already built in:

[http://swiss.ubuntuforums.org/showthread.php?p=8051588](http://swiss.ubuntuforums.org/showthread.php?p=8051588)


MarshaG.

---

### Post by trash on 2009-12-27
no idea, what it says on the device itself is smc2662w v.2 usb ezconnect
lsusb is what tells me it's a belkin f5d6050.. how would i find a version #?

> **marshag63 said:**
> Trash, just to verify - this is a Belkin f5d6050 usb device?  Do you know the version number?

I have a f5d7050 USB device.

MarshaG.

---

### Post by mark bower on 2009-12-27
Belkin USB 5FD7050 works out of the box with 9.04; i have had instant success on 3 PCs and 1 laptop with Unbuntu 9.04.  It's about $35, but eliminates the agony.  Ubuntu has the native drivers on board.

mark

---

### Post by trash on 2009-12-27
Good to know! this one has worked out of the box to in previous releases thats why i don't understand why it just got a whole lot more complicated:(

> **mark bower said:**
> Belkin USB 5FD7050 works out of the box with 9.04; i have had instant success on 3 PCs and 1 laptop with Unbuntu 9.04.  It's about $35, but eliminates the agony.  Ubuntu has the native drivers on board.

mark

---

### Post by marshag63 on 2009-12-27
Trash,
Plesae see post #10 of this thread (I found a solution).

MarshaG.

---

### Post by trash on 2009-12-27
No joy, after blacklisting at76c50x_usb, it uses the driver at76_usb and everything behaves the same way. doesn`t crash though LOL

> **marshag63 said:**
> Trash,
Plesae see post #10 of this thread (I found a solution).

MarshaG.

---

### Post by bkratz on 2009-12-27
Please see this listing

[http://ubuntuforums.org/showthread.php?t=1117162&highlight=f5d6050](http://ubuntuforums.org/showthread.php?t=1117162&highlight=f5d6050)

especially post 11 it tells you how to extract the file you need.

---

### Post by marshag63 on 2009-12-27
Trash,
Check an "lsmod" and see what module your wireless is now using.

You may have to modprobe the at76 or module.

MarshaG.

---

### Post by trash on 2009-12-27
looked promising but all i get is failed to extract as cabinate file:(

> **bkratz said:**
> Please see this listing

[http://ubuntuforums.org/showthread.php?t=1117162&highlight=f5d6050](http://ubuntuforums.org/showthread.php?t=1117162&highlight=f5d6050)

especially post 11 it tells you how to extract the file you need.

---

### Post by trash on 2009-12-27
I tried to blacklist both and then modprobed each seperately, still no change.
Dud driver??

> **marshag63 said:**
> Trash,
Check an "lsmod" and see what module your wireless is now using.

You may have to modprobe the at76 or module.

MarshaG.

---

### Post by trash on 2009-12-27
!! turns out that even though the setup program crashed it did install the .inf file i needed for the ndiswrapper.
Sad part is that it will still not connect even though it sees a much stronger signal. It also sees my router as WEP instead of WAP which is what i have to use on my router.

---

### Post by SeaJayEmm on 2009-12-27
Does this device use rt2870.inf? By the way you will need the .sys as well as the .inf file to install with ndiswrapper. If you are new to linux I would ndisgtk instead.

---

### Post by trash on 2009-12-27
neither one will allow me to and anything besides an inf file.
the inf file i add was named something like smcusb.inf
i might try and run the setup bkratz posted

> **SeaJayEmm said:**
> Does this device use rt2870.inf? By the way you will need the .sys as well as the .inf file to install with ndiswrapper. If you are new to linux I would ndisgtk instead.

---

### Post by bkratz on 2009-12-27
> **trash said:**
> neither one will allow me to and anything besides an inf file.
the inf file i add was named something like smcusb.inf
i might try and run the setup bkratz posted

@Trash

I just read through the whole link again, and I never saw ( perhaps I missed it ) but I never saw where the actual chipset was determined. Yes, it is a Belkin device, but when you typed in lsusb (LSUSB in lowercase) did it show a series of numbers such as

xxxx:xxxx   (that is a colon ( I never remember how to get rid of the faces!))

 near the name of the device ? This would identify what the chipset used is. All those manufacturers change devices internally and never tell anyone. At least we would know what the drivers should be. Again I apologize ( and ignore this posting)  if this was discussed somewhere, but I missed it (three times!) if it is there somewhere.

Also, a lot of people (me included!) are having problems with ndiswrapper and any type of encryption in 9.10. Unencrypted is fine, but mine is setup to WPA2.  I rolled back to 9.04 just for that. I did test the version due out in April (10.04) and everything was back to working (including my Intel video which became choppy in 9.10) so I am skipping 9.10 as a personal preference and eagerly waiting a little longer in the development cycle for the LTS ( long term support) version.

Subscribing to the thread.

---

### Post by trash on 2009-12-27
OH THAT # !!! 0d5c : a002

I'll go back to that thread and see.. thanks!!

---

### Post by trash on 2009-12-27
well this might sum it up...

[http://wiki.debian.org/at76_usb](http://wiki.debian.org/at76_usb)

---

### Post by marshag63 on 2009-12-27
;)

lsmod

MarshaG.

---

### Post by trash on 2009-12-27
well it is using the right module loading and always has been it's the WAP part that seems to be the issue. so there ain't much i can do about it since i have to stay with WAP.. guess i'm stuck with the blue cable for a while longer lol

> **marshag63 said:**
> ;)
lsmod
MarshaG.

@bkratz.. i only had to upgrade to 9.10 because i was hit with that random network freeze problem in 9.04.. I am now returning to linux after almost 6 months running vista!

---

### Post by bkratz on 2009-12-28
> **trash said:**
> well it is using the right module loading and always has been it's the WAP part that seems to be the issue. so there ain't much i can do about it since i have to stay with WAP.. guess i'm stuck with the blue cable for a while longer lol



@bkratz.. i only had to upgrade to 9.10 because i was hit with that random network freeze problem in 9.04.. I am now returning to linux after almost 6 months running vista!

Sure does if you are referring to the statement on the Debian website mentioned where it says

"Known Issues

The at76_usb and at76c50x-usb drivers do not support WPA or master mode operation."

---

### Post by timinator94 on 2010-06-10
Marking as solved because 9.10 fixes this issue and because I just bought a laptop. Thanks yall:guitar:

---

