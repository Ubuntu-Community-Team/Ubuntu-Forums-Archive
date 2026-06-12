---
title: "Disapointed in UBUNTU 10.4"
date: 2010-09-09
forum: General Help
---

### Post by Ziton on 2010-09-09
Ubuntu 10.4 was my first successful endeavor into Linux. I like it fine and am learning a lot.
Can't figure out why it crashes randomly and I have to restart, losing my work.
For the most part it works perfectly in all respects except for the crashes.
I can't get a lead on it.
Anyone know when a fix will be available?
Thanks
Ziton

---

### Post by sikander3786 on 2010-09-09
First of all install all the available updates from Update Manager. That helps most of the times.

Secondly enlighten us a little more about the crash problem. When do most likely you get it? Does it hang up? What applications are you running at the time this happens?

---

### Post by Rubi1200 on 2010-09-09
Can you please provide us with more information?

When does it crash?

Is it only certain applications?

How much RAM do you have installed and what graphics card are you using?

The more you tell us, the better chance we have of telling you how to fix it.

Thanks.

---

### Post by endotherm on 2010-09-09
information about what crashed (and why) may appear in your log files, particularly your system, kern, and messages logs. you can view them by going to System -> Administration  -> Log File Viewer

---

### Post by germanix on 2010-09-09
Sorry to hear about your problems with 10.4.  I have been running Ubuntu as sole operating system on my Sony laptop since Ubuntu 8.04. I installed all of the versions after that and am now also using 10.04 since it came out. I have never ever had a crash on any of the Ubuntu versions I have tried. The only problem I ever had that I could not fix was I could not get internet connection with Ubuntu 9.04 for some reason, but when 9.10 came out it connected out of the box. I guess what I am trying to tell you is that it may not be Ubuntu that needs fixing, and the problem may and probably do lie somewhere else. Could be you are duel booting or your graphics card is causing problems or some other hardware problem exists. If you require help to solve this problem you would need to give more information as to exactly when and under which circumstances your system fails, and info on your hardware etc. I am sure many here on this forum will be glad to help once they know the specifics of your problem.
Do not give up. Ubuntu is great.
Have a nice day

---

### Post by bodhi.zazen on 2010-09-09
One common problem of random crashing is overheating. Make sure your fans are working and the vents are clean. You might want to open the box and clean it.

---

### Post by Ziton on 2010-09-09
> **sikander3786 said:**
> First of all install all the available updates from Update Manager. That helps most of the times.

Secondly enlighten us a little more about the crash problem. When do most likely you get it? Does it hang up? What applications are you running at the time this happens?

 The crash is completely random with no association. Sometimes the system will run for hours. Sometimunes minutes. The crash is always the same first vertical lines across the top half of the screen. Then there is a flash of code in a terminal like seting "black and white". The code flashes for only a second and no time to note. The code has no pattern Its scattered across the screen. Then the screen goes blank and nothing responds but the kill switch. I have a simple Pentium celeron 2.4, 750 megs ram, onboard video.I've updated the computer. The case is open the tower is clean.

---

