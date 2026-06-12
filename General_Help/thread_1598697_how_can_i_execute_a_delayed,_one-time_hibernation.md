---
title: "how can i execute a delayed, one-time hibernation?"
date: 2010-10-16
forum: General Help
---

### Post by Lynx Phoenix on 2010-10-16
I've been googling trying to find a way to hibernate at a specific time or after a some minutes (like 40 minutes to an hour, guess the exact time doesnt matter anyway). normally i shutdown my comp at night with ```
sudo shutdown - P HH:MM
``` which works just fine, but sometimes i have like 4 workspaces of stuff open that i'm working on so i'd rather just hibernate. **shutdown -H** does this halt thing that is really not my cup of tea so from the aformentioned googling i found out about **at** and **sleep** and **crontab** etc. but** at** and** sleep** cant recieve my sudo password beforehand so its useless and **crontab** is for repetitive scheduling, which i'd like to avoid cause i would hate to be working and suddenly have my forgotten crontab script hibernate me.

so is there any way to do a delayed hibernation? or at least some way to provide the sudo password to an **at** or **sleep** prefixed command, beforehand?

i'm only interested in doing it straight up through the terminal, not through other 3rd party software cause i tried a few of those before i found out about**[FONT=Verdana] shutdown[/FONT]** and they didnt work very well.

thanks

---

### Post by Lynx Phoenix on 2010-10-17
*bump*

---

### Post by yetiman64 on 2010-10-17
The at command can be used to launch a command as a once only instance. The command would be the hibernate script at /etc/acpi/hibernate.sh.

> [SIZE=1][SIZE=2][COLOR=#cc0066][COLOR=Black]Scheduling With the at Command[/COLOR][/COLOR]
                You can use the at command to schedule a command or script to                  run a single time.[/SIZE][/SIZE] This is from [--here--.]("http://www.debianhelp.co.uk/schedulejobs.htm")

The link above also shows time syntax and may be of help to you.

Edit: just noted the comment "**at** and** sleep** cant recieve my sudo password beforehand". This may not be of much use then sorry.

Edit 2: Test out the command ```
sudo at HHMM today -f /etc/acpi/hibernate.sh
``` and see if that suits your needs. I am currently waiting for this machine to hibernate right now, but the terminal looked promising :). UPDATE: It worked here. Just remember to change "today" to "tommorow" if your shutdown time passes midnight.

---

### Post by Lynx Phoenix on 2010-10-17
it did work sorta - it tries to hibernate but ends up with a black screen and a flashing cursor. i noticed other people also got this result when using hibernate.sh i think

your syntax does help me though, cause now i know how to get it to ask for the password right away

i tried this, which works:

```
sudo at HH:MM today
```and then it asks for a command with

```
at>
```at which point you just type ```
pm-hibernate
``` and use ctrl+d to end the input

i use pm-hibernate cause it works properly for me - if someone doesnt have a problem using hibernate.sh your syntax is much better

i tried entering ```
sudo at HH:MM today pm-hibernate
``` but it thinks pm is part of its time specification and i also tried several different ways to make it understand its the command (like brackets and && and | - which shouldnt really work but i tried them anyway) but no luck.

i just entered it so that it executes more than 5 minutes after i enter the command to see if it keeps the sudo pass (since i havent changed sudoers, normally it will forget my sudo password after 5 minutes and since pm-hibernate needs sudo, it might not work)

so i'm still waiting on it - gonna report back what happens.

---

### Post by Lynx Phoenix on 2010-10-17
it did work! yeah =)

ok so although its a bit less elegant than a single line command (which i would like it to become if anyone knows how to convince at what is a command and what is a parameter) it works exactly as needed

now, for the scary stuff - i've been trying this with various methods since yesterday and i did have a few failed hibernations where data was saved but the hibernation wasnt completed properly (blank screen with just a cursor).

now, i'm assuming the kernel doesnt know it tried to hibernate before, thus wont know there's residual saved states on the disk from all the failed hibernations.

should i be worried? is there something i can run in order to check and possibly clear the residual data from previous hibernations?

oh and thanks ^_^

---

### Post by yetiman64 on 2010-10-19
> **Lynx Phoenix said:**
> ...```
sudo at HH:MM today pm-hibernate
```....

For a one liner, try changing that to,
```
sudo at HHMM today -f /usr/sbin/pm-hibernate
```As far as I understand the contents of RAM are dumped to (a file in ??) the swap partition.
If you have had a few failed hibernates I suspect any data from them is gone and shouldn't affect current boots. Someone more knowledgeable would need to confirm that though.

---

### Post by Lynx Phoenix on 2010-10-19
> **yetiman64 said:**
> For a one liner, try changing that to,
```
sudo at HHMM today -f /usr/sbin/pm-hibernate
```

looking at that now, it seems obvious lol - disappointed with myself :P

i ran df on the terminal and it seems to me there's no strange space consumption but then again, i dont know how much space a hibernation uses. i marked this thread as solved so i guess its a matter for another thread.

edit - seems i cant close the thread though. i'll make a thread on the hibernation thing. thanks again mate ^_^

---

