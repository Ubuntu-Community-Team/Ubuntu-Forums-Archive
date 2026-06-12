---
title: "Serial Terminal"
date: 2009-09-28
forum: General Help
---

### Post by Psycho.mario on 2009-09-28
I recently got a PDA (HP iPaq h1940). I put on putty and i was planning on using it to connect to my computer. My wifi card has not been delivered yet, so i am trying to use the COM1 port. The USB cable runs from the PDA to my computer, it shows up as COM1 on the PDA, and /dev/ttyUSB0 and /dev/serial on my computer. I was wondering, how could i set this up so that i can connect with putty, to COM1, to my computer, and let it give me a login prompt and a terminal, so i can run programs.
Basically, i want a terminal on my PDA from my computer over USB

Thanks

---

### Post by Psycho.mario on 2009-09-28
Bump

---

### Post by jonobr on 2009-09-28
Hello


Just woindering if you are able to connect to the PDA using a serial connection? Are you sure it allows that ?

If it does, then I would first check that your using the correct tty port

You can do this as follows, and Im showing mine as an example

```
me@here:~$ dmesg | grep tty
[    0.004000] console [tty0] enabled
[    2.030661] serial8250: **ttyS0** at I/O 0x3f8 (irq = 4) is a 16550A
[    2.030777] serial8250: **ttyS1** at I/O 0x2f8 (irq = 3) is a 16550A
[    2.031243] 00:08: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    2.031411] 00:09: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[    2.440137] tty tty29: hash matches

```

You can see above (bolded) I have two ports available to me.

From there, I prefer to use minicom

If you type in 

```
minicom -s
```
ion a terminal window it will start the program
(see attached graphic)

From there setup the serial connection speed by hitting s.
From there you need to put in the correct settings, usually its 8N1 and the speed normally defaults to 9600.
If your pda support its, then its probably documented somewhere.

Cheers

---

### Post by jonobr on 2009-09-28
Adding attachment as referred in previous post

---

### Post by Psycho.mario on 2009-09-28
I don't have a serial:
```
rory@rory-desktop:~$ dmesg | grep tty
[    0.004000] console [tty0] enabled
[   10.998631] usb 7-2: PocketPC PDA converter now attached to ttyUSB0
[  178.713503] ipaq ttyUSB0: PocketPC PDA converter now disconnected from ttyUSB0
[  360.961229] usb 7-2: PocketPC PDA converter now attached to ttyUSB0
[  374.153485] ipaq ttyUSB0: PocketPC PDA converter now disconnected from ttyUSB0
[  636.985812] usb 7-2: PocketPC PDA converter now attached to ttyUSB0
[  952.241737] ipaq ttyUSB0: PocketPC PDA converter now disconnected from ttyUSB0
[  965.335787] usb 7-2: PocketPC PDA converter now attached to ttyUSB0
[ 1076.241482] ipaq ttyUSB0: PocketPC PDA converter now disconnected from ttyUSB0
[ 1089.072998] usb 7-2: PocketPC PDA converter now attached to ttyUSB0
[ 1253.314497] ipaq ttyUSB0: PocketPC PDA converter now disconnected from ttyUSB0
[ 2144.580630] usb 7-2: PocketPC PDA converter now attached to ttyUSB0
[ 2361.630703] ipaq ttyUSB0: PocketPC PDA converter now disconnected from ttyUSB0
[ 2543.857188] usb 7-2: PocketPC PDA converter now attached to ttyUSB0
[ 2557.049504] ipaq ttyUSB0: PocketPC PDA converter now disconnected from ttyUSB0
[ 2843.690238] usb 7-2: PocketPC PDA converter now attached to ttyUSB0
[ 2857.129487] ipaq ttyUSB0: PocketPC PDA converter now disconnected from ttyUSB0
[ 3143.777819] usb 7-2: PocketPC PDA converter now attached to ttyUSB0
[ 3156.961493] ipaq ttyUSB0: PocketPC PDA converter now disconnected from ttyUSB0
[ 3443.573212] usb 7-2: PocketPC PDA converter now attached to ttyUSB0
[ 3457.041768] ipaq ttyUSB0: PocketPC PDA converter now disconnected from ttyUSB0
[ 3743.687914] usb 7-2: PocketPC PDA converter now attached to ttyUSB0
[ 3757.121497] ipaq ttyUSB0: PocketPC PDA converter now disconnected from ttyUSB0
[ 4043.520461] usb 7-2: PocketPC PDA converter now attached to ttyUSB0
[ 4056.954326] ipaq ttyUSB0: PocketPC PDA converter now disconnected from ttyUSB0

```

I connected and disconnecet the PPC a few times.

If i run:

ls /dev > before
ls /dev > after
diff before and after
(before and after plugging in the PDA)
the differences are /dev/serial and /dev/ttyUSB0 and /dev/usbdev*   (This one changes each time)

Thanks for the help sofar

---

### Post by jonobr on 2009-09-28
Im thinking connecting using USB is going to be the same?

It would be worth the shot of placing ttyUSB0

in the /dev/tty section and see what happens,

I believe its the same thing just the cable your using is using a different tty number.

If you setup minicom that way, and restart the pda,
if you see anything on your screen it would be a start, it may be just speed you need to change.

It may also be worthwhile, trying with Hyperterm on a windoze box,

windoze hyperterm does a good job of identifying and supplying the new com number when you plug in the device.
If you select that, it maygive you a pointer of what you should expect to see when you use minicom

---

### Post by Psycho.mario on 2009-09-29
I found that if i execute:
[CODE]getty 115200 rfcomm0/CODE]
i get a shell (I set it up to use bluetooth now) with login. I created a new user (becuase my password is awful to type in on a PDA) and i now have a shell  :)
Thanks for all the help

How do i get it to run that command on boot corrently? I heard of something called upstart, but im not sure how to use it

Thanks

---

### Post by jonobr on 2009-09-29
Hello

Glad to hear its doing something,.

FOr automatically starting it,
you should create a startup script which can be executed at boot time.,
you could use vi or gedit
open a terminal and type

```
gedit ipaqshell 
```

this will open a new text editor screen.

Enter your commands and save the file.
It should place a file called ipaqshell in your home directory.

You could run this script to start the program but to start at boot time, you could go to preferences and startup applications/

in there click add and then navigate to your script so it executes at boot,
hopefully that will work.

A couple of other things to consider is, in the file, you could end with an & symbol, this will make the thing run as a background task.
You could also redirect any output to not appear on your screen by entering > /dev/null

(dev null is the linux equivalent of throwing something into a black hole, never to be seen again.)

---

### Post by Psycho.mario on 2009-09-30
Or i could chuck it on the end of /etc/rc.local.
theres no output.
I might just leave it to manual, its only a short command (getty 115200 /dev/rfcomm0)

Thanks for all the help

---

### Post by jonobr on 2009-09-30
Sure thing,

Although I think you did all the work yourself

---

