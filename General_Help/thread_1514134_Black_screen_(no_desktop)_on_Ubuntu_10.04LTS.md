---
title: "Black screen (no desktop) on Ubuntu 10.04LTS"
date: 2010-06-20
forum: General Help
---

### Post by ep1centre on 2010-06-20
I've already got a little bit of help on another similar thread however it appears the problem's unrelated so i dont want to clutter someone else's thread with my problem, here's the description and the help i got so far!


> **ep1centre said:**
> I too am having the same sort of problem, the  computer was working fine last night, when i woke up this morning (i  leave it on) it was making strange noises through the speakers and i had  a blank screen, restarted a few times had some page full of code and  wouldnt move on from there, i went out came back started it up and it  did everything normally exept instead of a desktop i had a black screen,  however strangely enough when i press the power button on the PC a shut  down menu comes up, and the mouse works and i can select from the  options.

I am on an Nvidia ION tho...

how do i boot into a safe mode as such? as at the moment i'm using a  ubuntu live CD to read the forums!

> **jxtreme said:**
> On the GRUB menu, seclect "Ubuntu (recovery  mode)" (not exact wording). You'll get scrolling boot messages until you  get to a screen with a grey box and some options. Use the arrow keys to  select "x failsafe graphics mode" or something of the like. Press enter  and you'll probably get a message that your card can't be detected or  something. Press okay and continue. Your screen will be messed up, but  you'll be in.

It probably isn't the same problem, as you don't have an ATI card and  can see a shutdown menu, but good Luck!

> **ep1centre said:**
> How do you bring up the GRUB menu? My PC isnt  dual booted so i never see any menus at all, i thought all i had to do  was press F8 during boot up?

> **jxtreme said:**
> No, F8 is Windows. Hold down shift when booting  to see the menu.

EDIT: Downloaded & Installed the 10.6 driver and everything is  working fine. Unminimizing apps works much faster with this driver :D. However,  /usr/bin/aticonfig --initial results in 
```
Found fglrx primary device section
Using /etc/X11/xorg.conf
Saved back-up to /etc/X11/xorg.conf.fglrx-2
/usr/bin/aticonfig: Writing to '/etc/X11/xorg.conf' failed. Bad file  descriptor.

``` However, this doesn't seem to affect anything. Problem solved. :cool:


I'm sorry about some of the unrelated chat there as like i said it was someone else's help thread, right now i've tried what "jxtreme" suggested on quote nr2 however when i go into recovery mode i get a load of code scrolling through the screen as its supposed to but i never get any box with options as he says, it just gets to a point where theres a small white cursor flashing at me half way down the screen and it stays there... 

Can any one shine some light on this please, I'm in urgent need of using my computer!

Thank you.

---

### Post by davidmohammed on 2010-06-20
is this a brand new install or an upgrade?

have you tried booting with nomodeset or acpi=off or noacpi or noapic (you could use one or more of those) in your grub?

(press shift on boot to display the list of kernels - your grub.  Press e to edit.  Find the line with quiet splash.  Add one or more of the above options immediately BEFORE quiet splash e.g. ... nomodeset noapic quiet splash -- and then boot)

---

### Post by ep1centre on 2010-06-20
Well i've been running it for a few months but it was installed from scratch ie a 10.04 LTS fresh install not an upgrade from 9.xx.

i haven't tried what you mentioned yet, but i'm going to now...

i'll report back asap 20 mins or so as it takes ages to load the live CD each time... i have no access to another computer at the moment :(

---

### Post by ep1centre on 2010-06-20
Ok i added those lines like you said which allowed me to boot into failsafe mode which i then used the failsafe graphics option i went through the options chosing the "default graphics mode" but that didnt do anything other than the "shut down menu" i mention earlyer that comes up when i press the power button on the PC now looks ridiculously big, still had the same issue!

So i then decided to restart it again going through the same steps but now when i got to the menu in recovery mode i chose "repair broken packages" so it went ahead and did its business, and it now seems to work however my screen rez its all messed up and the "effects" are all off, is it a matter of just turning it all back on or should i be wary of it going wrong again? 

Anyway thank you very much for your help!



