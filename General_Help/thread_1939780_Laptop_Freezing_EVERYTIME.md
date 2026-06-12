---
title: "Laptop Freezing EVERYTIME"
date: 2012-03-12
forum: General Help
---

### Post by JrMolten on 2012-03-12
Im kinda new to ubuntu, so...
Yeah, I got an old laptop ( bout 7 years ) from my uncle. It originaly had windows XP on it, and was EXTREMELY slow, and freezed all the time. Well, then i got UBUNTU 10.04 (lucid lynx) installed on it, with no problems. Until I tryed to update it. Freezed at the first 30%, just like it did in windows:mouse dint move, no animations, nothing. Just solid screen, frozen. I could wait 3 hours, nothing happened. That freeze dindt happen when I wasn't using the laptop: only on internet apps, VIDEOS, games and stuff like that. Sometimes even when using only Firefox. I tryed reinstalling ubuntu so many times...
Then, one of those times, the laptop actually worked. With no freeze for like a week. Then, it froze when i tryed running Ace of Spades on it. After that first freezn, it started to freeze every 5 minutes again.
Please, HELP"

---

### Post by winh8r on 2012-03-12
Best thing to do is post details of the make and model of the laptop.

how much ram does it have?

what graphics card does it use?

Will it boot and run normally using a LIVE CD?

---

### Post by Mark Phelps on 2012-03-12
Sorry, but a laptop that is > EXTREMELY slow in WinXP and also froze a lot, is likely to be even SLOWER using any 11.x version of Ubuntu, primarily due to the demands of the Unity desktop.

Also, freezing could be a symptom of a failing drive (i.e., lots of bad sectors) and that is not going to improve in Linux.

Laptop specs will help at least determine if it COULD run OK using Ubuntu 11.x.

---

### Post by JrMolten on 2012-03-12
My laptop is an Itautec, cant find model because what seems to be it is scratched. Heavy. All I know about it. Also, i did NOT install ubuntu 11.x, the version i have on this laptop is 10.04. This laptop run like 1.5x faster than before. Only bad things is it keeps freezing. What i just dun understand is the fact that IT DID RUN NICELY for a week, but after the first freeze, it started freezing alot again. So it oes not seem to be hardware problem (could be, im noob to hose kind o' things) but something whroung in the kernel, or ubuntu code.

I appreciate your help, guys!

---

### Post by 2F4U on 2012-03-12
Does that happen after some time of use and is the laptop getting hot? Did you run the memtest program from the liveCD?

---

### Post by matt_symes on 2012-03-12
Hi

Both XP and Ubuntu freeze ?

Boot into the BIOS screen that displays the clock and leave overnight or longer.

If it still freezes (clock stops ;) ) , you are looking at hardware. Maybe CPU temps, motherboard problems, or memory. You can take out the hard drive for this test.

Either way, (almost) sure fire hardware if this test fails. I've had the same problem in the past.

Kind regards

---

### Post by Mark Phelps on 2012-03-12
From your further info, it doesn't sound like SW or Ubuntu related problems; instead, it sound like hardware.

I'd go with either overheating and/or failing hard drive -- possibly memory failures as well.

Others have already suggested stuff you can try to see if it will still freeze under different conditions.

---

### Post by dragonfly41 on 2012-03-12
My guess .. *and it is a guess* .. is too many tabs open in firefox browser some with flash media access.
At least that is what I found.   I installed firefox session manager add-on to kill the problem tab(s) causing the freeze when firefox opened.

Try launching firefox in safe mode to see if this helps.   Or try installing opera.

---

### Post by JrMolten on 2012-03-13
Almos 32 hours now since I but the laptop on boot menu...

Clock still running.

Discards Overheating ( checked that)and "POSSIBLY" hardware.
I still think it might be hardware, sumting bout the video card or something related.

Firefox in safe mode?
I tryed opera actually. Still freezin. Seems its not ONLY internet and stuff, just about everything. Typing ( yeah... ) opening the terminal, open browsers, open a new tab and, the most critical and 100% sure-to-freeze, the deadly YouTube.

Thanks for the support!

---

