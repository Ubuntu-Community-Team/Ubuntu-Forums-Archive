---
title: "UBUNTU for SCHOOL"
date: 2006-04-05
forum: General Help
---

### Post by ashrack on 2006-04-05
In school we are trying to set up an INTERNET CORNER with around 6computers so the students will have access to internet... I proposed that we should try LINUX instead of Windows. So tomorrow am getting a computer which I will try to set up.
The computers are around 1GHZ,256MB.
I will be setting them up with GNOME since its the most familiar DE 4M. 

On these computers only FIREFOX, OpenOffice,aMSN, THUMBDRIVEs(4 students to copy stuff of the net...) and around 5GB of HDD space will be allowed to students. The rest of the system must be protected by at least a password.

How do I go about doing this??

ps. and if it is somehow possible to have AUTOMATIC UPDATES so the updates would download and install without any user intervention. So the students wouldn't even know an update is being installed whilst they are doing something on the computer??

---

### Post by lleb on 2006-04-05
those systems should be fast/strong enough to run Ubunut even with Gnome as the desktop.  They will be slugish when it comes to opening programs like OO and FireFox, but should work well enough for FREE internet access.

as for locking the users out of the rest of the system, under full linux that is easy you just remove the premisions for the "user" to access anything outside of /home/user_name and you are done.

with Ubuntu i have no clue, but keep in mind if the root p/w is strong enough (at least 12 characters using both capital, lower case, and numbers along with symbols) then it will be harder for it to be cracked.

best of luck to you.

---

### Post by ubuntu27 on 2006-04-05
[QUOTE=ashrack]In school we are trying to set up an INTERNET CORNER with around 6computers so the students will have access to internet... I proposed that we should try LINUX instead of Windows. So tomorrow am getting a computer which I will try to set up.
The computers are around 1GHZ,256MB.
I will be setting them up with GNOME since its the most familiar DE 4M. 

On these computers only FIREFOX, OpenOffice,aMSN, THUMBDRIVEs(4 students to copy stuff of the net...) and around 5GB of HDD space will be allowed to students. The rest of the system must be protected by at least a password.

How do I go about doing this??

ps. and if it is somehow possible to have AUTOMATIC UPDATES so the updates would download and install without any user intervention. So the students wouldn't even know an update is being installed whilst they are doing something on the computer??[/QUOTE]

Woh, Cool! WHat school is that? and where are you from?

---

### Post by Jason_25 on 2006-04-05
Don't forget to check out edubuntu if you haven't already.

---

### Post by ubuntu27 on 2006-04-05
[QUOTE=Jason_25]Don't forget to check out edubuntu if you haven't already.[/QUOTE]

oH yeah! I almost forgot about the Linux for Young Human beings :D


ashrack, try [http://www.edubuntu.org/](http://www.edubuntu.org/)

It's ubuntu with Educational Packages.

---

### Post by tagg3rx on 2006-04-05
Hurm I think you have a good idea but the limitation needs may have not been considered correctly and the problems identified correctly.

First - you are not going to want create a new user account for each student in your school who comes by and wants to use the PC.  That would be a nightmare - would be better to have one standard user that runs a script on login to clear the home directory out.

Next - When you plug in a thumb drive it needs to be mounted before you can access it.  is there a way to automate this?  I don't know just adding the question for discussion.

Good luck here - hope someone with more experence as an ubuntu SA can step in here with some answers.

---

### Post by ashrack on 2006-04-06
[QUOTE=ubuntu27]Woh, Cool! WHat school is that? and where are you from?[/QUOTE]
We are from Europe,Slovenia and the the city is Kamnik.And in our little COUNTRY M$ is stil No.1:( The school is called ZUIM. Its a mixed school for phisycally and mentaly disabled teenagers and also us who are fortunate enough to be for the lack of my english vocabulary "normal". Well as U guesst it Im a student here also.

---

### Post by ashrack on 2006-04-06
[QUOTE=Jason_25]Don't forget to check out edubuntu if you haven't already.[/QUOTE]
I will check it out. But am am a lot more familiar with normal UBUNTU which I've been using for about half a year now. And also our needs only require the afore mentioned programs

---

### Post by ashrack on 2006-04-06
[QUOTE=tagg3rx]
First - you are not going to want create a new user account for each student in your school who comes by and wants to use the PC.  That would be a nightmare - would be better to have one standard user that runs a script on login to clear the home directory out.[/quote]
Crap apperantly I wasnt clear enough, my usual problem ](*,) ](*,) ](*,) 
Im just going to create one user account named ex.: STUDENT and this account should have:
> On these computers only FIREFOX, OpenOffice,aMSN, THUMBDRIVEs(4 students to copy stuff of the net...) and around 5GB of HDD space will be allowed to students. The rest of the system must be protected.

