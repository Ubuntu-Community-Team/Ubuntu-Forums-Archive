---
title: "rsync script not working when run as cron job"
date: 2011-11-20
forum: General Help
---

### Post by NautiusMaximus on 2011-11-20
This is really a continuation of [another thread]("http://ubuntuforums.org/showthread.php?t=1872145") I started a while back, but since that thread has got a little of the point I thought I should start a new one.

My problem is that I am trying to back up the contents of my home directory to an external NAS drive (Buffalo Linkstation) using a simple script with rsync, which I run as a cron job.

The weird thing is that if I run the script manually from the terminal (using sudo), it works just fine. However, when I put it in my /etc/cron.daily folder in the hope that it will run as a cron job, it behaves very differently.

The important line in the script file (which I have called mybackup) looks like this:

```
rsync -tr --delete --exclude=".gvfs" /home/myname /media/lsduo
```

/media/lsduo is the mount point for my external NAS drive. This is mounted via /etc/fstab, with the following line:

```
//172.16.100.251/Ubuntu /media/lsduo	cifs	auto,guest,noperm,_netdev	0	0
```

I have tried to be as unrestrictive as possible with permissions, as I suspected that problems might be due to permissions. The fstab setup seems to work, as the drive mounts correctly on startup.

The script works perfectly well if type

```
sudo /etc/cron.daily/mybackup
```

at the terminal. This creates a folder on the NAS drive with the entire contents of my home directory. One slightly strange thing is that the owner of this directory is "user #99". Perhaps that's a sign that everything isn't all as it should be?

However, when it runs as a cron job, although it runs at the expected time, its behaviour is then very different. As far as I can see, it's copying everything across, but not respecting a directory structure: everything is just loose in the /media/lsduo folder.

But it gets weirder than that. If I view the contents of the folder through my Ubuntu PC, the files have names such as "\myname\documents\document.odt", as if they are trying to fit into a directory structure (yes, I did have those slashes the right way round). But the documents seem to be corrupted in some way, in that I can't open them.

On the other hand, if I view the contents on a Windows PC, the file names have become mangled, and have names such as "_2ZEG9~8.JPG" (the file extensions seem to be respected correctly). I can also open the documents without any problems on a Windows PC.

One other piece of information that may be relevant: if I try using the -a option in rsync, then I get error messages telling me that chown failed within rsync.

This is something to do with permissions, isn't it? Does anyone know what might be going on and how I solve it?

I'm using Ubuntu 11.04. The external drive is formatted with xfs and is set up with access permissions disabled. I have previously used chmod to set the permissions on the mount point folder to 777.

---

### Post by Paddy Landau on 2011-11-20
Notice that you run *rsync* successfully when you use *sudo*, which means you are running it as root.

I suspect that if you run it without *sudo*, it won't work (it's worth a try to see).

When you run it with *cron*, there is of course no *sudo*. That's why you get the error message regarding *chown*.

I suggest that you add it to root's cron instead of your own. In other words, first delete your entry from cron; then create the entry in root's cron:
```
sudo crontab -e
```

---

### Post by NautiusMaximus on 2011-11-20
Sorry, I'm not sure what you mean by "add it to root's cron instead of your own". I have put the script in /etc/cron.daily. The file /etc/crontab is set to run things in /etc/cron.daily. As far as I know, there is only the one cron for the system, which I thought (although I'm somewhere past the limits of my comfort zone here, so I could easily be wrong) ran as root.

If I've misunderstood that, how would I add it to root's cron?

---

### Post by rewyllys on 2011-11-20
I recommend that you use rsync by installing LuckyBackup, and setting up your backup schedule(s) in LuckyBackup.  That is very easy to do in LB.  

LB has worked flawlessly for me for over a year now.

---

