---
title: "Live CD help"
date: 2006-02-27
forum: General Help
---

### Post by leviathan660 on 2006-02-27
I want to try out Linux, so I downloaded the Ubuntu Live CD. It loads up to just fine, however, after everything is booted, it goes to a brown screen, I hear a start-up noise, I can see my mouse, but that is it. Nothing happens. After getting the official CD's, I tried out those. The same thing happened. Just a brown screen, and nothing happening. I tried out the PC and 64-bit version, but the same thing happens. I've let it sit for a couple of minutes, but it's just the brown screen. I don't get to see the fabled login screen.

My current Setup is:
DFI Lanparty UT-D Ultra, 3200+ AMD 64 venice, 7800gt, and 2 gigs of OCZ valueram.
This stuff is fairly recent, so I suspect it is not a hardware problem. Do you guys know what is going on? Am I just not waiting long enough for a login screen?

---

### Post by unperson on 2006-02-27
I'm not certain exactly what it going on.  I doubt this is normal (i.e. proper) behavior if you really see no changes for minutes on end.  Here are two questions, the answer to which may help others give more insight on what may be going on:

[LIST=1]
[*]Is your system still reading from the CD that whole time?  Is the CD read light still flickering after several minutes?  When running the live CD, the speed of the CD drive is often/usually the limiting factor on speed.  There are sometimes points where it reads for quite a while without doing much.  How fast is your CD drive?
[*]Is the system unresponsive at that point?  Does the mouse still move?  One way to see If it is still responsive is by pressing CTRL+ALT+F1 or CTRL+ALT+F2 (one or both may work) you should get another "virtual terminal" (a command line or login screen).  Can you do this?  (you can then press CTRL+ALT+F7 to get back to your "desktop")
[/LIST]

---

### Post by leviathan660 on 2006-02-27
Right, so I attempted it again. Everything goes fine (except the clock synchronization), then I get the Brown screen of death. Yes, the mouse does respond to movement, and I do believe the keyboard responds as well because I can turn off and on the numlock.  I tried pressing the keys that you told me about, however,  nothing happens. All I get is my brown screen.

The CD tray does eventually stop flickering, but I gave it an extra 20 mins to settle, but to no avail. I then tried to press the CD eject button, but it wouldn't respond. (I assume this is because I am booting off the CD.) I then figured since my computer is slightly overclocked, it might be unstable, so I brought it back to its default settings, but I still got the Brown Background with a mouse.

Thanks for your efforts too.

---

### Post by leviathan660 on 2006-02-27
Update
I just tried out Kubuntu, but instead of a brown screen, I just got a teal screen. Still no response when I press ctrl + alt + F2, or ctrl + alt + F1. I may have to try out suse, but I dont have a DVD burner.

Am I forsaken? If I install Ubuntu instead of running it off the CD, will it run?

---

### Post by newuser111 on 2006-02-27
try acpi=off at boot

---

### Post by leviathan660 on 2006-02-28
How does one go about doing that?

---

### Post by RAOF on 2006-02-28
The reason you're not seeing anything is because your graphics card is too new for the (open source nv) drivers the live cd is using.  If you can press Ctrl-Alt-F1 (you'll probably need to use the left CTRL & ALT) to get to a console prompt, do so.  Run "sudo dpkg-reconfigure xserver-xorg".  You can accept the defaults, unless you know better.  Then, when it offers you a list of graphics drivers (it will have defaulted to "nv") select the "vesa" drivers - they're a failsafe driver which should work.

When that's done, run "sudo /etc/init.d/gdm restart" to load the GUI with the VESA drivers.  Yes, you will have to do this each boot.

---

### Post by leviathan660 on 2006-02-28
Unfortunatly, I have pressed the left ctrl and alt +F1, but no console came up.

---

### Post by RAOF on 2006-02-28
Whoops.  Should have read more carefully, sorry.  

Well, you can still do a similar thing:  boot the livecd with "live expert" rather than just pressing "enter", and select the vesa driver when asked.  This will ask a **lot** of questions.

Oh, and you'll want to boot to runlevel 5, if it asks :)

---

### Post by leviathan660 on 2006-02-28
Alright, thanks, I'll give it a shot when I get home. So I have to type in:

boot: live expert

then Select the Vesa Driver, and boot to runlevel 5 if asked. Alright. Thanks.

---

### Post by LordBug on 2006-02-28
HOWTO:  Fix this.

I had the same issue.  Took me a few hours of tinkering and talking on IRC to finally solve it.  The solution is surprisingly easy, it just took forever to find the cause.

Boot the LiveCD normally.  NO OPTIONS.  When X starts coming up, before the brown screen appears, hit CTRL-ALT-F2.  You now have 2 options, depending on RAM space (everything is running from the LiveCD and a RAM drive):

