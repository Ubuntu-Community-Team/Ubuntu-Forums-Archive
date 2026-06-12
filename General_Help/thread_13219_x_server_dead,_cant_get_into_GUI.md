---
title: "x server dead, cant get into GUI"
date: 2005-01-29
forum: General Help
---

### Post by Datchew on 2005-01-29
Been running fine for awhile. 

Then, attempted to change some things in [HERE](http://ubuntuforums.org/showthread.php?t=9671) 
and when i rebooted, after it scrolls through the dos-like screen loading everything and after it starts GNOME,  I get a blue screen and a message that says 

"cannot start x server (gui) likely not setup correctly etc
Would you like to view the x server to diagnose the problem?"

i picked yes, it gave me a bunch of install date, version, build number, etc, and at the end, it says "module loader present" and thats IT!  

I hit ok, and it says "I will disable this x server for now. 
Restart GDM when it is configured correctly."

Again, i hit OK and it takes me out to the dos prompt area for a login. 
I can login and browse, but cant get back into the gui.

Is there some package i can uninstall/reinstall?
Help. 

Thanks,
Datchew.

---

### Post by az on 2005-01-29
If you are having mouse problems, check to see that the psmouse module is loaded.

lsmod

If it is not, load it.

sudo modprobe psmouse.

If everything is honky-dory, add psmouse to the /etc/modules file.  You must sudo to do that.

sudo nano /etc/modules (CTRL-O to save, CTRL-X to leave)

dpkg-reconfigure xserver-xfree86 to reconfigure X.

Check the module thingy first.


Finally,
sudo killall gdm
sudo gdm


ctrl-atl-F1 to get back to a console if your mouse/keyboard is/are dead.

Good Luck.

---

### Post by Datchew on 2005-01-30
Dammit Jim... I'm a doctor not a linux guru!

Thanks much. 
I'll get to the other drive and try that right now.

---

### Post by Datchew on 2005-01-30
[QUOTE=azz]If you are having mouse problems, check to see that the psmouse module is loaded.

lsmod

[COLOR=YellowGreen]Couldn't get this to do anything[/COLOR]

If it is not, load it.

sudo modprobe psmouse.

[COLOR=YellowGreen]nothing happened here, but it looked like it took it.  returned me to prompt[/COLOR]

If everything is honky-dory, add psmouse to the /etc/modules file.  You must sudo to do that.

sudo nano /etc/modules (CTRL-O to save, CTRL-X to leave)

[COLOR=YellowGreen]was like editing the autoexec in windows... the psmouse was there, so i left it as it was. [/COLOR]

dpkg-reconfigure xserver-xfree86 to reconfigure X.

[COLOR=YellowGreen]had to sudo to get this one to work, opened up a GUI that walked me through setting up most of my hardware, keyboard, mouse, video card.  Everything looked fine.  took most of the defaults. then exited. [/COLOR]

Check the module thingy first.


Finally,
sudo killall gdm
sudo gdm

[COLOR=YellowGreen]this brought back the same blue GUI that said my x server is messed up etc. same as the first time.   
Did i miss something? Am I supposed to change something?
I also did the lspci command and it gave my video card as the following:
0000:01:00.0 VGA  Rage Fury Ati[/COLOR]


ctrl-atl-F1 to get back to a console if your mouse/keyboard is/are dead.

Good Luck.[/QUOTE]


any other ideas?
I appreciate the help!
Datchew.

---

### Post by az on 2005-01-30
"Dammit Jim... I'm a doctor not a linux guru!"

I'm just a perfusionist.


From the command line do:

sudo killall gdm
startx

and post the error lines (they begin with an EE)  (shift-pageup to scroll up)

---

### Post by Datchew on 2005-01-30
will do. 
probably tomorrow. 
have removable hard drives and i'll have to write down the error codes by hand, load my windows HDD and then type them all in here. 
Be back soon. 

thanks again. 
Datchew.

---

### Post by Datchew on 2005-01-30
ok, well, it wasn't as long as i thought. 

more and more i'm starting to think something i did editing that file to try and make the mouse work screwed this up. 

here's the output I got:

[COLOR=Red](==) Using Config File: "/etc/X11/XF86Config-4"
Parse error on line 66 of section InputDevice in file /etc/X11/XF86Config-4 
"/dev/psaux" is not valid keyword in this section. 

(EE) Problem parsing the config file
(EE) Error from xf86HandleConfigFile()

Fatal server error
no screens found[/COLOR]

then there was some junk like "... when reporting a problem make sure to do this...blah blah blah"...

then, it said:

[COLOR=Red]XIO: fatal IO error 104 (connection reset by peer) on X server ":0.0" after 0 requests (0 known processed) with 0 events remaining. [/COLOR]

that's it. 
The part where it said [COLOR=Red]/dev/psaux[/COLOR] is what i think i changed when i tried the mouse fix.  

Whattyathink?

---

### Post by az on 2005-01-31
"more and more i'm starting to think something i did editing that file to try and make the mouse work screwed this up.

here's the output I got:

(==) Using Config File: "/etc/X11/XF86Config-4"
Parse error on line 66 of section InputDevice in file /etc/X11/XF86Config-4
"/dev/psaux" is not valid keyword in this section."

That is exactly it.

sudo dpkg-reconfigure xserver-xfree86
That should have rewritten the file, though.  You should not get a parse error!  Try it again (the startx way).  If you still get an error, delete the file and start again

cd /etc/X11
sudo rm XF86Config-4

To get out of X started that way, CTRL_ALT_Backspace

---

### Post by Datchew on 2005-01-31
[COLOR=Red]cd /etc/X11
sudo rm XF86Config-4[/COLOR]

is that the command that deletes the file?
then the other command will re-create it?

---

### Post by az on 2005-01-31
Yes.

I think the reconfigure scripts for xserver-xfree86 ask you if you want to rewrite the file.   I think.

---

### Post by Datchew on 2005-01-31
well,  i did that, and it still gives me the same original error about x server not working in the blue screen. 

maybe i did it wrong?

not sure exactly what i did that time. 

any other ideas?

---

### Post by mr_ed on 2005-01-31
Before the dpkg-reconfigure xserver-xfree86, you have to do 
```
sudo md5sum /etc/X11/XF86Config-4 >/var/lib/xfree86/XF86Config-4.md5sum
```
otherwise the dpkg-reconfigure won't update the config file.

---

### Post by az on 2005-02-01
Are you trying differnt settings, or are you always picking the defaults?  You do not seem to have the mouse hardware that you are telling it to use.  That is the problem.  Try using /dev/input/mouse or any other options it gives you.



"sudo md5sum /etc/X11/XF86Config-4 >/var/lib/xfree86/XF86Config-4.md5sum"

I have never had to do that.

---

### Post by Datchew on 2005-02-01
ok... getting a little lost here, 
let's recap:

1.  I get the [COLOR=Blue]"cannot start x server (gui) likely not setup correctly etc[/COLOR]  and it asks me if i'd like to configure it. 

2. So i need to run this command [COLOR=Red]sudo killall gdm[/COLOR] and then 
[COLOR=Red]startx[/COLOR]

3. here's the output I got:

[COLOR=Blue](==) Using Config File: "/etc/X11/XF86Config-4"
Parse error on line 66 of section InputDevice in file /etc/X11/XF86Config-4
"/dev/psaux" is not valid keyword in this section.

(EE) Problem parsing the config file
(EE) Error from xf86HandleConfigFile()

Fatal server error
no screens found

then there was some junk like "... when reporting a problem make sure to do this...blah blah blah"...

then, it said:

XIO: fatal IO error 104 (connection reset by peer) on X server ":0.0" after 0 requests (0 known processed) with 0 events remaining. [/COLOR]

4.  so then i need to do this:  [COLOR=Red]cd /etc/X11
sudo rm XF86Config-4[/COLOR]

and that's supposed to take me through setting up my basic hardware.  I DID pick the defaults and I still have the same problem. 

5.  So now, I should try it this way? [COLOR=Red]sudo md5sum /etc/X11/XF86Config-4 >/var/lib/xfree86/XF86Config-4.md5sum[/COLOR] and put that command in the part I did first  which should now all be like this:


[COLOR=Red]sudo modprobe psmouse.

If everything is honky-dory, add psmouse to the /etc/modules file. You must sudo to do that.

sudo nano /etc/modules (CTRL-O to save, CTRL-X to leave)

sudo md5sum /etc/X11/XF86Config-4 >/var/lib/xfree86/XF86Config-4.md5sum

dpkg-reconfigure xserver-xfree86 to reconfigure X.

sudo killall gdm
sudo gdm[/COLOR]

Does that sound right so far?

---

### Post by Datchew on 2005-02-01
well, i went ahead and tried that. 

this line

[COLOR=Red]sudo md5sum /etc/X11/XF86Config-4 >/var/lib/xfree86/XF86Config-4.md5sum[/COLOR]

came back and told me that permission is denied. 
even with the sudo.  WTF??? i thought sudo was the same as doing it from root user and that the root login had ALLLLLLLLL the power!!!!

At this point, i'm thinking of just wiping/reinstalling ubuntu. 
Problem is, i have a couple pictures that I CANNOT afford to lose so if you guys are sick of this problem, could you tell me how to copy stuff or transfer it from this terminal?  i can browse to it, and i thought it'd be like dos in copying things, but it isn't.  Can a usb-flashdrive be used in the terminal mode?

Awaiting your answers anxiously. 
Datchew.

---

### Post by az on 2005-02-01
The problem is you are still picking the defaults.

You have to modify your mouse setting.  Chose a different device!

Keep trying all the devices untill you find the one that works.

---

### Post by Datchew on 2005-02-01
Well... 
here's an update. 
I'm doing some drinking now.  Hopefully, that will help spark my synaptic ability. (brain type synaptic)

ok, i'm not really drinking, but reallllly thinkin about it. 

I tried some advice off another post where they said to boot to the UBUNTU live cd and copy the XF86Config-4 file it creates to the one on the HDD under /etx/x11  but that didn't work. 

then i booted normally to the terminal (is that what it's called?) and ran 

[COLOR=Red]sudo xf86config[/COLOR]
which basically walked me through my entire list of mouse/keyboard/monitor/vid-card

tried several types of mouse settings, still no luck. 
at least i know that if i get sick of it, the live cd will enable me to backup files to my usb-stick.  i know it's not windows, but i'm almost at the point where i wanna reload the whole stinking OS!. 

will update on more mouse tries in xf86config in a few minutes. 
(hopefully from ubuntu)

Datchew.

---

### Post by Datchew on 2005-02-01
[QUOTE=azz]The problem is you are still picking the defaults.

You have to modify your mouse setting.  Chose a different device!

Keep trying all the devices untill you find the one that works.[/QUOTE]

will do.

---

### Post by Datchew on 2005-02-01
did every mouse device available in the list. 

did it in gdm (the blue gui) 
did it in [COLOR=Red]sudo nano /etc/modules[/COLOR]
did it in [COLOR=Red]xf86config[/COLOR]

screw it.  ](*,) 
either i'm missing out on something profoundly simple, or something is just screwed up.  

any last ideas before I format this junk and reinstall?

so far, linux seems like a WHOLE lot of work to get just the basic things working. 
(flash, mplayer for dvd's, java, shockwave, realplayer... and uh, let's not forget MOUSE!!!!!) 

i'm at my wits end here.  hope has left and it cursed at me as it walked out of my life.  

I do really appreciate the help though, even though i keep screwing this thing up. 
 :oops:

---

### Post by Compwiz on 2005-02-01
WOW, i have tried everytihing in this thread also  it is absolutely agonizing!! aarrgh  ](*,)  :-x  i am using an NVIDIA GeForce 6600GT AGP ... i think it might be the fact that it is AGP!!! but man! i cant even find the port number ... i do ```
lspci
``` and it gives me a bunch of zeros and "PCI:" things ... but no friggin AGP!! PLEASE HELP ... ANYONE!?!? oh, and dont reinstall, i have done it 5 times now!!! and the same thing happens EVERY SINGLE time. ne way i will keep trying to fix this and i hope someone will help us

