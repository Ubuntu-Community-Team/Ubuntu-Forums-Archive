---
title: "Dual Boot:  Grub issues w/ Vista?"
date: 2010-05-04
forum: General Help
---

### Post by danloz on 2010-05-04
Hi folks:  

I'm pretty sure there's an answer here, but I'm having a lot of difficulty coming up with the right combination of keywords to search under.  

-Compaq laptop, about a year old.  Came with vista.  

-Installed Kubuntu, in the 9 series somewhere, experienced occasional bouts where vista wouldn't boot up.  The problem is 'intermittent:  if I reboot enough times eventually vista will hold and I can get in.

-Gradually, the problem has gotten worse.  

-I've ignored it, because ---like----I run kubuntu, what do I need Vista for?  The answer:  A man name Sam Fisher desperately needs my help.  

------------

What actually happens:  
When I power up I get grub.  I select Vista from the list.  The Vista load screen (with the animated progress bar thingy) comes up and goes just fine.  While this screen is up, the computer goes into a reboot.  The lights go out momentarily and it's back to grub.  Typically, Vista gives the "start up repair" or "boot normal" options.  

-----

What I've tried:  A format.  Twice.  Not for the reasons described here.  

Why I think it's somehow tied to grub?  Both times I had to format I used factory disks to install vista.  The vista install worked fine - until I popped kubuntu on it.  Although, it's totally beyond me why the problem would be intermittent.




------
Forgot to add, inevitable questions:  
It's kubuntu 64
Single hard drive, 3 partitions (1 is the 'recovery partition')

---

### Post by GSF1200S on 2010-05-04
> **danloz said:**
> Hi folks:  

I'm pretty sure there's an answer here, but I'm having a lot of difficulty coming up with the right combination of keywords to search under.  

-Compaq laptop, about a year old.  Came with vista.  

-Installed Kubuntu, in the 9 series somewhere, experienced occasional bouts where vista wouldn't boot up.  The problem is 'intermittent:  if I reboot enough times eventually vista will hold and I can get in.

-Gradually, the problem has gotten worse.  

-I've ignored it, because ---like----I run kubuntu, what do I need Vista for?  The answer:  A man name Sam Fisher desperately needs my help.  

------------

What actually happens:  
When I power up I get grub.  I select Vista from the list.  The Vista load screen (with the animated progress bar thingy) comes up and goes just fine.  While this screen is up, the computer goes into a reboot.  The lights go out momentarily and it's back to grub.  Typically, Vista gives the "start up repair" or "boot normal" options.  

-----

What I've tried:  A format.  Twice.  Not for the reasons described here.  

Why I think it's somehow tied to grub?  Both times I had to format I used factory disks to install vista.  The vista install worked fine - until I popped kubuntu on it.  Although, it's totally beyond me why the problem would be intermittent.

Im sorry to say, but this isnt something you can fix with a grub command :(
If the Windows Vista logo comes up (its booting), then grub has done its job of locating the windows boot files and initiating them- from the point that vista comes up, grub and linux dont exist anymore. It sounds to me like maybe you have a hard drive that is failing, considering you have reinstalled Vista twice as youve said. I would seriously back up any important data to an external hard drive at the very least!

Does your BIOS (or perhaps you could try a smart utility like one found in the repos) allow you to see how many reallocated sectors a given drive has? If youre drive is reallocating sectors, make sure you have a backup...

---

### Post by Tregajorren on 2010-05-23
I am in the same situation: Year old Compaq notebook (CQ60) with a Vista/Ubuntu (10.04, 64bit) partitioned drive.

A pending hard drive failure sounds like a bit of a red-herring to me: My Hard drive is a week old - I upgraded it last week, so it is an unlikely cause here. 

> **danloz said:**
> The vista install worked fine - until I popped kubuntu on it.

Is also a pointer to it not being a failing HDD is it not?

In my case, I'm still booting to Vista most of the time at the moment, so its set as the default boot option.

Is the error reported by Vista after selecting the 'recovery' when the boot fails the same?

0xc000000f
The Boot selection failed because a required device is inaccessible
 
Presently whatever it is that is causing this Vista boot problem has been hitting my Compaq on an almost daily basis. It is not happening after every shut down, but I am getting it (seems like at least) daily, so I am keen to get to the bottom of this.

I have been resetting the Vista mbr with a recovery CD and using bootrec /fixmbr and bootrec /fixboot in the console then doing a reinstall of Grub.

The recovery disc is from: [http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/](http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/)
The grub instructions are here: [https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD](https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD)

Allowing the Vista recovery disc to do its bit and attempt a recovery also worked. Took ages, but did save me from reinstalling grub that time. If I remember right, the log mentioned it fixed 1 error (with a system restore) and something about an unexpected configuration change. It also mentioned Grub somewhere earlier in the 'report', but with having no error next to it.

I forget if I have tried just booting Ubuntu, doing 'update-grub' and 'grub-install'. 

 The coincidence of the OPs Compaq failing to boot makes me think that  this is maybe something from HP on Vista trying to 'fix' something. Perhaps even on a schedule. After this last restore of Grub, I am trying Vista with the bundled HP utilities 'HP Health Check Schediler' and 'HP Software Update' disabled from running at start-up. Normally I would disable most of the start-up crap anyway - I just didn't do it yet.

I have also enabled boot logging through msconfig in an effort to get more info if/when it happens again.

---

### Post by Tregajorren on 2010-05-25
Just thought I'd close by saying that it was not the HP health check app. - It was only a guess that it may have been. There are still other HP services, but I think that those are to do with things like the DVD autoplay, hotkeys and 'function keys' such as the volume control.

Possibly it is windows defender. Possibly (on my HP) it is Comodo security suite. I give up bothering to find out.

I decided to try EasyBCD from [neosmart]("http://neosmart.net/") instead to chainload Ubuntu from the Vista boot menu. The (currently) [Beta 2.0]("http://neosmart.net/forums/showthread.php?t=642") is the one to get for Grub2 and so far all is well. I suppose too that by using the Vista boot, there is less likelihood of having failed updates as well.

---

