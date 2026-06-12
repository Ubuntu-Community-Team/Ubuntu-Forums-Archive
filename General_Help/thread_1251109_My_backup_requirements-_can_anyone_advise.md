---
title: "My backup requirements- can anyone advise?"
date: 2009-08-27
forum: General Help
---

### Post by Donalb on 2009-08-27
Hi people,

I've been trying a few different backup apps with no success and I've gotten lazy about this since I moved to Ubuntu full time last year. I've also done a lot of google & forums searching with no luck.
No networking requirement.

My requirements are;

1: GUI (don't want command line for this)
2: Incremental backup (once the initial backup is done I only want changed files saved)
3: Must be able to backup to UDF file format (used for CD/DVD format, in my case I'm using a Iomega Rev HDD 70gb which also uses UDF)
4: Must be able to backup 2 folders at same level ( I want to backup /documents & /desktop but nothing else from the /home folder. If not able to do two top level folders must have exclusion ability so I achieve the same result from /home)
5: Must be smart enough to know when the destination drive isn't present (and not then fill up my root folder like Simple Backup does)
6: Granular scheduling
7: File level backup (don't want a compressed archive if I need to find/restore 1 file) 

I've tried:
Keep (no longer maintained) and couldn't do the above anyway
Gsync (pretty basic, couldn't do the 2 folder thing)
Simple Backup (filled my /root directory when no ext hdd present)
Testing Unison now (not sure yet)- Ok Unison is out, doesn't allow multiple folders. 

Appreciate any thoughts.

Regards

---

### Post by chriskin on 2009-08-27
have you tried back in time?

---

### Post by Donalb on 2009-08-27
Thanks. 
Just installed BiT for a look. GUI is ok, but on scheduling it's very basic. You can specify every day, week, month but not for example 5 days a week or specific days & time, like Wed at 4am.
Also notice there's no "abort" when you setup something wrong and no control from the applet. I had to kill the process to stop it when I wanted to change a setting. 
 BiT does allow folder choice with inclusion/exclusion as I require, but doesn't specify any provisions when the target folder isn't present. I tried starting it with the destination drive out and it's just sitting there, and I'd no idea what it was doing. The applet sat open with nothing showing in the Process Monitor . So all in all BiT is out also, looks like a very early development app.

---

