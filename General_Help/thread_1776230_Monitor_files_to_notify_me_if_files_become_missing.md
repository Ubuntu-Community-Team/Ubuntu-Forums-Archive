---
title: "Monitor files to notify me if files become missing or corrupt?"
date: 2011-06-05
forum: General Help
---

### Post by dorlow on 2011-06-05
Ok, as time goes on and I'm getting more and more pictures and videos on my hard drive, the possibility of loosing something dear to me is increasing everyday.  I have years worth of pictures and videos on my hard drive that I never want to loose.  I have a backup system going.  I have a 2 TB HD.  I have a script setup to run tar commands to backup my pictures folder, videos folders, documents folders, etc.  I have a weekly backup and then daily incrementals.  I manually rename a full backup once a month to monthly backup.  I am keeping a one year backup and then I keep a few most recent full backups and incrementals.  I then have two 500 GB very small hard drives that I copied my yearly backups and one or two most recent full backups on both of those and every week or two I recopy the one at the house and take it to work and bring the one from work home and in a week or so recopy that one with recent full backups just in case something destroys my PC via fire or some bad electrical surge.  Something is offsite and always semi-recent.

I think I have most of my bases covered, but the problem I am still running into is how do I know when something subtle is missing?  We also were keeping our pictures online hosted with myphotoalbum.com.  They are going out of business, so they sent out an e-mail to make sure you have all your pictures backed up.  I'm thinking to myself, I got my bases covered... no biggy.  Then I thought, I better check.  

I scanned the picture albums on myphotoalbum and compared them to my pictures folder and found about 6 months of pictures missing from about 3 years ago.  I keep my pictures well organized in date format to the folders (yyyy-mm-dd <title>).  So I can usually tell if there's a lot o pictures missing.

But as time goes on and I'm holding 5 years and 200+ GB of pictures and videos and it's only going to keep increasing, the possibility of loosing some of those over time is increasing.  And the biggest problem I have is not noticing that they're missing until my backups are all overwritten and I don't have a way to restore it.  I might not notice pictures from 6 months are missing until 6 months later, which means I probably overwrote my yearly backup.  

I guess what I'm looking for is something that constantly keeps an index of everything on my hard drive (or I can set the folders for it to monitor) and then notify me if there is anything in those folders that comes up missing.  Really there's no reason for a picture ever to be deleted... so one file modification shouldn't happen other than additions.

Maybe there's an ubuntu command or program that's already available that I'm not aware of?  

I was thinking of just writing a script that would do an ls on the directories and then pipe that out to a text file and then do it again every month or so and then use the diff command to tell me what's different... but that sounds like a pain.  I'd probably have to output the data to a file and then I'd have to look through a whole bunch of boring text files every week and I'd probably wouldn't keep it up.

I guess it probably wouldn't be that bad to do it that way because I guess the file ouput I have to read should only have additions... but when I dump off a ton of new pictures onto my hard drive, there will be a ton of additions to the file I'd have to look through, unless I found a way to filter out additions and only have file removals make it into the diff output, which I'msure I could get the grep command to strip off the additions and only show the removals.. but dang it... it's making by brain hurt just thinking about this.

I did take a unix shell scripting class in college... but I would rather not think too much and just have something do this for me.

I need a program that will just do it in the background for me and just alert me when something is wrong.

---

### Post by dorlow on 2011-07-10
Ok, I finally sat here and tried to figure it out.  This is what I have so far...

ls -R > $(date +%y%m%d)_$(date +%H%M%S)_pics_ls.txt

diff --suppress-common-lines 2011-07-101542picsls.txt ls.txt

ls -R > $(date +%y%m%d)_$(date +%H%M%S)_videos_ls.txt

diff --suppress-common-lines 2011-07-101542videosls.txt ls.txt

Right now I'm just going to run these commands manually every few weeks or so to see if anything is missing.  Overtime, I'm sure I'll find ways to perfect it a little and maybe automate it or script it.

---

### Post by Habitual on 2011-07-10
"Maybe there's an ubuntu command or program that's already available that I'm not aware of?"

[http://www.ibm.com/developerworks/linux/library/l-inotify/index.html](http://www.ibm.com/developerworks/linux/library/l-inotify/index.html)

---

