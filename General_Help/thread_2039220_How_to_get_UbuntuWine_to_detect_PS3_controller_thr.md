---
title: "How to get Ubuntu/Wine to detect PS3 controller through USB?"
date: 2012-08-08
forum: General Help
---

### Post by veroslav on 2012-08-08
Hi,

I need some help in order to configure my PS3 controller in Ubuntu 12.04 and use it for playing games I've installed in Wine 1.4.

I don't have bluetooth on my computer so I am trying to get it to work through USB connection only. What I have been doing is the following:

sudo apt-get install libusb-dev libusb-0.1-4

and then downloading, compiling and trying to run sixpair with:

./sixpair

sixpair then complains about missing bluetooth or something similar and then I am stuck. In all of the tutorials I've found they are talking about blutooth pairing which is not what I am trying to do. I believe that sixpair is used for blutooth pairing only but I might be wrong.

I've also stumbled across a tool named QtSixA which I understand is used for pairing of the PS3 and the computer. It detects my PS3 controller and displays it in it's GUI, but I lack knowledge of what to do next.

This is as far as I have come, I would really appreciate any pointers as to what to do next.

Whan I connect the controller through USB, the lights start continuously flashing but I am unable to do anything with the controller and there is no response to pressing any buttons while running games in wine.

Thanks in advance.

@MODS: I was unsure whether to post in this or in Gaming/Wine forum, please feel free to move the thread if necessary.

Kind Regards,
Veroslav

---

### Post by darkapec on 2012-08-08
I have used the PS3 controller (with a usb cord) through wine without any issues. I was however using it on a gameboy emulator, all I had to do was plug and play. Download BGB emulator from [http://www.emulator-zone.com/doc.php/gameboy/bgb.html](http://www.emulator-zone.com/doc.php/gameboy/bgb.html) 

run it via wine then browse through the menu until you find an option configure the gamepad and try to push buttons on the ps3 controller and see if they are registering.

---

### Post by veroslav on 2012-08-08
Thank you for the fast reply, darkapec.

I will have a go at it when I am at home later tonight.

My understanding has always been that you shouldn't need to do anything special in order to get it to work through USB, and that it was only blutooth that needed work, but it seems as though that is not the case.

Thanks again.

Regards,
Veroslav

---

### Post by MarjaE on 2012-08-08
There are a couple threads on how to get joysticks and gamepads [not sure what gamepads are] to work in Ubuntu. I wrote this one because I wanted to use a joystick as a more ergonomic substitute for a mouse:

[http://ubuntuforums.org/showpost.php?p=12121440&postcount=3](http://ubuntuforums.org/showpost.php?p=12121440&postcount=3)

Maybe this will help with the PS3 controller too. Maybe some of the steps won't be necessary.

---

### Post by veroslav on 2012-08-15
Hi again,

thank you for all of the replies. After further research, I came to the conclusion that it is very hard, if not possible to pair the controller through USB but much easier to do it through bluetooth.

It seems that it is straight forward to get Ubuntu to register the input from the controller when on USB, but to get anything meaningful from the input seems impossible.

I've found an old USB bluetooth dongle and I am going to try to connect it this way instead.

The first thing I need to do is to find and install the drivers for the dongle, and I have already posted a thread about this in the Wireless forum.

Thanks again!

---

