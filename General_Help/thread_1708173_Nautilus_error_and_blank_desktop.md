---
title: "Nautilus error and blank desktop"
date: 2011-03-16
forum: General Help
---

### Post by ARBAUM on 2011-03-16
I'm not sure how it started happening, but when I boot up I get three errors and then a blank desktop. I have seen similar problems on here but none of those threads has left me with a solution. I'm running Ubuntu 9.10

Here are my errors:

Could not update ICEauthority file /home/alex/,ICEauthority
(This one has been appearing for a while before the blank desktop problem started)

There is a problem with the configuration server.
(/usr/lib/libgconf2-4/gconf-sanity-check-2 exited with status 256)

Nautilus could not create the following required folders: /home/alex/Desktop, /home/alex/.nautilus.
Before running Nautilus please create these folders or set permissions such that Nautilus can create them

I'm pretty new to the command line, so I definitely need help trying to fix this.

Thanks!!

---

### Post by mssever on 2011-03-16
Sounds like your permissions are set wrong. Try ```
chmod 755 ~
```If that doesn't work, make sure your home folder is owned by your user (not, for example, root).

---

### Post by ARBAUM on 2011-03-16
When I try chmod 755 ~ I get back chmod: changing permissions of ' /': Operation not permitted

---

### Post by ARBAUM on 2011-03-16
how do I check/change the owner of the home folder?

---

### Post by mssever on 2011-03-16
Could you paste the exact command you typed along with the exact result? I can't see how the message you gave is possible. "~" is an abbreviation for your home directory. "/" is the root directory. They're two separate things.

There are many ways to find the owner of your home directory. One way is to type ```
ls -l /home
```
EDIT: This will also show whether your permissions are set correctly.

---

### Post by ARBAUM on 2011-03-16
Thank you, the result of 
ls -l /home was alex. 

As for chmod 755 ~ I get back exactly: 
chmod: changing permissions of `/': Operation not permitted

If it matters: the command line is started with alex@alex-laptop:/$

Thanks

---

### Post by mssever on 2011-03-16
Please paste the results of both commands. For the chmod, there's got to be a mistake somewhere. I don't think the output you mentioned is possible if you typed the command I gave you.

For the ls command, you reported the uninteresting info and omitted the relevant output. Please paste in the result.

For both posts, please also copy and paste the command that produced the results. Don't re-type it or summarize it. Copy and paste.

---

### Post by ARBAUM on 2011-03-16
I don't think I can copy and paste...I'm sending these messages from a different computer. I can't get the other computer into a working GUI (I'm stuck with a blank desktop), and because of that I can't get it online (or find any other way to copy and paste the data).

For the ls command, all that it showed me was alex on the next line, and the the line after that was just the default command line prompt. 

Sorry I'm not more helpful, but I don't know much about using the command line. I'm certain I typed everything exactly as it showed me on the other computer in the terminal.

Thanks, what do you think I should do from here?

---

### Post by mssever on 2011-03-16
If you had typed the command exactly, you would have gotten different results. For example, here's what I get:

```
scott-laptop:~$ ls -l /home
total 40
drwxr-xr-x  40 campmeeting sword  4096 2009-01-10 05:29 campmeeting
drwx------   2 root        root  16384 2008-06-12 11:43 lost+found
drwxr-xr-x 187 scott       scott 20480 2011-03-15 13:54 scott
```
If you don't get all those columns, you're typing it incorrectly.

---

### Post by ARBAUM on 2011-03-16
Ok, I was using a 1 instead of an l after the -, but with the l I get this:

total 4
drw-rw-rw- 87 alex alex 4096 2011-03-15 20:54 alex

then my default prompt.
Not sure if this matters, but my prompt starts with /$ while yours was ~$

I know this would be a lot easier if I could copy and paste, but thanks for sticking with it.

---

### Post by mssever on 2011-03-16
OK. The first column tells us that your home directory has global write permissions and no execute permissions. Many of the graphical components of a Linux system will refuse to run for security reasons if the home directory has global write permissions. And without execute permissions, programs can't access anything inside your home dir.

This command will fix things. Be sure to type it exactly. ```
sudo chmod 755 /home/alex
```

For an explanation, google Linux permissions and chmod.

---

### Post by ARBAUM on 2011-03-16
Sorry I did not see the second page :p When I typed that command it just showed my default prompt on the next line (after asking for password). Trying a restart now...

---

### Post by ARBAUM on 2011-03-16
Fixed! Thanks so much. Still have the ICEauthority error, but my gui is back and I will look for a solution to that before I post another thread.

Way to go!

---

### Post by mssever on 2011-03-17
Try deleting ~/.ICEauthority then logging in again. That should solve things.

```
sudo rm /home/alex/.ICEauthority
```

---

### Post by cinnamonspider on 2011-04-02
I'm having the same problem, but when I enter the chmod command I just receive this message: cannot access /home/kira: no such file or directory

---

### Post by hihihi100 on 2011-05-29
Hi there. I have EXACTLY this problem
 
[http://ubuntuforums.org/showthread.php?t=1769954](http://ubuntuforums.org/showthread.php?t=1769954)

---

### Post by hihihi100 on 2011-05-29
HELP ME PLEASE:
 
The ICEauthority file is owned by dexter:dexter, so is every file inside /home/dexter, now my troubles:
 
In the log in screen there are 2 users: Dexter(dexter) and Dexter(hihihi00) Dont ask why there are two, the most probably thing is that I, personally, f*cked it up, but I dont remember how: Both users have different passwords, and my aim is to migrate to Dexter(dexter) all the machine.
 
I selected Dexter(dexter), wrote the correct password and loaded Ubuntu 11.04, but the ICEauthority file update popup appeared again, so did, the ```
[FONT=Times New Roman][SIZE=3]There is a problem with the configuration server. (/usr/lib/libgconf2-4/gconf-sanity-check-2 exited with status 256)[/SIZE][/FONT]

