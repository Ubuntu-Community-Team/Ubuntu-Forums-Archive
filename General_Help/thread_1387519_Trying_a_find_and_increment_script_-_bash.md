---
title: "Trying a find and increment script - bash"
date: 2010-01-22
forum: General Help
---

### Post by buee on 2010-01-22
I tried searching for this, but everything, for pages and pages, shows me the `if -e filename`.  That's not what I'm looking for, at least I don't think I am.

I am working on a script that will search a directory for certain file names and increment a variable by one for each result returned. Each time I search this file name, the file found will also be deleted. I would like this script to be run about every 6 hours or so. We'll call this script A.

I also have a script that runs daily that I would like to tack the count to the end of the text file that it outputs. We'll call this script B. I'm confident that I would want to store the count from script A to a text file to be called in by script B, but don't know how to do so.

Here's what I have so far:

```
#!/bin/bash
SD=0	#Resetting variable count for testing purposes, removed this before release
#Below, Smith is used for testing purposes as this is the newest backup with instances found
find /cust_backups/Smith -name *Modified\ Script* && SD=$[SD+1] ;
find /cust_backups/Smith -name *Bitdefender\ Online\ Scanner* && SD=$[SD+1] ;
find /cust_backups/Smith -name *ccleaner.exe* && SD=$[SD+1] ;
find /cust_backups/Smith -name *HJT.exe* && SD=$[SD+1] ;
find /cust_backups/Smith -name *KillBox.exe* && SD=$[SD+1] ;
find /cust_backups/Smith -name *MBAM.exe* && SD=$[SD+1] ;
find /cust_backups/Smith -name *MSE\ V32.exe* && SD=$[SD+1] ;
find /cust_backups/Smith -name *MSE\ V64.exe* && SD=$[SD+1] ;
find /cust_backups/Smith -name *MSE\ XP.exe* && SD=$[SD+1] ;
find /cust_backups/Smith -name *SAS.exe* && SD=$[SD+1] ;
find /cust_backups/Smith -name *spybotsd.exe* && SD=$[SD+1] ;
find /cust_backups/Smith -name *spybotsd_includes.exe* && SD=$[SD+1] ;
find /cust_backups/Smith -name *Utility\ Batch* && SD=$[SD+1] ;
find /cust_backups/Smith -name *Windows\ Update* && SD=$[SD+1] ;
echo "$SD"
```

A couple of things here, the 2nd line variable, that's just for testing purposes. In the end result, I will not have the variable reset each time the script runs. It will be a year to date count if you will. Also, the echo at the end is for testing purposes. I abbreviated the search scope to one folder under /cust_backups but in the end, it will search the entire folder of /cust_backups for the file names in question.

Now, for those of you that know what you're doing, you're already shaking your head because you know that, no matter what, at the end of the script $SD will end up being 14. The problem is I don't know how to tell bash that if there is a result returned, increment by one. If there is no result returned, move to the next command.

Beyond that, I'll need to know how to call the text of a file in to a variable so I can plug it in to the text output of script B.

Any tips?

---

### Post by DaithiF on 2010-01-23
I would do something like this:
```
IFS=''
while read pattern
do
        for matchingfile in $(find . -maxdepth 1 -iname "$pattern")
        do
        SD=$(($SD+1))
        echo "$matchingfile, about to delete it..."
        rm -f $matchingfile
        done
done < patterns
echo "SD now $SD"
```

where patterns is a file containing the list of wildcard entries you want to match against, e.g.:
```
*Modified Script*
*Bitdefender Online Scanner*
*ccleaner.exe*
*HJT.exe*
*KillBox.exe*
*MBAM.exe*
*MSE V32.exe*
*MSE V64.exe*
*MSE XP.exe*
*SAS.exe*
*spybotsd.exe*
*spybotsd_includes.exe*
*Utility Batch*
*Windows Update*
```
and note that no need to escape the spaces since we enclose the iname parameter to find within quotes

---

