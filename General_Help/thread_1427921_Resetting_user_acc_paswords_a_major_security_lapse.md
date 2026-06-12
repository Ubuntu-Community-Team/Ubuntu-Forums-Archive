---
title: "Resetting user acc paswords a major security lapse"
date: 2010-03-12
forum: General Help
---

### Post by satish_j on 2010-03-12
Just came to know that it is possible to change the pwd of user accounts in Ubuntu through Recovery mode..Have read a lot of threads and blogs(and different views of users) on the usefulness/exploit of this feature,but,in my view,THIS IS THE MAJOR SECURITY HOLE IN UBUNTU/LINUX no matter what the experts say in its defence.
Now,that i know that this feature can anytime result in my accounting data leakage,can anyone tell me how do i disable recovery mode option to appear from grub menu that comes at boot time.I know it can be done by changing menu.lst file,but i dont know the exact steps/changes to be made in the file..
Also,in future,if i may need recovery option,how to edit the menu.lst on fly(i.e at grub menu)so as to boot into recovery mode for maintenance task..
If iam not wrong,Windows OS uses Safe mode as equivalent for Ubuntu recovery mode but there is no such stupid feature that enables anyone to change account passwords at will??
Any help seriously appreciated...

---

### Post by coffeecat on 2010-03-12
> **satish_j said:**
> THIS IS THE MAJOR SECURITY HOLE IN UBUNTU/LINUX

No more than in any OS. If you have physical access to the system, your security is compromised. PERIOD.

---

### Post by sdpiowa on 2010-03-12
It's just as easy to build a disk to change Windows passwords.  As said, physical access to the machine can do about anything.  Even without the password, anyone (in theory) can access all your files with a Live Disk (assuming they are not encrypted).

---

### Post by satish_j on 2010-03-12
> **coffeecat said:**
> No more than in any OS. If you have physical access to the system, your security is compromised. PERIOD.
You tell me if i have physical access to an XP machine(AND NOT THE BOOT CD/FLOPPY),can i change the admin pwd through safe mode???
I agree Live CD can compromise the security,but a person knowing the recovery mode trick can come empty-handed,enter some commands through recovery and change the pwd of the legitimate user..
This really is weird..
I just want to know how to customize grub menu to show only Ubuntu and XP OS AND NOT THE RECOVERY MODE OPTION..AND THEN(IF REQD IN FUTURE)TO ENTER RECOVERY MODE BY EDITING GRUB AT BOOT-UP TIME...Is it possible??

---

### Post by coffeecat on 2010-03-12
Here you go. Resetting the administrative password (major security lapses :-s) in:

[Windows]("http://pcsupport.about.com/od/toolsofthetrade/tp/passrecovery.htm")

[MacOS]("http://support.apple.com/kb/HT1274")

Note that it's actually Apple telling you how to do it for MacOS.

It took me about 2 minutes' googling to come up with those. A person wanting to maliciously log into someone's machine would probably know about them already.

**Edit:** just seen your second post. You'd be wasting your time editing the grub menu. A linux-savvy person would have a live CD to boot up with and could easily chroot into your system and change the password(s). Or steal your data. 

Sorry - whichever way you look at it, you have little or no security if there is physical access to the machine. Encrypting your personal data is about all you can do.

---

### Post by diesch on 2010-03-12
In */etc/default/grub* uncomment *GRUB_DISABLE_LINUX_RECOVERY="true"*

---

### Post by satish_j on 2010-03-12
> **coffeecat said:**
> You'd be wasting your time editing the grub menu. A linux-savvy person would have a live CD to boot up with and could easily chroot into your system and change the password(s). Or steal your data. 

Sorry - whichever way you look at it, you have little or no security if there is physical access to the machine. Encrypting your personal data is about all you can do.

