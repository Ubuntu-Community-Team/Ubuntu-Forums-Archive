---
title: "fan noise in hp laptop"
date: 2011-06-17
forum: General Help
---

### Post by tah_206207 on 2011-06-17
hello my laptop is hp dv6 6080(6000) with sandy bridge cpu and two graphic card...
i have problem with linux! 
my cpu fan in linux works hard although my cpu percent 1% - 9%  but in windows my cpu fan works slow and doesn't make noise. why this problem 
i use ubuntu 11.4 and new version of arch linux and i have same problem with my laptop but in windows i don't have this problem!
is this problem for linux kernel bug in versions of 2.6.38 and 2.6.39?
please help me to solve this proble...
i use linux as my operating system but this problem confused me!
thanks...

---

### Post by DanneStrat on 2011-06-17
Hi.

The first thing to try is to boot the kernel with

a different boot parameter.

Do this in terminal:

```
gksudo gedit /etc/default/grub
```

This will open your grub configuration file.

Now look for this line:

GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"

and add this part to it (marked in red):

GRUB_CMDLINE_LINUX_DEFAULT="quiet splash [COLOR="Red"]acpi_osi=\"Linux\"[/COLOR]"

Save the file (File > Save) and exit.

Then go back to terminal and do:

```
sudo update-grub
```

to make grub use your new settings.

Now reboot and see if your problem got fixed.

---

### Post by tah_206207 on 2011-06-17
thanks dear [DanneStrat]("http://ubuntuforums.org/member.php?u=1200686") for your reply.
i check your suggestion.
i use below option for booting ubuntu and without this my laptop can't boot ubuntu but i don't know how can i save this option
in grub menu i prees e key and add pci=noacpi to ubuntu boot option but i can't add this option as a default boot option when i add acpi=off  after GRUB_CMDLINE_LINUX_DEFAULT="quiet splash" like this
```

GRUB_CMDLINE_LINUX_DEFAULT="quiet splash" acpi=off

```
and update-grub after this my laptop can't boot ubuntu and i should add this option manually to grub boot option.
how can i solve this problem.
thanks

---

### Post by tah_206207 on 2011-06-17
> **DanneStrat said:**
> Hi.

The first thing to try is to boot the kernel with

a different boot parameter.

Do this in terminal:

```
gksudo gedit /etc/default/grub
```This will open your grub configuration file.

Now look for this line:

GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"

and add this part to it (marked in red):

GRUB_CMDLINE_LINUX_DEFAULT="quiet splash [COLOR=Red]acpi_osi=\"Linux\"[/COLOR]"

Save the file (File > Save) and exit.

Then go back to terminal and do:

```
sudo update-grub
```to make grub use your new settings.

Now reboot and see if your problem got fixed.
I add this option like you said. but after this my problem is stand!
when i am do nothings in ubuntu and close any open software my cpu fan after minutes work slow but when i open program like gedit or nautilus for browsing files in my hard drivemy cpu fan start to working hard and make noise! but i haven't this problem in windows when i open windows explorer to browsing files in my hard drive!
please help me to solve this problem!...
thanks

---

### Post by DanneStrat on 2011-06-17
> I add this option like you said. but after this my problem is stand!
when i am do nothings in ubuntu and close any open software my cpu fan after minutes work slow but when i open program like gedit or nautilus for browsing files in my hard drivemy cpu fan start to working hard and make noise! but i haven't this problem in windows when i open windows explorer to browsing files in my hard drive!
please help me to solve this problem!...
thanks

To be able to help you, I will need to have a look at the grub configuration file.

Open terminal and do:

```
cat /etc/default/grub
```

This will print out the contents of that file to standard output.

Post the output here so I can have a look at it.

---

### Post by tah_206207 on 2011-06-17
ok this is my grub configuration.
```

taher@Taher-HP:~$ cat /etc/default/grub
# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'

GRUB_DEFAULT=0
#GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi_osi=\"Linux\"" 
GRUB_CMDLINE_LINUX=""

# Uncomment to enable BadRAM filtering, modify to suit your needs
# This works with Linux (no patch required) and with any kernel that obtains
# the memory map information from GRUB (GNU Mach, kernel of FreeBSD ...)
#GRUB_BADRAM="0x01234567,0xfefefefe,0x89abcdef,0xefefefef"

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE=640x480

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_RECOVERY="true"

# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"


```i have windows 7 in my laptop bur i lose that in grub menu because my grub removed and i Being forced install grub manually but when i install grub i install it at /dev/sda although my ubuntu is in /dev/sda9 and after that grub can't recognize my windows7 in grub menu.
below code is update-grub out put...
```

taher@Taher-HP:~$ sudo update-grub
[sudo] password for taher: 
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.38-8-generic
Found initrd image: /boot/initrd.img-2.6.38-8-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Windows Recovery Environment (loader) on /dev/sda2
Found Windows Recovery Environment (loader) on /dev/sda5
Found Arch on /dev/sda8
done


```
thanks

---

### Post by DanneStrat on 2011-06-17
You mentioned earlier that you need to boot ubuntu with "pci=noacpi" for ubuntu to boot properly. We will make that setting permanent as well as trying a different approach with the "acpi_osi=" setting.

