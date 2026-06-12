---
title: "Auto-delete filesystem?"
date: 2009-10-14
forum: General Help
---

### Post by t0p on 2009-10-14
I would like to set up my laptop so that x number of failed logins due to wrong password will cause the machine to wipe the hard drive? Like with DBAN, or dd overwriting the disk with zeroes?

---

### Post by kanikilu on 2009-10-14
There was a thread on this, but no clear answer:

[http://ubuntuforums.org/showthread.php?t=1132612](http://ubuntuforums.org/showthread.php?t=1132612)

I can see the practicality of this, but I'd probably just encrypt the drive and call it a day ;)

---

### Post by t0p on 2009-10-14
> **kanikilu said:**
> There was thread on this, but no clear answer:

[http://ubuntuforums.org/showthread.php?t=1132612](http://ubuntuforums.org/showthread.php?t=1132612)

I can see the practicality of this, but I'd probably just encrypt the drive and call it a day ;)

But that wouldn't do! The NSA could probably use their supercomputers to decrypt an encrypted filesystem. And I wouldn't want the NSA to see my pr0n collection! ;)

---

### Post by t0p on 2009-10-14
Following on from kanikulu's post and the thread it links to: 

Assuming the /home directory is on its own partition: is /home already mounted when the login screen appears?

---

### Post by KeyserSoze93 on 2009-10-14
> **t0p said:**
> Following on from kanikulu's post and the thread it links to: 

Assuming the /home directory is on its own partition: is /home already mounted when the login screen appears?

Not AFAIK, I've been able to unmount /home when the login screen is open, but try it.

---

### Post by StuartN on 2009-10-14
> **t0p said:**
> I would like to set up my laptop so that x number of failed logins due to wrong password will cause the machine to wipe the hard drive? Like with DBAN, or dd overwriting the disk with zeroes?

I like the way Mel Gibson did it in Conspiracy Theory, with well placed phosphorus and strips of magnesium. Total erasure.

But back to your laptop, no it would not work unless it was enforced by the BIOS. Just stick any Linux CD (or even DOS disk!) in the drive and you bypass any login security. Anyone wanting your [pr0n]("http://images.google.ie/images?hl=en&source=hp&q=prawn&btnG=Search+Images&gbv=2&aq=f&oq=") collection would know that.

You would need to think of security that would work on an external hard disk too (because removing your disk is also an option for the determined NSA agent), which comes down to encryption or camouflage.

---

### Post by kanikilu on 2009-10-14
> **StuartN said:**
> You would need to think of security that would work on an external hard disk too (because removing your disk is also an option for the determined NSA agent), which comes down to encryption or camouflage. True. I've removed hard drives from various laptops - some makes/models are more difficult to get into than others (Sony Vaio comes to mind...the one I worked on pretty much had to be stripped to the motherboard to get at the hard drive), but the fact remains that if someone wants it, they'll get it.

I have to think that someone that resorts to sitting there trying passwords by hand, is not smart enough to break encryption, so, a strong password + [encryption]("https://help.ubuntu.com/community/EncryptedFilesystems") = win :D

---

### Post by blur xc on 2009-10-14
> **StuartN said:**
> You would need to think of security that would work on an external hard disk too (because removing your disk is also an option for the determined NSA agent), which comes down to encryption or camouflage.


Yeah, seriously- I'm no expert cyber criminal data theif, but if I found a laptop and wanted to see what was on the hdd, I'd just yank the drive, stick it in an external enclosure and plug it into a usb port, mount the drive and viola- unless of course it was encrypted...  then I'd probably smash it w/ a hammer or something (j/k)...

BM

---

### Post by undecim on 2009-10-14
If you wanted to do this, it would have to be a hardware-based solution, otherwise I could just remove your drive and read your data in my spare time.

You could do something like the black hat hacker in *How to Own a Continent* did: He had a data center enclosed in a large steel room that he welded together and set up thermite over all of his drives. He had sensors to detect possible physical intrusions, an IDS to detect successful cyber-attacks, and a keypad behind the first of two doors that required a 64-character password before it would unlock a second door to the actual computers. If you tried to break in by force, got the password wrong 3 times in a row, or took longer than 30 seconds to type in the password after opening the first door, the thermite would ignite, burning through each drive and the foundation of the building (this whole setup was in his basement) in a matter of seconds.

Though, that guy was also organizing a group of hackers and money launderers to steal billions of dollars from an African bank. He had a very real reason to be fearful of the government.

If you really want a software-based solution (i.e. there is no threat of bypassing the software; you modify your BIOS to only boot the hard drive, somehow prevent that setting from being changed, and put some kind of explosive to go off if anyone touches your computer with a screw driver) You would need to look at creating a script to erase the drive, and then using pam_exec to execute that script if the login fails (though I have no idea how to do that... I'm still learning about authentication modules in Linux myself.)

Or, better yet, if the software-based solution would be adequate, because you have eliminated the threat of bypassing that software, encryption will be plenty good enough, and you don't have to worry about losing your files when you get unlucky typos 3 times in a row. No matter how you look at it, encryption is a better solution to erasing the drive.

---

### Post by kayvortex on 2009-10-14
Unless your BIOS is password protected and your discs encrypted, it is pretty easy to gain access to your system if you have physical access to it.

Good encryption is probably enough unless you're prepared to buy some seriously paranoid hardware: unless the NSA build a quantum algorithm, or solve the p vs np problem in favour of a reverse computation algorithm (and it's not as if they're not trying!), then anything else would probably just be overkill.

Still, I suppose you could do it you have a separate partition for /home. You could then modify your init.d scripts and gnome config files so that /home only gets mounted on a successful password, or else formated if the pasword is wrong *n* times.

---

### Post by t0p on 2009-10-14
Maybe I should just boobytrap the laptop with thermite charges. Fiddle with the screws and WHOOMPH! no more laptop. Hehe.

---

### Post by kayvortex on 2009-10-14
> Maybe I should just boobytrap the laptop with thermite charges. Fiddle with the screws and WHOOMPH! no more laptop. Hehe.

Oo! Oo! Shotgun I get to turn the screw!!

Seriously, though, encryption is probably enough. If you wanted to destroy data after some amount of incorrect passwords, you'd also have to make sure that your system settings couldn't be changed once your system's been booted up. Basically, you'd have to do a lot of work for not much practical benefit.

---

