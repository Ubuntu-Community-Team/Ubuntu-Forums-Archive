---
title: "TMP folder not cleaning up"
date: 2011-05-29
forum: General Help
---

### Post by jonnan on 2011-05-29
After figuring out that this is happening  on my brand new 10.04 install, I've suddenly realized it explained what was happening on the 9.10 install I'm replacing.

I'm finding out on the internet that /tmp in Ubuntu is typically a Ramdisk, thus cleared automatically on reboot - but that's not how I was ever taught to setup a linux box; I *always* create /home var et al and mount them separately, including /tmp.

So on my new 10.04 install I am informed my tmp partition is down to 12 Meg, and find K9Copy crashed last night (I initially thought this was due to a crash, but testing shows it just - leaves them there. Thanks K9Copy!) leaving a 4.5 Gig file sitting in tmp. I add a couple Gig to the tmp partition (LVM rocks btw.) and reboot. Files are still there. 

I finally went in via gksu nautilus and manually deleted the data. 

More research find this results in exactly the kind of issues I was having previously in my 9.10 install (albeit without the helpful warning that helped me figure it out) of Firefox and various other programs acting glitchy because they right to tmp and it's full.

I'm a n00b, and really don't know how to fix this - the 'proper' way to clean tmp seems to involve [dropping entirely out of X to userlevel 0 and running from the commandline]("http://ubuntuforums.org/showthread.php?t=499248")?!?! . . /tmp is supposed to be for temporary files; ideally a program should clean up after itself, but it's actually Ubuntu's job to clean this.

My going in and manually cleaning out files is insane if gksu nautilus is involved, nevermind if that's the *wrong* way. I'm certainly not the guy to write a cronjob to clean this. On the other hand - this only started in the last week or so (on 9.10) so it has to be a recent change.

Thanks - Jonnan

---

### Post by fooman on 2011-05-29
don't know if this will help,  or if you have tried it already....but "bleachbit" is a fine tool for cleaning things up.  it can be run as a regular user or as admin. and has many options to choose,  including the cleaning of your tmp files.

bleachbit is available in the repos using synaptic or the ubuntu software center.

---

