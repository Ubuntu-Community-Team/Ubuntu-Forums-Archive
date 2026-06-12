---
title: "auto-sudo script"
date: 2011-04-20
forum: General Help
---

### Post by thomas515 on 2011-04-20
Ok so I've been trying to get a script to run without entering the sudo password.  I've tried several methods.  So far the best I've come up with is this top start the GUI

#!/bin/bash
sudo service gdm start
echo $PASSWORD

this prompts me for a password the first time only then after that I can just run the script fine until I reboot.  What confuses me is another script I have for a quit restart

#!/bin/bash
sudo shutdown -r now
echo $PASSWORD

This script runs fine from the start.  It never prompts for a password.  I have a total shutdown version of the same script that behaves just like the GUI start. 

Any ideas on what I'm doing wrong or suggestions on how to remedy this situation would be greatly appreciated.

---

### Post by ttshivers on 2011-04-20
Type ```
sudo -t
``` and you will only have to type in your password once.  You will be then logged in as root.  Be careful when logged in as root.  You can then run commands without sudo and without typing in your password.

---

### Post by thomas515 on 2011-04-20
is there a way to have it automatically reference my password  or at least only run as root for these commands?

---

### Post by Crusty Old Fart on 2011-04-20
Here's the safest way I've found to do it: [post=10317361]See This Post[/post]

---

### Post by thomas515 on 2011-04-21
Thanks a lot.  that did the trick.

---

### Post by Crusty Old Fart on 2011-04-21
You're mighty welcome. Glad you liked it.

---