---

### Post by az on 2005-02-01
"either i'm missing out on something profoundly simple, or something is just screwed up. 

any last ideas before I format this junk and reinstall?

so far, linux seems like a WHOLE lot of work to get just the basic things working. 
(flash, mplayer for dvd's, java, shockwave, realplayer... and uh, let's not forget MOUSE!!!!!) "

Let me get this straight.

You had X working and you tried to modify your XF86Config-4 file and that screwed up your X.

You can no longer get X running.

If this is true, so far, X should run again after you change your  XF86Config-4 file back.  This should be done by running sudo dpkg-reconfigure xserver-xfree86.

Why this is not working is beyond me.  Is your mouse plugged in?  Did you change any hardware?  Did you change any other file?


As for flash, mplayer for dvd's, java, shockwave, realplayer, they are proprietary apps so, yes, you have to do some work since the companies that make them don`t care about you.

---

### Post by Datchew on 2005-02-01
you are correct all the way across the board on your summation of what i did. 

everything was great.  Had a custom theme, gdesklets, all my stuff organized, all those apps (learned alot installing them) were installed and working great. 

however, i couldn't get the scroll button on my mouse to work so i changed whatever that was on the mouse settings in the link i mentioned at the beginning of this thread and POOF!!!  now i'm dead and reduced (sob) to working (sniff) in WINDOWS(shameless weeping). 

