---
title: "Start teamspeak with a desktop Shortcut"
date: 2010-04-07
forum: General Help
---

### Post by hugo007 on 2010-04-07
Hello all 
I'm new at ubuntu and I have a question.
I download the new version of teamspeak since using the synapitcs install me an older version.
my problem is to start the new teamspeak I have to go to the console and type ./starterscript_of_teamspeak 
Is there anyway to put a botton icon to make me this instead using the console to start it ?
I also have this problem with thunderbird
Thanks all for your time

---

### Post by cavh on 2010-04-07
Welcome to Ubuntu, hugo007, hope you'll be happy with us :) !

To create a shortcut, you can rightclick a blank section of the menu bar at the top of your screen (see screenshot below), then choose 'Add to panel', then either 'Application Launcher' or 'Custom Application Launcher' and follow the prompts. Once you've done this, you can drag the shortcut from the menu bar to your desktop. This will create a 'button icon' as you call it.

---

### Post by hugo007 on 2010-04-08
thanks for reply, I tryed do what you tell me to do but I only can add aplications that is already installed on ubuntu like amsn for exemple.perhaps I 'm doing something wrong:( Or I explain me not very well, lets assume I download the thunferbird from a tar.gz file and I decompress it to my Documents.Inside the folder there is a thunderbird file wich to run it I need to go to console and type ./thunderbird.
With your tip when I try to add this new appl. it is not in the list (like expected) and I can´t find a way to add it there
Does I have to compile thunderbird for that works as a command?
Thanks for your time

---

### Post by cavh on 2010-04-09
Okay: choose Custom Application Launcher (see screenshot 1 below), click Add, then enter a name (see screenshot 2 below, in which I put the name 'Thunderbird') and then click the Browse button. Browse to your Thunderbird executable file and that should be enough. 

If you cannot determine which file is your Thunderbird executable, then open a terminal, navigate to the Thunderbird folder and then type this code. Then reply to me with the output from this command.

```
ls -lart
```

---

### Post by Miscni on 2010-04-23
Hi all

I just tryed to do, what you showed on the Screenshots.

The only that happens for me, is that the Terminal shows up, for about 1 sec, and after that it closes down again. so it didn't work, sad to say.

But I have 2 functional files, in my TS3 Folder

"ts3client_runscript.sh" which start the "ts3client_linux_x86"
and I have a "Update"

Update and ts3client_runscript.sh is actaully the only 2, that really works.

I'm also pretty new to Ubuntu, and I really appriciate the help you have already shown.

Cheers

---

### Post by themusicalduck on 2010-04-23
You could try putting sh before the path to the script. Assuming you did as cavh said then the path should be already in the launcher and you just need to put sh before it.

So it would be like this ```
sh /path/to/ts3client_runscript.sh
``` Alternative you could just try and run the ts3client_linux_x86 directly by browsing to that file instead. You won't need the sh in that case.

---

### Post by Miscni on 2010-04-23
I just tryed what you suggested, but it didn't work.

But the "ts3client_runscript.sh" had those information here.

```
#!/bin/bash

export LD_LIBRARY_PATH=".:$LD_LIBRARY_PATH"

if [ -e ts3client_linux_x86 ]; then
    ./ts3client_linux_x86 $@
else
    ./ts3client_linux_amd64 $@
fi
```

Dont know if it means anything, but I still cant use the Launcher, and besides.
if we get this here to work, then I have another issue, that I'm trying to fix also.

but 1 thing at the time.

and thank you, for trying to help me out.

cheers

---

### Post by hugo007 on 2010-04-23
> **Miscni said:**
> I just tryed what you suggested, but it didn't work.

But the "ts3client_runscript.sh" had those information here.

```
#!/bin/bash

export LD_LIBRARY_PATH=".:$LD_LIBRARY_PATH"

if [ -e ts3client_linux_x86 ]; then
    ./ts3client_linux_x86 $@
else
    ./ts3client_linux_amd64 $@
fi
```Dont know if it means anything, but I still cant use the Launcher, and besides.
if we get this here to work, then I have another issue, that I'm trying to fix also.

but 1 thing at the time.

and thank you, for trying to help me out.

cheers
I'm also still have this issue.For now I am starting the teamspeak by going to the console but now I have found another problem, I cant get my sound settings well .
I dont see how can I put micro working since I already try all the input devices and none works

---

### Post by Miscni on 2010-04-30
Hi all

Found something that actaully worked for me, but I cannot take the credit for it. 

The user who made this, should really get the credit for this. Hi name is MarcusW, so please remember to Thank him, on the webiste

But here is the way you do it.

Here is a simple shell script that will do it. If you aren't familiar  with shell scripts, I'd google it. But I will try to explain.

You will open a text editor like kwrite or gedit, and put the code in,  replace YOURUSERHERE with your username. Also edit the location as it  reflects where you have the client folder:
```
#!/bin/sh
cd /home/YOURUSERHERE/TeamSpeak3-Client-linux_x86/
./ts3client_runscript.sh
```When you save it, you need to make sure to call it something like  TameSpeak3 or TeamSpeak3.sh... either will do.

Now you need to give it permission to run, so go to you console and go  to the directory where you put the file and type this:
```
chmod 755 TeamSpeak3
```if you put the .sh at the end, put that in that line as well. now when  you double click the shellscript, it should bring up TS3 without the  console/terminal.

Please remember to thank Marcus for it.
Link here is add here : [http://forum.teamspeak.com/showthread.php?p=237606#post237606](http://forum.teamspeak.com/showthread.php?p=237606#post237606)

Cheers all

---

### Post by ToxicBurn on 2010-05-01
I am trying to get Ubuntu to add teamspeak 3 to the repos so this will not be a problem 

I have filed a bug report hope they will do this and get rid of the old Teamspeak 2 thats in there now.

Link to the Teamspeak 3 request below.
[https://bugs.launchpad.net/ubuntu/+bug/572853](https://bugs.launchpad.net/ubuntu/+bug/572853)

---

### Post by Miscni on 2010-05-01
Well TS2 was a okay piece of software... 
But I do understand, why you are doing this. So if I can help out in any way, then please let me know.

Cheers

---

### Post by supermorph on 2011-03-25
> **ToxicBurn said:**
> I am trying to get Ubuntu to add teamspeak 3 to the repos so this will not be a problem 

I have filed a bug report hope they will do this and get rid of the old Teamspeak 2 thats in there now.

Link to the Teamspeak 3 request below.
[https://bugs.launchpad.net/ubuntu/+bug/572853](https://bugs.launchpad.net/ubuntu/+bug/572853)

not to offend you intensions,
but can i kindly request you make a slight change?

e.g ask them to put ts3 as a seperate option in the repo rather than remove teamspeak 2

i ask because i use both two and three, and i would be slightly mortified
if they removed ts2 support from apt-get lol

ill show you how i use myne, so u can grasp im not trying to be cheeky :-p

[http://ubuntuforums.org/showthread.php?p=10593783#post10593783](http://ubuntuforums.org/showthread.php?p=10593783#post10593783)


kind regards,
supermorph

---

