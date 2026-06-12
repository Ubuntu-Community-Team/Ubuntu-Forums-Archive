---
title: "Unable to mount Hard Drive, &quot;loopy&quot; help files"
date: 2010-06-02
forum: General Help
---

### Post by KrapuulX on 2010-06-02
Greetings fellow Ubuntu-geeks,

I seem to be having a little problem and so far my googling and console wizardry keeps pointing at things I have tried already. I am wondering if any of you could throw me a bone here.

What happened:
I didn't have Linux until the day Windows crashed on me for the gazillionth time. I was simply playing some music in Windows Media Player as the entire PC froze. No CTRL+ALT+DEL, no alt F4... so I was forced to hard-reset my computer using the ON-button. After that it never launched Windows again simply because it didn't feel like it.

Now, we're not here to find out why Windows is a bitch about all this, my real problem lays somewhere else. Seeing as a lot of important files were on my Windows drive I figured I could just install Linux on the other drive and fetch the files from there. The problem is I can't. Every time I attempt to open the disk I get the following error:

> Cannot mount volume.
Unable to mount the volume.

Hibernated non-system partition, refused to mount. Failed to mount '/dev/sda2': Operation not permitted. The NTFS partition is hibernated. Please resume and shutdown Windows properly, or mount the volume 'read-only' with the ro-option. Or mount the volume 'read-write' with the remove_hiberfile-option.
```
mount -t ntfs-3g /dev/sda2 /media/disk -o remove_hiberfile
```I've tried both the ro-option and the remove_hiberfile but in both cases I'm given this error in the console:

> Mount is denied because NTFS is marked to be in use. 
Choose one action:

Choice 1: If you have Windows.. click on the 'Safely Remove Hardware' icon in Windows task bar to shutdown Windows cleanly..

Choice 2: If you do not have Windows then you can use the 'force' option...And thus looping me back to the first command, upon entering I will again receive the first error. I hope you understand my frustration.

Things I have tried:
- said commands or slight variants
- re-installing windows (gets stuck during installation)
- used the Ultimate Boot CD in an attempt to access and copy the files from my Windows Drive onto an external hard drive / my Linux drive
- clicking the Drive icon furiously for a period of time in hope of a different result (which obviously did not work)

Seeing as I can't screw open my laptop and take the drive out I'm really hoping there is some way for me to connect to the drive from Linux and extract the files.

Stuff I've learned:
- most likely my Windows system files have gone corrupt and I will need a format, but I'm not willing to do that unless I'm a 100% sure there is no way for me to extract the files first.
- the console screen called me stupid

About my computer:
I have an Acer ASPIRE 7720G (laptop) running an Intel Core Duo T7500 and have 2 physical hard drives (each as one large partition) of 500GB, further more it has 4GB DDR2 RAM memory and a fancy graphics card.

Thanks in advance,
KrapuulX

On a side-note: I'm really enjoying Linux, I wasn't aware how powerful it was untill I actually started using it frequently. Go Tux! <3

---

### Post by jerome1232 on 2010-06-02
Try running ntfsfix, it should remove the dirty unmounted flag and remove the hibernation file for ya all in one fel swoop.

```
sudo ntfsfix /dev/sda2
```

---

### Post by KrapuulX on 2010-06-02
Thank you for the swift reply.

I've done as you suggested and received the following error report in the console.

> Mounting volume... FAILED
Attempting to correct errors... 
Processing $MFT and $MFTMirr...
Reading $MFT... OK
Reading $MFTMirr... OK
Comparing $MFTMirr to $MFT... OK
Processing of $MFT and $MFTMirr completed successfully.
Setting required flags on partition... OK
Going to empty the journal ($LogFile)... OK
Remount failed: Operation not permitted.

Afterwards I was still not able to access the HD.

Greetings,
KrapuulX

---

### Post by jerome1232 on 2010-06-02
same error message?

---

### Post by KrapuulX on 2010-06-03
Not the same as the ones I received at first. The ntfsfix-command only gave me what I pasted in my previous response. It's a copy-pasta from the console. So technically no error message but just a report telling me it failed. Would you prefer if I took screenshots of my console screen?

EDIT: Sorry, I misunderstood the question. When trying to enter the HD after the ntfsfix I **did get the same error message***. I should've read your response more carefully. :)

*> Cannot mount volume.
Unable to mount the volume.

Hibernated non-system partition, refused to mount. Failed to mount '/dev/sda2': Operation not permitted. The NTFS partition is hibernated. Please resume and shutdown Windows properly, or mount the volume 'read-only' with the ro-option. Or mount the volume 'read-write' with the remove_hiberfile option.
     ```
mount -t ntfs-3g /dev/sda2 /media/disk -o remove_hiberfile
```


---

### Post by jerome1232 on 2010-06-03
So it that the error it fails with when you try a regular mount, or is that the error you get when you mount it with the '-o remove_hyberfile' option?

Sorry I'm just confused about whether you are trying to mount it with the mount command you are posting or if you are just getting an error when you click on it's icon to mount it..

---

### Post by KrapuulX on 2010-06-03
When I click the icon I receive the first error, the one that asks me to mount the HD from the console. When I try and mount it in the console using the command given to me by the first error message, I receive the second error message and it supplies me with a new command to try. Upon entering said command I again receive the very first error message.

When using ntfsfix I get the report I pasted in my previous reply where it states that the HD is not mounted.

So yes, clicking the icon and attempting to manually mount it in the console give me the same error message.

Sorry if I have caused any confusion,
KrapuulX

---

### Post by KrapuulX on 2010-06-05
Update!

I actually got my terminal to report that the HD I am trying to retreive files from is corrupt and hence why I'm sort of unable to mount it. I'm just going to throw in the towel and presume my files are forever lost. Is there a way for me to format said drive.. without it being mounted?

---

### Post by jerome1232 on 2010-06-05
photorec could still recover files. You could give that a try.

as for your question yes you actually HAVE to have partitions unmounted to format them. Easiest way is to use gparted, you can install it from synaptic.

---

### Post by KrapuulX on 2010-06-06
When I change the options in Photorec to only recover e.g. .txt files I get segmentation faults. When I do not change anything it starts to recover files, but I've mentioned before the drive is 500GB and it's fairly full. If I keep the options untouched there is no way I can save any of it.

Also, when it created its recup_dir folders to store the files in, I can't access it, not even as root. TestDisk was able to analyse the disk though, slowly at the corrupted levels yes but it was able to run through the entire drive, so I'm going to conclude it's not broken.

Currently I'm in my exam period so I wont be able to format it anytime soon, seeing as I'm studying IT I sort of need a working OS and Linux is doing just fine. In 2 weeks time I'll just run gpart through both my drives and start scratch. Linux on the primary disk and then I'll install a fresh Windows on the other disk.

Thank you for your help Jerome, it has been a pleasure.
KrapuulX

---

