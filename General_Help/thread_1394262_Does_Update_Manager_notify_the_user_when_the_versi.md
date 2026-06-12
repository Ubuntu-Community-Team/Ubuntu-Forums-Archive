---
title: "Does Update Manager notify the user when the version is no longer supported?"
date: 2010-01-30
forum: General Help
---

### Post by GiveLove on 2010-01-30
Hello Everyone, :)

So I'm in the process of turning my mother over to using Ubuntu Linux as she is a typical clueless user that doesn't know how to keep to her WinXP OS and applications updated. So I'm trying to lessen my workload by bringing her over to Ubuntu, as Update Manager easily does all the updating for the user. This will hopefully be my first convert to Linux! :D  

I've been using Ubuntu for a number of years now, but I've never used a version till the end of it's support cycle. So what I'm wondering is will the "Update Manager" or perhaps another application warn the user that the version of Ubuntu they are using is no longer supported? 

My thought being, that if I can install Ubuntu on my mothers computer and she is able to use it with no problems, I need to have a way for her to let me know when I need to go back up there to do a fresh install of a new version when the current one is no longer supported. So that I do not have to keep track of that myself. 

Thanks. :)

GiveLove

---

### Post by jerrrys on 2010-01-30
why not go from LTS (currently 8.04) to LTS (about to be 10.04) and your good to go for two years...

---

### Post by GiveLove on 2010-01-30
Hello jerrys, :)

Thank you for your response. While I understand your point...  and I could do that. But it still does not answer the question of whether Ubuntu Update Manager notifies the user when the release/version they are using is no longer supported. Remember, I do not want to have to keep track of this for other people. In addition since Ubuntu releases have been less than stable and reliable upon release, using the most current version is usually a bad idea. So I tend to stay one version behind until the next version is released. 

GiveLove

---

### Post by todak on 2010-01-30
It will notify you of any new versions of ubuntu if you check how you want the new distros to be shown to you as per the attached screenshot from **Software Sources**

---

### Post by GiveLove on 2010-02-01
Hello todak, :)

Thank you for your reply. I have been aware of those options. Unfortunately it does not answer my question. Let me try and clarify...

If a user does not know at what date,for example, Ubuntu 9.04 support will end, which would be 10/2010. Is Ubuntu designed to notify the user that the release they are using is no longer supported? Rather than letting them continue to use that version without some sort of warning. 

GiveLove

---

### Post by mikewhatever on 2010-02-01
> **GiveLove said:**
> 
........
If a user does not know at what date,for example, Ubuntu 9.04 support will end, which would be 10/2010. Is Ubuntu designed to notify the user that the release they are using is no longer supported? Rather than letting them continue to use that version without some sort of warning. 

GiveLove

I don't think it does. That said, Ubuntu's support cycle is not a secret. Both release and end of support dates are announced in advance, so why would you not know or need a warning?

---

### Post by HiImTye on 2010-02-01
I think I saw this in patch notes some time ago, but I could be wrong so while my initial answer would be 'yes' my short answer would be 'no'

---

### Post by chewearn on 2010-02-01
I last ran Gutsy Gibbon 6 months past it EOL, and there is no notification about EOL.  I don't think there has been any development to change this since (I'm subscribed to the dev mail lists, and did not read any discussion on this topic).

---

### Post by GiveLove on 2010-02-02
Thank you for all of your responses. :)

I sort of suspected that there was no mechanism to notify the user of when support ended for a release. But I wanted to know for sure. 

To answer your question mikewhatever:
For myself, no this would not be an issue. I am aware of how long each release is supported for. But if you read my first post in this thread, as I try and convert family and friends to ubuntu Linux, these are people that are not terribly computer literate. And if I have enough people on Ubuntu to support, depending on what release they are using, it will be a pain for me to remember when their version needs to be updated. Keeping in mind that I stay about six months behind the current release, as I want a stable and mostly bug free OS and apps to work from. So in that light, a notification for the user would be handy and make sense. Looks like I'll have to leave them a note as to when support ends for their Ubuntu release so they can call me to come over and upgrade it. 

GiveLove

---

### Post by chewearn on 2010-02-02
I would say it's not overly difficult to hack a weekly cron script that check the date and pop an alert after EOL.

