---
title: "Ubuntu 10.04 and Evolution 2.28.3 problem"
date: 2010-05-04
forum: General Help
---

### Post by LANSA301 on 2010-05-04
Recently I updated to 10.04 and I begin to have an issue with the Evolution mail 2.28.3.
Originally I installed Ubuntu 8.04, latterly updated to 8.10, 9.04 and 9.10 keeping the EXT3 partition.
My system is updated and upgraded.
I always use Evolution mail with no problems, but since I updated to 10.04 the Evolution suddenly closes with no warning or error message.
The applications runs around 30 minutes and later simply closes.
I checked the log and I have no single message about the issue. Also I looked around and no one reported a similar problem.
I really appreciate your help.
Kindest regards,

---

### Post by dcstar on 2010-05-05
> **LANSA301 said:**
> Recently I updated to 10.04 and I begin to have an issue with the Evolution mail 2.28.3.
Originally I installed Ubuntu 8.04, latterly updated to 8.10, 9.04 and 9.10 keeping the EXT3 partition.
My system is updated and upgraded.
I always use Evolution mail with no problems, but since I updated to 10.04 the Evolution suddenly closes with no warning or error message.
The applications runs around 30 minutes and later simply closes.
I checked the log and I have no single message about the issue. Also I looked around and no one reported a similar problem.
I really appreciate your help.
Kindest regards,

Rename the .evolution folder and start Evolution so it creates a fresh profile.

If this now works then something is corrupt/incompatible in the old profile, you can copy various folders from the old to the new to restore your data.

---

### Post by LANSA301 on 2010-05-05
Thank you. I'll try your solution tonight and I let you know if my problem is solved.
Kindest regards,

---

### Post by LANSA301 on 2010-05-05
Well, your solution is not working for me. I renamed the .evolution folder and launch the Evolution. But again closes with no warning.
Last night I launched the application from the console using gdb and when the applications closes the console show me this error:

***MEMORY-ERROR***: evolution[7628]: GSlice: assertion failed: sinfo->n_allocated > 0

Program received signal SIGABRT, Aborted.
[Switching to Thread 0xad8f7b70 (LWP 8263)]
0xb7fe2422 in __kernel_vsyscall ()
(gdb)

---

### Post by sgosnell on 2010-05-05
There is a bug in Evolution that causes crashes, and AFAIK it is still unfixed.  It seems to have a connection with syncing with Google or other online calendars.  Mine crashed every time I clicked on the Calendar button, and I was never able to solve it until I installed Lucid with a new installation instead of an upgrade.  I can't find where the offending settings are stored, but they're somewhere.  I've purged Evolution many times, and deleted the .evolution directory in my home, but nothing worked except a complete new OS install.  There are open bugs on launchpad, and I've about decided that they will never be fixed.

---

### Post by dcstar on 2010-05-06
> **LANSA301 said:**
> Well, your solution is not working for me. I renamed the .evolution folder and launch the Evolution. But again closes with no warning.
Last night I launched the application from the console using gdb and when the applications closes the console show me this error:

***MEMORY-ERROR***: evolution[7628]: GSlice: assertion failed: sinfo->n_allocated > 0

Program received signal SIGABRT, Aborted.
[Switching to Thread 0xad8f7b70 (LWP 8263)]
0xb7fe2422 in __kernel_vsyscall ()
(gdb)

You can create a new user, log into it and do a fresh setup of Evolution.

If it works then there is a problem in the legacy profile that you upgraded from, if it still crashes then the problem is in the underlying system.

I **always** do a new install instead of an upgrade because of issues like this with many applications.

---

### Post by LANSA301 on 2010-05-06
Thank you all. You are totally right. Nothing is better like a fresh install. Is like the 'spring clean' to drop all the unused stuff. This days I am pretty busy so I updated. Well the weekend is close and maybe I can attend my computer scream 'please format me!'
Regards,

---

### Post by cooldot on 2010-05-06
I think you'll find the developers know about this, it was the same in the pre-release. I hope they fix it SOON  

