---
title: "Toshiba A300 Fanspeed"
date: 2010-02-19
forum: General Help
---

### Post by EliBei on 2010-02-19
Hi,

I have a problem with my Ubuntu 9.10 installed within Windows vista. When I boot into Unbutnu, after a while the fan speeds up like crazy as the computer heats up. In addition, all this causes battery life to be quite short. 
I am using a Toshiba A300 series laptop and I find that this a big issue for me. If I want to switch to Ubuntu completely I cannot accept to my battery lasts only 1 hour or so. Under vista fan speed and battery life are better for some reason. 

So is there any tweaking that needs to be done in order to get fanspeed to normal, and to avoid the heating thing?

Thanks in advance.

---

### Post by golanbatrac on 2010-02-19
If you're running ubuntu from within windows, you're running two operating systems simultaneously whenever you boot into ubuntu.  The solution is to install vista and ubuntu side by side, so that you're only running one OS at a time.

---

### Post by EliBei on 2010-02-19
Thanks for your reply,

But as I understood, Ubuntu is installed within windows, but when upon reboot, you choose to use either windows or ubuntu. So when I select and boot into Ubuntu, vista is put to sleep, no? 
In addition, many people are reporting fan speed problems even in Ubuntu only systems, so that's why I posted this thread.

Any thoughts on the subject?

Take care.

---

### Post by arvevans on 2010-02-19
Sounds like a conflict between Windows software trying to control fan speed and Linux software trying to control fan speed.  As "golanbatrac" suggested, try running them individually, instead of in parallel.

Toshiba laptops are a bit different in that some use OS software to augment and control the fan hardware.  If you search for "toshiba" in Package Manager you will find specific software for Linux OS interfaces with the ACPI firmware in your laptop BIOS.

---

### Post by EliBei on 2010-02-20
Hi,

So when I boot into Ubuntu am I running the two OS in parallel??

---

### Post by golanbatrac on 2010-02-20
> But as I understood, Ubuntu is installed within windows, but when upon reboot, you choose to use either windows or ubuntu. So when I select and boot into Ubuntu, vista is put to sleep, no?

I thought you meant that you were running Ubuntu virtually from Windows.  You installed via Wubi?  If that's the case, then you're only running one OS at a time.  Sorry for the confusion.

How long has it been since you defragged your hard drive?  Wubi installations don't like highly fragmented hard drives, and if it's really giving the hard drive a workout, that could account for the heat, the fan, and the short battery life.

---

### Post by gordintoronto on 2010-02-20
If you open Accessories/terminal and paste in this command:

cat /sys/devices/system/cpu/cpu0/cpufreq/scaling_available_frequencies 

it will tell you what speeds Ubuntu thinks your CPU can be set to.  Cpufreq normally does this dynamically, so most of the time it will be at the slowest and coolest speed, but if you do some computations (watch a flash video, for example) it will run the CPU faster and hotter.

This command will display what speed is being used right now:

cat /sys/devices/system/cpu/cpu0/cpufreq/scaling_cur_freq

---

### Post by EliBei on 2010-02-20
Hi,

