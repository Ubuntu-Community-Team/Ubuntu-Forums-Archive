---
title: "Unison - File Synchronization - profile help."
date: 2010-05-10
forum: General Help
---

### Post by alienprdkt on 2010-05-10
Is there a way with Unison to setup to sync more then one root path? 

and more then one source path?

Wanted to set something up like this...

Mount smb shares to local server:
/mymounts/server001/source
/mymounts/server002/source

then I would like to sync those mounted directories to something like this:

sync to directories:
/syncs/server001/source
/syncs/server002/source

can this be done?

can you please explain how I would configure this?
Thanks in advance
__________________

---

### Post by alienprdkt on 2010-05-11
Can anyone help me out with this?

Anyone here use Unison?

Let me explain why, I know I could just sync /mymounts/ and that would work but...

/syncs/server001/source 
&
/syncs/server002/source

are two different hard drives. I would really like to avoid creating a RAID 0 and merging the two disks to have the space to sync my network mounts. 





Any help would be appreciated. Thanks in advance.

---

### Post by 8Kuula on 2010-05-11
Im not so experienced about unison program but lets see...

I think you can't sync multiple locations with multiple locations with one command. So sollution would be create script that executes multiple unison commands.

like:
unison -batch /mymounts/server001/source /syncs/server001/source
unison -batch /mymounts/server002/source /syncs/server002/source

Or maybe I did not get what you wanted to do? :]

---

### Post by alienprdkt on 2010-05-11
> **8Kuula said:**
> Im not so experienced about unison program but lets see...

I think you can't sync multiple locations with multiple locations with one command. So sollution would be create script that executes multiple unison commands.

like:
unison -batch /mymounts/server001/source /syncs/server001/source
unison -batch /mymounts/server002/source /syncs/server002/source

Or maybe I did not get what you wanted to do? :]

No thats what I would like to do ... 

I have seen some articles on the web but not much info... 

Nothing really on the unison home page.

But after several hours searching (before I posted here)I seen here:

[http://www.pubbs.net/201001/debian/76302-synchronizing-more-than-one-folderfile-in-unison-per-profile.html]("http://www.pubbs.net/201001/debian/76302-synchronizing-more-than-one-folderfile-in-unison-per-profile.html")

that I could change the profile to look something like this:

root= /mymounts/server001/source
root= /mymounts/server002/source

path= /syncs/server001/source
path= /syncs/server002/source

Want to know if this works before installing and uninstalling yet another backup utility.. I have tried so far more then 1/2 dozen apps. Would really like to know if it will do what I would like before hand.

Thanks for your reply...

---

### Post by 8Kuula on 2010-05-11
That profile consept with unison is out of my experience.

<thinking out loud>
So you want to sync directory /syncs/server001/source with /syncs/server002/source
So: /syncs/server001/source <-> /syncs/server002/source

and these?
/mymounts/server001/source
/mymounts/server002/source
</thinking out loud>

Sorry, for im not getting what you trying to do. :(

If you doing changes only on other directory I would suggest to use rsync. Like for backuping data.
But if you make changes to both directories then unison is better, I think. Like syncing data with laptop.

PS.
And that -batch switch makes unison not to ask any questions, for first run lose it from command so you can see what it does.

---

### Post by alienprdkt on 2010-05-11
> **8Kuula said:**
> Im not so experienced about unison program but lets see...

I think you can't sync multiple locations with multiple locations with one command. So sollution would be create script that executes multiple unison commands.

like:
unison -batch /mymounts/server001/source /syncs/server001/source
unison -batch /mymounts/server002/source /syncs/server002/source

Or maybe I did not get what you wanted to do? :]

Thanks I think I know what you are saying correct me if I am wrong but I should be able to make multiple profiles, and then start them from the command line like this:

name them as:

server001.prf
server002.prf

write a script

#!/bin/sh
unison -server001

save as unison-server001.sh

give it executable permissions
chmod +x unison-server001.sh

#!/bin/sh
unison -server002

save as unison-server002.sh

give it executable permissions
chmod +x unison-server001.sh unison-server002.sh


load them into cron with crontab for every 30mins

crontab -e
* /30 * * *  unison-server001.sh

* /30 * * *  unison-server002.sh

this should work to keep them synced every 30 mins, correct?

Thank you for helping me out.
:)

For further reading:

Unison Manual (complete) [http://www.cis.upenn.edu/~bcpierce/unison/download/releases/stable/unison-2.32.52-manual.pdf]("http://www.cis.upenn.edu/~bcpierce/unison/download/releases/stable/unison-2.32.52-manual.pdf")
[http://stackoverflow.com/questions/584770/how-would-i-get-a-cron-job-to-run-every-30-minutes]("http://stackoverflow.com/questions/584770/how-would-i-get-a-cron-job-to-run-every-30-minutes")

---

### Post by 8Kuula on 2010-05-11
I have only used unison to sync locations "A" and "B" both ways, with direct command.

Profile versus direct command(s).
Your link ( [http://www.pubbs.net/201001/debian/76302-synchronizing-more-than-one-folderfile-in-unison-per-profile.html](http://www.pubbs.net/201001/debian/76302-synchronizing-more-than-one-folderfile-in-unison-per-profile.html) ) suggests that you could put multiple locations. For example "A" with "B" and "C" with "D" to same profile and run that with one unison command (unison profilename). Never used profiles with unison, so can't help on that, sorry. That manual may help on that I see you found.
That way you would not need to do script. And crontab would only need one command.

If you make two profiles, where is point to make those profiles in first place? That goes down to direct command(s) in script again, script to crontab so one command there again.

I asume you sync more than one set of locations. So then puting them to script and runing script from crontab. This I would do since I do not know how to put many location sets to single profile :)

unison-sync.sh file:
```

#! /bin/sh

unison -batch dirA dirB
unison -batch dirC dirD

```

and in crontab:
```

* /30 * * * unison-sync.sh

```

From manual quick read, in profiles you can put more sync options like exceptions and sutch, so if you use those too, I think profile would be more easier to maintain.

Ooh solved... *Puf* :D

---

### Post by alienprdkt on 2010-05-11
well the reason why I have 2 commands and 2 cron jobs was to have both of them run at the same time not one after the other.

But yes I believe that both would work.

I have also found that Unison doesn't sync in real-time. 

I will keep looking for something that will sync in real-time, and if I can not find anything then I will use Unison with these options discussed here.

I would rather have something that synchronize in real-time then every 30mins from a cronjob. But will resort to it if I can't find any other way. 

Thanks for your help.

---