---

### Post by philinux on 2010-02-02
> **GiveLove said:**
> Hello Everyone, :)

So I'm in the process of turning my mother over to using Ubuntu Linux as she is a typical clueless user that doesn't know how to keep to her WinXP OS and applications updated. So I'm trying to lessen my workload by bringing her over to Ubuntu, as Update Manager easily does all the updating for the user. This will hopefully be my first convert to Linux! :D  

I've been using Ubuntu for a number of years now, but I've never used a version till the end of it's support cycle. So what I'm wondering is will the "Update Manager" or perhaps another application warn the user that the version of Ubuntu they are using is no longer supported? 

My thought being, that if I can install Ubuntu on my mothers computer and she is able to use it with no problems, I need to have a way for her to let me know when I need to go back up there to do a fresh install of a new version when the current one is no longer supported. So that I do not have to keep track of that myself. 

Thanks. :)

GiveLove

Keep an eye on this page. LTS gets 3 years support for the desktop version.
[http://en.wikipedia.org/wiki/List_of_Ubuntu_releases#Release_history](http://en.wikipedia.org/wiki/List_of_Ubuntu_releases#Release_history)

---

### Post by lavinog on 2010-02-02
I think a notification should be implemented.  Ubuntu is for everyone, not just users that track releases.  Upgrades can break if support has expired...this puts users in a bad place.
You can submit an idea to brainstorm to add this notification.
Filing a bug report should get more attention though.

---

### Post by philinux on 2010-02-02
I install each new version however wouldn't the update manager complain that the repo's have gone. 404 error or something.

---

### Post by chewearn on 2010-02-02
> **lavinog said:**
> I think a notification should be implemented.  Ubuntu is for everyone, not just users that track releases.  Upgrades can break if support has expired...this puts users in a bad place.
You can submit an idea to brainstorm to add this notification.
Filing a bug report should get more attention though.

> **philinux said:**
> I install each new version however wouldn't the update manager complain that the repo's have gone. 404 error or something.


For fun I did a quick search.  There were a few places where it was considered how the Update Manager broke after EOL (repository offline, switched to archive).
[http://brainstorm.ubuntu.com/idea/17489](http://brainstorm.ubuntu.com/idea/17489)
[https://bugs.launchpad.net/ubuntu/+source/update-manager/+bug/319146](https://bugs.launchpad.net/ubuntu/+source/update-manager/+bug/319146)

However, this only apply to fixing the status of Update Manager from saying "Up to date" to EOL.  An active notification would be an additional step.

---

### Post by GiveLove on 2010-02-03
Thank you for all of your responses people. :)  I am aware of how long each Ubuntu release is supported for. But in the interest of keeping my work load low in helping friends and family with Ubuntu, that doesn't help those that I install Ubuntu on their computers. 


Hello lavinog, :)

Thank you, thank you, thank you!!!! :D

You are first user here that posted on this thread that really gets what I am saying!!! 


Hello chewearn, :)

While hacking out a script might be easy for you. I am not a programmer. So I'll leave that to you. :D  Thank you ever so much for searching for the brainstorm and launchpad links. The person who posted those has exactly the right idea, and it is what I am talking about as far as a feature missing, or bug in Ubuntu. I'm going to post on those places and link to this thread. 

Love_is

---

### Post by chewearn on 2010-02-03
> **GiveLove said:**
> While hacking out a script might be easy for you. I am not a programmer. So I'll leave that to you. :D 


Alright.  Here is a quick and dirty hack.  Please read the comments for the necessary modifications and requirement.

