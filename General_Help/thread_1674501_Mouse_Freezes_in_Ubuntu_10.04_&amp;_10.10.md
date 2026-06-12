---
title: "Mouse Freezes in Ubuntu 10.04 &amp; 10.10"
date: 2011-01-24
forum: General Help
---

### Post by Silt3003 on 2011-01-24
Hi, I am new to this forum and to the Ubuntu platform I have recently installed Ubuntu on my desktop. Whenever I log in after approx. 2 minutes the keyboard or mouse (or sometimes both) freezes. The mouse and keyboard are connected via USB and not p2/p. I would appreciate some help if someone has seen this problem before as rebooting every 2 min in order to use the OS is not exactly convenient :D

---

### Post by tigerstripedcat on 2011-01-24
What you are talking about is pretty rare with modern Ubuntu installs. It could be losing conectivity to keyboard/mouse or just locking up. Both are kinda rare.  

Is this a custom built computer?  Was this a fresh install of Ubuntu.  Have you tried booting with a Live CD and seeing if it works there?

---

### Post by Sleven7 on 2011-01-24
Hi Tiger,

Open your screensaver preference dialog box

System>Preferences>Screensaver

Uncheck the box that says,"Activate screensaver when computer is idle"

Uncheck the box right below it,"Lock screen"

Click on the Power Management button

Change Display from 30 minutes to never.

See if your lock up problem doesn't go away.

---

### Post by Silt3003 on 2011-01-24
Sleven7 ty for the advice however the mouse still froze approx 2-3min after startup after I implimented your solution. In response to tigerstriped the computer is custom built and this is a fresh install of ubuntu on a recently installed 1TB Seagate Hard drive. Also the freezing problem occured while running from a live cd also.
Here are the desktops specs:
Motherboard: Asus P5ND2-SLI
Memory: Dual Channel DDR2 RAM Channel A: 2x 512mb Memory cards Channel B: 1x 1Gb Memory Card
Hard Drive: 1TB Seagate
Graphics Card: Gigabyte Nvidia GeForce 8800 GTS
CPU: Intel 4 Series Unsure exactly the make or Ghz if this is needed please mention it and I will remove the fan to find out this is a computer I have had for a few years.
 
I would really appreciate an answer :D, Silt

---

### Post by Timmer1240 on 2011-01-24
About 6 months ago I had some freeze up problems I was using a usb lazer type mouse I had an old serial port mouse so I plugged that
in and It hasnt froze since.Just a thought.

---

### Post by tigerstripedcat on 2011-01-24
Ok so this SEEMS very fundamental.  If you get it to freeze up on the liveCD then this looks more like a hardware related problem or your stuff is just so new that ubuntu is having a hard time loading the right drivers for everything. 

1) Just to be clear, are we talking about hard freezes or just mouse or keyboard.  It definitely is hard to distinguish between a hard freeze and a simultaneous mouse/keyboard failure. But simultaneous mouse/keyboard failures are very rare.
2) Do you have any other mice or keyboards you can try?
3) Do you have this machine dual booting with windows?  Is everything ok in windows?
4) What's the wattage of your power supply?
5) Does your bios support temperature monitoring?  If so, what is the temp of the cpu and memory.

---

### Post by rocthrttle on 2011-01-24
i'm with timmer. your best bet is to try out a different mouse. rule that out first. i would grab something common like a dell laser mouse. i never had trouble with one of those. also check your bios. some require usb mouse enabling. windows may work around this automatically but linux may require that the bios be in order. just a thought good luck.

---

### Post by tigerstripedcat on 2011-01-24
Wait. His keyboard and mouse locks up and your solution is to try a different mouse?  Ok, fine, let's try that first ;).

---

### Post by rocthrttle on 2011-01-24
to keep with tigerstripedcat's thermal related idea.

"sudo apt-get install sensors-applet" in the terminal
right click on top gnome panel and you can add thermal sensors to panel

---

### Post by rocthrttle on 2011-01-24
hey sometimes the simple answers work the best. we dont know what kind of mouse he has whether it is wireless, gaming related, or just cheap and crappy. i'm with you. it could be something else. i guess the real test would be to livecd boot another rig and try the mouse there to verify that it can work in ubuntu.

---

