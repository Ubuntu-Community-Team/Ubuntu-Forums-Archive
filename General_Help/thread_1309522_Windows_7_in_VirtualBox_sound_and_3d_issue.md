---
title: "Windows 7 in VirtualBox sound and 3d issue"
date: 2009-11-01
forum: General Help
---

### Post by JugglinPhil on 2009-11-01
Just installed Windows 7 in VirtualBox in order to be able to play a few windows only games, however as soon as I start them I get error messages that no 3D Hardware and no Sound Device was found. Is it possible that Virtualbox intercepts the guest OS's access to hardware and if so how can I change it?

---

### Post by Slim Odds on 2009-11-01
> **JugglinPhil said:**
> Is it possible that Virtualbox intercepts the guest OS's access to hardware and if so how can I change it?

LOL ....  that's **exactly** how virtual machines work.

---

### Post by JugglinPhil on 2009-11-01
> **Slim Odds said:**
> LOL ....  that's **exactly** how virtual machines work.
Okay thanks for that info, learned something new again, but do you also know how to fix it?

---

### Post by Slim Odds on 2009-11-01
> **JugglinPhil said:**
> Okay thanks for that info, learned something new again, but do you also know how to fix it?

Do you have the box checked to allow 3D acceleration? (under Display)

---

### Post by JugglinPhil on 2009-11-01
> **Slim Odds said:**
> Do you have the box checked to allow 3D acceleration? (under Display)
Alright thanks it wasn't enabled. Now the other one, the missing audio thingy still prevents the games from loading.

---

### Post by Slim Odds on 2009-11-01
> **JugglinPhil said:**
> Alright thanks it wasn't enabled. Now the other one, the missing audio thingy still prevents the games from loading.

OK, is the box checked for "Enable Audio"?

And if so, what type of device?

---

### Post by JugglinPhil on 2009-11-02
> **Slim Odds said:**
> OK, is the box checked for "Enable Audio"?

And if so, what type of device?
It is enabled, 'Host Audio Driver' is set to 'PulseAudio' (the other choices would be 'ALSA Audio Driver' 'OSS Audio Driver' and 'Null Audio Driver');
and 'Audio Controller' is set to 'ICH AC97' (here the other choice is 'Soundblaster 16').
Any idea which ones I should choose?
Thanks

---

### Post by Slim Odds on 2009-11-02
> **JugglinPhil said:**
> It is enabled, 'Host Audio Driver' is set to 'PulseAudio' (the other choices would be 'ALSA Audio Driver' 'OSS Audio Driver' and 'Null Audio Driver');
and 'Audio Controller' is set to 'ICH AC97' (here the other choice is 'Soundblaster 16').
Any idea which ones I should choose?
Thanks

Those are the settings that I use for XP, and it works fine for me. I'm not sure what the best settings for 7 would be.

Anyone using this setup for Windows 7?

---

### Post by JugglinPhil on 2009-11-02
> **Slim Odds said:**
> Those are the settings that I use for XP, and it works fine for me. I'm not sure what the best settings for 7 would be.

Anyone using this setup for Windows 7?
You mean the ones I've got? I'll try and play around with it a bit.

---

### Post by 6205 on 2009-11-02
> **JugglinPhil said:**
> Just installed Windows 7 in VirtualBox...

You cannot virtualize better OS in worse OS. That is bad karma :)

---

### Post by JugglinPhil on 2009-11-02
> **6205 said:**
> You cannot virtualize better OS in worse OS. That is bad karma :)
In my eyes 7 is in no way better than Ubuntu, but as always you could argue about that sort of stuff. ^^

---

### Post by Slim Odds on 2009-11-02
> **6205 said:**
> You cannot virtualize better OS in worse OS. That is bad karma :)

Bad karma is calling windows better in a linux forum. ;)

---

### Post by dj-toonz on 2009-11-02
For 3D under a windows host in VirtualBox, you have to do a workaround

Direct 3D support in Windows guests. For this to work, the Guest Additions
must be installed in Windows “safe mode”. Press F8 when the Windows guest
is booting and select “Safe mode”, then install the Guest Additions. Otherwise
Windows’ file protection mechanism will interfere with the replacement DLLs
installed by VirtualBox and keep restoring the original Windows system DLLs

And for the sound in Win 7, Haven't a clue about that as I've never tried win 7 under a vm only XP & sound works great in that

---

### Post by JugglinPhil on 2009-11-03
> **dj-toonz said:**
> For 3D under a windows host in VirtualBox, you have to do a workaround

Direct 3D support in Windows guests. For this to work, the Guest Additions
must be installed in Windows “safe mode”. Press F8 when the Windows guest
is booting and select “Safe mode”, then install the Guest Additions. Otherwise
Windows’ file protection mechanism will interfere with the replacement DLLs
installed by VirtualBox and keep restoring the original Windows system DLLs

