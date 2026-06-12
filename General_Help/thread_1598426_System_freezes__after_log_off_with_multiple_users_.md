---
title: "System freezes  after log off with multiple users logged in"
date: 2010-10-16
forum: General Help
---

### Post by faflu on 2010-10-16
Hi,

I have the following reproducible issue:
On Ubuntu 10.04 when there are more than just one user logged in, if one of users logs off system hangs with a black screen.
After I reboot the machine and log in again, just after GDM login screen I get a window with a message about PowerMeter crash, with suggestion to 'cancel' and 'log off'. Only 'Log off' works, i.e. I'm successfully logged in.
Last entries from system.log before system freeze are:
```
Oct 16 19:50:45 desktop console-kit-daemon[858]: WARNING: Couldn't read /proc/2196/environ: Failed to open file '/proc/2196/environ': No such file or directory
Oct 16 19:50:46 desktop gdm-simple-slave[3750]: WARNING: Unable to load file '/etc/gdm/custom.conf': No such file or directory
Oct 16 19:50:46 desktop acpid: client 2880[0:0] has disconnected
Oct 16 19:50:46 desktop acpid: client 951[0:0] has disconnected
Oct 16 19:50:46 desktop acpid: client connected from 3752[0:0]
Oct 16 19:50:46 desktop acpid: 1 client rule loaded
```
Any one with similar problem, and/or solution?

---

### Post by dougalkerr on 2010-10-16
Have you tried uninstalling or updating Power Meter? and then rebooting.

---

### Post by faflu on 2010-10-16
Hi,

Good hint but it didn't work. I uninstalled pm-utils, as there's no Power Meter, but gnome-power-manager (I misremembered names). I will not uninstall g-p-m, as I would have to uninstall ubuntu-desktop too. It's not the thing I would like to get rid of. I will reinstall g-p-m and let you know the results.

---

### Post by faflu on 2010-10-16
Well, no it didn't help. Still freezing dead at log out

---