I think the problem has been solved. I went to the package manager and downloaded the ACPI for toshiba (gues that's the name) as it was recommended. Now the pc runs as smooth as can be and I don't have to increase music volume to hide the fan noise...hehehe. 

Yeah, I installed via the Wubi. I am kind of forcing other family members to try out Ubuntu, they are appreciating the speed at which it runs and access the internet (I don't know why, but page browsing is faster on Ubuntu, I guess it's because of security software that on vista it's slower).

---

### Post by gordintoronto on 2010-02-21
Do you know the exact name of the file in Synaptic?  Where did you find the recommendation?

BTW, Firefox is always much faster than Internet Explorer.  There are even faster browsers, but I like Firefox and have a couple of very useful extensions installed.

---

### Post by EliBei on 2010-02-21
Hi,

Well in the synaptic package manager I searched for toshiba and there was something called ACPI so I installed it, it's less than one mb I guess. 

As for Firefox, I have been using it since a long time on Windows and it has been my choice for web browser ever since (although I like Opera too, but have never developed a taste for chrome), having said that, it still renders faster on Ubuntu than on vista. That's a good thing, a plus for Ubuntu in my opinion. In addition, I have noticed that other cross-platform software such as OpenOffice and Gimp open way faster in Ubuntu than in Vista (or even XP for that matter, as I have them on XP too, in a different pc).

So good  thing for Ubuntu. This OS should be more popular in my opinion.

---

### Post by gordintoronto on 2010-02-21
When I search for Toshiba, I find: acpi-support and acpitool.  I also see toshset, toshutils and fnfxd.

If I knew which one of these solved your problem, I could help other Toshiba users.

---

### Post by EliBei on 2010-02-22
Hi

I used fnfxd. However, I may have spoken too soon, as now the problem has started all over again. The thing is I open several processes at the same time, fine, I do this on a regular basis in windows. I guess most of us do it too. In windows, when I see that my cpu is running on the high end, I close some processes and the cpu and the fan calm down. I tried doing this...in Ubuntu, even closing everything won't lower the fanspeed. This is strange and annoying.

Concerning the terminal...please, it's like a different language, I entered the commands cat /sys/devices/system/cpu/cpu0/cpufreq/scaling_cur_freq and I all I got is a series of numbers which I don't know what to do with.

---

### Post by gordintoronto on 2010-02-22
> **EliBei said:**
> I used fnfxd. However, I may have spoken too soon, as now the problem has started all over again.

Concerning the terminal...please, it's like a different language, I entered the commands cat /sys/devices/system/cpu/cpu0/cpufreq/scaling_cur_freq and I all I got is a series of numbers which I don't know what to do with.

Sorry to hear you're still having trouble.

"cat" lists the contents of a file.  Those words inside slashes are folder names.  "scaling_cur_freq" should be a single number, the current speed of your CPU.  What CPU does your computer have?  Administration/Sysinfo will tell you if you're not sure.  Some CPUs only run at top speed. Mine (AMD Phenom II X2) hops up to 3.1 GHz if it's busy, but normally runs at .8 GHz.

---

### Post by EliBei on 2010-02-27
Hi gordintoronto

Thank you for your concern, greatly appreciated.

The fan is getting more normal these days. I think, if open many processes at the same time and especially if I try to access the vista folder ( C drive), Ubuntu gets overloaded and triggers the fan. Well that's what I think.
However, I had a bigger last time with Ubuntu, and if it keeps on happening I will remove it altogether from my pc. I was browsing the net, using firefox, while messing around with Gimp, and all of a sudden, the computer froze, I cannot move the mouth...I cannot do anything at all. I had to power down and restart. However, to my surprise the same thing happened again two times. I thought this might be a firefox issue, however, I don't know. I installed Opera, hoping I will avoid such a problem. 

best regards

---

### Post by gordintoronto on 2010-02-27
Good luck in getting rid of that bad behaviour.

---

### Post by EliBei on 2010-02-28
Yeah,

I guess I need luck since I haven't managed to solve it yet. The fan speed is erratic, sometimes it is normal, while other time it goes really fast. I have just given up.

---

### Post by lomo2002 on 2010-04-02
hi,

I have the same problem, the fan is running constantly and the laptop heats up, that is why, i have somehow dropped using Ubuntu. Although i have been using ubuntu for several years.

Another problem is, if you install the graphic cards drive (Ati 34xx), then ubuntu does not boot up, so i think this may also be part of the heat up problem, because when you running ubuntu without the graphic drive. this may cause some incompatiblity problem.

---

### Post by davesmith on 2010-04-02
Toshiba laptops are notorious for having overheating issues. This is often a hardware problem associated with the main CPU heatsink  radiator vanes getting clogged with dust.
 
The cooling fans suck air in at the bottom of the casing and blow it  over the heatsink vanes from the inside. Unless you keep the bottom of  the laptop casing on a hard surface or run your m/c in a cleanroom this  will deposit dust and crapite on them and eventually clog them up. 
 
Tosh hard-wire a temperature sensor in the CPU, this changes the fan  speed incrementally and cools it down acording to the CPU temperature as  set by the BIOS. Until the h/s vanes are so clogged it won't cool  properly that is, then the fans go into overdrive and/or the m/c will  suddenly shut itself down to prevent damage.
 
Here is a simple solution. Turn the m/c off completely and turn it  upside down. Get a can of air and a vacuum cleaner. Put the vacuum  cleaner nozzle up against the fan covers and switch the suction on. This  will get the fans running in reverse, then blow air using the can's  thin tube through the rear casing slots over the heatsink vanes. With a  bit of luck the accumulated dust will detach and get sucked out. Be  carefull not to contact the vanes with the thin tube.
 
If the dust is well and truly caked on, more drastic means are called  for. This procedure will invalidate your guarantee, be carefull....!
 
With the m/c switched off, unscrew the base plate cover over the CPU and  expose the heatsink etc from the inside. Very carefully blow air over  the dust mat and dislodge it, gently use a fine paintbrush if necessary.  Suck the dust out. Then replace the cover. Boot up, and hope for the  best!

---

### Post by EliBei on 2010-04-05
Hi, 

Thank you for your advice.

I should remind you that I use Ubuntu along with Vista. Most of my work is done using vista and fan speed is not a problem under vista. Anyhow, I have noticed lately that fan speed is normal under Ubuntu, even after hours of use. So I think a certain update or something might have resolved the issue. I guess so, I don't have a clear explanation.

Best regards.

---