### Post by matt_symes on 2012-03-13
Hi

If the BIOS clock is still ticking then that is a good sign.

Test SMART status of hard drive next if it has it and run a SMART test on the drive. If the drive fails the SMART test, remove it and put it in an external casing and run the SMART test from a different laptop/computer. It the laptop freezes during the SMART test then test from another laptop/computer anyway.

That will help to pin point drive controller or drive issue, if that is the problem.

If the drive does not have SMART then look for DST (drive self test) software from drive manafacturer.

Check memory using memtest. Run it overnight at least.

Those would be my next steps.

Because both XP and Ubuntu froze, i would concentrate on hardware for the moment. When you are confident that hardware is not the problem then look at software.

Don't discount CPU temps at this stage. How are you checking them ?

Kind regards

---

### Post by Mark Phelps on 2012-03-13
Boot menu doesn't stress the graphics much and there's almost nothing running at that time.

Try booting to a desktop and leaving it THERE to see if it still freezes -- without you actually using it.

Still think it could be the hard drive -- since launching ANY app requires reading from the drive, and running any video streaming app or any Web app will require LOTS of writing to the drive.

---

### Post by JrMolten on 2012-03-14
Hey GUYS!

I ran memtest86+...

*****Pass complete, no errors, press Esc to exit*****

Yey! So itz not the memory, i guess. Think thats good. Heard memory problems are relly nasty ****.

Soo, now im wondering how to do the SMART test. Got no idea ofo to do it. Hope U guys can help me...

Thanks All!!!!

---

### Post by winh8r on 2012-03-14
On Ubuntu 10.04 go to 

System > Administration > Disk Utility

select your hard drive from the menu on the left hand side

then select "SMART Data" from the top right .

click on "run self test" and let it complete.

---

### Post by matt_symes on 2012-03-14
Hi

> **winh8r said:**
> On Ubuntu 10.04 go to 

System > Administration > Disk Utility

select your hard drive from the menu on the left hand side

then select "SMART Data" from the top right .

click on "run self test" and let it complete.

This is the test i would run next. 

Just as an addendum to this excellent advice, i would suggest running an _extended_ test.

Get a drink. It will take some time.

Kind regards

---

### Post by JrMolten on 2012-03-15
Yeah.

Test sad "nothin' to worry bout".

Keeps freezing, just the way it did before.

Now, something strange is that when i choose to ran a FULL test on the laptop, it freezed on screed sutuff. Got pinky and freezed. Anyways, i jumped that test an it went ok.

Thanks guys!

---

### Post by matt_symes on 2012-03-15
Hi

I don't understand this.

> Now, something strange is that when i choose to ran a FULL test on the laptop, it freezed on screed sutuff. Got pinky and freezed.

How are you checking your CPU temps ?

Kind regards

---

### Post by larsion on 2012-03-15
As you said in the description. the laptop was 7 years old and currently running Ubuntu 11.xx. So i guess the problem occur because the GPU is too old. why don't you try to downgrade to Ubuntu 10.04 which has less graphic effect and see if that can help solving the problem

---

### Post by matt_symes on 2012-03-15
Hi

> **larsion said:**
> As you said in the description. the laptop was 7 years old and currently running Ubuntu 11.xx. So i guess the problem occur because the GPU is too old. why don't you try to downgrade to Ubuntu 10.04 which has less graphic effect and see if that can help solving the problem

But XP was also freezing.... That's the only thing that makes me think the issue may be something different.

I think it's a good idea to try a LiveCD/USB of Lubuntu or Xubuntu though.

Kind regards

---

### Post by JrMolten on 2012-03-16
Heh. Heh.

I actually did run sistem test instead of disk utility. Sorry guys. Like I sad, im really noobish on ubuntu. Running disk utility NOW.

Sooooo...

Another noobish question: How do i boot form "liveCD"?

Itz like, insert the disk and select TRY ubuntu or something like that? Plese tell how to do it, cuz i dun now.

Thanks All for the support!

---

### Post by matt_symes on 2012-03-16
Hi

> **JrMolten said:**
> Heh. Heh.