LiveCD will be of no use to the Linux-savvy perosn.After installing UBuntu,I removed the DVD drive from my system..And now,if you tell that the person can open up the motherboard and attach his own DVD drive,that is the possibility that i think i can ignore or am not concerned of...
Seriously,Ubuntu community should really consider some blocking/unblocking mechanism for this feature so that the same can be enabled/disabled anytime by doing some changes in boot files.(sort of hardening the Ubuntu)
Maybe the option ‘Drop to root shell prompt’ should be made available depending on the settings made by user in Grub files..

---

### Post by satish_j on 2010-03-12
> **diesch said:**
> In */etc/default/grub* uncomment *GRUB_DISABLE_LINUX_RECOVERY="true"*

thanks for that..i will try it later tonight...But,i thought the grub menu options can only be updated from menu.lst file in /etc/boot location???

---

### Post by Dr Small on 2010-03-12
If someone can change the GRUB configuration, he is already at your system, and security is already compromised, as he now could steal your system, open your system, or take the hard drive. The only secure method, would be a full disc encryption.

---

### Post by coffeecat on 2010-03-12
> **satish_j said:**
> LiveCD will be of no use to the Linux-savvy perosn.After installing UBuntu,I removed the DVD drive from my system.

You can also create a live USB stick and boot up from that. Many do. It's quicker than a CD. A tech-savvy person could easily get into the BIOS and set USB as the first boot device.

Sorry. Next idea? :wink:

---

### Post by Arand on 2010-03-12
BIOS Password.

Make sure the BIOS battery (ability to remove & reset) is behind a physical lock.

That's how you prevent break-in via physical access.

Then, to prevent circumvention via stealing harddisk and booting on another system, either physically lock in the whole computer, or use disk encryption.


GNU/Linux systems have a tradition of openly disregarding "security-by-obscurity"-approaches, if there is no proper way (for ubuntu) to protect against a certain scenario, anyone interested in exploiting it will be aware of it, and any hiding of the route will only stop the opportunistic attacker ("malicious kid"), and give a false sense of protection (that is the theory at least). So yes, if you are worried about opportunistic attackers ("oh, hey, let's break his computer for poops and giggles"), then disabling recovery mode is viable, if the attack is intentional, it is moot.

 - Arand

---

### Post by Dr Small on 2010-03-12
> **Arand said:**
> BIOS Password.

Make sure the BIOS battery (ability to remove & reset) is behind a physical lock.

That's how you prevent break-in via physical access.

Then, to prevent circumvention via stealing harddisk and booting on another system, either physically lock in the whole computer, or use disk encryption.
- Arand
While a physical lock is a step in the right direction, it still wouldn't stop a theif with a bolt cutter. Then, the CMOS battery can be reset, and all that physical security went out the window, with the cut lock. A fully encrypted disk is the only sure form of security.

---

### Post by satish_j on 2010-03-12
> **coffeecat said:**
> You can also create a live USB stick and boot up from that. Many do. It's quicker than a CD. A tech-savvy person could easily get into the BIOS and set USB as the first boot device.

Sorry. Next idea? :wink:

Again,USB is disabled from BIOS and BIOS is password-protected..Removing the BIOs from Motherboard to reset its password will involve user to open the case.And,as i said,i can ignore the possibility where the case is opened..
Anyways,we are not here to discuss the hacking ideas..even the possible resolution i suggested,allows user to edit grub(if reqd in future for maintenance purpose..)And,this can be easily done by any hacker without any LiveCD and then after editing the grub,he can proceed with pwd resetting..in short,that also is a loop-hole:mad::mad:
But,atleast,i will be less vulnerable than showing the Recovery mode openly in grub menu and inviting trouble...
BTW,does this pwd reset feature also available in server versions of Ubuntu??

---

### Post by Dr Small on 2010-03-12
> **satish_j said:**
> Again,USB is disabled from BIOS and BIOS is password-protected..Removing the BIOs from Motherboard to reset its password will involve user to open the case.And,as i said,i can ignore the possibility where the case is opened..
Anyways,we are not here to discuss the hacking ideas..even the possible resolution i suggested,allows user to edit grub(if reqd in future for maintenance purpose..)And,this can be easily done by any hacker without any LiveCD and then after editing the grub,he can proceed with pwd resetting..in short,that also is a loop-hole:mad::mad:
But,atleast,i will be less vulnerable than showing the Recovery mode openly in grub menu and inviting trouble...
BTW,does this pwd reset feature also available in server versions of Ubuntu??
It's more a security tradeoff. We put that in there some newbies can reset their password easily, when they forget their passwords, and so geeks can get a root shell when the mess up their account. But the only time this becomes a security hazard is when physical security is compromised.

