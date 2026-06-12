---
title: "Letting multiple users use the same Thunderbird profile in 11.10"
date: 2012-01-17
forum: General Help
---

### Post by zon14 on 2012-01-17
[SIZE=2]Here's what I want to do.  I have a folder with all Thunderbird profile and email data.  I want that to be accessible and usable by two users (say x and y), when they log onto the same machine.  User x logs in, has his own profile, boots up Thunderbird and can read, write, receive, and send mail.  User y logs in, same thing.  They only thing they'd share is Thunderbird emails.  Seemed simple enough as I was able to do it in Profile Manager in Winduhs by setting all the users up under the same profile and giving them all Administrator privileges.  Dangerous for security, but it worked for years without a hitch.

Ubuntu 11.10 hasn't been so easy.  I did set up the Thunderbird Profile Manager for both users to point to the same folder.

The problem seems to stem from Thunderbird changing file owners and groups once someone starts to use it.

I've temporarily set up a third account called email which gives both users access to the email and nothing more.  So when I initially look at the Thunderbird folder all the files have the owner and group listed as email:email.  Now after a different user accesses Thunderbird, some files still list the owner and group as email:email, but others have now changed to x: x or y:y depending on who last ran Thunderbird.  I've already made x and y members of the email group thinking maybe that would do it but since Thunderbird changes group ownership as well as user ownership, no good there.

I've fiddled with setting the guid in chmod to 2???, but that seems to take away write capability for some files for x and y.

I've also looked at making symbolic links to the email folder for x and y and then have Profile Manager point to them with the same result.  Unable to write new emails into the data files.

My latest thought was to write a script that would chown all the files back to email:email when x or y close Thunderbird.  I looked at inotifywait, but that seems focused exclusively on files, rather than when a process starts or stops.  I could do it as a logout script, but that runs the risk of if someone simply switches users without logging off, then the file owners haven't changed, assuming of course they've already quit Thunderbird.
[/SIZE]

[SIZE=3]EDITED TO ADD:  I had to start over and repartition the drive, but at least everything's back in order now, with an additional 10gig FAT32 partition where the Thunderbird data is nestled in comfortably.  I had to add all the users to the plugdev group, but no biggie there.

Now I just have to wait and see if I missed anything else. :D[/SIZE]

---

### Post by ottosykora on 2012-01-17
somehow I can not think that this could work simple, because the current user will try to set all to his kind of ownership etc.

Don^t know if it will work, but if you make a fat32 poartition and try to place the profle folder there and point TB to look for it there? Could you try something like this?

OK, the drive would have to be mounted sure before one goes to use TB, but at least on fat32 no permissions exist, so if TB allows you have profile there, it might be worth trying.

---

### Post by saneearth on 2012-01-17
An easier method I think would be to use IMAP and give everyone you want to have access the same account credentials if this is possible.

---

### Post by zon14 on 2012-01-17
I thought about creating a fat32 partition.  It'd involve reallocating some disk space but this may be the best option, at least for now.

---

