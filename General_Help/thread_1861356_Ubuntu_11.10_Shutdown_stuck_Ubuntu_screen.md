---
title: "Ubuntu 11.10: Shutdown stuck Ubuntu screen"
date: 2011-10-15
forum: General Help
---

### Post by Jary316 on 2011-10-15
Hi everyone,

I updated my machine from Ubuntu 11.04 to 11.10. Now when I try to 'shutdown' from the menu, I get to the dark Ubuntu screen with 4 white dots. Nothing seems to happen, the hard disk does not do any work, it just stalls there.

I am not sure what I should do. I've had to press the power button to completely turn it off.

Any suggestions please?

Thank you very much.

---

### Post by jose_luis_fdez_diaz on 2011-10-15
Hi,

I have the same problem, by I updated from Ubuntu 10.10 to 11.10. I think that it is a kernel problem. In 10.10 kernel version was 2.6 and in 11.10 is 3.0. 

Any hint about what can I do to fix this problem?

Thanks in advance,
Jose Luis.

---

### Post by prupert on 2011-10-15
Hi 

Same issue here, upgraded from 11.04 - 11.10, I had the log-in issue others had here (can't log in and being brought back to log in screen again) alongside a weird issue during the first boot post-install where I got a message on the initial four dots boot screen saying that it was waiting for the network to be configured, it got stuck on that screen and then I had to hard reset....

Now, after rebooting a few times, I can boot up and log in fine, but Ubuntu refuses to shutdown, it just gets stuck on the four dots screen and apparently is doing nothing.

syslog and kern.log show nothing of use since there appears to be no obvious logging facilities of the shutdown process.

The same laptop also has UbuntuStudio installed on it and upgrading that has resulted in no issues (other than a pig ugly theme for some reason).

---

### Post by sagarthegreat1 on 2011-10-16
I too face the same proble. gets stuck in the ubuntu splash screen, never shuts down.
using i386 version with ati4670 & amd x3-435

---

### Post by SteveMayne on 2011-10-16
And another case of it here.  This is on a Dell Studio 15 laptop (if it matters).

Upgraded from 10.10 -> 11.04 -> 11.10 yesterday.

---

### Post by Elkimo on 2011-10-16
I have the same problem on 3 computers (2 different desktop pc's and 1 Dell Studio 15) here. When shutting down, the system hangs on the plymouth screen (the dots stop flashing on and off too), and the system doesn't power down. 

It does seem as if certain parts of the computer (I think the hard drive) shut down, since there is less noise, but the screen remains on, and the fan keeps spinning.

I don't know if it is related, but sometimes my shutdown button (the one in the top-right corner of the screen) doesn't work at all, after pressing 'shut down' the dialog window disappears, and nothing happens. I have to shutdown using 'halt' in a terminal window.

---

### Post by prupert on 2011-10-16
Hmm and now it seems to work!

The only thing I did, was post this message, so I guess that is the current fix...biatch about it on the UB forums and it fixes itself ;)

In all seriousness though, I'll keep an eye and see if it remains fixed and report back. 

It does seem one of the limitations of the UB beta testing process is that the upgrade from one release to another gets minimal testing (since most testers I guess either use a standalone machine and a fresh install to test, or the initial upgrade works fine with the alpha releases and so they never get to test a final upgrade). Whenever I have had problems with a new distro upgrade, it has always been with an upgrade and not a new install. Shame, but hard to solve I guess.

---

### Post by Joshas on 2011-10-16
I've been having the same problem with poweroff (upgraded 11.04 to 11.10). Only one time Ubuntu managed to power off correctly, otherwise it gets stuck on poweroff screen. Freeze happens on restarting too.

---

### Post by prupert on 2011-10-16
So, it happened again, not fixed, no surprise.

I am thinking it is an issue with our dear friend Network-Manager, which now appears, according to syslog, to load very early on and thus I suspect is being killed very late on.

When shutting down, if I login to another tty and kill lightdm and then issue the shutdown command, I get the message "Killing All Remaining Processes     [Fail]" which indicates the shutdown fails because a process isn't dying.

The following seems to work for me, when you want to shutdown, issue the following to get another tty log in screen:

```
Ctrl + Alt + F2 
```

Log in using your normal log in details.

Kill the new GDM (called lightgdm) by issuing:

```
sudo service lightdm stop
```

Then kill network-manager, because it is a right pita (in all honesty, this might be all you need to do, but the above steps allow you to see all the messages Ubuntu spits out as it shuts down to all you to help debug this issue):

```
sudo service network-manager stop
```

Then issue the shutdown command

```
sudo shutdown -hP now
```

And you should be able to shutdown properly.

Can anyone try this and let me know how it works? It worked for me.

It might also be worth noting I use an encrypted home folder, not sure if that has anything to do with it.

Anyway, I'm off to post a bug on launchpad to get some feedback from the guys in the know.y

---

### Post by prupert on 2011-10-16
Ahh, bugger. False alarm, that didn't fix it as this issue just happened to me and those steps didn't fix it.... sad face.

---

### Post by prupert on 2011-10-16
Hmm, I am still thinking it might be a network issue, if I boot into the recovery menu via grub and then choose to drop to a root prompt and try to shutdown, I see an error that the system was unable to deconfigure all network interfaces....it does however manage to shutdown.

Issuing sudo ifdown --force eth0 wlan0 before trying to shutdown (after killing network-manager) however doesn't help.

---

### Post by bkolek on 2011-10-17
I have similar problem. When I hit shutdown or restart it goes on lightdm screen and only from there I can turn the computer off. I've tried what prupert suggested and it worked.

---

### Post by bkolek on 2011-10-17
I have also tried:
```
sudo shutdown -P now
```and it worked.

---

### Post by laycor on 2011-10-18
> **prupert said:**
> Hi 

Same issue here, upgraded from 11.04 - 11.10, I had the log-in issue others had here (can't log in and being brought back to log in screen again) alongside a weird issue during the first boot post-install where I got a message on the initial four dots boot screen saying that it was waiting for the network to be configured, it got stuck on that screen and then I had to hard reset....

Now, after rebooting a few times, I can boot up and log in fine, but Ubuntu refuses to shutdown, it just gets stuck on the four dots screen and apparently is doing nothing.

syslog and kern.log show nothing of use since there appears to be no obvious logging facilities of the shutdown process.

The same laptop also has UbuntuStudio installed on it and upgrading that has resulted in no issues (other than a pig ugly theme for some reason).

Same here on a HP 6735s - upgraded from 11.04 to 11.10 and got the same network message..  After a massive number of reboots and connection to a wired network (turning off wireless), I managed to get it booted.  I had the same issues when shutting down (4 dots with Ubuntu logo and nothing else).

Since then I formatted the hard disk and installed 11.10 from scratch, no network issues this time but still have a shutdown problem.

Similar issue arises randomly when I safely remove a USB hard disk and then unplug it - keyboard, mouse, everything freezes..


Only solution to this is hold the power button for 5 seconds.

---

### Post by bernieke on 2011-10-18
My dell vostro v13 won't shutdown either. On my latitude e6500 I don't have this problem.

I can tell you it's certainly not network-manager that's causing the problem, since I've removed nm and run wicd instead.

[EDIT]
The laptop with the problem has an intel integrated gpu and an intel chipset.

---

### Post by Joshas on 2011-10-18
Removed ATI proprietary driver and now it looks like that shut down and reboot works correctly. It was giving kernel panic errors on shutting down.

---

### Post by Zilvermeeuw on 2011-10-19
After install all updates, it seems to be OK.

Edit: but shutting down is sloooooow

---

### Post by aschweig on 2011-10-19
I have a similar issue.  I am using xubuntu with two monitors.  Nvidia proprietary drivers. The thing hangs at the splash screen -- doesn't even finish drawing the splash screen.  
I was hoping to use the Nouveau driver, but I am at a loss how to get the "separate x screen" configuration to work that way in xubuntu.

---

### Post by changtraidoc on 2011-10-20
I have a trouble with lingdm, when i  try to 'shutdown' from the menu, it out to lingdm login :-o
Any nde know why :O

---

### Post by Magic_Spehar on 2011-10-22
Similar issue here.  

After the update from 11.04 to 11.10: when I shut down the pc sometimes it goes back to the login screen and then I have to do shutdown there which works well then.

Sometimes the pc shuts down but ends with the ubuntu splash screen and gets stuck there.

The issue may be driver related: I use the AMD/ATI FGLRX graphics driver.

I have a second pc where I also did the update to 11.10 and there I have no problem at all but I don't use the above driver but the NVIDIA graphics driver.  

Both pc's have Ubuntu 11.10 64-bit.

---

### Post by K4NEB on 2011-10-22
mine didnt like shutting down or restarting

i just left it yesterday and shutdown took about an hour i think  but its been fine since then

---

### Post by nicocool84 on 2011-10-24
Same problem here after upgrade from 11.04 to 11.10 on 2 very different computers. Tried killing lightdm and network-manager from the console, it didn't seem to work. Once I managed to obtain the "Will now shutdown" message but still I had to press the power button to *really* shutdown my machine.
Any help on this would be appreciated. I was just about to convince my girlfriend that ubuntu > windows :(

---

### Post by Magic_Spehar on 2011-10-27
I just registered the bug "after upgrade to Ubuntu 11.10 shutdown screen stuck" [https://bugs.launchpad.net/ubuntu/+bug/882817](https://bugs.launchpad.net/ubuntu/+bug/882817)

---

### Post by Jary316 on 2011-11-03
> **Magic_Spehar said:**
> I just registered the bug "after upgrade to Ubuntu 11.10 shutdown screen stuck" [https://bugs.launchpad.net/ubuntu/+bug/882817](https://bugs.launchpad.net/ubuntu/+bug/882817)

Thanks a lot for submitting it!

---

### Post by RichardSM on 2011-11-08
[COLOR="Black"][/COLOR]********Hello All

I also was having this same problem, I did get my Ubuntu 11.10 fixed. You'll have to make a change in terminal to do this press Ctrl+Alt+T, This will bring up Terminal screen. 
Type in sudo gedit /etc/default/grub
You should see somthing like this:
...................................\
GRUB_DEFAULT=0
GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT="10"
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null  echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splish"
GRUB_CMDLINE_LINUX"" 

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console
................................
where it says "GRUB_CMDLINE_LINUX="" is where you add acpi=force. it should look exacty like this:
GRUB_TERMINAL_ LINUX="acpi=force"

Save your file and and go back to terminal again and type:
sudo update-grub
...................

One last thing you my have to delete the words "quiet splash" or not, do what ever works. 
GRUB_CMDLINE_LINUX_DEFAULT=""

Updated 3/5/12
This might fix some computers but not all of them. But do read on down the posts as some of the other folks have worked out some of the fixes on their systems most of all don't give up keep asking for help. Best wishes to all.

Try this and let me know if it works for any of you.


MS-6380 MB
1Gb Memory
40Gb HD
256Mb nVidia card
32bit OS Ubuntu 11.10
Home built PC.

---

### Post by prupert on 2011-11-08
I'm afriad it doesn't fix it for me and I presume you mean:

GRUB_CMDLINE_LINUX="acpi=force"

It is depressing this is getting little response from the devs. the bug report is also getting no feedback from devs. I suspect it is because shutdown bugs are very hard to track down...

---

### Post by JoZ3 on 2011-11-08
> **prupert said:**
> I'm afriad it doesn't fix it for me and I presume you mean:

GRUB_CMDLINE_LINUX="acpi=force"

It is depressing this is getting little response from the devs. the bug report is also getting no feedback from devs. I suspect it is because shutdown bugs are very hard to track down...

Tnx RichardSM and prupert this work for me :D

AMD Phenom II X3
Ubuntu 11.10 x64
ATI HD4850

---

### Post by RichardSM on 2011-11-08
Hi prupert

Yes
GRUB_CMDLINE_LINUX="acpi=force"

One question did you omit the two words "quiet splash" in line GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"

---

### Post by RichardSM on 2011-11-11
Hello prupert
Maybe try it like this:
GRUB_CMDLINE_LINUX_DEFAULT="quiet acpi=force"
GRUB_CMDLINE_LINUX""

I remember back in Ubuntu 10.10 this worked it might be worth a try let me know.

Thanks Richard

---

### Post by cbl016 on 2011-11-19
This worked for me. Thanks!

---

### Post by prupert on 2011-11-19
> **RichardSM said:**
> Hello prupert
Maybe try it like this:
GRUB_CMDLINE_LINUX_DEFAULT="quiet acpi=force"
GRUB_CMDLINE_LINUX""

I remember back in Ubuntu 10.10 this worked it might be worth a try let me know.

Thanks Richard

Nope, no dice sadly.

Pretty sure this is an NFS / fstab issue where the one of the network or file share demons isn't properly exiting..

---

### Post by Ti_p_it on 2011-12-04
I tried all solutions suggested here without success. Also poweroff --force command does not make a difference or killing any network programs. 

"shutdown -r 0" goes nicely... 

There is not yet solution found for me here [1] either.

Any other suggestions I / we could try? Anyone? ](*,)

[1] [https://bugs.launchpad.net/ubuntu/+bug/882817](https://bugs.launchpad.net/ubuntu/+bug/882817)

---

### Post by Rhizoid on 2011-12-17
I've got a similar symptom.  I have a remote file system mounted as cifs which if I unmount manually and then restart/shutdown, it's like greased lightning.  If I leave it mounted and restart/shutdown it appears to hang for a very long time.

If you've got any remote file systems mounted, try un-mounting them manually and then shutting down - does that fix the problem?

---

### Post by Ti_p_it on 2011-12-18
> **Rhizoid said:**
> I've got a similar symptom.  I have a remote file system mounted as cifs which if I unmount manually and then restart/shutdown, it's like greased lightning.  If I leave it mounted and restart/shutdown it appears to hang for a very long time.

If you've got any remote file systems mounted, try un-mounting them manually and then shutting down - does that fix the problem?

I got a basic Xubuntu install in Lenovo Ideapad without any mounts after installing. /etc/fstab is pretty much the same basic partitioning I always do.
[1] []("https://bugs.launchpad.net/ubuntu/+bug/882817")here is discussion about whether the freeze is caused by mounts or something else. No solutions for my hang ups.

[1] 
[https://bugs.launchpad.net/ubuntu/+bug/882817](https://bugs.launchpad.net/ubuntu/+bug/882817)

---

### Post by okanagansage on 2011-12-21
I was getting a frozen screen at shutdown: lubuntu with four dots underneath that were no longer blinking (like the original poster). It's a fresh install of lubuntu 10.04. Something like this also happened to me on the same computer (different hdd) when I installed Xubuntu 9.10 on it. The following worked for me.

I changed /etc/default/grub a little differently than some of the posts on this thread. I opened the file with nano I believe:

sudo nano etc/default/grub

And then I change "quiet splash" to "quiet splash acpi=force"

Then updated grub2 with:   sudo update-grub2

The changes take effect after a restart. After restarting, see if it shuts down properly.

---

### Post by gianiaz on 2011-12-24
Same problem here with 2 dell precision notebook (m4400 and m4600).

I've purged network manager, tried the acpi=force method, but the system randomly doens't halt. 

In the m4400 I've never had this problem from previous versions of ubuntu.

---

### Post by orestis46 on 2012-01-03
Same problem here with Desktop PC (Intel i5 2320 8G ram - Ubuntu 11.10 64bit) after trying various solutions found nothing worked. What worked for me was the solution proposed for changing /etc/default/grub.conf : 

#GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi=force"

Then run command: update-grub2.

Thnx :)

NOTE: ...hmmmm....seems restart option although still is broken !!!

---

### Post by simoniux on 2012-01-09
I concur with Rhizoid. For me the problem was a mounted windows share. Restarting or shutting down, the system would hang with "Ubuntu" splash screen and running dots. It worked fine, if I unmounted the share manually before restarting or shutting down. 

To fix it permanently I adjusted when the share is automatically unmounted:

```
sudo update-rc.d -f umountnfs.sh remove
sudo update-rc.d umountnfs.sh stop 15 0 6 .
```

See: [https://help.ubuntu.com/community/MountWindowsSharesPermanently#System_Hangs_on_Shutdown]("https://help.ubuntu.com/community/MountWindowsSharesPermanently#System_Hangs_on_Shutdown")

---

### Post by linfidel on 2012-01-09
I believe there are multiple problem causes in this thread.  The one I'm familiar with (and there is at least one launchpad bug report on it - #750437, fglrx hard lockup on shutdown); it is a total crash most of the time on shutdown requiring a forced power off or reset - no response to any keypresses.

This is caused by the AMD fglrx driver.

---

### Post by Ti_p_it on 2012-01-09
> **simoniux said:**
> I concur with Rhizoid. For me the problem was a mounted windows share. Restarting or shutting down, the system would hang with "Ubuntu" splash screen and running dots. It worked fine, if I unmounted the share manually before restarting or shutting down. 

To fix it permanently I adjusted when the share is automatically unmounted:

```
sudo update-rc.d -f umountnfs.sh remove
sudo update-rc.d umountnfs.sh stop 15 0 6 .
```See: [https://help.ubuntu.com/community/MountWindowsSharesPermanently#System_Hangs_on_Shutdown](https://help.ubuntu.com/community/MountWindowsSharesPermanently#System_Hangs_on_Shutdown)

This is pretty sure a different bug we are dealing with here (introduced in 10.10) so this solution does not fix my problem. But thank you for pointing this resource.

---

### Post by Sigma1 on 2012-01-26
The solution given here sorted the problem out for me: [http://salaba.wordpress.com/2011/05/28/ubuntu-11-04-shut-down-problem-solved/](http://salaba.wordpress.com/2011/05/28/ubuntu-11-04-shut-down-problem-solved/)

```
sudo modprobe -rf rt2860sta
sudo modprobe rt2860sta
echo blacklist rt2800pci | sudo tee -a /etc/modprobe.d/blacklist.conf
```

I'm not quite sure what line 2 does. Or rather, I can't see the point of loading a module you've just removed... I must be missing something. The most important thing, it seems to me, is blacklisting the offending module in line 3. After another reboot things sorted themselves out for me.

---

### Post by bernieke on 2012-01-27
Neither of those drivers are loaded on my system.

But it seems a lot of these proposed solutions have to do with how the network behaves... (The rt drivers are both for wifi.)

---

### Post by feistybird on 2012-01-31
> **RichardSM said:**
> [COLOR="Black"][/COLOR]********Hello All

I also was having this same problem, I did get my Ubuntu 11.10 fixed. You'll have to make a change in terminal to do this press Ctrl+Alt+T, This will bring up Terminal screen. 
Type in sudo gedit /etc/default/grub
You should see somthing like this:
...................................\
GRUB_DEFAULT=0
GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT="10"
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null  echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splish"
GRUB_CMDLINE_LINUX"" 

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console
................................
where it says "GRUB_CMDLINE_LINUX="" is where you add acpi=force. it should look exacty like this:
GRUB_TERMINAL_ LINUX="acpi=force"

Save your file and and go back to terminal again and type:
sudo update-grub
...................

One last thing you my have to delete the words "quiet splash"
GRUB_CMDLINE_LINUX_DEFAULT=""

Try this and let me know if it works for any of you.


MS-6380 MB
1Gb Memory
80Gb HD
256Mb nVidia card
32bit OS Ubuntu 11.10

--

I have had the same problems after the recent Ubuntu 11.10 updates, this solution works for me, many thanks!

---

### Post by bernieke on 2012-02-03
Solved it for me.

Thanks!

---

### Post by aliarnold on 2012-02-05
> **bernieke said:**
> Solved it for me.

Thanks!

Hi
With what way?

---

### Post by petehild on 2012-02-11
For me the problem started with the update to kernel 3.0.0-15. Kernel 3.0.0-14 works like a charm. 3.0.0-16 (from ubuntu-proposed) doesn't work either. For now I'll stick with 3.0.0-14.

Greetings
Pete

---

### Post by petehild on 2012-02-16
As I just posted in another Thread, I played around with Kernel 3.2.0 under oneiric, and shutdown works with that kernel for me.
[http://www.upubuntu.com/2012/01/how-to-install-linux-kernel-32-under.html](http://www.upubuntu.com/2012/01/how-to-install-linux-kernel-32-under.html)

Pete

---

### Post by faint545 on 2012-02-24
> **petehild said:**
> As I just posted in another Thread, I played around with Kernel 3.2.0 under oneiric, and shutdown works with that kernel for me.
[http://www.upubuntu.com/2012/01/how-to-install-linux-kernel-32-under.html](http://www.upubuntu.com/2012/01/how-to-install-linux-kernel-32-under.html)

Pete

Installing the 3.2 kernel fixed this problem for me.

---

### Post by Sigma1 on 2012-02-26
I spoke too soon... the drivers weren't what was creating the problem. The suggestion found here: [http://ubuntuforums.org/showthread.php?t=1690434](http://ubuntuforums.org/showthread.php?t=1690434) appears, finally, to have sorted things out. i.e. add: apm power_off=1 to /etc/modules
I'll keep my fingers crossed.

---

### Post by faint545 on 2012-02-27
> **faint545 said:**
> Installing the 3.2 kernel fixed this problem for me.

I retract my earlier statement. Installing the 3.2 kernel **DID NOT** fix the problem. It came back soon afterwards. 

I, however, seem to have solved the issue for me. Shutdown/restart operations started working perfectly as soon as I had uninstalled my ATI proprietary drivers. I had installed them originally from jockey. I don't know if using the drivers from ATI directly would have the same negative effect or not.

---

### Post by lz1dsb on 2012-03-04
I would like to thank everybody on this thread for the help and insight they provided. I used one of the solutions proposed and now my issue with shutdown and restart is fixed. 
Just for a reference to others who might be having the same issue on a similar hardware. I'm using Dell Studio 1555 laptop and I'm running 11.10 64-bit.
Here's how my /etc/default/grub file looks like:
```

GRUB_DEFAULT=0
GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi=force"
GRUB_CMDLINE_LINUX="quiet splash acpi=force"

```

Thank you all!

Regards,
Boyan

---

### Post by lz1dsb on 2012-03-05
Hmmm... I'm confused...
After a few successful restarts and shutdowns I've got the same issue....
I'll have to experiment more and just like I suspected the issue seems to be a bit more complicated :( I'll report my findings...

---

### Post by tobiz on 2012-03-08
I get the failure to shut down on my clean install mythbuntu 11.10 (plus all updates to date), so I don't think it's anything to do with upgrading. I've tried the suggested mods to grub and still the problem persists. It seems (myth)(u)buntu is non deterministic in both start up and shut down, very bad for a computer system! Some times it will shut down ok, others it just hangs with the 5 red dots.  If I had to guess, and it is a guess since this is mythbuntu specific, it will always hang after mythtv-frontend has been run (in the limit just start it and immediately close it). I can't understand why this problem hasn't been solved by the dev team. A work around of holding down the on/off power switch is no good in a remote operation situation, as mine is - when it is told to shut down from s/w it has to shut down!!

---

### Post by tobiz on 2012-03-08
Ok an update. I've found that after running update-grub2 shut down  works correctly, ie 5 dots go red and after last one system powers off.  On reboot and shut down it then hangs.  Question is therefore: what does running sudo update-grub2 do to change the shut down behaviour?

Update. If you run update-grub2 then mythbuntu then shut down it hangs. If you run mythbuntu then update-grub2 it shuts down correctly. Looks like update-grub2 has to be just before shut down.  Will investigate further.  

My conclusion is that running update-grub2 just prior to shut down always works. After some google searches I found that others have also found this solution (not unsurprisingly). So the question for the development team is "what does update-grub2 do that fixes this problem?"

Another update. I've found that it you set "Automatically save session on logout" in Settings->Session and Startup to "yes" (this is for mythbuntu using Xfce) then the system shuts down to power off correctly, no need to run update-grub2.  Another hint as to the problem?

---

### Post by lz1dsb on 2012-03-09
Thank you for this interesting information tobiz!
I just checked it out on my system (Ubuntu 11.10 64-bit). Each time when I execute "update-grub2" prior to a shutdown, it works as expected. It's quite strange really. This needs to be investigated further. 
Another test I also did is to log in not in into the normal Unity 3D session but into Unity 2D. Each time I log into Unity 2D the shutdown just works! Hm... Quite strange indeed. 
At least for now I have a workaround, even though it's quite awkward...

---

### Post by tobiz on 2012-03-09
lz1dsb, did you try the "Save session on logout" alternative? I don't know how you do this in Unity but it should be possible somehow I guess; using update-grub2 is a pretty nasty work around.

---

### Post by lz1dsb on 2012-03-10
You're right. But I have to figure out whether in Unity DE I have this option...

---

### Post by lz1dsb on 2012-03-10
Today I've upgraded the kernel to 3.0.0-16.28
I've done few restarts and shutdowns and there was no issue. I'm getting the splash screen and than a normal shutdown or restart. 
I'll monitor this for the next week to see if this update really has solved it...


Regards,
Boyan

---

### Post by abdulmajid on 2012-03-12
I am using Ubuntu 11.10 Linux Kernel version 3.0.0-16-generic. My computer software is up-to-date. And I still face the same issue...it is taking 45-50 seconds to shutdown....:(

Any help would me much appreciated.

```
sudo mv /etc/rc6.d/S35networking /etc/rc6.d/S15networking
sudo mv /etc/rc0.d/S35networking /etc/rc0.d/S15networking

```
Didn't work for me...

---

### Post by robotics on 2012-03-14
```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi=force"
GRUB_CMDLINE_LINUX="quiet splash acpi=force"
```

This worked perfectly! After adding the lines, and after the forced shut-down, it works if I restart or shut-down. Thanks!

---

### Post by thietkelogo on 2012-03-14
I also found the same proble, it got stuck in the ubuntu splash screen, never shuts down

---

### Post by abdulmajid on 2012-03-14
Nothing works for me....neither editing grub file nor the renaming of the networking scripts...:(

---

### Post by robotics on 2012-03-14
did you restart ubuntu twice keeping the same configuration?

---

### Post by abdulmajid on 2012-03-14
Yes, I tried restarting multiple times...it took 50 seconds every time I shut down the computer.

---

### Post by haresear on 2012-03-14
I've had this problem at random times. One thing that has always worked for me is to shutdown via command line.
```
sudo shutdown -h now
```

Of course you can't use this if the computer is frozen, so you have to use it instead of a GUI shutdown.

---

### Post by abdulmajid on 2012-03-14
I've tried everything...nothing works. :(

---

### Post by haresear on 2012-03-14
> **abdulmajid said:**
> I've tried everything...nothing works. :(

Have you tried bringing up a single-user console session using CTL+ALT+F1, then issuing the shutdown command? Is it U11.10 that is exhibiting the problem, or U10.10?

---

### Post by abdulmajid on 2012-03-14
> **haresear said:**
> Have you tried bringing up a single-user console session using CTL+ALT+F1, then issuing the shutdown command? Is it U11.10 that is exhibiting the problem, or U10.10?
Yes, I've tried that. It's not working either. I am using Ubuntu 11.10. laptop (Toshiba Satellite) takes unusually long time to shut down, about 50 seconds.

---

### Post by vagrant4ever on 2012-03-29
The solution below worked for myself! Thanks!
```

GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi=force"
GRUB_CMDLINE_LINUX="quiet splash acpi=force"
```

---

### Post by travisf on 2012-04-01
I've been searching and trying for days and I think I've tried most solutions offered to get my Acer TM8743T to shutdown or reboot. I'm going to use the laptop as a server because it only uses about 10w when idling so I replaced 11.10 and installed 12.04 server (no desktop) and it has the same problem.

As a last resort I tried the latest mainline kernel and would you believe shutdown and reboot works flawlessly. Only problem is mysql refuses to start so I'm stuck with the standard kernel for the time being.

---

### Post by Alex.Pi on 2012-04-04
Hi,

Nothing worked for me: Ubunut 11.10, kernel version 3.0.0-17-generic-pae

The only temporary solution which works well is "sudo halt -p" or the stronger one "sudo halt -fp", for rebooting: "sudo reboot --force".

---

### Post by fraditi on 2012-04-05
Hi,

since update to 11.10 shutdown only with: "sudo shutdown -P now".
I updated to 12.04, still the same.
Thinkpad Edge 11
uname -a:
3.2.0-21-generic #34-Ubuntu SMP Thu Mar 29 22:13:29 UTC 2012 i686 athlon i386 GNU/Linux
What can I do?
Are there any logs, which show something?

fraditi

---

### Post by Alex.Pi on 2012-04-05
Hi,

I did not have this problem after upgrading to 11.10 but after some time it appeared. The solution for me was simple. The Session Management plugin in Compiz -> Utilities was switched on. I just disabled it and the problem gone.
Again Compiz...
Hope it will help to the others.

Success!

---

### Post by Mac Boy on 2012-04-06
> **Alex.Pi said:**
> Hi,

I did not have this problem after upgrading to 11.10 but after some time it appeared. The solution for me was simple. The Session Management plugin in Compiz -> Utilities was switched on. I just disabled it and the problem gone.
Again Compiz...
Hope it will help to the others.

Success!

This didn't work for me but I have left the settings as recommended, the following link did fix my problem:
[https://bugs.launchpad.net/ubuntu/+source/netbase/+bug/903825](https://bugs.launchpad.net/ubuntu/+source/netbase/+bug/903825)

[I][B]" When the system is shutting down, it executes the scripts located in /etc/rc0.d (or /etc/rc6.d if it is restarting). When executes S20sendsigs it sleeps 10 seconds to wait for the Upstart Jobs (located in /etc/init) terminate. But these jobs NEVER terminate.

Why?

They are waiting to receive the event "deconfiguring-networking", but the script who emits this event is "S35networking". It executes after S20sendsigs, so the upstart jobs NEVER receives this event.

The solution:

I renamed the links in /etc/rc0.d and rc6.d:

- S31umountnfs.sh to S05umountnfs.sh
- S35networking to S15networking "[/B][/I]

I hope this can help some more people.

---

### Post by megabuffen on 2012-04-10
I've tried editing /etc/default/grub, but it doesn't make any difference. Shutting down using the GUI works, but "sudo halt" doesn't. Rebooting always works. I've noticed that when i use the command line to shut down, i get the message "Will now halt" and then "System halted". I also hear the hard drives turn off.

Is this a kernel problem? Why does it make a difference if i use the GUI?

---

### Post by Beanmonster on 2012-04-15
> **Mac Boy said:**
> 
[https://bugs.launchpad.net/ubuntu/+source/netbase/+bug/903825](https://bugs.launchpad.net/ubuntu/+source/netbase/+bug/903825)[I][B]

The solution:

I renamed the links in /etc/rc0.d and rc6.d:

- S31umountnfs.sh to S05umountnfs.sh
- S35networking to S15networking "[/B][/I]

I hope this can help some more people.

That definitely helped me, Thanks!! :p

---

### Post by skiingisbelieving on 2012-04-23
I am running a Dell Studio 15 laptop that dualboots into either Windows 7 or Ubuntu 11.10. This shutdown issue began for me, as it did for many of you, when I upgraded from 11.04.

My kernel is 3.0.0-17-generic-pae.

I tried the suggested edits to /etc/rc0.d and /etc/rc6.d

> Originally Posted by Mac Boy  
[https://bugs.launchpad.net/ubuntu/+s...se/+bug/903825](https://bugs.launchpad.net/ubuntu/+s...se/+bug/903825)

The solution:

I renamed the links in /etc/rc0.d and rc6.d:

- S31umountnfs.sh to S05umountnfs.sh
- S35networking to S15networking "

I hope this can help some more people.

At first, this solved the problem completely, whether I booted into Unity or GNOME.

After a few boot / shutdown / restart cycles, however, the problem has returned. I now cannot shutdown or restart.

Also, the command ```
sudo shutdown -P now
``` no longer works at all. When I enter the shutdown command, the system hangs. Ctrl+C does not kill the shutdown. But if I manually close the Terminal window, the system returns to normal.

Anyone else having any similar issues after editing /etc/rc0.d and /rc6.d?

Thanks.

---

### Post by skiingisbelieving on 2012-04-24
I think we may have isolated the problem.

My /etc/rc0.d and /etc/rc6.d directories both contain the following sub-directories. Please note that the bold entries have been edited, as per the instructions posted by MacBoy:

K74bluetooth
README
**S05umountnfs.sh**
S10unattended-upgrades
**S15networking**
S20sendsigs
S30urandom
S40umountfs
S60umountroot
S90reboot

When I first made these edits, it solved the problem. The problem returned, however, within a few shutdown / reboot cycles, even though the changes were still changed. So here's what I did:

1) I manually turned my computer off, turned it back on, and logged back in.

2) I then navigated to /etc/rc0.d and /etc/rc6.d and **undid my edits**, and then **made the same edits again.**

3) I then rebooted. Reboot worked fine.

For some reason, it would appear that making these edits to /rc0.d (for shutdown) and /rc6.d (for reboot) **just prior** to shutting down or rebooting will allow the process to work normally. But apparently that means the contents of /rc0.d and /rc6.d are being automatically reverted, causing the problem to reappear unless you manually make the changes.

Figuring out why this occurs is beyond my ability level. Anyone else have any ideas?

---

### Post by lz1dsb on 2012-05-18
For anyone interested. I installed the ATI Catalyst driver about a week ago and the shutdown/restart issue seems to be solved for me. I've downloaded the driver from the AMD site and followed the instructions listed on that site:
[http://www.hecticgeek.com/2011/10/how-to-install-atiamd-catalyst-linux-driver-11-9-in-ubuntu-11-10-oneiric-ocelot/](http://www.hecticgeek.com/2011/10/how-to-install-atiamd-catalyst-linux-driver-11-9-in-ubuntu-11-10-oneiric-ocelot/)

Since I installed that driver (I don't know what exactly the difference is from the FGLRX version I'm offered directly from the Additional Drivers app in Ubuntu) it seems stable. I haven't got any issues with shutdown and restart. At least for now :p


Regards,
Boyan

---

### Post by The_Cougar_Kid on 2012-05-18
> **Jary316 said:**
> Hi everyone,

I updated my machine from Ubuntu 11.04 to 11.10. Now when I try to 'shutdown' from the menu, I get to the dark Ubuntu screen with 4 white dots. Nothing seems to happen, the hard disk does not do any work, it just stalls there.

I am not sure what I should do. I've had to press the power button to completely turn it off.

Any suggestions please?

Thank you very much.
I have UBUNTU running on 4 computers in our house - all dual boot with a version of WINDOWS.  All recently upgraded to 12.04 via 11.10.  3 of them are fine, but my wife's machine suffers from the 'refuse to shutdown' problem.  Her machine gets stuck at the four dots with this message:
Plymouthd ply-terminal.c:630 Ply_terminal_set_mode: Assertion 'Terminal!=((void*)) failed
I Googled this message and found that it is a recognised bug that has been reported but with only medium priority.  If it is causing this refusal to shutdown issue shouldn't it have a high priority?

---

### Post by war59312 on 2012-05-25
Well I am having this problem now too.

Started after having upgraded from Ubuntu 11.04 to Ubuntu 11.10 and then onto Ubuntu 12.04.

Very annoying and none of the "fixes" in this thread have made any difference.

Crazy how bugs like this make it into "stable" releases.

---

### Post by fotis_utmost on 2012-05-28
The same here. I'm also having this problem. It's really frustrating...

---

### Post by Sigma1 on 2012-06-22
Same here, with 12.04 on an Acer, and none of the fixes appears to work so far. The only thing that does seem to make a difference is logging out before powering down (or powering down via a terminal). Is there any way this can be done automatically?
Thanks in advance!

---

### Post by tobiz on 2012-06-22
I eventually found a solution to this problem for my mythtv 11.10 system that has worked 100% for me.  The problem is the network is not shutting down, this is solved by running sudo sh -c "/etc/init.d/networking stop" in the shut down sequence.  I run this as part of checklogin.sh which is a mythtv script used to control shut down so it can be woken by the RTC alarm for a TV recording. I suggest putting this in the shut down sequence for a non-mythtv system and see what happens.

---

### Post by Sigma1 on 2012-06-23
Thanks a lot for your last, tobiz. Like you, I'm pretty sure it's a networking issue, but can anyone tell me how to include this in a shutdown sequence script without having to go via a terminal? There does not appear to be a checklogin.sh file on the machine I'm using (now with 12.04).
Help appreciated, as ever.

---

### Post by tobiz on 2012-06-23
Sigma1, checklogin.sh is a (mythtv) optional user addition to mythtv so I wouldn't expect you to find it. I guess it could be included in a 'Kill' run level script, ie /etc/rc?.d but not sure how or where is best, /etc/rc0.d/s90halt perhaps?

---

### Post by Sigma1 on 2012-06-23
> **tobiz said:**
> Sigma1, checklogin.sh is a (mythtv) optional user addition to mythtv so I wouldn't expect you to find it. I guess it could be included in a 'Kill' run level script, ie /etc/rc?.d but not sure how or where is best, /etc/rc0.d/s90halt perhaps?

Thanks tobiz, for following this up. I did try including your snippet ```
sudo sh -c "/etc/init.d/networking stop"
``` inside a script in /etc/init.d/ and updating with something like ```
update-rc.d -f myscript.sh stop 6 .
``` but to no avail, unfortunately.

Perhaps I'd be better off including it inside s90halt as you suggest. Thanks again for your advice.

---

### Post by Sigma1 on 2012-06-23
I'm wondering, would commenting out this bit in /etc/rc0.d/S90halt help? 
```
	# Make it possible to not shut down network interfaces,
	# needed to use wake-on-lan
	netdown="-i"
	if [ "$NETDOWN" = "no" ]; then
		netdown=""
	fi
```
I'll try it when I can and report back.

---

