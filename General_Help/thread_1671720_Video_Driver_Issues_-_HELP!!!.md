---
title: "Video Driver Issues - HELP!!!"
date: 2011-01-20
forum: General Help
---

### Post by Nezmin2 on 2011-01-20
Hey Guy's,
I am a bit new to Ubuntu so I apologize if I sound like a newb. Last night I uninstalled the proprietary ati driver and then installed the open source version. Following a reboot, I now get a pink screen with no where to go...I am not sure where to go from here. There is nothing to click on.

I am using a HP Pavilion Entertainment PC (dv6) with an AMD processor and an ATI 4500 series gpu. I also am using Ubuntu 10.10 64 bit.

I appreciate any assistance...I really do not want to reinstall everything...


P.S. I am dual booting it with win 7...I know, I know, but unfortunately, I had to....:-(

Thanks....

---

### Post by lithopsian on 2011-01-20
Pink?  Nice :)

You will need to boot to the command line and remove your bad drivers.  Put back the good ones and then reboot.

If you can't boot to anywhere then you can try booting from a CD and making the changes from there.

---

### Post by Nezmin2 on 2011-01-20
> **lithopsian said:**
> Pink?  Nice :)

You will need to boot to the command line and remove your bad drivers.  Put back the good ones and then reboot.

If you can't boot to anywhere then you can try booting from a CD and making the changes from there.

How do I boot to the command line? It goes right from the Grub menu to a pink screen. It does show the Ubuntu logo and then immediately fades out to a all pink screen with nothing to click on...

---

### Post by pqwoerituytrueiwoq on 2011-01-20
recovery mode in the grub menu

---

### Post by ptrinder64 on 2011-01-20
I think the first thing to try in order to get to the CLI and a working desktop is to load the Ubuntu recovery entry on Grub. This should be the entry directly underneath your normal boot option and look something like this:

```
Ubuntu, with Linux 2.6.35-25-generic (recovery mode)
```

Assuming this loads and you get to the login screen, then you need to click the user you want to load up (DON'T enter a password yet). From here on the subsequent screen there should be a button at the bottom labelled 'sessions'. Click this and select the 'failsafe' option (I believe this is what it's called). Now enter your password and you will be taken to a CLI. 

I think this is worth a try, but not 100% sure it'll work.

EDIT: Looking at pqwoerituytrueiwoq's entry above, my advice may not be necessarily - I was making the broad assumption that the Ubuntu Recovery mode acted in the same way as the OpenSuSe failsafe mode!

---

