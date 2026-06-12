---
title: "Karmic and ATi Radeon 4890"
date: 2009-10-29
forum: General Help
---

### Post by Tonelero on 2009-10-29
Ok, I`ve searched the forum before and couldnt find anything that could help me with this.

I have a Atlhon x2 4200, 2Gb of RAM and a Powercolor ATI RadeonHD 4890. Since Karmic alphas it is impossible to install the catalyst drivers, as all the atempts results in a Black Screen and, therefore, the PC totally freezes. I try to change inits, bu no luck, the keyboard doesnt respond to anything. The only solution is to reboot in safe mode, drop to root shell and remove all fglrx crap, delete xorg.conf and then reboot again to have the PC back and running. Open source drivers do work, but with no 3D.

I`ve tried both Restricted Drivers from the Ubuntu menu, as to download and install 9.8, 9.9 and 9.10 catalyst drivers from ATI website.

Is someone having the same problem with this card? Only Ubuntu is giving me headaches.

Thanx in advance... ;)

---

### Post by stevenmansour on 2009-10-30
I cannot install the 9.10 drivers from ATI's website either (Radeon 3650). The install actually goes through but there is no hardware acceleration enabled after reboot, and attemping to run glxgears results in a hard crash.

---

### Post by lakerssuperman on 2009-10-30
I am also having trouble installing the fglrx drivers.  I tried both the repo version and the one from Ati's website.  The install seems to go fine.  I reboot and have graphics, however, compositing isn't running and I cannot enable it.  When trying to load the Ati console I get an error telling me that the driver either isn't installed or is not fucntioning.  I am running a Radeon 4870 which was working fine on 9.04 with the latest drivers.

---

### Post by BarisBlaq on 2009-10-30
I know this is no help, but I got 4650 on my laptop and the restricted ATI drivers are working fine for me so far, compiz and all.

---

### Post by rbmorse on 2009-10-30
In the past I have been able to get the FGLRX driver going by installing them and then opening a terminal and running:

sudo aticonfig --initial

and then rebooting the system (or restarting X)

I don't know if that still works.

---

### Post by Tonelero on 2009-10-30
> **rbmorse said:**
> In the past I have been able to get the FGLRX driver going by installing them and then opening a terminal and running:

sudo aticonfig --initial

and then rebooting the system (or restarting X)

I don't know if that still works.

Tried that already. Unfortunely, it was a no go.  I`ve also tried sudo ati config --initial -f, same thing happen. I wonder if this problems is happening with olny the 4890, cause other users at least are getting the desktop. Weird stuff.

---

### Post by GSF on 2009-10-30
> **Tonelero said:**
> 
I`ve tried both Restricted Drivers from the Ubuntu menu, as to download and install 9.8, 9.9 and 9.10 catalyst drivers from ATI website.


hm.. do you mean if you install the restricted drivers it freezes with a black screen? i have an ati HD 4890 and i've installed restricted drivers without any problem since beta... or u mean it freezes after you enable something in catalyst??

---

### Post by lakerssuperman on 2009-10-30
I got mine working.  I completely removed the driver from the repos and purged out everything fglrx related.  I then installed the 9.10 driver from the Ati website.  Once that was installed in ran 'ati-config --initial -f'.  Upon reboot I have full 3d acceleration and composite effects working.

---

### Post by Tonelero on 2009-10-30
> **GSF said:**
> hm.. do you mean if you install the restricted drivers it freezes with a black screen? i have an ati HD 4890 and i've installed restricted drivers without any problem since beta... or u mean it freezes after you enable something in catalyst??

Yes, it freezes right after the Reboot. I can see the nice White Ubuntu Logo, then the screen goes black and nothing wokrs. This hapens with the restricted drivers and the one from ATi website.

> **lakerssuperman said:**
> I got mine working.  I completely removed the driver from the repos and purged out everything fglrx related.  I then installed the 9.10 driver from the Ati website.  Once that was installed in ran 'ati-config --initial -f'.  Upon reboot I have full 3d acceleration and composite effects working.

I installed the driver from the website, everything goes fine, then I run the comand you mentioned ('ati-config --initial -f') and reboot the PC. After that, Black screen and no more desktop.

This is odd, as I'm only having problems with the 4890. I also a machine with a x800 and i works very good.

Do you guys tweaked the xorg.conf?

---

### Post by GSF on 2009-10-30
> **Tonelero said:**
> Yes, it freezes right after the Reboot. I can see the nice White Ubuntu Logo, then the screen goes black and nothing wokrs. This hapens with the restricted drivers and the one from ATi website.



I installed the driver from the website, everything goes fine, then I run the comand you mentioned ('ati-config --initial -f') and reboot the PC. After that, Black screen and no more desktop.

This is odd, as I'm only having problems with the 4890. I also a machine with a x800 and i works very good.

Do you guys tweaked the xorg.conf?

no, it worked right out of the box for me... thats why ur post seemed strange to me :/ 
does the card work fine on windows? then its 100% driver problem.. else maybe there's a defect on the card that triggers when 3d is enabled.. its a bit common on modern cards :(

edit: or maybe it has something to do with the monitor..??

---

### Post by QIII on 2009-10-30
1.  Check for sure that your card is supported with the latest driver, 9.10.  If so, move forward.  If not, you will have to use the open-source drivers and live with 2D.

2.  Remove and purge the fglx drivers you have installed.

3.  Use **Synaptic** to install Catalyst.  ATI made Catalyst 9.10 available to Canonical specifically for Karmic.

---

