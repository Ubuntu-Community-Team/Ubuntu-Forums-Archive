---
title: "zramswap snag"
date: 2012-06-05
forum: General Help
---

### Post by rjackson1969 on 2012-06-05
I'm not positive what initiated this problem but now anytime I try to upgrade or download updates or run my synaptic package manager or whatever in the terminal, I seem to run into this and it snags and hangs right there.[INDENT](Reading database ... 217483 files and directories currently installed.) 
Preparing to replace zramswap-enabler 0.2.1-0~19~precise1 (using .../zramswap-enabler_0.2.1-0~20~precise1_all.deb) ...
[/INDENT]Last thing I did before this was to install Miro. When I try to uninstall Miro, it snags there too. When I try to upgrade Miro to a newer version, it snags there.

Any ideas on how to repair?

---

### Post by rjackson1969 on 2012-06-05
The only way out of the hang is a reboot to force quit.

---

### Post by hypermodern on 2012-06-05
I have the exact same error.

---

### Post by chascon on 2012-06-05
I'm getting the same issue and I don't have Miro installed.

The way I got around the freezing of apt utilties was to kill off dpkg and then uninstall it, which gave me the freeze issue again. The second time trying to uninstall it worked like a charm.

I would uninstall it untill the zram folks can get it working properly. 

[INDENT]sudo killall -9 dpkg[/INDENT]

Any further attempts to use package utilties  should ask you to run the following to fix the state in which you left dpkg.

[INDENT]sudo dpkg --configure -a [/INDENT]

Then: 

[INDENT]wajig purge zramswap-enabler[/INDENT]


It'll still seem to get stuck. If you kill off dpkg again, from getting tired of waiting, make sure to run the purge command, just to make sure things are uninstalled.

Run thius again:
[INDENT]sudo dpkg --configure -a[/INDENT]

Then maybe run autoremove to remove unnecessary deps.

Someone should report the issue to what ever dev runs the corresponding ppa. I don't remember which ppa corresponds, but suffice to say it's not part of a default Ubuntu install, nor is it supported.

UPDATE
It's ppa:shnatsel/zram

---

### Post by traditionalist on 2012-06-05
You can try this;

[http://www.ubuntuupdates.org/package/core/precise/universe/base/zram-config](http://www.ubuntuupdates.org/package/core/precise/universe/base/zram-config)

it is still buggy and hard to remove. It grabbed 4 GB of my SSD, and I was unable  to change that  despite using a number of utilities. It has not caused any serious problems up to now, but I can't see any use for it on my machine and I don't want to lose 4 GB of space on my SSD to it. I am rather put out that it was installed as a default and without asking me.

There is no evidence to suggest that it is any use at all on a SSD.

So, you an remove it using "Disks"  utility. Just delete the swap partition on the SSD.

---

### Post by test666 on 2012-06-05
Update Manager got botched stalling zramswap-enabler update from zramswap-enabler_0.2.1-0~19~precise1_all.deb to 0~20.

Subsequently all this failed:
apt-get remove zramswap
apt-get install -f
apt-get autoclean
apt-get autoremove
synaptic
dpkg --configure -a

I then used the folowing long and fastidious method (overdetailed, newbie mode activated, beeing a newbie myself), to overcome this.

***********************************

note : < something > means a keyboard key ;-)

***********************************

pre-0 - Forgot this, I rebooted before doing this...

0 - Open a terminal:

0.1 - press simultaneously <control> <alt> <t>

or

0.2 - go through the menu for this step

1 - become root
sudo su <enter>
type_your_administrative_password <enter>

2 - stop zramswap-enabler, type
/etc/init.d/zramswap stop <enter>

3 - remove zramswap-enabler startup service
update-rc.d -f zramswap  remove <enter>

4 - Remove zramswap-enabler files, choose one of of the following two options:

4.1 - YOU ASSUME, BY CHOOSING THIS OPTION, THAT YOU FULLY UNDERTAND ALL ITS IMPLICATIONS; just remove all the zramswap* files, type
find / -type f -name "zramswap*" -exec rm -f {} \; <enter>

or

4.2 - ask for permission for every removal, type
find / -type f -name "zramswap*" -exec rm -i {} \; <enter>

5 - To be on the safe side

5.1 - type
apt-get autoremove <enter>

5.2 - type
apt-get autoclean <enter>

5.3 - probably not needed, but just in case, type
apt-get remove zramswap-enabler <enter>

6 - close terminal

7 - reboot

***********************************

Good luck.

---

### Post by skey. on 2012-06-06
Thanks guy's I have had the same problem all fixed
now All is good.

Cheers
Skey.

---

### Post by rjackson1969 on 2012-06-06
> **test666 said:**
> Update Manager got botched stalling zramswap-enabler update from zramswap-enabler_0.2.1-0~19~precise1_all.deb to 0~20.

Subsequently all this failed:
apt-get remove zramswap
apt-get install -f
apt-get autoclean
apt-get autoremove
synaptic
dpkg --configure -a

I then used the folowing long and fastidious method (overdetailed, newbie mode activated, beeing a newbie myself), to overcome this.

***********************************

note : < something > means a keyboard key ;-)

***********************************

pre-0 - Forgot this, I rebooted before doing this...

0 - Open a terminal:

0.1 - press simultaneously <control> <alt> <t>

or

0.2 - go through the menu for this step

1 - become root
sudo su <enter>
type_your_administrative_password <enter>

2 - stop zramswap-enabler, type
/etc/init.d/zramswap stop <enter>

3 - remove zramswap-enabler startup service
update-rc.d -f zramswap  remove <enter>

4 - Remove zramswap-enabler files, choose one of of the following two options:

