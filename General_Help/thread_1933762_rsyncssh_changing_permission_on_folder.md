---
title: "rsync/ssh changing permission on folder?"
date: 2012-03-01
forum: General Help
---

### Post by Roasted on 2012-03-01
I couldn't help but to notice this. I just set up a test environment with my laptop backing up a folder via rsync to my file server.



File Server:
drwxr-x--- 3 test          test        4096 2012-03-01 00:27 test

Then on laptop I run:
jason@Goliath:~$ rsync -a --delete ~/TEST/ test@192.168.1.10:/media/NAS/test/



Once I run that on the laptop, I notice this:
File Server:
drwxrwxr-x 3 test          test        4096 2012-03-01 00:27 test


Why are we switching from 750 to 775?

---

### Post by Khayyam on 2012-03-01
Roasted ...

What a difference a slash makes ... hehe

When you use '-a' (--archive)  the permissions on the destination directory will be changed to match those of the source directory. So, ommit the slash, in which case the directory "TEST" will be copied to dest/, or set the permissions on 'TEST' to reflect those you wish dest to have.

There are methods of changing permissions via rsync (--owner= --group= --chmod=) but its not really necessary here.

HTH ... khay

---

### Post by Roasted on 2012-03-01
You know, I even kind of thought about that after I shut everything down for the night... 

So just to recap...

rsync -a --delete ~/TEST test@192.168.1.10:/media/NAS/test/

...is what I want? 

I forget why I got in the habit of using a trailing slash. I think what originally happened was many months ago (years at this point, probably 2006 when I first started using rsync between two local drives). 

I thought I remember running into a situation where I was trying to back up files from drive A to drive B. Unless I used the slash, it would take the entire source directory and not just the contents of the directory. Meaning... let's say the destination was /media/backup, and the source was /home/user. Instead of all of user's contents being in /media/backup, it would simply copy user within backup... so it would be /media/backup/user/userscontentshere.

I think a slash of some sort in that scenario is what fixed it, which may be where my habit came from above.

That being said, am I nuking the slash off the source ,or dest?

rsync -a --delete ~/TEST test@192.168.1.10:/media/NAS/test/
rsync -a --delete ~/TEST/ test@192.168.1.10:/media/NAS/test

---

### Post by Khayyam on 2012-03-01
> **Roasted said:**
> [...] So just to recap ...

rsync -a --delete ~/TEST test@192.168.1.10:/media/NAS/test/

...is what I want?

yes, if you want "~/TEST" to be the source and ":/media/NAS/test/" to be where the archive (dest) is located ("TEST" will be nested within "*/test/").

When using "-a" and source/ dest/ source and dest will be "archives" of each other and so dest will exhibit all the characteristics of source.  

> **Roasted said:**
> I forget why I got in the habit of using a trailing slash. I think what originally happened was many months ago (years at this point, probably 2006 when I first started using rsync between two local drives). 

I thought I remember running into a situation where I was trying to back up files from drive A to drive B. Unless I used the slash, it would take the entire source directory and not just the contents of the directory. Meaning... let's say the destination was /media/backup, and the source was /home/user. Instead of all of user's contents being in /media/backup, it would simply copy user within backup... so it would be /media/backup/user/userscontentshere.

Yes, but thats sometimes what you want, if you have multiple backups under dest/ then you would want 'source' and not 'source/'. The trailing slash catches alot of people out, particularly when using --delete, you can wipe out whole directory trees with one slash ..

> **Roasted said:**
> That being said, am I nuking the slash off the source, or dest?

rsync -a --delete ~/TEST test@192.168.1.10:/media/NAS/test/
rsync -a --delete ~/TEST/ test@192.168.1.10:/media/NAS/test

It depends .. if you understand what I've written above regarding '-a' then its just a matter of how you want to nest the backups. I would choose something like the following:

:/media/NAS/backup/
:/media/NAS/backup/test
:/media/NAS/backup/john
:/media/NAS/backup/jane

