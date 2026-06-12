---
title: "File dates across machines"
date: 2012-03-30
forum: General Help
---

### Post by Cool Javelin on 2012-03-30
I am having some issues with file times.

I have an Ubuntu (10.10) desktop and an Ubuntu (10.10) server (no graphical interface,) both with some shared directories.

I also have 3 Windows XP machines with the following:
#1 XP Pro SP2
#2 XP Home SP2
#3 XP Home SP3

5 machines in all.

All the dates (and times) on all 5 computers are similar. (some are off by a minute or 2.)

The issue: When I make and save a file (using any of the 5 machines) to either Ubuntu server, the time of the file is off by an hour.

An example:
If I create a file on a Windows machine at 3:02 PM and save it on any Windows machine the file time shows as 3:02 PM (as expected.)

If I save the file to any Ubuntu it shows as 2:02 PM (an hour off.) This happens even if I create a file on the Ubuntu machine and save it on the Ubuntu machine. (I haven't tried to save it from Ubuntu to Windows yet.)

Yet,... If I COPY the file either way, the time of the file seems to be preserved properly.

Another symptom (may be unrelated,) On 2 of the XP machines with SP2, if I use the "synchronize time with the internet," it tries to set the time incorrectly. IE it tries to set the time to an hour earlier then it should. I have disabled that feature on those 2 XP machines. The third (XP w/SP3) is OK with the internet sync. Also, on at least one Ubuntu, I do have it sync the clock with the internet time and it seems to be OK too.

This is a problem as I have a batch file that checks the time of the file and copies the file from one machine to the other depending on which is newer. If I edit a file for less then an hour, it tries to overwrite the newer file with the older.

I have verified the timezone settings on at least one Ubuntu machine and all 3 Windows machines. I live in Custer WA. (now Pacific Daylight time GMT -8 hours.)

Is this a problem with Samba? or an issue with Ubuntu? or can someone think of something else?

Has anyone run across this before?

Thanks,
Mark.

---

### Post by llamabr on 2012-03-30
How did you verify the timezone settings?

[http://manpages.ubuntu.com/manpages/dapper/man8/tzconfig.8.html](http://manpages.ubuntu.com/manpages/dapper/man8/tzconfig.8.html)

---

### Post by qneill on 2012-03-30
Can you elaborate on where you're seeing the time in each case?  I can see a 4-way chart at least, and maybe one will shed more light:
```
                Create File
              Server | Client
View  Server     x       x
File  Client     x       x
```

Where you are "seeing" the time stamp may also have a problem.

---

### Post by Cool Javelin on 2012-03-31
llamabr

I went to the page you suggested and tried the tzconfig. My version of Ubuntu said:

```
:~$ tzconfig
WARNING: the tzconfig command is deprecated, please use:
 dpkg-reconfigure tzdata
```

I did that, and it here are the results.

```
Current default time zone: 'America/Los_Angeles'
Local time is now:      Fri Mar 30 23:34:41 PDT 2012.
Universal Time is now:  Sat Mar 31 06:34:41 UTC 2012.
```

That looks correct (I think) Pacific Daylight savings Time (PDT) is seven hours.


qneill:

It looks like I may have made a mistake or 2 in the original report.

After thinking about what you said, I realized there are 6 permutations for making, saving, and viewing the file.

Use Ubuntu or XP to make a file.
Save the file on XP or Ubuntu.
Use Windows Explorer or Nautilus to look at the time,

I finally made an excel sheet to keep it all straight, The results are attached in a PDF and I think the link is at the bottom of this post.

I know Ubuntu sets the system computer time to GMT and converts everything as needed. I am not sure if Samba uses operating system calls to do that or if it does it itself. That would only be half the problem as Samba is a file server, not the client.

I think Windows, on the other hand, sets the system clock to the local time and changes the clock twice a year. I know there is some kind of bug as to when windows changes the time (damn government changing the dates for that, and damn government for making daylights saving time in the first place, but that is another argument.)

Anyway, I am at a loss as to how to fix this particular problem.

Thanks, Mark.

---

### Post by Cool Javelin on 2012-03-31
The more I think about it, the more I bet this problem will go away by itself tomorrow, only to come back at the end of daylight savings time when we switch back to standard time.

In 2007, the government changed daylight savings time from the first Sunday in April (tomorrow,) to the second Sunday in March (3 weeks earlier.)

I bet there is some issue involving this change and I will rerun the 6 permutations tomorrow.

Mark.

---

### Post by Cool Javelin on 2012-04-02
Sho'nuf, today, Apr 2 '12, all file dates agree with each other no matter from where I create the file and no matter to which machine I save them. (I didn't go through the exercise of using Nautilus to look at the files, but using Windows Explorer reveals the times are OK.)

So, the symptom has gone away (as predicted,) and I expect it to return in the fall.

Again, my guess is it will only manifest itself during the 2 or 3 weeks between the old Daylight Savings Time / Standard Time and the new. (pre / post 2007)

It might be related to a missing update in one of the operating systems.

I generally turn off the automatic updates as I have had my share of problems coming to work in the morning and having to deal with a buggy update for several hours.

I can locate the comprehensive list of updates on the M'soft site, is there a similar list for Ubuntu?

I will get back to this issue in the fall when the problem appears again.

Mark.

---

### Post by dcstar on 2012-04-03
Ubuntu timezone updates occur on a regular basis to keep up with the various changes around the world. If you decide not to keep your systems updated then issues like this arise - end of story.

---

### Post by Cool Javelin on 2012-04-03
dcstar:

Not so much end of story, the clock reads the correct time, and changed at the proper moment 3 weeks ago, so I must have had the proper updates in place for that to happen.

Mark.

---

