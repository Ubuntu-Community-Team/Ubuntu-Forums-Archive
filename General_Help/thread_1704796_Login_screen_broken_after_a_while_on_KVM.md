---
title: "Login screen broken after a while on KVM"
date: 2011-03-11
forum: General Help
---

### Post by StephaneLenclud on 2011-03-11
I'm running a desktop installation of Ubuntu 10.04 LTS and using a KVM. After some time when I switch back to my Ubuntu machine the screen is just black. Keyboard and Mouse inputs are working but the screen stays black until I switch to another terminal and back to the graphical login screen doing ctrl+alt+F1 then ctrl+alt+F8. At this point all I see on the login screen is the background so I still cannot login from there. All I can do then is go back to a command line terminal which is then eventually displaying, login there and kill Xorg which restarts and thus fixes the broken login screen.

Although I enabled ctrl+alt+backspace and it works fine when a user is logged in it does not work from the login screen so I must use the command line to login and kill Xorg.

As anyone been there before. Is there a way to fix it or at least to get ctrl+alt+backspace to work from the login screen. It looks like Xorg is to blame.

---

### Post by fabricator4 on 2011-03-11
> **StephaneLenclud said:**
> 

As anyone been there before. Is there a way to fix it or at least to get ctrl+alt+backspace to work from the login screen. It looks like Xorg is to blame.

I'm running through a KVM switch, and the usual problem with my system is that no Hi-res modes are available until you make xorg.conf and put a few lines in there to tell X what the capabilities of the monitor are.  I got quite familiar with lo-res failsafe mode in X before I figured it out.

Am I to understand that you did not have to do this?  The monitor parameters must be getting passed to Xorg  when you boot allowing you to use a suitable resolution.  Perhaps when the monitor is switched away from X it gets confused and loses settings.

After much trial and error I found the simplest way of doing this was to put the vertrefresh and horizsync data for the monitor in xorg.conf, and let X worry about the modes it could infer from this.
Let me know if you want to try it: you'll need the the horizontal sync range and the vertical refresh range from the specs for your monitor.  If you don't have the monitor manual, you should be able to Google make/model for the specs.


Chris.

---

### Post by StephaneLenclud on 2011-03-11
I've had issues with the screen resolution when I first installed the OS. I don't recall exactly how I solved it though. Probably from the UI settings or by touching some conf files or both. Basically at the moment I run at the maximum resolution 1600x1200 but only once logged in. The log screen itself is displaying a lower resolution.

The monitor is a Dell 4:3 21" 1600x1200 from the previous generation of Dell monitors. Actually I also use a Windows machine directly through DVI while the problematic Ubuntu machine uses the VGA through the KVM switch. My KVM kinda screw the video signal that's why I'm doing it like that. Changing back and forth between the two machines works just fine usually but not after a prolonged time without using Ubuntu. I did try to disable all power saving feature on the Ubuntu machine too.


Pass on your solution to feed the screen settings to Xorg at boot time, I'll try it out.

---

### Post by fabricator4 on 2011-03-11
> **StephaneLenclud said:**
> Pass on your solution to feed the screen settings to Xorg at boot time, I'll try it out.


My monitor is a Samsung 1100p 21", so somewhat similar.  The following is my etc/X11/xorg.conf so you'll have to adjust accordingly but the main things are the Horizsync and Vertrefresh parameters.  When I was fighting with this originally I tried modeset and other things but they never worked for me. Once I came across this my problems were solved.  The use of xorg.conf seems to be almost redundant now, you probably won't already have one.  I was concerned when I found this on a new Lucid install, but I made the xorg.conf anyway and it just worked fine.

```

Section "Monitor"
	Identifier	"Samsung 1100p"
	Horizsync       30-110
	Vertrefresh     50-160
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Samsung 1100p"
	Device		"Configured Video Device"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
EndSection


```

After you reboot (or restart X) you'll probably have to go into monitor and select the resolution you want, after which the system will stay at that resolution regardless.

On my windows machine I had to plug the monitor directly into the vga card and set up the screen, after which it works quite happily through the KVM switch.

If they remove the use of xorg.conf completely from Natty I'm pooched.  Maybe I should try Maverick and Natty, I have them both here.

Chris.

---

### Post by farrinux on 2011-03-12
Chris:

I too have the same problem on an 10.04 LTS machine.  Would you need to add a section for the different resolutions for the monitor to the xorg.conf file?

Kevin

---

### Post by fabricator4 on 2011-03-12
> **farrinux said:**
> Chris:

I too have the same problem on an 10.04 LTS machine.  Would you need to add a section for the different resolutions for the monitor to the xorg.conf file?

Kevin

No, that's my entire xorg.conf file.  The system infers from the sync parameters what the possible resolutions are, you just have to pick the right one.

I'm running 1600x1200 which is the "ideal" resolution for the 1100p, though I can run 2048x1536 if I wanted to.  

The few attempts I had at specifying modes was not successful, usually resulting in the system dropping back to safe video mode or even console only. I've been running with this xorg.conf for almost two years now - since 9.04.  None of the normal recommended fixes with modes worked, until I stumbled on this one.

Chris.

---

### Post by StephaneLenclud on 2011-03-13
I tried your stuff without luck. It still breaks after a while sitting on the login screen. It's really an issue with the login screen cause I never get such problem when a user is logged in.

---

### Post by fabricator4 on 2011-03-14
> **StephaneLenclud said:**
> I tried your stuff without luck. It still breaks after a while sitting on the login screen. It's really an issue with the login screen cause I never get such problem when a user is logged in.

OK, it looks like adding a mode line to the screen section can affect the resolutions in the login screen. Have a look at [this post]("http://ubuntuforums.org/showthread.php?t=151192") and see if it helps you.

Chris

---