Do this step again

```
gksudo gedit /etc/default/grub
```

This time, modify the line to look like this:

GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi_osi= pci=noacpi"

Then save.

```
sudo update-grub
```

and reboot.

Any difference this time?

---

### Post by tah_206207 on 2011-06-17
Ok my ubuntu boot properly at this time thank you dear [DanneStrat]("http://ubuntuforums.org/member.php?u=1200686"). but my laptop fan problem is stand at this time! please help me to fix this problem!

how can i use better from my laptop battery? how can i use poser saving mode in linux?
i read in another post for bug of kernel 2.6.38 and 2.6.39 that use many battery! can i fix this problem?
very thanks for your help dear [DanneStrat]("http://ubuntuforums.org/member.php?u=1200686").

---

### Post by nrundy on 2011-06-17
Linux runs a lot hotter than Windows. Plus there is a current bug that is making it run even hotter. 

I've switched all my laptops over to Windows 7. 7 runs cooler, a lot quieter and you will get longer battery life.

Hopefully the heat issue will be addressed in the future of linux and it will run as cool as Windows. For the time being though there's not too much you can do.

---

### Post by DanneStrat on 2011-06-17
> Ok my ubuntu work properly at this time thank you dear DanneStrat.

I'm glad to hear that and you're welcome!

> but my laptop fan problem is stand at this time! please help me to fix this problem!

I don't know if there's anything more to do at this time. If it's a bug then hopefully it will get fixed in a later kernel update. 

> how can i do this instruction for my arch linux?

The steps should be pretty much the same. If you haven't set up sudo in arch you will need to log in with the root account and make the changes from there. If I were you I would go to the arch forums and ask the question there. If you need more help doing this I would be happy to assist.

> how can i use better from my laptop battery? how can i use poser saving mode in linux?
i read in another post for bug of kernel 2.6.38 and 2.6.39 that use many battery! can i fix this problem?

If you don't notice that you get shorter battery time when using ubuntu 11.04 compared to windows, then you don't have to worry about it. If you do, then there may be an existing bug in the kernel. In that case, wait for a while until a kernel update get's released and then maybe it will be fixed.

> i have windows 7 in my laptop bur i lose that in grub menu because my grub removed and i Being forced install grub manually but when i install grub i install it at /dev/sda although my ubuntu is in /dev/sda9 and after that grub can't recognize my windows7 in grub menu.

Do you need help with this? I can try to post instructions on how to fix it.

Good luck.

---

### Post by tah_206207 on 2011-06-17
thank you for yours replies.
i hope that kernel update make linux as cool as windows7 and use low battery like win7!.
can i tell kernel developers about this bug to fix it at future version? or they know this problem and try to fix it?
> Do you need help with this? I can try to post instructions on how to fix it.
yes i need your help for fixing this problem...

---

### Post by DanneStrat on 2011-06-17
> **tah_206207 said:**
> can i tell kernel developers about this bug to fix it at future version? or they know this problem and try to fix it?