> Good luck here - hope someone with more experence as an ubuntu SA can step in here with some answers.
I appreciate all the help I can get. I just hope I have or will learn enough expertise to complete this so called "internet corner"

---

### Post by Marshall2day on 2006-04-06
[QUOTE=tagg3rx]
Next - When you plug in a thumb drive it needs to be mounted before you can access it.  is there a way to automate this?  I don't know just adding the question for discussion.
[/QUOTE]

AFAIK Ubuntu does this by default.

---

### Post by tagg3rx on 2006-04-06
yea - i would have thunk the same then i plugged in my thumb drive and avast there was nothing listed under /media or /mnt for it.  Was a bit to busy to go through fdisk yesterday and check to see if it was in there.  BUt i suspect you have to mnt it in the fstab.

---

### Post by Toxicity999 on 2006-04-06
As for automatic updates... something was just added as of Dapper for controling silently installed updates... of course you don't need this just simply have a login script to run apt-get update to update the sources then run a nice upgrade.. of course since this requires their pass it's touchy... might want to just look into allowing upgrades for atleast base software and Security updates without needing the pass. prompt.

---

### Post by ashrack on 2006-04-06
I have the base install of UBUNTU installed. All great. Except I am a little worried about security. I created an account called STUDENT which students in school will use. It has auto login set.
But to my amazement I could run SYNAPTIC and all other sorts of administrative tasks without even for a prompt for password.. This is no good. How do I tighten up security

---

### Post by ashrack on 2006-04-07
[QUOTE=ashrack]I have the base install of UBUNTU installed. All great. Except I am a little worried about security. I created an account called STUDENT which students in school will use. It has auto login set.
But to my amazement I could run SYNAPTIC and all other sorts of administrative tasks without even for a prompt for password.. This is no good. How do I tighten up security[/QUOTE]
anyone pliz

---

### Post by trent dillman on 2006-04-07
Remove the student login from the admin group.

---

### Post by ashrack on 2006-04-07
[QUOTE=trent dillman]Remove the student login from the admin group.[/QUOTE]
will this reinstate the need for a password when shuch an application would lunch?

---

### Post by Ramses de Norre on 2006-04-07
Removing the user from the admin group should disable them to use sudo. They can't use it at all.

---

### Post by ashrack on 2006-04-08
[QUOTE=Ramses de Norre]Removing the user from the admin group should disable them to use sudo. They can't use it at all.[/QUOTE]

so I should first set everything up for the user STUDENT and then just remove it from the ADMIN GROUP??
How do I do that, and how would I add it back to the ADMIN GROUP if I ever need to change something

---

### Post by Chickenmonger on 2006-04-08
First set up the system with the user "teacher" or something a little more clever. That user would have administrator (sudo) privileges. After everything is set up, a "student" user could be created that does not have access to sudo.

---