Fresh install? Not an option for me, I use Ubuntu for business work. Yes I back up, but I don't want to go to use something then remember I need to install it again. Having said that, the upgrade path is next to useless with anything less than a speedy connection. I set it away upgrading at lunch time, went to bed that night, got up in the morning and finished off the upgrade!

---

### Post by sgosnell on 2010-05-06
Try doing this:  ```
dpkg --get-selections > ~/my-packages
```This places a list of all your installed packages in your home folder, named 'my-packages'.  When you do a new install, run ```
sudo dpkg --set-selections < my-packages && sudo apt-get dselect-upgrade
```  This will reinstall all your packages.  Plan to allow plenty of time for this.  It isn't perfect, and only packages in the repositories will be reinstalled.  You'll have to do the rest manually.  On my system, truecrypt, Citrix, and several others have to be manually installed, which is a pain, but at least the bulk of the packages get installed.

---

### Post by dcstar on 2010-05-07
> **sgosnell said:**
> Try doing this:  ```
dpkg --get-selections > ~/my-packages
```This places a list of all your installed packages in your home folder, named 'my-packages'.  When you do a new install, run ```
sudo dpkg --set-selections < my-packages && sudo apt-get dselect-upgrade
```
........

There is no need to use the command line for this when Synaptic has a perfectly good GUI mechanism for saving the package markings and then reloading them on a new system.

---

### Post by dedika on 2010-05-07
dear all,
     i use ubuntu 10.04 and i want to use evolution for my company mail that use exchange server. but unfortunately, i don't find option in dropdown list menu for exchange client in evo 2.28.3.

     plz, could you help my problem ?


tx/rgds

Dedika

---

### Post by sgosnell on 2010-05-08
Select Edit/Preferences.  Either add a new account, or edit the current one.  If you edit the current account, on the Receiving Email tab, there is a dropdown list, and you can pick Exchange. If you add a new account, select Exchange at the start.

---

### Post by duble08 on 2010-05-09
back onto topic about the automatic shut down of evolution...

I too have this problem - it seems most of you have chosen to upgrade ubuntu from previous versions, thus relating to the issue - my install was a fresh install from the beginning.  i used to use 9.10, but when 10.04 came out, i backed everything up, did a repartition and a format of all drives (including swap space) and installed 10.04 right from the cd upon boot up.  that's as clean of an install as you can get.  so i'm guessing that this issue is rooted more deeply, either in compatibility with ubuntu 10.04 and evolution, or a problem with evolution itself (is the version of evolution different when included in 10.04 compared to 9.10? maybe it contains a bug?) any help would be awesome in fixing this! i'm going to hound around a bit more to see if i find any fixes on other forums, and if i do, i'll post a link here.

Thanks guys!

---

### Post by sgosnell on 2010-05-09
Did you keep your /home folder unchanged?  A new install of the OS won't necessarily change anything in your /home, if it's on a different partition.

---

### Post by duble08 on 2010-05-11
> **sgosnell said:**
> Did you keep your /home folder unchanged?  A new install of the OS won't necessarily change anything in your /home, if it's on a different partition.

