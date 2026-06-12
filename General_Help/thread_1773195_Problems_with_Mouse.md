---
title: "Problems with Mouse"
date: 2011-06-01
forum: General Help
---

### Post by BrierRabbit on 2011-06-01
Hello all-

I'm new to Linux, and haven't been able to find a solution to this problem. 

I just got a new netbook, an HP Mini 1103. I installed Natty as soon as I got it, and it has been working fine the entire time (the last couple of weeks). I go to boot it up today, and my mouse buttons don't work. I've been fiddling with it all day, and here's what I have found- the left and right click generally work on the log in screen, but sometimes they won't at all. Once the desktop boots up, I can use the left click, but not the right. The left click only works until I try to open an application, such as firefox. Once I do that, the mouse will work within the application window, but I cannot click on anything else outside of the window. The menu bar on the side won't even pop up.

Any solutions/people with similar problems? Ubuntu was awesome until this morning, but this makes it pretty useless.

---

### Post by jerrrys on 2011-06-01
are you running a custom theme?  did you get any updates yesterday?
that was a couple of things i seen while searching the problem.  take a look here

[http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=mouse+11.04+natty&as_qdr=all&sa=Google+Search&lang=en#881](http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=mouse+11.04+natty&as_qdr=all&sa=Google+Search&lang=en#881)

---

### Post by BrierRabbit on 2011-06-01
No, I'm not running any custom themes... and I don't think I got any updates yesterday, but I can't check for certain because the mouse craps out.

---

### Post by jerrrys on 2011-06-01
do you have a mouse that you could plug in and try?

---

### Post by BrierRabbit on 2011-06-01
Yeah, I have a logitech wireless that I tried as well, and I get the same thing.

---

### Post by jerrrys on 2011-06-01
open a terminal (Alt + F2 and enter **gnome-terminal** in the box, then run)

now that your in terminal enter
sudo /etc/init.d/dbus restart

now enter your password (there will be no visual indication of this)

and again hit enter

---

### Post by BrierRabbit on 2011-06-01
Ran it, and something came up in the terminal, but the screen went black before I could read it and has stayed that way since. Next steps?

---

### Post by jerrrys on 2011-06-01
restart

---

### Post by BrierRabbit on 2011-06-01
No good =/

---

### Post by jerrrys on 2011-06-01
ok boot into recovery mode and in terminal enter **startx**

---

### Post by BrierRabbit on 2011-06-01
Booted in Safe mode, and ran startx- 
got "X: user not authorized to run the x server, aborting" 

and then "XIO: fatal IO error 11 (Resource temporarily unavailable) on X server ":0" after 7 requests (7 known processed) with zero events remaining".

Do I have to run it with sudo?

---

### Post by jerrrys on 2011-06-01
yes go ahead and go to root

sudo startx

---

### Post by BrierRabbit on 2011-06-01
Ran it, and got this-

"Fatal server error: Server is already active for display 0. If this server is no longer running, remove /tmp/.X0-lock and start again"

"Please consult the The X.Org Foundation support at [http://wiki.x.org](http://wiki.x.org) for help"

"ddxSigGiveUp: Closing log"

"xinit: connection to X se4rver lost"

"XIO: fatal IO error 11 (Resource temporarily unavailable) on X server  ":0" after 7 requests (7 known processed) with zero events remaining"

---

### Post by jerrrys on 2011-06-01
ok, looks like all were doing is digging a deeper hole. dbus restart should of been just that, but now something else is amiss. in order to get back to the original problem of fixing the mouse i think the best way to go is just reinstall.  but before you do that, let me explain.

11o4 is a work in progress and subject to breaking down.  you can reinstall, but theres a good chance that first update will break it again.  and its back to square one.

i would, for the moment suggest that you instead install 10.04.  this is the stable long term release and not subject to such breakdowns. and then wait untill 11.04 has become more stable.

what do you think?

---

### Post by BrierRabbit on 2011-06-01
Sounds like a plan. Thank you a ton! You've been incredibly helpful.

---

### Post by BrierRabbit on 2011-06-01
Also, will the fact that I am running it on a netbook slow 10.04 down at all? I have a 250Gb hard drive, and 2Gb RAM.

---

### Post by jerrrys on 2011-06-01
nope, not at all.  it will run just fine on those specs

[https://help.ubuntu.com/community/Installation/SystemRequirements](https://help.ubuntu.com/community/Installation/SystemRequirements)

---

### Post by BrierRabbit on 2011-06-01
I've got troubles- attempting to install 10.04, and the mouse button problem has appeared again. I'm stuck halfway through the process because I can't select the right field, or return. Any ideas?

---

### Post by BrierRabbit on 2011-06-01
Would wiping 11.04 off the hard drive before installing 10.04 be the way to go?

---

### Post by jerrrys on 2011-06-01
yes it would and just delete it.  do not format it to ext4 or anything.  that way when you install 10o4 the install will detect the free space and give you the option to install there.  also delete the swap.

---

### Post by BrierRabbit on 2011-06-01
I don't have a partition or anything on the hard drive... what would be the best way to remove 11.04?

---

### Post by jerrrys on 2011-06-01
if all you have on the hdd is ubuntu then no need to wipe it.  just install and check the "use entire disk" option.

i just figured that you were dual booting with windows.

---

### Post by BrierRabbit on 2011-06-01
That is what I have tried to do, but the mouse issue shows up immediately when I get to the install screen for 10.04, and I can't get through it to finalize the removal. Can I remove 11.04 through BIOS or anything like that?

---

### Post by jerrrys on 2011-06-01
this is the screen that ask if you want to try ubuntu or install ubuntu?

---

### Post by BrierRabbit on 2011-06-01
I get an installer boot menu that is in the same format as the BIOS menu, no mouse pointer. It asks whether I want to run from the USB, or install Ubuntu on the hard disk. If I run it from the USB, it will boot to the desktop, but the same mouse problem will show up. If I choose install on hard disk, I get the standard installation process window, but a step or two in the mouse will working, and I can't finish it.

---

### Post by jerrrys on 2011-06-01
i would like to see if we can work around this by staying away from the GUI.  when the first screen comes up (the one looking like BIOS) go straight to install ubuntu.  also your up/down arrow keys should work at this point if your mouse will not.

EDIT:  and in the mean time i will dig deeper into this netbook of yours to see what i can find.

---

### Post by BrierRabbit on 2011-06-01
How do I avoid getting sent to the GUI when I do this though? 

Also, up/down arrow keys do work, but they won't let me select certain fields, which is why the hard disk install has been a bust (ie. I can't select the "re-enter your password" field that would allow me to proceed to the next step in the install).

---

### Post by jerrrys on 2011-06-01
that is what i wanted to know, if it would let you do it at that point.  when you go directly to install the full GUI is not installed.  be back in about half an hour.

---

### Post by BrierRabbit on 2011-06-01
Thanks again for all your help, you've been a lifesaver. It's late here; I'll be back tomorrow at about 8pm EST.

---

### Post by jerrrys on 2011-06-01
great, ill continue researching this, but so far you seem to be the only one with this mouse problem.  see you in the morning.

---

### Post by jerrrys on 2011-06-02
p { margin-bottom: 0.08in; }  Ok, heres what I found:
 

 the [HP site]("http://h30434.www3.hp.com/t5/forums/searchpage/tab/message?q=Mini+1103#/?page=4&q=touch+pad&search_type=thread") has turned out to be the most informative.  The most often fix used is drivers, which they do have for linux.  Second biggest fix is a power removal. And third is send it to manufacture for repair.  Hope these pics are readable on your screen.


[ATTACH]193985[/ATTACH]
[ATTACH]193986[/ATTACH]
[ATTACH]193987[/ATTACH]
 

 Drivers would be a good idea if you have a system to install them on.  Power removal I guess is worth a shot.  And repair I guess will be last resort.
 

 A general fix-all found in this forum would be “no acpi” (F6 at beginning of install) but that is usually for older machines. Another is installing in “safe mode” (another option at beginning of install). 

 

[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

Since your lappy was working with 11o4 I think you should again try 11o4.  Reason for this is just to see that mouse work and prove beyond doubt its not hardware.
 

 As far as finding mouse problems on your model; none seem to be out there.  I have search the ubuntu forum, expanded to linux search and then expanded to include windows. And found nothing of importance.  Only HP seems to have general answers.
 

 Your thoughts

---

### Post by BrierRabbit on 2011-06-02
All sounds good- I'm going to attempt to install drivers now

---

### Post by BrierRabbit on 2011-06-02
Bugs are getting worse- too buggy to install drivers- attempting hard reset.

---

### Post by BrierRabbit on 2011-06-02
Woo! The hard reset failed the first time, but I then tried the one you had listed in your screenshot, and that has seemed to do the trick.

Again, I am amazed and grateful at the amount of time and effort you have put into this. You have been a total lifesaver- I'm pretty much a noob when it comes to the real inner workings of software.

Thank you!!!!

Now to update all of my drivers...

---

### Post by BrierRabbit on 2011-06-02
F. 

Apparently only a temporary fix... not even the hard reset works to fix the problem now.

---

### Post by jerrrys on 2011-06-03
#toc, .toc, .mw-warning { border: 1px solid rgb(170, 170, 170); background-color: rgb(249, 249, 249); padding: 5px; font-size: 95%; }#toc h2, .toc h2 { display: inline; border: medium none; padding: 0pt; font-size: 100%; font-weight: bold; }#toc #toctitle, .toc #toctitle, #toc .toctitle, .toc .toctitle { text-align: center; }#toc ul, .toc ul { list-style-type: none; list-style-image: none; margin-left: 0pt; padding-left: 0pt; text-align: left; }#toc ul ul, .toc ul ul { margin: 0pt 0pt 0pt 2em; }#toc .toctoggle, .toc .toctoggle { font-size: 94%; }body { font-family: 'Times New Roman'; color: rgb(0, 0, 0); widows: 2; font-style: normal; text-indent: 0in; font-variant: normal; font-weight: normal; font-size: 12pt; text-decoration: none; text-align: left; }table {  }td { border-collapse: collapse; text-align: left; vertical-align: top; }         &#65279;ok, i have one last idea.
 
HP does not actually support linux per say.  they support SUSE.  download openSUSE and give it a try.  i really expect the same results, but you should then be able to go to HP and get live support.  i have a feeling that HP will not want to talk to you if your using ubuntu.

---

### Post by BrierRabbit on 2011-06-03
Ok, I'll try that- I just managed to install 10.04... and I'm still having the same problem. Maybe hardware then? I'll try installing openSUSE and see what happens.

---

