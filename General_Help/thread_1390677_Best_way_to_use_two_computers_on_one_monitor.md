---
title: "Best way to use two computers on one monitor"
date: 2010-01-25
forum: General Help
---

### Post by spiritech on 2010-01-25
i have recently built my first computer with the following spec.

M3A78-CM MB
2.8Ghz AM2 dualcore CPU
2x 2gb DDR2 800Mhz RAM
ATI HD4650 GPU 
400Gb HD

i would like to use this mainly for web surfing, downloading, organizing files-video-music etc and programming.

i also have in the process of being built another computer with the following spec.

M4A79T deluxe MB
3.0Ghz AM3 quad-core Phenom II CPU
2x 2gb DDR3 1600Mhz RAM
ATI VapourX HD4890 GPU
1000Gb hd

i am building this for the sole purpose for using "Blender". Both computers will have Ubuntu Karmic installed . is there a way of using both these computers on the one screen without having to change HDMI channels? thankQ in advance.....

---

### Post by tgalati4 on 2010-01-25
Log into one then ssh into the other with X forwarding then you can run graphical apps from one machine on the other:

ssh -2 -Y user@2nd_machine
gcalctool

Or buy an hdmi switcher.

---

### Post by spiritech on 2010-01-25
> **tgalati4 said:**
> Log into one then ssh into the other with X forwarding then you can run graphical apps from one machine on the other:

ssh -2 -Y user@2nd_machine
gcalctool

Or buy an hdmi switcher.

er ok.

if im using first machine as the main ie. the mouse and keyboard connected to it will it still control the second machine (on my post), if so will it not slow it down. can i connect the second machine to the first machine through video in?.......maybe

thanks for replies...:)

---

### Post by steveneddy on 2010-01-25
Use a KVM switch

[http://en.wikipedia.org/wiki/KVM_switch](http://en.wikipedia.org/wiki/KVM_switch)

buy here

[http://www.kvmgalore.com/shopping/index.php](http://www.kvmgalore.com/shopping/index.php)

cheers

:popcorn:

---

### Post by t4thfavor on 2010-01-25
KVM switch is by far the best idea, but the X over SSH idea is nice. He's going to run blender, which means X would require huge network bandwidth, so that's why I don't like that idea.

---

### Post by NunyaB on 2010-01-25
I use a KVM switch.  Just remember to logon fully before switching to the other machine to logon.  Ubuntu gets very unhappy with display if you power up without the monitor connected.  ;-)

---

### Post by t4thfavor on 2010-01-26
My KVM was cheap, and it never lets the other PC think there is nothing attached. I have an IOGear 2 port. Each machine will even post as if it has a KB/mouse attached also.

---

### Post by spiritech on 2010-01-26
> **tgalati4 said:**
> Log into one then ssh into the other with X forwarding then you can run graphical apps from one machine on the other:

ssh -2 -Y user@2nd_machine
gcalctool

Or buy an hdmi switcher.


if i do use the shh option how do i connect the two computers. i suppose shh acts a bit like remote user??

could i use a firewire cable to connect & access the second computer then send the signal back through DVI and simply display this in a viewer. that way blender should run at full speed.

---

### Post by t4thfavor on 2010-01-26
Install openssh-server then:
You open your /etc/ssh/ssh_config and uncomment the stuff about forwarding X11
Then when you SSH into the other box you can issue commands like "nautilus ./" and instead of nautilus showint up on the remote machine it will show up on ths screen in front of you. 

same works if the remote machine is in another place or whatever. 

Just be warned, its a bandwidth hog, especially on Wireless.

---

### Post by spiritech on 2010-01-26
any comments about my last post. suppose the question here is can i remote access my second computer through a FIREWIRE cable or some other highspeed cable. then is it possible to send that signal back,through DVI, ifso what app do i use to display that signal.

the thing is with shh, i believe it uses the same wire to send and recieve info, therefor will be to slow?

---

### Post by t4thfavor on 2010-01-26
I belive the question is answered.

Firewire is a TCP stream just like ethernet, so you could ssh through that.

any connection to another pc that is not direct via a video card will be unbearably slow for 3d modeling with Blender this is just a law you cannot break.

a KVM would allow you to quickly change back and forth to each PC to do whatever work you need to do. As it stands you could A.) use ssh, and waste alot of time and network bandwidth on it, or B.) grab a cheap KVM, and use that.

Besides I believe HDMI as far as your video card is concerned is a one way protocol, and without expensive capture and decoding hardware your idea cannot work.

Oh, and I just googled for an hdmi kvm, and there isn't one. you should just pick up a usb A-B switch, and suffer with changing the channel on your monitor.

---

### Post by bab1 on 2010-01-26
> **spiritech said:**
> any comments about my last post. suppose the question here is can i remote access my second computer through a FIREWIRE cable or some other highspeed cable. then is it possible to send that signal back,through DVI, ifso what app do i use to display that signal.

the thing is with shh, i believe it uses the same wire to send and recieve info, therefor will be to slow?

You need to connect the 2 computers with Ethernet (a switch would be nice).  The protocol ssh runs over TCP/IP on Ethernet.

Edit:  Although Firewire is a possibility, TCP/IP over Ethernet is the most common for Linux.  I believe only MAC OSX will readily run TCP/IP on Firewire.

---

### Post by spiritech on 2010-01-26
> **t4thfavor said:**
> I belive the question is answered.

Firewire is a TCP stream just like ethernet, so you could ssh through that.

any connection to another pc that is not direct via a video card will be unbearably slow for 3d modeling with Blender this is just a law you cannot break.

a KVM would allow you to quickly change back and forth to each PC to do whatever work you need to do. As it stands you could A.) use ssh, and waste alot of time and network bandwidth on it, or B.) grab a cheap KVM, and use that.

Besides I believe HDMI as far as your video card is concerned is a one way protocol, and without expensive capture and decoding hardware your idea cannot work.

Oh, and I just googled for an hdmi kvm, and there isn't one. you should just pick up a usb A-B switch, and suffer with changing the channel on your monitor.

ok KVM seems like the best option. could always use DVI-HDMI adapter.

thanku all....:)

---

### Post by spiritech on 2010-01-26
> **t4thfavor said:**
> I belive the question is answered.

Firewire is a TCP stream just like ethernet, so you could ssh through that.

any connection to another pc that is not direct via a video card will be unbearably slow for 3d modeling with Blender this is just a law you cannot break.

a KVM would allow you to quickly change back and forth to each PC to do whatever work you need to do. As it stands you could A.) use ssh, and waste alot of time and network bandwidth on it, or B.) grab a cheap KVM, and use that.

Besides I believe HDMI as far as your video card is concerned is a one way protocol, and without expensive capture and decoding hardware your idea cannot work.

Oh, and I just googled for an hdmi kvm, and there isn't one. you should just pick up a usb A-B switch, and suffer with changing the channel on your monitor.

regarding HDMI KVM

[http://www.scan.co.uk/Products/Aten-CS1792-HDMI-KVM-Switch](http://www.scan.co.uk/Products/Aten-CS1792-HDMI-KVM-Switch)

---

### Post by t4thfavor on 2010-01-26
OK they do, I just didn't find one on NewEgg, and I thought they had everything.

It's also E100 which is alot here in the US for a KVM with so few ports, i guess you pay for the use of that sweet DRM'd technology.

---