I actually did run sistem test instead of disk utility. Sorry guys. Like I sad, im really noobish on ubuntu. Running disk utility NOW.

Sooooo...

Another noobish question: How do i boot form "liveCD"?

Itz like, insert the disk and select TRY ubuntu or something like that? Plese tell how to do it, cuz i dun now.

Thanks All for the support!

You need to make sure the first boot device in the BIOS is your CD player and not your hard drive. You can do this from the 'boot order' section in the BIOS.....

.... or, most new computers will have a quick select boot option that, on my laptop at least, is selected by pressing F8 (and holding) just after switching the computer on. There you can select the CD as the boot device.

You need to select 'try Ubuntu' option and play around with that for a number of hours.

See if the machine still freezes.

Kind regards

---

### Post by JrMolten on 2012-03-16
Now, ubuntu does not allow me to Sign in.

Tried both username and password all ways I could think off.

100% sure im tiping right.

Is there defaul pass or what?

Thanks

---

### Post by matt_symes on 2012-03-17
Hi

> **JrMolten said:**
> Now, ubuntu does not allow me to Sign in.

Tried both username and password all ways I could think off.

100% sure im tiping right.

Is there defaul pass or what?

Thanks

There is no default password. That would be a huge security risk. What is happening when you try to log in ?

I assume it froze and you hit the power button ? That can cause Ubuntu to get into a right mess (just like Windows).

When it freezes, have you tried the magic key combination ?

Press and hold ALT + SysRq and hit each of these keys on after another leaving five seconds between each key press.

```
r e i s u o
```

I suspect this will not work though as i think the problem is a hardware problem when it freezes.

Kind regards

---

### Post by JrMolten on 2012-03-17
Hey Guys!

First, wanna say i couldn't find "SysRq" key. Cant find it. Do U mean that Function key, used to ajust laptop options? (Fn Key)
Sorry...

Second, I managed to log in ubuntu. Just rebooted and it worked.
Awesome. Dont seems to freze. LOL. I tryed really hard. Like before it froze on youtube. Now got 3 vidz on. Lotza lag, no freeze. Yey!

But...
Its not ok, actually. Cant update system, download stuff and may need to keep changing monitor setup EVERY TIME after login, cuz default is  too small ( 60% of the screen ). Also, will need to use a pendrive for all the stuff i do in that laptop. 

Help! Is there a way to install ubuntu the way it is now, but using my HD and stuff? Like clicking the install ubuntu link? (did not do that being afraid it will freeze like it did before)

Thanks!

---

### Post by dave2001 on 2012-03-17
SysRec key is usually the same as "print screen" on a lot of laptops.

This is my first suggestion when people with an old laptop experience freeze-ups:

*Clean that sucker!*

Get some tiny #1 and #0 screwdriver and take the keyboard and front cover off. Get a can of compressed air and blow everything out. Try and get to the CPU fan and GPU fan and blow them out as well. Hold the fans still with a wire or pencil to keep them from spinning while you do this (or you can break the little bearings). 

You'd be surprised how much dust can accumulate in a laptop in just a year or two.

All that dust can keep the GPU especially from cooling down properly.

---

### Post by dragonfly41 on 2012-03-18
SysRq on my (old) Dell laptop requires Fn + F11 .. not Print Scrn

see this thread .. post #9

