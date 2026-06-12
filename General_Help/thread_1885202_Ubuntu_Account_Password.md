---
title: "Ubuntu Account Password"
date: 2011-11-22
forum: General Help
---

### Post by dkizzy on 2011-11-22
Hi all, I am fairly new to Ubuntu so please forgive my basic but essential question. Upon installation I created a password. Earlier today I decided to delete my password. Under the account settings it shows in the password field none. When I try to click the lock to be able to modify settings by unlocking it prompts me for a password. I tried the password that I had before deleting it, but it does not work. When it says none in the password listing, does it create a default password? I did some brief searching and saw that I might have to use the root password. Any help would be greatly appreciated. I have been enjoying Ubuntu for numerous reasons and just need to fix this little issue I self inflicted. Thanks!

---

### Post by ajgreeny on 2011-11-22
There is no root password in ubuntu unless you set one after installation, and I think that is unlikely as you would know what to do if you had done that.

Why did you try to delete your password?  It seems a strange thing to want to do, but I suppose you may have reasons for that.

However, I think the best thing you can do is follow the instructions in this link:-
[http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword)

---

### Post by newbiedeb on 2011-11-23
I have the same problem. After upgrading to 11.10 a week or two ago, it was asking for the password to do anything so I turned it off.  Then it would only ask when I first started the netbook and it accepted my original password.
A couple of days ago, it started asking for a password to do updates or install new apps.  It doesn't recognize my password (but it is still fine with it at original startup).
I have tried the link suggested above but it says that the password wasn't successfully changed.
Everything else is working fine, and since it recognizes the password for startup, I can continue to use everything--I just will never be able to update or install new apps.
Very frustrating so I would be grateful for any suggestions...(please don't assume I know anything about terminal and skip any steps  :( )

Thanks!

---

### Post by newbiedeb on 2011-11-23
I found this in an older post:

> **goodyboody said:**
> Thanks You are a life saver..See I knew there  must be easier solution no need to go crazy with live cd and crazy  commands.
Simple Press CTRL ALT F1 
Type passwd
Enter your new password
Press CTRL ALT F7
enjoy..thanks..goes to..^^:popcorn:

It worked for me....the CTRL ALT F1 shortcut didn't do anything on my Dell netbook so I accessed terminal (In accessories) and then followed the rest of the steps ("exit" will get you back out if CTRL ALT F7 doesn't work).  Also, nothing will show up when you type your password and then confirm it.

Now I have to type in my password every time I turn around again but at least I have control!

---

### Post by jharris1993 on 2011-11-27
> **newbiedeb said:**
> I found this in an older post:



It worked for me....the CTRL ALT F1 shortcut didn't do anything on my Dell netbook so I accessed terminal (In accessories) and then followed the rest of the steps ("exit" will get you back out if CTRL ALT F7 doesn't work).  Also, nothing will show up when you type your password and then confirm it.

Now I have to type in my password every time I turn around again but at least I have control!

I am posting here since others may have this issue too.

I suspect rather strongly that this is - or should be - a bug.

Issue:  Started a HP laptop (though I suspect any computer would do this) into the Live CD to do a disk image of a multi-boot Windows/'nix box.

While the image was being spooled off to a USB drive, I began working on another system.  Eventually I went back to the Ubuntu Live system and it had gone into "screen-saver" mode.  Upon returning from screensaver it wanted a password - and nothing worked!

Issue:  If the live CD is supposed to boot and start w/o a password, why does it request a password on return from screen-saver?  :confused:  IMHO, this represents a HORRID user experience, especially if the user is not exactly a bleed-edge Ubuntu/'nix sysadmin.

Workaround:
The CTL-ALT-F1 solution worked for me, I just ran "passwd" and supplied a new password.  Returning to the graphical screen then allowed me to login.

1.  Please pass this around.

2.  Shoot whoever had this brainstorm!

What say ye?

Jim ()JR)

---

### Post by oldtimer7777 on 2011-11-27
The quickest way to reset your password would be to drop to root in the recovery console on boot and do a password change for whatever user you need.

> **jharris1993 said:**
> I am posting here since others may have this issue too.

I suspect rather strongly that this is - or should be - a bug.

Issue:  Started a HP laptop (though I suspect any computer would do this) into the Live CD to do a disk image of a multi-boot Windows/'nix box.

While the image was being spooled off to a USB drive, I began working on another system.  Eventually I went back to the Ubuntu Live system and it had gone into "screen-saver" mode.  Upon returning from screensaver it wanted a password - and nothing worked!

Issue:  If the live CD is supposed to boot and start w/o a password, why does it request a password on return from screen-saver?  :confused:  IMHO, this represents a HORRID user experience, especially if the user is not exactly a bleed-edge Ubuntu/'nix sysadmin.

Workaround:
The CTL-ALT-F1 solution worked for me, I just ran "passwd" and supplied a new password.  Returning to the graphical screen then allowed me to login.

1.  Please pass this around.

2.  Shoot whoever had this brainstorm!

What say ye?

Jim ()JR)

---

### Post by dkizzy on 2011-11-29
Thanks everyone for your responses. The reason I took the password off was because I was using this at a school and wanted to let the faculty try out ubuntu without needing my password to login to the desktop.

When I do the ctrl alt f1 it asks me for the login and then a password. I tried using the login name (HP Laptop) and then typing passwd for the password prompt. What step am I missing? It didn't work for me.

---

### Post by newbiedeb on 2011-12-03
Ctrl Alt F1 didn't wasn't set up to take me to Terminal on my netbook--I had to find it in Apps.
It didn't ask me to log in...I just typed "passwd" and then put in my new password and then confirmed it when asked.  Then I just typed "exit" to close Terminal.  Nothing will show up as you are typing your password until you hit Enter, then it will go to the next line..
If you aren't sure of your user name, you can find that out in terminal as well. Type:
ls /home  (That is a lowercase L and there is a space before / )
My user  name wasn't the same as my account name.
Sorry for my "low tech" instructions!  
Good luck!

---

### Post by oldos2er on 2011-12-03
> **dkizzy said:**
> When I do the ctrl alt f1 it asks me for the login and then a password. I tried using the login name (HP Laptop) and then typing passwd for the password prompt. What step am I missing? It didn't work for me.

Try [http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword)

---

### Post by newbiedeb on 2011-12-03
The psychocats fix didn't work for me (went through all the steps and, at the end, it said that the password change wasn't successful).
Changing it in terminal did solve the problem for me though.

---

