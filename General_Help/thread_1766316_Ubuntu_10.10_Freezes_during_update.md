---
title: "Ubuntu 10.10 Freezes during update"
date: 2011-05-24
forum: General Help
---

### Post by abe12345 on 2011-05-24
I'm new to linux.  I have an AMD64 1.8GHz, 3GB ram.  Earlier I tried installing 11.04 but it kept freezing during update.  I even tried classic mode but same general result.  So then I installed 10.10 and after installation the computer froze during the update process again.

---

### Post by Topsiho on 2011-05-24
If the computer freezes during a process (such as updating) it might be looking for a file that it can't find, but expected to find on your computer, or it might run out of resources on your computer, such as working memory or so. As you have 3 GiB of memory, that's out of the question.

Another something that might be the cause is defective hardware. First thing, and easy to check, which comes to mind is memory. You can check this using your LiveCD, satrting up from it, and choose the option to check memory, and let this go through a number of passes.

It is not clear from your message what you mean with update, probably the updates that you should do after an install.

Did you check the integrity of your LiveCDs? That is also an option one gets after starting up from the LiveCD, and which you should do before installing from it.

Topsiho

---

### Post by abe12345 on 2011-05-24
It freezes after installation completes, during update.  Originally it would freeze during installation when I was installing 11.04 through the normal graphics based installation.  Then I switched to alternate installation, which managed to complete the install but froze when I tried to update through the operating system.  Same result for 10.10.
 
I did the memory test and it found some errors, though I don't know how to interpret the results.  Image of results: [http://imageshack.us/photo/my-images/836/memteste.jpg/](http://imageshack.us/photo/my-images/836/memteste.jpg/)
 
But I don't see how the RAM could be a significant problem because I'm running XP on it without issues, for year now.

---

### Post by linuxinstalledfromhdd on 2011-05-24
I would wait a while before upgrading to the latest version of Ubuntu. Natty just came out, and there are still quite a few issues.  If you want to test Natty first before actually installing it, create a live "persistant" USB stick of Ubuntu 11.04 and test your system before actually upgrading it.  Make sure the applications you need can run in it on the live stick first. That way you know what you may be in for with 11.04.

---

### Post by abe12345 on 2011-05-24
But it's freezing with 10.10 too.  Is there another good Linux operating system that might be more stable for my setup?

---

### Post by linuxinstalledfromhdd on 2011-05-25
It sounds like it could be a hardware issue. It depends how old your system is. You may wish to review your log files and review them for errors, and post whatever you find that looks strange.  Maybe we can try to figure it out that way. 

Yes, you can keep rolling back as far as it takes to see if you gain stability. Sometimes that helps.  I wouldn't go further back that 9.04 though.

---

### Post by abe12345 on 2011-05-25
I rebooted in failsafe graphic mode and it gave me some error notices and told me to run some commands.  Then I updated the packages and for the first time it completed, though it is running in failsafe mode now.  
UPDATE: The normal version of 10.10 seems to be running smoothly also.
One package is not installing, PDF rendering library:

installArchives() failed: (Reading database ...  (Reading database ... 5% (Reading database ... 10% (Reading database ... 15% (Reading database ... 20% (Reading database ... 25% (Reading database ... 30% (Reading database ... 35% (Reading database ... 40% (Reading database ... 45% (Reading database ... 50% (Reading database ... 55% (Reading database ... 60% (Reading database ... 65% (Reading database ... 70% (Reading database ... 75% (Reading database ... 80% (Reading database ... 85% (Reading database ... 90% (Reading database ... 95% (Reading database ... 100% (Reading database ... 142650 files and directories currently installed.) 
Preparing to replace libpoppler7 0.14.3-0ubuntu1 (using .../libpoppler7_0.14.3-0ubuntu1.2_amd64.deb) ... 
Unpacking replacement libpoppler7 ... 
dpkg-deb (subprocess): data: internal gzip read error: '<fd:0>: invalid distance too far back' 
dpkg-deb: subprocess <decompress> returned error exit status 2 
dpkg: error processing /var/cache/apt/archives/libpoppler7_0.14.3-0ubuntu1.2_amd64.deb (--unpack): 
 short read on buffer copy for backend dpkg-deb during `./usr/share/doc/libpoppler7/copyright' 
No apport report written because MaxReports is reached already
Errors were encountered while processing: 
 /var/cache/apt/archives/libpoppler7_0.14.3-0ubuntu1.2_amd64.deb

---

### Post by Topsiho on 2011-05-25
I think the problem is solved. The ram you have IS defective, so should be replaced, or possibly you have to remove the defective part of it. You'll have to try and take out one of the strips, one at a time, and try again, until you have found the culprit, which of course you remove.

That Windows XP runs without a problem doesn't say anything: if I remember correctly you have 6 GiB of ram in your computer, and a 32 bit system such as Windows XP uses only part of it, 4 GiB I think.

So please correct your memory first. If "only" 4 GiB or so remain, that's usually quite enough.

Greetings,

Topsiho

---

### Post by Topsiho on 2011-05-25
I just noticed you have only 3 GiB of ram, from scrutinizing the image of your memory check again, and from rereading your original post.

Still I think you must first have good ram in your computer before doing anything else. With defective ram you never can trust your computer.

Also the defective addresses are very high (2799 MB), so Windows XP may never have used these, and Linux does, because Linux (Ubuntu) uses available memory more effectively. It also indicates what memory strip is defective, but I can't tell you which. If you have three strips of 1 GiB each, from thinking logically it must be one of the outer strips, but as strips may be organized in banks, it might be the strip that is only the lonely in a bank. So just trying is the way to go.

So I still think your problem is solved :)

Topsiho

---

### Post by abe12345 on 2011-05-25
That sounds logical.  In fact the non-recovery mode version which earlier I said seems to be working fine just crashed when I was running Gimp graphics application, which is RAM intensive I assume.  I will test each RAM individually and seem if I can replace them.  Then I will come back with the results.

Another question: why are there 2 versions of Ubuntu on startup?  I only made 2 partitions, 1 for XP and 1 for Ubuntu.  See attachment.

---

### Post by plucky on 2011-05-25
> **abe12345 said:**
> That sounds logical.  In fact the non-recovery mode version which earlier I said seems to be working fine just crashed when I was running Gimp graphics application, which is RAM intensive I assume.  I will test each RAM individually and seem if I can replace them.  Then I will come back with the results.

Another question: why are there 2 versions of Ubuntu on startup?  I only made 2 partitions, 1 for XP and 1 for Ubuntu.  See attachment.

That is just a Kernel upgrade.You will get a new addition to the grub menu every time the kernel is upgraded.
It is recommended you leave at least 2 kernels,just in case you break the current kernel.You can remove older kernels using Synaptic Package Manager or some recommend "Ubuntu Tweak" to do the job of removing older kernels.


Good Luck

---

### Post by Topsiho on 2011-05-25
That's right.

If you want to see your partitions on the disk you can use System>Administration>Disk Utility (might differ for I had to (re)translate from Dutch, but it must give you a good idea). Selecting your disk gives information of the health of the disk, if the disk supports S.M.A.R.T., and also a graphical layout of the disk.

Primary partitions (sda1 .. sda4 are each apart, logical partitions (sda5 and up, are contained in a primary partition, which is called an extended partition, and which probably is sda2.

A nicer view you get in gparted. That is the application used when you manually partition your disk during the install, but which is removed after install when the installation is finished. You could install it again, but be very careful not to use it really, for changing anything on your disk, if you don't know what you are doing, is dangerous. But viewing does not hurt, and the view is very clear.

I guess you will also see a swap partition, which Linux needs, and is a space on the disk where the contents of ram are swapped to when the ram is needed for something else. So Ubuntu is installed into at least two partitions.

Topsiho

---

### Post by abe12345 on 2011-05-26
I ran memtest on each RAM by itself but found no errors! It was for about 2 passes on each RAM, though on the first I left it in DIMM3 instead of moving it to DIMM1.  

Then I put the RAMs back, but this time switched the DIMs of the 2 outside RAMs, but keeping all 3 RAMs together and ran memtest to see what address range it would give.  It gave 90 errors(pic attached) as opposed to first test ([http://imageshack.us/photo/my-images/836/memteste.jpg/](http://imageshack.us/photo/my-images/836/memteste.jpg/)) which had 6 errors, and the address range was about the same.  I expected it would be different range if it was one of the outside RAMs.

Also the settings line of the report that shows RAM and DDR varies on some of the tests.  The RAM and DDR on the single RAM tests were 200 Mhz and DDR 200 or 2 RAMs and 199 Mhz and DDR 399 on one RAM (SAMSUNG).  

But the full RAM tests were: 100 Mhz DDR 200 (for the two with few errors) and 163 Mhz DDR 327 (the one with 90 errors where I switched the position of the 2 outside RAMs).  

My 3 RAMs are: 2 ebay RAMs (has TA logo), and one Samsung, for a total of 3GB.  The motherboard manual said not to use RAM from different manufacturers, but I doubt that is the problem.  The error addresses show high MB #s: around 2700-2800.  I thought that might mean DIMM 3, which was the Samsung RAM.

I tried running ubuntu with only the two TA RAMs but immediately it crashed before I could run some memory intensive programs.  Now I'm in fail safe mode again with the orignial RAM configuration.

---

### Post by plucky on 2011-05-26
Could be a bad slot.

How long has the slots been empty? 

Infiltration of dirt could cause a bad connection on one of the slots.Get a can of air and blow out the dirt from the slots.

Good Luck

---

### Post by Topsiho on 2011-05-26
I agree with plucky. Though I would not have thought of this myself :)

Using different RAMs can cause (timing) problems, but you tried using the two same RAMs and that didn't work out either.

Also: maybe two passes is not enough to find the individual culprit, if there is one, that's why you really should test eternally, but no one has the patience to do so.

The chance, however, is small that one of the strips is faulty, from your tests (that's what tests are for: to know things).

But certainly the combination, as tested, doesn't work well.

So plucky is right: one of the slots may have gone dirty, or is downright not OK. If you are lucky you can possibly clean it with compressed air.

Instead of RAMs you might test slots now, in the same manner: put a strip in one of the slots at a time, and so test what slot gives problems. And after that: avoid that slot like the measles :)

Topsiho

---

### Post by abe12345 on 2011-05-27
All the RAM slots have now been tested but I found no errors.  There was lots of dust outside DIMM1 from the fan, though it didn't look like it had gotten inside the slot because there was always a RAM in it.  I vaccumed all the slots anyway.  Then I tested the SAMSUNG in DIMM1 and got 1 error after 3 passes on test 4.  This was the first error from a single RAM test.  Is that a significant enough error to replace the RAM?  But bad RAM may not be the issue because Ubuntu crashed with the 2 good RAMs too.

---

### Post by Topsiho on 2011-05-27
Of course this is bad. You should be able to depend on your RAM, it should not give errors no matter how long it is tested.

The problem is: is it the RAM or is it the slot? You should do the tests, different RAMs in different slots, and doing a good number of passes, before you decide RAM and slot are OK.
You experienced that 2 passes is not enough to decide that suspected hardware is OK, but testing eternally (as one should) is not an option. Some time you must decide the hardware is OK. A negative result is more positive than a positive one, if you know what I mean:o

Keeps you from the streets for a while, I suppose.

Hardware you can't trust is useless.

:)

Topsiho

---

### Post by abe12345 on 2011-05-30
I tested each slot for 11-12 hrs but found no errors.

---

