---
title: "How does the system shutdows?"
date: 2010-03-06
forum: General Help
---

### Post by hakermania on 2010-03-06
It isn't possib;e to shutdown via the command "shutdown" because it requires root priviliges. So, how does it shut down?

---

### Post by Martin Witte on 2010-03-06
```
sudo shutdown -h now
```
you need root priviliges

---

### Post by ssam on 2010-03-06
gdm (the login screen) is running as root.

---

### Post by Sef on 2010-03-06
Moved to General Help.

---

### Post by wojox on 2010-03-06
```
sudo poweroff
```

```
sudo halt
```

Works as well

---

### Post by realzippy on 2010-03-06
> **hakermania said:**
> It isn't possib;e to shutdown via the command "shutdown" because it requires root priviliges. So, how does it shut down?

...what he wants to know is why you not need root password when just clicking the shutdown icon in the panel.

---

### Post by uRock on 2010-03-06
> **realzippy said:**
> ...what he wants to know is why you not need root password when just clicking the shutdown icon in the panel.

That is a good question. Maybe in some places, such as the workplace, the shutdown option is removed so that only an admin can shut down the system. Just saying.

---

### Post by hakermania on 2010-03-06
Well, When I click on my username and then "Shut Down..." a command runs and doesn't require root priviliges for sure, because password isn't required!
Which is this command?[IMG]http://img26.imageshack.us/img26/9514/screenshotubuntuforumsr.png[/IMG]

---

### Post by falconindy on 2010-03-06
It's not a command, persay. You're given the ability to shutdown the computer as a normal user through ConsoleKit. ConsoleKit provides extra privileges to a user sitting at the console.

---

### Post by hakermania on 2010-03-07
Hmmm....Is it possible to make a shortcut in my desktop which with double click has th command to shut down the system from this KonsoleKit?

---

### Post by realzippy on 2010-03-07
You could give "shutdown" superuserflag with:

[B]sudo chmod +s /sbin/shutdown
[/B]

and then create a starter on the desktop with the command:

[I]shutdown -h now
[/I]
Disadvantage on multiusersystem is that every user could shutdown even when other users are still logged in.
Smarter would be adding your user and shutdown-h to the sudoers file:

**sudo visudo**

And add to the file:

[I]username ALL=(root) NOPASSWD:/sbin/shutdown -h now
[/I]

replace *username* with your username.

---

### Post by hakermania on 2010-03-07
Well, actually I did this but still it requires root priviliges....See below the pictures:

1)[IMG]http://img709.imageshack.us/img709/394/screenshotfr.png[/IMG]

2)[IMG]http://img709.imageshack.us/img709/789/screenshot1we.png[/IMG]
....I edited with nano and I saved it normally....
Did I do something wrong???

---

### Post by realzippy on 2010-03-07
To be honest,I myself use the first solution I suggested;it is only me who is logged in or my test users...so I do not care about.

Maybe,if still trying second solution,this helps:

[http://ubuntuforums.org/showpost.php?p=5678436&postcount=17](http://ubuntuforums.org/showpost.php?p=5678436&postcount=17)

---

### Post by hakermania on 2010-08-20
Well, I would like actually to know the exact command that shutdowns the PC from this ConsoleKit.... Is this possible?

---

### Post by dagdeniz on 2010-08-20
I don't understand how Gnome deals with HAL and policykit/consolekit, so I don't know how such a shortcut would be. 
For your changes in the sudoers file, everthing seems allright but what you've done is telling the computer not to ask you a password if you use sudo for shutting down the computer. I mean, you should say ```
sudo shutdown -h now
``` instead of shutdown -h now.

---

### Post by hakermania on 2010-08-20
Yes but you didn;t answer me..And as I have understand nobody can answer to this Simple Question:

HOW DOES THE F#CK13$ SYSTEM SHUTDOWNS WITHOUT THE USE OF ANY PASSWORD???????

---

### Post by Bachstelze on 2010-08-20
gdm is running as root, it doesn't need a password to shut down the system.  No need to curse in all caps.

---

### Post by ratcheer on 2010-08-20
I like the old-style UNIX init commands, "sudo init 6" to restart and "sudo init 0" to shutdown and power off the machine. Old habits die slowly.

Tim

---

### Post by QLee on 2010-08-20
[QUOTE=Bachstelze]gdm is running as root, it doesn't need a password to shut down the system.  [/QUOTE]

hakermania, you were told this in post 3 of this thread but I guess it wasn't what you wanted to hear.

[QUOTE=Bachstelze]No need to curse in all caps.[/QUOTE]

+1 Acting petulant is not an effective method of getting useful help and it often attracts unwanted comments or cause people who could help you to to ignore your question..


hakermania, 
What is it that you are actually trying to accomplish, what is the use you want to put to the "command", perhaps there is a way if you state your ultimate goal.

---

