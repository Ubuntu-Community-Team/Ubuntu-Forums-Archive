---
title: "encrypted hard drive fragged- how to recover data?"
date: 2010-02-04
forum: General Help
---

### Post by beakdan on 2010-02-04
Hey folks-

I'm currently running Koala on a Dell Latitude D630.  I've been with Ubuntu since Hardy, so I have some experience, but this is beyond me.

Basically, I was at school, closed my laptop, and bicycled home.  When I opened it up at home, I saw a blank screen.  When I tried to reboot, I was told that the disk couldn't be mounted.

When I boot a LiveCD, I can see my two disk partitions (/ and /home) as "16GB Filesystem" and "95GB Filesystem".  The 16GB system can't be mounted, and I'm pretty sure is fragged.  I tried reinstalling Ubuntu, figuring that would fix it, but no luck- it starts fine, but it gets about halfway through and then says it can't install the files.

The machine is still under a service contract with Dell, so swapping out the HD itself isn't such a big deal.  It would be nice to get my data, though.

I can successfully mount the 95GB (/home) system.  I then see two folders "dan/" and "lost+found/".

I can't enter the "dan" folder because I don't have permission.  Opening a terminal and navigating to /media/95GB\ Filestystem/dan/ works if I "sudo su root" first, but not as "ubuntu"

In the dan/ folder, all I see is "Access-your-private-data.desktop" (because my /home directory is encrypted) and "README.txt".  The README says to run the command "encryptfs-mount-private".  When I do that, however, I just get the message 
ERROR: Encrypted priavte directory is not setup properly

I tried putting my decryption password immediately after the decrypt command, a la:
encryptfs-mount-private mypasswordgoeshere

but with no change in results.

The one ray of sunshine in all this is that I backup my /home directory to an external every week or two.  So the actual data loss is not catastrophic.  But it *has* been a busy week, so I would really like to recoup that data, since it includes little things like the first chapter of my dissertation, and the job negotiation emails in my .evolution folder

Any help would be WONDERFUL!

Thanks,
Dan

---

### Post by Allochtoon on 2010-04-02
i am interested as well. fried my harddisk. now want my data back :)

any help much appreciated

---

### Post by Ocxic on 2010-04-02
there's a special password that was given to you when you encrypted the drive for recovery purposes. I think you might need that

---

### Post by Mark Phelps on 2010-04-02
Are you asking how to bypass the password on an encrypted drive?  

If that was even possible, there would be no point in encrypting drives, now would there.

Our IT department regularly encrypts drives for company-issued laptops, and even with commercial software, they are unable to recover drives where the original person has forgotten the password they used to encrypt the drives.

---

