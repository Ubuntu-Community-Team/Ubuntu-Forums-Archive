---
title: "Sbackup not working"
date: 2010-05-11
forum: General Help
---

### Post by OnlyTim on 2010-05-11
Hey all, I upgraded to 10.04. Was using deja dup, but found it would not back up anymore. I tried using sbackup and it seems to take all the configuration, but when I choose back up now, it shows the process ID but sits idle. The destination drive shows no new files.

Any help would be appreciated. Thanks!

---

### Post by R Smit on 2010-05-12
Same problem here on laptop and desktop; did not find yet a usefull alternative.

Apparently known bug:

[http://sourceforge.net/tracker/index.php?func=detail&aid=2996590&group_id=145360&atid=761640](http://sourceforge.net/tracker/index.php?func=detail&aid=2996590&group_id=145360&atid=761640)

---

### Post by OnlyTim on 2010-05-12
Thanks for the information! Glad to see it's a bug and not me.. I guess it involves daja dup back up as well. I'll wait and see what they come up with as a fix.

Thanks again!

---

### Post by 98cwitr on 2010-05-12
i had the same problem. Im willing to bet you can run it from terminal though and it'll work.

---

### Post by OnlyTim on 2010-05-12
Would you know the command for sbackup in terminal? I may try that.
In the mean time,, I unloaded sbackup and installed NSsbackup from synaptic. It worked! Don't ask me how? The files are backed up as tar files. At least I can use it until a fix comes out.

---

### Post by 98cwitr on 2010-05-12
sudo sbackupd

further commands and restore commands can be found here:
[http://www.linuxcertif.com/man/8/sbackupd/en/](http://www.linuxcertif.com/man/8/sbackupd/en/)
[https://help.ubuntu.com/community/BackupYourSystem/SimpleBackupSuite](https://help.ubuntu.com/community/BackupYourSystem/SimpleBackupSuite)

---

### Post by OnlyTim on 2010-05-12
Thanks 98.. Appreciate the help!

---

### Post by recluce on 2010-06-18
I should start out by stating that I did not find this solution, but merely tried what somebody else suggested on SourceForge. So here we go:

There is a bug in a configuration file of Simple Backup Config, were a function call is missing a parameter, causing the process you start with the "Backup Now" Button to immediately go Zombie.

Here is the how to fix, step by step:

```

sudo gedit /usr/share/sbackup/simple-backup-config.py

```

Find the following function: def on_backupnow_clicked(self, *args):

Once you find it, edit the next line, which looks like this:

 pid = os.spawnl( os.P_NOWAIT, self.conf.get("places", "prefix") + "/sbin/sbackupd" ) 

edit to look like the code box below:

```

 pid = os.spawnl( os.P_NOWAIT, self.conf.get("places", "prefix") + "/sbin/sbackupd", "/dev/null" )

```

Don't forget to save.. 

You are now back in business, the "Backup Now" button will work again.

---

### Post by unperson on 2010-06-19
recluce: Thanks so much for posting this.  Your fix worked like a charm.  I don't know anything about that function, but I'm guessing from looking at the output of ps that that last argument tells it what to do with STDERR?  In any case, you're a life saver.

It sounds like this problem has been present for a while.  If the fix is so simple, I really don't understand why the package hasn't been updated.

---

### Post by recluce on 2010-06-19
> **unperson said:**
> recluce: Thanks so much for posting this.  Your fix worked like a charm.  I don't know anything about that function, but I'm guessing from looking at the output of ps that that last argument tells it what to do with STDERR?  In any case, you're a life saver.

It sounds like this problem has been present for a while.  If the fix is so simple, I really don't understand why the package hasn't been updated.

Thanks... :-D

I can read that function call a little bit, so I am guessing somewhat here. Seems to me that this simply defines the action to take when somebody clicks the button "Backup Now". It goes ahead ahead and spawns a process in the simple backup daemon. The daemon seems to expect an output device for error reports and such and assumes that a console is available. However, there is none and the process goes Zombie since there is no error handling for this situation. Adding the /dev/null parameter gives it a valid output device and it happily directs its text output to nirwana.

I also cannot understand why such a simple error doesn't get fixed posthaste.

---

### Post by sderrick on 2010-07-06
If I make the change that Recluse recommends. 

The SBackup Config app wont' start!

Scott

---

### Post by recluce on 2010-07-06
> **sderrick said:**
> If I make the change that Recluse recommends. 

The SBackup Config app wont' start!



From what you describe, it seems very likely that you broke something in the file you edited - which would cause a problem like the one you described. 

Check back that you made the changes **exactly** as in my example, including every space and quotation mark. Also, you do not want to change formatting on this file. Double check that everything is correct.

Otherwise: any error messages?

---

### Post by Sparky51 on 2010-07-17
Thanks Recluce, your fix worked fine for me also. :D

---

### Post by o1e9 on 2010-07-20
@recluce:  Thanks ! It works now.

---

### Post by aritafari on 2010-07-27
I spent endless hours (to no avail) trying to fix and find another easy to use backup utility.

recluce, Thank you very much for the suggested fix. It worked

ari tafari

---

### Post by creepa1982 on 2010-07-30
Thanks a lot. Simple fix!

---

### Post by helgeklemm on 2010-08-04
Hi,

fist of all, thanks for this fix. But:

I guess this is not fixing the same problem for timed backups?
I set my config file to backup every night, but haven't produced a singel backup by doing so... 
Any ideas on that?

Cheers

Helge

---

### Post by paxmark1 on 2010-08-07
Enjoy it while you can.  From something that had a lot of work put into it over two Google summers of codes - now no activity.

aptitude search back     yields no sbackup in Debian testing.  

Squeeze froze.  Enjoy it while you can. (Where does Ubuntu get its .deb?} Sbackup started acting in 9.10, and it appears that no one is working on keeping it up.  Pity.  I miss pysol too.

---

### Post by alexvb on 2010-08-08
Thanks for this solution. Have been scratching my head for a while. Indeed why is not this problem solved in the meantime????

---

### Post by Bearly Able on 2010-08-10
Thank you, Recluce.  I can sleep again at nights now! :)

---

### Post by Bearly Able on 2010-09-19
Well, it was working perfectly until about three weeks ago, since when I've been unable to get it to back up anything.  I went to try Recluce's solution again, in case an update had rewritten the config file.  However, I found the line following ```
def on_backupnow_clicked(self, *args)
``` now reads ```
pid = subprocess.Popen([self.conf.get("places", "prefix") + "/sbin/sbackupd"]).pid
```and not ```
pid = os.spawnl( os.P_NOWAIT, self.conf.get("places", "prefix") + "/sbin/sbackupd" )
```as in Recluse's example.

As I don't understand the code, I don't want to start guessing at it in case I make matters worse.

I'd really appreciate help in fixing this.  Thank you.

---

### Post by recluce on 2010-09-19
I checked and found out that one of the more recent updates completely changed the way how sbackup calls the sbackup daemon to perform the actual backup.

[SIZE="3"]So the solution I gave to the problem existing in the original release of Lucid is no longer applicable - and the problem is resolved by an update.[/SIZE]

@Lesley Lutomski: since we have no details for your problem, I can only give a bit of general advice. Since sbackup works for me and I haven't seen other complaints lately, the first thing to do would be to purge and reinstall sbackup and sbackupd. (In Synaptic choose "completely remove" and install again after that).

---

### Post by Bearly Able on 2010-09-19
Thanks again, recluce, that seems to have worked.  It has at least completed a manual backup; hopefully the automatic backups will be OK now.

---

