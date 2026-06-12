---
title: "Cron job not running"
date: 2010-01-06
forum: General Help
---

### Post by bobonthenet on 2010-01-06
Can someone please tell me why my second cron job isn't running?  The first one runs fine but the second one does not run at all.  If I manually run the script using ./check.sh then it does what it is supposed to but will not run from cron.  It should run every weekday at 9:45am, it looks good to me but clearly I am doing something wrong.

```

# m h  dom mon dow   command
#This will backup my hosted websites.
0 2 * * * /home/bob/scripts/websitebakscript.sh

#This will run check and upload it's contents to the net.
45 9 * * 1,2,3,4,5 /home/bob/scripts/check.sh

```

---

### Post by DaithiF on 2010-01-06
cron entry looks ok to me.  i'd guess the script *is* being launched by cron, but is erroring out before doing anything useful.  Try capturing output into a logfile ... and see what turns up
45 9 * * 1,2,3,4,5 /home/bob/scripts/check.sh >> /home/bob/check.log 2>&1

---

### Post by bobonthenet on 2010-01-06
The script runs fine when I run it by itself.  Is there a function for cron that would tell it to ignore errors and or warnings?

I will start generating a log file also but I'm not confident that it would tell me anything.

---

### Post by bobonthenet on 2010-01-07
The second cron job did not run again this morning.  No log was generated.  I ran the script manually and it did what it was supposed to.  Any other ideas why this might be happening?

---

### Post by happyhamster on 2010-01-07
Perhaps the script needs some environment variable that's not available in cron's shell (cron runs in its own environment IIRC).

---

### Post by DaithiF on 2010-01-07
there are basically 2 possibilities here:
1. cron doesn't actually execute the job because of some problem with cron or the cron-entry for the job
2. cron does execute it, but the script fails.
 
1. seems unlikely to me because the cron entry as you have listed should work fine.  And it does indeed work for me.  Your other cron entry runs, so that shows that cron itself is working on your system.
2. although you can run the script fine manually, thats no guarantee that it will run successfully when being run by cron.  Cron will not run the job with the same environment as your user, so different PATHs, missing environment variables, etc. can all cause issues.  Adding logging to the cron job as I suggested in the previous post would normally capture error messages.  Getting no log output is strange, but could be explained if the script itself redirects/swallows stdout and stderr messages.
 
So my next suggestion to narrow down definitively between 1 and 2 would be to add at the top of your script something like:
echo "I am being run! $(date)" >> /home/bob/check.log
 
I would also suggest adding a new cron entry for 1 or 2 minutes from now while testing, so that you don't have to wait 24 hours between test runs! :)

---

### Post by bobonthenet on 2010-01-07
I can't make changes on my server until I get home but here is some more information which hopefully will shed light on things.  I didn't think it was relevant before because I figured the script was not running at all.  Since you believe it must be running this would be indeed important.  Here is the check.sh file.
```

#!/bin/sh

python check.py
cp check$(date +%Y%m%d).xml /var/www/mysite/check/.

```

I know the cp command works with cron because my website backup uses pretty much the exact same command.  Will python not run from cron?  If so how do I get it to run.  Now that I'm thinking about it I'm sure this must be the problem and I feel foolish for not considering it before.  The python script generates some output as a dated xml file it usually takes about 3 to 5 minutes to run.

---

### Post by DaithiF on 2010-01-07
```
python check.py
```
is check.py also in /home/bob/scripts?
if so, this is [one reason] why it isn't running.  the cron job will start with current directory set to your home directory, /home/bob.  So even though you are executing a shell script in scripts/, any relative paths in that script will still be relative to your home dir, not the script dir.  So basically python will be looking for a file check.py in your home dir,  and failing to find it.  

So either:
```
python scripts/check.py
```
or probably better...
```
python /home/bob/scripts/check.py

```