### Post by DOS286 on 2010-10-20
I'm experiencing similar symptoms except that the reboot is normal with no error messages. It is reproducible. It happens every time multiple users are logged in and one logs out. I am also having the random freeze issue discussed ad nauseum with no solutions here:
[http://ubuntuforums.org/showthread.php?t=1478787](http://ubuntuforums.org/showthread.php?t=1478787)
but I have not been able to predict/reproduce those freezes.

Any updates to your situation?

---

### Post by faflu on 2010-10-21
Nothing has changed. But I can see I'm lucky to have only this freeze. As it's predictable, I don't switch users, just log off and log in as different user. The truth is also that I don't have much time to investigate this issue.

---

### Post by richfeat on 2010-11-06
I have had this problem since updating to Lucid (via clean installs) on 3 machines. 2 are Athlon and Sempron desktops, and the other is an Intel based laptop. But all have Nvidia graphics with Nvidia drivers. I have not dared to update 2 other machines from Hardy. If a user tries to log out while another user is logged in, the screen blanks and the system then fails to respond to keyboard or mouse. This is a repeatable fault. I can log in via a network connection to reboot the machine, but I have not found consistent messages in the logs to tie down what is happening. X appears to be still running, but as described above it is not responding. Using the old-school method of switching user, issuing a ALT-CNTRL-F7 or F8, gives similar, though sometimes delayed-action results.
Similar problems have been reported in the Forums and as bugs (what do I report a bug in?) but no solutions have been proposed. I have not tried Maverick, but I suspect it would be the same.
I have been an Ubuntu advocate for some time. I have a small business and a large family running on it. But I really cannot recommend it any longer. This is an LTS release showing regressive show-stopping faults in basic Linux functionality. Faults which have not been fixed 6 months after initial release. They are causing real pain for my users, and I really have no confidence the fault will ever be fixed in Lucid. It looks like multi-user capability is now lost to Ubuntu.
So where do we go? 
Xnest or Xephyr running gnome-session is one rather clumsy work-round, but this is spitting out a lot of nasty looking error messages. 
NXclient attached to neatx-server on localhost is OK but a bit slow. 
Or is there a distro that doesn't suffer from crippling regressions in basic functionality? Any suggestions? I would be happy to give up Ubuntu One, which is so unreliable as to be positively dangerous.

---

### Post by faflu on 2010-11-09
After an upgrade to Maverick the issue is away. The other thing is that I no longer use nv driver from nvidia but nouveau instead (it's not supported by recent kernel)- perhaps that was the reason...

---

### Post by richfeat on 2010-11-12
After googling for nvidia drivers with lucid, I found this thread: [http://ubuntuforums.org/showthread.php?t=1569894](http://ubuntuforums.org/showthread.php?t=1569894)
which was very helpful.
For the card in my main desktop, the comments on the Nvidia site concerning the latest driver update are:
"Fixed a bug that caused X server crashes when certain rendering occurred. This was triggered by the Ubuntu 10.04 GDM login theme. Fixes Launchpad bug #553200.
Fixed a bug that could cause X.Org xserver >= 1.7 to hang when restarted."
I have installed the latest drivers from the Nvidia site on 2 desktops, and all seems to be OK at last. Unfortunately the video on my laptop is too old to get any Nvidia updates, so I'm still stuck with that.

---

### Post by richfeat on 2010-11-15
After 1 working day with system apparently working OK:
2 X sessions. User 2 browsing using Firefox.
Then a spontaneous switch-out to the gdm greeter, leaving User 2 still logged in. But User 1 has been logged off, hosing the session. So the predictable Log Off with multiple users has been fixed, but the random? session crash has not.
As I asked before, where from here?

---

### Post by hansheijmans on 2011-01-07
Hi, same problem here with ATI Radeon X300 video card, see my lshw:

```
           *-display:0
                description: VGA compatible controller
                product: RV370 5B60 [Radeon X300 (PCIE)]
                vendor: ATI Technologies Inc
                physical id: 0
                bus info: pci@0000:04:00.0
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: pm pciexpress msi vga_controller bus_master cap_list rom
                configuration: driver=radeon latency=0
                resources: irq:44 memory:d8000000-dfffffff ioport:e000(size=256) memory:d7fe0000-d7feffff memory:d7fc0000-d7fdffff

```Logging off with another user still logged on produces a freeze (black screen, unable to switch to tty1, 2 etc). Machine is not dead, but still controllable via ssh or NX.

Any suggestions?

---

### Post by hansheijmans on 2011-01-10
Would installing fglrx be an option?

---

### Post by hansheijmans on 2011-02-02
Anyone?

---

### Post by hansheijmans on 2011-03-31
Isn't there anyone ????

---

### Post by woodensoul on 2011-04-09
I get the same lockup problem when switching users or logging off one user while another is logged in.  One change from the screen just going black - My display goes crazy and strange colors appear and the display starts to fade away.  I can restart using the REISUB key combination.

This is the behavior most of the time but I was able to get it to work properly for a time without doing any fixes.  Here's what I did: When the screen goes crazy with fading random colors, I closed the laptop screen and left it alone for 5 minutes.  When I came back the screen was normal again.  I haven't tried this repeatedly to see if it repeatable yet.  

It sure would be nice if there was a good fix for this issue.  It makes multi-user use virtually impossible.

---

### Post by faflu on 2011-04-09
My problem has gone for good in 10.10 after installing Nvidia Driver ver. 96.43.19

---

### Post by woodensoul on 2011-04-09
I have ATI Xpress 200M integrated graphics.  Is there a fix for ATI graphics?

---

### Post by matty abbo on 2011-04-09
> **faflu said:**
> 
I will not uninstall g-p-m, as I would have to uninstall ubuntu-desktop too.

you don't have to uninstall GDM to remove one of its features, you can uninstall features from it using synaptic:)

---

