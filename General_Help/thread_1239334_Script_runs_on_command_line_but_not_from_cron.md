---
title: "Script runs on command line but not from cron"
date: 2009-08-13
forum: General Help
---

### Post by noobydev on 2009-08-13
I'm running ubuntu server 9.04 and having a problem getting cron to run scripts.

It's a simple shell script that calls a python function in a web app. It works fine on the command line but not from cron. I need it to run once every minute.

Here's the script (~/bin/process.sh):

```
#!/bin/sh
cd app
paster run example.ini r2/lib/media.py -c "process_new_links()"
```

I also did a chmod 755 on the script.

Here's my cron settings:

```
* * * * * ~/bin/process.sh
```

Am I missing something in either of them? Any help would be great!

---

### Post by michy99 on 2009-08-13
Try changing```
cd app
```to use the absolute path.```
cd /home/YOUR_USERNAME/app
```or wherever app is located.

---

### Post by noobydev on 2009-08-13
Thanks, I just tried that and it's still not working unfortunately.

---

### Post by noobydev on 2009-08-13
Should I have anything else in my cron file? That one line is all I have in it at the moment.

---

### Post by wojox on 2009-08-13
Try this:
```
/1 * * * * ~/bin/process.sh
```

Make sure the script is in /bin/

---

### Post by noobydev on 2009-08-13
> **wojox said:**
> Try this:
```
/1 * * * * ~/bin/process.sh
```

Make sure the script is in /bin/

That give me this error:

```
crontab: installing new crontab
"/tmp/crontab.ORbxDB/crontab":0: bad minute
errors in crontab file, can't install.
```

---

### Post by ronaldprettyman on 2009-08-13
> **noobydev said:**
> I'm running ubuntu server 9.04 and having a problem getting cron to run scripts.

It's a simple shell script that calls a python function in a web app. It works fine on the command line but not from cron. I need it to run once every minute.

Here's the script (~/bin/process.sh):

```
#!/bin/sh
cd app
paster run example.ini r2/lib/media.py -c "process_new_links()"
```

I also did a chmod 755 on the script.

Here's my cron settings:

```
* * * * * ~/bin/process.sh
```

Am I missing something in either of them? Any help would be great!

```
 ~/bin/process.sh
```
Is your script located in /root/bin/
Put the full path to your script.
Make sure you have the header
add this line to make sure the script runs
and its not a logic error
```
echo SCRIPT WAS RUN `date` >> /var/log/MYSCRIPT
```

---

### Post by wojox on 2009-08-13
Sorry forgot *
```
*/1 * * * * ~/bin/process.sh
```

---

### Post by noobydev on 2009-08-13
> **wojox said:**
> Sorry forgot *
```
*/1 * * * * ~/bin/process.sh
```

Thanks, yeah I just a minute ago realised you probably meant that and gave it a try, but no change.

> **ronaldprettyman said:**
> ```
 ~/bin/process.sh
```
Is your script located in /root/bin/
Put the full path to your script.
Make sure you have the header
add this line to make sure the script runs
and its not a logic error
```
echo SCRIPT WAS RUN `date` >> /var/log/MYSCRIPT
```

Ok thanks, I'll try this out. Why should the script have to be in /root/bin/ though? I have had this working on 8.04 before the way I am trying it now (~/bin/). I wonder what has changed in ubuntu since then?

---

### Post by ronaldprettyman on 2009-08-13
> **noobydev said:**
> Thanks, yeah I just a minute ago realised you probably meant that and gave it a try, but no change.



Ok thanks, I'll try this out. Why should the script have to be in /root/bin/ though? I have had this working on 8.04 before the way I am trying it now (~/bin/). I wonder what has changed in ubuntu since then?

~ is the user directory
CRON is run as root
~ when run by cron means the root home directory as specified by the /etc/passwd file
if your /etc/passwd file says```
 root:x:0:0:root:/root:/bin/bash 
```like a normal distro.
~/bin/whatever
mean /root/bin/whatever when run by cron
you can always specify the use with this
~user/bin/bash
this would then refer to the home directory specifed by /etc/passwd file for the user user
so if your passwd file said
```
user:x:1000:1000:users:/export/home/user:/bin/sh
```
then 
~user/bin/whatever
would refer to 
/export/home/user/bin/whatever

Use full paths in configuration files and scripts
Unless you specify a PATH variable or define HOME don't use ~

---

### Post by noobydev on 2009-08-13
Ah right I get it, thanks.

The script is running ok and printing to the log file, but still not executing the python program.

Hitting /root/bin/process.sh on the command line works.

Ubuntu 9.04 moved to Python 2.6, maybe that has something to do with it?

---

### Post by DaithiF on 2009-08-13
> **ronaldprettyman said:**
> 
CRON is run as root
~ when run by cron means the root home directory as specified by the /etc/passwd file

Hi,
thats not correct actually, crontabs can exist for individual users too, and if the poster is editing their crontab using the usual crontab -e command then it is their own crontab they are editing, and any commands there will be run under their user id, and ~ will expand to their home directory, not roots.

Having said that, I would normally use explicit paths in my crontabs for avoidance of doubt.  Ditto for any script I run via cron.  So I would suggest making the paths to paster explicit in the script, and also add echo logging statements at various points in the script to see how far it gets.

---

### Post by noobydev on 2009-08-13
This app requires python 2.6 and I think ubuntu 9.04 has more than one version of python installed?

Does anyone know if there are any settings that should be in either my crontab or shell script that define the version/path for python?

I'm thinking that maybe the crontab/script is not running the same environment (python) as the command line.

---

### Post by DaithiF on 2009-08-13
no, in 9.04 the python on the path (/usr/bin/python) is a link to python2.6

just to confirm, your script now has a full path in the cd command ? 
and paster is in the default path (e.g. /usr/bin ?)
and the example.ini and r2/lib/media.py files are all below the app directory you cd to ?

as a last resort, how about redirecting stdout and stderr from your command to a file that you can inspect afterwards to see any errors reported.

so your paster command with this at the end
> /home/yourname/cron.out 2>&1

then wait to see what ends up in cron.out

---

### Post by noobydev on 2009-08-13
Yeah I'm using the full path in the cd command and the files are below app/

My cron.out is showing:

```
/root/bin/process.sh: 3: paster: not found
```

Looks like I need to tell it where paster is? As my name suggests I am quite the noob when it comes to linux. I've looked in the /usr/bin dir and there is the 'paste' program in there. Not sure what to do next.

---

### Post by DaithiF on 2009-08-13
ok good, we're getting there.
so we need to find where paster is on your system ( this is not the same as paste)
in a terminal, do
```
which paster

```

---

### Post by noobydev on 2009-08-13
That returns:

```
/usr/local/bin/paster
```

---

### Post by DaithiF on 2009-08-13
ok, so change your script to make that path explicit then, ie.
/usr/local/bin/paster
rather than just 
paster

---

### Post by noobydev on 2009-08-13
It's working!

Thank you so much for the help, I really do appreciate it. It's great that there are people out there willing to help noobs like myself :)

---

### Post by DaithiF on 2009-08-13
excellent, you're welcome.

---