### Post by Toxicity999 on 2006-04-08
If you need any clarification as it was a little vague, the previous poster is saying to install Ubuntu but the main account created on install will be 'teacher', 'staff', 'owner' or whatever, something for computer admins to use. This account will have Sudo access and for that matter access to anything they need. Now create another user after loging in as this user (created during installation.) called student. You can use the system > administration > users and groups for all of this. Ah, and add the student account to any groups you find they will need that aren't given to them on account creation. Shouldn't need to tweak that for a basic installation but in anycase reference that statement if needed. The easiest thing for you update wise is add startup scripts to the teacher account to gksu apt-get update && apt-get upgrade or just run synaptic themselves press ctrl+g and apply. However you want. Or of course you could always just set up a job to automatically fetch them. And I think dapper now has an auto update thang going on. But, all up to you.

Edit:: Also, I applaud you 10,000 fold for introducing Linux into a classroom!

---

### Post by ashrack on 2006-04-09
[QUOTE=Toxicity999]Ah, and add the student account to any groups you find they will need that aren't given to them on account creation.[/quote]
how do I add my account to groups thru CLI, I know only how to do it thru GUI??

> The easiest thing for you update wise is add startup scripts to the teacher account to gksu apt-get update && apt-get upgrade or just run synaptic themselves press ctrl+g and apply. However you want. Or of course you could always just set up a job to automatically fetch them.
This computers will be in the lobby, mostly unattended meaning usually only students will be using them. That's way securing them is of outmost importance. So I thing the best way would be to set up a cron job, right??

> Edit:: Also, I applaud you 10,000 fold for introducing Linux into a classroom!
Not only classroom, since these 6 computers will be in the lobby the students and also the teenagers that live in the dormitory will have free access to them. If this project works I believe we could convert more computers to *nix.

going to bed now. Will be posting more questions about certain issues about security tomorrow. Im to tired right now.

---

### Post by ashrack on 2006-04-10
anyone could help with my previous post

---

### Post by Ferrat on 2006-04-10
[QUOTE=ashrack]
This computers will be in the lobby, mostly unattended meaning usually only students will be using them. That's way securing them is of outmost importance. So I thing the best way would be to set up a cron job, right??

Not only classroom, since these 6 computers will be in the lobby the students and also the teenagers that live in the dormitory will have free access to them. If this project works I believe we could convert more computers to *nix.

going to bed now. Will be posting more questions about certain issues about security tomorrow. Im to tired right now.[/QUOTE]

If it was me I would just make a lowlevel usergroup with the once in the Lobby, where they can just run programs and not use any sudo ect. 
As Im guessing you only need firefox and OpenOffice on them? 

Since it's only 6 computers now as I understand I would just do it as simple as possible but if your school is thinking of expanding ( I'm guessing all comps are in a network ) I would look upp the possibilities of having a comp serv as login server on the network giving diffirent access depening on each person, sure this is more work but in the longrun it's less work for Maintenance, updates and so on, I server that can wake up all the comps via LAN, log what users are online and so on, this will remove alot of thing that students can mess up and also priviliges will be easy to give and remove ect. 

Also a timer update perhaps? all systems start up sometime on every sunday and update, not 100% sure how to do this in Ubuntu but I had that configuration for updates when I was on redhat a few years ago and was on a 33.6 modem, my comp booted up every thursday and monday at around 03:00 and updated then went back sleep. 

Simple rule is the more initial work you do, the less you need to run and fix everything later ;)

---

### Post by ashrack on 2006-05-03
In the meantime I went from BREEZY to DAPPER! And I have secured the STUDENT account with the help of PESSULUS! And removed SUDO priviligies to it.So the computer is almost ready for deployment to school!!!! But still have the following glitch:
The users logged under STUDENTs will still be able to change their home directory(example: .gnome2,Deskop,.aMSN,.metacity... etc) How do I also secure these so they will only be able to read them and execute them??

btw.I know I could achieve this thru CHMOD or CHOWN but I dont know of which files/directories I can change permission!!! So please help me so I can get this machine to school already