### Post by hrickh on 2010-09-09
> **Ziton said:**
> The crash is completely random with no association. Sometimes the system will run for hours. Sometimunes minutes. The crash is always the same first vertical lines across the top half of the screen. Then there is a flash of code in a terminal like seting "black and white". The code flashes for only a second and no time to note. The code has no pattern Its scattered across the screen. Then the screen goes blank and nothing responds but the kill switch. I have a simple Pentium celeron 2.4, 750 megs ram, onboard video.I've updated the computer. The case is open the tower is clean.
Run Log File Viewer (it's under Preferences... Administration) and look in a couple of the log files. kern.log, messages, and syslog are good places to start.

Look for anything out of the ordinary. segfault or core are good search words.

That might give you some idea of what's going on.

R.
==

---

### Post by zuerston on 2010-09-09
I went back to 9.10 myself ,10.4 was buggy for me also.Maybe its better now since its been out a while but 9.10 has no problems for me.

---

### Post by Rubi1200 on 2010-09-10
What onboard graphics do you have?

Next time, go to the terminal (Applications > Accessories) and post the output of this please:```
 lspci | grep VGA
```

---

### Post by mastablasta on 2010-09-10
Also check your motherboard for any leaking or bulging capacitors such as these:
 
[http://www.google.com/images?hl=en&expIds=25657,25901,26446,26515&sugexp=ldymls&xhr=t&q=bulging+capacitors&cp=18&wrapid=tljp128410863849610&um=1&ie=UTF-8&source=univ&ei=YPGJTK6XBMHDswbO7bCMAg&sa=X&oi=image_result_group&ct=title&resnum=4&sqi=2&ved=0CDAQsAQwAw&biw=1259&bih=823](http://www.google.com/images?hl=en&expIds=25657,25901,26446,26515&sugexp=ldymls&xhr=t&q=bulging+capacitors&cp=18&wrapid=tljp128410863849610&um=1&ie=UTF-8&source=univ&ei=YPGJTK6XBMHDswbO7bCMAg&sa=X&oi=image_result_group&ct=title&resnum=4&sqi=2&ved=0CDAQsAQwAw&biw=1259&bih=823)

---

### Post by davrosuk on 2010-09-10
The *first* thing to check with random crashes is memory. It is the #1 reason for an OS to fail. There are plenty of tools available to do a proper test. 

[http://oca.microsoft.com/en/windiag.asp]("http://oca.microsoft.com/en/windiag.asp")

Despite where it comes from and the name, this is an excellent tool for diagnosing memory related issues. (It doesn't require Windows, it is bootable CD that just tests memory)

---

### Post by Rubi1200 on 2010-09-10
> **davrosuk said:**
> The *first* thing to check with random crashes is memory. It is the #1 reason for an OS to fail. There are plenty of tools available to do a proper test. 

[http://oca.microsoft.com/en/windiag.asp](http://oca.microsoft.com/en/windiag.asp)

Despite where it comes from and the name, this is an excellent tool for diagnosing memory related issues. (It doesn't require Windows, it is bootable CD that just tests memory)
Why not just use memtest that comes with Ubuntu? It is available either via the GRUB menu or on the LiveCD as a menu option.

---

### Post by davrosuk on 2010-09-10
> **Rubi1200 said:**
> Why not just use memtest that comes with Ubuntu? It is available either via the GRUB menu or on the LiveCD as a menu option.

or you could do that - good point, well presented :-)

---

### Post by B_rebel on 2010-09-10
You didnt mention what type of fall occurred. There are several causes of fallen system. if it is grub does nt found you may open ubuntu with failure desktop option (boot selection option-- ubuntu or **failure desktop of ubuntu** or memory test or Microsoft.... ) there will be an option to open ubuntu safely with low graphics mode, before select that option you may recovery greb from the option list.

you may test your VGA card & try it with low graphics.

---

### Post by Vigh on 2010-09-10
Sounds like a hardware problem. You build the computer yourself? Could be a problem with the memory frequency clock not being set to communicate the CPU FSB properly. I had similar problems, turned out it was hardware problems. I temporarily fixed by manually changing the memory frequency so that CPU FSB and memory were 1:1 ratio. Then eventually put memory that was properly supported by the motherboard in.

---

### Post by TwelveGauge on 2010-09-10
> **Ziton said:**
> The crash is completely random with no association. Sometimes the system will run for hours. Sometimunes minutes. The crash is always the same first vertical lines across the top half of the screen. Then there is a flash of code in a terminal like seting "black and white". The code flashes for only a second and no time to note. The code has no pattern Its scattered across the screen. Then the screen goes blank and nothing responds but the kill switch. I have a simple Pentium celeron 2.4, 750 megs ram, onboard video.I've updated the computer. The case is open the tower is clean.

750 megs is NOT a lot of ram and because of that I think it's unlikely that this is graphics or install related. Chances are you're overloading what RAM you have available. If you set everything to the most basic settings and run only one workspace you might see an improvement. However i think it's unlikely that you'll see a huge improvement unless you get more ram :( additionally, you could try going back to one of the older versions like Ibex or Gutsy and see what happens.

---

### Post by searchfgold6789 on 2010-09-10
I'll try to sum this up for the poster:
You want to check these in the following order

[LIST=1]
[*]Did you install all the updates? If not, it is a very good idea to go into applications > system > Syanptic Package Manager and Mark All Upgrades, Apply. If you did not install the updates I wouldn't be surprised that your system is crashing :)
[*]Is your memory good? Try a memtest. Select it from the Grub2 menu. If many errors occur, your RAM is probably bad. Do not worry, though: RAM is cheap and easily replaceable nowadays.
[*]Try reinstalling ubuntu. With only 750 megs of RAM, you might consider [Xubuntu]("http://www.xubuntu.com/") as an alternative to Ubuntu. It may be some trouble to go through the downloads and the cd-burning, but in the long run it may save you some trouble.
[*]Check the system logs and post here for people to check out.
[/LIST]

---

### Post by sydbat on 2010-09-10
To the OP - all good suggestions so far. However, I have another question that has not been asked yet...

How did you install Ubuntu? Is it a dual boot with Windows XP, and Ubuntu is in it's own partition? 

Did you use wubi (Ubuntu installed as a 'program' inside Windows)?

Did you install Ubuntu as the only Operating System on your computer?

While a hardware problem might be what is making your computer crash, or not having all updates installed, if it is a wubi install, there might be a problem with file system corruption in Windows which can compromise your Ubuntu installation. Wubi is not for long term use, but as an easy way to test a near-fully functioning Linux install.

---

### Post by Topsiho on 2010-09-10
I agree this sounds like a hardware related problem, not one of Ubuntu. Even the best OS doesn't work on crappy hardware.

It may be several things, easiest to investigate is memory and hard disk (see (I (re)translate from Dutch): System>Management>Disktool ).

What I do not agree with is that 750 MB is too little memory. It is quite sufficient. Formally you need more than 256 MB of memory, and while upgrading from one version of Ubuntu to the next you need far more, say 512 MB.

I run Ubuntu on several computers with 512 (and I used to with only 384) MB, without any problem.

I experience sometimes a crash, very rarely indeed, and suspect it is with Firefox, as it everytime is this program, and NOT Ubuntu.

Ubuntu doesn't crash, which doesn't mean that all applications are 100%.

Hope this helps :)

Topsiho

---

### Post by bobstro on 2010-09-10
> **bodhi.zazen said:**
> One common problem of random crashing is overheating. Make sure your fans are working and the vents are clean. You might want to open the box and clean it.Don't forget the fans on things like chipsets and the video card. I once noticed my CPU fan was completely clogged with dust, even thought the fan was spinning away.

Have you run diagnostics on the hardware? A memory test would be a good place to start. A hardware problem could certainly explain those symptoms.

Good luck with it!

- Bob

---

