---
title: "Need help NOW! The jerking, haning and freezing has become a nightmare!"
date: 2010-12-30
forum: General Help
---

### Post by colobix on 2010-12-30
Hey guys. So these problems started like yesterday or something?
Nautilus is very jerky, (doesn't answer) and sometimes makes the pc freeze.
I have this problem no matter how many files there are in the folder.
Even on empty folders.
Typing in the ALT+F2 command line hangs a lot, and the system is generally working slower. When I open firefox it takes like 5 - 10 sec before it opens. This is very frustrating.
I don't wanna reinstall because I somehow know this will happen again, so I just wanna fix it now.
I am using ubuntu 10.04. It has always been a bit more jerky than the previous versions of ubuntu but this is just ridiculous. I mean today it's just a nightmare.

---

### Post by germanix on 2010-12-30
I am sorry to heat about your problems, and I can understand your frustration, but demanding help, I quote "Need help NOW" and addressing all as "Hey" will probably not get you the attention you would like.
May I suggest that you edit your post to "Need help PLEASE" and take out the "Hey".
This I am sure will get people to want to help you.

---

### Post by Grenage on 2010-12-30
> **colobix said:**
> Hey. So these problems started like yesterday or something?
Nautilus is very jerky, (doesn't answer) and sometimes makes the pc freeze.
I have this problem no matter how many files there are in the folder.
Even on empty folders.
Typing in the ALT+F2 command line hangs a lot, and the system is generally working slower. When I open firefox it takes like 5 - 10 sec before it opens. This is very frustrating.
I don't wanna reinstall because I somehow know this will happen again, so I just wanna fix it now.
I am using ubuntu 10.04. It has always been a bit more jerky than the previous versions of ubuntu but this is just ridiculous. I mean today it's just a nightmare.

Computer specifications? Memory diagnostic?

---

### Post by colobix on 2010-12-30
> **Grenage said:**
> Computer specifications? Memory diagnostic?
What do you need?

---

### Post by cchhrriiss121212 on 2010-12-30
Try opening System Monitor from the System>Admin menu. The first tab will show your system specs, the second and third tabs will show whether something is maxing out your CPU/RAM resources. Post the relevant info here.

Also you should run a memtest from a live cd. This will check whether your RAM is healthy or not.

---

### Post by colobix on 2010-12-30
Thanks. sysinfo was more specific:

Kernel: 2.6.32-27-generic
CPU Vendor: GenuineIntel
CPUs: 2
-Model Name: Intel(R) Atom(TM) CPU 230 @ 1.60GHz
-Frequency: 1599.938 MHz
-L2 cache: 512kb
Memory total: 3023
-Free : 83%
-Swap Total: 5572 MiB
-Free: 100%
GFX card: Nvidia ION, PCI.
-NVIDIA UNIX x86 Kernel Module 256.52
Available disk space: 89,5gb on my ext4 partition, and my NTFS partition has 75gb of free space.

If you need any more details, please tell me.

---

### Post by Grenage on 2010-12-30
I'm going to put the speed down to that processor, but run a memory check - it can't hurt to test.

I am assuming this is a laptop or HTPC.

---

### Post by colobix on 2010-12-30
Ok thanks. here's what I got from  free -m:
             total       used       free     shared    buffers     cached
Mem:          3023       1941       1082          0        223       1132
-/+ buffers/cache:        585       2438
Swap:         5572          0       5572

I have no idea what these numbers are telling you, but I Hope it's good :D
Also, if you want me to post my hardware info from lshw, just tell me.
But the thing is, that will be a looooong post.

---

### Post by Grenage on 2010-12-30
Do you have, or can you get (download and burn/friend*) an Ubuntu CD?  When booting from the CD, there should be a memcheck option in the menu.  There might be a memcheck in the installed Grub menu - I've never looked.

*either or, don't download an ISO and then burn a friend.

---

### Post by colobix on 2010-12-30
ok here it is:

Memory: 3071 |MHz 2052mb/s
L1 cache: 24 |MHz 6250mb/s
l2 cache: 512 |MHz 3721mb/s
l3 cache: none
Cached: 3071m
RsvdMem: 264k
MemMap: e820
Cache: on
Ecc: Off
Test: std
Pass: 0
Errors: 0
Ecc Errors 0

---

### Post by theasprint on 2010-12-30
Hi,

To all: 

Just wondering if its the graphics card problem?

---

### Post by Grenage on 2010-12-30
> **colobix said:**
> 
Pass: 0
Errors: 0
Ecc Errors 0

Hmm, wouldn't Pass:0 mean that it didn't perform a single full pass?

Anyhow, assuming it did a full scan, no errors have been reported.  I personally suspect the processor, because it's not a very powerful one.  I am sure others will chime in if they think otherwise.

---

### Post by colobix on 2010-12-30
> **Grenage said:**
> Hmm, wouldn't Pass:0 mean that it didn't perform a single full pass?

Anyhow, assuming it did a full scan, no errors have been reported.  I personally suspect the processor, because it's not a very powerful one.  I am sure others will chime in if they think otherwise.

Wait, what? First of, do I have a bad processor?
Also, how can you tell it's not the processor's fault if it's not very powerful?
Well, I have no idea here but I too doubt that the processor got anything to do with this. Why?
1) the nautilus problem started for only 2 days ago.
2) The random laging and freezing problems in Lynx Lucid have been reported a billion times.

