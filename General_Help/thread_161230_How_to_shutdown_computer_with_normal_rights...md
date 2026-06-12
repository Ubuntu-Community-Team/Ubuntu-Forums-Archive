---
title: "How to shutdown computer with normal rights.."
date: 2006-04-16
forum: General Help
---

### Post by encompass on 2006-04-16
I am setting up my computer with lirc and want to have a feature to shutdown my computer with my remote... irexec is the program I need to use... but I can't shut the computer down without typing a root password.  Is there a way to do this without loosing too much security?

---

### Post by babalou on 2006-04-16
[QUOTE=encompass]I am setting up my computer with lirc and want to have a feature to shutdown my computer with my remote... irexec is the program I need to use... but I can't shut the computer down without typing a root password.  Is there a way to do this without loosing too much security?[/QUOTE]

use sudoers

edit sudo property and add your list of user as a list of trusted user to run shutdown command.
run "sudo visudo" to open sudoers file

then create user(s) alias and command alias. Then allow this user alias to run this command alias
Add the folllowing entries to file: 

# User alias specification
User_Alias TRUSTED = yb, anyOtherUser
# Cmnd alias specification
Cmnd_Alias SHUTDOWN = /sbin/shutdown, /sbin/halt
# User privilege specification
root ALL=(ALL) ALL     (default entry already present, do not add it again)
TRUSTED ALL=SHUTDOWN


Then when user yb wants to shutdown the system, "sudo shutdown -h now" (with his own password) should make it.
Note that if you want to limit the access to the command shutdown, you will have to make the entry in sudoers file more explicit about what's permitted.

yb

---

### Post by pitkali on 2006-04-16
Cool, though it'll still ask for a user's password, AFAIR. If you want real automation, you'll need one additional thing, like this:
```
TRUSTED ALL=**NOPASSWD:** SHUTDOWN
```

---

### Post by ububaba on 2006-04-16
[QUOTE=babalou]use sudoers

edit sudo property and add your list of user as a list of trusted user to run shutdown command.
run "sudo visudo" to open sudoers file

then create user(s) alias and command alias. Then allow this user alias to run this command alias
Add the folllowing entries to file: 

# User alias specification
User_Alias TRUSTED = yb, anyOtherUser
# Cmnd alias specification
Cmnd_Alias SHUTDOWN = /sbin/shutdown, /sbin/halt
# User privilege specification
root ALL=(ALL) ALL     (default entry already present, do not add it again)
TRUSTED ALL=SHUTDOWN


Then when user yb wants to shutdown the system, "sudo shutdown -h now" (with his own password) should make it.
Note that if you want to limit the access to the command shutdown, you will have to make the entry in sudoers file more explicit about what's permitted.

yb[/QUOTE]


To start my computer with normal rights, I tried to access /etc/sudoers by feeding 
"sudo visudo" to get rid of a syntax error in sudoers but this is the message I got:

[COLOR="DarkOrchid"]>>> sudoers file: syntax error, line 19 <<<
sudo: parse error in /etc/sudoers near line 19[/COLOR]

That is what I am supposed to correct but am now going round in circles. Is there 
any other way than running "[COLOR="DarkOrchid"]sudo visudo[/COLOR]"? I have already failed in using gedit.
Any suggestions how may one proceed further?

---

### Post by babalou on 2006-04-16
[QUOTE=ububaba]
[COLOR="DarkOrchid"]>>> sudoers file: syntax error, line 19 <<<
sudo: parse error in /etc/sudoers near line 19[/COLOR]
[/QUOTE]
It means one of your new entry is invalid. 
Could it be a "tab" character is required between the alias name (first word of line) and the actual value (value=something). I used tab but didn't mention this on my post

What's on line 19?

[QUOTE=ububaba]
"[COLOR="DarkOrchid"]sudo visudo[/COLOR]"? I have already failed in using gedit.
Any suggestions how may one proceed further?[/QUOTE]
you have to use visudo to edit the file (gedit is no good)

yb

---

### Post by ububaba on 2006-04-16
[QUOTE=babalou]It means one of your new entry is invalid. 
Could it be a "tab" character is required between the alias name (first word of line) and the actual value (value=something). I used tab but didn't mention this on my post

What's on line 19?


you have to use visudo to edit the file (gedit is no good)

yb[/QUOTE]

As I can not access System>Administration>Disks, I have no idea, what ugly characters
are housed on line 19. Can't even guess. As mentioned "visudo" also not letting me edit. 
Unless there is some other way out, I am stuck for the time being. Logging in recovery 
mode did not help either. Have not been able to find a trick to work my way around.

---

### Post by babalou on 2006-04-16
[QUOTE=ububaba]As mentioned "visudo" also not letting me edit[/QUOTE]
you might want to check vi syntax to know how to use visudo

---