### Post by tigerstripedcat on 2011-01-24
Well that's why I asked him if it was mouse AND keyboard.  To the OP this is REALLY important.  If it is both that are locking up I give it 1/100 odds that replacing the mouse would fix both.

---

### Post by Timmer1240 on 2011-01-24
Ive had my machine lock up to because of heat issues usually it would reboot on its own though anythings possible!

---

### Post by rocthrttle on 2011-01-25
tigerstripedcat your sniffed this one out perfectly. timmer if you over heated it even once you may have ruined the capacitors on the mobo. 

[http://fubarjohnnyr.com/forums/viewtopic.php?t=5](http://fubarjohnnyr.com/forums/viewtopic.php?t=5)

if any capacitors look like the damaged ones in the link above your mobo is trashed and the source of the lockups. replace the mobo.

---

### Post by tigerstripedcat on 2011-01-25
No I don't think that's it.  You can check, but that is also rather unlikely.  

CPUs are made to immediately shut off when a temperature threshold is reached.  It is rather hard these days to damage a processor--just ask any of the hard core guys at the overclocker forums.  As for the mobo, the capacators blow when there is too much current running through them, not really temperature.  Either way, I, nor anyone I know, nor anyone on these forums have had capacitors blow on their motherboards.  That's not to say it doesn't happen--you obviously found a thread where the site admin has collected a hundred or so, but that's a hundred of the tens, if not hundreds of thousands of people registered on that forum. And if a capacitor blows, the chances of actually starting up are also kinda small.

The order of likelihood for lockups:

1) Software
2) Software
3) Software
4) Memory/power supply/overheating

---

### Post by rocthrttle on 2011-01-25
processors are well protected but depending on the mobo maker the caps tend to get pretty cheap out there. i'm just relaying what i've delt with lately. if he doesnt have enough case airflow and is overclocking with voltage and clock speeds he may have damaged the caps. dust can cause bulging caps. i had a friend recently tank a mobo due to bad airflow and overheating. i gave him a salvaged mobo and it worked great at first but then overheated. he just kept rebooting. it eventually hit the point where it boots but will not handle any real load. the voltages do a happy dance and the mobo senses it and then it shuts off. timmer if you are rebooting this often i would say its the caps. similar to this story i told. just something to consider. it isnt always software. software is usually first on my list just to be safe. (when dealing with windows it's hard to tell, booting a livecd of ubuntu usually tells me if it is hardware and not software)

---

### Post by Silt3003 on 2011-01-29
First a thanks to everyone who has responded to this thread unfortunantly as yet none of the fixes have worked so here is more information.
I have tried plugging in a dell laser Usb mouse and an asus laser Usb mouse both seem to freeze when I am opening a tab or a file. I have also tried another video card this also met with no success.
Also in response to a few comments here are the average temperatures of my components.
CPU:63 degrees Celsius
MB:39 degrees Celsius
Video Card: 40 degrees Celsius
Also the wattage of my power supply is 430W.
 
I hope this helps :D

---

### Post by Oliver90 on 2011-01-29
software is usually first on my list just to be safe. (when dealing with  windows it's hard to tell, booting a livecd of ubuntu usually tells me  if it is hardware and not software.

---

### Post by Silt3003 on 2011-01-29
As I said before the same problem occured while running the live CD. Also it is a single OS Drive and does not use windows.

---

### Post by tigerstripedcat on 2011-01-29
Go back in the thread and answer the questions if you want help:

1) Does it happen in windows? Do you even have windows?
2) Keyboard/mouse or both?
3) How often?
4) Temperature?
5) Power supply?
6) Memory type/size/brand?

---

### Post by ste_bran on 2011-01-29
> **tigerstripedcat said:**
> What you are talking about is pretty rare with modern Ubuntu installs. It could be losing conectivity to keyboard/mouse or just locking up. Both are kinda rare.  

Is this a custom built computer?  Was this a fresh install of Ubuntu.  Have you tried booting with a Live CD and seeing if it works there?