---

### Post by Grenage on 2010-12-30
I doubt the processor itself is faulty, the 230 is just a *relatively* slow processor.

If the problem started only recently, then have you installed or reconfigured anything of late?  Does top (command line) or System Monitor (AGUI-Under Admin) show anything CPU intensive during the laggy periods?

I've seen plenty of Nautilus issues in the current build, but none were laggy.  That said, none of them were on Atoms, so the symptoms may be more profound.

---

### Post by msandoy on 2010-12-30
Try turning off visual effects, if the problem persists, it is not a graphics problem. Your computer should manage to run Ubuntu without problems. Also make sure you have the proper nVidia drivers installed.

---

### Post by colobix on 2010-12-30
I have already tried that but no, plus I need compiz for the zoom function.
Also, I have the recommended nVidia driver, yes. I installed the nvidia-common package and deleted the 96 and 175 drivers I already had installed.
This helped a lot, but I did this for a long time ago.

@Grenage, can I somehow tweak the processors speed? the pc have always been a bit slow even when I had windows 7 installed.
The only thing I have installed recently failed, but I fixed it.
It was a package that broke down during the installation so I couldn't open synaptic or install anything. Synaptic told me to reinstall the package but it couldn't find it. So I solved the problem by force install it. Solved the problem like a charm. But I doubt this problem have anything to do with my freezing (sorry, not laggy) Nautilus.
But whats laggy is when I do general things such as typing and scrolling.

---

### Post by misterbiskits on 2010-12-30
> **colobix said:**
> I have already tried that but no, plus I need compiz for the zoom function.
can I somehow tweak the processors speed? the pc have always been a bit slow even when I had windows 7 installed.


You have a slow 1.6ghz processor.  You can overclock it (make it faster) at the risk of burning it out.  Having a slow processor doesn't explain why suddenly things are lagging or slow to respond.
Linux often freezes on me as well.  I often have to hard reboot.  I take it as part of the ubuntu experience.

---

### Post by Grenage on 2010-12-30
> **colobix said:**
> I have already tried that but no, plus I need compiz for the zoom function.
Also, I have the recommended nVidia driver, yes. I installed the nvidia-common package and deleted the 96 and 175 drivers I already had installed.
This helped a lot, but I did this for a long time ago.

@Grenage, can I somehow tweak the processors speed? the pc have always been a bit slow even when I had windows 7 installed.
The only thing I have installed recently failed, but I fixed it.
It was a package that broke down during the installation so I couldn't open synaptic or install anything. Synaptic told me to reinstall the package but it couldn't find it. So I solved the problem by force install it. Solved the problem like a charm. But I doubt this problem have anything to do with my freezing (sorry, not laggy) Nautilus.
But whats laggy is when I do general things such as typing and scrolling.

I am surprised that it lags while typing, but I've seen graphical scroll lag before.  It might be worth turning off compiz as suggested, just to see if it does make much difference?  I wouldn't recommend overclocking, but then I never do. :)

Did Top or System Manager show anything taking much CPU use?

---

### Post by colobix on 2010-12-30
> **Grenage said:**
> I am surprised that it lags while typing, but I've seen graphical scroll lag before.  It might be worth turning off compiz as suggested, just to see if it does make much difference?  I wouldn't recommend overclocking, but then I never do. :)

Did Top or System Manager show anything taking much CPU use?