And for the sound in Win 7, Haven't a clue about that as I've never tried win 7 under a vm only XP & sound works great in that
Thanks I'll give it a shot and report back. :)

---

### Post by JugglinPhil on 2009-11-04
Alright the sound... I've tried all the possible combinations of 'host audio driver' and 'audio controller' with no success, until I found that you have to intall the sound drivers from inside windows from the realtek website ([http://forums.virtualbox.org/viewtopic.php?f=8&t=23224](http://forums.virtualbox.org/viewtopic.php?f=8&t=23224)). I don't know yet if this works, but since nobody has a better idea I'll try it anyway.

---

### Post by JugglinPhil on 2009-11-04
> **dj-toonz said:**
> For 3D under a windows host in VirtualBox, you have to do a workaround

Direct 3D support in Windows guests. For this to work, the Guest Additions
must be installed in Windows “safe mode”. Press F8 when the Windows guest
is booting and select “Safe mode”, then install the Guest Additions. Otherwise
Windows’ file protection mechanism will interfere with the replacement DLLs
installed by VirtualBox and keep restoring the original Windows system DLLs

And for the sound in Win 7, Haven't a clue about that as I've never tried win 7 under a vm only XP & sound works great in that
Sound is working now, next I'll try this suggestion for the 3D.

---

### Post by JugglinPhil on 2009-11-04
Okay crap, something's gone badly wrong.. Now it doesn't let me execute the installers of any of my cds, it says they are broken.. all of them! Stupid ms..
*sigh*

---

### Post by JugglinPhil on 2009-11-06
Alright I reinstalled 7, and got the sound working with the Realtek drivers, can anybody help me now with the 3D issue? I tried dj-toonz suggestion but it didn't work either..
Thanks

---

### Post by wildweathel on 2009-11-06
You need two things for 3D acceleration in a virtualbox guest: 

- Working 3D acceleration in the host 
- Sun's graphics driver.

You should also be using *Sun's* driver for audio, not Realtek's.  The virtual sound card is a part of Virtualbox, written by Sun, so the Sun driver is the one you want.  The fact that the Realtek driver works is a testament to the fact that Sun's virtual device is very similar to the real hardware.

Unlike the soundcard, the virtual GPU works completely differently from any real ones.  You have to use the Sun drivers.   Also, the abilities of the guest cannot exceed the abilities of the host.

So, first test OpenGL on Ubuntu by running something decently complex.   The Phoronix test suite has some great stuff.  You can install the installer with Synaptic or aptitude.  Then read  how to use it: [http://www.phoronix-test-suite.com/?k=usage](http://www.phoronix-test-suite.com/?k=usage)  

Exactly what you should try running depends on what games you're trying to get working on Windows.  However, Ubuntu must be able to run something of equivalent complexity for it to work inside Virtualbox.  (And even that's no guarantee.) opengl-demos looks like a good place to start, though.

Sun's device drivers for the guest OS are called "Guest Additions." Make sure you use them for both sound and graphics.  [http://blogs.chron.com/techblog/archives/2009/06/set_up_windows_7_in_virtualbox_a_tutorial.html](http://blogs.chron.com/techblog/archives/2009/06/set_up_windows_7_in_virtualbox_a_tutorial.html) .

Good luck.

---

### Post by JugglinPhil on 2009-11-06
Thanks for the reply, but I got a bit lost. Do you mean Sun that also does Open Office? When I was googling for it it came up with a site that charged my like 3$ per download, I take it that was the wrong one? Anyway, could you maybe give me a link or something to were I can get the right drivers?

---

### Post by jocko on 2009-11-06
> **JugglinPhil said:**
> Thanks for the reply, but I got a bit lost. Do you mean Sun that also does Open Office?
Yep. Sun microsystems makes java, open office, virtualbox, their own os and probably a lot more. I don't think they make any driver for the virtual sound card (it was made to be detected by the guest os like if it was a physical realtek ac97 compatible sound chip, so the driver from realtek is the correct one). If you can find any such thing on sun's website they have probably just repackaged realtek's driver with some custom info...

---

### Post by JugglinPhil on 2009-11-06
> **wildweathel said:**
> You need two things for 3D acceleration in a virtualbox guest: 

- Working 3D acceleration in the host 
- Sun's graphics driver.

You should also be using *Sun's* driver for audio, not Realtek's.  The virtual sound card is a part of Virtualbox, written by Sun, so the Sun driver is the one you want.  The fact that the Realtek driver works is a testament to the fact that Sun's virtual device is very similar to the real hardware.

Unlike the soundcard, the virtual GPU works completely differently from any real ones.  You have to use the Sun drivers.   Also, the abilities of the guest cannot exceed the abilities of the host.

