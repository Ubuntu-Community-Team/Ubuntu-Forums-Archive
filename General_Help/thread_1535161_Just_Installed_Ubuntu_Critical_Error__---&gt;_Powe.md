---
title: "Just Installed Ubuntu: Critical Error  ---&gt; Power Supply Smoking!"
date: 2010-07-20
forum: General Help
---

### Post by RoboticRickJames747 on 2010-07-20
Hello,

    I recently installed Ubuntu on my brand-spanking new desktop (that I built with premium parts), but I noticed something severely wrong with my desktop.  After installing Ubuntu, I noticed that the "overall movement" of everything (such as mouse speed, keyword speed, time between sound, even as well as fan speed and memory) was slow to almost a snail's pace.  Now I have built several computers in the past (43 to be exact), so I know this is definitely not a installation issue, and the service that I bought the parts is from a legit seller, as well. 
    Anyways, after installing Ubuntu, running/installing the drivers required for my desktop, and updating the computer, my desktop then began to shriek and rumble along my desk as if there was a family of squirrels frantically trying to scare off an intruding invader! I immediately turned off the computer, rebooted it, and then ran it in safe mode (to hopefully find the error without the shrieking noise).  Once running, a deep, resonating moaning noise began to be expressed from the backside of the desktop (pinpointed to the fan) where it began to expel a rather pungent odor of burning plastic/melting metal.  If i left it on, the odor would become more prevalent and the moaning would become louder and louder.
     Since the only issue I can really pinpoint is the new OS, hopefully this forum will help me with the issue that has just arisen. Thank you.

---

### Post by anon.jdh on 2010-07-20
From what you describe it sounds like you have a bad power supply. 
No one doubts your machine building cred but I would be slow to blame the operating system if you see smoke.

---

### Post by ajgreeny on 2010-07-20
I don't think Ubuntu could possibly set your system on fire, as appears to almost happen.  It definitely sounds like a faulty PS, probably the transformer in there, and you should take it back immediately.

---

### Post by Mark Phelps on 2010-07-21
There have been reports of PCs overheating after installing Ubuntu 10.04 -- and if the overheating was severe, and you left it on a long time, I could see some damage resulting.

But, since you apparently did not try any other OS, and if this is the FIRST OS you tried on the new machine, it's most likely merely a coincidence that Ubuntu happened to be running on it.

---

### Post by Golem XIV on 2010-07-21
I can think of no way that any OS could burn out the power supply.  It was probably faulty.

The slowdown that you experienced could have been caused by the same condition, either through improper current to the components or through overheating (that would made the CPU slow down to avoid burning)

---

### Post by RoboticRickJames747 on 2010-08-06
After waiting for a new power supply to come in the mail, I finlly recieved a new one. And oddly enough the same issue has risen up again. Any thoughts? I reformatted it and installed XP and it worked fine, but when I put Ubuntu back on it the issue prior began to occur again...

---

### Post by RoboticRickJames747 on 2010-08-06
I apologize for the late reply, but this is a pressing matter because I new to build another computer for someone else. I am frustrated, but patient so I am willing to listen to whatever anyone has to say and will do whatever is asked/suggested. But if this continues to occur, even after all the help I recieve and work I put into it, I will probally not put Ubuntu on any more future computers I build... especially if this OS is known to cause issues like this.
 
And yes, I have read through the support section and through the Q&A's section here (and on different sites), nothing they have put up helped or even really looked into the situation I am having currently.

---

### Post by lukeiamyourfather on 2010-08-06
Linux doesn't cause power supplies to fail. End of story. Or any other operating system for that matter. What power supply is it, have you tried any others?

---

### Post by Shompol on 2010-08-06
Just do what all other PC manufacturers do: pre-install with XP and refuse to support any other OS :)

Seriously, though, if you are running a small shop/serious hobby (43 is far from "several"), you should have quite a few spare computer parts lying around. If you don't, you can always "borrow" them from another computer.

I would take the guts out of the case, and run it. This should help pinpoint the source of noise right away. Then keep swapping components until you find the one that's not compatible. 

