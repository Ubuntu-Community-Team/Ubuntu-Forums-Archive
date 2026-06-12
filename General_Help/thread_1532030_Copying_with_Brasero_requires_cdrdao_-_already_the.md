---
title: "Copying with Brasero requires cdrdao - already there"
date: 2010-07-15
forum: General Help
---

### Post by FredVanH on 2010-07-15
Hi.  I tried to copy a CD with Brasero.  Brasero said:  "All required applications and libraries are not installed.  Please install manually and try again:
toc2cue (application)
cdrdao (application)
toc2cue (application)
cdrdao (application)".
Ignoring that each was listed twice, I first ran sudo apt-get update on the terminal, then ran
sudo apt-get install cdrdao
I tried another copy operation, but this time:
The error message for a missing toc2cue was no longer there, but there were still 2 error messages for a missing cdrdao, which I had just installed!
I tried installing cdrdao again;  but got the message that the latest cdrdao was already installed.
I tried installing toc2cue but got the message that it could not be found.
Anyone know how I can get cdrdao to be recognized and toc2cue to get installed?
Thanks,
Fred

---

### Post by sau99ms on 2010-07-16
> **FredVanH said:**
> Hi.  I tried to copy a CD with Brasero.  Brasero said:  "All required applications and libraries are not installed.  Please install manually and try again:
toc2cue (application)
cdrdao (application)
toc2cue (application)
cdrdao (application)".
Ignoring that each was listed twice, I first ran sudo apt-get update on the terminal, then ran
sudo apt-get install cdrdao
I tried another copy operation, but this time:
The error message for a missing toc2cue was no longer there, but there were still 2 error messages for a missing cdrdao, which I had just installed!
I tried installing cdrdao again;  but got the message that the latest cdrdao was already installed.
I tried installing toc2cue but got the message that it could not be found.
Anyone know how I can get cdrdao to be recognized and toc2cue to get installed?
Thanks,
Fred

I've got the exact same problem on 64 bit Ubuntu 10.04....can anyone help?

---

