---
title: "ROOT user is slow Guest user is incredibly fast. How to fix?"
date: 2010-12-29
forum: General Help
---

### Post by Nitrozzy7 on 2010-12-29
Hello,
I created a Guest user with no root access and no admin rights and when I logged in as Guest I discovered that everything was working FAST (to my big surprise); and I'm talking from Firefox to Media Player to Flash. EVERYTHING!
Now, why is this happening and how can I make the original ROOT user that fast and reliable?
Note: I noticed the same change when I used to run on older versions of Ubuntu. Now I'm on 10.10

---

### Post by Nitrozzy7 on 2010-12-30
Well, no matter what I've tried since yesterday I couldn't managed to get my ROOT user to work faster. 
I've tried clearing all the chace and the cookies but it only worked for a caple of minutes. As soon as I loaded a flash game it all went south again.
It has to do something with the flash plug-in. But only when it comes to the Browser; Media Player, Amarok and other aplications still don't work as fast as the Guest user.
What's causing it? Any thoughts?

---

### Post by fibrebiz on 2010-12-30
I don't know but you shouldn't be working as root.

Do you refer to an administrator account as opposed to a guest account?

---

### Post by Nitrozzy7 on 2010-12-30
No I don't.
Why I shouldn't work as root?
It's the default account.
Anyway, I guess I should make one more user with full rights but not root access.

---

### Post by wilee-nilee on 2010-12-30
> **Nitrozzy7 said:**
> No I don't.
Why I shouldn't work as root?
It's the default account.
Anyway, I guess I should make one more user with full rights but not root access.

You need a password to use the super user privileges correct?

---

### Post by ottosykora on 2010-12-30
In fact no one should work as root, this is rather dangerous way of computer usage.
But if your operating system is ubuntu, then default account is definitely not root, but simple a restricted user. For special tasks where administrative rights are needed you will be prompted for password.

---

### Post by Nitrozzy7 on 2010-12-30
> **ottosykora said:**
> In fact no one should work as root, this is rather dangerous way of computer usage.
But if your operating system is ubuntu, then default account is definitely not root, but simple a restricted user. For special tasks where administrative rights are needed you will be prompted for password.

So, I'm guessing my original guess that I was using root, was wrong.
Yes. I am prompted for a password.
_Let me rephrase;_
The default user is working terribly slow compared to a new user which I created two weeks ago. I named it "guest". The new "guest" user has no Root access and no Administrative privileges (according to the check box I used to make it), 
NOTE: On the "guest" user I performed a task which required me to give the password I use when I perform admin tasks. I can't recall the task.
When I use the terminal from my default user to perform certain tasks I am prompted for a _sudo:_ password to which I give the admin password.
Sorry for the inconvenience; Hope I provided you with enough feedback.

---

### Post by Nitrozzy7 on 2010-12-31
So, what do I need to do in order to make it work just as fast?

---

### Post by Irony on 2010-12-31
Transfer your documents and files to the 'guest' and use that as 'root'... though root isn't actually root.

---

### Post by yetiman64 on 2010-12-31
> **Nitrozzy7 said:**
> So, what do I need to do in order to make it work just as fast?

Try creating a second account for yourself for "daily use". 

If you need to administer anything use the "Switch from" button on the Indicator applet and change to your current admin account.

Any files you need for daily use can be copied (or moved) to the new home folder from your current home folder. All normal use programs should be available to the new user account for you. Though you may have to adjust some settings (I'm thinking of Network Manager here) to make some services like wireless available to all users, this is done from your current user account.

Cheers.

---

### Post by Nitrozzy7 on 2010-12-31
Thnx I'll do what you're all suggesting, in fact I already thought about dealing with it this way. There's one thing though; I need to know what is the likely cause of this behavior from the default user. This is the reason for starting this thread.
Is there anything I can do that can help me understand the cause and maybe fix it?

---

### Post by Nitrozzy7 on 2011-01-01
So is there any?

---

### Post by jocko on 2011-01-01
One thing you could try is to get rid of some of the configuration files in your home directory (that's the hidden files and folders with names starting with a ".". Press Ctrl+H to see them).
As your problem seems general and not related to any one single application, my guess is that the problem is caused by something that is running all the time, such as some gnome component, compiz or pulseaudio, so you could try to delete the following folders (or move them to a new directory if you want to be able to restore them later):
.compiz
.config/compiz
.config/gnome-session/saved-session
.gconf
.gconfd
.pulse

Then force xorg to restart by pressing Alt+SysRq+K. A normal logout would probably allow the programs to re-write their configuration files from the ones in memory.
All the folders will be recreated automatically when you log in again, but should contain the default configurations which are the same as in your new "guest" account.

---

### Post by Nitrozzy7 on 2011-01-01
Simple as that!
Thnx!
It worked. :)

---

### Post by QLee on 2011-01-01
[QUOTE=Nitrozzy7]... I need to know what is the likely cause of this behavior from the default user. This is the reason for starting this thread.
...[/QUOTE]

So, now you also have the answer to this question, you had chosen to mis-configure something for that user.

---

### Post by Nitrozzy7 on 2011-01-02
> **QLee said:**
> So, now you also have the answer to this question, you had chosen to mis-configure something for that user.

Not as far as I realize. It's been like this since Ubuntu 8.04. But only now it became annoyingly slow.
Cheers!

---

### Post by QLee on 2011-01-02
Well Nitrozzy7, here's the logic I used.

There was a problem for a user.
The problem did not exist for a different user.
Delete the user configuration files for compiz, GNOME, pulse and with the default user configuration restored the problem no longer existed for the user.
The problem is likely related to a user configuration.

---

