---
title: "firefox overheats the machine and shuts down the system"
date: 2010-01-21
forum: General Help
---

### Post by dhariwal on 2010-01-21
Hi,

This is the first time I am posting on Ubuntu forum, i hope this is the right place.

I have done a clean install of Ubuntu 9.10 (from the CD), single OS on the machine, it seems to be working perfectly alright (better than windows 7 which was previously installed).

Only one problem I am facing right now is when I open lot of firefox tabs, I can hear that the processor or fan starts making a lot of noise and eventually system shuts down abruptly, i can feel that the machine heats up. Than I have to wait for few minutes to let it cool and than start again. If i use firefox with (lets say) 2-3 tabs open, it works ok. but when i open over 4-5 tabs, it goes mad.

Any help in this regard will be much appreciated.

Thanks in advance.

---

### Post by bodhi.zazen on 2010-01-21
Most of the time this is a hardware problem. Firefox is not typically a CPU intense application, you can check you CPU use ith top or other monitoring app, you should see activity when you open firefox, then it should taper off.

Shut your box down, disconnect the power supply, open the case, and clean it out.

---

### Post by lovinglinux on 2010-01-21
> **bodhi.zazen said:**
> Most of the time this is a hardware problem. Firefox is not typically a CPU intense application, you can check you CPU use ith top or other monitoring app, you should see activity when you open firefox, then it should taper off.

Unless, the OP is opening a site with some crazy javascript. Then it can actually raise the CPU usage to 100%. 

Does it happen with any web site?

Take a look at [Firefox optimization and troubleshooting thread](http://ubuntuforums.org/showthread.php?t=1193567) for several types of Firefox optimization.

---

### Post by jamesisin on 2010-01-21
As another test you can install Opera and see how it behaves:

[http://www.soundunreason.com/InkWell/?p=197](http://www.soundunreason.com/InkWell/?p=197)

---

### Post by anselm on 2010-01-21
Are you running any flash sites? when I do my fans go to full speed to cool down the machine. This happens in firefox and chrome.

---

### Post by hwttdz on 2010-01-21
Ok this sounds like two problems
1) firefox is being too resource intensive
2) your box is overheating entirely too easily - you should be able to run at 100% cpu indefinitely without overheating, can you take a look at sensors (you may need to first install lm_sensors and run sensors-detect), this will hopefully allow you to monitor the temperature of your cpu.  If it's getting too hot (somewhere between 60 and 100 C depending on cpu type), you're going to need to fix that, either by resetting the heatsink, cleaning dust out of it, replacing a fan... There are lots of possibilities to improve the situation.

Firefox acting up is less worrying.

Also to stress test the cpu you can run burnBX (and one instance per core), if it overheats that's bad.

---

### Post by dhariwal on 2010-01-22
First of all, thanks for the response - really appreciated.

I did further tests and found that it might be to do with the websites - coz i opened 8-10 tabs of a forum and it didnt misbehave, it could be to do with the sites with flash, or javascript (i am not sure) - may be i should try again with different sites and see.

cleaning the box, i think it is also needed but same websites worked fine with windows or when i was running ubuntu from within the windows (when i ran ubuntu from within the windows i installed 9.04 and than upgraded to 9.10)

i will do all the tests mentioned and also will take the notebook to hp centre to clean it up.

Many thanks
Khalid Masood

---

### Post by Saiko Berry on 2010-01-22
Sounds like your fan sucks. Pun intended. Is it in backwards? lol

---

### Post by SiliconS on 2010-01-22
I'm about to buy an Acer Nettop on which I'll install Ubuntu and one of the things I've discovered during my research is that existing versions of Flash Player use the CPU for graphics rather than the GPU, so if you're opening Flash-heavy websites like YouTube or similar then it's the CPU that'll do all the work. Traditionally this hasn't been a problem but with more popular sites now using HD video the burden on the CPU is becoming noticeable.

Disregarding the fact that your PC shouldn't ever get hot enough to shut down abruptly, you might find that if all else fails, trying the new Flash Player 10.1 Beta helps to offload the graphics processing burden from the CPU onto the GPU where it'll be much more efficiently handled.

Something else to consider is that you may be in the same position as me with my HP/Compaq laptop, which has an ATI graphics processor. I'm a noob and I haven't yet found a way to get good drivers working for it, which means it's running in a less efficient 'basic' way. The fan is generally louder and the battery life is about 60% of what I get with the proper drivers under Windows. This makes any heavy-duty processing much more stressful on the hardware.

I know these are vague ideas but I'm a noob and that's the best I can do. :)

---

### Post by dhariwal on 2010-01-22
its a HP tx2550ee .... graphics card is ATI radeon, i installed the graphics driver ATI/AMD FGLRX driver ... graphics seems to be ok, i will check which flash version is installed... perhaps changing flash version can fix the problem...
and i dont think the fan is in backwards :)

but 4-5 years ago i had compaq evo N610C, which use to shut down in a similar fashion under windows OS, fan running like jumbo jet engine and overheating and shutting down ..

