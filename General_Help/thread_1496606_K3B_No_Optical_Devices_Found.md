---
title: "K3B No Optical Devices Found"
date: 2010-05-29
forum: General Help
---

### Post by Nythain on 2010-05-29
So i've been having this problem since lucid, in both ubuntu and kubuntu, though im currently running kubuntu wich is why i tagged it that way.

I open k3b, and it immediately tells me there's no optical device/drive...
Then i "wodim --devices" and it returns
```

wodim: Overview of accessible drives (0 found) :
-------------------------------------------------------------------------
-------------------------------------------------------------------------

```
well that sucks, next stop "wodim --scanbus"
```

scsibus4:
        4,0,0   400) *
        4,1,0   401) *
        4,2,0   402) *
        4,3,0   403) *
        4,4,0   404) *
        4,5,0   405) *
        4,6,0   406) *
        4,7,0   407) *
wodim: No target found.

```
once again, nothing... so im like, ok, time for a "sudo lshw"
```

        *-ide:0
             description: IDE interface
             product: MCP73 IDE
             vendor: nVidia Corporation
             physical id: 8
             bus info: pci@0000:00:08.0
             logical name: scsi4
             version: a1
             width: 32 bits
             clock: 66MHz
             capabilities: ide pm bus_master cap_list emulated
             configuration: driver=pata_amd latency=0 maxlatency=1 mingnt=3
             resources: irq:0 ioport:1f0(size=8) ioport:3f6 ioport:170(size=8) ioport:376 ioport:ffa0(size=16)
           *-cdrom
                description: DVD-RAM writer
                physical id: 0.1.0
                bus info: scsi@4:0.1.0
                logical name: /dev/cdrom
                logical name: /dev/cdrw
                logical name: /dev/dvd
                logical name: /dev/dvdrw
                logical name: /dev/scd0
                logical name: /dev/sr0
                capabilities: audio cd-r cd-rw dvd dvd-r dvd-ram
                configuration: status=open

```
Well its there, but i already knew that, i mean, the bios sees it, i installed ubuntu from it, lshw sees it, so any clue why wodim/k3b cant find it?

---

### Post by Nythain on 2010-05-29
bumpity bump... no else has had this problem with lucid?

---

### Post by Nythain on 2010-05-29
After reading a few forum threads, I have discovered what I would call a "workaround" for this problem... i literally had to reboot my computer with a disc in the drive, and not an empty disc, but a disc with something to read on it.

there's no way im marking this solved though untill someone can either explain to me why i had to reboot with a disc in to get ubuntu to realize i have a dvd burner or untill someone can tell me what to do to keep me from having to reboot every time i want to burn something

---

### Post by jacksonz123z on 2010-05-30
I dual boot Lucid 32 and 64 bit. The optical drive works normally with the 32 bit, however the 64 bit will not recognize the optical drive.  That's a big problem!

---

### Post by jacksonz123z on 2010-06-01
Ok today it works, no problem.  I did not change anything..

---

### Post by dummy910 on 2010-06-01
for future reference, i would also like to suggest checking the users account **privileges** as well... System>Administration>Users and Groups>_A_dvanced Settings(button)>User Privileges(tab)> place a check next to hardware you want the account to have full access to use.

---

### Post by Nythain on 2010-06-11
sadly enough, not working again :(

---

### Post by ankspo71 on 2010-06-11
> **Nythain said:**
> After reading a few forum threads, I have discovered what I would call a "workaround" for this problem... i literally had to reboot my computer with a disc in the drive, and not an empty disc, but a disc with something to read on it.

there's no way im marking this solved though untill someone can either explain to me why i had to reboot with a disc in to get ubuntu to realize i have a dvd burner or untill someone can tell me what to do to keep me from having to reboot every time i want to burn something

Hi
[https://bugs.launchpad.net/ubuntu/+source/udev/+bug/562092](https://bugs.launchpad.net/ubuntu/+source/udev/+bug/562092)
This is a bug report that I think describes the problem we're having. If you have the time, say it effects you too (requires registration) It effects me in ubuntu and kubuntu (lucid) as well. In my case, I have been able to narrow it down to the current Lucid kernels. Lucid Kernel 2.6.32-21 'sometimes' works for me, but not always. Kernel 2.6.32-22 doesn't work for me at all (not since getting updates for them). Will it work for you with a blank cd if you boot into the 2.6.32-21 kernel?

---

### Post by Nythain on 2010-06-11
yeah, but it HAS to be blank... if i have a data dvd in the drive, its a no go still

---

### Post by Nythain on 2010-06-11
i see you stated that the 2.6.33 kernels work properly for you... are they still holding true or suffering now also? think it would be worth a kernel upgrade to try to fix my problem?

*edit* I decided to give upgrading the kernel a try, upgraded to 2.6.35-2-generic and everything is working fine so far, booted with empty drive, inserted a data dvd, got notification and mount... thanks mate

---

### Post by ankspo71 on 2010-06-11
yes and no. The trouble there is I think those kernels aren't compiled for use with proprietary graphics drivers. If I was okay with using the open source graphics drivers I would be using those kernels now. Installing them on this computer with the Nvidia non-free drivers installed gives me the black screen of death, but they seem to work great with the Nouveau drivers (Ubuntu's default driver for nvidia cards). I think the kernels need to be compiled from source if we want 3d effects etc.

---

### Post by Nythain on 2010-06-11
hmmm... i didnt encounter any problems with the proprietary nvidia drivers... did you manually install your nvidia drivers or use repo package? because im now running 2.6.35 with the packaged nvidia drivers just fine

---

### Post by ankspo71 on 2010-06-11
Hi again,
I use the Nvidia "current" drivers offered by the Hardware Manager. I don't have any problems with them either with Lucid's kernels. When I was testing the newer kernels from the PPA, I tested them on a clean install of Kubuntu (no third party drivers installed yet) and they worked great. About a week later, when I went to install my Nvidia drivers through the hardware manager, I got no display on the next boot. That is where I went back to the default kernels (I reinstalled kubuntu again) and unplugged my external dvd drive. That is where my cd problem went back to working again (as I said in my update on the bug report), but then later the updates for the 32 kernels made my drive dysfunctional (again). Now I can only access my cds using the original kernel, but only sometimes. Luckily, I have an external burner that I can plug in and use, otherwise I would be forced to dual boot.

I haven't tried a manual installation with Nvidia drivers from the Nvidia site.

If you decide to try this, backup everything first...just in case.

---

### Post by ankspo71 on 2010-06-11
> **Nythain said:**
> hmmm... i didnt encounter any problems with the proprietary nvidia drivers... did you manually install your nvidia drivers or use repo package? because im now running 2.6.35 with the packaged nvidia drivers just fine

Huh? You already installed it? That was fast. I didn't catch that when I read this post the first time. I thought you were thinking it over.

So how is your optical drive doing?

PS. I hope you don't get the black screen on your next reboot.

---

### Post by Nythain on 2010-06-11
so far, no problems with the optical drive and no black screen, but i've only booted twice since im about to trigger an fsck on 2TB worth of data.

thanks again for the kernel suggestion, here's hoping it stays a permanent fix

---

### Post by squidpotion on 2010-07-03
The same thing happened to me recently. Not only did it not detect my optical drives, Ubuntu didn't detect my external HD on boot up neither. I tried uninstalling K3B hoping everything would go back to normal, but it still hasn't. The keyring screen also lags when it boots up. I don't know why it doesn't detect my drives (the external being USB), but it detects my wireless adapter and mouse. 

I read in another post that simply reinstalling the HAL might be a fix. Any suggestions?

---

