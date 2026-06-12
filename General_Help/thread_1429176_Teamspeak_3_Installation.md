---
title: "Teamspeak 3 Installation"
date: 2010-03-13
forum: General Help
---

### Post by Neiklot on 2010-03-13
Hey there 

I am having trouble installing the file TeamSpeak3-Client-linux_x86-33.0.0-beta17.run

I try clicking on it , the error message i get is 'Please check that you are not trying to open a binary file.'

I am very unfamiliar with ubuntu so I appreciate your patients! Thanks!

I have been missing a series of important meetings because of this problem. 
Please help!

---

### Post by denver on 2010-03-13
You will have to run it from a terminal. Go to applications-->accessories-->terminal and type in the following:

```
cd ~/Desktop
sh TeamSpeak3-Client-linux_x86-33.0.0-beta17.run

```

Assuming that the file is on your Desktop of course. It will then ask you to agree to a license. Press enter to view the license, and then press "q" to quit the licence viewer. Type in yes to agree to the license (if you DO agree of course) and a new folder should be present on your desktop.

In that folder you should see:

ts3client_runscript.sh

Just double click that, and you should be good to go.

---

### Post by diavel on 2010-04-10
Unfortunately (as often in Ubuntu) there is a problem with sound. I either can hear teamspeak or game sound, not both. I don't want to set up sound again after I finally somehow managed to talk using skype (after a few hours of googling). :'(

---

### Post by cK` on 2010-04-13
good post thanks!

---

### Post by Dayofswords on 2010-04-13
> **cK` said:**
> good post thanks!

random much?


to diavel
what game are you running alongside?

---

### Post by wrcflier on 2010-09-12
Hi,  I followed Denver's instructions exactly (I think), except substituting the newer version numbers.  While in terminal it comes back saying that it can not open it ?
 cd ~/Desktop
 sh TeamSpeak3-Client-Linux_x86-3.0.0-beta29.run 
 I also re-downloaded the file direct from teamspeak
   Suggestions ?  Please ?   Thanks,  Bill

---

### Post by v1ad on 2010-09-13
first of all.
```

chmod u+x TeamSpeak3-Client-Linux_x86-3.0.0-beta29.run
./TeamSpeak3-Client-Linux_x86-3.0.0-beta29.run

```
it will extract it after you accept the license.

---

### Post by v1ad on 2010-09-13
what i did was rename the folder to TeamSpeak3 after it extracted then

sudo mv TeamSpeak3 /usr/share

and created a startup file in /usr/bin called teamspeak with this script

```


#!/bin/bash

export QT_PLUGIN_PATH=.
export LD_LIBRARY_PATH=".:$LD_LIBRARY_PATH"

cd /usr/share/TeamSpeak3/

if [ -e ts3client_linux_x86 ]; then
        ./ts3client_linux_x86 $@
else
        ./ts3client_linux_amd64 $@
fi


```

did sudo chmod 755 /usr/bin/teamspeak

and whenever you type teamspeak in console it will open it, or you can create a menu app

---

### Post by v1ad on 2010-09-13
also my sound works perfect in Ubuntu.

---

### Post by ArbiterOfTruth on 2010-10-29
Hey this worked for me. Thanks!

---

### Post by wolfar15 on 2012-09-07
> **denver said:**
> You will have to run it from a terminal. Go to applications-->accessories-->terminal and type in the following:

```
cd ~/Desktop
sh TeamSpeak3-Client-linux_x86-33.0.0-beta17.run

```Assuming that the file is on your Desktop of course. It will then ask you to agree to a license. Press enter to view the license, and then press "q" to quit the licence viewer. Type in yes to agree to the license (if you DO agree of course) and a new folder should be present on your desktop.

In that folder you should see:

ts3client_runscript.sh

Just double click that, and you should be good to go.

I got all the way to the agree to terms page it says it uncompressing but it gives me ..... and then goes back to the desktop line and i cant find the file anywhere any ideas?

---

### Post by mshaugh on 2012-11-25
When I run the "ts3client_runscript.sh" the following appears:
> 
Do you want to run "ts3client_runscript.sh", or display its contents?

"ts3client_runscript.sh" is an executable text file.It gives me four options:
"Run in Terminal", "Display", "Cancel", and "Run"

When I click "Run" nothing happens.

---

### Post by wildmanne39 on 2012-11-25
If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.

---

