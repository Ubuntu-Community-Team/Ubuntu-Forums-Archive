---
title: "Another kernel???? what"
date: 2009-08-06
forum: General Help
---

### Post by DarinB on 2009-08-06
I have been with ubuntu since, feisty, 
that worked like gold, now i am up to jaunty, 
but whats up with all the kernel releases i never had that with any of the other versions.
my boot menu is getting kind of long. and i still dual boot with vista (yuck) but i have to keep it for one or two apps. 
well i have had more issues with jaunty that with feisty, and it seems that each version has more bugs than the last one. whats up with this. Id the Dev team biting off more than it can chew????? 
sorry if this belongs on a different part of the forum.

---

### Post by Warren Watts on 2009-08-06
> **DarinB said:**
> ..my boot menu is getting kind of long

You can always edit **/boot/grub/menu.lst** and edit or remark out the older kernel listings.

I know this isn't any sort of answer to your question, but it will keep the size of your boot menu under control.

---

### Post by FuturePilot on 2009-08-06
> **Warren Watts said:**
> You can always edit **/boot/grub/menu.lst** and edit or remark out the older kernel listings.

I know this isn't any sort of answer to your question, but it will keep the size of your boot menu under control.

Why do that when you can just uninstall the old ones?

---

### Post by JawsThemeSwimming428 on 2009-08-06
> **FuturePilot said:**
> Why do that when you can just uninstall the old ones?

How do you do that?

---

### Post by kevdog on 2009-08-06
Just delete the old kernels -- but remember -- newer isn't always better

---

### Post by FuturePilot on 2009-08-06
> **JawsThemeSwimming428 said:**
> How do you do that?

Go into Synaptic and mark the old ones for removal. That is, if the new one works fine for you.

---

### Post by shazbut on 2009-08-06
Or you can use startup-manager to limit the number of kernels listed.
```
sudo apt-get install startupmanager
```
then run it from system-> administration

---

### Post by Warren Watts on 2009-08-07
> **FuturePilot said:**
> Why do that when you can just uninstall the old ones?

Will uninstalling the previous kernels remove them from ***menu.lst*** as well?

---

### Post by windows-killer on 2009-08-07
> **JawsThemeSwimming428 said:**
> How do you do that?

download *startup manager* from synaptic or add remove programs and there should be a "limit the number of kernels" put a limit and done!

---

### Post by cariboo on 2009-08-07
> **Warren Watts said:**
> Will uninstalling the previous kernels remove them from ***menu.lst*** as well?

Yes, removing extra kernels will also remove them from /boot/grub/menu.lst You have to use Synaptic, Add/Remove or apt-get in order for this to work.

---

### Post by DarinB on 2009-08-07
1. please explain how to remove only the old ones via synaptic
2. is that what i should do???
3. what are the possible problems???
4. why so many kernel upgrades and why is this release so much more buggy that feisty????? they seem to be getting worse not better???????

---

### Post by martinbaselier on 2009-08-07
1. please explain how to remove only the old ones via synaptic
2. is that what i should do???
3. what are the possible problems???
4. why so many kernel upgrades and why is this release so much more buggy that feisty????? they seem to be getting worse not better???????

1. Click somewhere in the list and then type linux-image in synaptic, this will bring you to the kernels.

2. This would be the best, since you don't use them anyway. Each kernel takes about 100MB of space. 

3. Always keep a few kernels installed so you have one to revert to as a backup.

4. If you've never removed your old kernels, you probably have all the kernels that came out from feisty till jaunty. Jaunty is working flawlessly on my machine. If you say it's buggier, than please provide proof/examples which actually point to the kernel and not to other stuff installed. If an older kernel works better for you, you can just use it instead. 

Kernel modules provide hardware support. Since there is constantly coming out new hardware, the kernel needs to change too. Plus the old modules are improved, to provide better support.

---

### Post by kpkeerthi on 2009-08-07
[http://tombuntu.com/index.php/2007/10/17/remove-ubuntu-kernels-you-dont-need/]("http://tombuntu.com/index.php/2007/10/17/remove-ubuntu-kernels-you-dont-need/")

---

### Post by DarinB on 2009-08-07
Thanks kpkeerthi that is exactly what i was looking for. funny how sometimes you can't find easy instruction. it worked great i removed the two oldest and left the two newest. And with startup manager i spruced up the screen, lol (really, not important to me)
Thanks Again folks

---