i don't think i understand what you mean by this, if you're relating to my reply... the way i set up my install was by removing the 2 partitions (ext3 and swap, which then makes them "combined" so to speak, even though it's considered unallocated), then recreated them (240gb on ext3, with root set to "/", and then created a 10gb partition for swap), formated the ext3 (i would've formated swap too, but there was no option to do so), and then did the install on the ext3 partition (obviously).  i have issues with evolution shutting down randomly, but mine seems to do it when the computers idle for a while (such as when it's gone into a screensaver for an extended period of time).  i don't know how i could keep my home folder "unchanged" if it was completely wiped off and then reconstructed by the installer. there's no weird partitioning going on - just a basic ext3 and the swap... i'm thinking one of the original posters might be right about evolution having a memory leak, which might be the cause of it.  i don't really know... just something to ponder on... let me know if anyone else has any ideas leading to a fix.

Thanks for helping!

---

### Post by sgosnell on 2010-05-11
OK, you wiped out your /home.  I set my system up with /home on a separate partition, so that I don't lose anything when I reinstall the OS.  That has a downside, though, since your configuration files are largely in your /home directory hierarchy.  The problems I've hade with Evolution crashing are a result of syncing with Google calendar.  I've quit doing that since I finally got it working, through a new install.  I don't know what is causing your problems.

---

### Post by Usksider on 2010-05-12
Anyone know if there's any progress being made on this? I'm also suffering the problem.

Just for clarity I have a new installation of Lucid (X64 version), not an upgrade so there's no carry over from a previous version.

---

### Post by mune on 2010-05-12
I upgrade to lucid, too.

I have the same autoclosing problem.

Moreover I have this issue [[No accent in evolution]]("http://ubuntuforums.org/showthread.php?t=1480256"), but I don't know if it can be related.

---

### Post by nozema on 2010-05-16
Same problem here, randomly closes...
I've installed 10.04, no upgrade. Format of my HD inc. /home, did a restore from backuparchive off Evolution which was origanally started in 8.04, upgraded to 9.04 and 9.10, there it worked fine.

I have no clue where its coming from, just randomly closes, also sometimes when i hit new email...

---

### Post by groogruxking40 on 2010-05-17
same problem...

also sometimes when I click on Evolution the program doesn't even start..

anyone have this issue??

---

### Post by nozema on 2010-05-23
No progress yet?
Still being kicked out without any reason :(

---

### Post by Usksider on 2010-05-23
It's all getting to be a bit frustrating now isn't it? Don't get me wrong, I do love 10.04, but I never experienced this kind of issue with Karmic - or with any version of Outlook come to that. :(

---

### Post by sgosnell on 2010-05-23
I had the opposite experience.  In Karmic, Evolution just crashed immediately every time I clicked on Calendar or Tasks.  With Lucid, it works, and I've yet to have my first crash.  It's infinitely better than Karmic, which was pretty much a disaster all around.

---

### Post by LANSA301 on 2010-05-23
Well, I made a clean fresh Ubuntu 10.04 LTS installation and I still have the originally reported issue. The Evolution 2.28.3 continue crashing. Even I create a backup from my old Evolution I tried this time creating everything (accounts, signatures, etc.) manually to prevent import the error.
I'll keep looking for a solution.
Please let me know if anyone find it first.
Regards,

---

### Post by LANSA301 on 2010-05-23
[http://ubuntuforums.org/showpost.php?p=9325127&postcount=24](http://ubuntuforums.org/showpost.php?p=9325127&postcount=24)
Actually I'm trying this solution. I hope that finish my problem.
Regards,

---

### Post by LANSA301 on 2010-05-23
The posted solution to upgrade to Evolution 2.3 didn't works for me. I got the 'gray screen' issue and the reboot doesn't works. I'm reinstalling the 2.28.3 version...
PS. **'Gray screen' issue solved**: Upgrade libgtkhtml-editor-common #sudo apt-get upgrade
Testing Evolution 2.30.1.2.

---

### Post by darkstaar on 2010-05-24
Am I the only one who *isn't* having a problem with Evolution on 10.04? I use it extensively for work mail and Google Calendar and it runs flawlessly.

---

### Post by Usksider on 2010-05-24
> **sgosnell said:**
> I had the opposite experience.  In Karmic, Evolution just crashed immediately every time I clicked on Calendar or Tasks.  With Lucid, it works, and I've yet to have my first crash.  It's infinitely better than Karmic, which was pretty much a disaster all around.

It's interesting isn't it? I only had a couple of minor issues in Karmic and never with Evolution. I guess I was relatively late coming to Karmic though so perhaps the bugs had all been squashed before my initial install? It's the exact opposite with Lucid. Damn shame, because just about everything seems so good. I live in hope. ;)

---

### Post by Usksider on 2010-05-24
> **darkstaar said:**
> Am I the only one who *isn't* having a problem with Evolution on 10.04? I use it extensively for work mail and Google Calendar and it runs flawlessly.

That's good to know... I'll keep my fingers crossed and [-o<

---

### Post by dcstar on 2010-05-24
> **darkstaar said:**
> Am I the only one who *isn't* having a problem with Evolution on 10.04? I use it extensively for work mail and Google Calendar and it runs flawlessly.

I have found one issue where on new IMAP accounts on an upgraded Evolution system the Filters would not work for new incoming e-mails.

I have seemingly fixed it by renaming my .evolution folder, creating a new temp test access to that IMAP account and testing that the Filtering works, and then going back to my original .evolution folder. For some bizarre reason the IMAP filtering then functions as expected.

I suspect that the Evolution config settings are not all being upgraded correctly with each new Evolution version used, and forcing Evolution to create a fresh .evolution folder and then use an existing account syncs up the configuration to a state that works correctly with the latest version. It is in as a bug, I will await to see if the developers can do anything about it.

---

### Post by sgosnell on 2010-05-24
Usksider, I was also late to Karmic.  I ran the betas on my SD card, but had lots of problems with it, especially sound and Evolution, so I kept Jaunty on my HD until just a few months ago.  I finally installed Karmic well after its release, and hated it.  Lucid works ootb, haven't had a single problem with it yet.

---

### Post by LANSA301 on 2010-05-25
Well, the fresh Ubuntu 10.04 LTS Lucid installation didn't solve the Evolution issue. Neither the 2.28 to 2.30.1.2 Evolution upgrade. Evolution still closes with no warning.
Meanwhile I'm going to use Thunderbird 3 and hope I can use it with no problem until someday this issue is solved.
Thanks all.
Regards,

---

### Post by Bill_in_SD on 2010-05-25
I caught Evolution terminating unexpectedly with no warning. It did it while retrieving mail from a POP3 server.  I have about 7 accounts I check every 5 minutes so you can imagine how often evolution quits automagically.

For bug tracking:

Evolution closes unexpectedly when attempting to download email from POP3 server (randomly)

System:
Upgraded from 9.10 to 10.4 using update tool (Update Manager)
AMD64 Single Core 3000+
3 GB RAM
Hard drive (200GB) has 45% free space

Only other application open was Firefox (not on a Flash page or anything taxing)

---

### Post by LANSA301 on 2010-05-27
Update: Evolution continues unexpectedly closing but I discover that a Google Calendar appointment message kills immediately Evolution 2.30.1
I have been using my Evolution with five email accounts, four from google apps and gmail (POP3) and one from my local ISP (POP3). I'm guessing that the bug could be addressed to google accounts.

---

### Post by nozema on 2010-05-27
I have 12 accounts, most off them are from my own servers (from websites i've made) and 1 ¨free¨ account, all off them are pop3 but no google account.

I'm not using the calendar at all.

---

### Post by Bill_in_SD on 2010-05-27
Accounts are the following:

POP3 from GoDaddy, iPower, and sbcglobal.net

no calendar or any other usage.  My GoDaddy accounts use the 'secure' option. (SSL?)

---

### Post by Tenntrailblazer on 2010-05-28
I only have two pop3 accounts from comcast and don't use the calendar either.  I gave up.  didn't like the format of thunderbird so I still use it but I installed poptray minus. It gives me the subj lines and basic info so now i know what emails are in my box. I can let them stack up and when I want to read them open evolution read them and just close it again and not worry about it.

---

### Post by ilowrie on 2010-06-01
Have been experiencing this or similar problem -Evolution 2.30.1.2 unexpectedly closes - since upgrading to 10.4. Have 4 pop email accounts checking at default frequency (? 5 min). It rarely stays alive for longer than an hour or 2. Only using the mail function (and contacts when needed). Sometimes the app closes just as I am about to perform an operation - eg the last time I was just about to check how many accounts I have active and as my mouse went to the menus the app closed.

This has not resulted in any losses, but is frequent enough to have me considering going to another email client. Frustrating, as have not any issues in over 2 years. 

Ubuntu (normally) rocks!!!

Have not managed to create a bug report using bug buddy which seems not to be able to find enough evidence, but will try again later.

---

### Post by itmanvn on 2010-06-02
Hi all,

Try to install the 2.30 package [https://launchpad.net/~jacob/+archive/evo230](https://launchpad.net/~jacob/+archive/evo230)

Or run evolution with this command: > G_SLICE=always-malloc evolution

---

### Post by dede468 on 2010-06-02
I find the most irritating part of this is that it closes just when I'm about to send a long email etc. OK, it asks if I want to recover unfinished messages when I open it again but just in case.... does Evolution have autosave when composing?  I can't find it if it does and it doesn't seem to be turned on if there is one.

---

### Post by sgosnell on 2010-06-02
It should autosave to your home folder automatically, unless you do some serious editing of the configuration.  With a default install, it autosaves to a Drafts folder down in the .evolution hierarchy.  I don't recall the exact folder names, but it's there.

---

### Post by dede468 on 2010-06-03
Oh dear.... Well that doesn't happen which is why I wondered. Must be a prob with my Evo somewhere. Thanks for the reply and I'll look into it. It certainly doesn't autosave to the normal Drafts folder. I have to manually Save to Drafts.

---

### Post by sgosnell on 2010-06-03
Further reading of the Evolution docs seems to indicate that you may have to manually click on the Save to Drafts button in order to save a draft.  I believed that it was done automatically, but now I'm not sure.  I also didn't find a setting to control this.  It certainly should be a feature, but it might not be implemented.  You might try checking to see if there are any Evolution-specific forums on the interwebz, and ask for help there.

---

### Post by bhart007 on 2010-06-03
Same issue here with Evolution crashing with a Segmentation Fault.. However I seem to be the only one in this thread thusfar using the Exchange MAPI plugin.  I've also followed those instructions on upgrading Evo to 2.30...no help.  This is running 10.04 on a T43, fresh install.

I've commented on all the threads Ive found so far involving Evo and 10.04.

Seems being one of the most, if not THE most, popular Email client on linux the devs would put a little more importance on it.

Or if the devs checked the forums very often.

---

### Post by sgosnell on 2010-06-04
Expecting 'the devs' to 'check the forums' is expecting way too much.  There are literally dozens of Linux forums around, probably hundreds, and if they spent their time checking all of them, they would have no time to do any work.  This forum is for one specific distro, and there are many more distros around, almost all with their own forums, and there are many generic Linux forums around.  If you have a problem the only way to get 'the devs' to see it is to report a bug.

---

### Post by dudaah on 2010-06-09
Hey,

Here's my reply to this. I first upgraded my 9.x version to 10.04 and had this problem. I then backed my evolution data and reinstalled a fresh install of 10.04 and the problem was still there on the fresh install...

Now I tried opening it via terminal to be able to see if it gave me an error message when it closed down. And behold, it haven't closed in the past 45 minutes or so. Maybe the bug isn't there when opening it through the terminal? It could be because of other reasons, I'm an ubuntu newbie but it could be worth a shot I guess? If it indeed should close on me again I will post here to let you know...  :)

---

### Post by nozema on 2010-06-09
Havent thought about that before, opening in terminal. Did that and the error I got after Evolution closed:

***MEMORY-ERROR***: evolution[6068]: GSlice: assertion failed: sinfo->n_allocated > 0

---

### Post by dudaah on 2010-06-09
Well it was open a longer time than earlier but when I got home from work, it had actually closed down and the error in my terminal was the segmentation error I'm afraid. ;(

---

### Post by dudaah on 2010-06-09
and my latest evolution error *sigh*

ERROR:gkr-operation.c:392:gkr_operation_block: code should not be reached
Avbruten (SIGABRT)

I guess the evolution client and ubuntu 10.04 is not working very well together. :(

---

### Post by dcstar on 2010-06-10
> **dudaah said:**
> and my latest evolution error *sigh*

ERROR:gkr-operation.c:392:gkr_operation_block: code should not be reached
Avbruten (SIGABRT)

I guess the evolution client and ubuntu 10.04 is not working very well together. :(

Maybe, but you should check for any non-standard Evolution plugins that you may have running.

A lot of these things seem to cause problems because a lot of Evolution users using nothing but "vanilla" setups have few - if any - issues at all.

---

### Post by nozema on 2010-06-11
It also looks like it sometimes crashes when recieving spam:
> report junk?? That Paris, with his effeminate crew, his chin and oozy ha
Segmentatiefout


---

### Post by thewarlock on 2010-06-13
I'm having the autoclose issue as well.

Screensaver has always been active, and I haven't checked the logs yet.

Clean install of 10.04 but I had restored the mail/settings/etc from the 9.10 backup.  

7 email accts, a whackpot of filters, and using bogofilter antijunk filter as well.  No google calendar.

---

### Post by Rodneyck on 2010-06-15
There was an update for evolution today. I was hoping it would correct the crashing, but unfortunately that was not the case...Evolution still crashing. This is so annoying.

---

### Post by fonsi2099 on 2010-06-15
I've the same problem, do have somebody any idea? thank you

---

### Post by nozema on 2010-06-16
Also posted it here [https://bugs.launchpad.net/ubuntu/+source/evolution/+bug/584183](https://bugs.launchpad.net/ubuntu/+source/evolution/+bug/584183) but I have no idea what to do when they say: > We need a new log with dbgsym, please install the libcamel1.2-14-dbgsym,  evolution-dbgsym, evolution-data-server-dbgsym,  libglib2.0-0-dbgsym and libgtk2.0-0-dbgsym, We need a backtrace and a  valgrind log, Nils, Jean and Ubuntolo if you think you're getting the  same crash please provide the logs and let us to determine if that's the  same or not, commenting on random bugs because the title is probably  the thing you're facing isn't good and is not going to help us to solve  the issue, thanks.


---

### Post by LANSA301 on 2010-06-18
I still have the issue. The Evolution and Ubuntu kernel are updated to the last version but nothing looks to solve the problem.

---

### Post by Bruce L on 2010-06-22
I've been having the same problem ever since I loaded 10.04.  Evolution crashes for no reason.  Sometimes when the screensaver is active, sometimes when I just click on an email.  There is no real rhyme or reason.

Have the Evolution developers taken a look at this issue?

Obviously there are more than a few instances.  I figure about 100 times the number of problems that have reported are also experiencing the problem.

---

### Post by sfruitt on 2010-06-26
I hope this problem with evolution gets fixed shortly.  It worked fine in 9.10 and then I completely formatted and install 10.4 and now I have a problem with evolution closing for no reason.  I can be deleting mail or just reading mail and it closes.  Anywhere from 1 second to 5 minutes.  Next time it will stay open for hours as long I do not click on anything.

---

### Post by mune on 2010-06-28
I have the same problem.

Initially I upgraded from [past], 9.10, 10.04

As evolution haven't worked I did a fresh installation, copying all the .evolution gerarchy from a backup.

The random close isn't gone.

I waited for the new installation as I hoped  somebody'd someone found a solution in the meantime.

Fede

---

### Post by cydejsn on 2010-06-28
I am also experiencing the program closing.  In addition, I am getting Fetching mail errors (not every day, just some days), and it will forget saved passwords (only one, and the one it forgets is random).

---

### Post by nozema on 2010-07-11
It looks like the latest updates off Ubuntu 10.04 solved this bug?

---

### Post by luccapenguin on 2010-07-11
Yes.
At last...

---

### Post by CoolJohnB on 2010-09-27
It's back again in 10.10!!!

---

### Post by luccapenguin on 2010-09-27
10.10 is bugged? Beta?
Thanks...

---

### Post by Michl on 2010-10-04
Also have problems with Evolution and 10.04 in two different
computers.  Evolution freezes regularly, usually after I try
to close an email or send one.

---