Edit: i just risked enabling the desktop effects and away it goes "searching for available drivers" and then it just says "desktop effects cannot be enabled" the nvidia drivers are still enabled and installed any ideas?

---

### Post by davidmohammed on 2010-06-20
since you said that this is a fresh install, but you had to go through and do a repair, I don't think the install was fully successful.  


I would repeat the install again (erasing your entire disk during partioning) to make sure you've got a successful install.

---

### Post by ep1centre on 2010-06-20
it was fresh (ie not an "upgrade" from a previous ubuntu install") but i've been using it for months now and i have all my programs and files on the computer so if i could get away without reinstalling it it would be nice!

---

### Post by wojox on 2010-06-20
Can you boot into the purple options screen. Press F6 and choose nomoeset with spacebar.

---

### Post by ep1centre on 2010-06-20
not sure what the "purple options screen is" sorry can you be a little more specific?

Thanks.

---

### Post by davidmohammed on 2010-06-20
try the following to reinstall you nvidia graphics.

in a terminal do the following (copy and paste the text below)


```
sudo aptitude install build-essential
```
uninstall any and all nvidia components installed.


```
sudo apt-get purge nvidia*
```
Next we need to blacklist “nouveau”. 


```
gksudo gedit /etc/modprobe.d/blacklist.conf
```
add the following text to this file.


```
blacklist nouveau
```
Next ,install the latest official stable driver from the repository


```
sudo apt-get install nvidia-current
```
Next we’ll load the Nvidia kernel module


```
sudo modprobe nvidia-current
```
Verify it’s successful entry via lsmod like so


```
sudo lsmod | grep -i nvidia
```
And one last step, we must create the Nvidia configuration file.


```
sudo nvidia-xconfig
```

---

### Post by wojox on 2010-06-20
Sorry nevermind I see you got it to boot.

---

### Post by ep1centre on 2010-06-20
Ok David, i followed your instructions, it all went well untill i got to 

sudo modprobe nvidia-current

when i typed it in and pressed enter, nothing happened i just got the prompt again... i tryied it twice and i had the same result so i moved on, the output from 

sudo lsmod | grep -i nvidia

was:

[COLOR=Black]nvidia  [/COLOR]             9962496  0 
agpgart                31788  3 ttm,drm,[COLOR=Red]nvidia[/COLOR]

and then the output from

sudo nvidia-xconfig

was:

WARNING: Unable to locate/open X configuration file.

New X configuration file written to '/etc/X11/xorg.conf'




Any thoughts, is that what's soposed to happen or did something go wrong?

---

### Post by davidmohammed on 2010-06-20
that looks ok - what happens when you reboot (remembering to add those boot options...)?

---

### Post by ep1centre on 2010-06-20
reboot and do this again, is that what you refering to when you said "by adding those options"?

> **davidmohammed said:**
> is this a brand new install or an upgrade?

have you tried booting with nomodeset or acpi=off or noacpi or noapic  (you could use one or more of those) in your grub?

(press shift on boot to display the list of kernels - your grub.  Press e  to edit.  Find the line with quiet splash.  Add one or more of the  above options immediately BEFORE quiet splash e.g. ... nomodeset noapic  quiet splash -- and then boot)

---

### Post by davidmohammed on 2010-06-20
yes - whatever options you had to do to get to your desktop previously.

---

### Post by wojox on 2010-06-20
It created a default xorg file. Reboot and open a terminal and type

gksudo nvidia-settings

---

### Post by ep1centre on 2010-06-20
i think i'll try rebooting without any "options" at the moment as i beleive it wasn't the "options" that sorted the desktop problem out but the "repair broken packages" that did it! 

i'll report back in a min.

---

### Post by ep1centre on 2010-06-20
everything seems perfect at the moment, computer seems quite snappy as well... what exactly did you get me to do? i gathered i basicly reinstalled the Nvidia drivers but... was it any particular version you got me to install also any strange tricks that improved performance? 

sorry i'm not that clued up on linux things - getting there though.

---

### Post by davidmohammed on 2010-06-20
you got it - yes just clean out the old configuration and reinstall from scratch.  Glad things have worked.

Don't forget to mark the thread as solved when happy.

---

### Post by ep1centre on 2010-06-20
Thank you for all your help!

---

