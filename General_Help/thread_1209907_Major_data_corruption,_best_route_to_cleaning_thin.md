---
title: "Major data corruption, best route to cleaning things up"
date: 2009-07-10
forum: General Help
---

### Post by geologic on 2009-07-10
A while ago my Ubuntu had an unexpected crash which required a forced reboot. This system dual boots with Windows using Grub.
Only problem was upon the reboot, Grub failed, and I received an error message. So I fixed this by booting off a live cd and reinstall grub and it booted right back up. Except it had the same problem.
After a few rounds of this, I was booting back into Ubuntu, except the system actually failed to fully start, something fsck didnt like. Manually running fsck got the system going again, except when I got to the desktop lots of things were a little different, such as all my firefox preferences, and even some of my gnome icons/settings.
By this point I realized it seemed to be something specific to Ubuntu, so I began only using Windows. But one can only go on so long like that before the problem needs to be addressed.

For started I did a complete backup of my hard drive to an external hard drive using the dd command. I wasnt 100% sure if this was a hardware problem with my main hard drive, but the problem is persisting on the new copied over hard drive, so I'm thinking/hoping its something with Ubuntu.

Now I still don't know what happened, but at this point I'm ready to move on for the most part. I have all my data backed up, and like to get Ubuntu running again. If possible I would like to do a reinstall so that my data and settings can be kept in tact, but the main priority is getting Ubuntu up and working again.

I downloaded a copy of the 9.04 alternate iso -- alternate because my understanding is that you can do upgrade installs as oppose to just clean installs from the livecd. However, the alternate cd failed in copying the base system. I ran a disc integrity check on the CD and everything came thru fine.

I apologize if this is a bit long, but I'm a bit confused. So can anyone suggest a way to [re]install ubuntu such that it will clear out any (filesystem?) problems that its having, but without completely wiping the partition?

Thanks

---

### Post by phillw on 2009-07-10
[SIZE=2][FONT=Arial]Hi,

Jeez ........

As the only thing I can suggest will be a wipe off all your data, you need to do this ...

[http://ubuntuforums.org/showthread.php?t=35087&highlight=backup+restore+Ubuntu](http://ubuntuforums.org/showthread.php?t=35087&highlight=backup+restore+Ubuntu)

From the backup, you will have everything salvageable - If you need to, you can do it with a LiveCD - but you will have to be careful where you put the output file. The thread does show how to alter the destination.

[/FONT][/SIZE][SIZE=2][FONT=Arial]IF you are dual booting with windows, the backup procedure in the 1st article can back that area up, as well.
[/FONT][/SIZE]
[SIZE=2][FONT=Arial]
MAKE SURE YOU CAN CAN VIEW THE CONTENTS OF THE BACKUP FILE(S) 

From here on in, you wave bye-bye to your current Ubuntu installation.

Depending on how much 'localisation' you have done (adding programmes etc)

If you have added several & don't trust memory to re-call them all, you can ask Synaptic Package Manager to give you a list....

[http://ubuntuforums.org/showthread.php?t=1057608&highlight=synaptic+package+manager](http://ubuntuforums.org/showthread.php?t=1057608&highlight=synaptic+package+manager)

Thereafter, just do a clean install - I recommend doing a manual resizing of the partitions - delete them all, write them & re-boot - Your disk is then 100% free. Then set your slices up as you want.

Not the greatest of fun, I appreciate, but at least you get the chance to save your data.... Oh, the hours I have spent on screwed up systems with a different operating system ....... At least the LiveCD gives me a chance to pull the data from such an operating system ;-)

Depending on how much tweaking you have done (the package manager output will look after that) - about the only other thing you'll need is your ~/home directory(ies). With the backup plan, you have the option to re-install everything, or just parts - I always go for clean install (In a certain, other, operating system) and add the user files afterwards.

Hoping this is of help, if you need any further help, my email addy is below - The forums are faster at replying, I can take upto 48 hours !!!

Regards,

Phill

[EMAIL="phillw@uk.vpolink.com"]phillw@uk.vpolink.com[/EMAIL]

:p
[/FONT][/SIZE]

---

### Post by geologic on 2009-07-17
Thanks for the response, even tho this reply is a bit delayed now..

I wound up doing something along the lines of what your suggestion was. I made sure I had some redundancy in my data backup of non-replaceable files. Then I just went for a full wipe and reinstall.

I did leave the windows partition intact, but did a reformat of the extended partition table and stuck Ubuntu & swap in there. I figured it had been long enough that it didnt hurt to just do a clean reinstall and start over.

This route does take a lot of time. And the frustration is in when you had something setup nicely and then when you need to go and use that tool again its not there, or only in its vanilla form.

Anyway, thanks again, and hopefully this post -- and the one you linked to -- can help someone else who finds themself in a similar situation.

---

