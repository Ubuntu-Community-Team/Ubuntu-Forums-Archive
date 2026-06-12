---
title: "Problem with dpkg: 'sudo dpkg --configure -a' crashes."
date: 2009-08-08
forum: General Help
---

### Post by jonnybal@googlemail.com on 2009-08-08
This problem began after 'sudo apt-get install openoffice.org' crashed and I had to reboot.

The machine is a Dell Latitude C610 with 1GB of RAM running Ubuntu Studio 9.04 with kernel 2.6.28-3-rt

Gparted (run from a LiveCD) reports that the root partition has 4.22GiB unused and the /home partition has 8.78 GiB unused

However, Nautilus, (run from the installed distro) reports that the root partition has only 470.1MB free space and the /home partition has 8.5GB free space. I don't know why there is this discrepancy.
Strangely,  when I run the LiveCD and mount my root partition, Nautilus then reports that the root partition has 3.9GB free and the home partition has 8.5GB. I have made sure I am mounting the root partition on my hard-disk and that I am not looking at the liveCD root (which has 426.6MB free: presumably a RAM disk).

The sequence of actions I have tried is below

```
$ sudo apt-get -f install
E: dpkg was interrupted, you must manually run 'sudo dpgk --configure -a' to correct the problem.
$ sudo dpgk --configure -a
Setting up openoffice.org-emailmerge (1:3.0.1-9ubuntu3) ...
Adding extension /usr/lib/openoffice/basis3.0/program/mailmerge.py...
```At this point, the hard disk light appears to stop flashing, although if I look closely I see there is a regular tiny flash every  ~2.5 seconds and you can just hear the hard disk ticking in time with this, like a very very short disk access. The cursor in the terminal keeps flashing but nothing else appears to happen. If I try to start another application, the Gnome menu freezes and the desktop clock stops updating. However, the terminal still responds to [Ctrl] [c] as follows

```
dpkg: error processing openoffice.org-emailmerge (--configure): subprocess post-installation script killed by signal (Interrupt)
Setting up libwps-0.1-1 (0.1.2-1) ...
```Then it stops again.
Further presses of [Ctrl] [c] still show in the terminal but have no further effect.
The mouse still works and clicking the X in the top right corner of the terminal window produces a dialogue as follows

```
Close this window?
There is still a process running in this terminal. Closing the terminal will kill it.
```Pressing 'Cancel' dismisses this dialogue box.

When I press 'Close Terminal' the button stays depressed but nothing further happens. Pressing the X at the top right corner of the dialogue box depresses the symbol and releasing it releases it but again nothing further happens.

Now the only thing I can do is hit the power button. After rebooting the same cycle begins.

I have googled the phrase "ubuntu sudo dpkg --configure -a crashes" and found this forum thread [http://ubuntuforums.org/showthread.php?t=518991](http://ubuntuforums.org/showthread.php?t=518991)

Below is what I tried next.

```
$ sudo dpkg -l |grep openoffice.org
iU  openoffice.org                        1:3.0.1-9ubuntu3                     full-featured office productivity suite
iU  openoffice.org-base                   1:3.0.1-9ubuntu3                     full-featured office productivity suite -- d
iU  openoffice.org-base-core              1:3.0.1-9ubuntu3                     full-featured office productivity suite -- s
iU  openoffice.org-calc                   1:3.0.1-9ubuntu3                     full-featured office productivity suite -- s
ii  openoffice.org-common                 1:3.0.1-9ubuntu3                     full-featured office productivity suite -- a
ii  openoffice.org-core                   1:3.0.1-9ubuntu3                     full-featured office productivity suite -- a
iU  openoffice.org-draw                   1:3.0.1-9ubuntu3                     full-featured office productivity suite -- d
iF  openoffice.org-emailmerge             1:3.0.1-9ubuntu3                     full-featured office productivity suite -- e
iU  openoffice.org-filter-binfilter       1:3.0.1-9ubuntu3                     full-featured office productivity suite -- l
iU  openoffice.org-filter-mobiledev       1:3.0.1-9ubuntu3                     full-featured office productivity suite -- m
iU  openoffice.org-impress                1:3.0.1-9ubuntu3                     full-featured office productivity suite -- p
iU  openoffice.org-java-common            1:3.0.1-9ubuntu3                     full-featured office productivity suite -- a
iU  openoffice.org-math                   1:3.0.1-9ubuntu3                     full-featured office productivity suite -- e
iU  openoffice.org-officebean             1:3.0.1-9ubuntu3                     full-featured office productivity suite -- J
iU  openoffice.org-report-builder-bin     1:3.0.1-9ubuntu3                     OpenOffice.org extension for building databa
ii  openoffice.org-style-human            1:3.0.1-9ubuntu3                     Human symbol style for OpenOffice.org
iU  openoffice.org-writer                 1:3.0.1-9ubuntu3                     full-featured office productivity suite -- w
iU  openoffice.org-writer2latex           0.5-8ubuntu1                         Writer/Calc to LaTeX/XHTML converter extensi

$ sudo dpkg -r openoffice.org
(Reading database ... < I didn't copy this down unfortunately > files and directories currently installed.)
Removing openoffice.org
```This didn't remove everything, as I had hoped - just the meta-package.

```
$ sudo dpkg -r openoffice.org-emailmerge
(Reading database ... 151331 files and directories currently installed.)
Removing openoffice.org-emailmerge ...
```and there it hangs until I press [Ctrl] [c]

```
^Cdpkg: error processing openoffice.org-emailmerge (--remove):
subprocess pre-removal script killed by signal (Interrupt)
```Then I am back to the same place as before.

Is there something I am missing? What should I search for to stand a better chance of fixing this problem and getting my system working again so I can install packages again? Thanks for your consideration.

---

### Post by Soul-Sing on 2009-08-08
```
dpkg --remove --force-remove-reinstreq openoffice.org-emailmerge
```

---

### Post by jonnybal@googlemail.com on 2009-08-08
Thanks. Unfortunately, that hangs too.

---

### Post by Soul-Sing on 2009-08-08
> Setting up libwps-0.1-1 (0.1.2-1)

then it stops..

This should be the "hangman" I think. Google doesn't brought me any further on this.

---

### Post by Soul-Sing on 2009-08-08
Could you please tell us why you are installing openoffice? (because it comes by default with Ubuntu)
Is there a old version of it on your system?

---

### Post by jonnybal@googlemail.com on 2009-08-08
Because it didnt come installed on UbuntuStudio

---

### Post by Soul-Sing on 2009-08-08
You are not the only one having troubles installing openoffice on ubuntu studio. Launchpad and the openoffice forum do report many problems. No solution found though....

---

### Post by jonnybal@googlemail.com on 2009-08-11
Oh damn! Trouble is, now I can't install anything. I never had this problem with Ubuntu Studio Hardy so maybe I should wipe my system partition and install that.

---

### Post by skwhirl on 2009-08-27
I am in the same boat with openoffice. 

I was having the problem with mailmerge.py. Cleaning 'emailmerge' off as described above will get synaptic back in running order.

Later I ran apt-get and it felt a duty to continue installing 'writer2latex' from the openoffice package, and that hung the entire system.  

I'm now in the process of wiping out all openoffice files in 

/var/lib/dpkg/info/


To the other comment above, The complete Openoffice.org package was NOT installed in Jaunty 9.04, however only one component was available after the initial install. Trying to install the complete package fries the package manager.

---

### Post by jonnybal@googlemail.com on 2009-08-30
I will try deleting the files as mentioned above. I'm getting to the point where if that doesnt work I will probably reformat my root partition and just install UbuntuStudio 8.04
I had that working sometime in the past.

---

