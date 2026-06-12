---
title: "Terrible boot time in 11.04"
date: 2011-04-29
forum: General Help
---

### Post by aG93IGRvIGkgdWJ1bnR1Pw== on 2011-04-29
On my Asus 1018P netbook, the boot time has seriously regressed from 10.10. It now usually takes around 1 minute. What can I do about this? Bootchart attached.

[bootchart](http://dl.dropbox.com/u/1509348/bootchart.png)

---

### Post by aG93IGRvIGkgdWJ1bnR1Pw== on 2011-04-29
bump

---

### Post by aG93IGRvIGkgdWJ1bnR1Pw== on 2011-04-30
bump #2

---

### Post by cimh on 2011-05-01
You have 2 options

1. get unity 2d this is much faster booting and more responsive on my eee901 (switch on to wifi connected = 29s). I cant remember if 2d is in the repository or not but a quick search will tell you. Once you have downloaded it goto the login screen and select it as your default startup.

2. go to the login screen and choose 'classic gnome' as your default start up (unity doesnt do anything for me). I havent used a stop watch but I think this may be a second faster than 2d. So a sub 30s boot to wifi is just the same as 10.10. 

Feel free to add you findings to my boot time spreadsheet.

[https://spreadsheets.google.com/ccc?key=0Aib-MC2xtkLhcFRBaGJ1Q3o4WUJSSHNvUzdQNFM2T3c&hl=en_GB](https://spreadsheets.google.com/ccc?key=0Aib-MC2xtkLhcFRBaGJ1Q3o4WUJSSHNvUzdQNFM2T3c&hl=en_GB)


to get these times I get rid of stuff I dont use (eg. ubuntu one) disable many start up programs. 



cimh
901 
11.04 & peppermint ice

---

### Post by lithopsian on 2011-05-03
> **cimh said:**
> You have 2 options...

You're kidding, right?  Did you even look at the bootchart?  Both those options suck and have nothing to do with why this boot took so long.

The only thing I can say is odd at this point is that most of your boot is taken up with the fsck.ext4 job.  This disk check should take a second or two on a normal boot, and should only do a full check maybe every 10 or 20 boots depending on your configuration.  Does it do this every boot?  If not, please post a bootchart for a normal boot.

If it does the full fsck on every boot then you may have a disk problem, or you may have it configured in an unusual way.  Look in fstab for the disk check interval.

Other than that, I'd say it is pretty normal.  Take out that 35s, get ureadahead working, and you'll probably be happy with the boot.

---

### Post by cimh on 2011-05-03
> **lithopsian said:**
> You're kidding, right?  Did you even look at the bootchart?  Both those options suck and have nothing to do with why this boot took so long

What a nice guy - thank you so much for your thoughtful and positive response.

Could I suggest other replies might have been more appropriate -
such as 'I dont agree - I think the real problem is....'

or

'No I dont think your suggestions will help....'

but no, you prefer the rude and unpleasant approach - I dont think that's not a great way to encourage people to try and help. 

But then perhaps us lesser mortals should keep quiet and leave it to the experts like you. 

cheers
cimh

---

### Post by lithopsian on 2011-05-04
I'm not an expert.  I just looked at the bootchart and there is a massive task taking up half the boot time while maxing out IO and CPU.  Until that is fixed, nothing is going to produce a satisfactory boot experience.  I happen to know that that task is a disk check utility that shouldn't be doing all that work on every boot, but that's not rocket science.

---