[http://ubuntuforums.org/showthread.php?t=1942219](http://ubuntuforums.org/showthread.php?t=1942219)

---

### Post by JrMolten on 2012-03-18
Hello!

I managed to install Ubuntu while in try ubuntu option. After install, ubuntu froze on th update, just the same way it did before. Then I tested magic screen comb. Did not work. Screen did move at wall, laptop didn't restart, nothing. rebooted and put try ubuntu again, where nothing freezes the laptop.

Problem is, the way it is now, does not froze, but is extremely laggy, and I cannot save anything without a pen drive. With is frustrating. I s there a way to start with the try ubuntu on boot by default? Andto use all my laptop disk space while in that setup? 

Thanks!

---

### Post by matt_symes on 2012-03-18
Hi

> **JrMolten said:**
> Then I tested magic screen comb. Did not work. Screen did move at wall, laptop didn't restart, nothing. rebooted and put try ubuntu again, where nothing freezes the laptop.


If the magic key combination did not work (and you are confident you typed it correctly; i normally suggest trying it when the computer is not frozen just to make sure) and there was no kernel panic then i would be pretty confident it was a hardware issue.

Maybe something on the motherboard has gone.

It maybe worth opening it up and putting some more thermal paste between the heatsink and the top of the CPU/GPU. This has fixed freezing on more than one laptop i have looked at in the past.

If not it may be a trip to the repair shop.

Kind regards

---

### Post by JrMolten on 2012-03-18
Tryed the magic combination before freeze. It rebooted PC. Right?

So, i think i found something very interesting!

I got to use the laptop at my uncle house ( wich has no internet ) for like an hour non stop...

No freeze, and I was using install, not live CD. When i came home, connected to net and started using mozilla, it froze, in like 1 minute.

Heh, ope that helps!

Im thining on paying for pros to fix it, but im only goin to do that on last resort. Really. That kind of thing, for a laptop like this, is not cheap stuff.

Thanks for all the support guys!

---

### Post by matt_symes on 2012-03-18
Hi

> **JrMolten said:**
> Tryed the magic combination before freeze. It rebooted PC. Right?

Try the magic key combination when it freezes. 

Also when it freezes, is the CAPS lock LED blinking ? If it is then this is a kernel panic and the magic key combination may not work.

If it is not flashing and the magic key combination does not work then, as i said, i would suspect hardware.

> 
So, i think i found something very interesting!

I got to use the laptop at my uncle house ( wich has no internet ) for like an hour non stop...

No freeze, and I was using install, not live CD. When i came home, connected to net and started using mozilla, it froze, in like 1 minute.

Heh, ope that helps!

Im thining on paying for pros to fix it, but im only goin to do that on last resort. Really. That kind of thing, for a laptop like this, is not cheap stuff.

Thanks for all the support guys!

It good to hear it did not freeze,  but that may be due to how you used the computer.

This laptop has frozen under both XP and Ubuntu. This is why i still think it may be hardware.

Kind regards

---

### Post by dragonfly41 on 2012-03-18
If you experience a freeze with firefox or mozilla running try launching firefox in safe mode to see if it still freezes .. run this command with firefox not running

firefox -safe-mode

My past freezes have usually been firefox / flash related.

---

### Post by JrMolten on 2012-03-18
Yeah. Must be hardware.
Freeze, nothing works. No blinkin on capslock, no magic keys.
Installed Xubuntu to se if it worked.
Didn't. Froze on sistem update. And on anything else Web-Related.
Damn!
Oh, and i tryed the safe firefox mode. Many times. DUN WORK! =((((
So, as it freezes on Win XP, ubuntu 10.04 AND Xubuntu 10.04, it is freaking hardware. Very sad.

But..Didt froze on live CD.

Is there a way to make live CD persistant/permanent, saving stuff and .. yeah?

Thanks for all the support!

---

### Post by matt_symes on 2012-03-18
Hi

> Didn't. Froze on sistem update. And on anything else Web-Related.

Are you connecting via wired or wireless connection or both ?

Were you connected to the Internet when you were around you uncles house ? Were you connected using the same method you use at home ?

Kind regards

---

### Post by JrMolten on 2012-03-23
In my uncles house, iwas not using internet. At all. No internet.

Im my own house, i use only wireless, not cable. When oi try cable net, it freezez thhe same way.

Sorry i took long time to reply, busy at school.

Thanks!

---

### Post by matt_symes on 2012-03-24
Hi

Unload the wireless driver and have a play at home for a good number of hours. The longer you can leave it on the better, even though you will have no wireless internet access.

```
sudo modprobe -r <name_of_driver>
```

Use this

```
lspci -nnk | grep -iA3 wireless
```

or this

```
sudo lshw -c network | grep -i wireless | grep -i driver
```

to get the driver.

Does it still freeze ?

Also use it at home without connecting to the Internet, with the driver loaded.

Kind regards

---

