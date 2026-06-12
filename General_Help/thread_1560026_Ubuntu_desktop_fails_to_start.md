---
title: "Ubuntu desktop fails to start"
date: 2010-08-24
forum: General Help
---

### Post by Euticus on 2010-08-24
When Ubuntu boots, I get the following message:
"Could not update ICEauthority file /home/jim/.ICEauthority"

After I dismiss this message, I get
"There is a problem with the configuration server.(usr/lib/libgconf-4/gconf-sanity-check-2 exited with status 256"

Then the desktop fails to start.

What does this mean?

---

### Post by clrg on 2010-08-24
This means your GNOME configuration is messed up. The simplest solution is to create a new user.

The more complicated solution is to search for the error in the configuration files and correct it manually.
What happens when you log into a terminal (Alt+F1) and run 
```
gconf-sanity-check-2
``` manually? Does it say which files are corrupted?

---

### Post by Brackenn on 2010-08-26
Hi. I got the same problem. When I try to gconf-sanity-check-2 i get a command not found. I cut and pasted the command out of your post, so i know it wasn't a typo. Is there a way to to fix this? I can log in as another user, but i have a bunch of files i want to recover. this all started because and when i tried to change my password.

---

### Post by clrg on 2010-08-26
It looks like there is no such program. Stupid error message...

---

### Post by JBAlaska on 2010-08-26
Not sure what caused your problem, but this sometimes happens when you use sudo for graphical programs, to fix it:

Boot into recovery mode, Select "*Drop to root shell prompt*"
Enter:
```
chown jim:jim /home/jim/.ICEauthority
chmod 644 /home/jim/.ICEauthority
exit
```

Do a normal boot.

---

### Post by Brackenn on 2010-08-26
Hi. Clueless beginner here. How do I boot into recovery mode. Is that Where you cntrl+alt+f1? and How do I Select "Drop to root shell prompt"?
And Is it safe to assume that I put My username in where you have Jim?
Thanks in advance.

---

### Post by clrg on 2010-08-26
Press and hold shift immediately after powering on, this should bring you to the boot menu. Select recovery mode from there.

---

### Post by Brackenn on 2010-08-26
Okay. I got into the Root shell prompt and carefully typed in
 **chown william:william /home/william/.ICEauthority**
which returned:
**chown: cannot access '/home/william/.ICEauthority' :no such file or directory exists.**
 it retyped the line a couple of times, and I added a space between the **william/** and the **.ICEauthority**, but it sat that I couldn't access .ICEauthority same reason. What have i done to my poor profile? Can i rebuild this file? of copy one from the other users on the machine?
Thanks in advance,
Brackenn.

---

### Post by JBAlaska on 2010-08-27
To Brackenn, As far as I remember .ICEauthority recreates itself on boot if it does not exist. Some mention deleting .ICEauthority to cure the permissions error.

Try rebooting and entering: 
```
chown william:william /home/william/.ICEauthority
chmod 644 /home/william/.ICEauthority
exit
```
If your sure you typed it right and it still comes up "no such file or directory exists" after a reboot, Then I have no idea why it's not being re-created:(

---

### Post by Brackenn on 2010-08-27
This all started when I tried to change  my password. Keep in mins that this is my 'Family" computer and there is a different logon for everyone in the family, about 5 users. Mine is the only one that is screwed up. I tried to change my password. Now i get a chain of error messages. first one is 
"**could not update ICEauthority file /home/william/.ICEauthority**"
I close that, and then get: 
**"there is a problem with the configuration server. /usr/lib/libgconf2-4/gconf-sanity-check-2 exited with status 256)**
i close that, and get:
"**Nautilus could not create the following required folders:/home/william/desktop/, home/william/.Nautilus. please create these folders, or set permissions such that Nautilus can create them.**
And before you read that, and click 'ok' up popps :
**Record your Encryption Passphrase**
and no matter what you do, it just keeps asking for that over and over again. searched the forums for this, found a lot of conflicting advice.i have tried:
[B]chown user:user /home/user/.ICEauthority
chmod 644 /home/user/.ICEauthority
exit[/B]
 But it says that file doesn't exist.
I want to try this:
[B]1) reboot in recovery mode
2) select the option to "drop to root shell prompt with networking"
3) log in as my user. (Does not require the .ICEauthority file)
4) sudo apt-get install ubuntu-desktop[/B]
that I found here===>[http://ubuntuforums.org/showthread.php?t=1021106&page=2](http://ubuntuforums.org/showthread.php?t=1021106&page=2)
do you think that will blow away any files and wine setting I have on my profile?

---