So, first test OpenGL on Ubuntu by running something decently complex.   The Phoronix test suite has some great stuff.  You can install the installer with Synaptic or aptitude.  Then read  how to use it: [http://www.phoronix-test-suite.com/?k=usage](http://www.phoronix-test-suite.com/?k=usage)  

Exactly what you should try running depends on what games you're trying to get working on Windows.  However, Ubuntu must be able to run something of equivalent complexity for it to work inside Virtualbox.  (And even that's no guarantee.) opengl-demos looks like a good place to start, though.

Sun's device drivers for the guest OS are called "Guest Additions." Make sure you use them for both sound and graphics.  [http://blogs.chron.com/techblog/archives/2009/06/set_up_windows_7_in_virtualbox_a_tutorial.html](http://blogs.chron.com/techblog/archives/2009/06/set_up_windows_7_in_virtualbox_a_tutorial.html) .

Good luck.
Alright I installed the Guest Additions from the tutorial you recommended which is pretty cool, now the mouse isn't captured in windows anymore and I can go fullscreen. :) 
Still can't find the right graphics drivers though.. :(
If anybody could provide me with the appropriate links I'd be more than thankful.

---

### Post by JugglinPhil on 2009-11-06
If it's of any use the games I'm trying to install are:
Star Wars Jedi Academy
Star Wars Republic Commando
Tomb Raider: Underworld
Assassin's Creed
Mass Effect
So they are all more or less new, but my hardware should be enough because they worked fine back in vista (no virtualbox though).

---

### Post by jocko on 2009-11-07
> **JugglinPhil said:**
> If it's of any use the games I'm trying to install are:
Star Wars Jedi Academy
Star Wars Republic Commando
Tomb Raider: Underworld
Assassin's Creed
Mass Effect
So they are all more or less new, but my hardware should be enough because they worked fine back in vista (no virtualbox though).
Just because they worked on your computer with vista does not mean they will ever work in virtualbox. The virtual graphics card is never going to be as good as your real graphics card.

The graphics driver for the virtual graphics card comes with the guest additions. If you can go fullscreen and your mouse pointer is released from the guest when you move it to the edge of the screen you have the correct graphics driver installed.
If you have activated 3d acceleration support in the virtual machine and given the virtual graphics card enough memory you have done all you can do.
Try to run some simple 3d graphics in windows to see if it works.
In XP you could run some directX tests by running the command "dxdiag", not sure if that's still included in vista or 7.

If the games don't work, it's because the virtual graphics card is not good enough.

---

### Post by JugglinPhil on 2009-11-07
> **jocko said:**
> Just because they worked on your computer with vista does not mean they will ever work in virtualbox. The virtual graphics card is never going to be as good as your real graphics card.

The graphics driver for the virtual graphics card comes with the guest additions. If you can go fullscreen and your mouse pointer is released from the guest when you move it to the edge of the screen you have the correct graphics driver installed.
If you have activated 3d acceleration support in the virtual machine and given the virtual graphics card enough memory you have done all you can do.
Try to run some simple 3d graphics in windows to see if it works.
In XP you could run some directX tests by running the command "dxdiag", not sure if that's still included in vista or 7.

If the games don't work, it's because the virtual graphics card is not good enough.
Okay that's a shame, never knew that.. Do you know why it is that you can't use hardware to it's full extent in a vb? I mean that's quite a big disadvantage isn't it?
Edit: Is there no way to make the virtual graphics card better? I'm getting sort of desperate about this one..

---

### Post by jocko on 2009-11-07
> **JugglinPhil said:**
> Okay that's a shame, never knew that.. Do you know why it is that you can't use hardware to it's full extent in a vb? I mean that's quite a big disadvantage isn't it?
Edit: Is there no way to make the virtual graphics card better? I'm getting sort of desperate about this one..
To use the hardware to it's full extent, the operating system needs to be running directly on the actual hardware.
With a virtual machine you have the host os running on the actual hardware and the virtual machine running in the host os. The os in the virtual machine have no way of communicating directly to the real hardware. It's fully dependent on which resources the host os can give to the virtual machine, and which of those resources the virtual machine can give to the guest os...
I guess the reason it is like this is a limitation of both the hardware and the operating systems. You simply can't run two different operating systems at the same time on the same hardware, which is why virtual machines were invented.
Someone will have to invent a good, fast and safe way of suspending one os, and simultaneously waking up another suspended os, or inventing a whole new computer architecture that allows running more than one os in parallel.
The closest thing I can think of that is actually possible now would be to have two pc's connected to a KVM switch so you can use the same keyboard, monitor and mouse to control both.

---

### Post by JugglinPhil on 2009-11-07
Okay thanks anyway, I'll just have to give up then.. :(

---

