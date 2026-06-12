---
title: "fatal error: linux/smp_lock.h: No such file or directory"
date: 2012-01-27
forum: General Help
---

### Post by enak101 on 2012-01-27
Hey guys, I'm pretty new to linux and ubuntu but it's fairly awesome. I'm just trying to set up my xbox controller which is helping out with my linux skills. I'm stuck on


fatal error: linux/smp_lock.h: No such file or directory

which is in xpad.c file. Removing it just made more errors

The guide I am following is here. [https://help.ubuntu.com/community/Xbox360Controller](https://help.ubuntu.com/community/Xbox360Controller)

So yah, fairly confused.

It happens when I type make in which opens the makefile which I'll actually take a look at now :P.

Any help would be appreciated.
Edit: Can't see anything wrong in make file.
Edit: Ah yeah, using wubi if that makes a difference. Dragging windows is fairly slow compared to windows, is that a wubi thing?

---

### Post by Sazhen86 on 2012-01-28
First off, which version of Ubuntu are you using as I believe that header file went away at some point in the kernel development.

Otherwise you can find it in the kernel headers, usually at /usr/src/linux-headers-xxx (where xxx is the value from "uname -r")

Check whether you have the kernel headers package installed:

dpkg -l | grep linux-headers

and then check the makefile to see if it includes the kernel headers directory in the compiler's command line.

Hope that helps.

---

### Post by enak101 on 2012-01-28
Ubuntu 11.10 it's recent enough. I'll check it out now.

I assume there is no use looking for it with this version but after usr/src/linux-headers-xxx where would I check?

I don't quite get the directory system yet so that doesn't make too much sense. Check makefiles for dpkg?

---

### Post by Sazhen86 on 2012-01-28
You could always try the following command to see if it exists anywhere on your disk:

sudo find / -name smp_lock.h -print

You'll need to enter your password as it uses sudo.

It searches the whole file system so it could take a while, but it will tell you anywhere and everywhere a file with that name exists.

Do you have any directories in /usr/src?  Try:

ls -l /usr/src

Hope that helps

---

### Post by enak101 on 2012-01-28
Yeah, the sudo find command just didn't show anything after about 45 seconds of just being standstill. Then it showed my command line thing. 

I have directories. linux headers 3.0.0.12
3.0.0.15
generic versions of both of them and 
nvidia 280.13 drivers or such. 

Do I need to obtain smp_lock.h from somewhere and place it somewhere in order for this to work?

---

### Post by Sazhen86 on 2012-01-28
The instructions you are following are for an old version of Ubuntu where the kernel didn't include the xpad driver.  More recent versions, including 11.10, should have that module available already, so you don't need to build it.  Try

sudo modprobe xpad

and then:

dmesg

It should show something like:

[70253.710849] usbcore: registered new interface driver xpad
[70253.710856] xpad: X-Box pad driver

Hope that helps.

---

### Post by enak101 on 2012-01-28
I assume you meant modprobe instead of modprob. Thanks. ONly issue is now 

It says usbcore:registered new interface driver xpad

Then I attempt so sync it and it's still flashing rather than connecting a number from 1-4 

I read that it can actually do that on linux and still be connected.

How can I test if it is working? THe controller that is.

---

### Post by Sazhen86 on 2012-01-28
Sorry, I did mean modprobe.  I've edited the post in case anyone else reads it.

To test it, you can probably use js_demo which you can install with the joystick package:

sudo apt-get install joystick

then run 

js_demo

Hope that helps.

---

### Post by enak101 on 2012-01-28
Thanks for the help. I installed the package and it says that it I haven't installed the 600+mb flight sim package or something :confused:

That happens when I type in the js_demo 

I'm mucking around in tux kart and I can see that it is working but I can't accelerate for some reason. I think when I press the button it's 'spamming' the press over and over. That's why the menu is working but accelerating isn't. Any thoughts?

---

### Post by Sazhen86 on 2012-01-28
I'm using 10.04, so I didn't have any problems installing the joystick package.  I'll have to install 11.10 in a VM to see why that happens.

It's a shame, because we really could use the js_demo and jstest programs working to see what is going on.

I also don't have an XBox controller, so I can't try that bit :-(

I'll be going offline shortly to get some sleep, so hopefully someone else can step in and help out. 

Cheers

---

### Post by enak101 on 2012-01-28
No problem, you have been a big help. I'll test some more.

---

### Post by enak101 on 2012-01-28
Hmm, I can type in jstest and it says it has the modes 

--normal
--old
--event
--nonblock
--select

I put the command jstest normal Generic X-Box pad in

I get all sorts of errors

It says to put it as

jstest [<mode>] <device> but it seems I can't get the syntax right.

jstest [<normal>] <Generic X-Box pad> gives

bash:syntax error near unexpected token 'newline'

jstest <normal> <Generic X-Box pad> gives

bash:syntax error near unexpected token '<'

jstest [normal] <Generic X-Box pad> gives

token near newline

jstest normal <Generic X-Box pad>

as above.

I'm really confused as to what to type to get jstest to work. Tuxkart says my devices name is Generic X-Box pad. ANd still can't get js_demo to work in 11.10.

---

### Post by Sazhen86 on 2012-01-28
Hi

The jstest program is looking for the device that the joystick is using.  Linux/Unix uses special files in the /dev directory to represent devices that are present on the system, including joysticks and game pads.  

Hopefully the device you want will be called /dev/js0 for the first joystick device.

The first part of the command, which wants the mode, needs the two dash characters to be included which is a common way of specifying options to unix programs.  Sometimes there is a short option with a single dash, such as -d or a long option with two dashes such as --device.

The command you probably want is:

jstest --normal /dev/js0

Hope that helps.

---

### Post by enak101 on 2012-01-28
Welcome back :D

Ran jstest --normal /dev/js0 and I get

jstest: No such file or directory

should I try
cd
mkdir jstest

?

edit:that didn't seem to work.

---

### Post by Sazhen86 on 2012-01-28
Hi

jstest is just telling you that it can't find the device for your controller.  You can take a look in /dev by typing:

ls /dev

and see if there are any files starting with js in there. 

Can you also unplug the device, plug it back in and post any relevant lines from the output from:

dmesg

Cheers

---

### Post by enak101 on 2012-01-28
input: Generic X-Box pad as /devices/pci0000:00/0000:00:13.0/usb5/5-2/5-2:1.0/input/input11
[   47.299749] input: Generic X-Box pad as /devices/pci0000:00/0000:00:13.0/usb5/5-2/5-2:1.2/input/input12
[   47.299817] input: Generic X-Box pad as /devices/pci0000:00/0000:00:13.0/usb5/5-2/5-2:1.4/input/input13
[   47.299890] input: Generic X-Box pad as /devices/pci0000:00/0000:00:13.0/usb5/5-2/5-2:1.6/input/input14
[   47.299937] usbcore: registered new interface driver xpad
[17290.118895] tuner 1-0061: tuner type not set
[17290.127333] tuner 1-0061: tuner type not set
[18013.951222] usb 5-2: USB disconnect, device number 2
[18013.954747] xpad: xpad_irq_in - usb_submit_urb failed with result -19
[18013.954762] xpad: xpad_irq_in - usb_submit_urb failed with result -19
[18013.954772] xpad: xpad_irq_in - usb_submit_urb failed with result -19
[18039.036064] usb 5-2: new full speed USB device number 3 using ohci_hcd
[18039.207440] input: Generic X-Box pad as /devices/pci0000:00/0000:00:13.0/usb5/5-2/5-2:1.0/input/input15
[18039.207958] input: Generic X-Box pad as /devices/pci0000:00/0000:00:13.0/usb5/5-2/5-2:1.2/input/input16
[18039.208504] input: Generic X-Box pad as /devices/pci0000:00/0000:00:13.0/usb5/5-2/5-2:1.4/input/input17
[18039.208952] input: Generic X-Box pad as /devices/pci0000:00/0000:00:13.0/usb5/5-2/5-2:1.6/input/input18


ls /dev doesn't show anything promising.

---

### Post by Sazhen86 on 2012-01-28
Hi

Is there anything useful looking in /dev/input

Cheers

---

### Post by enak101 on 2012-01-28
js0
js1
js2
js3

---

### Post by Sazhen86 on 2012-01-28
Hi

That looks promising.  Can you try using /dev/input/js0 instead of /dev/js0 with the jstest command:

jstest --normal /dev/input/js0

Cheers

---

### Post by enak101 on 2012-01-28
Great! That works!

Pressing the 'a' button results in numbers spanning across the terminal changing from 0 to 32767. I'm overwhelmed by the program jstest though. Could you elaborate on how it works?

Guess I should elaborate. The problem was acceleration in tuxkart. So if I binded that to a key 'a' for example it wouldn't work. I noticed in the menu pressing a would make it go through 3 menu options at once etc. Like the button was being spammed. How can we apply that to jstest?

edit: pressing 'b' to go back in the game would make it exit the whole program even if I was a few steps in.Meaning the button was pressed about 2 or 3 times from 1 press.

---

### Post by Sazhen86 on 2012-01-29
Hi

jstest just displays the raw state of the joystick input.  It's a good way of finding out whether it works or not.  Normally it displays a single line that shows the state of the axes and the buttons.  I'm guessing that the Xbox controller has too many axes or buttons for it to fit on a single line which is messing up the display.  You could try maximising the terminal window to make it wider to see if it will fit.

This one looks useful:

[http://pingus.seul.org/~grumbel/jstest-gtk/](http://pingus.seul.org/~grumbel/jstest-gtk/)

But it's fairly old and I'm not sure how easy it would be to build.

Cheers

---

### Post by enak101 on 2012-01-29
Ahh okay. It does have alot of axes and jazz it was massive. I get 

file "/usr/lib/scons/SCons/Script/Main.py", line 834, in_main.

THe controller IS definately working though. Just being weird lol. I might try out my guitar.

---

### Post by enak101 on 2012-01-29
My guitar works fine for frets on fire :D

Yeah not sure about my xbox controller problem. That's annoying.

---

### Post by Sazhen86 on 2012-01-29
Hi

Glad the guitar works!

I reckon we need someone else with an XBox controller to step in and help out.  I tried my only joystick ( a logitech stick) and it works OK, so I don't know how to help you out.

Now that we've got it sort of working, I recommend that you start a new post with a different title, something to do with XBox controller, and see if anyone else can chip in.

Cheers

---

