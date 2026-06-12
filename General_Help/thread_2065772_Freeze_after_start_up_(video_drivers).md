---
title: "Freeze after start up (video drivers)"
date: 2012-10-02
forum: General Help
---

### Post by cdoublejj on 2012-10-02
So I have been getting freezing after start up just after it gets to the desktop (consistently, same time every time) so i did some trial and error and found that installing with out internet worked, as in no freezes.

So i decided to try adding things one by one till it started locking up again and the first thing i tried was video drivers and low and behold it locks up just after boot like before.

I installed the Nvidia {recommended} drivers, so i'm wonder if there isn't a way to disable them before/during boot So i can try [post release drivers]? 

Is there a way to see what video drives it is installing, like what card it thinks it is detecting?

Specs:
Asus A8n32-SLI Deluxe
4gb DDR 400
200GB WD IDE
BFG GTS250 1GB Vram

Back Story: i've been running Lubuntu in VMplayer for while with far less resources and it has been just awesome so now i finally found a spare hard drive and want to install and run it on real hardware. 8)

EDIT: By freezing i mean total lock up, i believe it's a hard lock but, be sure because it's a KVM switch and the old num lock trick doesn't work.

---

### Post by cdoublejj on 2012-10-02
Managed to disable the drivers and switch to the "post release update" driver and it still locks up after boot.

---

### Post by cdoublejj on 2012-10-03
the first time i was able to switch drivers i must have stumbled onto an invisible boot menu by pressing escape because text showed before the Lubuntu menu.