Since I only built one PC, you are supposed to be teaching me. 
"I will probally not put Ubuntu on any more future..." I hear that often. I am not afraid. Say hello to the "Antivirus 2000 trojan" and his relatives for me.

---

### Post by RoboticRickJames747 on 2010-08-07
I seem to be sensing some misunderstanding, so I will reliterate for you...
 
I took out the old power supply, stripped the computer I was working on originally, swapped it with other parts (I failed to mention earlier that I rebought all the parts from a different provider), then reassembled the computer. I then installed Windows XP on it, and I then allowed it to run for awhile and no issues arose. I then uninstalled XP and installed Ubuntu to see if it would work just as well as XP did, it didn't... it went back to the original noise that was described in the 1st post.
 
[[COLOR=#000000]CORSAIR CMPSU-750TX[/COLOR]]("http://www.newegg.com/Product/Product.aspx?Item=N82E16817139006") is the power supply... 
 
After posting what I just wrote, do you have any other suggestions or comments to make, luke?
 
Thats what I did Shompol, ironically I dont have spare parts around, people jsut buy the parts, give me money ot buy their parts, or get them elsewhere and then give them to me. I then encorporate them into a PC for them. :/ 
 
> Since I only built one PC, you are supposed to be teaching me. "I will probally not put Ubuntu on any more future..." I hear that often. I am not afraid. Say hello to the "Antivirus 2000 trojan" and his relatives for me. 
 
I don't understand what you mean, sorry.

---

### Post by bodhi.zazen on 2010-08-07
> **lukeiamyourfather said:**
> Linux doesn't cause power supplies to fail. End of story. Or any other operating system for that matter. What power supply is it, have you tried any others?

This ^^

You have some kind of hardware problem, it is not related to Ubuntu.

---

### Post by bergfly on 2010-08-07
Assuming, just for a second, that the OS is to blame (I've seen stranger things) here is what I would do. First, ditch the case, lay out the motherboard, power supply, ram and processor. Don't connect any peripheries other than mouse, keyboard and monitor to onboard VGA if there is one. Now boot from a USB drive into ubuntu. 

If that comes up clean, then try adding an HDD with Ubuntu on it. Again, watch and learn. Are all the fans spinning etc. It is possible that a fan has some weird motherboard windows driver requirement to operate, and missing that driver it won't run. Hence the issues. Personally, I'd ditch the hardware configuration and go for something that doesn't burn on boot.

---

### Post by lukeiamyourfather on 2010-08-07
> **RoboticRickJames747 said:**
> 
After posting what I just wrote, do you have any other suggestions or comments to make, luke?

This kind of issue is difficult to troubleshoot through a forum. If you were down the street I'd say come on over and lets troubleshoot it together component by component until the problem is identified. Unfortunately that's not an option and I don't really know what the problem from here.

No one is saying what you describe is not true, just that Ubuntu is not the direct cause. It might be the catalyst though. For example earlier this year I was connecting to a BlueArc SAN using CIFS protocol (Samba). Older Linux distributions worked fine but newer ones like Ubuntu didn't. Eventually I pinpointed the version of Samba where things stopped working. At first the conclusion was obviously the newer versions of Samba on the client side had a bug. What I later found out is the BlueArc implementation of CIFS was flawed and the problems only showed up when the newer clients called functionality that was broken. So the newer Samba was the catalyst but not the cause of the problem. Once BlueArc released a patch the problem went away.

In your case its possible the firmware on the motherboard or another device is faulty so Ubuntu could potentially ask the hardware to do something that might damage itself or overheat. That doesn't mean Ubuntu is the cause, the faulty firmware would be the cause and Ubuntu would be the catalyst. Know what I mean? Or it could be any number of other things where Ubuntu is the catalyst but not the cause.

Try other components, motherboard, fans, everything. Try them one at a time to see where the issue comes up. I'm pretty sure when you get to the bottom of everything you'll find its a hardware issue even if it only occurs with Ubuntu.

---

### Post by neoargon on 2010-08-07
How did you choose the power supply? . Did you calculate the total amount of power the computer would consume and did you chose the power supply according to it ?


Please try to do something that would consume intense CPU like converting video formats in windows to see if the same problem happen in it too

---

### Post by DrMelon on 2010-08-07
I'm very sure that your choice of OS wouldn't cause your power supply to break. Especially considering the OS has nothing to do with the PSU anyway - it only contacts it through the motherboard. I'd say you have a faulty unit (or it's running on the wrong voltage). Get a spare one and switch it, see if it works.

---

### Post by uberbuntufan64y on 2010-08-09
There was a time when I used a ubutnus laptop that was so hot you could fry eggs on it, but the person told me that it was cooler when it ran Winblows or even other linuxes.

---

### Post by RoboticRickJames747 on 2011-02-02
Hello,
 
I am currently reviving this thread because the computer I was working on (at the time of these posts) recently "flared up", and the owner of this computer has been frantically calling me. She only used the computer (from the time I built it up until a few days ago) for uploading pictures from her camera and printing them out from her scanner/printer.  When I went over to her house, I was shocked to see that the whole back-end of the desktop was charred beyond reconition, and when I opened it up all I could see is the severely burned remains of a the orginal computer innerts.
 
She told me that she only added on the camera software on her computer (which Ubuntu seemed to have no problem installing/running), and that her apartment owner was also an extremely good electrician, so there was no possibility of a surge/electrical overload and/or failure.
 
I reread the previous posts to this thread and it is apparent that Unbuntu has overheated several computers before, but now I am completely upset and bewildered to see that the OS might be the cause of this critical failure again!!
[-X
 
If anyone has any advice or any experience with this situation, I would truely appreciate it all the information you could provide!
 
Thank you for your time.

---

### Post by piquat on 2011-02-02
Just kind of for my own curiosity, what brand and model of Motherboard, CPU, video card and power supply were in the machine?

I love building systems.  It's an interesting problem....

---

### Post by RoboticRickJames747 on 2011-02-08
Hello,
 
Sorry for the late response, I was out-of-state for a couple days due to a family event. I haven't had any time to get the specs for her computer, but I wil get them t oyou as soon as possible.
 
This is disheartening that I only was able to recieve only one reply since I revived this troubling event. I am certian that there are some form of Ubuntu techs/experienced users on this forum that must've come across this situation, and I am hoping that there are some people here that would hopefully be willing to help me.
 
Please help Ubuntu forums, you're my only hope! :sadface:

---

### Post by quadproc on 2011-02-08
> **RoboticRickJames747 said:**
> 
I reread the previous posts to this thread and it is apparent that Unbuntu has overheated several computers before, but now I am completely upset and bewildered to see that the OS might be the cause of this critical failure again!!
It is true that there have been some heating problems associated with a small number of kernel versions - it seems that the task scheduler sometimes would spin the CPU in a loop while waiting for something to do.  However, that problem was quickly diagnosed and the kernel code was fixed.  That problem was a part of the 10.04 release.  Please note the past tense.

However, those heating problems did not cause heating to the point of doing visually apparent damage to components.  Instead, in severe cases, people would find that their computers would shut down without warning.  This is a result of the fact that most computers contain at least one temperature sensor and that something, usually the BIOS, will shut down the system if the sensor detects an overtemperature condition.

Methinks that the problem is some technical weakness in the hardware, and that the software happens to reveal this weakness.  It is also likely that the BIOS is involved in this because the system does not protect itself.

Thousands of people have been running Ubuntu for years and have not reported any incineration problems so it is entirely possible to get satisfactory results from Ubuntu.

I would check into the BIOS first, then the motherboard design.

Edit: upon more consideration, here is another thing to check for: missing ground connections.  Modern desktops have power supplies which can easily push 20 or more amperes through the circuitry, and that current has to return to the power supply.  If the expected return path isn't there then the current will seek another path.  The current could find a place such as the ground on a USB connector, the ground trace on a parallel interface port, or something similar.  That place could be intended to carry only signal currents of a few milliamps.  Pushing a large fraction of the power supply current through such a path could result in that trace overheating and causing damage around that trace.  Once the damage has started then it could cause short circuits to develop in the PC board and that would cause larger areas to become involved.

It is not clear why this problem would occur with some correlation to Ubuntu, but such a problem would explain why the temperature sensor(s) did not detect the problem.

quadproc

---