wish i had written down what i originally had in there. 

I haven't changed any hardware.  Still using the same optical usb logitech mouse. 

i'm truly stumped.

---

### Post by az on 2005-02-01
sudo apt-get install mdetect
sudo dpkg-reconfigure xserver-xfree86


Otherwise, I do not know what else you should try.  I'm looking for my hari-kiri.

---

### Post by Datchew on 2005-02-01
i'll try that. 
right now, i'm on the UBUNTU live cd. 
i can look at the XF86config-4 and XF86Config files in my /etc/X11 folder but i cannot edit or write to them. 

is there anything you can think of that i can do from teh live cd?
i.e.  at least post text of my files and maybe you can see the mistakes?

I notice that the XF86Config files that are "virtual" while running off the cd are different.  

i thought i could copy them to a disk or something and then boot regular and replace them, but my terminal prowess is lacking.  can't even figure out how to delete a file or make a new directory in that mode.

---

### Post by Fealuin on 2005-02-01
My situation is similar:

I tried Ubuntulinux Live CD and liked me enough to install it.

My PC is assembled with motherboard PC-Chips M909G, Celeron 1.8 GHz, 768 MB RAM and monitor Samsung SM793v. The motherboard is complete integrated and uses chipset intel 845GV/ICH4.

With Live CD, the graphic desktop starts at minimal resolution (640x480), but works.