i think i should take it for cleaning anyway, probably dust factor also

---

### Post by dhariwal on 2010-01-22
by the way, is there a notebook which comes pre-configured with ubuntu ... i read somewhere that ibm machines are shipped with ubuntu pre-configued, but nothing on their website... should i open a new thread for this question?

---

### Post by Saiko Berry on 2010-01-22
No. It's cake to install though. Run a liveCD and click install. Select largest partition format done.

---

### Post by 00_Spykes on 2010-01-22
Another tip is to check your BIOS settings for your CPU and fan as well as power control. I had some problems with my Athlon x64 (not laptop) when the powernow K8-driver was disabled in the BIOS and/or operating system.

I would check the kernel config too and see what the ACPI options and power control driver for your CPU if I were you. One dirty quick-fix I did was to set the CPU frequency governor to powersave until I had figured out what the problem was (it was powernow-K8 driver disabled in BIOS). 

If I remember correctly (read at Gentoo forums I think) AMD Athlon x64 (and maybe others) shut itself down immediately if they got overheated, whereas Intel processors managed it by reducing its performance. Don't take this for the truth, it's just something I've heard or read somewhere.

Good luck!

---

### Post by Speshio on 2010-01-22
Yes, I've had a similar problem with Firefox on both Win XP and Mepis on this HP zv5340us (amd64). At times I've had easily 10 tabs open without issue, but at odd intervals, the machine gets all hyper and goes full bore with hairdryer-like blasts of hot air from the rear exhaust vent, and responsiveness plummets to near-zip. 

To improve ventilation, I shimmed up the rear of the machine. Easier to type that way too. Nevertheless, several of these episodes have elicited reboots, shutdowns, serious error reports from Windows. On other occasions, I've had to use a hard shut-down, because the machine would not do so gracefully. 

To my recollection, these problems started last summer, and were more severe under Mepis than Win XP in that with Win, if I could manage to shut down all my aps, including firefox, then after a bit, the system might calm down. I use Mob meter to see cpu and hd temps, and cpu revs. But in Mepis, once the the cpu spun up to max, there was no going back, so I simply restarted, and usually Mepis would let me do that.

I replaced the m/b after 2.5 years when the onboard graphics died. Onboard graphics acting up again now, and I believe I've seen some discussion about my particular m/b being susceptible to graphics subsystem failures because of overheating, and this machine has always run hot. Usable as a laptop only in a cool room in winter.

I agree with the poster who implicted the Flash player in causing some machines to go hysterical.

FWIW

---

### Post by 00_Spykes on 2010-01-22
An application like Firefox with Flash should never have that kind of control over an operating system, and it's very rare that they do, well, in the *nix universe at least. ;)

But please, disregard everything and every experience you have from Windows, it's of no use here. Unless of course it happens in both Linux and Windows, but even then, take it with a grain of salt. If it happens in all you operating systems, it's likely a hardware or BIOS error/misconfiguration. It should be pretty obvious but, eh, I'm just trying to help.

---

### Post by jamesisin on 2010-01-22
> **dhariwal said:**
> is there a notebook which comes pre-configured with ubuntu ... i read somewhere that ibm machines are shipped with ubuntu pre-configued

Dell is offering Ubuntu machines:

[http://www.dell.com/content/topics/segtopic.aspx/ubuntu?c=us&cs=19&l=en&s=dhs&~ck=anavml](http://www.dell.com/content/topics/segtopic.aspx/ubuntu?c=us&cs=19&l=en&s=dhs&~ck=anavml)

Others are as well.  Just need to look around.

---

### Post by bodhi.zazen on 2010-01-22
> **dhariwal said:**
> by the way, is there a notebook which comes pre-configured with ubuntu ... i read somewhere that ibm machines are shipped with ubuntu pre-configued, but nothing on their website... should i open a new thread for this question?

See also - System76  [http://system76.com/](http://system76.com/)

---

### Post by dhariwal on 2010-01-25
You will not believe it, I am sitting with a bloody hair dryer in one hand and working with the other :)

Anyhow the heating problem got worse and processor/fan goes crazy even when I copy big files between external drive and main disk. than i wiped the box and installed ubuntu 8.04, same problem.... so it was not really firefox problem, probably something else .... 
now i re-installed ubuntu 9.10 from cd sent by canonical, so far it seems to be behaving ok, bit too early to draw conclusion .... also took the machine for cleaning up, i hope this problem goes away....

as far as the amd vs intel processor is concerned, i had heating up issues with intel processors also and they used to switch off abruptly .... i think HP must also ship a damn hair dryer or air blower with their notebooks.... coz previous machine which gave me same trouble was also Compaq, this one is HP (essentially same product/company).

---

### Post by hwttdz on 2010-01-25
Like I said, if you wanted to stress test run one instance of burnBX per core. The big problem here was probably that the heatsink was either not well seated, didn't have the right thermal paste or was clogged with dust.

---