---

### Post by IYY on 2006-05-03
About your auto-update problem:

Maybe you could add a cron job that'll be executed as root (to eliminate the need to enter a password when it happens) at specific time intervals that'll run the CLI command for update.

About locking the configuration files:

You could just set it up so when a user logs out, his home directory gets restored to its original status (copied from some location in /usr/share/......). I think this is better than just locking access to config files, or at least it's what I'd prefer as a user.

---

### Post by ashrack on 2006-05-03
[QUOTE=IYY]About your auto-update problem:

Maybe you could add a cron job that'll be executed as root (to eliminate the need to enter a password when it happens) at specific time intervals that'll run the CLI command for update.[/QUOTE]
I put an INIT script so at shutdown the DAPPER will auto get updated.
If interested here's how I did it:
[http://ubuntuforums.org/showpost.php?p=982374&postcount=14](http://ubuntuforums.org/showpost.php?p=982374&postcount=14)

[QUOTE=IYY]
You could just set it up so when a user logs out, his home directory gets restored to its original status (copied from some location in /usr/share/......). I think this is better than just locking access to config files, or at least it's what I'd prefer as a user.[/QUOTE]
Thats very interesting. How exactly would I do that?

---

### Post by ashrack on 2006-05-04
[QUOTE=IYY]
You could just set it up so when a user logs out, his home directory gets restored to its original status (copied from some location in /usr/share/......). I think this is better than just locking access to config files, or at least it's what I'd prefer as a user.[/QUOTE]
Does anyone know how would I achieve this?

---

### Post by ashrack on 2006-05-09
Over at GNOME forum a user said that in order to achieve this:
> You could just set it up so when a user logs out, his home directory gets restored to its original status (copied from some location in /usr/share/......). I think this is better than just locking access to config files, or at least it's what I'd prefer as a user.
I must do this:
> Modify the user ~/.xsession, add the script you want to execute at logout after the "gnome-session" line (and maybe disable the X option to use "Ctrl-Alt-Backspace"). Gdm should have similar options too.

Even if not strictly Ubuntu related, you should find with google various project to configure "kiosk" box.
But theres no ~/.xsession file. How should I procced?

---

### Post by ubuntu27 on 2006-05-11
This thread is "interesting" I will like to see a solution to his plans. :) 