### Post by babalou on 2006-04-16
[QUOTE=ububaba]
Unless there is some other way out, I am stuck for the time being. [/QUOTE]
If you want, attach the sudoers file (/etc/sudoers) to your next message, I will update it for you and post the resulting file.
Just tell me what the user names and expected permissions (if different from shutdown) are.

---

### Post by ububaba on 2006-04-16
[QUOTE=babalou]you might want to check vi syntax to know how to use visudo[/QUOTE]
Sorry to admit, never had to do anything with **vi,** hence am totally ignorant about it.:confused:

---

### Post by ububaba on 2006-04-16
[QUOTE=babalou]If you want, attach the sudoers file (/etc/sudoers) to your next message, I will update it for you and post the resulting file.
Just tell me what the user names and expected permissions (if different from shutdown) are.[/QUOTE]
Thanks **babalou** for the offer but my problem is that I can not read 
Places>Home Folder>etc>sudoers nor can I go via System>Administration>Disks
as I get this error message:

[COLOR="Gray"]Failed to run disks-admin as user root:
 Child terminated with 1 status[/COLOR]

I am in a fix.

---

### Post by aysiu on 2006-04-16
Although this will not tell you whether you have an invalid line or whatnot, I know this command will let you edit the /etc/sudoers file to see what's wrong: ```
sudo nano /etc/sudoers
```

---

### Post by babalou on 2006-04-16
[QUOTE=ububaba]
[COLOR="Gray"]Failed to run disks-admin as user root:
 Child terminated with 1 status[/COLOR][/QUOTE]
You have to be root to read this file. If you still want to post file, copy it into your home directory 
```
sudo cp /etc/sudoers ~

```
then attach it to your next message.

---

### Post by ububaba on 2006-04-16
[QUOTE=babalou]You have to be root to read this file. If you still want to post file, copy it into your home directory 
```
sudo cp /etc/sudoers ~

```
then attach it to your next message.[/QUOTE]
This is the outcome:

[COLOR="RoyalBlue"] sudo cp /etc/sudoers ~
>>> sudoers file: syntax error, line 19 <<<
sudo: parse error in /etc/sudoers near line 19[/COLOR]

---

### Post by babalou on 2006-04-16
[QUOTE=ububaba]This is the outcome:

[COLOR="RoyalBlue"] sudo cp /etc/sudoers ~
>>> sudoers file: syntax error, line 19 <<<
sudo: parse error in /etc/sudoers near line 19[/COLOR][/QUOTE]

I found a link which explains how to get access to the corrupt sudoers file and fix it: [http://www.ubuntuforums.org/archive/index.php/t-140852.html]("http://www.ubuntuforums.org/archive/index.php/t-140852.html").

So basically, you follow the instruction to get access to this limited environment with bash shell. From there run again visudo, go to line 19 (using arrow keys) and press "dd" (to delete line). Then press "Esc", then "wq". If visudo complains about another invalid line, position the cursor on this line and press "dd" to get rid of it .. and so forth.
When "wq" closes visudo without error/warning message, you're good to restart your machine (Ctr+Alt+Suppr). At least you'll be back to a working configuration.

yb

---

### Post by ububaba on 2006-04-17
[QUOTE=babalou]I found a link which explains how to get access to the corrupt sudoers file and fix it: [http://www.ubuntuforums.org/archive/index.php/t-140852.html]("http://www.ubuntuforums.org/archive/index.php/t-140852.html").

So basically, you follow the instruction to get access to this limited environment with bash shell. From there run again visudo, go to line 19 (using arrow keys) and press "dd" (to delete line). Then press "Esc", then "wq". If visudo complains about another invalid line, position the cursor on this line and press "dd" to get rid of it .. and so forth.
When "wq" closes visudo without error/warning message, you're good to restart your machine (Ctr+Alt+Suppr). At least you'll be back to a working configuration.

yb[/QUOTE]

I had ended up adding a line [COLOR="RoyalBlue"]adduser ububaba adm[/COLOR] in **sudoers** which was causing all the 
trouble. I was able to remove it while at the root level, still in CLI, from the** sudoers** file. 

All seems to be perfect. Thanks each and eveyone of you for the much needed help.:D

---

### Post by encompass on 2006-04-17
[QUOTE=babalou]you might want to check vi syntax to know how to use visudo[/QUOTE]
visudo uses what ever your default editor is... in my case and in probably many peoples cases... it is nano.  so it just is a name.  But I was worried to as I never used vi but stick to nano and emacs.

PS and thanks to everyone who helps me... it works great now.  I can now shutdown my computer with my cellphones IR transciever. muhahah.

---

### Post by encompass on 2006-08-07
I made that mistake... I created a root acount in recovery mode and logged in as that... then using visudo I got in to edit the file and fix my problem.  you could also do the fix with a boot cd.
lastly.  visudo uses your default editor, odds are it is nano.8)

---

