---
title: "3G modems two similar machines - 1 OK the other not -ideas?"
date: 2012-04-07
forum: General Help
---

### Post by bouncingwilf on 2012-04-07
I have a little problem - my nephew recently bought a Huawei E353 3G dongle but his PC would not "see" it. So I tried it in my desktop - it immediately mounted and gave me a good internet connection. - Silly nephew! one immediately thinks but - I then tried it on my second machine and also on a netbook with no success i.e. one of the 4 machines OK the other three no go!  Now here's the strange part, All 4 machines are running up-to-date versions of 10.04.4 My question is  - where should I look to find why 1 kernel "sees" the device but the other three do not? Clearly if it can work on one then it should be possible to make it work on the other three.


Bouncingwilf

---

### Post by gordintoronto on 2012-04-07
Open a terminal and type the command: uname -a
to see what version of the kernel is being used.

Perhaps the machine where it works has the Backports repository enabled.

---

### Post by bouncingwilf on 2012-04-07
Thanks for the repy - The working machine is on the 2.6.32-40 kernel, the non working netbook is on the 2.6.32.39 kernel but attempts to update are failing on a 404 code (IP not found in the fetch) The IP is cannonical and pingable so something is a bit fishy. Additionally, the netbook seems to be trying to fetch headers for the 2.6.32.39.46 kernel - not what I was expecting. Otherwise, updating appears to be set up the same on the two machines. Sadly, the other two machines are "out of range" at the moment so I will try again later.

Bouncingwilf

---

### Post by bouncingwilf on 2012-04-08
Well, managed to update to the 2.6.32.40 kernel but only after changing the update source from the UK server to the main Server ( interestingly, several other updates, not offered by the UK server, were downloaded - including gcc - are the servers not synced?) 

Result is the same : 1 machine fine with Huawei 353 ; the other does not see it although both are running the same kernel

I can find no differences in the update setup (backports etc.)  Any ideas anyone?

Bouncingwilf

---

### Post by alexfish on 2012-04-08
the 353 can switch two different type of modem one as pure 3g and another as 3g + ether interface which provides faster interface , only thing can suggest is to use sakis3g to configure the device

but prior two using sakis3g . but disable the switching in the /etc/usb_modeswitch.config .. before trying / sakis3g will configure the ppp to use port forwarding so / my help with the server errors

you may spot differences of the interface using "lsusb -t"  or depending on version libusb "usb-devices"

also this device requires the Huawie Drivers to operate correctly when the Ether interface is present

have done a post here  #[**64**]("http://ubuntuforums.org/showpost.php?p=11709821&postcount=64")

see what happens

---

### Post by 3rdalbum on 2012-04-08
Have you tried plugging it into a different USB port? One of your USB ports might be faulty. Or perhaps your USB's electricity capabilities are overloaded; try unplugging some other USB devices.

---

### Post by bouncingwilf on 2012-04-08
> **3rdalbum said:**
> Have you tried plugging it into a different USB port? One of your USB ports might be faulty. Or perhaps your USB's electricity capabilities are overloaded; try unplugging some other USB devices.

Yes thanks but I've tried multiple USB slots on Multiple machines - still just the one working. 

Thanks Alexfish, Ill have a look at your suggestions. The situation is not critical but I like to know why these things happen.


Bouncingwilf

---

### Post by bouncingwilf on 2012-04-08
Many thanks all - I'm going senile I was absolutely convinced I'd installed usb-modeswitch but guess what - when I checked it wasn't there!

Bouncingwilf

---

### Post by gordintoronto on 2012-04-09
Did that solve the problem? If so, please use Thread Tools to mark the thread as "solved."

---