Is it really so rare, tigercat? I have an almost identical problem as Silt, but I posted about it in a 166-page thread (#1478787) where others are having a similar freeze on 10.04 and 10.10.

Anyway, to answer your questions (above and in your last post):
Yes, custom built, brand new computer and fresh install of ubuntu and my first time with ubuntu(so I have lots of possibilities for errors!:p).

1. Do not have Windows installed, so don't know if it happens there. It does happen both on Live CD and on my fresh install of 10.10 with kernel 2.6.35-24.
2. Both mouse and keyboard -- not always at the 2-minute mark like Silt, sometimes longer. The computer still is alive, tho -- when I press the power button, the screen comes back on and I am at a login screen where I am asked for my password, and I see the mouse pointer. I can't enter anything or move mouse, of course.
3. Everytime, so far. Just installed on the 26th.
4. Temps -- cpu 49C, m/b 33C
5. PSU - Corsair AX850. Fan barely spinning, cool to the touch.
6. RAM - G.skill ripjaws 2x4GB, DDR3-1333 7-7-7-21 running stock, passes Memtest86+

Going to try different keybd & mouse and go back to kernel -22 to see what happens.

---

### Post by Silt3003 on 2011-01-29
tigerstipedcat all of your questions have been answered throughout the thread just not within the one reply.

---

### Post by clhsharky on 2011-01-29
Silt3003

Just for testing sake, remove all usb devices and have mouse & keyboard plunged in motherboard.

I have had strange thing occur with usb devices in past.


Sharky

---

### Post by tigerstripedcat on 2011-01-30
Well if it happens with the liveCD every 2 min then this should be easy to fix.  (As long as it's not in the exact same place when you boot with the liveCD, if that's the case then it's the CD or 10.10 that's the problem.) My guess is that the new mouse/keyboard didn't work, did it?  

Keep trying to boot the liveCD, and run a computer burn-in program if you get in successfully. Here's one:

[http://www.passmark.com/products/bitlinux.htm](http://www.passmark.com/products/bitlinux.htm)

Run it in a loop overnight and see if it locks up, if it does, notice what test it was running at the time.  Was it video? cpu?

But you probably won't make it that far.  If it's every two minutes we just need to keep removeing/reseating things until it works

1) remove all ram except for one module and maybe try a different module
2) disconnect everything from the computer except for monitor/mouse/keyboard
3) Leave the cover off of the computer (Is that 60deg idle or full load?)
4) Reseat the memory/video card fan
5) take out any other expansion cards

Make it as simple as possible and try to boot the liveCD.  

If it still doesn't boot correctly after all that:

1) Get a new cd, try liveCD 8.04 or something else, or better yet, try a windows CD and see if you can boot to the install program, try booting off of an ubuntu 8.04 liveCD off of a usb drive.
2) If you still get lockups with a completely different OS and off a usb drive, you reseated everything, made sure everything was cool, unplugged everything, then you have no choice but to start replacing things.  You should note that your temp is a bit on the high side (if I remember the range correctly) and your power supply is a bit on the low side.  Of course it SHOULD work with both of these, but it also SHOULD boot to a liveCD, so after all these tests it could be your power supply is failing or you need better cooling.  It also could be the memory.  Do you have any other computers that you can use to canablize parts only temporarily.  It would be great if we could put in different ram/PS/video card, swapping things in and out to see if we get it to fully post.

Well run all that and then post back the results.
Good luck.

---

### Post by tigerstripedcat on 2011-01-30
> **ste_bran said:**
> Is it really so rare, tigercat? 

Actually, yes it is despite your anecdotal evidence of a handful of people who had similar problems.  Look, maybe there might be a usb detection/login or some serious bug with 10.10 or the kernel, if it is that is the only reason there would be large number of lockups. Maybe thats the case.  But under normal circumstances, no, full-on lockups are not very common.  Just search the threads, you'll run into nvidia driver problems 50 times more frequently than problems locking up.

But if you tried a different version of the OS and a different kernel, then it is probably not that.  Do yourself a favor, try a different distro altogether. Just temporarily.   Go to distrowatch.org and pick one and download their liveCD and see if it locks up still.  If it does not, it's probably the ubuntu software, if it does, then it's probably something hardware related.  

Now know there is a difference between:

1) Unable to receive input from the keyboard or mouse
2) A lockup

These are COMPLETELY different, and the distinction is VERY important.  The first goes no further than xorg or something software related or maybe the keyboard or mouse (ok maybe the port), the second can be almost ANYTHING.  If it is a bona fide lockup then replacing the mouse/keyboard will not fix your problem. If it is just a detection problem where both the keyboard and mouse are not detected then that is different (also VERY rare if it is both at the same time.)

