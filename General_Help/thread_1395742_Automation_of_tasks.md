---
title: "Automation of tasks"
date: 2010-02-01
forum: General Help
---

### Post by GeeJay89 on 2010-02-01
Hello
 
As you can tell, im new to the forum so would like to say hello and a thank you for taking the time to make such a great referance site and community, it has been a big help so far and I hope in the future to return the favour.
 
Now, introductions aside, the problem. I have been tasked to setup a linux based machine to RDP into a windows platform. This is fine, it works perfectly, but it all has to be done manually.
 
The trouble arises when I try to automate the sequence, for example autorun RDP at bootup. There are many parts in which I wish to automate but I need to get the basics done first.
 
The following is how I wish to setup the system.
 
*Auto login to Ubuntu
*Auto start RDP and login
*Auto restart RDP connection if quit
*Lockdown the system where possible without conflicting with the autostart
 
I've tried to script it myself along with various other applications and nothing has been successful. I was able to autorun and login to RDP successfully but when I started to lockdown the system it all went a bit wrong.
 
The scenario for said machine is in the warehouse, displaying a database for orders. peripherals are required to sign off tickets etc and as such I cannot do away with them.
 
If anyone could provide some assitance on how to achieve the said goals, I would be most grateful.
 
**Note**: I've already tried creating a script and adding it to the start applications but as I said, it all went a bit wrong when I locked down the system.

---

### Post by HiImTye on 2010-02-01
what output are you receiving when it fails to work?

try running it in a shell until you figure out whats not working

---

### Post by GeeJay89 on 2010-02-01
It does not give an error as such, just simply dosn't run. I've even used the "Restore this desktop session at power on" function. But that is no use as if someone were to close the program, it would stay closed.
 
Im fairly knew to Ubuntu, so when you say shell im presumming you mean via sudo or as root user?

---

### Post by HiImTye on 2010-02-01
no, just in a terminal

never run anything as root unless you:
a) have to
b) know that you're doing something benign

you can choose 'run in shell' or w/e in the run, etc dialogs or you can run it from a shell initially. this will cause the output of the program to output to a shell

or, you can fork the output to a text file, if that would be easier to you, to do so add '> /path/to/file.txt' to your commands. i.e.

```
ls /usr/bin/ > $HOME/line1.txt
ls /root/ > $HOME/line2.txt
```

---

### Post by t4thfavor on 2010-02-01
shell means on the commandline.

I would be interested in viewing your script, just the parts that do work, I may be abpe to give you pointers on how to make it work.

---

### Post by GeeJay89 on 2010-02-01
It's really nothing at all. No sparkly bits and flashing lights, it just simple and should work.
 
>  #!/bin/sh
echo "Starting RDP session into Server"
rdesktop -k en-gb 192.168.0.11 -f -u *username* -p *password*
 
Obviously the italics have been substituted for anonymous information.
 
The script has been added to the start applications list and sometimes it works, but other times it does not.
 
Hope it helps explain the situation further.

---

### Post by undecim on 2010-02-01
Could it be that the network connection is not always there by the time the script starts? On my laptop the wireless connection doesn't start until I log in (obviously, it has to get the WPA key from my keyring)

But I don't know if that behavior is the same for wired connections, so I don't know if that is the problem (unless you are connecting via wireless, in which case I would say that it is definitely the reason your script only works sometimes.)

---

### Post by GeeJay89 on 2010-02-01
Unfortunatly it's wired and thus I think it rules out the option. But I did worry that id neglected such an obvious point. Thank you for pointing that out.

---

### Post by undecim on 2010-02-01
If you can run your script in a terminal at boot, that would help diagnose the problem. First, add the following lines to the end of your script:```
echo "rdesktop exited with status $?"
echo "press enter to exit"
read
```

Then use this as the command to start the script:```
gnome-terminal -e /path/to/script.sh
```where /path/to/script.sh is the path to your script.

that should run the command in a terminal, give us a little bit of diagnostic info, and make it so you can read the output before the terminal disappears

---

### Post by GeeJay89 on 2010-02-02
As nice as it was, the program simply ran and that was it, there were no outputs at all, just simply the RDP session. Running it is fine, but running it automatically on startup is another problem all together.
 
Please tell me if I did something wrong as I believe I have done. The code reads as follows:
 
> #!/bin/sh
echo "Startomg RDP session to Server"
rdesktop -k en-gb 192.168.0.11 -f
echo "rdesktop exited with status $?"
echo "press enter to exit"
read

---

### Post by undecim on 2010-02-02
The script looks fine. Have it run on startup as per the instruction in my previous post, and get a sample of the output from when it succeeds and a sample of the output when it fails.

---

### Post by GeeJay89 on 2010-02-02
Funnily enough I think I've solved my problem. I was having a play today to see if I could find any options and I found one. It was something to do with editing my profile and it gave the option of entering a boot command, so I put in:
 
> rdesktop -k en-gb 192.168.0.1 -u *username* -p *password*
 
To my suprise it worked, and whilst I was typing in the command I noticed a box that gave the option of restarting the command if it was closed. Therefore I ticked it in the hope it would work, and it did.
 
It's now doing everything that I had hoped it would and there is no way in which a user can gain access to Ubuntu desktop as it restarts the command if quit immediatly and reboots into terminal services. Which is great news, but when I want to change the password it's a different story. Is there anyway in which I can interupt the process of running the script? And also, does anyone recognise the application I used to set the start command? 
 
It mentioned something about Editing User Profiles, I need to re-access it to change the password as stated above. I believe it was listed under Control Panel somewhere, but I simply cannot find it at all.
 
Thank you for all your help so far, it's much appreciated. Just one more little bug to figure out then this problem is solved.

---

### Post by undecim on 2010-02-02
you must be running a version of Ubuntu before 9.10 (Smart move on your part if you stuck with the 8.04 LTS release). That sounds like something that would be in the old Login Window config.

So you are running rdesktop and absolutely nothing else then? If that's the case, you can start the Control Panel with this procedure:

[LIST=1]
[*]Press Ctrl+Alt+F1
[*]Log in as the user running rdesktop (note that you will not get any feedback while typing your password. Your password is completely invisible while you type it in the terminal)
[*]Run the command "export DISPLAY=' :0'"
[*]Run the command "gnome-control-center"
[*]Press Ctrl+Alt+F7
[/LIST]
And you should see your Control Panel.

If you do this a lot, you may want to add this to ~/.bashrc:```
if [ "x$DISPLAY" = "x" ]; then
 export DISPLAY=" :0"
fi
```This will allow you to skip step 3 in the procedure above.

---