rsync -a --delete ~/john/ test@192.168.1.10:/media/NAS/backup/john

'/media/NAS/backup/john' will be indentical to "~/john" including ownership and permissions.

HTH ... khay

---

### Post by Roasted on 2012-03-01
Hi there. Yes that's a huge help. I kind of have that setup already, but I may be taking it a step further. For example:

/media/NAS/john
/media/NAS/bob
/media/NAS/frank

That's how my setup is now. But frank has a desktop and laptop, both of which I want backed up, so I was thinking on dropping a sub directory in frank

/media/NAS/frank/laptop
/media/NAS/frank/desktop

Then set the rsync to point to the proper directory depending upon what system it is.


> **Khayyam said:**
> yes, if you want "~/TEST" to be the source and ":/media/NAS/test/" to be where the archive (dest) is located ("TEST" will be nested within "*/test/").


This test vs test thing is a bit confusing, so let me recap like this. The user is frank, and the destination is /media/NAS/frank/desktop. The source is his home directory.

If I use: **rsync -a --delete ~/Frank frank@server:/media/NAS/frank/desktop**
then "desktop" would contain all of Frank's raw data.

But...

If I use: **rsync -a --delete ~/Frank/ frank@server:/media/NAS/frank/desktop/**
then "dekstop" would contain "Frank", and within */desktop/Frank I would see Frank's raw documents. Right?

And through it all, the -a will still make the directories mimic one another in terms of permissions? Or would this be negated with the re-structuring of where the / goes?

---

### Post by Khayyam on 2012-03-01
> **Roasted said:**
> [...]That's how my setup is now. But frank has a desktop and laptop, both of which I want backed up, so I was thinking on dropping a sub directory in frank

/media/NAS/frank/laptop
/media/NAS/frank/desktop

That's inadvisable ... nest like so:

:/media/NAS/backup/
:/media/NAS/backup/bup-john
:/media/NAS/backup/bup-john/hostname/john
:/media/NAS/backup/bup-bob
:/media/NAS/backup/bup-bob/hostname/bob
:/media/NAS/backup/bup-frank
:/media/NAS/backup/bup-frank/hostname/frank
:/media/NAS/backup/bup-frank/hostname/frank

where "hostname" is the name of the client machines.

```
[john@a]$ rsync -a --delete ~/john/ john@192.168.1.10:/media/NAS/backup/bup-john/$(hostname -s)/john

[bob@b]$ rsync -a --delete ~/bob/ bob@192.168.1.10:/media/NAS/backup/bup-bob/$(hostname -s)/bob

[frank@c]$ rsync -a --delete ~/frank/ frank@192.168.1.10:/media/NAS/backup/bup-frank/$(hostname -s)/frank

[frank@d]$ rsync -a --delete ~/frank/ frank@192.168.1.10:/media/NAS/backup/bup-frank/$(hostname -s)/frank
```By nesting this way and sticking to a naming converntion you prevent potential confusion, it also means that if 'john', 'bob' or 'frank' acquire another machine it can be backed up using the same logic without having to switch things around to make the new requirements work.

> **Roasted said:**
> And through it all, the -a will still make the directories mimic one another in terms of permissions? Or would this be negated with the re-structuring of where the / goes?

With the '-a' "dest" will aquire those of "source" .. this is the case whether its in '*/backup' */backup/' or '*/backup/bup/hostname/frank'. All the trailing slash does is define (or rather change) the exact path of "dest".

HTH ... khay

---

### Post by papibe on 2012-03-01
@Roasted

May be a silly question but, ¿What kind of filesystem are source and destination?

Regards.

---

### Post by Roasted on 2012-03-01
> **Khayyam said:**
> That's inadvisable ... nest like so:

:/media/NAS/backup/
:/media/NAS/backup/bup-john
:/media/NAS/backup/bup-john/hostname/john
:/media/NAS/backup/bup-bob
:/media/NAS/backup/bup-bob/hostname/bob
:/media/NAS/backup/bup-frank
:/media/NAS/backup/bup-frank/hostname/frank
:/media/NAS/backup/bup-frank/hostname/frank


I do appreciate your insight, but quite honestly the host name thing is only going to confuse me. This is a backup for my parents, siblings, etc. My brothers have their way with their computers. I just want to make sure their data is backed up in case they have another system drive fail or anything like that. Since they have full reign to do stuff like that, it concerns me that using host names would only aide in confusion. That way I can immediately associate laptop being the one and only laptop they have, desktop being the desktop they have, etc. It's a solid thought though that may come in handy later on here at work, but for this case I'm not too sure.

> **papibe said:**
> @Roasted

May be a silly question but, ¿What kind of filesystem are source and destination?

Regards.

Mixture of EXT3/4. Why do you ask?

I'm a little concerned about how it will work out with tagging a few Windows systems in the mix. I'm just not sure how I'll be able to push data over the WAN to my file server and have it authenticate based on SSH keys, however "DeltaCopy" has suggested it's possible. I guess we'll find out later.