### Post by DaithiF on 2011-04-21
for whatever its worth I don't like Crusty's approach ... its an example of [http://en.wikipedia.org/wiki/Security_through_obscurity](http://en.wikipedia.org/wiki/Security_through_obscurity) ... you are relying on an attacker not knowing about the 'batman' backdoor to root privileges.

the OP's requirement of having sudo run a script without the need for a password is catered for specifically by sudo/sudoers, and its very straightforward to configure:
```
sudo visudo

```and add the line:
```
%admin ALL = NOPASSWD: /path/to/your/script

```
and save ... now anyone in the admin group can execute the script via sudo without the need for a password.

---

### Post by Crusty Old Fart on 2011-04-21
> **DaithiF said:**
>  ... you are relying on an attacker not knowing about the 'batman' backdoor to root privileges.
Oh most venerable DaithiF:

With all due respect, Sir, it seems to me that in order for an attacker to discover batman, he'd have to have already busted through the front door. And if he can do that, he can build himself as many back doors as his sweet little heart desires.

Right?

And just to make matters worse, here's another shocker: I'm also relying on an attacker not knowing any of the users' passwords (gasp!) :cool:

---

### Post by DaithiF on 2011-04-21
> **Crusty Old Fart said:**
> With all due respect, Sir, it seems to me that in order for an attacker to discover batman, he'd have to have already busted through the front door. And if he can do that, he build himself as many back doors as his sweet little heart desires.

Right?

no, if I sit down at your terminal one of the first things I'll do is:
```
sudo -l

```to see what (hopefully) interesting sudo privileges I may have.

With your batman setup I'll see this:
```
User dave may run the following commands on this host:
    (ALL) ALL
    (batman) NOPASSWD: ALL

```
Interesting ... so I can sudo into the batman user without a password, so next lets see what this batman user can do:
```
sudo -U batman -l

```and I see 
```
User batman may run the following commands on this host:
    (ALL) ALL
    (ALL) NOPASSWD: ALL

```
and the game is up.  None of this requires knowing any password.

I think the point here is that you should grant the mininum privileges necessary to get the job done.  If theres a single script that you want to be able to run as root without entering a password, then configure sudoers to do just that, and no more.
 

[/QUOTE]

---

### Post by Crusty Old Fart on 2011-04-21
> **DaithiF said:**
> no, if I sit down at your terminal one of the first things I'll do is:
...
~ chop ~
...
and the game is up.  None of this requires knowing any password.


What?...How are you going to issue any of the commands you posted without first logging in with my password?. Unless you're assuming you sit down at my terminal after I had already logged into it and surrendered my seat to you, in which case you'd have already been allowed through the front door.

Regardless, why bother jumping through all those hoops when you could just disconnect my box, schlep it out to your truck, and drive off with it?

Once you have my machine, and are sitting comfortably in front of it at home, without the concern of being interrupted by me leveling a .44 Magnum revolver at the back of your head, you'd have plenty of time to drop a LiveCD into the drawer and have at anything you want. :cool: Even if it wasn't a Linux box, you could access the Windoze drives (for example) from the LiveCD.

It seems to me that you're using a scenario, in which the machine is completely vulnerable to anything, to discredit the batman sudo solution, which is kind of over the top, don't you think? Especially considering that your sudo solution provides no protection in this case either.

> **DaithiF said:**
> I think the point here is that you should grant the mininum privileges necessary to get the job done.
In general, I agree with you on that point.

> **DaithiF said:**
> 
If theres a single script that you want to be able to run as root  without entering a password, then configure sudoers to do just that, and  no more.
 
Okay, for a single script, I agree with that as well.

However, I developed the batman solution because I was dealing with dozens of scripts that I wanted to run without a password and knew that I would have more in the future. My intent was to find a safe way to embed sudo commands in my scripts, have them run without a password, and eliminate the need to manually edit the sudoers file so often. I never intended the batman solution to protect my machine from scenarios that leave it vulnerable enough to be stolen. For that, I have firearms. :cool:

Looking forward to any further comments you may have. Perhaps I'm missing something.

Thanks for taking the time to reply to my posts.

All the best, 

Crust

---

### Post by DaithiF on 2011-04-21
Crusty, with respect I think theres a slight flaw in your reasoning here.  The reason its worthwhile separating our root privileges from normal user privileges at all is based on the possibility that an attacker may gain access to your users account.  The point being that if this happens, at least you have limited their access to root to prevent more damage being done.

If you are 100% confident that no-one / no-thing can gain a shell prompt as your user on your machine, then may I ask why you require a sudo password for your regular user in the first place ... ie. why not just cut out the batman middleman?  The answer is that to be that confident you would basically need to have no network connections in or out of your machine, and have it completely physically secured too.  So there likely is a real (though small) risk of your user account being hacked, and my point is that the batman trick doesn't add any significant extra security because it is discoverable with 2 simple commands.

---

### Post by hwttdz on 2011-04-21
Second the edit the sudoers file as DaithiF suggests.  Though we're getting to the single user system vs multi-user system question.  If you have a multi-user system you need to be more careful than if you have a single user system.  Sounds like you're describing a single user system.  The catch is, that a single user can use a multi-user system well, but if you put multiple users on a single user system bad things are likely to happen.

---

### Post by Crusty Old Fart on 2011-04-21
> **DaithiF said:**
> Crusty, with respect I think theres a slight flaw in your reasoning here.
It's probably more than a "slight" flaw.

> **DaithiF said:**
> 
The reason its worthwhile separating our root privileges from normal user privileges at all is based on the possibility that an attacker may gain access to your users account. The point being that if this happens, at least you have limited their access to root to prevent more damage being done.
Hmmmmm...hmmmm...So, now we're not talking about and attacker sitting down at my terminal anymore. He's coming at me remotely. Okay. That changes things a bit. Thanks for redirecting my thinking.

> **DaithiF said:**
> If you are 100% confident that no-one / no-thing can gain a shell prompt as your user on your machine,...
Nope...Other than being sure that some day I'm going to die, I'm not 100% confident of anything anymore, and doubt I ever will be.

> **DaithiF said:**
> ...then may I ask why you require a sudo password for your regular user in the first place ... ie. why not just cut out the batman middleman? The answer is that to be that confident you would basically need to have no network connections in or out of your machine, and have it completely physically secured too. So there likely is a real (though small) risk of your user account being hacked, and my point is that the batman trick doesn't add any significant extra security because it is discoverable with 2 simple commands.

Well...since you asked, the real answer for me is that I had mistakenly assumed that with my user account being downgraded all the way to a desktop user, there would be no way the batman user could be discovered by a remote attacker gaining access to my user account. Obviously, you did a fine job of blowing that assumption completely out of the water with 2 simple commands. Schidt...I'm screwed!

Now I need to re-think the whole damned deal. A sexy trick in sudoers that I might use to do what I want is not immediately obvious to me. Hopefully, I'll come up with something better within the next couple of days. If I do, I'll post it in this thread with hopes that you might expose any holes I've left open. 

Thanks for setting me straight. I thought I might learn something when you showed up. You never disappoint.

I need to spend some time with my nose buried in the man pages for a while now.

Thanks again for everything DaithiF, especially your patience with me.

Sincerely appreciative,

Crusty

---

### Post by Crusty Old Fart on 2011-04-22
To DaithiF:

I think I've finally figured a few things out. So, if you would kindly read through this post and let me know where my thinking may still be off the mark, I sure would appreciate it.

To start with, let's assume I'm logged into my Linux box as user: crusty. And let's say I'm grudgingly paying my bills online when some butthead attacks my system and gains access to my crusty session. So, now he's in without ever having to enter my password.

That's the threat. Right?

So, now he wants to raise holy hell and enters:
```

sudo -i

```But he gets nowhere with that because he needs to supply the system password to elevate his privileges to root.

So, he comes to this thread, reads your posts, and learns that he can become root with the following three commands:
```

sudo -l
sudo -U batman -l
sudo -u batman sudo -i

```And then I'm totally screwed. Right?

At first, I couldn't figure out how he was able to get the first "sudo -l" command to work without entering the password to elevate his privileges to root. After poking around in the sudoers man page, I found the following reason on line 243:
> 
By default, if the NOPASSWD tag is applied to any of the entries for a user on the current host, he or she will be able to run sudo -l without a password.
Additionally, a user may only run sudo -v without a password if the NOPASSWD tag is present for all a user's entries that pertain to the current host.  This behavior
may be overridden via the verifypw and listpw options.
Well...because I had the following entry in my sudoers file:
```

crusty       ALL=(batman)       NOPASSWD: ALL

```It left the "sudo -l" command wide open.

But if I could lock down the "sudo -l" command tight enough so that it would require the same system password required by "sudo -i" then neither of the following commands:
```

sudo -l
sudo -U batman -l

```would pose any greater security risk than "sudo -i" does. Right?

I didn't think they would. So, I tried to make it happen.

I added the following line to my sudoers file in order to force the password requirement for "sudo -l":
```

Defaults  listpw

```And then I thought if I posted that as the final solution, you'd tell me something like..."That's fine, as long as you hadn't entered your own sudo command and invoked the system's default fifteen minute grace period during which it allows sudo commands to be entered without a password. An attack could occur while the clock is still ticking on that timer and it would be game over."

So, I decided to fix that little problem by making sudo ask for a password every time it's entered by adding the following line to my sudoers file:
```

Defaults   timestamp_timeout=0

```Now, the bottom of my sudoers file looks like this:
```

######################################################################
# Custom commands follow
######################################################################

# Always require password to use sudo with the -l option
Defaults   listpw

# Set the number of minutes that will elapse before sudo will ask for a password again to zero
Defaults   timestamp_timeout=0

# Allow batman to run any commands anywhere without a password
batman       ALL=(ALL)       NOPASSWD: ALL 

# Allow crusty to run any commands as user: batman without a password
crusty       ALL=(batman)       NOPASSWD: ALL 

```It works like a charm.

What say you, Venerable Sir?

Hope to read from you soon,

Crusty

---

### Post by Crusty Old Fart on 2011-04-22
Oh damn. Just when I thought I had everything ducky in Dixie, I realized a few things that were a bit disturbing.

Consider the situation where an attacker has gained access to my crusty user session as described in the preceding post.

While he won't be able to discover batman's sudo privileges by running any "sudo -l" commands anymore, there's nothing to prevent him from discovering the batman account by running a search for files containing a "sudo" string like this:
```

grep -rls sudo *

```That would give the butthead a recursive list of every file in the present working directory on down that contained a sudo command.

Assuming those files are owned by user: crusty, he could read them and discover that many of them contain the string:
```

sudo -u batman sudo some_command

```...and batman's cover is now blown. Any hacker worthy of the title would surely run a command like:
```

sudo -u batman sudo -i

```...just to see if he could get away with it...and in my case, he would be most generously rewarded for the attempt by instantly becoming root.

So, giving NOPASSWD: ALL privileges to batman in sudoers is probably a **really, really bad idea**.

At this point, I thought I should take a look at DaithiF's suggestion and see if it was bombproof. Certainly it had to be safer than what I've been doing so far.

So, let's say I put a line in my sudoers file similar to what DaithiF suggests that looks like this:
```

crusty ALL = NOPASSWD: /path/to/my/script/hacktest

```...and let's assume that crusty is the owner of the "hacktest" script.

With that, let's bring in our attacker again and see what the butthead does.
He hits me with this again:
```

grep -rls sudo *

```...and in the list of files he gets there is at least the one named "hacktest" which contains a sudo command that will run without a password (as we have allowed in the sudoers file).

Next, he cd's into the directory that contains the "hacktest" file and issues the following command:
```

sudo ./hacktest

```...and discovers that he didn't need to provide a password for it to successfully complete its execution.

Furthermore, if the following line had not been added to the sudoers file:
```

Defaults   listpw

```...the attacker could run the following command without a password to discover which files he might be able to run without having to provide a password for them with this:
```

sudo -l

```The output would have contained something like this:
```

User crusty may run the following commands on this host:
(root) NOPASSWD: /path/to/my/script/hacktest

```which is even easier than having to discover them by running them and seeing which ones didn't ask for a password.

Now...since crusty owns the file and since our attacker is in a crusty session, he can edit the file.

So, he does. And inside the hacktest file, he puts this:
```

#!/bin/bash
sudo -i
exit 0

```Then he runs it again with:
```

sudo ./hacktest

```...and the sunovabitch has just become root!...without ever having to enter a password.

Ain't that nice?

So...it's probably a **really, really bad idea** to put something like:
```

crusty ALL = NOPASSWD: /path/to/my/script/hacktest

```in the sudoers file.

In fact, the more I think about it, it's probably a **really, really, bad idea** to embed any sudo commands inside any custom scripts.

There has to be a safe way around this whole mess. Perhaps it may come down to designing a scheme involving file ownership and permission levels in combination with special entries in the sudoers file. I'll have to think about that for a while. It ain't on the tip of my little brain...yet.

Sorry for all the bad news.

Have a rockin' day lads,

Crusty

---

### Post by thomas515 on 2011-04-25
is there a way to say have the password in a password-protected text file or script and then have the script reference the text file/script?  That was one of my original ideas but scraped it early on.

---

### Post by Crusty Old Fart on 2011-04-25
> **thomas515 said:**
> is there a way to say have the password in a password-protected text file or script and then have the script reference the text file/script?  That was one of my original ideas but scraped it early on.
Yes...that's very similar to the idea I had a couple of days ago. Since my last post, I have been testing a new configuration based on a combination of that thought and what I was doing earlier.

What I came up with is something that I can't hack anymore. I'll post instructions that you can use to set up a similar scheme on your machine within the next day or two.

Hopefully, DaithiF is still watching this thread and will try to hack the new scheme. I'd like to see if he'll be able to break into it without a password. I haven't been able to do it, but I've been working many hours on it and have been pretty shagged out during some of the testing. So, I may have missed something.

Glad you're still here. I was hoping you were reading what's been going on.

Don't touch that dial :cool:

Crusty

---

### Post by thomas515 on 2011-04-25
Yeah I'm definitely going to keep up with it.  The whole idea of an all-powerful super user kinda scared me.   Again I appreciate all the help.

---

### Post by thomas515 on 2011-04-25
Crusty you seem to be well-versed in the ways of Ubuntu Linux.  If you don't mind, could you take a look at another post of mine here [http://ubuntuforums.org/showthread.php?t=1738815](http://ubuntuforums.org/showthread.php?t=1738815)

---

### Post by Crusty Old Fart on 2011-04-26
> **thomas515 said:**
> Crusty you seem to be well-versed in the ways of Ubuntu Linux.  If you don't mind, could you take a look at another post of mine here [http://ubuntuforums.org/showthread.php?t=1738815](http://ubuntuforums.org/showthread.php?t=1738815)
DaithiF nailed it down for you before I could get there.

---

### Post by Crusty Old Fart on 2011-04-26
[SIZE=+1]Introduction:[/SIZE][INDENT]Here's my best thinking on all of this so far. An attacker would be able to run any any scripts that robin could run without a password. But, he wouldn't be able to become root, or modify a sudo script without providing at least one password to get to it. Please let me know if you can hack this, or if you have any problems testing it. -- Thanks, Crusty
[/INDENT][SIZE=+1]User descriptions:[/SIZE]
[LIST]
[*]robin: The initial/existing administrator account, which will be allowed to run as batman, and later downgraded to a Desktop user instead of an administrator.
[*]batman: The new administrator account, which will be allow to run specific commands without password authentication.
[/LIST]

[SIZE=+1]Overview of setup steps (details provided further down in this post):[/SIZE]
[LIST]
[*]Step 1 - Create user: batman as an administrator.
[*]Step 2 - Edit the sudoers file to always require password authentication before listing privileges given to users in the sudoers file.
[*]Step 3 - Edit the sudoers file to disable the grace period between password entries for sudo commands.
[*]Step 4 - Edit the sudoers file to allow batman to run specific commands without password authentication.
[*]Step 5 - Edit the sudoers file to allow robin to run as batman.
[*]Step 6 - Create a directory, owned by batman, inside batman's home directory (~/), named batcave, in which to store scripts that contain sudo commands.
[*]Step 7 - Set recursive permission levels on the batman directory to disable writing by anyone but batman.
[*]Step 8 - Downgrade robin to a Desktop user.
[/LIST]

[SIZE=+1]Overview of How To's (details provided further down in this post):[/SIZE]
[LIST]
[*]How To - Run robin as batman.
[*]How To - Run batman as root.
[*]How To - Run robin as root.
[*]How To - Write a file containing sudo commands that robin can run without having to manually invoke sudo or manually provide a password.
[*]How To - Create a symlink shortcut to a sudo script that robin can use as a shell command or a launcher command.
[/LIST]

[SIZE=+1]Details of setup steps:[/SIZE]
[LIST]
[*]Step 1 - Create user: batman as an administrator.
From robin's Gnome desktop:
[LIST]
[*]_Create user: batman:_ System > Administration > Users and Groups > Add > Name: batman > Short Name: batman > OK > New password: whatever > Confirmation: whatever > OK <--Don't close this window yet, Follow the instructions on the next line to make batman an administrator.
[*]_Make batman an adminstrator:_ To the right of the text "Account type:", click: Change > click the radio button to the left of: Administrator > OK > Close.
[/LIST]
 
[/LIST]

[LIST]
[*]Step 2 - Edit the sudoers file to always require password authentication before listing privileges given to users in the sudoers file.
(Add the blue lines in the code box below to the bottom of the sudoers file.)
```

[B][COLOR=Blue]######################################################################
# Custom commands follow
######################################################################

# Always require password to use sudo with the -l option
Defaults   listpw[/COLOR][/B]

```
[*]Step 3 - Edit the sudoers file to disable the grace period between password entries for sudo commands.
(Add the blue lines in the code box below to the bottom of the sudoers file.)
```

######################################################################
# Custom commands follow
######################################################################

# Always require password to use sudo with the -l option
Defaults   listpw

[B][COLOR=Blue]# Set the number of minutes that will elapse before sudo will ask for a password again to zero
Defaults   timestamp_timeout=0[/COLOR][/B]

```
[*]Step 4 - Edit the sudoers file to allow batman to run specific commands without password authentication.
(Add the blue lines in the code box below to the bottom of the sudoers file.)
```

######################################################################
# Custom commands follow
######################################################################

# Always require password to use sudo with the -l option
Defaults   listpw

# Set the number of minutes that will elapse before sudo will ask for a password again to zero
Defaults   timestamp_timeout=0

[B][COLOR=Blue]# Allow batman to run specific commands anywhere without a password.
batman ALL=(ALL) ALL, NOPASSWD: \
/usr/bin/apt-get update, \
/usr/bin/apt-get -y upgrade, \
/usr/bin/apt-get clean, \
/usr/bin/apt-get autoremove, \
/usr/bin/dpkg --configure -a, \
/usr/sbin/update-initramfs -k all -u, \
/usr/sbin/update-grub, \
/sbin/reboot now[/COLOR][/B]

```
[*]Step 5 - Edit the sudoers file to allow robin to run as batman.
(Add the blue lines in the code box below to the bottom of the sudoers file.)
```

######################################################################
# Custom commands follow
######################################################################

# Always require password to use sudo with the -l option
Defaults   listpw

# Set the number of minutes that will elapse before sudo will ask for a password again to zero
Defaults   timestamp_timeout=0

# Allow batman to run specific commands anywhere without a password.
batman ALL=(ALL) ALL, NOPASSWD: \
/usr/bin/apt-get update, \
/usr/bin/apt-get -y upgrade, \
/usr/bin/apt-get clean, \
/usr/bin/apt-get autoremove, \
/usr/bin/dpkg --configure -a, \
/usr/sbin/update-initramfs -k all -u, \
/usr/sbin/update-grub, \
/sbin/reboot now

[B][COLOR=Blue]# Allow robin to run as batman.
robin ALL=(batman) NOPASSWD: ALL[/COLOR][/B] 

```
[*]Step 6 - Create a directory, owned by batman, inside batman's home directory (~/), named batcave, in which to store scripts that contain sudo commands.
```

**[COLOR=Green]~~~ First, become batman as follows: ~~~[/COLOR]**
sudo -u batman su batman
Password: **[COLOR=Red]<--Provide robin's password here.[/COLOR]**

**[COLOR=Green]~~~ Now, create the batcave directory as follows: ~~~[/COLOR]**
mkdir ~/batcave

```
[*]Step 7 - Set recursive permission levels on the batman directory to disable writing by anyone but batman, yet allow reading and execution by all.
While still acting as batman, issue the following command:
```

chmod -R 755 ~/batcave

```
[*]Step 8 - Downgrade robin to a Desktop user.
From robin's Gnome desktop:
[LIST]
[*]System > Administration > Users and Groups > To the right of the text "Account type:", click: Change > click the radio button to the left of: Desktop user > OK > Close.
[/LIST]
 
[/LIST]

[SIZE=+1]Details of How To's:[/SIZE]
[LIST]
[*]How To - Run robin as batman.
```

**[COLOR=Green]~~~ While acting as robin, issue the following command: ~~~[/COLOR]**
sudo -u batman su batman
Password: **[COLOR=Red]<--Provide robin's password here.[/COLOR]**

```
[*]How To - Run batman as root.
```

**[COLOR=Green]~~~ While acting as batman, issue the following command: ~~~[/COLOR]**
sudo -i
[sudo] password for batman: **[COLOR=Red]<--Provide batman's password here.[/COLOR]**

```
[*]How To - Run robin as root.
Become batman first, then run batman as root.
[/LIST]
 
[LIST]
[*]How To - Write a file containing sudo commands that robin can run without having to manually invoke sudo or manually provide a password.
[LIST]
[*]Become batman. (see above)
```

sudo -u batman su batman
Password: **[COLOR=Red]<--Provide robin's password here.[/COLOR]**

```
[*]Get into the batcave directory:
```

cd ~/batcave

```
[*]Create a file. For the sake of this example, name it: batfile.sh
```

touch batfile.sh

```
[*]Edit batfile.sh with your favorite editor. Using the commands for which password authentication was removed for batman in the sudoers file, an example script follows:
```

#!/bin/bash

# **[COLOR=Green]~~~ Preface each command that requires root privileges with:[/COLOR] [COLOR=Blue]sudo -u batman sudo[/COLOR] [COLOR=Green]~~~[/COLOR]**

echo "This echo command runs without root privileges."
echo "But, all of the following commands need sudo to run."
**[COLOR=blue]sudo -u batman sudo [/COLOR]**apt-get update
**[COLOR=blue]sudo -u batman sudo [/COLOR]**apt-get -y upgrade
**[COLOR=blue]sudo -u batman sudo [/COLOR]**apt-get clean
**[COLOR=blue]sudo -u batman sudo [/COLOR]**apt-get autoremove
**[COLOR=blue]sudo -u batman sudo [/COLOR]**dpkg --configure -a
**[COLOR=blue]sudo -u batman sudo [/COLOR]**update-initramfs -k all -u
**[COLOR=blue]sudo -u batman sudo [/COLOR]**update-grub
**[COLOR=blue]sudo -u batman sudo [/COLOR]**reboot now

exit 0

```
[*]Change the permissions on batfile.sh to protect it from being modified by anyone but batman:
```

chmod 755 batfile.sh

```Now robin can run batfile.sh from his own shell or in a script without sudo or a password with the following command:
```

/home/batman/batcave/batfile.sh

```
[/LIST]
 
[*]How To - Create a symlink shortcut to a sudo script that robin can use as a shell command or a launcher command.
```

**[COLOR=Green]~~~ While acting as robin, create a bin directory with the following command: ~~~[/COLOR]**
mkdir -p ~/bin

**[COLOR=Green]~~~ While acting as robin, create a symlink in the ~/bin directory with the following commands: ~~~[/COLOR]**
cd ~/bin
ln -sf /home/batman/batcave/batfile.sh nice

```Now robin can run batfile.sh from his own shell or in a script without sudo or a password with the following command:
```

nice

```
[/LIST]

Ta da.

Crusty

P.S. I hope I didn't make too many mistakes in all this.

---

### Post by DaithiF on 2011-04-27
Hi Crusty, theres obviously a lot of effort gone into this so i'm a little hesitant to admit this but ... I don't understand the benefit of doing this.

Probably I'm misunderstanding something, so let me try to recap in my own words: robin can't sudo to root, he can only sudo to batman.  and batman can only run certain specific commands as root.

what i don't understand is the need for batman as the middle-man.  why not just give robin the right to run these commands as root?  Is the benefit the fact that an attacker who gets access to robin won't know about the batman-route to running those commands as root?  That's easily discoverable though because robin has to be able to access those batcave scripts in order to run them, and so a robin-attacker could run a command like:
```
cd /home
find . -type f -path ./robin -prune -o -print

```to see all the files he has access to under other users accounts.

probably i'm missing something.

---

### Post by Crusty Old Fart on 2011-04-27
> **DaithiF said:**
> Hi Crusty, theres obviously a lot of effort gone into this so i'm a little hesitant to admit this but ... I don't understand the benefit of doing this.

Probably I'm misunderstanding something, so let me try to recap in my own words: robin can't sudo to root, he can only sudo to batman.  and batman can only run certain specific commands as root.

what i don't understand is the need for batman as the middle-man.  why not just give robin the right to run these commands as root?  Is the benefit the fact that an attacker who gets access to robin won't know about the batman-route to running those commands as root?  That's easily discoverable though because robin has to be able to access those batcave scripts in order to run them, and so a robin-attacker could run a command like:
```
cd /home
find . -type f -path ./robin -prune -o -print

```to see all the files he has access to under other users accounts.

probably i'm missing something.
Howdy DaithiF:

Thank you for taking the time to scrutinize what I'm doing and provide your criticism. I really appreciate that...seriously.

My last post was long on ***how*** to do things and short on the reasons ***why***. I think part of what may be causing some confusion is that my introduction sucks. It doesn't introduce jack. I was having a hard time figuring out how to write it. So I punted, hoping that if I at least posted the setup and the how to's, the wizards and noobs alike would have something to throw darts at. Based on the responses, I'd have a better idea of what I needed to write in the introductory section.

Beyond that, I might get even luckier and have you send me back to the drawing board by either poking holes in what I've done, or suggesting ways to either simplify it and/or make it better, which you just did. Thanks.

I'll come back here and address each of your comments later. I need some more time to think about things, do some testing, and find ways to answer you that make sense. That might take a little while. So, in the meantime, I thought I should let you know that I'm not ignoring you or giving up.

With your help keeping me on the right track, I think we're going to end up with a pretty sexy solution.

Thanks again,

Crusty

---

### Post by Crusty Old Fart on 2011-04-29
Howdy DaithiF:

I'm going to chop up your last post and address it in a slightly different order than you wrote it. So, here goes...

> **DaithiF said:**
> Hi Crusty, theres obviously a lot of effort gone into this so i'm a little hesitant to admit this but ... I don't understand the benefit of doing this...Yup...it is/was a fair amount of work. Please don't ever hesitate if I post anything that causes your brain to stub its toe. If you, being the wizard that you are, don't understand what I've done, then I surely haven't explained it well enough for the noobs to get it, and I think it's important that they do.

> **DaithiF said:**
> ...Probably I'm misunderstanding something, so let me try to recap in my own words: robin can't sudo to root, he can only sudo to batman.  and batman can only run certain specific commands as root...Yup...that's right. Your understanding is spot on so far.

> **DaithiF said:**
> ...Is the benefit the fact that an attacker who gets access to robin won't know about the batman-route to running those commands as root?...Nope. I never intended to block discovery of the batman-route to running those commands as root. There are several ways that can be discovered, but I can't think of any that do it more efficiently than your find command. You have an enviable knack for highly efficient bash code. I tip my hat to you for that once again.

> **DaithiF said:**
> ...probably i'm missing something.Yup...I think you are. I think you're missing the crux of the problem. But that's my fault because I neglected to mention it and I presented things in a way that didn't seem to allow for its possibility. Sorry about that.

> **DaithiF said:**
> ...what i don't understand is the need for batman as the middle-man.  why not just give robin the right to run these commands as root?...This stuff is so much harder for me to explain than it is for me to think it up in the first place that I'm going to post two answers in hopes that one or both of them will make sense to anyone trying to understand what I'm trying to do with all this.

_Here's the first answer:_

The setup you suggest does not benefit from the creation of the batman account or the batcave directory ***as long as robin limits his* [COLOR=red]NOPASSWD:[/COLOR] *entries in the sudoers file to *[COLOR=red]specific root commands[/COLOR]**. In that case, it's fine. But..._and here's the crux that I neglected to mention_ --> ***if robin puts a *[COLOR=red]script[/COLOR] *in his* [COLOR=red]NOPASSWD:[/COLOR] *entries***, then he becomes vulnerable to an attacker discovering the script and editing it with something like:
```

#!/bin/bash
sudo -i
exit 0

```Now the attacker can become root by running the script. Note that since robin owns the script, the attacker can edit it and run it ***without ever knowing robin's password***. I addressed this problem as part of [post=10708577]Post #15 in this thread[/post].

By creating the batman user and the batcave directory, we give robin a place to store his scripts and relinquish ownership of them to batman. We also allow write privileges to the scripts to batman only, and write access to the batcave directory to batman only. Doing this prevents an attacker from editing any of the scripts, or storing new scripts, in the batcave directory. In order for robin to do either of these, he must first become batman and that requires a password, which the attacker doesn't know. After this is set up, we can safely add lines to the sudoers file like:
```

batman ALL=(ALL) ALL, NOPASSWD: /home/batman/batcave/batfile.sh
***[COLOR=blue]~~~ or even ~~~[/COLOR]***
batman ALL=(ALL) ALL, NOPASSWD: /home/batman/batcave/*

```Finally, now that we have batman, who must be an administrator to run root commands, we downgrade robin to a Desktop user for extra security.

_And here's the second answer:_

Let's go back to the initial system configuration where robin is the only user, and as such, the system will require that he has an administrator account.

Now...let's do what DaithiF suggests and edit the sudoers file to allow robin to run ***specific root commands*** without having to authenticate with a password.

At this point robin can create scripts containing those commands by prefacing each command with: **sudo** and his scripts will run without password authentication. An attacker who has penetrated robin's firewall and has managed to piggy-back onto robin's session, without knowing robin's password, can do the same. Since for all practical purposes, the only difference between robin and the attacker is that robin knows all of the passwords, whereas we are assuming the attacker knows none of them.

As long as robin doesn't include root commands in his NOPASSWD: entries in the sudoers file that he considers too dangerous for an attacker to run, he should be fine. For those dangerous root commands, robin should still allow the system to require even robin to manually enter his password before running them.

This setup doesn't compromise any security that was obtained with the batman/robin setup that I described earlier. So, in this case, **as long as robin never allows one of his scripts to run without authentication in the sudoers file**, then there is no benefit to creating the batman account or anything associated with it, including batman's privileges in the sudoers file, or the batcave directory.

However...

If robin edits his sudoers file and ***allows a script that he can edit***, say: /home/robin/robinfile.sh, ***to run without password authentication***, an attacker could become root as explained in [post=10708577]Post #15[/post] and then the jig is up and robin is screwed.

As long as robin limits his NOPASSWD: entries to specific root commands that he considers relatively safe, he's in good shape. But, there's nothing to protect him if he departs from this principle and begins including his own custom scripts as members of his NOPASSWD: entries in the sudoers file.

So...to protect robin against this threat, we can downgrade robin's account to a Desktop user. But before we can do that, we have to create a new administrator account because the system requires the existence of at least one administrator. That's where batman comes in. Once the batman administrator account has been created, robin's account can be downgraded to a Desktop user. But, as soon as we do that, robin won't be able to run any root commands, regardless of whether they require passwords or not.

We can get around robin being shut out from some of the root commands, by allowing robin to run as batman and limiting what batman can run without password authentication to specific commands and ***scripts owned and writeable only by batman***. Granted, an attacker would still be able to do the same. BUT, unless the attacker knows batman's password, he would not be able to edit any of batman's files that were writeable only by batman (e.g.: chmod 755 batfile.sh). Nor, could the attacker store a new script in a directory that could only be written to by batman (e.g.: chmod 755 batcave). And consequently could not become root. On the other hand, robin can do all three because he knows batman's password, can become batman and can make batman become root.

What are the chances, especially after robin reads the sudoers man page, that he won't ever allow one of his scripts to run without a password? I think those chances are so slim that I should find a way to protect him from an attacker in such cases. Hence batman -- who rather than being an unnecessary middle-man, I like to think of as the gatekeeper to the batcave :cool:

I hope some of this made sense. I'm getting lost in my own writing and becoming blind to what it's actually saying.

Maybe I need a break. My wrinkled old brain hurts,

Crusty

P.S. Hey DaithiF...If you understand what I'm trying to say now, and think you could do a better job of explaining it, I invite you to give it a shot. As hard as I've tried, I can't seem to come up with an explanation that I'm satisfied with.

---

### Post by DaithiF on 2011-04-29
Ah ok, now I understand.  Thanks for the explanation.  Personally my view would be that if there is a script that needs to be run as root and which is going to be allowed to run via sudo NOPASSWD by some user, then that script needs to be owned (and only writable) by root.  
Thats to avoid the risk of someone editing the file to change the original intention of the script, or indeed launching a root session via sudo -i, as you point out.

So that means
1. chown'ing the script to root
2. chmod'ing it to 755
3. putting it in a directory only writeable by root (e.g. /usr/local/bin)
#3 is particularly important as if a script is put in a directory writeable by a user (e.g. /home/someuser/bin) then even if 1. and 2. are done, the script can still be deleted/recreated by the user to do anything they want.

---

### Post by hwttdz on 2011-04-29
I second DaithiF again.  Read your previous post and replace all instances of batman with root and suddenly it looks like a linux system.  Batman is root, batcave is /root, ....  Granted, I agree that it'd be way cooler if root was named batman.

---

### Post by Crusty Old Fart on 2011-04-29
> **DaithiF said:**
> Ah ok, now I understand.  Thanks for the explanation.  Personally my view would be that if there is a script that needs to be run as root and which is going to be allowed to run via sudo NOPASSWD by some user, then that script needs to be owned (and only writable) by root.  
Thats to avoid the risk of someone editing the file to change the original intention of the script, or indeed launching a root session via sudo -i, as you point out.

So that means
1. chown'ing the script to root
2. chmod'ing it to 755
3. putting it in a directory only writeable by root (e.g. /usr/local/bin)
#3 is particularly important as if a script is put in a directory writeable by a user (e.g. /home/someuser/bin) then even if 1. and 2. are done, the script can still be deleted/recreated by the user to do anything they want.

If I made a file named robinfile.sh, followed your steps 1 - 3, and made an entry for robin in the sudoers file like this:
```

robin ALL=(root) NOPASSWD: /usr/local/bin/robinfile.sh

```That seems to be all I'd need. That's a lot cleaner than futzing around with batman and his batcave. Plus, as long as there was at least one administrator account (batman), robin can still run as a Desktop user. Or, we can eliminate batman completely and change robin back to an administrator.

[B]Oh man, oh man, oh man...
This is so much better in so many ways[/B]. Thanks DaithiF

If I went back and edited my [post=10721629]Post #21[/post] reflect this change, it would really mess up the continuity of this thread. So, I'll rewrite it and post the new version as a new post.

I can't thank you enough for this DaithiF.

Very gratefully,

Crusty

---

