---
title: "Severe problems with last samba update"
date: 2011-10-07
forum: General Help
---

### Post by mikeydeeeee on 2011-10-07
Anybody else out there having problems with samba after the last update?  Ever since it installed (version 2.3.5.8 which was on 10/4, I believe) I've been having nothing but problems with my mounted file systems.

Moving files between the local and remote file systems has become basically impossible, as the mounted file systems and files periodically disappear, taking even the mount points with them at times.

The situation is so bad that I'm looking into rolling back the changes (any help in this regard would be appreciated) at least until the next update comes out.

I'm running kubuntu 11.04 64bit, all current updates  ...  easily the weakest version of the OS I've ever seen.

MikeD

---

### Post by duke.tim on 2011-10-07
Synaptic -> File -> History

Should show you what recent changes that have happened

Or if you don't see them there (Which for some reason I can't :/ 
)
Open up Ubuntu Software Center -> History

and then I guess you will just need to remove and reinstall the packages.
[I'm not a big user of Kubuntu so I'm guessing it is pretty much the same]

---

### Post by mikeydeeeee on 2011-10-07
Well yeah, I know what I installed, thank you.

The question is: How do I find out what the previous versions were, so I can go back to there?

Anyone?

---

### Post by duke.tim on 2011-10-07
I'm sorry if I misunderstood your question. 
(and I hope that wasn't a sarcastic 'thank you[very much]')

Synaptic Package Manager
Find what you installed
-> Package -> Download Changelog

It will show you all of the previous versions

---------------------

If you want to 'Force' use of a previous version
you can

Package -> Force Version
or Ctrl -E 
---------------------

If you want to find what the previous version was, you will
need to look through your logs

It will show this in: 
Ubuntu Software Center -> History
```
/var/log/dpkg.log
```
```
/var/log/apt/history.log
```

Or you might be able to see what previous versions were avalible through

Synaptic Package Manager
Find what you installed
Right Click Properties -> Versions

I hope this helps you with your question

---

### Post by mikeydeeeee on 2011-10-07
Sorry if I sounded a little snotty, I'm just annoyed with this distribution.  It's been giving me problems since day 1.

Sincere thanks for the help.  I'll give it a shot tomorrow.  Please stay tuned...

Go Philllies,
MikeD

---

### Post by mikeydeeeee on 2011-10-09
Well, that was hard to watch...  Phillies, I mean.

Anyway, I figure that outside of waiting for the next version of samba to come out, the best way to go would be to regress from the new version 'amd64 (3.5.8~dfsg-1ubuntu2.2, 3.5.8~dfsg-1ubuntu2.3)' to the last version which showed up in the apt history logs 'amd64 (3.5.4~dfsg-1ubuntu8 )' but I can't figure out how.

Using Synaptic -> Package -> Force Version, the only other choice is '2:3.5.8~dfsg~ubuntu2(natty)' , which aside of not being the version I want,  would cause kde-desktop to be removed.

I then thought that removing all the samba packages and rebuilding, but that would remove damn near everything.

Anybody done anything like this?
MikeD

---

### Post by capscrew on 2011-10-09
> **mikeydeeeee said:**
> Well, that was hard to watch...  Phillies, I mean.

Anyway, I figure that outside of waiting for the next version of samba to come out, the best way to go would be to regress from the new version 'amd64 (3.5.8~dfsg-1ubuntu2.2, 3.5.8~dfsg-1ubuntu2.3)' to the last version which showed up in the apt history logs 'amd64 (3.5.4~dfsg-1ubuntu8 )' but I can't figure out how.

Using Synaptic -> Package -> Force Version, the only other choice is '2:3.5.8~dfsg~ubuntu2(natty)' , which aside of not being the version I want,  would cause kde-desktop to be removed.

I then thought that removing all the samba packages and rebuilding, but that would remove damn near everything.

Anybody done anything like this?
MikeD

I believe it's possible to fix your problems.  I've had no problems with Samba 3.5.8.  Can you be more specific?  Are you having problems with NetBIOS names?  How are you mounting your shares?  What do you have to do to restore the mount?

---

### Post by mikeydeeeee on 2011-10-10
[I]I believe it's possible to fix your problems.  

[/I]Well, Ryan Howard's got to remember to bring his bat to the playoffs ... Oh, you mean with samba :(
[I]
I've had no problems with  Samba 3.5.8.  Can you be more specific?  Are you having problems with  NetBIOS names?  How are you mounting your shares?  What do you have to  do to restore the mount?

[/I]The mounted file systems live on a windows 2000 server named 'ren' on the local network.  I do a standard filesystem mount through fstab, the relevant entries being:
[FONT=Trebuchet MS]
[FONT=Century Gothic]//ren/music             /music                  cifs   nocase,mapchars,noperm 1 2
//ren/video             /video                  cifs   nocase,mapchars,noperm 1 2
//ren/hold              /hold                   cifs   nocase,mapchars,noperm 1 2
//ren/data              /data                   cifs   nocase,mapchars,noperm 1 2[/FONT]

[FONT=Arial]One of the nice things about this release is that it fixed a problem where some of the file systems (usually video and music, the bigger ones) would fail to mount.  Only other oddity previous to this release is that for some reason, a dummy entry [/FONT][/FONT][FONT=Trebuchet MS][FONT=Arial]shows up in kdiskfree[/FONT][/FONT][FONT=Trebuchet MS][FONT=Arial] for each mount point.

[FONT=Arial]Now they mount, but after some I/O activity, like playing music or video file, the[/FONT][FONT=Arial]re are gaps in the playback.  When attempting to move a large file like a video to the remote system, the target file seems to simply disappear.  When the root directory is listed, not only has the entire /video or /music structure disappeared, but the mount point as well.  The filesystems still show as mounted in df of kdiskfree, but issuing another mount command usually fixes the problem, but it comes back after more I/O.  

Now mind you, I'm not doing anything any differently now than I have been for some years now.  The only thing that changed is the version of samba.

I can't be the only person out there having this problem.
[/FONT][/FONT] [/FONT]

---

### Post by capscrew on 2011-10-10
> **mikeydeeeee said:**
> [I]I believe it's possible to fix your problems.  

[/I]Well, Ryan Howard's got to remember to bring his bat to the playoffs ... Oh, you mean with samba :(
[I]
I've had no problems with  Samba 3.5.8.  Can you be more specific?  Are you having problems with  NetBIOS names?  How are you mounting your shares?  What do you have to  do to restore the mount?

[/I]The mounted file systems live on a windows 2000 server named 'ren' on the local network.  I do a standard filesystem mount through fstab, the relevant entries being:
```

//ren/music             /music                  cifs   nocase,mapchars,noperm 1 2
//ren/video             /video                  cifs   nocase,mapchars,noperm 1 2
//ren/hold              /hold                   cifs   nocase,mapchars,noperm 1 2
//ren/data              /data                   cifs   nocase,mapchars,noperm 1 2
```

[FONT=Arial]One of the nice things about this release is that it fixed a problem where some of the file systems (usually video and music, the bigger ones) would fail to mount.  Only other oddity previous to this release is that for some reason, a dummy entry [/FONT][/FONT][FONT=Trebuchet MS][FONT=Arial]shows up in kdiskfree[/FONT][/FONT][FONT=Trebuchet MS][FONT=Arial] for each mount point.

[FONT=Arial]Now they mount, but after some I/O activity, like playing music or video file, the[/FONT][FONT=Arial]re are gaps in the playback.  When attempting to move a large file like a video to the remote system, the target file seems to simply disappear.  When the root directory is listed, not only has the entire /video or /music structure disappeared, but the mount point as well.  The filesystems still show as mounted in df of kdiskfree, but issuing another mount command usually fixes the problem, but it comes back after more I/O.  

Now mind you, I'm not doing anything any differently now than I have been for some years now.  The only thing that changed is the version of samba.

I can't be the only person out there having this problem.
[/FONT][/FONT] [/FONT]
Texas takes it all!  Also; watch for the Rugby World Cup Finals on 10/23.  Football with no helmets.  :D

Back to the business at hand: I really don't know what to say.  I never mount SMB shares using fstab.  I let Nautilus do that.  

I regularly move (and create) 20+ GB files (meaning a single file being greater than 20GB) to a SMB Share.  I have only once had problems.  This turned out to be *resource exhaustion*.  That particular Samba server is a P3 with 512 MB of RAM.  

I believe it must have been a race condition.  When I looked at *top* (actually htop) I could see the load averages touching 1.0.  I suppose that the connection was dropped and could not establish itself again.  The error logs pointed to that.  After I rebooted the Samba server I monitored the system load and have not not seen those kind of loads again.  Check the logs to see what actually happens when you have a failure.

In the past I have bypassed all of the GUI interface and moved files using the command line.  You can try that method (smbclient) and see what happens.  It works more like FTP and I have never had problems that way.

I do see that these are multimedia files and I wonder if the applications (video and music) might be the culprit.  There are plenty of stories about how Open Office is not Samba aware.

---

### Post by mikeydeeeee on 2011-10-11
Well yes, I'm aware there are other ways of making remote file systems available to a *nix system, but this is the way I'm used to doing it, and like I said, it's worked fine up till now.

I'm getting used to the idea that I'm going to have to back out this update, going from the 2:3.5.8 samba utils back to 2:3.5.4 and losing KDE in the process.  Obviously, I'll have to do this at the command line level, which will be a pain.  On the good side, looks like a new version of KDE is out there anyway, so the net pain should be mitigated.

Be back in a few days ... hopefully.
MikeD

---

### Post by mikeydeeeee on 2011-10-15
For whatever reason, simply removing and reinstalling samba and all associated packages seems to have fixed the problem.  It actually only involved maybe a dozen packages as 'kde-desktop' isn't actually the whole of kde, but only one small part of it.  Everything looks fine.

Before doing this, I did try to regress samba to 3:5.4 from 3:5.8, but had no luck.  Couldn't even get the earlier package to download.  Went all through the 'apt-get' documents, but never got a version back lower than 3:5.8.  Not sure why.

Anyway, back to work.
MikeD

---

### Post by mikeydeeeee on 2011-10-15
On a completely different note:

RIP: [Dennis Ritchie]("http://www.salon.com/2011/10/13/dennis_ritchie_the_geek_prometheus/").

Say Hi to Steve for us!
MikeD

---

