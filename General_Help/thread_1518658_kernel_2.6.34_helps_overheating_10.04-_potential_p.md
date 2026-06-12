---
title: "kernel 2.6.34 helps overheating 10.04- potential problems?"
date: 2010-06-26
forum: General Help
---

### Post by cloyd on 2010-06-26
I've been trying to get lucid to work on my gateway netbook. The major problem I've seen is that it would overheat (to about 63 C or a little higher, and then the display would go crazy and crash.  I've looked and looked, and nothing seemed to help. My BIOS doesn't support cpu scaling. Somewhere in a google search, someone mentioned the 2.6.34 kernel. I had no ideal what I was doing, and I installed this kernel. (could not install headers -- a dependency issue I didn't understand)  Tried it, and it booted. Saw some errors, like timer or something not found and something about a soft reset.  However, it boots, and it works, and the temperature is much better (at least for the last 42 minutes: I've not been able to run it that long before)

Are those errors likely to cause problems? Are there any issues I should be aware of using a non-standard kernel like this?

I am dual booting with 9.10, which works well, and all my serious work is on the 9.10 partitions.

                                 HID compliant mouse
 Synaptics PS/2 Port touchPad
 Generic PnP Monitor
 Atheros AR5B95 Wireless Network Adapter
 Reltek PCIe FE Family Controller
 AMD Athlon(tm) Processor L110
 Realtgek High Definition Audio
 Microsoft iSCISI Initator
 

 Gateway LT3103u
 

 

                          As I write, temp is still at 56, but I am getting some intermittent display problems.
Any ideas, or should I give up on lucid?

---

### Post by cloyd on 2010-06-27
*bump*

This kernel seems to control temperature. Internet works well. But after 30-40 minutes, display starts to go crazy. Cursor changes to square box appox. 1/2 in sq. with horizontal lines. Bands of horizontal lines may appear on screen, and may go away. If I stay logged in, screen deteriorates to to the point I can't read shut down menu or tell where cursor is located on menu.  What could cause this?

As info, I tried going back to the old karmic kernel, but wifi does poorly on it.

---

### Post by cloyd on 2010-06-28
*bump*

I've searched and searched . . . I may find something, but haven't found it yet. I tried installing maverick kernal (6.35 . . . ) but could not because of dependency error.  I now have more kernels on 10.04 which is not my main system than on 9.10.

It took me quite a while to get 9.10 to run well. My biggest problem was wireless . . . lost signal soon after booting. Installed lucid backports, and lucid wireless backports (technicaly not the exact names, but I hope you get the idea).  9.10 works well after that. Thought about installing those backports in lin lucid, but the option in synaptic is not available (also tried with apt-get install in terminal--didn't work). Is such a thing possible? I do have the 6.31 rt kernel . . . could this work?   

I know, I ask too may questions on one post. But I'm trying to figure it out. Thanks for any help.

---

### Post by cloyd on 2010-06-30
Here is how it stands:
2.6.31 kernel ran cooler, but wifi did not work well.
2.6.34 kernel ran cooler and wifi worked well, but would only run 5 to 50 minutes until video went crazy with horozontal lines.  Got to just searching Lucid issues, and read about plymouth and thought my problem may be there (not because I understood plymouth, but because I understood it involved startup screen;  crashing problem went away with 2.6.31 kernel, and so did splash screen). Tried the solutions on this thread:
[COLOR=#000080]_[http://news.softpedia.com/news/How-to-Fix-the-Big-and-Ugly-Plymouth-Logo-in-Ubuntu-10-04-140810.shtml](http://news.softpedia.com/news/How-to-Fix-the-Big-and-Ugly-Plymouth-Logo-in-Ubuntu-10-04-140810.shtml)_[/COLOR]
 
There were two solutions on this page. The second was simpler, so I tried it first. It didn't work. I tried the first. It took longer, and video was starting to act up before I got it done, but managed to finish (also think that having multiple applications open aggravated video issue; video would go crazy, and I'd see if I could close an application and it helped.)  The first seems to have worked, but I've been using lucid for about an hour and a half, opening all the applications I can, and playing videos, and it is still working right.

If this works, I am going to get rid of a few worthless kernels (but not all of them, but especially 2.6.31 and 2.6.35)  When I can use it for a day with no issues, I'll marked the thread solved.

Sometimes I think I learn more when no one helps me, but I'd like the help anyway. However, sometimes, I think I haven't asked the question properly. I hope what I learned here can help someone else

---

### Post by davidmohammed on 2010-06-30
hi there,
  what graphics card have you got?

type in a terminal

lspci | grep VGA

---

### Post by Yellow Pasque on 2010-06-30
Edit: Nvm

---

### Post by cloyd on 2010-06-30
grep | VGA returns an error, but


lspci | grep VGA
returns:

01:05.0 VGA compatible controller: ATI Technologies Inc RS690M [Radeon X1200 Series]


It seems to be working. I had seen some suggestions to install another graphics driver, but was having trouble getting to the site that had the driver lastnight, then, when I got on the site,  realized that they seemed to be for particular kernels, and there were none for any kernel past 2.6.32.  So, I kept trying until I found the link posted above.

---

### Post by RJARRRPCGP on 2010-06-30
> **cloyd said:**
> I've been trying to get lucid to work on my gateway netbook. The major problem I've seen is that it would overheat (to about 63 C or a little higher, and then the display would go crazy and crash.  

63 C is nothing to worry about, unless it's already 63 C when just sitting at the desktop.

---

### Post by Yellow Pasque on 2010-06-30
You should upgrade to lucid and run a 2.6.35 kernel (because it still sounds like you're overheating). The significant power savings come with the undervolting support in 2.6.35: [http://www.phoronix.com/scan.php?page=news_item&px=ODIyOA](http://www.phoronix.com/scan.php?page=news_item&px=ODIyOA)

---

### Post by cloyd on 2010-06-30
> **RJARRRPCGP said:**
> 63 C is nothing to worry about, unless it's already 63 C when just sitting at the desktop.

Yes, I know 63 is not supposed to be that hot. Then, I ran this:
 sensors

and got this:

acpitz-virtual-0
Adapter: Virtual device
temp1:       +53.0°C  (crit = +100.0°C)                  

k8temp-pci-00c3
Adapter: PCI adapter
Core0 Temp:  +47.0°C                                    
Core1 Temp:  -49.0°C                                    

acerhdf-virtual-0
Adapter: Virtual device
temp1:       +53.0°C  (crit = +63.0°C)   

Now, that very last line . . . what does it mean? Is it the hard drive temp? I don't know.

Common sense, and every thing I've read say not to worry unless it gets to 85, 90 or so. But . . . it was also crashing.

But, it does seem to be fixed.

Temujin, thanks for the suggestion.  I am running Lucid, and I tried 2.6.35 (also tried 33) One wouldn't install, and one had wifi problems, but really, I'm not sure which now.

---

### Post by gradinaruvasile on 2010-06-30
Temperature readings on AMD processors might be wrong. And older AMDs have the reputation of going hot in laptops under all OSes. But it seems Lucid has some extra issues in the kernel (Debian on the other hand seems to work as before with the .32).

Watch out for the display issues, those mean that certain components have overheated and it may damage your hardware permanently - i have seen it happen on a Dell D630.

Install the proprietary Ati drivers (if you havent already) in order to enable video card power saving - this should further decrease the temperature.

---

### Post by Yellow Pasque on 2010-06-30
Please try to install the .35 kernel and post the output error (if any).

---

### Post by cloyd on 2010-07-01
> **gradinaruvasile said:**
> Temperature readings on AMD processors might be wrong. And older AMDs have the reputation of going hot in laptops under all OSes. But it seems Lucid has some extra issues in the kernel (Debian on the other hand seems to work as before with the .32).

Watch out for the display issues, those mean that certain components have overheated and it may damage your hardware permanently - i have seen it happen on a Dell D630.

Install the proprietary Ati drivers (if you havent already) in order to enable video card power saving - this should further decrease the temperature.

I'm  a little leery of trying any more because the system seems to be working now. No splash screen, but so what?  However, if there is a possibility of damaging my system, I'd like to avoid that.  My problem is, I don't know where to get proprietary drivers. I've been to an AMD support site, and didn't understand what I saw there. Will synaptic help me here?  What am I looking for?

---

### Post by davidmohammed on 2010-07-01
synaptic will not help here.

ATI graphics in lucid is not very good and causes overheating issues.  Hopefully these will be resolved by the time maverick appears.

I would strongly recommend you install the ATI proprietary drivers from [here]("http://support.amd.com/us/gpudownload/Pages/index.aspx").

Instructions from [here]("http://www.hotsquid.org/2010/05/updating-to-ati-10-4-onlucid/")

on the ATI website link 

step 1 - choose desktop graphics
step 2 - choose radeon x series
step 3 - choose radeon x1xxx series
step 4 - choose linux x86

---

### Post by Yellow Pasque on 2010-07-01
> **cloyd said:**
> I'm  a little leery of trying any more because the system seems to be working now. No splash screen, but so what?  However, if there is a possibility of damaging my system, I'd like to avoid that.  My problem is, I don't know where to get proprietary drivers. I've been to an AMD support site, and didn't understand what I saw there. Will synaptic help me here?  What am I looking for?
Your card is unsupported by proprietary drivers (except on old distros like Ubuntu Hardy or Debian Lenny).

---

### Post by cloyd on 2010-07-01
Ok. I have the downloaded package, but I can't run it. result is :
sh: Can't open ./ati-driver-installer-10-4-x86.x86_64.run

also, to remove old driver as per the the instructions to uninstall current driver in the pdf on the site, I currently have no folder called usr/share/ati

Will installing this prevent damage to my system? Or just work better. (again, no video issues when on for up to 3 hours; no video issues since I worked on boot instructions. Sensors report decent temps, though I don't understand the line that showed 63 as critical in sensors output) I am about to the point to where if it is bad for the system, I'm almost ready to keep using 9.10. 

But it would be nice to keep the LTS distribution.

Edit: Figured out what the last line as critical at 63: that is the temperature at which  acerhdf switched the fan on. I also learned that it cut it off at 58. Fanon and fanoff both are now set at 5 degrees lower. It may cost me on battery, but I usually operate on power anyway.

---

### Post by Yellow Pasque on 2010-07-01
> Ok. I have the downloaded package, but I can't run it. result is :
sh: Can't open ./ati-driver-installer-10-4-x86.x86_64.run

You would need to chmod +x the file, but your card is not supported anyway... (so delete that file and stop trying to install proprietary drivers for an X1200/690M on Lucid!)

---

### Post by cloyd on 2010-07-02
Well, I don't know if I can install the ATI driver or not. The site instructions read like this driver would support my card, but I'm not brave enough to try it any farther. What if I uninstall current drivers, and cannot get new ones to work? I'm chicken right now. But so far I have:
1. Found a kernel which does not overheat  and wifi works (2.6.34).
2. Stopped video issues by getting rid of splash screen.
3. Found out how to change fan settings to get fan working at lower temp to get a head start on cooling. (with acerhdf).

I think I am considering my problem solved.  I haven't yet decided to get rid of 9.10, but 10.04 is getting more workable.

---