4.1 - YOU ASSUME, BY CHOOSING THIS OPTION, THAT YOU FULLY UNDERTAND ALL ITS IMPLICATIONS; just remove all the zramswap* files, type
find / -type f -name "zramswap*" -exec rm -f {} \; <enter>

or

4.2 - ask for permission for every removal, type
find / -type f -name "zramswap*" -exec rm -i {} \; <enter>

5 - To be on the safe side

5.1 - type
apt-get autoremove <enter>

5.2 - type
apt-get autoclean <enter>

5.3 - probably not needed, but just in case, type
apt-get remove zramswap-enabler <enter>

6 - close terminal

7 - reboot

***********************************

Good luck.


Took a few tries but it seems to be working right now. Thanks.

---

### Post by hypermodern on 2012-06-06
I did it with sudo dpkg -r --force-remove-reinstreq zramswap-enabler it threw an error, then went xkill on the terminal. Rebooted 

sudo apt-get update
sudo apt-get upgrade -f
sudo dist-upgrade -f

Now things are back working again and I can update my system.

---

### Post by JamesRock7 on 2012-06-06
> **hypermodern said:**
> I did it with sudo dpkg -r --force-remove-reinstreq zramswap-enabler it threw an error, then went xkill on the terminal. Rebooted 

sudo apt-get update
sudo apt-get upgrade -f
sudo dist-upgrade -f

Now things are back working again and I can update my system.
Thanks a lot hypermodern! Your solution worked very fine.

---

### Post by rjackson1969 on 2012-06-06
> **rjackson1969 said:**
> Took a few tries but it seems to be working right now. Thanks.

Same here. This fix took a few tries but worked for me.

---

### Post by Shnatsel on 2012-06-07
I'm the author of that script I have a simpler solution ;)

running "sudo start zramswap" while the package is trying to upgrade lets it upgrade successfully. Don't ask why or how it works.

If the installation fails and the package is left in an inconsistent state, run "sudo dpkg --force-all --purge zramswap-enabler" and then you'll be able to install it cleanly.

These issues appear on upgrading from revisions 19 and 20; revision 21 should not suffer from this bug.

Revision 21 also sets the size of zramswap to 1/2 of RAM as it was supposed to be (this is the optimal configuration according to [http://code.google.com/p/compcache/wiki/Eeepc701](http://code.google.com/p/compcache/wiki/Eeepc701)). It was erroneously set to the size of RAM in previous versions.

---

### Post by thobu on 2012-06-07
> **Shnatsel said:**
> I'm the author of that script I have a simpler solution ;)

running "sudo zramswap start" while the package is trying to upgrade lets it upgrade successfully. Don't ask why or how it works.

If the installation fails and the package is left in an inconsistent state, run "sudo dpkg --force-all --purge zramswap-enabler" and then you'll be able to install it cleanly.

These issues appear on upgrading from revisions 19 and 20; revision 21 should not suffer from this bug.

Revision 21 also sets the size of zramswap to 1/2 of RAM as it was supposed to be (this is the optimal configuration according to [http://code.google.com/p/compcache/wiki/Eeepc701](http://code.google.com/p/compcache/wiki/Eeepc701)). It was erroneously set to the size of RAM in previous versions.
I get sudo: zramswap: command not found using zramswap start while tryin to replace via update. And sudo dpkg --force-all --purge zramswap-enabler stalls.
Any idea what to do?

---

### Post by draki on 2012-06-07
I think it should be > sudo *service* zramswap start

Seems to have worked for me

---

### Post by thobu on 2012-06-07
> **draki said:**
> I think it should be 

Seems to have worked for me
worked for me too - thanks!

---

### Post by Tatjanaen on 2012-06-08
> **Shnatsel said:**
> I'm the author of that script I have a simpler solution ;)

running "sudo zramswap start" while the package is trying to upgrade lets it upgrade successfully. Don't ask why or how it works.

If the installation fails and the package is left in an inconsistent state, run "sudo dpkg --force-all --purge zramswap-enabler" and then you'll be able to install it cleanly.

These issues appear on upgrading from revisions 19 and 20; revision 21 should not suffer from this bug.

Revision 21 also sets the size of zramswap to 1/2 of RAM as it was supposed to be (this is the optimal configuration according to [http://code.google.com/p/compcache/wiki/Eeepc701](http://code.google.com/p/compcache/wiki/Eeepc701)). It was erroneously set to the size of RAM in previous versions.

I had the exact same error again while it attempted to upgrade from revision 20 to 21, so hopefully this was due to the errors in the 20 revision.
My way of solving this was to enter the Grub boot menu, boot in recovery mode and repair broken packages. Doing that successfully updates zramswap-enabler (both when it crashed on the update from 19 to 20 and from 20 to 21). 
If it freezes again, I'll try the "sudo zramswap start"

---

### Post by Shnatsel on 2012-06-08
Should be "sudo start zramswap". Fixed in the original post. Sorry for the bug and for all this confusion.

---

### Post by kay65535 on 2012-07-02
> **Shnatsel said:**
> (...snip...)
Revision 21 also sets the size of zramswap to 1/2 of RAM as it was supposed to be (this is the optimal configuration according to [http://code.google.com/p/compcache/wiki/Eeepc701](http://code.google.com/p/compcache/wiki/Eeepc701)). It was erroneously set to the size of RAM in previous versions.

Hi. Revision 21 makes my netbook go really slow, and it works a lot better setting zramswap to 100% of RAM size (I've left a comment on the wiki page you refer to also with more details.)

I have currently fixed the situation by editting /etc/init/zramswap.conf and changeing the following line:

echo $((mem_total / 2 / num_cpus)) > /sys/block/zram$i/disksize

to:

echo $((mem_total / num_cpus)) > /sys/block/zram$i/disksize

That aside, good work!

---