```
 
My machine, if I log in as Dexter(dexter) is too limited: I can see the main menu, but I cannot access internet, libreoffice, not to any of my programs, I can switch users, or turn it off though, the wifi sensor works (my machine tells me there are available wifi networks in the area), I can see the weather and current time
 
Now, what is driving me nuts:
 
Top-right corner, the turn off button: below the options: lock screen, guest session, switch from dexter.. I see:
 
Dexter(hihihi100)
 
Losing pressure, whats is going on? Why do I read Dexter(hihihi100) when I logged in as Dexter(dexter)? I have very much valuable information in my machine, and it took me months to compile I dont know how many files from source
 
Please tell me that it can be fixed
 
MORE Information:
 
Luckily, I was able to access users and groups:
 
Dexter(dexter) custom account type
Dexter(hihihi100) administrator account type
 
Basic settings of group name dexter:
group ID: 1001,
group members: Dexter (not marked) and Dexter (unmarked too) there is no way for me to tell you which one of each is Dexter(dexter) and Dexter(hihihi100)
 
Advanced settings for Dexter(dexter):
 
home directory: /home/dexter
shell: /bin/bash
main group: dexter
user ID: 1001
 
user privileges: every item has been marked
 
Advanced settings for Dexter(hihihi100)
home directory: /home/hihihi100 (THIS DIRECTORY NO LONGER EXISTS)
shell: /bin/bash
Main group: hihihi100
user ID: 1000
 
User privileges: every item is marked
 
should I deactivate the user Dexter(hihihi100)? delete it?
 
Help please

---

### Post by Chenthu on 2011-07-28
I have the same problem as ARBAUM....but i treid what ever u have speciefied.... 

sudo chmod 755 ~ and every other thing... this is my problem in pasebin...please help me.. [http://paste.ubuntu.com/653847/](http://paste.ubuntu.com/653847/)

---

