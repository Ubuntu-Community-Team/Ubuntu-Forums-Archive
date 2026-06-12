---
title: "fast help, karnel"
date: 2011-05-18
forum: General Help
---

### Post by oklinuxyo on 2011-05-18
hi
i need install ati driver from ati.com
i dl but someone say i need to complie (or recompile i duno) karnel first, because next time i update this karnel, linux will go bsod and not work because driver get broken
he give me some command but i get error and not work
how i do this "compile" and install ati driver? i already figure how to install the .rpm (i just click properties and check "executable") but i ned comile first?

help me fast please need at driver because fan sped 100% al the time :><<<

---

### Post by 4Orbs on 2011-05-18
I think [This Page]("http://wiki.cchtml.com/index.php/Ubuntu_Natty_Installation_Guide") is what you are looking for. Go down to the section "Install Drivers Manually".

But before you do this: Have you tried installing the drivers supplied by Ubuntu? Just go to the system menu and click on "Additional Drivers".

---

### Post by oklinuxyo on 2011-05-18
hi this install driver fglrx propritary driver = not good one guy said
because it install driver to kernel without compile and when i get kernel update it come linux bsod i want avoid tis

---

### Post by 4Orbs on 2011-05-18
It is easy to avoid problems. I use the driver supplied by "Additional Drivers", and when a new kernel update comes I deactivate the driver and reboot BEFORE running the kernel update. Then I activate the driver after the kernel update. Never caused any problem for me.

---

### Post by oklinuxyo on 2011-05-18
Hmm, so why linux get problem when forgot to disable fglrx driver on rebot when update kernel_?

---

### Post by 4Orbs on 2011-05-18
I don't know if Ubuntu has that problem. I began deactivating the driver two years ago because it just seems like the safe way to do a kernel upgrade. These days it may be safe to upgrade the kernel while the driver is still activated. But rather than take the risk of breaking my system, I prefer to deactivate the driver before running the kernel update.

---

### Post by debd on 2011-05-18
you dont have to compile your kernel, but what you have to do is to build the driver for your kernel if you are doing it manually. Well, that might sound intimidating, but its easier than it sounds.

_1st method (if you want the open source driver):_
 try out the instructions and the PPA released for ATI drivers for Ubuntu 11.04 [here]("https://help.ubuntu.com/community/RadeonDriver")