### Post by dcstar on 2011-11-21
> **NautiusMaximus said:**
> 
.........
The weird thing is that if I run the script manually from the terminal (using sudo), it works just fine. However, when I put it in my /etc/cron.daily folder in the hope that it will run as a cron job, it behaves very differently.
.........
Running a script in a user shell is very different environment from cron running it:

[http://askubuntu.com/questions/23009/reasons-why-crontab-does-not-work](http://askubuntu.com/questions/23009/reasons-why-crontab-does-not-work)

---

### Post by Paddy Landau on 2011-11-21
> **NautiusMaximus said:**
> As far as I know, there is only the one cron for the system...
Nope.

Linux is set up so that, unless you run as root, you can change only your own stuff. Remember that Linux can allow two or more people to sign in *at the same time*, and so it carefully separates each person's behaviour so that one does not affect the other.

Therefore, when you run [FONT=Courier New][SIZE=2]crontab -e[/SIZE][/FONT], you change *your* cron. If you run [FONT=Courier New][SIZE=2]sudo crontab -e[/SIZE][/FONT] (where *sudo* means "temporarily run as another user, root by default"), you change *root's* cron. If you run [FONT=Courier New][SIZE=2]sudo -u alice crontab -e[/SIZE][/FONT], you change Alice's cron.

Commands in your cron run under your user with your permissions, and commands in root's cron run under root's user with root's permissions.

---

### Post by NautiusMaximus on 2011-11-21
OK, looks like I may have understood something about how cron jobs run. I'm new to this, so that's quite plausible.

This was how I understood things worked. Let me know which bit (or bits) I've got wrong.

I have a file /etc/crontab, the contents of which look like this:


```
# /etc/crontab: system-wide crontab
# Unlike any other crontab you don't have to run the `crontab'
# command to install the new version when you edit this file
# and files in /etc/cron.d. These files also have username fields,
# that none of the other crontabs do.

SHELL=/bin/sh
PATH=/usr/local/sbin:/usr/local/bin:/sbin:/bin:/usr/sbin:/usr/bin

# m h dom mon dow user	command
17 *	* * *	root    cd / && run-parts --report /etc/cron.hourly
25 6	* * *	root	test -x /usr/sbin/anacron || ( cd / && run-parts --report /etc/cron.daily )
47 6	* * 7	root	test -x /usr/sbin/anacron || ( cd / && run-parts --report /etc/cron.weekly )
52 6	1 * *	root	test -x /usr/sbin/anacron || ( cd / && run-parts --report /etc/cron.monthly )
#

```

I had assumed, because of what it said in the comments, that it was a system-wide thing, and not a per-user thing. I also assumed, because it said I don't have to run the crontab command, that I wouldn't have to run the crontab command.

The crontab file refers to various folders (/etc/cron.hourly etc) which run at the specified intervals, and if I put my script in the appropriate folder (I've used /etc/cron.daily) it would run, as root, at the specified times.

Well, it does run at the specified times, but with the odd behaviour I've already described.

So am I wrong about it running as root? If so, how do I access the root crontab? Or am I still misunderstanding something?

---

### Post by Paddy Landau on 2011-11-22
Ah, yes, there is a degree of misunderstanding.

First, realise that there is a *strict* separation of users within Linux. If you come from a Windows environment, this takes a little getting used to. What one user does cannot affect another user, ever, unless the latter user has given permission to the former. (Root is the sole exception, and can do anything to anything on the system.)

Cron is no different.

If you (as nautiusmaximus or whatever your username is) try to run programs in /etc/cron.hourly, you are trying to use cron to run cron while manually creating the cron files. It is a  little messy and definitely the wrong way of going about things. You are also trying to act like root even when you are not. That is bound to cause you problems, though fortunately (because of the strict separation of users) without damaging your system or any other use on the system -- though you could mess yourself up.

Ideally, you should *never* edit the cron file directly, but use the command [FONT=Courier New][SIZE=2]crontab -e[/SIZE][/FONT] to do so.

So, suppose you want to run the following commands (I've put just any old stuff here; don't try to read anything meaningful into it):
```
mydaystuff -d nirvana   # To run every day at 4:00 p.m.
myhourlystuff           # To run every hour on the hour.
prime --stuff           # To run every 13 minutes.
weeklybackup /home      # To run every Sunday at midday.
yearend                 # To run 1st January at midnight.
```**Repair**

As a first step, please *undo anything you did in /etc/crontab and elsewhere in /etc*. (You can back up any files first if you wish.) As a general rule, you do *not* manually change any files other than those in your own home folder (there are rare exceptions, but over time you will learn when to do that).

**Setting jobs through cron**

(From here on, where I talk about a command, it must be typed into the terminal unless otherwise stated.)

Type the following command. The bit in red is optional, but it will let you use a familiar editor so I suggest it.
```
[COLOR=Red]VISUAL=gedit[/COLOR] crontab -e
```Now add the following to the file. (Spacing is not important, so use any spacing you desire. Anything starting with a hash is ignored. The order of the lines is not relevant, except for the very first statement, so you may change their order. Also, remember that I made this stuff up -- you would put your own valid commands with timings there instead.)
```
MAILTO=''         # *[FONT=Verdana]I write about this later under "Other important notes".[/FONT]*

0    16 * * *     mydaystuff
@hourly           myhourlystuff
*/13 *  * * *     prime --stuff
0    12 * * Sun   weeklybackup /home
@yearly           yearend
```[FONT=Courier New][SIZE=2]@hourly[/SIZE][/FONT] is shorthand for [FONT=Courier New][SIZE=2]0 * * * *[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]@yearly[/SIZE][/FONT] is shorthand for [FONT=Courier New][SIZE=2]0 0 1 1 *[/SIZE][/FONT]

Save the file and close the editor.

At this point, *everything will run automatically at the right times.*

**Other important notes**


[LIST]
[*] To learn more about the funny time specifications in the cron table, use the command:```
man 5 crontab
```
[/LIST]

[LIST]
[*]If the jobs create any output (errors or otherwise), these will be emailed to you. This is *not* your Internet email, but an internal email system (the email system predates the Internet).

To check your internal emails, use the [FONT=Courier New][SIZE=2]mail[/SIZE][/FONT] command in terminal. It is, sadly, not an intuitive program to use. Use the command [FONT=Courier New][SIZE=2]man mail[/SIZE][/FONT] to learn to use it.

To prevent this from happening in the first place, use the command [FONT=Courier New][SIZE=2]MAILTO=''[/SIZE][/FONT] at the very top of the cron table.

You can also save your output. For example:```
@hourly myhourlystuff [COLOR=Blue]&>/home/nautiusmaximus/myhourlystuff.lst[/COLOR]
```The blue bit will redirect output (normal and errors) to the file [COLOR=Blue]myhourlystuff.lst[/COLOR] in your home directory (change [COLOR=Blue]nautiusmaximus[/COLOR] to your actual user name).
[/LIST]

[LIST]
[*]You cannot use [FONT=Courier New][SIZE=2]~[/SIZE][/FONT] or [FONT=Courier New][SIZE=2]${HOME}[/SIZE][/FONT] in your cron table, as they will not be initialised.
[/LIST]

[LIST]
[*]If any of the commands need to be run as root instead of as you, you will need to add them to root's cron table instead of yours. In other words, instead of:
```
[COLOR=Red]VISUAL=gedit[/COLOR] crontab -e
```you would enter:
```
**sudo** [COLOR=Red]VISUAL=gedit[/COLOR] crontab -e
```The commands in your and root's cron tables are run entirely independently of each other (remember that one user cannot affect another?).
[/LIST]

[LIST]
[*]If a program misses its slot, it will not be rescheduled. So a program that runs hourly on the hour will run every hour only when your computer is actually turned on.

To learn about how to run a skipped job automatically (e.g. the yearly or weekly job), read all about [FONT=Courier New][SIZE=2]anacron[/SIZE][/FONT].

To learn about how to submit a job just once instead of regularly, learn about the following commands: [FONT=Courier New][SIZE=2]at[/SIZE][/FONT], [FONT=Courier New][SIZE=2]atq[/SIZE][/FONT], [FONT=Courier New][SIZE=2]atrm[/SIZE][/FONT] and [FONT=Courier New][SIZE=2]batch[/SIZE][/FONT].

(To learn more about a command, type [FONT=Courier New][SIZE=2]man[/SIZE][/FONT] before the command, e.g. [FONT=Courier New][SIZE=2]man at[/SIZE][/FONT].)
[/LIST]

[LIST]
[*]To delete your entire cron table, use the following command:
```
crontab -r        # [FONT=Verdana]*To delete your own cron table.*[/FONT]
sudo crontab -r   # [FONT=Verdana]*To delete root's cron table.*[/FONT]
```
[/LIST]

[LIST]
[*]To just view your cron table without editing it, use the following command.
```
crontab -l        # [FONT=Verdana]*To view your own cron table.*[/FONT]
sudo crontab -l   # [FONT=Verdana]*To view root's cron table.*[/FONT]
```
[/LIST]

Happy "cron-ing"!

---

### Post by Jacobonbuntu on 2011-11-22
....there are two tools that make (cron-) scheduled backups with rsync really a lot easier for non geeks (like me :))

- Grsync
- Gnome schedule


[LIST]
[*]create your backups with the graphical interface of Grsync, run it once for a test-drive. if it works, copy the output (command) of the backup
[*]open gnome-schedule (GUI) and paste the output, set a schedule in the (easy) interface and voila!
[*]take care that you put directory names with spaces between ""
[/LIST]
if you want you can also make a quicklist of your backupscripts in the Unity launcher, no separate script-files needed :)

---

### Post by Paddy Landau on 2011-11-22
> **Jacobonbuntu said:**
> - Grsync
- Gnome schedule
I had not seen those before. I've just looked at them in Ubuntu Software Centre. They look good.

---

### Post by Jacobonbuntu on 2011-11-22
> **Paddy Landau said:**
> I had not seen those before. I've just  looked at them in Ubuntu Software Centre. They look good.
I agree, and the nice thing is that you can actually *see* what is the rsync and crontab output of your choices, and edit it if you want, unlike the more "soft" backup programs with only GUI and no "back-end view".

---

### Post by NautiusMaximus on 2011-11-23
When I was choosing a Linux distro, I read somewhere a piece of advice that went something along the lines of "Ubuntu is a good choice because it has a very active and helpful user community, so it is easy to get help on the forums if you need it".

Well, they weren't wrong!

Guys, thanks so much for your help here, I really appreciate it. Paddy, a big thank you to you in particular for your very detailed explanation of how cron jobs work. That cleared up a lot of my misunderstandings.

So, I set this up as a cron job under my own account, using Gnome schedule to help me do that (thanks Jacobonbuntu!), and I'm delighted to say that it worked. The backup ran at the scheduled time, and produced the desired results.

Now, although I have a solution that seems to work for me, I'm still slightly puzzled about one thing. If this was a permissions issue, then why did it not work when I was running the cron job via the root crontab, but worked when I ran it under my own one? Shouldn't permissions problems usually be less likely when running something as root? Or perhaps it wasn't a permissions issue? Not that I need to answer these questions for my backup to work, but I'd still like to understand why it didn't work as root to satisfy my curiosity.

Anyway, thanks again for taking the time to help me solve my problem!

NM

---

### Post by Paddy Landau on 2011-11-23
> **NautiusMaximus said:**
> ... it is easy to get help on the forums if you need it
Whatever the moderators have been doing, they have been doing well, because this forum is almost entirely free of flaming and other nasty habits. It is a pleasure to be involved here.

> **NautiusMaximus said:**
> If this was a permissions issue, then why did it not work when I was running the cron job via the root crontab...
I don't think you were running it. As far as I can tell from your description, you did not set up your cron table in the correct way, which means cron did not register what you had done. I could be wrong, but that's in the past now.

---

### Post by Jacobonbuntu on 2011-11-23
> **Paddy Landau said:**
> Whatever the moderators have been doing, they have been doing well, because this forum is almost entirely free of flaming and other nasty habits. It is a pleasure to be involved here. 

Couldn't agree more!
Glad it worked...

---

### Post by Paddy Landau on 2011-11-23
Oh, yes, now that you have solved the problem, please [mark this thread as solved]("https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads"). It will help others who have the same question.

---

### Post by NautiusMaximus on 2011-11-24
I hesitated a bit to mark the thread as solved, first because I wanted to make sure it worked more than once and wasn't a fluke (it's now worked again, so I feel more secure there) and second because I think that what I've done is more of a workaround (albeit a perfectly satisfactory one) than a solution.

Since the machine I'm backing up here is a single-user desktop, running the cron job as myself is perfectly reasonable, but there must surely be other circumstances when it would be appropriate to schedule backups as the root user. I'd still like to understand why it didn't work when I did.

But I think you're right that the thread is nonetheless likely to be more useful to others if marked as [solved], so I shall do just that.

---

### Post by Paddy Landau on 2011-11-24
> **NautiusMaximus said:**
> ... I think that what I've done is more of a workaround ... than a solution.
Um, I don't think so. You used gnome-schedule, a GUI front-end to crontab, which is exactly the correct way to do it.

> **NautiusMaximus said:**
> ... there must surely be other circumstances when it would be appropriate to schedule backups as the root user.
Indeed, yes, there would be such circumstances. In such a case, you would change root's cron (instead of your own) -- not by editing the file directly, of course, but by using either of the two following commands:
```
**sudo** [COLOR=Red]VISUAL=gedit[/COLOR] crontab -e     # *[FONT=Verdana]The standard way.[/FONT]*
**gksudo** gnome-schedule            # *[FONT=Verdana]Using the program that Jacobonbuntu suggested.[/FONT]*
```The difference is the use of *sudo*. Note that for GUI programs, you must not use *sudo* but instead *gksudo*.

> **NautiusMaximus said:**
> I'd still like to understand why it didn't work when I did.
As I said, you had not changed your cron tables in the correct way, so it is quite possible that cron was unaware of any changes. I don't know how cron works in the background, so that's a bit of a guess.

Whenever you do things the wrong way, there is always the chance of either unintended side-effects or, as in this case, no effects at all!

---

### Post by Azdour on 2011-11-24
Hi,

I know that I am jumping in after quite a few posts and I see it has been marked as solved, but my understanding is that if you place a script in /etc/cron.daily it will be run by anacron - from [https://help.ubuntu.com/community/CronHowto](https://help.ubuntu.com/community/CronHowto)

> For example, anacron offers simple system-wide directories for running commands hourly, daily, weekly, and monthly. Scripts to be executed in said times can be placed in /etc/cron.hourly/, /etc/cron.daily/, /etc/cron.weekly/, and /etc/cron.monthly/. All scripts in each directory are run as root, and a specific order to running the scripts can be specified by prefixing the scripts' filenames with numbers

If its run as root I cannot see why it would be a permission issue. If I understand the OP it should have worked. I guess if you want to debug to find out more you could output the EUID variable in the script to a log file. That way you'll find out who is running it, e.g. 0 = root.

---

### Post by Paddy Landau on 2011-11-24
Thank you for the information, Azdour.

(Incidentally, your link had an error. Here is the correct [CronHowto link]("https://help.ubuntu.com/community/CronHowto").)

According to the anacron manual, you change /etc/anacrontab to add jobs to anacron.

You can, however, use your own anacron file with the -t option.

In summary, my understanding is:

[LIST=1]
[*]Change /etc/anacrontab (or your own file if you need to run under your own name).
[*]Test the file with the -T option.
```
anacron -T                 # Test /etc/anacrontab
anacron -Tt ~/anacrontab   # Test ~/anacrontab
```
[*]Run anacron.
```
**sudo** anacron               # Run jobs from /etc/anacrontab
anacron -t ~/anacrontab    # Run jobs from ~/anacrontab
```**EDIT:** You are unlikely to use the first (i.e. with sudo), as root runs anacron automatically.
[/LIST]
Additionally, from [another manual]("https://help.ubuntu.com/community/AutoWeeklyUpdateHowTo") (though it's a year old), anacron does not look in /etc/cron.d, but it does start automatically when the computer is booted.

So, it seems to me (but I've never used anacron so I could be wrong) that you do not manually change files in /etc, other than /etc/anacrontab (if you are an administrator).

However, your suggestion for anacron is a good one. If NautiusMaximus's computer may be turned off when he wants the backup to be run, anacron is an excellent alternative.

---

### Post by Azdour on 2011-11-24
Hi,

On my Ubuntu 10.04 I have also found /etc/cron.daily etc... in the file /etc/crontab.

If you look at the file it just seems to detect the presence of /etc/anacron and uses run-parts to run each scripts it finds.

So I believe cron will run those scripts instead of anacron. You should not have to do anything other than drop your script into the appropriate daily, weekly or monthly directory just like the OP did. That's why I find it strange that it did not work - or did not work as intended.

BTW thanks for pointing out the link error :)

---

### Post by Paddy Landau on 2011-11-24
> **Azdour said:**
> You should not have to do anything other than drop your script into the appropriate daily, weekly or monthly directory...
Looking again carefully at the specifications for cron and crontab, I believe that you are correct as far as anacron goes.

What, then, is the mystery behind why NautiusMaximus got strange results? Truth is, I don't know. But he has solved the problem for now, and you have given some valuable extra information.

---

### Post by NautiusMaximus on 2011-11-25
> **Azdour said:**
> You should not have to do anything other than drop your script into the appropriate daily, weekly or monthly directory just like the OP did. That's why I find it strange that it did not work - or did not work as intended.


Yes, that's exactly what I did. I didn't touch the root crontab at any stage. So I'm also puzzled about why it didn't work.

Anyway, no matter. It works now, which is the main thing, and I have also learned much about crontabs from this thread, so all in all a good outcome.

---

### Post by Paddy Landau on 2011-11-25
> **Azdour said:**
> You should not have to do anything other than drop your script into the appropriate daily, weekly or monthly directory...> **NautiusMaximus said:**
> Yes, that's exactly what I did...
I have one more idea.

Do it again, but this time ensure that you have set execute permission on the files. I understand that you need to reboot and wait: 5 minutes for daily jobs, 10 for weekly and 15 for monthly.

I have, however, just tested it and it did not work.

---

### Post by NautiusMaximus on 2011-11-26
I had set execute permission on the files (you mean the script that I put into the cron.daily folder, right?) right from the start, so that's not it.

---

### Post by EricDP on 2011-12-13
> **NautiusMaximus said:**
> I have a file /etc/crontab, the contents of which look like this:

```

25 6    * * *    root    test -x /usr/sbin/anacron || ( cd / && run-parts --report /etc/cron.daily )

```

Unless I'm mistaken, the "||" in that line (which means "OR") will result in nothing happening if it detects anacron is executable. It will only proceed to "run-parts" if anacron is not found or is not executable. This doesn't make sense to me. Shouldn't it be a "&&" so that it will "run-parts" if anacron is found and is executable? It looks like the system-wide crontab is broken.

---

### Post by Paddy Landau on 2011-12-13
> **EricDP said:**
> Unless I'm mistaken, the "||" in that line (which means "OR") will result in nothing happening if it detects anacron is executable. It will only proceed to "run-parts" if anacron is not found or is not executable. This doesn't make sense to me. Shouldn't it be a "&&" so that it will "run-parts" if anacron is found and is executable? It looks like the system-wide crontab is broken.
I believe it is correct as it stands. I understand it as follows. If Anacron exists, Anacron will do what it has to do. If it does not exist, then Cron will run the various parts in order to emulate Anacron.

---

### Post by Azdour on 2011-12-13
Hi,

I think Eric maybe onto something. The test -x does not run anacron, it just detects if it is present and is executable. The || means that if test returns false then run the command 'cd / && run-parts --report /etc/cron.daily'

On my computer /usr/sbin/anacron exists and is executable so anything after the || never runs and therefore it could be the cause of the cron job not running.

---

### Post by NautiusMaximus on 2011-12-13
My problem was never that the job didn't run. It ran at the expected time, but it just did unwanted things when it ran.

---

### Post by EricDP on 2011-12-13
> **Paddy Landau said:**
> I believe it is correct as it stands. I understand it as follows. If Anacron exists, Anacron will do what it has to do. If it does not exist, then Cron will run the various parts in order to emulate Anacron.

Ah, yes... and there is also an /etc/anacrontab which takes care of the daily, weekly, and monthly jobs... I never knew about this file. 

And my problem running the scripts in /etc.cron.daily is that /usr/sbin/anacron exists (so run-parts never runs), but anacron is also not running (so the daily jobs in /etc/anacrontab never run).

Is this also the problem for the original poster?

Next thing is to figure out why anacron is not running...

---

### Post by Dave_L on 2011-12-13
> **EricDP said:**
> Ah, yes... and there is also an /etc/anacrontab which takes care of the daily, weekly, and monthly jobs... I never knew about this file.

anacron also uses the directory /var/spool/anacron/ to keep track of when its jobs last ran:

> $ ll -h /var/spool/anacron/
total 20K
drwxr-xr-x 2 root root 4.0K 2010-08-04 14:56 ./
drwxr-xr-x 7 root root 4.0K 2010-04-29 07:28 ../
-rw------- 1 root root    9 2011-12-13 04:29 cron.daily
-rw------- 1 root root    9 2011-11-27 04:37 cron.monthly
-rw------- 1 root root    9 2011-12-08 05:12 cron.weekly

The files in that directory contain the last-run dates in the format YYYYMMDD:

> $ sudo cat /var/spool/anacron/cron.daily
20111213

---

### Post by EricDP on 2011-12-13
Oddly, my /var/spool/anacron/cron.daily contains "20111213" (implying that anacron ran very recently) but the jobs did not run today. :(

Or maybe they did run:

```

/var/log/syslog.1:Dec 13 07:30:01 metis CRON[7447]: (root) CMD (start -q anacron || :)
/var/log/syslog.1:Dec 13 07:30:01 metis anacron[7450]: Anacron 2.3 started on 2011-12-13
/var/log/syslog.1:Dec 13 07:30:01 metis anacron[7450]: Will run job `cron.daily' in 5 min.
/var/log/syslog.1:Dec 13 07:30:01 metis anacron[7450]: Jobs will be executed sequentially
/var/log/syslog.1:Dec 13 07:35:01 metis anacron[7450]: Job `cron.daily' started
/var/log/syslog.1:Dec 13 07:35:01 metis anacron[7464]: Updated timestamp for job `cron.daily' to 2011-12-13
/var/log/syslog:Dec 13 07:53:29 metis anacron[7450]: Job `cron.daily' terminated (mailing output)
/var/log/syslog:Dec 13 07:53:30 metis anacron[7450]: Normal exit (1 job run)

```

And the logs rotated so something clearly happened. Now I need to figure out why certain jobs in /etc/cron.daily are not running.

---

