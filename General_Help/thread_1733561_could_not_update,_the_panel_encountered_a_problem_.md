---
title: "could not update, the panel encountered a problem while loading, firefox is already r"
date: 2011-04-19
forum: General Help
---

### Post by dl456 on 2011-04-19
I'm running ubuntu 10.04 and I get several weird pop up windows when I first boot up.  I have tried getting help from the community forums and have tried several of the recommendations but they haven't helped.  In fact, I think some of the things that I have done have made my computer worse.  The first window I started getting said "Could not update ICEauthority file/home/dpan/.ICEauthority"  (dpan is my user name).  If I would click on the close button it would close.  Before that when I was saving a bunch of sound files to my home folder, I got a message that my root drive was almost full which was weird considering I wasn't saving anything to my root drive.  When I check how much of my root partition is used with "GParted" (under system>administration) along with using the "df -H" command in the command line it shows that I have only used about 4.5GB and have about 7GB of unused space on my root partition. Although, when I use the "Disk Usage Analyzer" (under Applications>Accessories) it shows that my whole root partition is full.  

When I searched for ways to fix the "could not update" window, some of the forums talked about removing some of the keyring codes.  So I did that, but it seemed that that caused later problems.  I stated to get two windows on top op each other that were identical that said "The panel encountered a problem while loading 'OAFIID:_IndicatorApplet'   Do you want to delete the applet from your configuration?".  In the same window, there is a box that says "don't delete" and a box that says "delete".  I should mention that I think there were two keyring codes that I deleted and there are two identical pop up windows.  I have tried clicking both the delete and the don't delete boxes several times but I get the same thing every time.  

Shortly thereafter, I also lost my ability to get on the internet with Firefox and Chromium. When I tried to get on with Chromium, it would start to load but then it would stop and nothing would happen.  When I tried to get on with Firefox, a window would pop up that said "Close Firefox...... Firefox is already running, but is not responding.  To open a new window, you must first close the existing Firefox process, or restart your system.".  It also had a clickable box in the window that said "OK".  I didn't have Firefox already running and Firefox wouldn't let me on the internet.  For awhile, I was able to use the browser "Epiphany" to get on the internet but after a week, Epiphany wouldn't even let me on the internet and it did the exact same thing that Chromium did when I clicked on it (started to load but then stopped and did nothing).  When Epiphany did allow me to use the internet it wouldn't let me view PDF's or save pictures that were attachments on my emails.

Currently, I am using the partition of my hard drive that has windows xp installed on it.   

Thanks for any help

---

### Post by hwttdz on 2011-04-19
Addressing the keyring and ofaid whatever error.  There are a couple of ways to go.  The easiest (though possibly most annoying) is thus:
move all your configuration files to a directory other than ~, this will totally reset your profile to the default.  You'll get a keyring message first time you try to connect that asks you to set a keyring password, use the empty string (i.e. just click through) it will say something about "unsafe storage" say this is ok.  The ofaid applet thing is a bug, you might get it again, you might not, if you do hit delete it should be lost and gone forever.  
To do this run:

cd ~
mkdir configs
find . -xdev -maxdepth 1 -name "\.*"|\grep -Ev "^\.$"|xargs mv -t configs

then logout and then log back in.  Any of your config files will be in the configs directory, so say you want your firefox config back, just go into configs, do "ls -A" and find something about firefox, and then move it back to ~. 

Addressing the firefox is already running, can you post output of "top -u `whoami` -b -n 1|\grep firefox".

That should at least be a start.

---

### Post by dl456 on 2011-04-20
Thanks for the reply hwttdz,

I did what you said in the best way that I understand.  I am assuming that putting 

cd ~
mkdir configs
find . -xdev -maxdepth 1 -name "\.*"|\grep -Ev "^\.$"|xargs mv -t configs

in the command line (each line at a time) is how I move all of my configuration files to a directory other than ~.  Is that correct?  What is ~?  When I put in cd ~, it prompted me to the next command line.  When I put in "mkdir configs" in the next command line it posted, "mkdir: cannot create directory `configs' : Permission denied".  Do I have to replace any of the words in these commands with any specific names of my personal files (i.e.  alot of times people will put "user" which is supposed to be the name that they assigned to their home folder)?



Regarding  the "Firefox already running issue",  when I put 

top -u `whoami` -b -n 1|\grep firefox

in the command line, nothing happens and it just prompts me to a new empty command line.

Thanks for any help.

---

### Post by dl456 on 2011-04-20
I forgot to mention that for some reason today I was able to get on the internet with Ubuntu 10.04 using my Epiphany web browser even though it hasn't worked in the past.

---