I think they are aware of them. If you want to file a bug report I think you can do it here: [https://bugs.launchpad.net/ubuntu](https://bugs.launchpad.net/ubuntu)

> yes i need your help for fixing this problem...

I will be back with instructions soon.

---

### Post by tah_206207 on 2011-06-17
> I will be back with instructions soon.
thank you dear [DayonneStrat]("http://ubuntuforums.org/member.php?u=1200686").
mention that i haven't win7 dvd to get win7 boot loader in my laptop and i have recovery media in one of my laptop's drives.

---

### Post by pqwoerituytrueiwoq on 2011-06-17
check to see how fast the cpu is running on windows under power management advanced section
it may be limited to 40-60 % of the true speed to lower the temperature

---

### Post by DanneStrat on 2011-06-17
> **tah_206207 said:**
> thank you dear [DayonneStrat]("http://ubuntuforums.org/member.php?u=1200686").
mention that i haven't win7 dvd to get win7 boot loader in my laptop and i have recovery media in one of my laptop's drives.

That's a bit problematic. You will need either your win 7 dvd or a recovery cd that you have to build from inside win 7. I don't think the recovery partition you have can be used to fix the MBR. I will have a look around for an alternative method. 

Meanwhile, you can run the bootinfo script so we we can have a look at your disks and partitions.

Do this:

1. Boot your pc from the ubuntu live cd.

2. When you get to the screen with selections, choose to "try ubuntu without installing"

3. When you get to the desktop, start the web browser and download the script here: [http://dl.dropbox.com/u/15638108/boot_info_script.sh](http://dl.dropbox.com/u/15638108/boot_info_script.sh)

Save it to your desktop folder.

4. Bring up terminal and do:
```
sudo bash ~/Desktop/boot_info_script.sh
```

After this you will have a file called "RESULTS.txt" on the desktop. Post the contents back here or make an attachment.

---

### Post by tah_206207 on 2011-06-17
> **DanneStrat said:**
> That's a bit problematic. You will need either your win 7 dvd or a recovery cd that you have to build from inside win 7. I don't think the recovery partition you have can be used to fix the MBR. I will have a look around for an alternative method. 

Meanwhile, you can run the bootinfo script so we we can have a look at your disks and partitions.

Do this:

1. Boot your pc from the ubuntu live cd.

2. When you get to the screen with selections, choose to "try ubuntu without installing"

3. When you get to the desktop, start the web browser and download the script here: [http://dl.dropbox.com/u/15638108/boot_info_script.sh](http://dl.dropbox.com/u/15638108/boot_info_script.sh)

Save it to your desktop folder.

4. Bring up terminal and do:
```
sudo bash ~/Desktop/boot_info_script.sh
```After this you will have a file called "RESULTS.txt" on the desktop. Post the contents back here or make an attachment.
ok i do this instruction very soon...
i have windows recovery DVDs that i make them from hp recover media but i haven't win7 installer DVD!

---

### Post by tah_206207 on 2011-06-17
I got below output from boot script.
[http://pastebin.com/ZizjMK28](http://pastebin.com/ZizjMK28)

---

### Post by nrundy on 2011-06-17
> **tah_206207 said:**
> thank you for yours replies.
i hope that kernel update make linux as cool as windows7 and use low battery like win7!.
can i tell kernel developers about this bug to fix it at future version? or they know this problem and try to fix it?
yes i need your help for fixing this problem...

the linux community knows about the Regression Bug. The problem though is that linux was running hotter than windows before the regression. A lot of people have been asking for developers to make linux run as cool as Windows for years. So far the people's request have gone unanswered.

You can request it from the developers, but most likely you'll just be ignored.

---

### Post by DanneStrat on 2011-06-17
So, I had a look at your bootinfo output and as far as I can see everything looks pretty normal.
I don't know if you need to repair your windows MBR or a reinstall of grub would be enough(to get the win7 entry back in grub menu). 

Maybe somebody else knows?

---

### Post by tah_206207 on 2011-06-17
> **DanneStrat said:**
> So, I had a look at your bootinfo output and as far as I can see everything looks pretty normal.
I don't know if you need to repair your windows MBR or a reinstall of grub would be enough(to get the win7 entry back in grub menu). 

Maybe somebody else knows?
why my grub can't recognize win7?
can every one help me to appear win7 in grub menu.

---

### Post by pqwoerituytrueiwoq on 2011-06-17
try running this command
sudo update-grub

---

### Post by tah_206207 on 2011-06-17
> **pqwoerituytrueiwoq said:**
> try running this command
sudo update-grub
i run this command but grub can't recognize my win7! and only recognize win7 recovery. i paste out put of update-grub at first page of this post!.

---

### Post by tah_206207 on 2011-06-17
I have another question about linux!
was linux hottest than win7 at old version of kernel? because i use linux on my pc and after i bought laptop install ubuntu11.4 and arch new version on my laptop and encounter with this problem on my laptop!

---

### Post by nrundy on 2011-06-18
> **tah_206207 said:**
> I have another question about linux!
was linux hottest than win7 at old version of kernel? because i use linux on my pc and after i bought laptop install ubuntu11.4 and arch new version on my laptop and encounter with this problem on my laptop!

Tah, linux has run considerably hotter than Windows going back years. See this post here from 2008: [http://ubuntuforums.org/showthread.php?t=821591](http://ubuntuforums.org/showthread.php?t=821591)

Searching online will produce similar findings. Ubuntu's Brainstorm has ideas going back years begging developers to get the temperature down. But no joy.

If you want a cool, quiet running laptop, you have no choice but to run Windows (or Mac). It sucks. But what can you do? There's plenty of folks that kindly offer hacks to resolve the problem but it's hardly a comparable fix to having the developers make it run cooler "out of the box."

---

### Post by tah_206207 on 2011-06-19
> **nrundy said:**
> Tah, linux has run considerably hotter than Windows going back years. See this post here from 2008: [http://ubuntuforums.org/showthread.php?t=821591](http://ubuntuforums.org/showthread.php?t=821591)

Searching online will produce similar findings. Ubuntu's Brainstorm has ideas going back years begging developers to get the temperature down. But no joy.

If you want a cool, quiet running laptop, you have no choice but to run Windows (or Mac). It sucks. But what can you do? There's plenty of folks that kindly offer hacks to resolve the problem but it's hardly a comparable fix to having the developers make it run cooler "out of the box."
thank you
this bug ( hot system ) is competent for ubuntu distribution or other distribution has this bug?
this bug is for kernel of linux or for ubuntu distribution?

---

### Post by nrundy on 2011-06-19
> **tah_206207 said:**
> tank you
this bug ( hot system ) is competent for ubuntu distribution or other distribution has this bug?
this bug is for kernel of linux or for ubuntu distribution?

It's in the linux kernel and not specific to ubuntu. You will see it in all distros.

It's a huge disappoint for me because I really like using ubuntu more than Win7. But a cool, quiet running machine is really a CRITICAL feature. I'm really hoping that the developers address this issue and that once the bug is fixed other improvements are made and the running temp comes way down. Keeping my fingers crossed that ubuntu 12.04 will run as cool and quiet as Win7.

---