When you boot to your login screen, BOTH the keyboard and the mouse don't work?  Do you notice the cursor blinking? (I can't remember if they do or not I haven't logged in locally on my machine in a long time.)  If you hit Ctrl+Alt+F2 does that do anything?  Ctrl+Alt+Bksp?  Does your numlock light blink when you press the button?

---

### Post by ste_bran on 2011-01-30
> **clhsharky said:**
> Silt3003

Just for testing sake, remove all usb devices and have mouse & keyboard plunged in motherboard.

I have had strange thing occur with usb devices in past.


Sharky

Hey, Silt, did you try what Sharky suggested above? Use a PS/2 mouse and keyboard? I have the opposite setup as you -- I have PS/2 mouse and keyboard, so I am now trying mouse and keyboard thru USB. I'll let you know if it helps. But at least you and I can eliminate the conector(s) as being the problem.

---

### Post by Silt3003 on 2011-01-31
It may take me awhile to get my hands on a ps/2 mouse but in the meantime I will try the process that tigerstipedcat recommended. Thankyou all for your help I will try to eliminate as many possibilites is I can until I find the problem. If I find the solution I will update and if I do not I will go through everything I tried in the hopes of someone else figuring it out from the information I provide.
\/
"'
Peace

---

### Post by ste_bran on 2011-01-31
OK, now we're getting somewhere! I changed my screensaver settings as suggested by Sleven earlier in this thread, and plugged in mouse & kybd thru USB.

Then fired up my comp, and let ubuntu sit there doing nothing, which it did for 14 hours or so -- my longest time by far of having the computer "working" -- if a computer doing nothing except being on can be called working. I did move my mouse and use the keyboard a little just to be sure they were alive.

After my first successful test, I then started using the browser to visit some sites and watch some videos. So far, so good after another five hours. Although it may jinx it, I am ready to say my problem is solved. Now I have to go back and see which one of the two changes did it.

Silt, I know you are looking for a PS/2 mouse/keyboard, but in the meantime, you did set the screensaver settings like Sleven said, right? I'm not crazy about no screensaver, but better than the alternative.

If the answer is 'yes,' you might try what I did -- just turn on the computer and let it sit and see how long it will go without crashing/freezing, whatever.

---

### Post by stchman on 2011-03-14
I too am getting random freezes with an external USB mouse on my laptop running Ubuntu 10.04.2.

It does not affect my desktop PCs.

---

### Post by rhintintin on 2011-06-23
Hi,

I am having a similar problem. I've installed using the windows installer. The mouse works for a bit and then freezes. It does this the very first time I run ubtuntu after an install so I can rule out a freeze- it continues to copy files to complete the install. The first time it did it I thought it was a freeze so restarted (messing up the install). Formatted the installation drive, tried again and just had the same problem. It is copying the files as I type. 

I too am on a custom build using USB mouse. I have a PS2 Keyboard which also freezes (no light if I press the caps button). I've got no problems in windows. I really want rid of Microshaft but seem stuck at the moment :(

---

### Post by tigerstripedcat on 2011-06-23
Get a USB keyboard, let it complete the install until it promps for user input (I think it will restart automatically and wont prompt until you're in ubuntu).  If the keyboard and mouse are unresponsive reseat the conections but when you plug them back in leave them in for 5 min (its ok to move the mouse or type to test for responsiveness) but sometimes it takes a min or so for the usb stack to detect and install a driver before you can actually use it.  If it still doesnt work, try different ports, you probably have a few (try nto into a hub).  Just keep reseating and waiting.  If it is not actually locking up and its only a keyboard/mouse problem, theres a high probability this will fix it.  Try different usb mouse/keyboard if it still doesnt work.  Does it work when you boot into a live cd?

---

### Post by kschumake83 on 2011-10-27
i had a similar problem a while back on an old dell e521, the mouse would freeze after a few minutes in ubuntu but not in windows. i tried all sorts of tricks that people on this forum told me about and nothing seemed to work. through some extensive research i found out my problem was in the bios, dell bios's really suck... now i wouldn't reccomend flashing the bios as a first try thing, i've heard that that can make a brick really quick out of your computer if something goes wrong, but as a last resort if you cant figure out the problem it might be a good thing to try. it worked wonders on my machine. i have had mint running on this machine for about 2 days now and no freezes after bios update. before it would freeze every 3 minutes or so.

---