This time i frantically tapped escape and tired the arrow keys and enter to no avail, i just barley managed to disable the driver but, it locked up halfway through (locking up at ti's normal time a minute or so after booting up) and it still persists to freeze as i think it didn't totaly manage to disable the driver.

I'm at a loss here.

---

### Post by cdoublejj on 2012-10-03
so i did this...

[quote name="tom.slick" url="/t/1312334/lubuntu-freezing-after-auto-log-in-nvidia-drivers#post_18284419"]Press and hold the "shif"t key after bios to bring up your grub menu
Select the default entry (it should already be highlighted)
And press "e"
A new menu will appear.  look for a line that starts 
```
linux /boot/vmlinux
```
At the end of the line you  will see something like
```
quiet splast $vt_handoff
```
Chang quiet splash to text and add the letter "s" to the end 
So that it looks more like
```
text $vt_handoff s
```
Then press "F10" to boot
This will bring you to a command line
Then at the prompt type 
```
sudo apt-get purge nvidia*
```
answer prompts,  then
```
sudo dpkg-reconfigure xserver-xorg
```
answer prompts, and Nvidia should be gone[/quote]

i think it worked how ever it still locks up, is there a way to find out what is causing it to lock up?

---

### Post by cdoublejj on 2012-10-04
Well, i think i'm gonna try reinstalling with out internet again to confirm it is the drivers.

---

### Post by cdoublejj on 2012-10-04
So, i re clean installed double, triple, quadruple confirmed it is the driver. I found this, 

[http://askubuntu.com/questions/154387/my-computer-freezes-when-nvidia-drivers-activated](http://askubuntu.com/questions/154387/my-computer-freezes-when-nvidia-drivers-activated)

However it does not fix this issue, then i found this,

[http://forums.fedoraforum.org/showthread.php?t=279781](http://forums.fedoraforum.org/showthread.php?t=279781)

this guy found out with the drivers his GPU was falling off the bus. I'm not sure whats happening in my case but, unlike that guy I'm getting hard locks.

---

### Post by Bashing-om on 2012-10-04
cdoublejj; 

Looks like you are having more than your share of troubles:

see if this works for you:
Boot to command line video issues:
Remove nvidia drivers -> install nouveau -> reboot and let Ubuntu detect your videocard when you're running the desktop -> install the new drivers -> reboot.
#Remove nvidia
```

sudo apt-get update
sudo apt-get purge nvidia-*
sudo apt-get install nvidia-current

sudo apt-get purge nvidia-common
#Install nouveau and remove the xorg.conf
sudo apt-get install xserver-xorg-video-nouveau
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.backup

``` I found helpful instructions here:
[https://bugs.launchpad.net/ubuntu/+s...rs/+bug/982485](https://bugs.launchpad.net/ubuntu/+s...rs/+bug/982485)
this link may prove helpfull:
[http://ubuntuforums.org/showthread.php?t=2029882](http://ubuntuforums.org/showthread.php?t=2029882)
[INDENT]hth <==BDQ

[/INDENT]

---

### Post by cdoublejj on 2012-10-04
Thanks for the reply. Basically those are instructions for going back to default drivers no?

 I can just as easily clean install. The thing is i have tried 3 or 4 different driver version already, it detects the correct video card.

However the above instructions might make since if wanted to keep the install for reading logs, which i know nothing about.

I'm at the point now where i can bet money and make promises that any driver version i install is gonna cause a lock up after boot/log in.

I could understand if it was/is hardware problem but, it runs and games just fine in windows 7. (totally different hard drive no dual boot)

I'm gonna go ahead and run those commands from recovery mode.

---

### Post by cdoublejj on 2012-10-04
Just ran the commands how ever some of it didn't work take, perhaps those commands are tailoyerd for Ubuntu instead of Lubuntu.

for now i'm gonna leave in the root command shell aka recovery mode till i have more time.

---

### Post by Bashing-om on 2012-10-04
Regret not helping much, know how time-consuming trouble shooting can be !

To see your graphics card and info:
```
sudo lshw -C display
lspci | grep VGA

```and suggest comparing to the compatibility list :
[http://www.ubuntu.com/certification/catalog/](http://www.ubuntu.com/certification/catalog/)

and then there is the official "guide" info irt Nvidia:
 
**  Install Latest Nvidia/ATI drivers **

 Ubuntu uses a GUI frontend to [Jockey]("https://launchpad.net/jockey") for the installation of the proprietary nVidia drivers (and other proprietary drivers). 
 Menu -> System -> Hardware Drivers  
[LIST]
[*]Sometimes after a kernel upgrade a proprietary driver may stop  working. In such a case, try installing the new linux-headers that match  the newly upgraded kernel:
[/LIST]
 sudo apt-get install linux-headers-$(uname -r)  If dkms and build-essential have never been installed on your system, these can also be worthwhile:  sudo apt-get install dkms build-essential 
from: 
[http://ubuntuguide.org/wiki/Ubuntu:Precise#Install_Latest_Nvidia.2FATI_drivers](http://ubuntuguide.org/wiki/Ubuntu:Precise#Install_Latest_Nvidia.2FATI_drivers)
[INDENT]Try'n to help <==BDQ

[/INDENT]

---

### Post by cdoublejj on 2012-10-05
You're helping, and thankyou for it atleast i'm not all by my self trying to figure this out. NOt only did on run the grep command i had also run the [PHP]sudo lspci - v[/PHP] earlier and it does detect the gpu correctly, at least the model and brand.

[PHP]NVIDIA Corporation G92 [Geforce GTS250] (rev a2)[/PHP] and of course my lspci -v command brings up similar info except it mentions it being a BFG card, which it is, i don't know what revision the card is, without removing it and looking or confirming on windows (again no dual boot I have 2 totally different {hard drives}.

I wish i could get some way of knowing what is happening when it locks up. I keep question my self it it is a hardware fault but, it runs in windows just fine it even stress tests and games.

The only drive i haven't downloaded and and installed is 295.49 how ever it is in the repository and i believe the "post updates" tried form the official driver installer was probably actually 295.49 since it shows up in the default repos.

There has to be some fault weather it be the driver or hardware (the GTS250) or somewhere in between causing the locks if.... if i just knew what it was. For all i know it could actually be caused by some error from a bugged dependency program (drive dependency) or weather it's some sort of call or function the driver is trying to run or initiate.

I don't think it's fault of the system, i've tried lowering clocks and that made no  difference and i know it runs windows and programs fine, I believe I have beyond reasonable doubt to believe it's a linux/driver thing. Now yes this hardware is old (2005-2006| 6 some odd years old) and may not 100.00 percent stable and if it was indeed some instruction or code/command that cpu or gfx card couldn't handle properly then yeah it would make since.

However seeing other people have similar problems and reading stuff like the fedora forum link i posted where the guys log showed the the GPU falling of the system bus in the software, i think that fortifies it has very likely possible linux/driver thing. not say it couldn't be some hardware qwerk but, even then if I at least knew it was hardware bug, I  could at least know to give up find another machine to install to or try and fix the broken hardware.

---

### Post by sambukhari on 2012-10-05
i am new

---

### Post by cdoublejj on 2012-10-05
Okay the last time iran commands was the last time someone post commands in the this thread, by that i mean the last command i ran were the Nvidia purge and grep command. 

Purging the drivers works and i know for sure that i can go into recovery mode and purge drivers and continue to use the same installation with out issue (untill i install nvidia drivers again of course).

Mention: lspci does have some interesting notes, some of the "subsytem" line for various device (chipset stuff) such as fire for one example list other asus motherboards under "subsystem" I'm assuming this is normal as it is not uncommon for similar board to use like/same drivers for various things such as usb or fire wire or network controllers. However I figured it was worth mentioning.

Perhaps i should post a lspci report soon.

For now I'm not sure what to go from here, I guess i'll see what tomorrow brings along with other posts/suggestions.

---

### Post by Bashing-om on 2012-10-05
sheeeshhh, OK --I agree most likely graphics driver issue. Sooo..You have tried the open source drivers, the current proprietary drivers.  I have two other alternatives I can think of off the top of my head.
1. install an old(er) version driver (proprietary).
2. install a bleeding edge driver.

I lean toward an older version so here is the method:
Non-working Nvidia driver included on .iso: Solution is to remove any proprietary drivers and then revert to old Nvidia driver.

```

sudo add-apt-repository ppa:ubuntu-x-swat/x-updates
 sudo apt-get update
 sudo apt-get install nvidia-current=295.33-0ubuntu1~precise~xup1

```Reboot and you should be good to go.
This will get you the old proprietary nvidia driver. However, for some nvidia graphic cards even this fails because compiz crashes when trying to start Unity-3D. (However, Unity-2D should work, at least it did in my case.)

WARNING! If you can start Unity-3D without problems DON'T run the following commands if you don't know what you're doing since it can break your 3D graphics acceleration!
A workaround that did help me was to completly remove proprietary drivers and use nouveau instead:
```
sudo apt-get remove --purge nvidia-* 
```You also might have to remove a custom xorg.conf created by the driver or yourself:
```
sudo rm /etc/X11/xorg.conf
```The xorg.conf will be automatically recreated after rebooting if required.

In order to use nvidia-173 or nvidia-96, please see this post here:
[https://bugs.launchpad.net/ubuntu/+s...73/+bug/922268](https://bugs.launchpad.net/ubuntu/+s...73/+bug/922268)

--------------[INDENT]Try these and see what results <==BDQ

[/INDENT]

---

### Post by cdoublejj on 2012-10-05
Was gonna try installing jockey to install drivers but, i see i already have it. at this moment i'm at a stand still.

---

### Post by Bashing-om on 2012-10-05
Yeah, "additional drivers" is but the GUI front end for jockey-gtk. In any event, and no drivers working, might consider dusting your innards out and reseating the driver card.

AS of now I am out of suggestions, let me know what else you come up with. I will be on the look-out for other fixes.

[INDENT]regards <==BDQ
[/INDENT]

---

### Post by cdoublejj on 2012-10-05
Not only is this card clean it just refurbished/repaired it not to long ago with a fresh Arctic silver 5.

side not my drivers names when loading up "additional drivers" changed now they read 

"nividia binary xorg driver, Kernel module and VDPAU library" instead of "Nvidia current"

so i installed one (they both had the same exact name) and now the activated one reads "nvidia_current_updates" also i can not purge it not matter what name i try it just says it can't find the package. 

Now it locks up every time and and i can't purge it. Perhaps another clean isntall with out internet is in order? I think the last time suggest commands, the said commands messed up/corrupted stuff.

As useless as I know it may be since it runs fine in windows 7, I'm gonna reseat the graphics card as suggested.

---

### Post by Bashing-om on 2012-10-05
Let's get a good nights sleep, wake up and get a new plan.
Here is the tutorial to get us back to basics;
[https://help.ubuntu.com/community/BinaryDriverHowto](https://help.ubuntu.com/community/BinaryDriverHowto)
and
```
lspci | grep VGA
sudo lshw -C display

```should tell what driver is loaded.
Figure out how to un-install what is presently loaded, and load the older driver ? ?
[INDENT]still try'n to help <==BDQ

[/INDENT]

---

### Post by cdoublejj on 2012-10-05
for now i have by passed my KVM switch so i can do the num lock trick, I have confirmed it hard locks when it freezes.

I also tried to run the the installers from official Ubuntu discs, both 7.10 and 8.04. I know for sure 8.04 hard locked (even after lowering CPU clocks and unhooking the Ethernet cable) , never checked for 7.04.

I ran that command,

[IMG]http://i.imgur.com/nrzGZl.jpg[/IMG]

I also noticed my usually method of recovery mode no longer works this could be because of the driver or because previous command from previous suggestion in this thread borked something. 

normal method is, hold shift>e> look for $vt handoff command tack on " s" (space included)>F10= root shell. This time around i held down shift chose recover and mode and then chose "root shell"

I'm thinking it's time fora clean install, i think i might try another version or distro just to see what happens.
I'm still wondering if it isn't a hardware problem. I have checked and rechecked my capacitors time and time and time again on the main board. non of the regular ones are bulged, and the all aluminum ones aren't leaking from the bottoms though i don't think i tell if there were bulged with out de soldering them and checking the bottoms. however it runs and stress tests fine.

[IMG]http://i.imgur.com/9FoXZ.jpg[/IMG]

EDIT: for now i'll let a few other distros and version torrent over night and leave the machine as it is just in case any one wants to try any more commands.
Like these.

---

### Post by Bashing-om on 2012-10-06
Doing the research now for this card// lemme see what I come up with, I foresee editing the x-org file // but -> one step at a time. will advise on what I come up with.

[INDENT][INDENT]BDQ

[/INDENT][/INDENT]

---

### Post by Bashing-om on 2012-10-06
Hours later and lots of searching; found nothing you have not tried. I have ran across several references to "bad" or inferior power supplies. Are you sure your PS is up to snuff ?

Here is a good troubleshooting link with a recipe to obtain a clean working environment:
[https://wiki.ubuntu.com/X/Troubleshooting/VideoDriverDetection?action=show&redirect=X/Troubleshooting/FglrxInteferesWithRadeonDriver#Problem%3a__Need_to_fully_remove_-nvidia_and_reinstall_-nouveau_from_scratch](https://wiki.ubuntu.com/X/Troubleshooting/VideoDriverDetection?action=show&redirect=X/Troubleshooting/FglrxInteferesWithRadeonDriver#Problem%3a__Need_to_fully_remove_-nvidia_and_reinstall_-nouveau_from_scratch)

Do not know what to advise else:
clean slate:
install open source driver, see what results:
bad =>uninstall open source
install closed source through apt-get install (upwards compatibility)

I remain committed to resolution, let me know what you decide as best course.
[INDENT]just try'n to help <==BDQ

[/INDENT]

---

### Post by cdoublejj on 2012-10-06
What would the open source driver be called? I actually just had this PSU RMAed when i built this machine, it *SHOULD* but, it's not the best brand or quality. I doubt that replacing it would change anything as the problem is so consistent. 

I'm also about to plug in the windows hdd back in to doubley make sure it just just happen to have hardware failure at the same time i tried to run linux.

I'm also gonna clean install and possibly try regular ubuntu to see if it's some freak bug with Lubuntu 12.04.

I also did some research on the A8N-SLI Deluxe with linux and didn't come up with much.

---

### Post by sembagdod on 2012-10-06
Try to install different version of Ubuntu

---

### Post by cdoublejj on 2012-10-07
So I tested,

Ubuntu 12.04
Lubuntu 11.10
Lubuntu 12.04

They all lock up just after getting to the desktop as usual. Hard locks, as usual. I burn all my discs at 4x speed with imgburn.

Tested Windows 7 too just to make sure it wasn't some weird happenstance but, windows 7 worked fine as usual I played BioShock fora bit. My GPU temps are great, 37ish C idle and 55ish C load (BioShock). It's ssssssssssooooooooooo silky smooth, great frames and response is great even with an old PS2 Microsoft mouse.

---

### Post by cdoublejj on 2012-10-07
So I just learned Nouveau is the open source driver, I was thinking it is the generic VGA driver used when it has no proper drivers. Even then I'm pretty sure it wouldn't work nearly well as the proper drivers.

Not to sure where to go form here yet. I guess I'll sleep on it some more.

---

### Post by MG&amp;TL on 2012-10-07
> **cdoublejj said:**
> So I just learned Nouveau is the open source driver, I was thinking it is the generic VGA driver used when it has no proper drivers. Even then I'm pretty sure it wouldn't work nearly well as the proper drivers.

Not to sure where to go form here yet. I guess I'll sleep on it some more.

Nouveau gives me about half the proprietary grunt on my hardware. If it works, and you don't intend to do any serious gaming (you have w7 for that, right?), using nouveau is probably your best bet.

---

### Post by cdoublejj on 2012-10-07
> **MG&TL said:**
> Nouveau gives me about half the proprietary grunt on my hardware. If it works, and you don't intend to do any serious gaming (you have w7 for that, right?), using nouveau is probably your best bet.


Actually the whole plan was to get ready for steam for linux and do some compatibility testing for/on wine.

---

### Post by Bashing-om on 2012-10-07
Have you had an opportunity to read through the latter howto ? I found advisory info I was not aware of. In particular why/how to clean up after multiple driver installs. Maybe at this time you have some interfering files laying about ?

Don't know, just a suggestion <==BDQ

---

### Post by cdoublejj on 2012-10-07
I did! :) However I chose to try installing a few other distros/version to see if the problem exists with other versions and it does.
ATM i'm still not sure what to do other than possibly reinstall Lubuntu 12.04 and wait for any other possible suggestions.

---

### Post by cdoublejj on 2012-10-09
i'm considering trying an install on my laptop after install an nvidia card in it, how ever it will only have a T5250 CPU and a GT240m which as might guess doesn't really compare to GTS250 and overclocked AMD dual core.

That said I finally backed up my bios settings and will try and on stock clocks for the heck of it though I could probably bet money on the fact that it change any thing.

---

### Post by Bashing-om on 2012-10-09
Best to ya! ..Like you I do not see clocking as a problem. Conversely, I can not comprehend not able to get a Nvidia card to work with "some" driver. Will continue to have you/situation on my mind.

[INDENT]best regards <==BDQ

[/INDENT]

---

### Post by cdoublejj on 2012-10-09
went back to stock clocks and nothing changed. It could be the board it does have a few issues but, as mentioned many times it runs fine in windows 24/7. I may look further in to it.

---

### Post by cdoublejj on 2012-10-16
tried with a few sata drivers but, they were kind of borked beforehand and one died after install. I may actually end up using my laptop in some sort of dual boot. so long as it sees the partitions correctly.

I had tried dual booting on the original drive on the desktop this thread is reffering to, and partition-er was all seeing all kinds of f***ed up partitions, like 10 different partitions that don't exist. I did some research, and unfortunately that is normal.

---

### Post by Bashing-om on 2012-10-16
don't see a correlation between hard drive and graphics driver performance.
disk utility in ubuntu can assess the drive if S.M.A.R.T. enabled.

Going back to the original thing.... I ran across a statement that with kernel mode setting in 12.04 ....the xorg file is no longer needed with Nvidia cards/// would not loose anything by trying a clean slate/install either open source or a proprietary driver with the xorg file deleted.

what ya think ? ==> BDQ

[INDENT][/INDENT]

---

### Post by cdoublejj on 2012-10-16
> **Bashing-om said:**
> don't see a correlation between hard drive and graphics driver performance.
disk utility in ubuntu can assess the drive if S.M.A.R.T. enabled.

Going back to the original thing.... I ran across a statement that with kernel mode setting in 12.04 ....the xorg file is no longer needed with Nvidia cards/// would not loose anything by trying a clean slate/install either open source or a proprietary driver with the xorg file deleted.

what ya think ? ==> BDQ



If you don't mind, just tell me how.

---

### Post by Bashing-om on 2012-10-16
Sure... no sweat...
```
sudo apt-get purge nvidia-current nvidia-settings
sudo rm /etc/X11/xorg.conf
sudo apt-get install xserver-xorg-video-nouveau

```Is my suggestion ..start all over again with the open source driver, see what happens.
[INDENT]still try'n to help <==BDQ
 
[/INDENT]

---

### Post by cdoublejj on 2012-10-17
Well i can't even start with an nivdia driver and always start with the open source driver by unplugging the either net cable when i install it (install updates afterwards). If you leave an internet connection plugged in it will install Nividia drivers (with out asking, automatically). I know fora fact it does NOT hard lock with Nouveau. I 100% know it's an nividia driver problem and not just the repository drivers I have tried other Ubuntu repository drivers that weren't' in the repository that i down loaded and installed to no avail (RPM file).

---

### Post by Bashing-om on 2012-10-17
Yikes ! Again, I am back to think'n and looking// Short of blacklisting, there must exist a way to load a desired module.
Out of curiosity what modules are presently loaded ?
```
sudo lsmod
```[INDENT]'tis a puzzle ==>BDQ

[/INDENT]

---

### Post by cdoublejj on 2012-10-18
nothing at the moment but, if you owuld like i clean install working or non working and run the command. and by that i mean i clean install with with drivers and updates (insta fail) or with out (nouveau).

---

### Post by Bashing-om on 2012-10-18
cdoublejj;

I am not the sharpest tool in the tool box - but, I find logic the greatest asset in fault isolation.
My desire is to share my passion for ubuntu -> get your system operational !
Back ground: I have never had a problem installing Nvidia drivers, several times I have not been able to get ATI/radeon functional with old cards ...Nvidia works ! (presently running radeon on this system no problems !)

on topic: I am here to assist you to get your system operational - a learning experience is always welcome -;
You have installed, reinstalled the operating system several times, attempted installing drivers in lots of ways - the patience of a rock.
my logic dictates to see what graphics drivers are loaded -> you say none:
my preference for drivers is open source for a number of reasons,
second is through support channels, 
third is direct from Nvidia (lost in upgrades).

To that end ...my suggestion for fault isolation:
boot up with "nomodeset" -> attempt to install the open source driver.
see what the system identifies the driver as :
modprobe that sucker and see if we can force load it !

we want to avoid any possibility of a "conflict with drivers" situation. (clean slates)

so...what are your thoughts ?
[INDENT]doin' what I can ==>BDQ
[/INDENT]

---

### Post by cdoublejj on 2012-10-18
well i ahve nothing installed right now I should have specified that. Open source drivers work fine at least for 2d but, as far as i know for gaming open source drivers rob performance.

This problem is with only nivida drivers. that said i can install lubuntu again. I usually install with no internet so that it will default to open source drivers because open source drivers do not lock up the machine after boot like the nvidia drivers do.

that said i'm gonna head an do a "no internet install" and then do updates then reboot with "nomodeset"... actualy how do i boot with "nomodeset" i do safe boot to shell first and then run "nomodeset" or can i run it terminal.

---

### Post by Bashing-om on 2012-10-18
IMO the simplest way to "nomodeset" is edit the kernel command line from the grub boot screen.
Boot up install system->hold shift key down soon as bios screen clears->grub menu
hit any key to halt the countdown to boot; I expect the first enty is the kernel you desire to boot with, make sure it is higlighted (arrow key to it if needed) -> "e" key to edit -> arrow down to the kernel command line (similar to:  "linux /boot/vmlinuz-3.2.0-24-generic root=UUID=dbd69ed2-530c-4409-8f5a-a3f1ea41fc67 ro quiet splash $vt_handoff " after "quiet splash" insert the term "nomodeset" -without the quotes- ==> ctl+x to continue booting.
No graphics module(driver) is loaded --uses the kernel vesa driver for X. From this point we can load the driver of choice (Additional drivers utility is pretty smart, but can install a driver that does not function)[tried that ->] so might consider installing a bleeding edge driver from the ppa ?? If this driver fails will require un-installing to install another and using this ppa method, the driver will be lost when upgrading.


I am sure glad I do not require high definition  graphics ! <==BDQ

---

### Post by cdoublejj on 2012-10-19
notsure what you mean by "Boot up install system" but, i started my system with my already clean install lubuntu (no proprietary nvidia drivers) and "nomodeset" it and it appears to have no driver. i guess i'll try installing a proprietary nvidia drivers again.

EDIT: it hard locked just like with proprietary nvidia drivers.

EDIT:EDIT: confirmed, it is locking up with "nomodeset" I reboot and booted normaly and all was fine then i "nomodeset" it again and it locked up just like the first time i ran "nomodeset"

---

### Post by Bashing-om on 2012-10-20
looking and considering...get back to ya soonest.

[INDENT][INDENT][INDENT][INDENT]BDQ

[/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by Bashing-om on 2012-10-20
cdoublejj;

how about this approach:[http://ubuntuforums.org/showthread.php?t=2029882](http://ubuntuforums.org/showthread.php?t=2029882)
instructs to clean up, go to Nvidia web site, submit info-> d/l suggested driver ->install instructions.

I am still considering the need for the xorg config file under KMS in 12.04.
[INDENT]regards <==BDQ
 
[/INDENT]

---

### Post by Bashing-om on 2012-10-20
still looking bout kms/xorg ...this may no longer apply ...

> 
**Screen Blanks/Monitor Turns Off**

 Using a laptop with a [GeForce]("https://help.ubuntu.com/community/GeForce")  Go card, or connecting the sole display via DVI on a dual-head system  sometimes results in the screen not receiving a picture. This is caused  by the driver outputting video to the VGA port on the graphics card,  instead of DVI. 
The  usual hint that you have this problem is when you hear the startup  sound but nothing appears on the screen. If you do not hear any sound,  you are more than likely experiencing unrelated problems. 
This is a [bug]("https://bugs.launchpad.net/bugs/82312") about displays on digital outputs being blank when using NVIDIA driver, and can be resolved by editing your /etc/X11/xorg.conf file: 

[LIST]
[*]Switch to the console by using ctrl+alt+F1, or reboot and select recovery mode from the GRUB menu.
[*]Open and edit xorg.conf like this: sudo nano /etc/X11/xorg.conf.
[*]Find the line that says: Section "Screen"
[*]Insert a new line that says Option "UseDisplayDevice" "DFP".
[*]Save the file. If you had to restart into recovery mode, type reboot, otherwise restart your display using sudo /etc/init.d/gdm restart.
[/LIST]

continue to look <==BDQ

---

### Post by cdoublejj on 2012-10-21
While it is not a laptop it is a dual DVI card but, the problem is hard lock and not a loss of signal.

---

### Post by Bashing-om on 2012-10-21
my brain is hurting ...but I am pressing on// In the process i do pick up  acorns of knowledge// (KMS puts it's fingers in lots of pies !)

[INDENT]cul <==BDQ

[/INDENT]

---

### Post by cdoublejj on 2012-10-21
I do appreciate all the help.

---

### Post by Bashing-om on 2012-10-23
Not much direct help...I really want to get this Nvidia card working. In this process I expect to learn a bunch.
Boy, how things have changed in just 3 years ! ..3d rendering, KMS, graphics cards capabilities undreamed of, drivers to support it.

I have two other machines running Nvidia cards; solid never so much as a hickup from them//but the times are coming I will have to cope with the faster/better cards and system they run on !


Currently: still seeking that connection I lost and so far have not found it ...

edit: I do have something in mind ..still researching as I have not seen any others talk about the option.
[INDENT][INDENT]looking ==> BDQ

[/INDENT][/INDENT]

---

### Post by Bashing-om on 2012-10-25
cdoublejj;

I remain active in seeking what is going on with the Nvidia/Xorg.conf/(KMS)...
I ran across this that might be pertinent as you profess to be overclocking.
QUOTE]
**I use the Coolbits overclocking interface to adjust my graphics card's clock frequencies, but the defaults are reset whenever X is restarted. How do I make my changes persistent?**
    
 Clock frequency settings are not saved/restored automatically by default to avoid potential stability and other problems that may be encountered if the chosen frequency settings differ from the defaults qualified by the manufacturer. You can use the command line below in ~/.xinitrc to automatically apply custom clock frequency settings when the X server is started:
     # nvidia-settings -a GPUOverclockingState=1 -a GPU2DClockFreqs=<GPU>,<MEM> -a GPU3DClockFreqs=<GPU>,<MEM>  Here <GPU> and <MEM> are the desired GPU and video memory frequencies (in MHz), respectively.
      **Why is the refresh rate not reported correctly by utilities that use the XRandR X extension (e.g., the GNOME "Screen Resolution Preferences" panel, `xrandr -q`, etc)?**
    
 The XRandR X extension is not presently aware of multiple display devices on a single X screen; it only sees the MetaMode bounding box, which may contain one or more actual modes. This means that if multiple MetaModes have the same bounding box, XRandR will not be able to distinguish between them.
 In order to support DynamicTwinView, the NVIDIA X driver must make each MetaMode appear to be unique to XRandR. Presently, the NVIDIA X driver accomplishes this by using the refresh rate as a unique identifier.
 You can use `nvidia-settings -q RefreshRate` to query the actual refresh rate on each display device.
 This behavior can be disabled by setting the X configuration option "DynamicTwinView" to FALSE.

[/QUOTE]
Presently I do not know how old the info may be ....intriguing docs never-the-less at:
[http://http.download.nvidia.com/solaris/1.0-9629/README/chapter-03.html](http://http.download.nvidia.com/solaris/1.0-9629/README/chapter-03.html)
[INDENT]still try'n to get my ducks in a row ==> BDQ

[/INDENT]

---

### Post by cdoublejj on 2012-10-25
Interesting my card is OCed by default (factory Overclocked [again runs fine in 7]), i wonder if it is playing with the clocks or setting them to what it thinks they should be. sounds like there are a few other things going on with the drivers based on the comment.

---

### Post by Bashing-om on 2012-10-26
I also am thinking..maybe the EDED data from the monitors is not being interpreted correctly...I know of the methods to see this data, but have not figured out if X.org.conf is required, and if so how to configure Xorg...from what I have gathered, the nvidia installer should take care of any config files ??

Nvidia-settings utility has a lot of versatility, Play with some of them and see what results ?
 At one time the 173 proprietary driver was the recommended driver for your card ..how bout re-installing 173 -> Nvidia-install update utility ; see if it finds a better driver now ?
[INDENT]problems, problems, problems, what to do; what to do <== BDQ



[/INDENT]

---

### Post by cdoublejj on 2012-10-26
well i supposes i could try to find 173 version drivers. also need to try lubuntu 12.10. the trick is with the driver settings utility i would have to find a a way to use it in safe mode.

---

### Post by Bashing-om on 2012-10-27
still here ...still not helping much at all :
Just checked Nvidia's d/l site:
[http://www.nvidia.com/Download/Find.aspx?lang=en-us](http://www.nvidia.com/Download/Find.aspx?lang=en-us)

and current recommended drive fer your AMD/64 GTS250 is the 304.60 version.

I am presently at a loss as to what to do ...
- we know that the display's data is good ...else the opensource drivers would not work at all.
- we know that overclocking is not a factor
-* and we know that installing ANY proprietary driver causes a "lock up"

questions: can we make configs in Xorg,conf to any effect ?

going to go see what I can find on Nvidia's web site -> back soonest.
[INDENT]still try'n <== BDQ

[/INDENT]

---

### Post by Bashing-om on 2012-10-27
addit: safemode -> best I recall this mounts the drives in -read only - mode ...from this mode, can re-mount the drives - read write -- will have to hunt up the commands/procedure ... my tunnel vision condition dictates Nvidia web site first.

[INDENT]later ==> BDQ

[/INDENT]

---

### Post by Bashing-om on 2012-10-27
nothing new to report at this time ..
what errors are in /var/log/Xorg.0.log ..??? replace 0 with whatever log number is applicable to the time frame of booting ...

Would it help any to compare to my file (stable - radeon --If it would help I can get the log file from a system running Nvidia) ...to big of a file to attach onto the forum ..any suggestion ??

Nvidia help ->..xorg.conf...umptenn hundred "options"  available ..do not comprehend the majority of them...directly applicable ???

back to looking ==> BDQ

---

### Post by cdoublejj on 2012-10-28
> **Bashing-om said:**
> nothing new to report at this time ..
what errors are in /var/log/Xorg.0.log ..??? replace 0 with whatever log number is applicable to the time frame of booting ...

Would it help any to compare to my file (stable - radeon --If it would help I can get the log file from a system running Nvidia) ...to big of a file to attach onto the forum ..any suggestion ??

Nvidia help ->..xorg.conf...umptenn hundred "options"  available ..do not comprehend the majority of them...directly applicable ???

back to looking ==> BDQ

Where and how do i see or get the file?

""Nvidia help ->..xorg.conf...umptenn hundred "options"  available ..do  not comprehend the majority of them...directly applicable ???""

Not sure what that means.

---

### Post by Bashing-om on 2012-10-28
Let me see if I can get my own mind straight ....

As I understand it ...xorg.conf is no longer "required" but if it does exist it will be used.
It is mind boggling the number of options that may be employed in the xorg.conf  config file.

My Xorg.0.log file for comparison: too large to upload on this forum as a .txt file - If you want to look at it ...what is your suggestion to get it to you.

recovery mode -> edit: terminal command from the recovery mode console:
```
mount -o remount rw /
``` mounts the root partition read and write

to edit files use the vi (text) editor
for instance:
```
vi /etc/fstab
```If you can use the 304. 60 driver version, good thing will be that dkms (dynamic kernel module support) is available --> automatic   builds of new modules if/when a different kernel is installed.
[INDENT]hth ==> BDQ

[/INDENT]

---

### Post by cdoublejj on 2012-10-29
well step one i'm going to install Lubuntu 12.10 with internet and see what happens, if it locks up like usual perhaps i can get the xorg logs for you.

---

### Post by cdoublejj on 2012-10-30
Well 12.10 defaults to open source drivers so that was interesting the drivers installer is incorporated in to "software sources". Regardless same as usually enable nvidia drivers reboot > desktop > hard lock.

It would be really cool if someone with  some super coder linux fu could chime in. I'm only have google fu ans I'm all alone on this issue one the reason that makes me partially suspect hardware.

At this point I'm tempted to try OSX x86 again.

---

### Post by Bashing-om on 2012-10-30
second that -chiming in- I am all out of ides at this point.

wait watch and see ==> BDQ

---

### Post by cdoublejj on 2012-11-27
Installed Propriety graphics with the video card in another system and it worked fine. said system is a q9550, P5E3 Deluxe, 8gb ddr3 ram.

---

### Post by Bashing-om on 2012-11-28
Hey great news....

All I can surmise is some kind of buss conflict on the irqs ????
Might be interesting to look at the irqs at some future point.

[INDENT][INDENT]Happy ubuntu'n <== BDQ

[/INDENT][/INDENT]

---

### Post by cdoublejj on 2012-11-30
I don't really understand IRQs. I believe modern OSes ignore the IRQs? I was thinking bugged nivida chipset drivers?

---

### Post by Bashing-om on 2012-11-30
irq's still much in use ...look at your log files, will see the irq's assigned. Think ya said the card works in another box ? Could be that KMS is not playing nice with the card. In that case, I think, we are back to configuring xorg (never had too, very weak point).

xorg is largely depreciated but is still around and has to have some use sometimes, perhaps in a situation such as this ?

You have tried every driver you can load and I assume you have also used nvidia settings to no effect. Done all that you can to get a driver working ...except build an xorg config file. Right ?

[INDENT][INDENT]still try'n to help <== BDQ

[/INDENT][/INDENT]

---

### Post by cdoublejj on 2012-12-04
In the end i got what i wanted (the other machine) i just wanted a multi boot machine with an nvidia card since Nvidia has the best linux support. 

I have no real reason to toy around with linux on this machine when i have it working in the other box.

Normally I would bother me and would try to figure it but, i'm kind of tired of working on this machine.

I think i'm going to stick purely with window 7 on this one since my other box has linux running just fine with  an OTHER gts250 i recently purchased as well as THIS gts250.

It's either something wonky with this mobo the IRQs or driver troubles. I think i'd rather ust get this machine up working again while i play with linux on my other box.

---