However, installed i found no way to make ir work. XFree86 gives me a pair of error screens (like datchew describes)

I tried:
-base-config, 
-apt-get update and then apt-get upgrade

I add repsitories and again apt-get update and then apt-get upgrade...

Later I change warty for hoary and apt-get update and then apt-get upgrade...

I install xserver-xorg and neither... it send me to check out a file Xorg.0.log that have a lot of warnings and, near to end says:
**(EE) I810(0): No Video BIOS modes for chosen depth**
And too:
**(EE) Screen(s) found, but none have a usable configuration**

Recently I try dpkg-reconfigure xserver-xorg, but I think the thing is about **i845** video drivers, because isn't listed... I am novice in ubuntu and linux and I don't know what to do!

---

### Post by Datchew on 2005-02-01
Fealuin, yours sounds more like video drivers problem. 
do you have another video card that you could try and/or digup drivers for it?

---

### Post by Datchew on 2005-02-02
ok.  gave up. 

reinstalled ubuntu and everything is working fine. 
i'm posting from it right now.  

oh well, needed practice setting up stuff anyway. 

thanks so much for all the help.

---

### Post by azelter on 2005-02-02
Hi Guys,
That thread was a very intertesting read. I know it's bit late I now, after all the past agonizing but for future fiddling ...

Fiddling with config files is great, but do this first:
cp configfile configfile.bak
that way once you screw everything up you can just do the reverse command and replace your screwedup file with the origonal one.

I had a similar problem with X recently. I installed ubuntu with an old graphics card, which I then wanted to replace. So I did. After that my XF86config-4 file was obviously wrong and I got the aforementioned blue screen. I tried dpkg-reconfigure xserver-xfree86 which didn't help. I also tried xf86cfg, which hung, and then I tried xf86config, which I didn't even attempt to do as it asked so many questions.

I wonder if there is an Ubuntu expert out there who can tell me what program the installation program uses to configure X. Ubuntu obviously has very good hardware detection/X configuration abilities as doing a clean install normaly works great. If the computer can detect hardware and setup X correctly at instalation time, how can all us lazy bums re-run that program when we replace hardware or mess up a file? My solution was also to backup my data and reinstall. Took 1 hour. But still. Rather an embarising solution to getting X configured properly after a change of graphics card. SuSE has something called SaX2 which configures X beautifully. Ubuntu can obviously do it to as it does at installation.  What am I missing???

Thanks!

Alex

---

### Post by Datchew on 2005-02-02
cool. 
thanks much Alex.  that is actually what i'm planning on doing this time before i mess with anything.  I didn't know how to do it though, so that's a big help. 

I agree that replacing hardware is a pain. 
Please post if you come up with something that makes it easier. 

Datchew.

---

### Post by JayCnrs on 2005-02-11
I ran into a similar problem, everything was running fine then the Xserver stopped working. After some agonizing troubleshooting I reliezed that I had disabled the hotplug service  ](*,) 

When I re-enabled the hotplug service I rebooted and voila my Xserver was working again, during the hotplug service starting it loads the agpgart module 

Hope this helps if somebody runs into the same problem.

---