_2nd method(proprietary driver):_
goto [http://support.amd.com/us/gpudownload/Pages/index.aspx](http://support.amd.com/us/gpudownload/Pages/index.aspx)
and download the appropriate binary driver for your graphics card.
save the file in your home folder (for conveniences's sake)
now, right click the file > click on the 'permissions' tab > there's a option 'allow executing file as program' ; check the box beside it.

now, for manual building of the driver, I suggest this method:
1. boot into recovery mode
2. select 'drop into root shell'
3. now enter 
```
 sudo sh ./filename.bin
```
and follow the instructions.
mostly, you should select 'yes'...generally.

either way, if you upgrade the driver later, you'll have to perform the installation again as the drivers are compiled for only the kernel you are currently using.

edit: I found some more info on installing the proprietary driver [here]("https://help.ubuntu.com/community/BinaryDriverHowto/ATI")
but , these are for 10.10 and may be outdated.

---

### Post by oklinuxyo on 2011-05-18
> **debd said:**
> you dont have to compile your kernel, but what you have to do is to build the driver for your kernel if you are doing it manually. Well, that might sound intimidating, but its easier than it sounds.

_1st method (recommended):_
 try out the instructions and the PPA released for ATI drivers for Ubuntu 11.04 [here]("https://help.ubuntu.com/community/RadeonDriver")

_2nd method(manual):_
goto [http://support.amd.com/us/gpudownload/Pages/index.aspx](http://support.amd.com/us/gpudownload/Pages/index.aspx)
and download the appropriate binary driver for your graphics card.
save the file in your home folder (for conveniences's sake)
now, right click the file > click on the 'permissions' tab > there's a option 'allow executing file as program' ; check the box beside it.

now, for manual building of the driver, I suggest this method:
1. boot into recovery mode
2. select 'drop into root shell'
3. now enter 
```
 sudo sh ./filename.bin
```and follow the instructions.
mostly, you should select 'yes'...generally.

either way, if you upgrade the driver later, you'll have to perform the installation again as the drivers are compiled for only the kernel you are currently using.
hi, you look like expert
so is this necesary? because i dont want make extra work for nothing = too much time
i read this link you give me and i think tshi is the "defaulT" driver already instaled in ubuntu/kubuntu
but this cause problem, it ok with 3d acceleration but no fan control my fan speed 100% 24/7 = much noise like vacum cleaner
so is this likn you linkd for included driver or some other, i dont understand

---

### Post by debd on 2011-05-18
I've little experienced about ATI drivers.
but, what I know is, any other driver, which comes pre-installed with the basic installation, would be disabled after you try to install the proprietary driver for the first time. 
so you may have to try installing the proprietary driver a second time.
Its ok if that happens.
I suggest you go with the second method. the manual one.
do you know what model of graphics card you have?

---

### Post by oklinuxyo on 2011-05-18
sorry i didnt notice, the 1st method is for "default" driver already included in ubuntu
i have hd 5870, i have instaled proprietary driver befor and it worked goof, but one guy in intersnet say that if i now update kernel my linux will broke :<
so i need to do this "compile" or "build" thing you talk about befor so that when i update linux work good.
i will try manual method of install proprer driver now
got any tips ? i will 99% get problems haha

---

### Post by debd on 2011-05-18
> **oklinuxyo said:**
> sorry i didnt notice, the 1st method is for "default" driver already included in ubuntu
i have hd 5870, i have instaled proprietary driver befor and it worked goof, but one guy in intersnet say that if i now update kernel my linux will broke :<
so i need to do this "compile" or "build" thing you talk about befor so that when i update linux work good.
i will try manual method of install proprer driver now
got any tips ? i will 99% get problems haha

so you had a proprietary driver installed before?
if that's so, all you have to do is to reinstall the driver once again like you did before. after kernel upgrade, you'll possibly get a black screen after login. then you reinstall the driver again.
btw, how did you install the driver last time?

**and remember, you have to reinstall the driver after you have upgraded kernel. not before that!**

---

### Post by 4Orbs on 2011-05-18
I have one question. If you manually install the latest driver from the ati website, does it include a fan speed control in the Catalyst Control Center (like the one included in the CCC for Windows)?

---

### Post by oklinuxyo on 2011-05-18
> **4Orbs said:**
> I have one question. If you manually install the  latest driver from the ati website, does it include a fan speed control  in the Catalyst Control Center (like the one included in the CCC for  Windows)?
yes i want know too



to you linux expert again


wait? with propriet driver next time i update kernel i will get black screen? how can i use my mouse?

and last time i install noob style with additional driver, and befor that i use software manager (the one that use these repository) and it work good (just angst for kernel update).

but now i will install driver manal mode
becaus i want be cool like santa claus 8-)

---

### Post by debd on 2011-05-18
> i want be cool like santa claus 
well buddy, then get the driver from [this link ]("http://support.amd.com/us/gpudownload/Pages/index.aspx")
and follow the manual method.

---

### Post by oklinuxyo on 2011-05-18
yes i will do it soon, i just ned reinstall kubuntu real fast lol i bug something install take 2 mins anyway.

---

### Post by oklinuxyo on 2011-05-18
ok i got 2 roble m
1 it is not .bin but .run bt i enter run instead, is this ok or i break linux?
2 now in recovry mode it ask where i want install driver, i dunno i want it in kernel how i tell driver to go there? please givr directory path.

---

### Post by oklinuxyo on 2011-05-18
anyone can help fast?
i wait at black screen for 40mins now...
i will boot to kubuntu normal now
can anyone tell me way to only install driver to current kernel without going to recover mode, becaus i dont know what directory i want install the driver.

so i want:
install driver to current kernel only so when kernal update arive, i install update and driver is gone so no kernel bugged please help

---

### Post by debd on 2011-05-19
did you keep the .run file in your home folder?
if so, login to normal mode, you'll get a black screen.
enter the commands:
```
ls
```
or if you saved it in the Downloads folder, use
```
cd Downloads && ls
```
you see the ati driver file?
now, run
```
sudo sh ./file-name.run
```

if the file name's long, type the first two-three letters of the file name, then press TAB, this will complete the name. Press enter.

---

### Post by oklinuxyo on 2011-05-20
ok i find this comand:
sudo apt-get install build-essential linux-source-2.6.38

does this comand now anti bug my system when instal driver?
so when i instal new kernel, it will recompile it without driver so i ned reinstall`?

atm all workd good, but i ned equalizer for system, becaus i need boost bass (very bass lacked headphone and sound card) how i install equalizer?

---

### Post by debd on 2011-05-20
> sudo apt-get install build-essential linux-source-2.6.38

you dont need this command! what this does is that, it'll download the source files(raw codes) of the linux kernel 2.6.38 and are only needed for testing/other advanced uses.
you can compile it for use though, but that certainly not what you need.

if you need a new kernel, you can get it through the software updater.

did your driver installation go well?

for a equalizer, install smplayer from the synaptic. it has a very functional equalizer.
for rythmbox, there's a equalizer plugin (i dont remember the link!sorry) , but its not functional enough; i mean it doesn't really give the desired effect.

---

### Post by oklinuxyo on 2011-05-20
> **debd said:**
> you dont need this command! what this does is that, it'll download the source files(raw codes) of the linux kernel 2.6.38 and are only needed for testing/other advanced uses.
you can compile it for use though, but that certainly not what you need.

if you need a new kernel, you can get it through the software updater.

did your driver installation go well?

for a equalizer, install smplayer from the synaptic. it has a very functional equalizer.
for rythmbox, there's a equalizer plugin (i dont remember the link!sorry) , but its not functional enough; i mean it doesn't really give the desired effect.
man 2 pages of text in this post and i dont understand
some say i dont ned to do anything kernel update is ok without problem
and then some other say no i need to recompile otherwise linux bug when update kernel....
maaaan 

also for equalizer, i need for whole linux not just one program how i install?
and yes driver instal ok no problem i now know some comand how to use.
but still i want to understand this kernel update, if I **NOW  **update kernel (if there was update, lets imagina) would my driver bug?

---

### Post by Petrolea on 2011-05-20
> **oklinuxyo said:**
> hi
i need install ati driver from ati.com
i dl but someone say i need to complie (or recompile i duno) karnel first, because next time i update this karnel, linux will go bsod and not work because driver get broken
he give me some command but i get error and not work
how i do this "compile" and install ati driver? i already figure how to install the .rpm (i just click properties and check "executable") but i ned comile first?

help me fast please need at driver because fan sped 100% al the time :><<<

Nobody can say everything will be ok, but one thing is for sure: you won't see a BSOD. You don't need to compile kernel. Install drivers and don't listen to people that say that it is necessary to compile it. 

Install driver the way others already said (either download from internet or use automated install). If anything goes wrong you can always go back to default drivers and try again.

---

### Post by Petrolea on 2011-05-20
> **oklinuxyo said:**
> 
but still i want to understand this kernel update, if I **NOW  **update kernel (if there was update, lets imagina) would my driver bug?

Most likely not. But distro upgrade, it might. I see about 8 kernels in my grub menu and by the time there was only one my drivers never got bugged (and I didn't use the automated install).

---

### Post by oklinuxyo on 2011-05-20
okay thank you i think i will just ignore this compile ****
but can you help me find system wide equalizer?
alsafreq not work anymore

---

