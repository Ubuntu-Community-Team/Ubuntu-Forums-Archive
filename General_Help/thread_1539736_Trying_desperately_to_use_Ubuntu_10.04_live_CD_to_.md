---
title: "Trying desperately to use Ubuntu 10.04 live CD to do a virus scan and failing!"
date: 2010-07-26
forum: General Help
---

### Post by ZenStephanie on 2010-07-26
Hello all.

I'd been using the same Dell laptop since 2003 with no problem until a little less than a week ago, when my Windows stopped booting. I had just cleared a virus (or so I thought) that was jacking up the CPU, and afterward installed the latest version of Avast! I let the computer reboot and came back to a black screen. Ever since, I have not been able to get Windows to boot no matter what I do. It won't boot from the hard drive in any mode, it won't even boot from the Windows CD-Rom I have. I downloaded the Recovery Console onto six floppy disks, which my computer read, but then wouldn't run after the last disk, saying there was a virus requiring Windows to shut down.

I was at a loss until I remembered Ubuntu, of which my stepdad is a faithful user. Got a friend to burn an Ubuntu live CD, and sure enough, it started up no problem. I've been able to open my hard drive and access files on it, so I know they're still there.

My goal is to (1) scan and clean the hard drive for any viruses, (2) back up the contents of the hard drive to an external hard drive, and (3) install Ubuntu as a dual boot system so that I can use it in addition to Windows, or instead of Windows if Windows is unrecoverable, until I can get a new computer. I don't want to install Ubuntu on the hard disk until I've backed up my files, and I don't want to back up my files until I've been able to scan and clear any remaining viruses...

The problem is that I cannot get an antivirus program to work from the live CD. I faithfully followed the instructions on [this site]("http://www.howtogeek.com/howto/14434/scan-a-windows-pc-for-viruses-from-a-ubuntu-live-cd/") to install and update avast Linux home version, but they didn't work. Even after properly entering all commands instructed by the site, when I try to update to the newest virus database, avast! crashes and won't re-start, even to the point other programs start to crash. I then tried to use Clam AV but got an error that it was outdated and couldn't figure out how to get the newest version on the computer.

So I'm very frustrated and I imagine there must be *some* solution! I don't know if the problem is using the live CD (which means I can't use a reboot to try to make things work) or if the problem is with 10.04, because it seems these fixes and instructions I find are for other, older Ubuntu versions.

I'm not even sure the problem with Windows is a virus--I think it's also possible the boot file got corrupted by the new install of Avast (that is when it crashed). I've also heard that if you try to install a new version of Avast without manually installing the old Avast, which is exactly what I did, the old avast! may react to the new one as if it is a virus.

That said, I don't want to take any chances and don't want to back up my files before doing a virus scan. For reasons I don't want or need to go into here, I don't immediately have access to someone who could burn more CDs for me, so an antivirus rescue CD is not the most attractive option. If *anyone* could help me get avast working from the live CD (or, if not Avast, another program), I would be very grateful!

---

### Post by ezsit on 2010-07-26
> That said, I don't want to take any chances and don't want to back up my files before doing a virus scan.

Most viruses will plant themselves in system folders and files related to the bootup processes. I would definitely backup your files while you have access to them. It is easy enough to put your backup files on a flash drive and scan that drive for viruses on another computer. If the scan comes up clean, then I would wipe your old hard drive and reinstall Windows from scratch. Even if you think you've cleaned your old Windows installation, a virus infection can find ways to rear its ugly head.

---

### Post by ZenStephanie on 2010-07-26
Wow, thanks for the fast response. I've figured that if I back the files up and there's a virus in them, I can always "re-back them up" if I'm later able to scan and clean the files.As soon as I have a chance, I'm still going to buy the backup drive and do the backup, even if I haven't been able to do the virus scan. I'd still like to figure out how to get Avast to run properly from the live CD, but I'm wondering if I might not be able to get things to work better if I had Ubuntu installed on my hard drive and could reboot it after changing settings, etc. Which I don't want to do until I've backed up the files.

Main thing is, I don't want to lose the files. I guess I'm scared that if I move a virus onto the backup hard disk along with the files I'm backing up, it could cause them to become corrupted or inaccessible. Even if I never get Windows to run again, that's OK... I'm just squeezing whatever life I can out of this computer until the money and timing is right to get a new one (planning on getting a Mac). Main thing is I want my files to survive in accessible and usable form.

I would like to figure out what happened in general also; I'm not even sure what caused the crash was a virus. It crashed after I installed the latest version of Avast! I didn't realize you had to manually uninstall the old version, and I'm wondering if this double install could have caused problems with the boot file or with one thinking the other is a virus, etc.

---

### Post by ezsit on 2010-07-26
I know you mentioned that downloading and burning another LiveCD was not optimal, but if you can give it a try:

[http://www.freedrweb.com/livecd/](http://www.freedrweb.com/livecd/)

Here is a Linux distro that includes a virus scanner specifically meant to rescue Windows systems. It might be easier than trying to get Avast to work. Dr. Web Cure It Live CD is updated everyday, so it is always at the latest version.

---

### Post by confused57 on 2010-07-26
You might also want to try the AVG Rescue CD, which is a live cd, and if you have an internet connection it can update the virus definitions and perform a scan on your system:
[http://www.avg.com/us-en/avg-rescue-cd](http://www.avg.com/us-en/avg-rescue-cd)

---

### Post by no2498 on 2010-07-27
does he not need to install Avast first then look for updates
then run it
dont think it will run from the cd only

was just reading the how to the other day
i do not have windows on my 2 computers so i didnt retain much of it

hope it give someone else a spark

---

### Post by Mark Phelps on 2010-07-27
> **no2498 said:**
> does he not need to install Avast first then look for updates ...

No -- it is a Rescue CD and is bootable.  Once running, you can go online to download the most current AV info.  Then, you run the program to do the virus scan.

Nothing needs to be installed.

---

### Post by ZenStephanie on 2010-07-30
I appreciate the direct links, but, again, I have no one local who can do this for me and would have to take someone through the process over the phone and have them mail me the CD. I'm looking to see if there is an *alternative*...
 
So is there any alternative to burning another live CD? No one has any idea how to get an up to date antivirus program to run off of an Ubuntu 10.04 live CD?

---

### Post by howefield on 2010-07-30
> **ZenStephanie said:**
> So is there any alternative to burning another live CD?

If you can't use a CD, how about a USB pen drive ?

---

