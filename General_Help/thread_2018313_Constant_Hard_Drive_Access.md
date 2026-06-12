---
title: "Constant Hard Drive Access"
date: 2012-07-06
forum: General Help
---

### Post by SgtT on 2012-07-06
My apologies if this has been asked before, but I was unable to find an answer. Every few seconds I see my HD light on and it seems like the HD is being accessed every 3 to 4 seconds.

Any clue what may be the culprit? Has anyone else run into this issue?

Thanks,

T.

---

### Post by steeldriver on 2012-07-06
I've run into something like that when a process is writing the same error message to a log file over and over but really without more info all you're going to get is wild guesses

- is this a new install, or is it an old system that suddenly started doing this?

- what type of system (laptop? desktop? server? do you have RAID?)

- have you installed any new applications / packages recently?

Look in /var/log/dmesg and /var/log/syslog to see if there's anything that jumps out - you could install and run 'iotop' as well

---

### Post by chocklet on 2012-07-06
Your question has been asked for years, across a wide sampling of Linux releases.  In fact, over the years with other distros, unexpected activity has been common.  Once upon a time when I tried to figure out what was going on, when I was using other distros (not Ubuntu), the answers appeared to be...

- the light was blinking but the writes were not actually happening
- file system journalizing
- continual desktop environment maintenance, including HAL
- logging

