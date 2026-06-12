---
title: "Howto - System-wide Cron jobs?"
date: 2010-01-23
forum: General Help
---

### Post by JetSirus on 2010-01-23
**EDITING FOR CLARITY:**  I can get Zenity to run in roots crontab, the issue is getting any command to run in the /etc/crontab file that is used run to system-wide cron jobs.

I need to make a whole series of system-wide cron jobs.  Ones that run no matter who is logged into the computer at the time.  Here is the list of things I need to do.

apt-get update
apt-get upgrade
reboot

And give warnings with something like - ```
zenity --info --text "System rebooting soon."
```

I have added all this stuff to the /etc/crontab file, but it NEVER executes.  I even added - ```
* * * * * root zenity --info --text "It works."
```

- and that never pops up the info box.  I have searched and scoured, but all the relevant information seems to be centered on setting up jobs for one specific user account at a time, and that isn't practical for my needs.  

Thanks in advance for any help!

---

### Post by dcstar on 2010-01-24
> **JetSirus said:**
> I need to make a whole series of system-wide cron jobs.  Ones that run no matter who is logged into the computer at the time.  Here is the list of things I need to do.

apt-get update
apt-get upgrade
reboot

And give warnings with something like - ```
zenity --info --text "System rebooting soon."
```

I have added all this stuff to the /etc/crontab file, but it NEVER executes.  I even added - ```
* * * * * root zenity --info --text "It works."
```

- and that never pops up the info box.  I have searched and scoured, but all the relevant information seems to be centered on setting up jobs for one specific user account at a time, and that isn't practical for my needs.  

Thanks in advance for any help!

All GUI apps require the screen to be specified.

This has been detailed many times in the hundreds of similar posts, search them out.

---

### Post by JetSirus on 2010-02-06
> **dcstar said:**
> All GUI apps require the screen to be specified.

This has been detailed many times in the hundreds of similar posts, search them out.

I appreciate your reply.  However, I mentioned quite clearly that I was unable to find information on my own with ample searching.  The root of my problem is not only getting zenity itself to work, but getting ANYTHING to execute from the main crontab file.  In fact, weeks later, I have found no competent answer on why this won't work.  I have found many tutorials yet none of them offer results.  All along I knew I could just edit roots crontab via 'sudo crontab -u root -e', but have been warned not to do so, and to instead use the other safer methods.  

Now, if there is any information I can provide to narrow down this issue I will gladly do so.  I am hesitant to make a bug report on this issue as I have not ruled out user error.  Until I can find a solution for my needs I have had to resort to using roots crontab despite warnings.  

Thanks in advance for any help.

---

### Post by dcstar on 2010-02-07
> **JetSirus said:**
> I appreciate your reply.  However, I mentioned quite clearly that I was unable to find information on my own with ample searching.  The root of my problem is not only getting zenity itself to work, but getting ANYTHING to execute from the main crontab file.
......

Well, 20 seconds searching these forums with the terms "cron zenity" delivered this (along with many others):

[http://ubuntuforums.org/showthread.php?t=1388161&highlight=cron+zenity](http://ubuntuforums.org/showthread.php?t=1388161&highlight=cron+zenity)

---

### Post by JetSirus on 2010-02-07
> **dcstar said:**
> Well, 20 seconds searching these forums with the terms "cron zenity" delivered this (along with many others):

[http://ubuntuforums.org/showthread.php?t=1388161&highlight=cron+zenity](http://ubuntuforums.org/showthread.php?t=1388161&highlight=cron+zenity)

Did you notice that the post you linked was by me?  I got it working by doing what I explained, using roots crontab, which is a no no.  Even the bit you quoted from my post states that it is not only zenity that I cannot get to run, but anything.  

Here, let me show you the exact quote you used from me:

> **JetSirus said:**
> I appreciate your reply. However, I mentioned quite clearly that I was unable to find information on my own with ample searching. _The root of my problem is not only getting zenity itself to work, but getting **ANYTHING** to execute from **the main crontab file**._
......

I want to apologize to anyone trying to help here for my slightly disgruntled tone.  While I do appreciate the bumps the other posters have provided, they aren't fully reading my posts.

Let me state one more time, for the record.

-I can get Zenity working fine in roots crontab.

-I can in fact get any command I need to execute in roots crontab.

-The problem is that I cannot get **any** command to execute in the **/etc/crontab** file that is supposed to be used for **system wide cron jobs**.

Thanks again to any and all that are trying to help.

**EDIT:**  On further reflection I am going to take some responsibility to the mix ups here. My first post wasn't very clear on my exact problems, and my follow up may have came off as foul tempered, causing it to be skimmed over.  I have edited the first post to more verbosely reflect my exact problem.

---

### Post by rnerwein on 2010-02-07
hi jetsirus
may be your problem is already solved - here is what will work ( just test it )
-----> if you are using crontab -e as root DONT enter the owner into the line !!!! see following lines <--

1. sudo /bin/bash
2. crontab -e
# m h  dom mon dow   command
45 13 * * * env DISPLAY=:0.0 /usr/bin/zenity --info --text "this will work !"

3. save this file
the problem was cron jobs running with out a display. but just a little thing you hav to do is !

4. xhost +localhost  <============ !!!!!
there fore i give the cronjob a shell script to execute.

# m h  dom mon dow   command
50 15 * * * /home/my_user/scripts/runcron 
the contens of the script is:
#!/bin/bash
xhost +localhost
DISPLAY=:0.0
export DISPLAY
/usr/bin/zenity --info --text "schau mal mal obsworks."
echo "hier bin ich" > /home/richi/tmp/cron-rundate."`date`"

be sure to make this script runable and do a chown root:root to it ( i now security system where cron is checking owner of the command to run too )

have a nice day  :-)
ciao

---