I tried to turn off compiz, it didn't get rid of the lags but works way better here in firefox. THe ALT+F2 commend is still lagy while I start typing. Nautilus is still messed up.
Top's top 3 processes are Firefox.bin, Xorg and compiz.
When I watch hulu videos or ustream shows, some plugin thing (can't remember the name) takes a lot of CPU.
EDIT: The commend line (alt+f2) is lagy only at the beginning or the word. everything I type after that goes smoothly.

---

### Post by Grenage on 2010-12-31
I am guessing that Hulu uses flash or something (I've never used Hulu); Flash does tend to make the CPU work a fair bit.

As for the lag remaining, I am wondering if it's the HD spinning up after powering down, although I am surprised that a bit of text would prompt the HD to be required immediately.

---

### Post by melander on 2010-12-31
> **Grenage said:**
> I am guessing that Hulu uses flash or something (I've never used Hulu); Flash does tend to make the CPU work a fair bit.

You're correct; Hulu is flash-based. The new Flash 10.2 beta plugin on my ION-based system has made a big difference in usability due to the introduction of hardware acceleration using vdpau.

Thus, once he's got his current difficulties sorted, the OP, who also has an ION-based system, may want to look into the beta.

Regards,

---

### Post by colobix on 2010-12-31
Adobe flash approved a lot. I used the one from synaptic, and hulu works much better now.
Where can I find the beta version?
Also, is it stable, I mean since it's still in beta? or will it crash firefox or something?
Nautilus is still randomly freezing though. I tried to reinstall it but no.
Any suggestions? And are there any error scanners or something that can automatically search the system for errors?

---

### Post by melander on 2010-12-31
The download of the beta can be found [here]("http://labs.adobe.com/technologies/flashplayer10/"). I am unaware of it having been packaged into a .deb. I installed libflashplayer.so in ~/.mozilla/plugins/. 

However, given the gravity of your other problems, introducing non-Ubuntu software at this stage might not be the best idea. Unfortunately, as we're all Xu- and Kubuntu users at our house, I'm afraid Nautilus is beyond our ken.

Regards,

---

### Post by colobix on 2010-12-31
ok so first I uninstall the adobe plugin from synaptic and then I create the plugin folder inside ./mozilla, and move the .so file there ?
Will firefox recognize the .so file now then?

---

### Post by melander on 2010-12-31
I think you just need to create the .mozilla/plugins directory and copy the .so there and it will work for the relevant user. YMMV.

But this is *not* going to solve your core problem with Nautilus or your video driver. A less jerky version of Ke$ha on SNL is cold comfort at a time like this. ;)

Regards,

---

### Post by colobix on 2010-12-31
> **melander said:**
> I think you just need to create the .mozilla/plugins directory and copy the .so there and it will work for the relevant user. YMMV.

But this is *not* going to solve your core problem with Nautilus or your video driver. A less jerky version of Ke$ha on SNL is cold comfort at a time like this. ;)

Regards,
Thanks. No I just needed to test the new adobe flash plugin version.
Is there any nautilus alternatives I can use? maybe if I use something else, that will solve it?

EDIT: And firefox still reads the old .so file, so I solved the problem. moving it to the /usr/lib/adobe-flashplugin/ folder and replacing the old one. The new version works fine so thanks a lot :)

---

### Post by colobix on 2010-12-31
I am starting to think that this is more of a PC problem than a problem with my ubuntu.
Why? Programs refuse to start even in the safe GNOME session.
Since this pc is less than 4 months old, I am not going to by a new one.
So, is there something I can do to test this?
EDIT: Firefox and other programs I can run aren't slow at all.
This is the weirdest problem I've ever discovered.

EDIT 2: Or wait, maybe not, since this happened just a few days ago.

---

### Post by colobix on 2011-01-01
Bump.
Please guys, I really need your help.
Ok so the lagging (typing delay) is not because of Compiz.
Well, some of it is, but I need compiz so I guess I just gonna have to live with it. But the typing delay on the command line (ALT+F2) is not because of compiz, and nor the fact that nautilus is frustratingly freezing in some folders all of the sudden.

So there you have it folks. What can I do to fix this?
Please help me.

---

### Post by msandoy on 2011-01-02
I see earlier in the thread, that you did a memcheck, but it reported Pass:0, indicating it did not finish it's testing. Please start it again, and let it complete the scan, it takes about 15 minutes, but be patient. If you have memory problems, it would explain alot about your problems.

---