[http://www.aboutmyip.com/AboutMyXApp/DeltaCopy.jsp](http://www.aboutmyip.com/AboutMyXApp/DeltaCopy.jsp)

---

### Post by Khayyam on 2012-03-01
> **Roasted said:**
> I do appreciate your insight, but quite honestly the host name thing is only going to confuse me. This is a backup for my parents, siblings, etc. My brothers have their way with their computers. I just want to make sure their data is backed up in case they have another system drive fail or anything like that. Since they have full reign to do stuff like that, it concerns me that using host names would only aide in confusion. That way I can immediately associate laptop being the one and only laptop they have, desktop being the desktop they have, etc. It's a solid thought though that may come in handy later on here at work, but for this case I'm not too sure.

Understood, but its really not that confusing, all the information needed can be reduced to two terms, the 'hostname' and 'username', and when you are rsync'ing this information is on the source machine. The rational is no different from URI's .. site.domain.tld/subsection/subsection/subsection. Obviously you are free to choose whatever schema you want, but there is a reason why people get into all kinds of bad habits ... it begins at $HOME (quite literally). Agreed, I am presenting somewhat of a 'work' schema, but having worked in insitutions where bad habit is 'de regueur', and where once someone has left, hours are spent sifting through "backups", with absolutely indescriminate filenames, and filesystem organisation, because their replacement is looking for a project proposal, or budget, from 2002, think that structured data should be something that has similar weight to 'literacy'.

Note that with the above scheme each rsync uses almost exactly the same syntax, with the only invariance being user and hostname, it provides for a very simple machanism to remember. We are not alternating "TEST" to "test" or "frank" to "laptop", each 'dest' has the same name as 'source', etc .. and this is half way to stearing clear of mistakes (like trailing slashes, "*/frank/frank", etc), and thats kinda how we got started on this. In case you haven't guessed, I'm a sys admin, and so speak with some understanding of the issues/problems involved ... and thats all I was trying to relay. I would never say, do it this way otherwise bad things will happen, only that in my long experience bad things **have** happened (fortunately not to me, but closes enough to pinch) and most of it I can reduce to the practices already outlined. So, complicated as it might seem at first glance, some reflection might show it as actually quite simple.

If your having your parents/syblings make thier own backups you can provide them with somekind of automation/script which will save them the headache of following the **master plan**.

> **Roasted said:**
> I'm a little concerned about how it will work out with tagging a few Windows systems in the mix. I'm just not sure how I'll be able to push data over the WAN to my file server and have it authenticate based on SSH keys, however "DeltaCopy" has suggested it's possible. I guess we'll find out later.

Its fairly straighforward ... install [cwRsync]("http://www.rsync.net/resources/howto/windows_rsync.html") (it comes with everything needed for ssh keys) and then write a script/execuatble for your various clients. I've not seen DeltaCopy and so I can't comment, it probably doesn't work with keys.

HTH & best .... khay

---

### Post by Roasted on 2012-03-02
Well I initiated the first backup last night. Upon checking it on my server something was clearly out of whack. I saw a "some contents unreadable" flag under properties and it said only 17 MB transferred when there was about 30 gig there. I'm going to check it a little later, but I pretty much ran the command as so:

rsync -a /home/pam pam@server:/media/NAS/pam/desktop/

I couldn't see anything sticking out to me in the command there, besides the fact it ended up doing the "layered" setup, which after thinking about it, was what I wanted... where if you're on the server and you go to /media/NAS/pam you see /desktop/pam/ within there instead of Pam's files. I began to think this would just be easier to isolate laptop vs desktop so I kept it as such.

Beyond that I wasn't sure what was going on, though. I'll give it another shot then, but the fact some of her folders came through locked confused me. Maybe due to the -a it's keeping permissions and she just has 700 permissions on some of her home directory folders and doesn't realize it?

---

### Post by Roasted on 2012-03-02
I'm a bit confused. I did notice in Pam's home directory, a few items had permissions that could have been an issue (700, etc). Well, maybe not a true issue, but I wanted to see if I could get things to be consistent.


Everything in Pam's home directory on the desktop computer is 755 permissions.

Then I ran:

rsync -a /home/pam pam@server:/media/NAS/pam/desktop/

But on the server:
drwx------ 2 pam pam   4096 2012-03-02 12:56 Desktop
drwx------ 2 pam pam   4096 2012-03-02 12:56 Documents
drwx------ 2 pam pam   4096 2012-03-02 12:56 Downloads
drwx------ 2 pam pam   4096 2012-03-02 12:56 Music
drwx------ 2 pam pam   4096 2012-03-02 12:56 packages
drwx------ 2 pam pam   4096 2012-03-02 12:56 Pictures
drwx------ 2 pam pam   4096 2012-03-02 12:56 Public
drwx------ 2 pam pam   4096 2012-03-02 12:56 Templates
drwx------ 2 pam pam   4096 2012-03-02 12:56 Videos

So why is it everything is 755 on the client, and switches to 700 on the server? I thought -a controlled the permissions and kept them the same. However, this backup is going to take quite a long time. Does it by chance reset permissions right at the end when the transfer is completed?

---

### Post by Khayyam on 2012-03-02
> **Roasted said:**
> [...] Everything in Pam's home directory on the desktop computer is 755 permissions. Then I ran:

rsync -a /home/pam pam@server:/media/NAS/pam/desktop/

But on the server:
drwx------ 2 pam pam   4096 2012-03-02 12:56 Desktop
drwx------ 2 pam pam   4096 2012-03-02 12:56 Documents
drwx------ 2 pam pam   4096 2012-03-02 12:56 Downloads
drwx------ 2 pam pam   4096 2012-03-02 12:56 Music
drwx------ 2 pam pam   4096 2012-03-02 12:56 packages
drwx------ 2 pam pam   4096 2012-03-02 12:56 Pictures
drwx------ 2 pam pam   4096 2012-03-02 12:56 Public
drwx------ 2 pam pam   4096 2012-03-02 12:56 Templates
drwx------ 2 pam pam   4096 2012-03-02 12:56 Videos

So why is it everything is 755 on the client, and switches to 700 on the server? I thought -a controlled the permissions and kept them the same.

Just to show that '-a' does preserve permissions under normal circumstances.

```
% mkdir -p test/test{1,2,3}
% ls -ld test/*
drwxr-xr-x 2 user group 4096 Mar  2 20:20 test/test1
drwxr-xr-x 2 user group 4096 Mar  2 20:20 test/test2
drwxr-xr-x 2 user group 4096 Mar  2 20:20 test/test3
% rsync -a -e ssh ~/test/ user@host.domain.tld:/home/user/test
% ssh user@host.domain.tld "ls -ld test/*"
drwxr-xr-x 2 user group 4096 Mar  2 20:20 test/test1
drwxr-xr-x 2 user group 4096 Mar  2 20:20 test/test2
drwxr-xr-x 2 user group 4096 Mar  2 20:20 test/test3
```

Everything is pretty much as I'd expected it to be. In your case I should ask a number of questions:

1. What is your NAS? (OS, product name, etc)
2. How is :/media/NAS/ configured? (is it a smb/cif share or what have you)
3. What OS is the client? 
4. What is the UID of the person executing 'rsync'?
5. Is 'pam@server' a shell account? (is there perhaps a mask set?)
6. What is the ownership of ':/media/NAS/' and ':/media/NAS/pam'  
7. Is '@server' running rsyncd? (not important as your not stating 'server::')
8. Is 'rsh' the default shell for 'pam', et al?
9. Is 'pam' in some 'rsync' group, without an actual shell? Were these accounts setup via a webgui "for rsync access"? 

Note that using rsync without '-e ssh' will use 'rsh' on the target machine.

> **Roasted said:**
> However, this backup is going to take quite a long time. Does it by chance reset permissions right at the end when the transfer is completed?

No, they are written as they are sync'ed. As I mentioned previously there is the facility (--owner= --group= --chmod= --perms) to change these after the fact (which is sometimes necessary to allow them to be 'shared' via smb).

best ... khay

---

### Post by Roasted on 2012-03-02
> **Khayyam said:**
> Just to show that '-a' does preserve permissions under normal circumstances.

```
% mkdir -p test/test{1,2,3}
% ls -ld test/*
drwxr-xr-x 2 user group 4096 Mar  2 20:20 test/test1
drwxr-xr-x 2 user group 4096 Mar  2 20:20 test/test2
drwxr-xr-x 2 user group 4096 Mar  2 20:20 test/test3
% rsync -a -e ssh ~/test/ user@host.domain.tld:/home/user/test
% ssh user@host.domain.tld "ls -ld test/*"
drwxr-xr-x 2 user group 4096 Mar  2 20:20 test/test1
drwxr-xr-x 2 user group 4096 Mar  2 20:20 test/test2
drwxr-xr-x 2 user group 4096 Mar  2 20:20 test/test3
```

Everything is pretty much as I'd expected it to be. In your case I should ask a number of questions:

1. What is your NAS? (OS, product name, etc)
2. How is :/media/NAS/ configured? (is it a smb/cif share or what have you)
3. What OS is the client? 
4. What is the UID of the person executing 'rsync'?
5. Is 'pam@server' a shell account? (is there perhaps a mask set?)
6. What is the ownership of ':/media/NAS/' and ':/media/NAS/pam'  
7. Is '@server' running rsyncd? (not important as your not stating 'server::')
8. Is 'rsh' the default shell for 'pam', et al?
9. Is 'pam' in some 'rsync' group, without an actual shell? Were these accounts setup via a webgui "for rsync access"? 



1 - Ubuntu 11.04 on a standard Dell desktop.
2 - /media/NAS is the mount point loaded in fstab for a software raid volume containing 2x500GB drives.
3 - Ubuntu 11.10 (and some Windows XP and 7 in there, but not in this scenario... didn't get to them yet)
4 - No idea.
5 - I have a Dynamic DNS setup with my home LAN, so pam@server refers to pam@mydomain. My file server is forwarded on port 22, so it hits it accordingly.
6 - /media/NAS is owned by administrator:users. then "pam" (within NAS) is owned by pam:pam.
7 - No idea.
8 - No idea.
9 - No, Pam is a local user on the system. Previously this box was physically in their residence as I used to live with them. I would use certain programs to back up their data over Samba. Now that I'm out of the house, I'm aiming to do it via rsync/ssh.

> 

Note that using rsync without '-e ssh' will use 'rsh' on the target machine.



I was under the impression that -e ssh is no longer needed as rsync utilizes SSH by default now-a-days anyway.

> 
No, they are written as they are sync'ed. As I mentioned previously there is the facility (--owner= --group= --chmod= --perms) to change these after the fact (which is sometimes necessary to allow them to be 'shared' via smb).

best ... khay

I conducted a little test at home. When it looked like the permissions were hanging up, it was actually still in the progress of writing more directories, particularly hidden directories. I did an exclude on .* so it blocked out all hidden files/folders, and it worked instantly and set the permissions just fine. I have to assume since it was still loading the hidden directories it simply didn't set them yet. However, based on what I was reading, several sources and users confirmed rsync sets permissions afterwards, which may be why I was seeing the permissions messed up when they weren't completely done yet.

In other news, this backup solution is going to prove to be a real challenge. Pam only has 35GB of data, while other users have quite a bit more. At the transfer rate it was going, it looked like Pam's data alone was going to take about 11 days to fully transfer. Instead, I'm going to resort to plan B and hope B is the ticket. Otherwise I'll have to invest in a network based external hard drive (which I REALLY don't want to do) and hook it up for local access within their residence. But plan B will consist of simply copying their data onto an external hard drive and porting it over to the server. Hopefully once the bulk of the data is there, the synchronize steps will be significantly faster. We'll see how it goes...

---

### Post by papibe on 2012-03-02
> **Roasted said:**
> I conducted a little test at home. When it looked like the permissions were hanging up, it was actually still in the progress of writing more directories, particularly hidden directories. I did an exclude on .* so it blocked out all hidden files/folders, and it worked instantly and set the permissions just fine. I have to assume since it was still loading the hidden directories it simply didn't set them yet. However, based on what I was reading, several sources and users confirmed rsync sets permissions afterwards, which may be why I was seeing the permissions messed up when they weren't completely done yet.

I can confirm that if you kill (Ctrl+C) the rsync in the middle of its operation, the permissions will be messed up. I just made a test and I'm seeing similar results: main directories set to 700 instead of 775.

Just wanted to share.
Regards.

---

### Post by Roasted on 2012-03-02
> **papibe said:**
> I can confirm that if you kill (Ctrl+C) the rsync in the middle of its operation, the permissions will be messed up. I just made a test and I'm seeing similar results: main directories set to 700 instead of 775.

Just wanted to share.
Regards.

Good thought. I was using CTRL+Z but I'm sure it does the same thing.

I brought all of the documents over via external hard drive. As I expected, it synced up very very fast. This could be a potential option as long as I get the bulk of the data down here. I don't foresee the bulk of the data changing that much.

I wonder, how would rsync be affected if the user shuts off the client computer when the rsync cron job is running? Would that be the equivalent of doing a CTRL+Z or CTRL+C and have the potential for messing things up? Or would it catch and repair it next time it ran successfully?

---

### Post by papibe on 2012-03-02
> **Roasted said:**
> Or would it catch and repair it next time it ran successfully?
Yes, exactly.

That's one of the most useful features of rsync. I experience several interruptions when rsyncing over the Internet due to a drop connection or ISP DHCP renewal.

If you are running a reasonable, short, interactive rsync script, you just run it again in case of any error.

In case you are transferring a big file, it would save you a lot of trails to use the option --partial. That keeps the partially transferred file parts, so the next time you run rsync, it doesn't start from zero.

In case you want to do an unattended transfer, the safest way to do it is to use an script with this structure:
```
rsync ...
until [ $? = 0 ]
do
    sleep 90 # optional. Not necessary over LAN.
    rsync ...
done
```
Hope that helps.
Kind Regards.

---

### Post by Khayyam on 2012-03-02
Roasted ...

I asked that series of questions as a "NAS" could be [FreeNAS](http://www.freenas.org/), a [Netgear ReadyNAS or NV+](http://www.readynas.com/) or any number of commercial "NAS" products. I had assumed this was the case from your use of ":media/NAS" and the fact that no other details were provided. I was trying to get some idea of what the server platform was, because many of these products provide rsync but no shell access and are configured via web interfaces in ways that **might** have been the reason rsync wasn't setting permissions correctly ... it seems now, this isn't really an issue. In hindsight I can only ask: shouldn't it have been noticed with your "TEST"?

Now, for my own part I've never seen rsync set permissions after the fact, but then I've never stood over a 35GB transfer and asked myself if its doing its job correctly, I would have hopefully noticed this in the 'test' phase, thats the whole purpose of testing. Its at this stage that questions like "I thought -a controlled permissions" could be asked with some credulity, **if** it wasn't behaving as expected.

Your problems and "confusion" boils down to your not really "testing" as you initially stated you had, and your reporting is mostly speculation about a state of affairs that would have been clear to you had the 'test' been carried out with some level of thoroughness.

I've answered your questions to the best of my knowledge, and in some regards extensively so, but can't help but think that mostly its been wasted.

best ... khay

---

### Post by Roasted on 2012-03-02
> **Khayyam said:**
> Roasted ...

I asked that series of questions as a "NAS" could be [FreeNAS](http://www.freenas.org/), a [Netgear ReadyNAS or NV+](http://www.readynas.com/) or any number of commercial "NAS" products. I had assumed this was the case from your use of ":media/NAS" and the fact that no other details were provided. I was trying to get some idea of what the server platform was, because many of these products provide rsync but no shell access and are configured via web interfaces in ways that **might** have been the reason rsync wasn't setting permissions correctly ... it seems now, this isn't really an issue. In hindsight I can only ask: shouldn't it have been noticed with your "TEST"?


I told you, my NAS is Ubuntu. Period. That's it. Ubuntu 11.04. /media/NAS is simply the mount point of the RAID'ed volume I have that I use for it. There's nothing else to build on that. These points were brought up in earlier posts.

> 
Now, for my own part I've never seen rsync set permissions after the fact, but then I've never stood over a 35GB transfer and asked myself if its doing its job correctly, I would have hopefully noticed this in the 'test' phase, thats the whole purpose of testing. Its at this stage that questions like "I thought -a controlled permissions" could be asked with some credulity, **if** it wasn't behaving as expected.


Based on my testing earlier, it sounds like it very well acts that way. When I was pushing the initial batch, it was doing everything in the home directory. It set the permissions to 700 by default in the home directory contents, but at the time I did not realize it was backing up hidden files/folders as well. What I did to speed up the testing phase is I set a ton of exclusion tags, so instead of copying all 10 folders and 100 hidden folders, I was only rsyncing 2 of the smaller non-hidden folders and 5 smaller hidden folders. A quick array of ls -l bashing resulted in the permissions being seen as one way in mid transfer, and then changing after the conclusion of the transfer. That's the best that I could tell, anyway.

> 
Your problems and "confusion" boils down to your not really "testing" as you initially stated you had, and your reporting is mostly speculation about a state of affairs that would have been clear to you had the 'test' been carried out with some level of thoroughness.


Actually, no. I was testing, and in fact I was testing rather extensively in each of these scenarios. What I didn't take into account was the hidden files/folders that were being tagged with the transfers, which is where the confusion with the permissions came from due to the fact when the systems were in mid transfer of the hidden docs, the permissions were not formally set *yet*. Once I slimmed down the array of files that were being transferred, things ended up in a much more predictable fashion.

> 
I've answered your questions to the best of my knowledge, and in some regards extensively so, but can't help but think that mostly its been wasted.

best ... khay

Yes, you did, and for that I thank you. You've been excessively helpful in this thread, which is actually what makes these forums so great. While you have provided me with a ton of information, some of it just isn't applicable to what I'm aiming to do. There's always 100 ways to handle every task at hand, but at times a specific way being tailored to your specific needs is sometimes the best shot. 

At any rate, this thread has provided me with a lot of useful information which aided in the completion of what I was trying to do. All in all, it's actually rather simple, but you just have to be unusually aware of what type of reaction the /'s may have in the command you're firing out. 

I have some options to weigh in regard to which way I go with this. A 35GB transfer is going to take upwards of 11 days to complete, however with the bulk of the data already residing here (transported via external hard drive) and the likelihood of 35GB transfers in the future being slim/none, it makes me think perhaps continuing with this rsync setup would still be a good thing. After all, if no data changed, the rsync completes in seconds. Any data transfer beyond that is dictated upon the size of the data. Maybe we'll see how this pans out...

For what it's worth, thank you. Your time is appreciated.

---

### Post by Khayyam on 2012-03-03
> **Roasted said:**
> I told you, my NAS is Ubuntu. Period. That's it. Ubuntu 11.04.

Yes you did, in post #13, but only after I asked you that series of 9 questions in which I was trying to get a better idea of "why permissions were not being set when -a was used". So, while I was mentally persuing all possible reasons why this might be the case (particularly that some "NAS" was involved), it was **then** my assumption based on ':media/NAS' was made clear. A merry chase, no doubt based on my own, false, assumption, but none the less one that I was prone to make given the circumstances. 

> **Roasted said:**
> Based on my testing earlier, it sounds like it very well acts that way. When I was pushing the initial batch, it was doing everything in the home directory. It set the permissions to 700 by default in the home directory contents, but at the time I did not realize it was backing up hidden files/folders as well. What I did to speed up the testing phase is I set a ton of exclusion tags, so instead of copying all 10 folders and 100 hidden folders, I was only rsyncing 2 of the smaller non-hidden folders and 5 smaller hidden folders. A quick array of ls -l bashing resulted in the permissions being seen as one way in mid transfer, and then changing after the conclusion of the transfer. That's the best that I could tell, anyway.

Can't you see how you are over complicating things? Read the first line of the first post in this thread: "I just set up a test environment [..] why are we switching from [permissions] 750 to 775?" I explaned how this might happen, and assumed in all other regards this 'test' was sucessful. Then read my post #12 where I illustrate a test, no --excludes, no 35GB of data, just a test to show that with the use of '-a' permissions **are** set correctly. This took me a minute or less to setup, rsync and log. Now compare to the paragraph above.

> **Roasted said:**
> Actually, no. I was testing, and in fact I was testing rather extensively in each of these scenarios. What I didn't take into account was the hidden files/folders that were being tagged with the transfers, which is where the confusion with the permissions came from due to the fact when the systems were in mid transfer of the hidden docs, the permissions were not formally set *yet*. Once I slimmed down the array of files that were being transferred, things ended up in a much more predictable fashion.

Each of which "scenarios"? I was speaking about post #1, the "test". Everything you have posted since, bar the clarifications asked about trailing slashes, should have been made clear with the 'success' of that 'test'. I can't see why that isn't obvious to you.

> **Roasted said:**
> [...] and for that I thank you. You've been excessively helpful in this thread, which is actually what makes these forums so great. While you have provided me with a ton of information, some of it just isn't applicable to what I'm aiming to do. There's always 100 ways to handle every task at hand, but at times a specific way being tailored to your specific needs is sometimes the best shot.

Your most welcome, and I mean that sincerly. Hopefully you understand my frustration, often the most basic of tasks can be turned into a trial by not following the most simple of procedures ... but I'll save you my 'best practices' speech.

> **Roasted said:**
> At any rate, this thread has provided me with a lot of useful information which aided in the completion of what I was trying to do. All in all, it's actually rather simple, but you just have to be unusually aware of what type of reaction the /'s may have in the command you're firing out.

OK, good.

> **Roasted said:**
> [...] For what it's worth, thank you. Your time is appreciated.

Again, your welcome.

best ... khay

---

