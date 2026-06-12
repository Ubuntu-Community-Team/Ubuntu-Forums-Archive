---
title: "Does your Update Manager alert you to updates?"
date: 2010-08-13
forum: General Help
---

### Post by murphycc on 2010-08-13
Is there a bug in the 10.04 Update Manager? I have set my update manager to automatically notify me of updates daily, but I have never seen a pop-up alert in my task manager. For the last 3 months I have been checking almost daily for updates manually through the Add/Remove Software --> Software Updates GUI.

Anyone know why this doesn't work?

-Chris

---

### Post by kiridude on 2010-08-13
I think you have set it to CHECK daily for updates rather than notify you daily. Mine is set to check daily as well but only prompts me to update about once a week.

I don't see a need to update daily.

---

### Post by murphycc on 2010-08-13
I don't think that's my problem. I checked and I have "Check for updates: Daily" checked, as well as "Only notify about available updates" checked. The only other options are "Download all updates in the background" or "Install security updates without confirmation".

I also checked the notifications for kpackagekit, and all of the alerts for that program are activated, though I think the update manager uses a different alert system than the system-wide notification window that rises up on bottom of my screen.

Maybe I need to try setting it to weekly updates, then it would work.

-Chris




> **kiridude said:**
> I think you have set it to CHECK daily for updates rather than notify you daily. Mine is set to check daily as well but only prompts me to update about once a week.

I don't see a need to update daily.

---

### Post by inameiname on 2010-08-13
Just copy and paste (overwriting the old ones) the attached files into the folder mentioned and then you should get notified much more frequently of new updates. Also, this requires you to install unattended-upgrades:

sudo apt-get install unattended-upgrades

Although, while I sometimes use this, I'm more a terminal guy, and just have an alias in my .bashrc file which enables me to check for updates with a single word. Just copy and paste this into your ~/.bashrc and then with the word 'check' you can update just like that. Could even set it to run at startup or something, idk. (Note, it'll also cleanup for you after it installs too.)

alias check='sudo apt-get update && sudo apt-get -y upgrade && sudo apt-get -y dist-upgrade && sudo apt-get -y autoclean && sudo apt-get -y autoremove && sudo apt-get -y clean && sudo apt-get -y remove && orphand && sudo deborphan | xargs sudo apt-get -y remove --purge'

---

### Post by murphycc on 2010-08-13
Thanks, inameiname. I will try that.

Does that mean that you have also had problems with the Update Manager program, or have you always just used this other method? I will be glad to use this method if it's the only work-around, but I would like to know if the Update Manager is also not working or if it's just me.

Thanks again,
Chris


> **inameiname said:**
> Just copy and paste (overwriting the old ones) the attached files into the folder mentioned and then you should get notified much more frequently of new updates. Also, this requires you to install unattended-upgrades:

sudo apt-get install unattended-upgrades

Although, while I sometimes use this, I'm more a terminal guy, and just have an alias in my .bashrc file which enables me to check for updates with a single word. Just copy and paste this into your ~/.bashrc and then with the word 'check' you can update just like that. Could even set it to run at startup or something, idk. (Note, it'll also cleanup for you after it installs too.)

alias check='sudo apt-get update && sudo apt-get -y upgrade && sudo apt-get -y dist-upgrade && sudo apt-get -y autoclean && sudo apt-get -y autoremove && sudo apt-get -y clean && sudo apt-get -y remove && orphand && sudo deborphan | xargs sudo apt-get -y remove --purge'

---

### Post by Cavsfan on 2010-08-13
A friend of mine calls Update Manager Update Mangler! It is good for seeing if there are updates available and reviewing what they are, 
but I believe as **inameiname** does the command line method is better.

Just be sure and read what it is saying and if at the bottom it says it is removing something without replacing it 
```
0 upgraded, 0 newly installed, 0 to [COLOR=Red]remove[/COLOR] and 0 not upgraded.
```Or if Update manager mentions a Partial Update, just wait a day or so and when it goes away, then update.

---

### Post by plucky on 2010-08-13
> **murphycc said:**
> Is there a bug in the 10.04 Update Manager? I have set my update manager to automatically notify me of updates daily, but I have never seen a pop-up alert in my task manager. For the last 3 months I have been checking almost daily for updates manually through the Add/Remove Software --> Software Updates GUI.

Anyone know why this doesn't work?

-Chris

From the **Release Notes**

> Change in notifications of available updates

Ubuntu 10.04 LTS launches update-manager directly to handle package updates, instead of displaying a notification icon in the GNOME panel. Users are notified of security updates on a daily basis, but for updates that are not security-related, users will only be prompted once a week.

Users who wish to continue receiving update notifications in the previous manner can restore the earlier behavior using the following command:

gconftool -s --type bool /apps/update-notifier/auto_launch false

(This change was made in Ubuntu 9.04.) 

Good Luck

---

### Post by inameiname on 2010-08-13
Both methods I mentioned work just fine, it's just I tend to always be on the terminal, so I tend to go with updating through it instead of the update manager. I don't have any problems with update manager, and do use it when I am curious just what will be updated and perhaps what changes will occur with an upgrade, but like how the terminal shows all the packages that will be upgraded, including extras when something gets updated, and also the sizes of the updates. Also, with those extra commands I have on my terminal one I mentioned, it will automatically clean up whatever can be cleaned after an upgrade. 

FYI, if you do ever decide to just use the terminal command, probably a good idea to remove all the '-y' pieces of code from my command until you are used to it, as what that does is automatically do all the commands without having you input the 'yes' or 'no' command. Easier, but if you are unsure of whether you should or shouldn't upgrade something, better to look at what is getting updated/removed/installed first.

Nonetheless, the update manager works just fine, and with those couple files to replace that I gave it should pop up for ya with new updates daily, as you desire.

---

### Post by Cavsfan on 2010-08-14
> **inameiname said:**
> 

FYI, if you do ever decide to just use the terminal command, probably a good idea to remove all the '-y' pieces of code from my command until you are used to it, as what that does is automatically do all the commands without having you input the 'yes' or 'no' command. Easier, but if you are unsure of whether you should or shouldn't upgrade something, better to look at what is getting updated/removed/installed first.

I agree with this. You NEVER want to automatically give the "y" to continue an update! 
You could end up messing things up and wasting a lot of time getting things back to working again. That is if you ever do.
I think the '-y' option is a very bad idea!

---

### Post by murphycc on 2010-08-14
Thanks, everyone, for the replies. They are very helpful. I will probably set up the alias to allow me to update through command line, but for time being might stick with manual updates through the Update Manager.

Regarding the gconftool ... suggestion. I did see that in my searches too, but since I'm using KDE I didn't think gconftool would change anything in my registry that would matter to KDE anyhow. Isn't gconftool only for Gnome?

I also tried installing the update-notifier and update-notifier-kde packages, but I think that has also been replaced in the current Lucid distro. A little confusing.

So again, thanks for the help. I will likely try the command line method (without automatically saying 'y' to all updates as Cavsfan suggests) in the future.

-Chris

---

### Post by mörgæs on 2010-08-23
I had a similar problem in Ubuntu 10.04 minimal, and the reason was a missing **update-notifier**:
[http://ubuntuforums.org/showthread.php?t=1557339](http://ubuntuforums.org/showthread.php?t=1557339)

I don't know with Kubuntu, though.

---

