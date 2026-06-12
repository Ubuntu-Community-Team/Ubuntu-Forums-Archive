---
title: "Enabling CPU Frequency for 9.10"
date: 2010-02-20
forum: General Help
---

### Post by robster66 on 2010-02-20
I have a n2pap-lite motherboard with a AMD Sempron 2800+.  My host clock is at 133mhz when it needs to at least be at 166mhz to be a AMD Sempron 2800+...  I installed the system on 100mhz clock not thinking that it mattered.  I have searched and searched for an answer.

I tried the following

sudo apt-get install rcconf
sudo rcconf
*Disabled "ondemand"
It says on guides that it will ask me to reboot but it doesn't, so I manually did it and put the CPU Frequency Monitor on my taskbar.  
It does not have the options like it shows in the screenshots to set my CPU frequency..  I have tried a lot of things and can not figure it out.  I don't want to reinstall at the moment so any help would be appreciated...

Thanks

---

### Post by robster66 on 2010-02-20
CPU Multiplier = 12.5
FSB should be at 166mhz to equal the 2ghz speed that it is but like I said I installed it at 100mhz because I didn't think this would be a problem

---

### Post by spiky001 on 2010-02-20
just a thought can is it not done in the bios?

---

### Post by robster66 on 2010-02-20
To change the frequency yes but Linux won't boot up if I do that without doing this as right now it is programmed as a bottleneck that I can't figure out :(

---

### Post by robster66 on 2010-02-20
Bump

---

### Post by robster66 on 2010-02-22
Does anyone know?  Will it definitely work if I reinstall?  What if I want to OC after am I going to have to reinstall every time??

---

### Post by mcduck on 2010-02-22
That processor doesn't support frequency scaling, so you *really* have to just set the correct speed in BIOS.

If you have problems booting after setting the correct FSB in BIOS then you have some hardware problem. Overheating, faulty RAM or CPU, or some motherboard problem. Try setting the correct FSB and then running the memtest from the Grub menu.

Linux definitely doesn't care what speed your CPU was running at the time when you installed.

---

### Post by robster66 on 2010-02-22
It boots fine into Windows, this is the stock speed of the processor.  It will only boot in Linux if the FSB of the CPU is at 133/266Mhz.  My computer is meant to run 166/333Mhz but it will not boot into Linux.  These are the options that I have set in my BIOS..  This is the error I get when booting with 166/333 setting.


I don't feel like typing all of it so im going to post a couple of the last lines
```

check_bugs+0xbb/0xe9
start_kernel+0x2dc/0x2ec
? unknown_bootoption+0x0/0x1ab
i386_start_kernel+0x7c/0x83

```

---

### Post by mcduck on 2010-02-22
> **robster66 said:**
> It boots fine into Windows, this is the stock speed of the processor.  It will only boot in Linux if the FSB of the CPU is at 133/266Mhz.  My computer is meant to run 166/333Mhz but it will not boot into Linux.  These are the options that I have set in my BIOS..  This is the error I get when booting with 166/333 setting.


I don't feel like typing all of it so im going to post a couple of the last lines
```

check_bugs+0xbb/0xe9
start_kernel+0x2dc/0x2ec
? unknown_bootoption+0x0/0x1ab
i386_start_kernel+0x7c/0x83

```

Windows is rather sloppy when it comes to running on hardware that is operating incorrectly (it runs, but causes faulty calculation results and corrupted data over time), while Linux tends to halt on the first error.

So it doesn't mean anything if you are able to boot into Windows. Like I said, Linux doesn't care if your CPU frequency is different from what you used when you installed. And Linux can't change the frequency with that CPU model because the CPU doesn't support frequency scaling.

I actually had almost exactly the same CPU (I had Athlon XP 2800+, the same CPU but twice the cache you have), overclocked to 2300MHz running on Ubuntu, so I do know what I'm talking about. ;)

---

### Post by robster66 on 2010-02-22
I never said you didn't know what your talking about but I am telling you what I see and the problem that Im faced with.  A couple years ago I have had debian, fc, gentoo, ubuntu run on these specs.  Why would it give me this error when I change my FSB in the BIOS back to it's stock 166/333mhz setting??  My BIOS only recognizes my processor as a AMD Sempron 2800+ if the setting is 166/333

---

### Post by mcduck on 2010-02-22
> **robster66 said:**
> I never said you didn't know what your talking about but I am telling you what I see and the problem that Im faced with.  A couple years ago I have had debian, fc, gentoo, ubuntu run on these specs.  Why would it give me this error when I change my FSB in the BIOS back to it's stock 166/333mhz setting??  My BIOS only recognizes my processor as a AMD Sempron 2800+ if the setting is 166/333

because your hardware has developed some problem since then?

It really can't be any Linux setting that would require you to reinstall with different FSB since *there is no setting that would store such information or care if you change the FSB*. This really must be a problem in your hardware or your BIOS settings. And if you are able to boot to Windows then it doesn't sound like you'd need to change any FSB divider setting in BIOS to keep your other hardware running with 166MHz FSB either, so that would only leave CPU, RAM and the motherboard itself.

I still think you should set the FSB to 166 and then run the memtest overnight to see if you get any memory errors. And of course check that the CPU cooler is properly attached and clean to rule out any overheating problems.

(If you still don't believe that there is no setting that cares about the CPU speed in Linux, then set the FSB even lower, to 100MHz, to test that. If there is such setting somewhere in Linux then surely your system will fail to boot at even lower CPU speed..)

---

### Post by robster66 on 2010-02-22
Temperature is not a problem at all.  As my system runs at load around 43C with stock settings and even lower with 133/266.  I tried booting it back at 133/266 and now it won't mount filesystem.  Last time I did this it worked, it doesn't make much sense to me =/.  Im going to try a couple different things and post how I make out

fsck fixes the mount problem after I reverted back to 133/266 wtf?

---

### Post by mcduck on 2010-02-22
43°C sure is reasonable for that CPU so I agree that temperature isn't causing the problems.

---

### Post by robster66 on 2010-02-22
I tried running ubuntu from disk with 166/333mhz settings and it won't load it hangs with _ blinking

---

### Post by robster66 on 2010-02-25
So know one can figure it out?  I have a Nforce2 and it wont even install at my stock FSB settings..  If I make it 133/266mhz it boots

---

### Post by Markak34 on 2010-03-03
Hmm have you considered the RAM.. I had an MSI motherboard (which was nforce 2 chipset) a few years back with an xp2500 athlon oc to xp3200 @ 400mhz fsb but I couldn't change any RAM timings or anything similiar due to cheap ram, it just used to freeze on POST. The RAM was 400mhz so I could use it at those speeds.
I'm not sure if I'm correct here but does Ubuntu use a different RAM queue system or anything like that? Would it push the use of RAM up.. i.e. more heat?

Anyway hope it helps.

---

### Post by mcduck on 2010-03-05
> **Markak34 said:**
> Hmm have you considered the RAM.. I had an MSI motherboard (which was nforce 2 chipset) a few years back with an xp2500 athlon oc to xp3200 @ 400mhz fsb but I couldn't change any RAM timings or anything similiar due to cheap ram, it just used to freeze on POST. The RAM was 400mhz so I could use it at those speeds.
I'm not sure if I'm correct here but does Ubuntu use a different RAM queue system or anything like that? Would it push the use of RAM up.. i.e. more heat?

Anyway hope it helps.

yep, that's why I've been suggesting running the memtest.

Linux doesn't use RAM in any way that would stress it more, but it tries to use all available RAM (unlike old windows version), so it might hit a broken RAM address while Windows would never use it. And like I also said, Linux tends to halt on such errors while Windows ignores them and keeps on running even though that means that all the processed data might end corrupted.

Nforce2 was famous for being picky with the RAM modules it worked with.

---

### Post by FiveSidedPoly on 2010-03-05
Everyone here has given you great advice, but if you're still stuck I'll add my two cents, take it if you want.
 
You should probably take a gander at the rest of your bios settings as well, possibly set them to factory defaults.
 
- Turn it off, unplug the powercord, wait five seconds.  Push and hold the power button for five seconds.  Plug back in.
 
- Did you check for BIOS updates that are relevant?
 
- Try disabling CnQ and CSS.
 
- Set the basics to "Auto"  (unless your MB runs either high or low in voltage or clocks)
 
-  Check to see if ECC and its additional settings aren't "Enabled" if you have non-ECC memory.
 
- Check both AMD and your MB companies websites to get official specs and to find out others are having this issue.
 
- Check to make sure your ram is on the QML and QVL for your MB and CPU.
 
- Run MemTest (like others have said) also you might want to download the latest one rather then the one on the Live CD, I've seen it have issues with some newer ram.

---