1) {preferred} Run 'apt-get install nvidia-glx'.  This will install the real nVidia drivers into the RAM drive.  Run 'nano /etc/X11/xorg.conf' and change the video driver from 'nv' to 'nvidia'.  Save and exit.  Run '/etc/init.d/gdm restart'.  Enjoy Gnome.

2) Run 'nano /etc/X11/xorg.conf' and change the video driver from 'nv' to 'vesa'.  Run '/etc/init.d/gdm restart'.  Enjoy Gnome, although maybe slower than option #1.

---

### Post by unperson on 2006-02-28
I can't seem to find a decent listing of the boot options for the Ubuntu LiveCD, but on knoppix you can [apparently](http://www.knoppix.net/wiki/Cheat_Codes) specify the video driver at boot with the option xmodule=vesa.  So you migtht try that, although I don't know if the Ubuntu live cd takes the same options.  It seems like easy is best if this is something you'll have to do each time you boot.  On an installed version this would be fairly easy to fix perminantly in a way similar to the way LordBug suggests.

---

### Post by leviathan660 on 2006-02-28
Alright, thanks Buglord, I'll give that a shot before I try out what was suggested by unperson and roaf.  I guess I'll have to print off that post so I know what to type in. I'll let you guys know how this goes when I get on my computer at home.

---

### Post by leviathan660 on 2006-02-28
Alright, So I mashed the Keys and was able to get into the console before the start up.  I entered in the apt-get bit, but I got this error:
E: Could not open lock file /var/lib/apt/lists/lock -open (13 Permission denied). I tried out the nano part and whatnot, but appearenltly it cannot be found. I then Pressed CTRL ALT F7, and to my suprise, I saw some of the desktop. Not all, some of the features were missing. But after that, I could not get back into the console. Any suggestions?

---

### Post by unperson on 2006-03-01
When one application is using the apt system to install or configure packages it generally locks some of the important files so that no other application can use them.  My guess is one such program must run during the start-up of the Live CD, blocking you from using apt-get.

Another piece of bad news is I plugged in my Ubuntu Hoary Live CD (don't have Breezy live at the moment) and tried the xmodule=vesa option with no luck.  Unless they've added it to the Breezy CD it may be a dead-end on that front.  I still can't find any page documenting all the Ubuntu live cd boot options.

I'm no expert on these things, so perhaps someone else has a better suggestion, but I see two options:

[LIST=1]
[*]Boot to runlevel 3 (text command line, no GUI) by typing "live 3" at the boot prompt.  When it's done starting up, you should be dropped at the command prompt.  You could then try LordBug's suggestion again.  I've not tried this, so I'm not sure it will work, but I *think* it should.  Also, I assume you don't need to use sudo to do those things on the live cd, but you might experiment with prefacing the commands with sudo.
[*]the other suggestion would be (if possible) burn a Knoppix CD (another Linux live CD) and see if you can get that working, either with the default  settings or with the xmodule=vesa.  The main advantage to the Knoppix CD is that its functions seem to be [documented a bit better](http://www.knoppix.net/wiki/Cheat_Codes).
[/LIST]

Good luck.

---

### Post by LordBug on 2006-03-01
> Could not open lock file /var/lib/apt/lists/lock -open (13 Permission denied)

I made a mistake.  I was thinking the LiveCD would leave you with a root shell.  It didn't.  Tack 'sudo ' in front of all the commands I gave you.  Should take care of it.

---

### Post by leviathan660 on 2006-03-02
It's a no go. After using Sudo, it did work, but it had problems, saying I should update. when I typed Sudo apt-get update, it could not connect to the net.  I tried switching my ethernet cord to my other ethernet port, but it still couldn't connect. I'm thinking that if my Video card is too new, my Motherboard may be as well. It also cannot connect to the site to synchronize the clock.

---

### Post by steve.horsley on 2006-03-02
[QUOTE=leviathan660]It's a no go. After using Sudo, it did work, but it had problems, saying I should update. when I typed Sudo apt-get update, it could not connect to the net.  I tried switching my ethernet cord to my other ethernet port, but it still couldn't connect. I'm thinking that if my Video card is too new, my Motherboard may be as well. It also cannot connect to the site to synchronize the clock.[/QUOTE]
 
Well, let's give up in the nvidia driver download for now. It's still worth changing the driver from "nv" to "vesa".  Use alt-ctl-f2 to get a console then these 2 comands:
    sudo nano /etc/X11/xorg.conf (edit and save the file)
    sudo /etc/init.d/gdm restart

See how that goes.

---

### Post by leviathan660 on 2006-03-02
Alright, I'm responding to you guys from Ubuntu right now. It took a long time, but I'm finally on, and I was able to get my internet running. I'll have to give this thing a shot later as soon as I understand what is going on. But thanks go out to the all of you.

---