### Post by endotherm on 2011-01-20
if you are having trouble, here are some instructions for entering and using ubuntu's recovery/rescue mode:
[http://www.linuxtopia.org/online_books/system_administration_books/ubuntu_starter_guide/ch08.html](http://www.linuxtopia.org/online_books/system_administration_books/ubuntu_starter_guide/ch08.html)

---

### Post by Nezmin2 on 2011-01-20
> **ptrinder64 said:**
> I think the first thing to try in order to get to the CLI and a working desktop is to load the Ubuntu recovery entry on Grub. This should be the entry directly underneath your normal boot option and look something like this:

```
Ubuntu, with Linux 2.6.35-25-generic (recovery mode)
```

Assuming this loads and you get to the login screen, then you need to click the user you want to load up (DON'T enter a password yet). From here on the subsequent screen there should be a button at the bottom labelled 'sessions'. Click this and select the 'failsafe' option (I believe this is what it's called). Now enter your password and you will be taken to a CLI. 

I think this is worth a try, but not 100% sure it'll work.

EDIT: Looking at pqwoerituytrueiwoq's entry above, my advice may not be necessarily - I was making the broad assumption that the Ubuntu Recovery mode acted in the same way as the OpenSuSe failsafe mode!

I was able to boot into recovery mode. I am now sitting at a command prompt with networking. I am just not sure how to uninstall the driver and reinstall the correct open source ati driver with all of its dependencies...

---

### Post by endotherm on 2011-01-20
> **Nezmin2 said:**
> I was able to boot into recovery mode. I am now sitting at a command prompt with networking. I am just not sure how to uninstall the driver and reinstall the correct open source ati driver with all of its dependencies...

I would just CD back to the location where you downloaded the proprietary driver, and just rerun the installer. it will unlink the open driver in the process.

---

### Post by ptrinder64 on 2011-01-20
> **endotherm said:**
> I would just CD back to the location where you downloaded the proprietary driver, and just rerun the installer. it will unlink the open driver in the process.

+1 for this.

However if you can not remember where you saved the driver, or for some reason deleted it this may not be an option. I'm assuming you are using a live CD to go on Ubuntu forums? If so, all you need to do if you don't have the files any more is go to the site of your graphics card (Nvidia or ATI) using the live CD, mount your normal home partition, and save the files there. Once this has been done, reboot into the Ubuntu recovery mode and unpack the files by changing directory to your home file.

I think this will automatically remove the non-proprietary drivers so do this first. If you think the other drivers are still on the system **_AFTER_** you have done the above, then you can remove these by running in the terminal:

```
sudo apt-get remove <name of drivers>
```

---

### Post by ptrinder64 on 2011-01-20
oops... duplicate post...

---

### Post by Nezmin2 on 2011-01-20
I was able to install the proprietary ati radeon driver and it unseated whatever I broke yesterday. Now I have a regular session running. However, I am still left with the desire to install the open source version of the driver. I am wanting it because of the ability to tweak it to run WOW.

I am using an HP Pavilion Entertainment PC (dv6) with an ATI Radeon HD 4500 series graphic card and 3 gigs of ram.

Can someone tell me exactly (step by Step) how to download the source, compile for my pc, install, and run the open source ATI driver? Including any dependencies that may be required?

---

### Post by Nezmin2 on 2011-01-20
I was able to install the proprietary ati radeon driver and it unseated whatever I broke yesterday. Now I have a regular session running. However, I am still left with the desire to install the open source version of the driver. I am wanting it because of the ability to tweak it to run WOW.

I am using an HP Pavilion Entertainment PC (dv6) with an ATI Radeon HD 4500 series graphic card and 3 gigs of ram.

Can someone tell me exactly (step by Step) how to download the source, compile for my pc, install, and run the open source ATI driver? Including any dependencies that may be required?

---

### Post by Nezmin2 on 2011-01-20
I was able to install the proprietary ati radeon driver and it unseated whatever I broke yesterday. Now I have a regular session running. However, I am still left with the desire to install the open source version of the driver. I am wanting it because of the ability to tweak it to run WOW.

I am using an HP Pavilion Entertainment PC (dv6) with an ATI Radeon HD 4500 series graphic card and 3 gigs of ram.

Can someone tell me exactly (step by Step) how to download the source, compile for my pc, install, and run the open source ATI driver? Including any dependencies that may be required?

---

### Post by Nezmin2 on 2011-01-20
I was able to install the proprietary ati radeon driver and it unseated whatever I broke yesterday. Now I have a regular session running. However, I am still left with the desire to install the open source version of the driver. I am wanting it because of the ability to tweak it to run WOW.

I am using an HP Pavilion Entertainment PC (dv6) with an ATI Radeon HD 4500 series graphic card and 3 gigs of ram.

Can someone tell me exactly (step by Step) how to download the source, compile for my pc, install, and run the open source ATI driver? Including any dependencies that may be required?

---

### Post by Nezmin2 on 2011-01-20
I was able to install the proprietary ati radeon driver and it unseated whatever I broke yesterday. Now I have a regular session running. However, I am still left with the desire to install the open source version of the driver. I am wanting it because of the ability to tweak it to run WOW.

I am using an HP Pavilion Entertainment PC (dv6) with an ATI Radeon HD 4500 series graphic card and 3 gigs of ram.

Can someone tell me exactly (step by Step) how to download the source, compile for my pc, install, and run the open source ATI driver? Including any dependencies that may be required?

---

### Post by Nezmin2 on 2011-01-20
I was able to install the proprietary ati radeon driver and it unseated whatever I broke yesterday. Now I have a regular session running. However, I am still left with the desire to install the open source version of the driver. I am wanting it because of the ability to tweak it to run WOW.

I am using an HP Pavilion Entertainment PC (dv6) with an ATI Radeon HD 4500 series graphic card and 3 gigs of ram.

Can someone tell me exactly (step by Step) how to download the source, compile for my pc, install, and run the open source ATI driver? Including any dependencies that may be required?

---

### Post by Nezmin2 on 2011-01-20
I was able to install the proprietary ati radeon driver and it unseated whatever I broke yesterday. Now I have a regular session running. However, I am still left with the desire to install the open source version of the driver. I am wanting it because of the ability to tweak it to run WOW.

I am using an HP Pavilion Entertainment PC (dv6) with an ATI Radeon HD 4500 series graphic card and 3 gigs of ram.

Can someone tell me exactly (step by Step) how to download the source, compile for my pc, install, and run the open source ATI driver? Including any dependencies that may be required?

---

### Post by Nezmin2 on 2011-01-20
I was able to install the proprietary ati radeon driver and it unseated whatever I broke yesterday. Now I have a regular session running. However, I am still left with the desire to install the open source version of the driver. I am wanting it because of the ability to tweak it to run WOW.

I am using an HP Pavilion Entertainment PC (dv6) with an ATI Radeon HD 4500 series graphic card and 3 gigs of ram.

Can someone tell me exactly (step by Step) how to download the source, compile for my pc, install, and run the open source ATI driver? Including any dependencies that may be required?

---

### Post by Nezmin2 on 2011-01-20
I was able to install the proprietary ati radeon driver and it unseated whatever I broke yesterday. Now I have a regular session running. However, I am still left with the desire to install the open source version of the driver. I am wanting it because of the ability to tweak it to run WOW.

I am using an HP Pavilion Entertainment PC (dv6) with an ATI Radeon HD 4500 series graphic card and 3 gigs of ram.

Can someone tell me exactly (step by Step) how to download the source, compile for my pc, install, and run the open source ATI driver? Including any dependencies that may be required?

---

### Post by ptrinder64 on 2011-01-21
Well I'm using a slightly older HP DV6 too with a ATI Mobility Radeon 4200 series (not using Ubuntu 64 bit however).

I think the way you need to install this is to:

1. Download the correct drivers from [http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx]("http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx") and save to your home directory
2. Open up a terminal window
3. If for whatever reason your terminal doesn't open to your home drive automatically cd to it
4. Run the command:
```
chmod +x ati-driver-installer-10.12.x86.x86_64.run
```
(this makes the file executable)
5. Now as you are installing drivers you need to run the ATI installer file as sudo by doing the following in the same terminal window:
```
sudo ati-driver-installer-10.12.x86.x86_64.run
```
6. Next a new window should pop up asking you whether you want to install the driver or generate a distribution specific driver. You need to click the first option - 'install the driver'
7. At the next screen you should choose the automatic option rather than the custom option

*Hopefully* this should work as this is what I did on mine. I would caution however that before you try this, make sure that you know the process you went through before to get back to a normal login session.

I hope this works for you.

---