---

### Post by Arand on 2010-03-12
If you have the "boot a liveCD/USB/PXEboot" issue out of the way, and you don't want to have a BIOS password on each boot (one solution), then the next step would be to password-protect grub, in grub-legacy this is fairly simple: 
[http://ubuntuforums.org/showthread.php?t=7353](http://ubuntuforums.org/showthread.php?t=7353)

In grub2 it is trickier (but doable of course):
[http://ubuntuforums.org/showthread.php?t=1369019](http://ubuntuforums.org/showthread.php?t=1369019)

This will limit certain entries in the menu to only be bootable if a password are provided, which I'm guessing is kind of what you are looking for.

Also disabling manual editing of grub entries will be required for lockdown.

Of course, anyone with access to the sudo password will be able to circumvent easily.

If they don't have the sudo or grub passwords, then the lock in should be acceptable.

- Arand

---

### Post by frodon on 2010-03-12
Yep, what you are looking for is BIOS password, it is the only way to bring a bit of security when there's a physical access to the computer and this is true for any OS.

---

### Post by pricetech on 2010-03-12
Maybe it's just me, but it looks like you want the line drawn where YOU want it and nowhere else.

There are always going to be weak links in any given chain, as the analogy goes.  If someone is determined to access your stuff, they will find a way to do so no matter what you do to prevent it.

I'm having trouble understanding, however, why you want to be able to reverse your fix of what you feel is a terrible security flaw.

---

### Post by diesch on 2010-03-12
> **satish_j said:**
> thanks for that..i will try it later tonight...But,i thought the grub menu options can only be updated from menu.lst file in /etc/boot location???

Maybe it only works for GRUB2 (9.10 and newer), I don't have anything older to test at hand right now.

---

### Post by satish_j on 2010-03-13
> **pricetech said:**
> 
I'm having trouble understanding, however, why you want to be able to reverse your fix of what you feel is a terrible security flaw.
I cannot understand the logic behind resetting user passwords through REcovery mode...Recovery mode is something that is required when there are some boot-up issues in normal mode(i.e for toubleshooting)and during such instances,any operating system must first make sure that user performing the maintenance task is the admin user(like in XP,you cannot enter safe mode w/o admin pwd)..
And,sooner or later,Recovery mode will be required for troubleshooting purposes.thats why i want to be able to reverse the fix at boot-up time (or any other option,if available) whenever required..
Iam deeply shocked after learning about this feature(a serious loop-hole for me though) and more than that,iam still wondering how many of the users ae considering this a good feature...
Ubuntu is not only for Geeks...If it is,thier slogan should be UBUNTU--LINUX FOR GEEKS..

---

### Post by satish_j on 2010-03-15
Well,i removed all the lines for recovery mode option from /boot/grub/menu.lst and now,i have successfully removed the recovery mode boot option from grub menu...can also boot to Ubuntu in normal mode..
What remains a concern for me now is:If,in future,i may need recovery option again,can i be able to edit menu.lst at boottime to add recovery option again???
Also,i need the procedure for password-protecting the menu.lst file so that any reference to it should require password..
Desperately waiting for assistance on this....

---

### Post by satish_j on 2010-03-15
Just read the foll thread 
[http://ubuntuforums.org/showthread.php?t=7353](http://ubuntuforums.org/showthread.php?t=7353)
It explained how to password protect the grub boot options and that was the type of security i was looking for...
I can now keep the recovery option visible in boot menu and whenever required can boot into it with the password...
Tell you what,md5 hash is what will take an hacker years to crack...Great....

---