The unexpected disk activity on my 12.04 Unity OS is much less than yours.  If I let my PC just sit for a minute, with the only desktop applications open being gedit and GKrellM, then the gap between writes is often over 25 seconds, which is not an issue at all.  However, my /tmp is in RAM, which may have an impact on monitoring software that is looking at writes to hardware drives.  (Unusual Note: I'm seeing a rough and inconsistent correlation between typing in gedit and increased boot drive activity... maybe a coincidence)

Three tools you might look at are 

- GKrellM 
reports no detail by process
configure to show each drive separately.

- pidstat 
part of the sysstat package
does not require admin privileges 
appears to ignore very small bits of activity
example: pidstat -d 5 30

- iotop (already suggested by steeldriver)
requires sudo
sometimes does not list processes that have very small bits of activity
example: sudo iotop -o -a

On my own 12.04 Unity, journalizing continues occasionally even when no application appears to be requiring disk activity, which conforms to my recollection of what happened with some other distros.

I don't see HAL (searched system monitor and htop).  My old notes (about another distro) were that the activity could be reduced on my PC with the following command: hal-disable-polling.  If, in 12.04 Unity, some other software performs the same function as HAL did, then that software may be responsible for some of the activity.

Sometimes GKrellM shows boot drive activity that is not shown by pidstat or iotop.  Sometimes neither lists very small writes shown by GKrellM.  Sometimes iotop -o indicates activity momentarily (a number will flash for a moment above the output column titles) but does not list the activity below in the detail itemization by process.  The amount of data that is not being reported is very small.  Tiny.  There may be a way to configure these programs to show all activity, but I'm not too concerned about such small activity.  Besides, some of the inconsistent reporting may be related to the fact that /tmp in my system is in RAM and not on a physical drive.

As usual for me, gaining knowledge with a comfortable level of certainty takes more effort and time than I have available.  Hope that you fare better!  People here should be able to assist you if you provide more info about your system, as suggested by steeldriver.  Good Luck.

---

### Post by SgtT on 2012-07-06
Thank you both for your posts.

I'm still having no luck, even at idle the the HD is constanly being accessed. I see the HD light on every 3 to 4 seconds.

I read that adding noatime to fstab would help. When I run iotop I constanly see jbd2 process running off and on. Can anyone advise me on how to turn off Jbd2 or how to edit fstab to add noatime?

I'm a noob so I don't understand fstab.

Thanks,

T.

---

### Post by chocklet on 2012-07-07
I'm hoping that steeldriver or someone else with solid technical expertise will help you.

In the meantime you should *backup your fstab*.  Open up a terminal, enter "gksudo nautilus", navigate to /etc, and copy fstab.

I do not have your problem.  I have had the problem in the past with multiple distros. Currently I have 3 installs of 12.04 Unity, on two significantly different hardware architectures, and none of them write every 3 or 4 seconds.  All, if left alone for a minute, settle down to write less than once every 25 seconds.  None are servers.

None of my installs are noatime.  You can come to a conclusion here as easily as I can... using noatime may simply mask your real problem.

Trying to make sense of my previous research about drive activity makes my head spin.  However, because you seem to be jumping to some decision very quickly, I will recommend that you consider two opinions before proceeding:

"Summary: leave the settings as they are, they were chosen for a reason."
[http://askubuntu.com/questions/2099/is-it-worth-to-tune-ext4-with-noatime](http://askubuntu.com/questions/2099/is-it-worth-to-tune-ext4-with-noatime)

"Your disk will be more vulnerable for data corruption on uncontrolled shut-downs without journaling."
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/607560](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/607560)

There are lots of opinions about noatime and journaling.  Opposing opinions might both contain truth.  The person who simplifies, like I have done by posting only the two quotes above, is leaving out important conflicting factors. These are not trivial things and require serious research if you begin to think that distro developers have made a mistake.

I decided NOT to use noatime myself on my daily OS, even though I have an SSD than thus would theoretically be motivated to do so.  However, against my own best judgment, and assuming that your system is similar to mine, here is how to put noatime in your fstab...

Open a terminal and enter "gksudo nautilus"
navigate to /etc and open fstab in gedit
find the line that contains "errors=remount-ro 0 1" (there should be only one such line)
add noatime to that line so that it looks like this...

```
UUID=19adba01-1ff5-4fcd-a084-999999999 /   ext4    noatime,errors=remount-ro 0 1

```Your UUID will be different.
If there is more than one line with "errors=remount-ro 0 1", then disregard my instructions and wait for someone with expertise to help.

Without knowing anything about your PC, here is something that you might try first if you have 2GB or more RAM:  Put /tmp in RAM.  This suggestion is based upon two assumptions...
- that Unity/gnome uses /tmp as part of its ongoing internal mechanics.
- your system won't be fooled to the result that your disk activity light continues to flash even though writes are not actually happening.
The purpose of putting /tmp in RAM is to see what happens to writes to your boot drive.  If writes to the boot drive diminish, then we might be able to more easily determine exactly what is causing the activity.  After the cause is identified, then the ramdisk can be abandoned by eliminating the entry from fstab.

Here is the fstab entry to put /tmp in RAM...

```
#
# added by me to run /tmp from RAM
none /tmp tmpfs noexec,nosuid,size=20%,mode=1777 0 0
```Have you determined the total volume of daily activity (writes) that journaling has cost you?  Actually, the most relevant number might be the volume of activity while your PC is just sitting doing nothing.  You should be able to extrapolate from a sample using iotop -o -a.

steeldriver has recommended that you provide more information.  How about starting with
- your computer model, CPU, RAM
- the uses of your PC (configured for remote access?)
- the results of uname -a

steeldriver or somebody, please jump in here and let SgtT know what info would help.

---

### Post by steeldriver on 2012-07-07
I'm really no expert - but I doubt there's anything wrong with your fstab / noatime, based on my limited experience when you see lots of jbd2 activity that's more likely a symptom than a cause (i.e. something *else* is doing periodic small writes and *that* is forcing journaling) - I went down that rabbit hole myself 

FWIW here's a little one-liner to find the top 10 most recurring messages in each of the three log files /var/log/dmesg, /var/log/syslog, and /var/log/kern.log (the sedery is just to strip the timestamps - otherwise every line is different and we can't count recurrences)

```
for log in /var/log/{dmesg,syslog,kern.log}; do echo "${log} :" ; sed -e 's/\[[^]]\+\]//' -e 's/.*[0-9]\{2\}:[0-9]\{2\}:[0-9]\{2\}//' ${log} | sort | uniq -c | sort -hr | head -10; done
```See if that throws up anything

---

### Post by chocklet on 2012-07-08
steeldriver -  Thanks for the very cool one-liner :)  I've stashed it on my Linux cheat-sheet and will surely put it to good use.

---

### Post by steeldriver on 2012-07-08
^^^ you're welcome, it's NOT  thoroughly tested though, you may find you need to tweak it (especially the sed expressions - I'm not really sure how to match the timestamps reliably)

---