Too bad I cannot help you. :(

Keep up your good job ashrack. Remember to persevere.


***Bump*** :rolleyes:

---

### Post by ashrack on 2006-05-11
so far I did this:

this is how I achieved this:
I tarred the STUDENT folder to /home/qhome.tar.gz. And chown it to TEACHER and gave executable permission to all.
So then I put this script into GNOME->SESSIONS->STARTUP PROGRAMS:
[ATTACH]9278[/ATTACH]

tell me what do U think?

ps. and another usefull link for locking down computer:
[http://ubuntuforums.org/showthread.php?t=93397](http://ubuntuforums.org/showthread.php?t=93397)

---

### Post by xtacocorex on 2006-05-11
I applaud your effort! The nice thing about what you are doing is that you're setting up decently secure systems that can't be infected by virii so any visit to a bad website won't cause harm.

I would make sure that when you restore the default settings to the student user's home directory that you don't delete any files they may have saved there. 

One thing I'm getting confused on is the username. Is STUDENT the students username or a general one that everyone will use? This raises some issues as if it is the same username, people won't log off the machine when they are done, thus preventing the settings reset. 

One thing I would change is the autoupdater. If I was in this position, I'd set up a cron job to have it run in the middle of the night and not at shutdown. Linux as an OS has a good record of uptime and doesn't need to be shutdown. You could also have that script check if something was updated that it could restart the machine for the new fixes to take effect. This would ensure that vulnerabilities would close after an update. A more intelligent idea, albiet a lot harder, would figure out what got updated and if any important services did, restart them. I don't have ideas on how that would work, but someone somewhere might have figured it out.

Quick edit here: If I remember correctly from searching this forum, Gnome needs to be restarted after updates for stuff to take effect, I could be wrong though.

Hope I gave some good ideas and sorry if they seem way out there, I'm an engineer and we like to think all the time.

---

### Post by ashrack on 2006-05-11
[QUOTE=xtacocorex]I applaud your effort! The nice thing about what you are doing is that you're setting up decently secure systems that can't be infected by virii so any visit to a bad website won't cause harm.[/quote]
thank U

> I would make sure that when you restore the default settings to the student user's home directory that you don't delete any files they may have saved there.  
It is intentional to delete everything new created in there.

> One thing I'm getting confused on is the username. Is STUDENT the students username or a general one that everyone will use? This raises some issues as if it is the same username, people won't log off the machine when they are done, thus preventing the settings reset. 
4accounts exist.
TEACHER---the allpowerfull teacher account...
STUDENT----used for students, tightly secured
BLUMEN-----used for students with handicapped needs also tightly secure
PLAY_WITH_ME-----used for those who would want to try something and perhaps even learn. With this account ppl can do anything that concerns their home dir/settings... And also this account will not be supervised. So if they break it they will have to fix it. 

> One thing I would change is the autoupdater. If I was in this position, I'd set up a cron job to have it run in the middle of the night and not at shutdown. Linux as an OS has a good record of uptime and doesn't need to be shutdown. You could also have that script check if something was updated that it could restart the machine for the new fixes to take effect. This would ensure that vulnerabilities would close after an update. A more intelligent idea, albiet a lot harder, would figure out what got updated and if any important services did, restart them. I don't have ideas on how that would work, but someone somewhere might have figured it out.
I wrote an INIT script that is executed at shutdown. So all of the updates are installed and no restart is required.

> Quick edit here: If I remember correctly from searching this forum, Gnome needs to be restarted after updates for stuff to take effect, I could be wrong though.

I believe that only certain parts needs to be restarted. Ive never needed to restart a machine unless there was a KERNEL UPDATE.
> Hope I gave some good ideas and sorry if they seem way out there, I'm an engineer and we like to think all the time.
Everysince I switched from Win to LINUX about 6months ago(woav that long=)) Ive found myself thinking more. It kinda changed the way I view certain things in life.But then again am a 21year old teenager what do I know ;)

---

### Post by xtacocorex on 2006-05-11
[QUOTE=ashrack]But then again am a 21year old teenager what do I know ;)[/QUOTE]
Then technically you aren't a teenager... :p 

Thanks for the clarifications on how you have stuff setup. I have to say that you have it setup nicely. The hard thing for new Linux users to understand is that by figuring out problems, like yours, you learn how the OS works. I know a couple of people who run Linux that wouldn't even have attempted this after using it for 6 to 12 months.

As soon as I read your reply to the updater, I figured out why you did that. I just set a subscription to the init scripts thread because that might come in handy, especially since thesheep posted a good description of how it [init] works.

---

### Post by ashrack on 2006-05-18
finally achieved the restore user at log in. My previous sollution didnt work because the GNOME stopped responding. But this new sollution works great.
Here the link to it:
[http://gnomesupport.org/forums/viewtopic.php?p=51538#51538](http://gnomesupport.org/forums/viewtopic.php?p=51538#51538)

---

### Post by ashrack on 2006-06-10
just to inform U all! The schools DIRECTOR was very happy with the project so happy that on tuesday the minister for schools is coming to see my project...

---

### Post by ubuntu27 on 2006-06-10
[QUOTE=ashrack]just to inform U all! The schools DIRECTOR was very happy with the project so happy that on tuesday the minister for schools is coming to see my project...[/QUOTE]


Great!! That's awesome!! Good job :) ashrack. You are the hero 8) 

Now, I will like to know what the minister said :)

---

