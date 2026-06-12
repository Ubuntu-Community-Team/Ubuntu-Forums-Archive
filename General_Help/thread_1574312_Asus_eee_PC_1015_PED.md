---
title: "Asus eee PC 1015 PED"
date: 2010-09-14
forum: General Help
---

### Post by downcommer on 2010-09-14
Is the Asus eee PC 1015 PED compatible with Ubuntu? I am a raw beginner.

Thanks

---

### Post by cocokessler on 2010-10-01
I just got one. You will definitely encounter a few problems, though I think that solutions will be forthcoming soon.
I'm having trouble with the internal mic and with disabling the mousepad (I think that Ubuntu mistakenly believes that the mousepad is a normal mouse, thus it does not give a option to disable).

As I said, I have just gotten the computer, so I haven't had time to really investigate it yet.

---

### Post by Detroit Frog on 2010-10-01
Same problem here... the internal mic and disabling the tap-click on the trackpad. I tried about every solutions offered on the help forums with no success... So if you have any update, I'm definitely interested!

---

### Post by imaffett on 2010-10-05
The following disables the trackpad.  Pick up an external mouse to use, as the trackpad is really flaky.

I added the below entries to my .bash_aliases.  You may need to modify 134 to something differnt.  Run xinput list-props 'ImPS/2 Logitech Wheel Mouse'  and find what the id of "Device Enabled" is.  I'm working on mic and webcam now, but not promising much.  Haven't used linux much since 2002.

alias moff='xinput set-int-prop "ImPS/2 Logitech Wheel Mouse" 134 8 0'
alias mon='xinput set-int-prop "ImPS/2 Logitech Wheel Mouse" 134 8 1'

---

### Post by bamboodragonfly on 2010-10-08
Had the same problem with the internal microphone not working on my Asus 1015PED but I fixed it by installing the padevchooser package with the Package Manager and then using the volume control to unmute the audio (click on icon that looks like a speaker symbol) in the Input Devices tab. You may have to play around with the left and right volume control sliders a bit. I am using Ubuntu Netbook Edition 2.6.32-25-generic. Hope this post is helpful to someone.

---

### Post by Detroit Frog on 2010-10-10
Just upgraded to Ubuntu 10.10 and so far it solved all the bugs with the touchpad and the function buttons.

Not sure about the sound yet as some of the attempts I made at fixing the issue in the previous version might have carried over to the new one. I might have to make a clean install...

---

### Post by Detroit Frog on 2010-10-10
Sound problems are solved too!

I just hope we won't get too many new bugs but so far so good!:popcorn:

---

### Post by bamboodragonfly on 2010-10-12
how did you solve the touchpad issues? I am missing the "Touchpad" tab in the Mouse config app and looks like the OS is only detecting the touchpad as a PS/2 mouse.

---

### Post by JohnElway on 2010-10-12
The only issues I had with my 1015 that bothered me was not being able to turn off the trackpad and not getting any sound from the headphone jack (also note that most of the function keys don't work in 10.04, although you can create custom hotkeys to replace some of this lost functionality so this wasn't a big deal for me).

To turn the trackpad on and off I basically did the same thing as imaffett. I added the following two commands to my .bash_aliases file:

-to turn the trackpad off:```
xinput set-int-prop "ImPS/2 Logitech Wheel Mouse" "Device Enabled" 8 0
```

-to turn the trackpad on:```
xinput set-int-prop "ImPS/2 Logitech Wheel Mouse" "Device Enabled" 8 1
```

To get the sound working in my headphones I did the following:

-added this PPA to my software sources:
```
*ppa*:ubuntu-*audio*-*dev*/*ppa*
```

-reloaded the package info, searched for "linux-alsa-driver-modules" in synaptic and installed this package:
```
linux-alsa-driver-modules-2.6.32-25-generic
```

NOTE: The package you need to download will depend on what kernel version you're using. Use the "uname -r" command if you're unsure.

---

### Post by Detroit Frog on 2010-10-13
Well back when I was on Lucid Lynx I had tried a few of the solutions offered on the forums, to no avail.

- Function keys did not work except for the back light.

- Installed a few touch pad manager (synaptics, etc), they either did not work or failed to launch or only recognize my touch pad as
a mouse. It was out of control and would select, click, drag and drop anything my pointer was hovering on. Drove me insane.

- Trying to solve my microphone issue, I installed Pulse and ended up with no sound at all.

So I decided I would wait until 10.10 to see if it would solve any of these issue. I upgraded on Sunday and noticed the Mouse options in System has now a touchpad tab where I was able to:
- disable touchpad when typing
- NOT enable click through touchpad
- enable 2 finger scrolling.

I still had no sound but a few quick tweaks between Multimedia System Selector and Pulse did the trick: speakers, mike and headphones work.

And of course the function keys now work fine. So overall I'm pretty happy with Maverick Meerkat despite the minor sleep mode bug.:guitar:

---

### Post by bamboodragonfly on 2010-10-13
Thanks. I just upgraded from 10.04 to 10.10 and indeed the touchpad tab showed up in the Mouse config app. However, my left click seems to be screwed up as I can only single click and there is no double-click even when I use the touchpad buttons. I think all of the tweaking i have done so far is causing some conflicts. i plan to do a complete new install of 10.10 and hopefully everything will be as peachy as yours.

BTW, i am not sure i like the new Unity UI though but that's for another thread.

---

### Post by ThatBum on 2010-10-13
I had Lucid on my 1015. I got the touchpad, function keys, and microphone/headphone jack to work with a custom built kernel module, a GRUB boot parameter, and a backports ALSA module, respectively. Now I upgraded to Maverick, and my word, everything works! There is native support for everything but the Broadcom wireless, which needs the proprietary driver wl from the LiveCD.

---

### Post by Detroit Frog on 2010-10-13
Actually, after a quick check I noticed mine was an Asus Eee PC 1015 PEB and not PED.

The main differences seem to be about the size of the HD, the proc (Atom 450 Vs 455) and the DDR2 vs DDR3 memory.

Sorry if my experience was not relevant to this thread :-#

---

### Post by ThatBum on 2010-10-14
> **Detroit Frog said:**
> Asus Eee PC 1015 PEB and not PED.

I don't really think it matters. Sounds like the hardware is similar enough that it would apply. I mean, stuff for the 1005 is shared wth the 1015.

---

### Post by linein on 2010-10-16
hi guys, i've just got 1015ped and tryin to make it work on 10.10 nbr.everything is ok,but wifi is not able to find any networks..that's really not good.driver is installed ok, i've also reinstalled it in terminal typing apt-get install bcmwl-kernel source, but problem is still with me.how did u get it working?tnx for your answers and sorry 4 my english in b4.

---

### Post by Akaedintov on 2010-10-16
well , i have asus eee pc 1215N , but nvidia is forcing me to smash my computer!

---

### Post by Sereph on 2010-11-22
I have this netbook running ubuntu 10.04 regular not netbook remix and the linux-alsa-driver-modules-2.6.32-25-generic worked for me, but I am still having the issue with the touchpad and do not wish to go to 10.10 and also does anyone have any suggestions for the suspend bug? this is my school computer and if it cannot suspend it isn't terribly useful to me :(

---

### Post by roman_sharp on 2011-01-16
Bought this netbook recently. Tried to start LiveUSB Netbook release, but failed: touchpad didn't work, some application reported errors.

It seems that 1015 PED for now works better with Ubuntu 10.10 standard, than with 10.10 Netbok remix.

---