### Post by mc4man on 2010-07-16
There are loads of bug reports, fixes released, but usually never works. (same for the rhythmbox plugin

(I myself use Imgburn in wine for copying a complete cd

[https://bugs.launchpad.net/ubuntu/+source/brasero/+bug/529696](https://bugs.launchpad.net/ubuntu/+source/brasero/+bug/529696)

A new bug, will probably get duped
[https://bugs.launchpad.net/ubuntu/+source/brasero/+bug/605637](https://bugs.launchpad.net/ubuntu/+source/brasero/+bug/605637)

At the bottem of the first listed bug is a ppa that may fix in lucid, gave it a try and worked 'to some degree'
(rhythmbox still failed here

I only updated the brasero packages and cdrdao from the ppa

A restart was required, initially no r. click "copy disc" showed up but when inserting an audio cd, holding down shift button and choosing brasero from pop up did work

now the r. click copy cd is there.

ppa
[https://launchpad.net/~renbag/+archive/ppa](https://launchpad.net/~renbag/+archive/ppa)

---

### Post by FredVanH on 2010-07-17
Thanks, sau99ms, for your validating reply and to mc4man for your most informative reply - especially your link to bugs.launchpad.  There I learned that Brasero basically just will not copy CD's, this has been reported as a bug many, many times since February (that's 5 months), many esoteric partial fixes have been toyed with;  and the bug status jumps back and forth from fixed to not fixed.  If this is not true, I apologize for my assumptions.

I'm very grateful to those who have tried solutions.  I've tried some and could not understand others.  Many of those I tried failed for the system not having some command available.  Many times I read later in the link that that was also experienced by others.  I'm hopeful that increased priority may be given to fixing Brasero so that it works without going into Terminal and doing ten or twenty "but firsts";  because a simple CD copy seems elementary.  I had to go back to the unmentionable to copy one and this is not the way I want to go.

I'm also grateful to those who wrote Brasero and Ubuntu and realize it's an ongoing process;  however, from a production point of view, I'm hoping for results which I can't affect (or effect!).
Thanks for listening,
Fred

---

### Post by digitography on 2010-08-07
I too have exactly the same problem. The message I get is to install cdrdao manually which I do

sudo apt-get install cdrda

reading package lists... Done
Building dependency tree       
Reading state information... Done
cdrdao is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

So it's there but it doesn't look like it is seen.

I may have to go back to W!#$%^&$

---

### Post by FredVanH on 2010-08-07
Hey, Digitography.  Thanks for your response.  Hopefully the following was just a typo in your reply;  but did you leave the last "o" off the "cdrdao" in your command?

BTW - I found a good program to copy a CD in Ubuntu.  It's a KDE desktop program called K3b.  To do it in Windows XP, InfraRecorder works well.  To copy a DVD in Ubuntu, Brasero works.  To do that in Windows, I haven't found any free progs to do that so far.

---

### Post by digitography on 2010-08-09
After a lot of searching I found the solution.

cdrdao is version 1.2.2 and brasero needs 1.2.3, although there is no managed installer for it.

I finally found this on launchpad

[https://launchpad.net/~renbag/+archive/ppa]("https://launchpad.net/%7Erenbag/+archive/ppa")

someone far cleverer than me built an installer for it, I followed the instructions so that if would install, and Voila brasero now works, well at least the copy to iso works, which is what I wanted.
Hopefully when Ubuntu moves on to the next update this will be fixed, cos frankly it's doozy of a problem that seems to have many many manifestations.

---

### Post by inameiname on 2010-08-09
Here you go, install this version of cdrdao and it should work fine. It's the one from renbag.

---

### Post by inameiname on 2010-08-09
Oops, I clicked the link and saw there is a newer version out now. Here is that one from that PPA:

Also, I must ask the others who have used that PPA, I tried it a while back and the reason I only installed the cdrdao deb and only that one from it is that the rest would break brasero. Has anybody else had that issue? Of course, it seems many have had similar woes.

UPDATE:

So I got bored and decided to try out the renbag ppa again, and it actually seems to work now. Not sure why now. Although, I am running linux kernel 2.6.35-14-generic, so maybe that changed something, idk.

---

### Post by ewan86 on 2010-08-17
> **inameiname said:**
> Oops, I clicked the link and saw there is a newer version out now. Here is that one from that PPA:

Also, I must ask the others who have used that PPA, I tried it a while back and the reason I only installed the cdrdao deb and only that one from it is that the rest would break brasero. Has anybody else had that issue? Of course, it seems many have had similar woes.

UPDATE:

So I got bored and decided to try out the renbag ppa again, and it actually seems to work now. Not sure why now. Although, I am running linux kernel 2.6.35-14-generic, so maybe that changed something, idk.

Thank you I downloaded the .deb and now brasero works perfectly at copying a cd straight to a blank cd. Now I just have to work out why it wont blank DVD's!!!

---

### Post by FredVanH on 2010-08-17
Thanks, guys/gals for sticking with it!  I downloaded and installed your latest solution and it works great!:D - Brasero now copies CD's for me.  For those even newbie-er than me, I should comment that the process of getting it installed was not super-intuitive.  Many screens just sat there without explanation and I had to guess at what to do.  On the other hand, even I figured it out, so it's all good.  Several times, the dialog implied I should pick out a directory in which to place some unspecified entity.  I chose Desktop each time and it seemed to be an OK choice.
I'm marking this "solved", thanks (again) to you folks.  Nice going!
Fred

---

### Post by inameiname on 2010-08-17
That's great you both got it working. I seriously don't get why such a bug was left in Lucid, as burning CDs with Brasero is sort of a main thing. hehe. Ah well. Least the solution wasn't too difficult.

---

### Post by ve7eme on 2010-08-28
Thanks for the file, and hints for the install,that has put a few hours search, trail and error to bed for me. Solved ! :KS

---

### Post by cor2y on 2010-08-29
Thanks for this thread and the solution.
This is one of the reason i dont really like brasero because of things like these.
Lets hope come 10.10 this is fixed along with a few other things like the plugins for brasero.

---

### Post by inameiname on 2010-08-29
From what I've heard it probably will not be fixed in 10.10. It's one of those upstream bugs that will just continue:

[http://www.omgubuntu.co.uk/2010/08/fix-brasero-copyburn-error.html](http://www.omgubuntu.co.uk/2010/08/fix-brasero-copyburn-error.html)

What I agree with many of those who commented from this link is how pathetic it is a fix is required from a PPA for an official app and version in the official repos. That's not supposed to happen. :P

---

### Post by x-x on 2010-09-12
I Just tried the link above and during the install process I got the message

Error: Wrong architecture 'i386'

My system is an AMD64. Is there a 64-bit version of cdrdao_1.2.3?

Or is there a way to make the i386 version run on my system?

thanks;)

---

### Post by inameiname on 2010-09-13
This link has a AMD64 version. Just download it directly, or add the PPA:

[https://launchpad.net/~renbag/+archive/ppa/+packages](https://launchpad.net/~renbag/+archive/ppa/+packages)

---

### Post by x-x on 2010-09-16
thanks inameiname

by installing cdrdao1.2.3 problem with brasero solved!

thanks

---

### Post by inameiname on 2010-09-16
No prob.

---

### Post by dexterslab on 2010-09-21
> **inameiname said:**
> This link has a AMD64 version. Just download it directly, or add the PPA:

[https://launchpad.net/~renbag/+archive/ppa/+packages](https://launchpad.net/~renbag/+archive/ppa/+packages)

Thanks!!! this worked for 64bit version \\:D/=D>

---

### Post by giodemon on 2010-10-17
gracias realmente funciona:guitar:

---

### Post by JamButty on 2010-10-23
Another bit that is confusing. OP states the error is
"All required applications and libraries are not installed.  Please install manually and try again:
toc2cue (application)
cdrdao (application)"
Which is correct - that is still the error Brasero gives, but in addition to the problem of the missing 1.2.3 version of cdrdao (yes, it worked for me too), the other application is actually
cue2toc, NOT toc2cue as the error states.

For me another issue with this is that the default image type is the TOC/BIN combination rather that the more commonly used ISO. Needing to dig into the properties to get to this rather than having ISO as the default is puzzling.

Another issue with Brasero is it's "windows compatibility" file naming bits.  Seems to be stuck in a reference to 20 year old MS systems - there has been no compatibility issues I know of for at least 10 years. Referring to the most archaic common denominator is not really needed. Further - if you choose to not "make it compatible" it DOES make it compatible with MS systems of 20 years ago (8 char filenames). If you choose to "make it compatible", it does not seem to change any filenames, though occasionally it will bomb out claiming it could not change some filenames, but never displays any of the filenames that are supposedly the problem and leaving the user to make guesses. Not an insurmountable problem, just irritating.

As long as I am sounding off on TOC/BIN/ISO, let me put in a plug for AcetoneISO, a gui for various operations on such files. I tried many commands suggested on various pages for mounting/unmounting ISOs, also full scripts that supposedly  added these options to the Nautilus GUI, but none of them worked. AcetoneISO works for dummies like me.

No issues to solve - just info. Thread still "solved"

---

### Post by Objekt on 2010-10-26
cdemu is also pretty darn good for mounting CD/DVD images.  It's sort of an Ubuntu equivalent to Daemon Tools in Windows, only it doesn't try to sucker you into installing a useless browser toolbar.

cdemu can handle Blu-ray images, which is handy for those of us who don't have a Blu-ray drive.

Anyway, more on topic, I can now use Brasero to rip audio CDs to images.  I had the previously discovered errors.  Finally got Brasero ripping audio CD's by:

1) installing the packages it asked for (cue2toc & cdrdao) by hand through Synaptic;
2) upgrading cdrdao to version 1.2.3 by adding the author's ppa, as detailed on an earlier page of this thread.

Note that I'm running the 32-bit flavor of Ubuntu 10.04, not that it should matter.

It seems a bit inelegant that an audio CD has to be imaged into 2 separate files, one with the raw data and one showing where the tracks begin and end.  Has someone devised a single-file image format for audio CD's in the meantime?

---

### Post by Mike_tn on 2010-11-11
> **inameiname said:**
> This link has a AMD64 version. Just download it directly, or add the PPA:

[https://launchpad.net/~renbag/+archive/ppa/+packages]("https://launchpad.net/%7Erenbag/+archive/ppa/+packages")

Running 64bit Maverick. Wonder if this works? It's labeled Lucid at the PPA site. Do I have to waste a disk possibly or does anyone know?  There is one other Maverick package there. Perhaps not supported yet.

---

### Post by Mike_tn on 2010-11-13
SOLVED

removed Brasero and added K3b

---

### Post by inameiname on 2010-11-13
Well, Mike_tn, there is a Maverick version of Renbag's ppa, but there isn't a Brasero fix there. Though, do you have issues with Brasero on Maverick? I found the problem that Renbag's Lucid ppa fixed in Lucid isn't there for me to deal with in Maverick.

---

### Post by Mike_tn on 2010-11-16
> **inameiname said:**
> Well, Mike_tn, there is a Maverick version of Renbag's ppa, but there isn't a Brasero fix there. Though, do you have issues with Brasero on Maverick? I found the problem that Renbag's Lucid ppa fixed in Lucid isn't there for me to deal with in Maverick.

inameiname, I only had definite issues with Brasero iso burn failures in Lucid.  I never tried Maverick except to burn an APTonCD iso that seemed to burn OK however it was a bad test because I think the APTonCD application is quite temperamental at least for myself.  So I didn't give Brasero a fair test on Maverick. 

I've had so many burners I hated over the years, I wanted to avoid the headaches of trial and error. Brasero may be fine in Maverick but the forums I located didn't have anything good to say. In the forums they talked of Brasero not being fixed with the new release, the posted comments had current dates.  

Comparing the GUIs to burn ISOs in the two, K3b seemed more advanced. I didn't do a huge comparison.  At first look it reminded me of the difference between Gnome Commander and Krusader of which Gnome Commander is no match whatsoever for, so I decided to use K3b. Burning ISOs for music or data is no easy job.  Even if the app can burn a disc, results can be flawed. A burner needs a good long standing reputation. Already removed Brasero so I can't glance at it now. My decision to do the burner switch was not based on thorough and recent testing by myself....more by first looks & hearsay.

---

### Post by Swagman on 2010-11-16
> **Mike_tn said:**
> SOLVED

removed Brasero and added K3b

Hows Normalise work for you in K3B ?

---

### Post by Mike_tn on 2010-11-16
> **Swagman said:**
> Hows Normalise work for you in K3B ?

I saw the "normalize-audio" add-on in the Software Center but elected not to add it.  I only would use it for compilation music CD which I never make.  And the few I once made I never listen to.  If that button on other software is unknowingly selected and I find out later, after burning a bunch of discs,  well let me say...livid would describe me. So I thought it was cool that I could in effect uninstall that feature. I can see how it would be good for making your own greatest hits volumes. I always listen to full albums.

Did you have problems with it not doing its job?

---

### Post by Swagman on 2010-11-17
> **Mike_tn said:**
> I saw the "normalize-audio" add-on in the Software Center but elected not to add it.  I only would use it for compilation music CD which I never make.  And the few I once made I never listen to.  If that button on other software is unknowingly selected and I find out later, after burning a bunch of discs,  well let me say...livid would describe me. So I thought it was cool that I could in effect uninstall that feature. I can see how it would be good for making your own greatest hits volumes. I always listen to full albums.

Did you have problems with it not doing its job?

[img]http://www.upload3r.com/serve/171110/1290006308.jpeg[/img]


```


paul@pauls-desktop:~$ sudo apt-get install normalize-audio
[sudo] password for paul: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
**normalize-audio is already the newest version.**
0 upgraded, 0 newly installed, 0 to remove and 4 not upgraded.
paul@pauls-desktop:~$

```



If (you can be bothered) you goggle it there is quite a bit about it but no copy & paste this cure.


Just the usual "Secret handshake whilst standing on one leg, nudge nudge, wink wink"  hints.


After googling for eleventy million hours I ended up firing up Brasero and dragging over my burn list into it. Normalize-Audio worked in Brasero no probs.

---

### Post by Mike_tn on 2010-11-17
> **Swagman said:**
> 
Just the usual "Secret handshake whilst standing on one leg, nudge nudge, wink wink"  hints.

After googling for eleventy million hours I ended up firing up Brasero and dragging over my burn list into it. Normalize-Audio worked in Brasero no probs.

secret handshake....Snicker~

Hey I googled for the answer and found this thread at the top :) is that a sign? Seems everyone has the problem, even people running Kubuntu. Mostly Lucid users mentioned.  No PPAs either. Audio is a tough gig.  Hmmm. Sometimes we have to work around with other apps as you are. One person in an old old post said they normalized afterwards with Audacity.  Audacity is fun. 
Off track...
I have a Firefox bug that pixillates images if you enlarge them such as with Control+MouseWheel. No cure other than a PPA that outdates everytime Firefox updates and who knows what else it does to you. So I don't zoom images, just zoom text a bit and use Chromium if I get annoyed. It was annoying at first because photography is my main hobby along with Linux lately. My photo stream [http://www.flickr.com/photos/beginasyouare/](http://www.flickr.com/photos/beginasyouare/)
But it's really best to go to All Sizes and get a larger original, zoomed images softened, not really better resolution.
One thing good, the bug got me to try out a new browser. So that's how I see Linux. Every bug fix teaches solutions or new tools to compensate etc. Im reading how to compile an html tarball on GIMP...DOH just found out I don't need to compile it, just click one header page in the archive.
But I digress...

Glad Brasero is putting out normalization for you, that's good news, I assume that means it burns a good music ISOs to CD in Maverick? That would be good to know in case I need it later. I am also guessing you'd prefer to use K3b if you could.  

The hair pulling of computing are audio ISO burning and running graphic chipsets,  in those areas I like stuff that works from the get-go, no patches. Wireless drivers aint no cupO'tea either but what a celebration when you get online with Linux for the first time ha ha. I liked IMGburn in the other OS. I hope I can find its equal for my needs.  Everyone's needs vary.  Needing apps like IMGburn are what led me to Linux.

Currently am dual booting and have used Ubuntu-Gnome for most everything except trying KDE apps in burning, file analysis, and today downloaded digiKam but not sure I need it.  When I needed 2 dozen distro ISOs burned while picking out the best one to install, I went back to the other OS and used IMGburn....otherwise I never would have seen that monster in those days....Wind_OS, I call it on my hard drive now.
Keep burning and rock on....or perhaps you normalize classical or something else, that's OK too.

---

### Post by JamButty on 2010-11-17
I've give up for now on Brasero. I've never had a need to normalize so that is not yet a issue for me. I moved over to K3B (thanks for the tip Mike_tn!) Been burning a lot lately on that and it has worked flawlessly. Light years ahead of Brasero.

---

### Post by Mike_tn on 2010-11-20
Thanks for the vote for K3b [JamButty]("http://ubuntuforums.org/member.php?u=1134643")
I used it for my first burn, made an ISO burn of Peppermint Linux and it ran great from Live CD. Nice program!  Also decided to edit fstab in /etc/fstab so my computer mounts the partitions that stored my ISO saves at boot time. Now K3b sees all my partitions.

---

### Post by Steveareeno on 2010-11-23
> **Mike_tn said:**
> SOLVED

removed Brasero and added K3b

:D  I too was fustrated by this bug.  I'm running 10.10 and was getting the message indicating need to update to later version of Cdrdao.  When I attempted some of the suggested fixes I'm kept getting errors.  Thus, I removed Brasero and Added K3b.  NO PROBLEMO.  Works great.

---

### Post by herdivet on 2010-12-14
I'm with Steveareeno - have 10.10 and when I try to install the CDRDAO_1.2.3-Orenbag2_i386.deb I get a message 'Dependecy is not satisfiable: libao2 (>-0.8.8).

If I try to install libao2 it tells me that has been deprecated and 10.10 is using libaocommon.  

I guess it's time to dump Brasero and try the K3B solution.

- K3B works as advertised.  It works, Brasero does not.

---

### Post by crtlbreak on 2011-01-17
Many Thanks for your help in this ....;)

---

### Post by mkanuaraz on 2011-04-06
I got this log msg while trying to copy a winsvr disc:

Checking session consistency (brasero_burn_check_session_consistency brasero-burn.c:1741)
Unsupported type of task operation
Session error : An internal error occurred (brasero_burn_record brasero-burn.c:2839)

So I just run apt-get install cue2toc cdrdao and it solved... thanks all!

---

### Post by huwjenjinn on 2011-10-26
> **digitography said:**
> After a lot of searching I found the solution.

cdrdao is version 1.2.2 and brasero needs 1.2.3, although there is no managed installer for it.

I finally found this on launchpad

[https://launchpad.net/~renbag/+archive/ppa]("https://launchpad.net/%7Erenbag/+archive/ppa")

someone far cleverer than me built an installer for it, I followed the instructions so that if would install, and Voila brasero now works, well at least the copy to iso works, which is what I wanted.
Hopefully when Ubuntu moves on to the next update this will be fixed, cos frankly it's doozy of a problem that seems to have many many manifestations.

Many thanks for the linkage. Solved my CD copy on Lucid. Once I added that renbag PPA to my repositories it offered to upgrade Brasero from 2.30.0 to 2.31.2 Accepted and all sorted.

---

