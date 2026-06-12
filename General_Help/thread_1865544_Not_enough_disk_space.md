---
title: "Not enough disk space"
date: 2011-10-20
forum: General Help
---

### Post by Ghostlove on 2011-10-20
Since upgrading to 11.10 (via the Live CD) I am having trouble with Thunderbird. When I try to download new messages I get an error "There is not enough disc space to download new messages. Try deleting old mail, emptying the Deleted folder, and compacting your mail folders, and then try again.". I have done this but I'm still getting the error.

My HD was full, so I moved a good eighty gigs of stuff to an external HD, but that hasn't solved the problem either.

Any help would be gratefully received!

---

### Post by mikejonesey on 2011-10-20
post
```
df -h
```

---

### Post by Ghostlove on 2011-10-20
```
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda2             241G  229G     0 100% /
udev                  1.4G  4.0K  1.4G   1% /dev
tmpfs                 540M  892K  539M   1% /run
none                  5.0M     0  5.0M   0% /run/lock
none                  1.4G  1.4M  1.4G   1% /run/shm
/dev/sdf1             280G  106G  175G  38% /media/External___
/dev/sdg1             1.9T  588G  1.3T  32% /media/WD External___
/dev/sda3              53G   34G   19G  65% /media/Windows_
df: `/root/.gvfs': Permission denied
```

---

### Post by drs305 on 2011-10-20
The returns show your / partition is full.

You can use this guide on finding the reason your partition is now full. (Hint: normally it is unemptied trash bins, large log files, or backups made to / instead of a backup partition).

[HOWTO: Recover Lost Disk Space]("http://ubuntuforums.org/showthread.php?t=1122670")

---

### Post by Ghostlove on 2011-10-20
Thank you, I will use that guide. :)

---

### Post by Ghostlove on 2011-10-20
Okay, I started to use it, but have run into a problem.

```
sudo du -h --max-depth=1 /
``` shows me that my home/anji folder is 223GB. ```
sudo du -h --max-depth=1 /home/anji
``` shows a list of the contained folders and their sizes, which does not add up to anywhere near 223GB, it's more like 60-70GB. So where's the rest come from? I've already emptied the trash folder. :/

---

### Post by drs305 on 2011-10-20
> **Ghostlove said:**
> Okay, I started to use it, but have run into a problem.

```
sudo du -h --max-depth=1 /
``` shows me that my home/anji folder is 223GB. ```
sudo du -h --max-depth=1 /home/anji
``` shows a list of the contained folders and their sizes, which does not add up to anywhere near 223GB, it's more like 60-70GB. So where's the rest come from? I've already emptied the trash folder. :/

So let's try a few commands to search your entire / partition. First, you should unmount all your other devices so we can concentrate on what is physically on the / partition. For instance, if you have a USB external device mounted on /media/xxxx, it should be unmounted. Otherwise, you won't really see what may be *underneath* /media/xxx until the external device is removed/unmounted.

Close out all running apps and unmount any external devices and other partitions.

See if these commands find anything.
```
sudo umount -a # unmount all 'non-busy' devices in fstab. 
du -h  --max-depth=3 ~/.local/share/Trash # Check your trash.
sudo du -h  --max-depth=3 /root/.local/share/Trash # Check root trash.
sudo find / -name '*' -size +500M  # Look for large files.