### Post by colobix on 2011-01-02
> **msandoy said:**
> I see earlier in the thread, that you did a memcheck, but it reported Pass:0, indicating it did not finish it's testing. Please start it again, and let it complete the scan, it takes about 15 minutes, but be patient. If you have memory problems, it would explain alot about your problems.

You're right. ok so after the test now it says no errors.
So yea, it's not a memory error, which is somehow a good thing.

---

### Post by mziskandar on 2011-01-02
try this.. [http://digitalspine.blogspot.com/2010/11/ubuntu-lucid-1004-freezeslock-ups.html]("http://digitalspine.blogspot.com/2010/11/ubuntu-lucid-1004-freezeslock-ups.html")

---

### Post by colobix on 2011-01-02
> **mziskandar said:**
> try this.. [http://digitalspine.blogspot.com/2010/11/ubuntu-lucid-1004-freezeslock-ups.html]("http://digitalspine.blogspot.com/2010/11/ubuntu-lucid-1004-freezeslock-ups.html")
I think that actually help a little bit for the lagging (can't tell yet), thanks:)
But I still have this very frustrating nautilus problem though.

---

### Post by msandoy on 2011-01-02
Can you remember if you added any cpu hogging feature in compiz around the time you discovered this problem?
If you havent already, install CompizConfig settings manager, and try disabling whatever you do not need. It should give you slightly quicker response and less lag.

---

### Post by mziskandar on 2011-01-02
..and also, try to use elementary theme (minimal), minimize unneeded processes/load after bootup (eg: infrared, bluetooth, etc.) using [ubuntu-tweak.com]("http://www.ubuntu-tweak.com"). Use proprietary driver where possible.

---

### Post by colobix on 2011-01-03
I didn't add anything to xompiz.
The only compiz effects I use is Opacity, zoom and Negative. And yes I have even tried without compiz at all.
Also, I use the normal Ubuntu theme.
I have also went through the history log in synaptic and installed everything I removed in that period, but no luck so I removed them again.

---

### Post by colobix on 2011-01-03
Ok things that I've tried since my last post are:

First I removed the config file and rebuilt it
```
 rm -r $HOME/.config &&  sudo dpkg-reconfigure -a && sudo aptitude -f install && sudo update-grub
```
This would have solved it if the problem was too many errors in the config file, but no.
I ended up with neither nautilus or compiz in the startup. And it messed up my start menu ofcourse. Cuz I have my own little system there where I reorganize things to fit my needs and stuff, so yea. :D
Not a big deal, but no. This didn't solve anything.
Nautilus is still slow as crap, and I can't find anything on the web that works for me. I really don't trust random websites either since I have no idea what I'm doing with this PC. It's all just a blur in my mind JK.
But ok seriously, it would be really great if I could just fix this without having to reinstall the whole thing.

---

### Post by msandoy on 2011-01-03
I have to say that I can't help you there. I have given you all my ideas, so I hope someone else comes by that can assist you. I'm all out of ideas here.

---

### Post by colobix on 2011-01-03
@msandoy well, thank you anyway.


I think I'm getting at the bottom of something here.

FSLint gave me this error:

Traceback (most recent call last):
  File "/usr/bin/fslint-gui", line 27, in <module>
    import gtk
ImportError: No module named gtk

BleachBit gave me a similar error but pygtk instead.

So, I think I have stumbled across the problem here.
There are some missing packages or files somewhere.

How can I see what packages I need?

---

### Post by madurax86 on 2011-01-05
[http://kernel.ubuntu.com/~kernel-ppa/mainline](http://kernel.ubuntu.com/~kernel-ppa/mainline)

download a kernel from here and install it, you can try Natty kernels in Lucid but its not that recommended. BTW, if your hardware is not stable with Lucid, theres no reason for you to be still using it please upgrade to Maverick and try the newest kernel for it. It should work.
Please post all versions of(the files end with .1 ..etc) /var/log/kern.log 

DO not expect Linux to run best on newest technologies, you'll have to wait for the new code commits in the Kernel in order for the new hardware to be supported. The kernel devs add new code to kernel for these kind of support after they get bug reports, this is nothing like the corporate OS manufacturing! If you want to be productive on your new machine either you have to fall back to the OS that the device fully supports or you'd have to wait until the right code is committed. 

What you should have done is to get a notebook that fully supported by Linux.

---

### Post by colobix on 2011-01-06
Thank you guys. I didn't manage to fix this so I had to reinstall the whole thing. Very frustrating but ok. Everything works fine now, and I REALLY hope this never happens to me again.

---

