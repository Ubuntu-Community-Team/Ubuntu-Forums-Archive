---
title: "usb devices that wont work unless i reboot"
date: 2010-11-28
forum: General Help
---

### Post by witeds on 2010-11-28
ok i have been in Ubuntu for almost a year now and i have a problem i am trying to get worked around or fixed I have searched thousands of times and thousands of sites for the answer it dosen't seem to be really known or talked about yet 

i have xbox controllers and when i plug them in while the computer is on lsusb reads them but i canto use them on any thing but if i reboot they are recognised by the programs

this also goes for my ekey small usb midi keyboard 

is there a way to get thease devices to recognize while the computer is on couse i hate having to reboot just to play an emulator or somthing or to play with my midi keyboard in lmms

---

### Post by davec64 on 2010-11-28
Hi,
This is a bit of a long shot but I had a google for your problem and came up with this:

[http://www.webupd8.org/2010/05/fix-usb-devices-automount-not-working.html]("http://www.webupd8.org/2010/05/fix-usb-devices-automount-not-working.html")

It's got to be worth a try!

---

### Post by witeds on 2010-11-28
that worked nicely thank you 
all i had to do was 
sudo modprobe -r floppy

I didn't think it would be this because my computer is an e machine el1200
and dose not come with a floppy drive or even a hook up for one 

after i put that comand in terminal and reinserted my xbox controller it was
recognized without need to restart thank you

i tried the midi keyboard but it still dose not mount into midi devices when pluged in that is another one i need help with

---

### Post by davec64 on 2010-11-28
Nice one!

You might want to change your bios setting as well for the next time you restart.
I'm afraid i don't know what to suggest for the keyboard. I suspect you might need to load a a module using modprobe again but identifying it might be a problem.

best of luck!

---

### Post by davec64 on 2010-11-28
Just done a bit more reading!

try running the following without the keyboard installed:

```
lsmod
```
That will list loaded modules. Make a note of the installed modules.
Reboot with the keyboard installed and run the command again. If there's one more in the list that's probably the one the keyboard is using. You can then try and install it using modprobe to see if that works.

---

### Post by witeds on 2010-11-28
ok sounds good i will have to try that is there a way to see if the keyboard is pluged in and run the item if it works that will make it readable by devices it dose show up in lsusb but not in amidi -l where it should be listed aswell


lsmod without keyboard:

ff_memless              4393  1 xpad
snd_seq_dummy           1350  0 
parport_pc             26058  0 
ppdev                   5556  0 
binfmt_misc             6599  1 
snd_hda_codec_realtek   217971  1 
nvidia               9329739  46 


lsmod with keyboard:

ff_memless              4393  1 xpad
binfmt_misc             6599  1 
parport_pc             26058  0 
ppdev                   5556  0 
snd_hda_codec_realtek   217971  1 
snd_usb_audio          86480  0 
snd_usbmidi_lib        17413  1 snd_usb_audio
nvidia               9329739  38

---

### Post by davec64 on 2010-11-29
I suspect it won't show up in amidi -l until the module is loaded.
I think a good candidate looks like:
> snd_usbmidi_lib 17413 1 snd_usb_audio
So if you use modprobe to load the module:
```
modprobe snd_usbmidi_lib
```
Does that work?
You might have to play around with the name and you might have add some supporting modules as well. Looking at your lsmod output, I think it's probably best to add snd_usb_audio first as its reported first in the list.
Post back how you get on!

---

### Post by witeds on 2010-11-29
thanks alto those help 

since i don't have legacy floppy option in my bios settings i need a solution to get it to work but i can probably just disable it form the start up with a script 

The Xbox Controller:
```
 sudo modprobe -r floppy
 sudo modprobe xpad
```works also only if i use sudo modprobe xpad
is there a way to get this to run when ever it is plugged in because it dose show up in 
lsusb so the computer reads it

The Midi Keyboard: 
```
 sudo modprobe snd_usb_audio 
```that is all i needed to run and it read the keyboard again 
is there away to run this upon or shortly after the keyboard is plugged in automaticly

---

### Post by davec64 on 2010-11-29
I've found this:

[http://www.cyberciti.biz/faq/linux-how-to-load-a-kernel-module-automatically-at-boot-time/]("http://www.cyberciti.biz/faq/linux-how-to-load-a-kernel-module-automatically-at-boot-time/")

So my theory is, if you add the modules to /etc/modules (for Ubuntu) the modules will then be present when you plug the controller and the keyboard in.

Let me know how you get on!

Dave

---

### Post by davec64 on 2010-11-29
Just a note if my last suggestion works, when an update occurs and a new kernel is installed you'll have to add the modules to the file again. So it might be worth bookmarking this thread! :)

---

### Post by witeds on 2010-11-29
only problem i see with that suggestion is its for boots and not when the usb is plugged in 
oh and i only needed sudo modprobe xpad for the controller but now that i have the commands i just need a way to identify the usb when it is plugged in and run the modprobe commands

---

### Post by davec64 on 2010-11-30
If you load the module at boot, when you plug the controller/keyboard in it should be recognised as the module is present.
I had a similar problem with a firewire camcorder awhile back and that was the suggestion.
The alternative would be to write a bash script and have it on your desktop and run it when you plug it in.

---

### Post by witeds on 2010-11-30
your right thank you it worked thank you and for any one who comes across this article looking for somthing similar here is what worked for me in order

```
sudo gedit /etc/modules
```
then i added
xpad and snd_usb_audio
and it now looks like the following
```
# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

lp
xpad
snd_usb_audio
```

---

### Post by davec64 on 2010-12-04
Glad its all sorted, all the best!  :)

---