```

Also run this command to find out exactly where on you /home folder the extra space is being consumed. Again, unmount everything first.
```
sudo du -h --max-depth=3 /home/anji | sort
```

---

### Post by tartalo on 2011-10-20
```
sudo du -h --max-depth=1 /home/anji
```
is showing to you how much disk space take the **subfolders** under /home/anji, the missing bytes are in the files stored directly in your home, try this:
```
ls -lah /home/anji
```

Edit: added a to the ls options to see the hidden files too

---

### Post by Ghostlove on 2011-10-20
I would love to try that but now my Ubuntu partition will not boot at all. I can work in my (very small) Windows partition just fine, but the Ubuntu partition gets stuck on the purple screen with the white/red loading dots and does nothing.

I'm in a Live CD right now, and looking at 'MainPC' (my Ubuntu partition), it says I have 163.3GB of free space.

---

### Post by drs305 on 2011-10-20
> **Ghostlove said:**
> I would love to try that but now my Ubuntu partition will not boot at all. I can work in my (very small) Windows partition just fine, but the Ubuntu partition gets stuck on the purple screen with the white/red loading dots and does nothing.

I'm in a Live CD right now, and looking at 'MainPC' (my Ubuntu partition), it says I have 163.3GB of free space.

Your system may not be booting because there is no space.

Mount the Ubuntu partition (substitute your Ubuntu drive/partition)

```
sudo mount /dev/sdXY /mnt
```
Example: sudo mount /dev/sda5 /mnt

Open a file browser as root:
```
gksu nautilus /mnt/var/cache/apt/archives
```
You'll need to delete some files. Use SHIFT-DEL so the space is freed.

I've used a command which will open the APT archives folder. You can safely delete any .deb files contained therein. Do not delete the 'partial' folder.

If there are no .deb files there, go to your home folder and find some files which you do not need (.bak files, for instance, or files in your /mnt/home/anji/Downloads folder). You could also delete files in /mnt/tmp.  You don't need to delete many files - just a MB or two will be more than enough.

---

### Post by Ghostlove on 2011-10-20
```
du -h  --max-depth=3 ~/.local/share/Trash
``` shows 32MB usage.
```
sudo du -h  --max-depth=3 /root/.local/share/Trash
``` gives me the message "du: cannot access `/root/.local/share/Trash': No such file or directory".
```
sudo find / -name '*' -size +500M
```
gave me nothing but a list of 14 .mkv files I was downloading; I have deleted them for now and emptied the trash.
```
sudo du -h --max-depth=3 /home/anji | sort
```
gave me a *huge* list (I'm quite folder-happy). The biggest ones are:
1.1G	/home/anji/.thunderbird
1.1G	/home/anji/.thunderbird/gi885p62.default
1.4G	/home/anji/.cache/spotify
1.4G	/home/anji/.cache/spotify/Storage
1.5G	/home/anji/.cache
250M	/home/anji/.thumbnails
3.2G	/home/anji
998M	/home/anji/.thunderbird/gi885p62.default/Mail

I don't think that adds up to anywhere near 223GB...

```
ls -lah /home/anji
```
gives me a huge list of stuff, but at the top of the list it says "total 728K".

Now I've deleted a bunch of stuff I'm going to try Thunderbird again I think. Though it says my Thunderbird folder is about 1G - could that be the problem? Is there a limit to how much Thunderbird can store?

---

### Post by Ghostlove on 2011-10-20
Aha! Now df -h gives me:```
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda2             241G   21G  208G  10% /
udev                  1.4G  4.0K  1.4G   1% /dev
tmpfs                 540M  868K  539M   1% /run
none                  1.4G  656K  1.4G   1% /run/shm
```That looks more like it, doesn't it! Off to try TB now. ;)

---

### Post by Ghostlove on 2011-10-20
Nope, now Thunderbird is telling me "Unable to write the email to the mailbox. Make sure the file system allows you write privileges, and you have enough disc space to copy the mailbox.". Also, when I try to view certain folders within Thunderbird, it just doesn't show me anything and the mouse has that little... spinny thing... next to it for ages.

It was working yesterday and I know everyone says this but I honestly *haven't* changed anything since then as far as I know!

---

### Post by drs305 on 2011-10-20
It looks like you have solved your space issues. 

Since you can't access it and you also can't see them, it sounds like they may now be owned by root. 

If you know where your Thunderbird files are located, check the ownership with:

```
sudo ls -la /*path to Thunderbird files*
```

---

### Post by Ghostlove on 2011-10-20
And if I don't know where my Thunderbird files are located, how do I find that out? I've never had to do anything with them before so I have no idea! :P

---

### Post by Ghostlove on 2011-10-20
Ah, think I found them:```
total 24
drwxrwx---  4 anji anji 4096 2011-05-02 14:16 .
drwxr-xr-x 59 anji anji 4096 2011-10-20 22:01 ..
-rw-r--r--  1 anji anji  335 2011-04-05 15:40 appreg
drwx------  2 anji anji 4096 2011-10-17 22:29 Crash Reports
drwx------  8 anji anji 4096 2011-10-20 23:08 gi885p62.default
-rw-r--r--  1 anji anji   94 2011-04-05 15:40 profiles.ini
```

I'm not sure what any of that means, actually. I'm um, a good user of Ubuntu but I haven't really delved into the technical stuff enough.

---

### Post by drs305 on 2011-10-20
I'm not a Thunderbird expert, but could you try starting thunderbird with a new profile to see if it is a problem with your current profile or something more system-wide?
```

thunderbird -P
```
Choose 'Create Profile, Next, enter a new name and click Finish. See if it runs. I may not be able to tell you what to do next, but if it runs we know that the problem is in one of your old account's files.

---

### Post by Ghostlove on 2011-10-20
Yes, it opened in a new profile, I entered my email address/password and it downloaded the newest messages.

---

### Post by tartalo on 2011-10-20
Since you had huge discrepancies between what df and du+ls reported I suggest that you check your file system with fsck

```
fsck /dev/sda2
```

EDIT: From an Live CD

---

### Post by tartalo on 2011-10-20
Oh, I might be confusing things: [http://www.cyberciti.biz/tips/freebsd-why-command-df-and-du-reports-different-output.html](http://www.cyberciti.biz/tips/freebsd-why-command-df-and-du-reports-different-output.html)

---

### Post by mikejonesey on 2011-10-21
cool you got this sorted, ubuntu does have a computer janitor, does that tool report anything?

think is uner either system>pref or system>admin

(has a gnu broom icon)

---

### Post by Ghostlove on 2011-10-22
It's not sorted yet. Thunderbird is working fine in the new profile, but the old one is still all silly - won't download new messages, won't let me view folder contents.

---

### Post by CitizenUnderdog on 2011-10-22
I have the same issue, I think. 

```
jake@manamana:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1              73G   68G  544M 100% /
udev                  680M  4.0K  680M   1% /dev
tmpfs                 276M  772K  275M   1% /run
none                  5.0M     0  5.0M   0% /run/lock
none                  688M  460K  688M   1% /run/shm

```

But when I run the Disk Usage Analyzer or du command, I can't find any files or folders that are even over 4GB. 

Any suggestions on how to troubleshoot this?

---

### Post by CitizenUnderdog on 2011-10-22
I think I found my issue...

There was a directory under /media that was owned by root instead of my usual user. As a result is wasn't showing up using the Disk Usage Analyzer program.

I found it using the du command. I was confused because I thought it was reporting on my unmounted USB external hard drive. But it looks like one of my backup programs was writing to that directory when my USB HDD was not attached... and as root?

The name of the backup application is CrashPlan if anyone else sees the same issue.

---

### Post by drs305 on 2011-10-22
> **CitizenUnderdog said:**
> I think I found my issue...

... But it looks like one of my backup programs was writing to that directory when my USB HDD was not attached... and as root?

The name of the backup application is CrashPlan if anyone else sees the same issue.

That happens frequently - at least with forum members with disk space problems. Another popular app causing this is *sbackup* - though it's not the app's fault.



@ Ghostlove,

I'm not a Thunderbird wizard, but one thing you could try would be to add the old Tbird mail accounts to your currently-working one.

The first thing to do would be to make a copy of the complete *.default profile folder. It is probably in ~/.thunderbird. Make a copy and then you can 'experiment' with the good folder. You could try renaming the 'Mail' subfolder to something like MailX and then copy your 'bad' profile's Mail folder into the new one. Then open Tbird and see what folders you have and if it works.

Be careful though, as you have a working copy now with at least some new mail. If copying a folder doesn't work or breaks Tbird, delete the bad folder and rename the older one to the original. If all else fails, delete the entire *.default folder and restore the backup copy.

There are probably guides on the Net that will tell you what specific folders contain your Mailboxes, etc. I hope you can get everything restored.

---

### Post by mikejonesey on 2011-10-22
i would ask you to tar gz the files and upload for inspeition... obviously thats not posible in this case (your emails lol)... hmm can you tar gz any non confidential files... i'll take a look at the thunderbird conf files tomoz, see if i can identify where any probs could be...

in the mean time, du and cat your thunderbird conf files... see if you notice anything abnormal...

posibily diff the two configs...

---

### Post by Ghostlove on 2011-10-23
I think I have solved this problem, though not how I'd have liked to. I made a new profile in Thunderbird and re-downloaded all my mail. So far it seems to be all right.

---

### Post by Ghostlove on 2011-10-24
Right, I'm in the new profile. It's stopped downloading my email again. "There is not enough disc space to download new messages. Try deleting old mail, emptying the Deleted folder, and compacting your mail folders, and then try again."

Doing df -h tells me once again that I am using 100% of my hard drive. This is simply not possible; I haven't downloaded anything since the last time I checked!

---

### Post by Ghostlove on 2011-10-24
Okay, so I found a file (.xsession-errors) which was over 200GB (?!) and deleted it, rebooted, no problem with it as far as I can tell, it's just created a new file which is only a few KB.

Thunderbird is still not working.

I used the Disk Usage Analyser and I'm not sure if I'm reading the results correctly; it seems to think my /home folder is full even though it has only 4.5GB in it?

---

### Post by drs305 on 2011-10-24
> **Ghostlove said:**
> Okay, so I found a file (.xsession-errors) which was over 200GB (?!) and deleted it, rebooted, no problem with it as far as I can tell, it's just created a new file which is only a few KB.

Thunderbird is still not working.

I used the Disk Usage Analyser and I'm not sure if I'm reading the results correctly; it seems to think my /home folder is full even though it has only 4.5GB in it?

No, DUA is sometimes not that intuitive. What it shows is that your /home (anji) is 100% of /home, but not 100% of your partition. Likewise, pop.googlemail.com is 96% of the Mail folder. Each shows the percentage of the parent folder.

One suggestion when running DUA - always unmount any external drives/partitions if possible. It makes the totals more accurate since you are usually only interested in one partition's results. Otherwise the extra partitions are included in /media, /mnt or wherever they are mounted.

---

### Post by Ghostlove on 2011-10-24
Thanks drs305. I *think* I have now finally solved my Thunderbird problem. I uninstalled and then reinstalled Thunderbird itself. It seems to be downloading my email with no issue now. I'll give it a couple of days and then if it's still working I'll mark this thread as solved. Thanks so much for all your help!

---

### Post by Ghostlove on 2011-10-28
Aaaand I'm back to the same error messages again. .xsession-errors was 234GB again. What is this file, why is it growing so large so quickly, and how do I stop it doing that?

---

### Post by drs305 on 2011-10-28
You can open the file and inspect what recurring error messages you are getting, The file should be located in you home folder.

If you see one error continuously repeated you could try to troubleshoot the problem. Posting it would allow forumites to help you.

The other option would be to modify the script generating the error so that it either recreates the file from scratch each time X is started, or modify the script so the errors aren't logged in ~/.xsession-errors.

If possible you should solve the problem causing the errors, but as a normal user if you don't particularly care about the file you can modify the error reporting - i.e. how many normal users really CARE about xsession errors as long as the computer works.

Anyway, here are two links that describe how to modify reporting these errors if you aren't able to fix the problem directly. I've looked at my /etc/X11/Xsession file and the lines refer to are lines 61 and 83 (in my Oneiric setup).
[http://debian-user.blogspot.com/2007/05/problem.html]("http://debian-user.blogspot.com/2007/05/problem.html")
[http://blog.dhampir.no/content/moving-or-removing-xsession-errors]("http://blog.dhampir.no/content/moving-or-removing-xsession-errors")

There are lots of links, just do a search for ".xsession-errors"

---

### Post by Ghostlove on 2011-10-30
There are lots of different errors showing up, but ```
** (process:2958): WARNING **: recent-manager-provider.vala:125: Desktop file for Banshee was not found
``` seems to appear more than most. Which is odd as I don't actually have Banshee open...

ETA: ```
(nautilus:2674): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed
```
is popping up a lot as well.

ETA2: Oh, and loads of these: ```
Window manager warning: Window 0x2800112 () sets an MWM hint indicating it isn't resizable, but sets min size 369 x 46 and max size 369 x 47; this doesn't make much sense.
Window manager warning: Window 0x28000d7 () sets an MWM hint indicating it isn't resizable, but sets min size 369 x 161 and max size 369 x 162; this doesn't make much sense.
```

I am literally sitting here watching the size of .xsession-errors go up at a couple of kb ever second, doesn't seem like much but I can see how it fills my hard drive so quickly!

---

### Post by drs305 on 2011-10-30
I get some of the same errors and they have been reported as bugs.

If I was in your situation, I would use the second link in my last post by editing /etc/X11/Xsession to 
1) delete the file at first X startup
> ERRFILE=$HOME/.xsession-errors
rm -f "$ERRFILE"
2) If the file is still growing too large in one session:
> ERRFILE=/dev/null
This will write the 'errors' to the nowhere.

After accomplishing either 1 or 2, I'd forget about it unless you have unexplained system problems, at which point I'd reverse the changes.

It's not a perfect solution but one that will probably work without the need for extensive troubleshooting.

---

### Post by okusi on 2011-11-03
> **Ghostlove said:**
> Nope, now Thunderbird is telling me "Unable to write the email to the mailbox. Make sure the file system allows you write privileges, and you have enough disc space to copy the mailbox.". Also, when I try to view certain folders within Thunderbird, it just doesn't show me anything and the mouse has that little... spinny thing... next to it for ages.

It was working yesterday and I know everyone says this but I honestly *haven't* changed anything since then as far as I know!

i'm having the same problems.  Thunderbird crashing with all sorts of errors, including the above.  i have a lot of accounts and folders. is this perhaps causing new versions of thunderbird to have problems?

---

### Post by drs305 on 2011-11-03
> **okusi said:**
> i'm having the same problems.  Thunderbird crashing with all sorts of errors, including the above.  i have a lot of accounts and folders. is this perhaps causing new versions of thunderbird to have problems?

Your issue may be the same or it could be slightly different. To avoid confusion, it would be best if you open your own thread. Include the exact error messages you receive if possible.

You can continue to watch this thread and try any solutions offered here to see if they apply to your situation, but having your own thread will allow you to get personalized attention.

---