### Post by Tonelero on 2009-10-30
The card works perfect in Windows. Used it in XP, Vista and 7, like a charm. Now the odd is that, in Jaunty, with the default restricted driver, it works, but with a watermark of AMD saying the card is not supported. With the 9.7 also works and removes the watermark, but performance is terrible. With the other driver, in both Jaunty and Karmic, it fails to boot. I just tried to purge fglrx and reinstall, but no luck.

---

### Post by QIII on 2009-10-30
According to ATI/AMD, Catalyst 9.10 supports the HD 48xx series.

---

### Post by Tonelero on 2009-10-31
> **QIII said:**
> According to ATI/AMD, Catalyst 9.10 supports the HD 48xx series.

Yes, it does. Thats why I'm so upset. It is suposed to work. I just dont know what is happening.

---

### Post by robobot on 2009-11-02
Do you have all the dependencies for the driver met?

You need to have the following packages installed to build the kernel module:
build-essential, cdbs, fakeroot, dh-make, debhelper, debconf, dkms, libstdc++6

---

### Post by Xorp21 on 2009-11-02
Does anyone else have tearing with animations and video playback?

---

### Post by Tonelero on 2009-11-02
> **robobot said:**
> Do you have all the dependencies for the driver met?

You need to have the following packages installed to build the kernel module:
build-essential, cdbs, fakeroot, dh-make, debhelper, debconf, dkms, libstdc++6

Yes, I have. In fact, the driver installs without any error messages, everything goes just fine. Then I run aticonfig command and reboot. After the white ubuntu logo screen the PC hangs in a black screen. Really annoying.

---

### Post by Zizzech on 2009-11-07
> **Xorp21 said:**
> Does anyone else have tearing with animations and video playback?
I have the same problem

Ubuntu 9.10 x32
ATI 4850
FGLRX Drivers, 9.10

---

### Post by Vitorreus on 2009-11-10
I'v just updated to ubuntu 9.10 and I'm having exactly the same problem. I haven't tried to do anything yet, and I'm not helping to solve the problem, but just letting Tonelero know he isn't the only one having this issue.

---

### Post by darkksyde on 2009-11-10
Have you tried going to System > Administration > Hardware Drivers and installing FGLRX from there

---

### Post by Tonelero on 2009-11-19
> **darkksyde said:**
> Have you tried going to System > Administration > Hardware Drivers and installing FGLRX from there

Yes I have. Every way. Also tried the new 9.11 Catalyst driver. Same issue.

---

### Post by Zizzech on 2009-11-20
I've also tried the 9.11 drivers, still choppy :/

---

### Post by khelben1979 on 2009-11-20
According to [this review]("http://www.phoronix.com/scan.php?page=article&item=amd_radeon_hd4890&num=3") from Phoronix, it worked for them using Catalyst 9.4.

Maybe it's worth a try going for an older driver?

---

### Post by Tonelero on 2009-11-25
> **khelben1979 said:**
> According to [this review]("http://www.phoronix.com/scan.php?page=article&item=amd_radeon_hd4890&num=3") from Phoronix, it worked for them using Catalyst 9.4.

Maybe it's worth a try going for an older driver?

I`ve tried that as you mentioned. The 9.4 and 9.5 drivers used to work, the first with a watermark saying 'Hardware not supported', but they were good to go in Jaunty. However, in Karmik, things got nasty as well. With these drivers, I got to hear the Ubuntu login sound, but with a black screen and some artifacts. Also, the mouse cursor was an orange square. I think I'm gonna wait until the final kernel 2.6.32 is out and AMD releases a compatible driver with it. And if that doesn't work, then I'm going green for sure!

---

### Post by khelben1979 on 2009-11-25
> **Tonelero said:**
> I`ve tried that as you mentioned. The 9.4 and 9.5 drivers used to work, the first with a watermark saying 'Hardware not supported', but they were good to go in Jaunty. However, in Karmik, things got nasty as well. With these drivers, I got to hear the Ubuntu login sound, but with a black screen and some artifacts. Also, the mouse cursor was an orange square. I think I'm gonna wait until the final kernel 2.6.32 is out and AMD releases a compatible driver with it. And if that doesn't work, then I'm going green for sure!

Skipping Karmic and staying with Jaunty might be a good alternative if Jaunty works better.

---

### Post by bghost4 on 2009-12-18
Anyone Tried the New 9.12 driver?

---

### Post by cybaix on 2009-12-30
I just tried the 9.12 driver and it hasn't fixed anything :(

---

### Post by QIII on 2009-12-30
Just to add some joy...

The Catalyst 9.10 works just fine for me in Karmic.  I had some trouble with Flash to begin with, but that was resolved with the 64 bit version (which everyone else seems to complain about).

Lucid, however, has been a different story.

Every attempt to install Catalyst, either from the website or through the repos, has resulted in failure.  However, I am able to drop to the command line and remove it so I can get to Gnome on the next reboot.

A bit frustrating, since the best I can get on my three monitor system is a mirrored view on all three.

Hope this is resolved by April...

---

### Post by Tonelero on 2010-01-10
I couldn't get the 9.12 to work either. In Lucid, the only thing that works is the opensource driver, that gives me enough 3D to run compiz. I've installed kernel 2.6.32 in Karmic and somehow managed to get the same opensource driver to give compiz enabled.

I suggest people whos having problems with fglrx to ditch and try to put the radeonhd to good use. The chances are way bigger than the proprietary drivers!

The only problem is the noise your vga will cause, since the driver do not control the fan. :)

---