```
#!/bin/bash

# Add the script to run periodically in crontab
# Example, run every Monday at 12pm:
# 0 12 * * 1 /full/path/to/script/eol-check.sh >/dev/null 2>&1

# Required for crontab script to find the X display
export DISPLAY=:0

# Ubuntu EOL Date
# Reference: http://en.wikipedia.org/wiki/List_of_Ubuntu_releases
# Date is only accurate to the month.
# Remove comment # for your install
EOL_DATE=$[ `date +%s` - 1 ]    # Test
#EOL_DATE=`date -d "1 Apr 2011" +%s`    # Hardy Heron
#EOL_DATE=`date -d "1 Apr 2010" +%s`    # Intrepid Ibex
#EOL_DATE=`date -d "1 Oct 2010" +%s`    # Jaunty Jackalope
#EOL_DATE=`date -d "1 Apr 2011" +%s`    # Karmic Koala
#EOL_DATE=`date -d "1 Apr 2013" +%s`    # Lucid Lynx

CURRENT_DATE=`date +%s`

if [ $CURRENT_DATE -gt $EOL_DATE ] ; then
# need Zenity to display pop-up
# sudo apt-get install zenity
    zenity --info --title="Installation End-Of-Life" \
    --text="This Ubuntu installation has reached End-Of-Life.  Please upgrade to new version."
fi
```

---

### Post by lavinog on 2010-02-03
> **chewearn said:**
> Alright.  Here is a quick and dirty hack.  Please read the comments for the necessary modifications and requirement.



I am going to attempt a script.
Instead of using a preset date, a formula can be used to determine the EOL date.

The distribution versions use a year.month code
If the year is even and the month code is less than 7 (dapper was 6.06) then it is a LTS and has 3 years for desktop and 5 years for servers.

otherwise it is 18 months.

---

### Post by lavinog on 2010-02-03
Attached is a python script for notifying the user if end of support is coming soon.

right not debug is set to True for testing.

I am looking for a way to test if the system is a server install or a desktop install.

I am also looking at adding an icon to the notification.
pynotify is still new to me.

---

### Post by GiveLove on 2010-02-03
Hello chewearn & lavinog,  :)

While I've been using Linux for many years now, I'm not completely versed in all it's aspects. So how would I go about installing your custom scripts so I can test them? I assume it is just a text file that has to be placed in the correct folder? Something in /etc likely?  

And are you placing these scripts here just as examples? Or are you willing or wanting to fine tune them? 

Can I assume that I can test the notification by just changing the system time?

Thanks for joining and contributing to this thread. :D

GiveLove

---

### Post by lavinog on 2010-02-03
My script isn't finished yet. The one I posted can be downloading to any folder (such as home)
then executed by opening a terminal
change to that folder then type:
```

python eol_notify.py

```

---

### Post by lavinog on 2010-02-03
Ok I updated it.

To test it out:
```

python eol_notify.py -D 8.10

```

You should get a notification that looks like this:
[img]http://ubuntuforums.org/attachment.php?attachmentid=145937&stc=1&d=1265256592[/img]

If you would like to install this use the following commands:
```

sudo cp eol_notify.py /usr/local/bin/eol_notify
sudo chown root:root /usr/local/bin/eol_notify
sudo chmod 755 /usr/local/bin/eol_notify

```

you can then test it by using just **eol_notify -D 8.10** from any folder.

**-D 8.10** tells it to assume the system is 8.10 which should be expiring soon.  **eol_notify** by itself will warn if the current system is about to expire.

you can add this check to startup applications (System->Preferences->Startup Applications) so that it does this check every time you logon.

edit: To uninstall it:
```

sudo rm /usr/local/bin/eol_notify

```

---

### Post by chewearn on 2010-02-04
> **GiveLove said:**
> Hello chewearn & lavinog,  :)

While I've been using Linux for many years now, I'm not completely versed in all it's aspects. So how would I go about installing your custom scripts so I can test them?  I assume it is just a text file that has to be placed in the correct folder? Something in /etc likely?  

No installation required.
Copy/paste the script into a text file (I use: "eol-check.sh").
Save the file somewhere out of the way where it won't get deleted by normal user (e.g. set owner to root, move to location /usr/local/bin/).
Set the executable bit for the file.
Set a crontab to run it periodically.


> And are you placing these scripts here just as examples? Or are you willing or wanting to fine tune them? No problem getting feedback and fine tuning the script.  But you need to have at least a minimum of BASH knowledge to change the few things I commented in the script yourselves.

> Can I assume that I can test the notification by just changing the system time?

Thanks for joining and contributing to this thread. :D

GiveLoveThe script is simple enough, I don't see any need to change system time just to test it.

Anyway, I already have one (debug) line testing the notification (which assume the EOL date is yesterday).

---