Just to note also, python should be spitting out an error message (can't find file 'check.py' ...), and if you added the logging to your cron job as per previous post that should have been captured in the log file.  So maybe theres something else going on here too.  In fact, while you're making changes, make the path to python explicit too, probably /usr/bin/python, but worth confirming on your system.

---

### Post by bobonthenet on 2010-01-07
I'll try this as soon as I get home.  Thanks.

---

### Post by bobonthenet on 2010-01-08
I have made all of the suggested changes and the cron job still does not appear to be running and I am not getting any error output.  This time though when I went to manually run the script it threw out some errors and my XML file came out bad as well.  I think I might have an idea why this is.  I believe that my data isn't all available at 9:45 yet and so the cron job is failing, when I go to run it at 10am the data is there and the script runs fine.  I will be investigating this further because I'm not sure.  What still bothers me though is that I am not getting errors when this is supposed to run from cron.  I did add the output as was suggested.

---

### Post by MooPi on 2010-01-08
Is your script running something in GUI. If so you will need to do as I have and indicate which screen to use. ```
env DISPLAY=:0
```

---

### Post by DaithiF on 2010-01-08
not capturing error output is indeed strange.  would you mind copy/pasting your cron entry here again please

---

### Post by bobonthenet on 2010-01-08
This is my entire crontab, as you can see I'm not doing a lot with cron yet.  I hope you spot something simple that I missed.  This is beginning to stress me out.  If I can determine that my cron IS running then I will actually just have it run more than once in the morning so that if my data is not there the first time then it'll just grab it later.

```

# m h  dom mon dow   command
#This will backup my hosted websites.
0 2 * * * /home/bob/scripts/websitebakscript.sh

#This will run check and upload it's contents to the net.
45 9 * * 1,2,3,4,5 /home/bob/scripts/check.sh >>/home/bob/check.log 2>&1

```

---

### Post by bobonthenet on 2010-01-08
OK after making my last post and re-reading it I see that I set the log to go into my home dir instead of the scripts dir.  Looks like cron is in fact running and python is throwing out some errors.  Thanks a lot for the help.  I think I may be able to take it from here.

---

### Post by lunatico on 2010-07-20
Hi!

I'm having a similar problem running a script from crontab.

It's a backup script that looks like:
```
#!/bin/bash
#Desktop
/usr/bin/rsync -r -t -v --progress --delete /home/dani/Desktop/ /usr/bin/ssh dani@dani-desktop:/home/dani/dani-backup/Desktop/;
```

I have done the suggestions in this thread to add logging and all that and the crontab job is running and the script is running but for some reason the command isn't and I don't get any errors.

Any ideas?

---

### Post by bobonthenet on 2010-07-20
I should have responded before now.  I actually fixed this ages ago using the suggestions above.  Thank you all and I am greatful for the help.  Anything run from cron must have the full directory paths explicitely stated.  If I remember correctly I also had to alter the scripts I was running so that the full path was included in those scripts.

---

### Post by lunatico on 2010-07-20
> **bobonthenet said:**
> I should have responded before now.  I actually fixed this ages ago using the suggestions above.  Thank you all and I am greatful for the help.  Anything run from cron must have the full directory paths explicitely stated.  If I remember correctly I also had to alter the scripts I was running so that the full path was included in those scripts.

Good that you got your fixed.
I do have full paths and all... and this vary same script was working fine before I upgraded from 9.10 to 10.04...

---

### Post by bobonthenet on 2010-07-20
> **lunatico said:**
> Good that you got your fixed.
I do have full paths and all... and this vary same script was working fine before I upgraded from 9.10 to 10.04...

I wish I could be of more help.  All I can say is what worked for me.  Obviously, something must have changed from 9.10 to 10.4, my thought is to try and find out what is different that would have an effect on your scripts.  That advice probably isn't that helpful but it's the best I've got.

---

### Post by lunatico on 2010-07-20
> **bobonthenet said:**
> I wish I could be of more help.  All I can say is what worked for me.  Obviously, something must have changed from 9.10 to 10.4, my thought is to try and find out what is different that would have an effect on your scripts.  That advice probably isn't that helpful but it's the best I've got.

Thanks! Hopefully someone else will have some other suggestions.

---

### Post by rubylaser on 2010-07-20
lunatico, short of dumping the rysnc results to a logfile I'm not sure why it would be failing.  I assume that you have keyless ssh setup on the remote host dani-desktop so that rsync can start without you needing to type your password in?

Also, have you made your script executable? 
```
chmod +x script_name.sh
```

Finally, I would probably revise that command since you're launching from cron, you don't really need progress stats.  Maybe something like this...
```
#!/bin/bash
/usr/bin/rsync -avz --delete /home/dani/Desktop/ dani@dani-desktop:/home/dani/dani-backup/Desktop/
```

Hope that helps.

---

### Post by lunatico on 2010-07-20
> **rubylaser said:**
> 
Hope that helps.

Thanks for your suggestions!
Yes the user has keyless ssh access to the desktop.
The script is executable
Tried you suggestion with '-avz --delete' for rsynch but still not running from crontab. If I run the script manually from terminal it works fine.

This is weird...

---

### Post by lunatico on 2010-07-20
Ok after reading a bit, specially post in [this thread]("http://ubuntuforums.org/showthread.php?t=874849") I was able to fix this. Basically the problem was that to create a keyless ssh connection it needs to find the ssh which is normally part of the user env, which for reason's I don't understand when running stuff from cron the environment is not the real user's environment... anyway... this is how I fixed it.

At login export the SSH_AUTH_SOCK to a file. Create an executable script that runs at startup and contains the following:

```
#!/bin/bash
sleep 5
touch $HOME/.Xdbus
chmod 600 $HOME/.Xdbus
env | grep SSH_AUTH_SOCK > $HOME/.Xdbus
echo 'export SSH_AUTH_SOCK' >> $HOME/.Xdbus
```

Then at the beginning of the backup script I import this by adding the following line at the start of the script:
```
source ~/.Xdbus
```

Hope this helps anyone else that stumbles upon this thread.

---

