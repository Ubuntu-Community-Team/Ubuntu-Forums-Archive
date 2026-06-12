---
title: "Why am I not the Root?! (Just administrator not owner)"
date: 2010-04-30
forum: General Help
---

### Post by scathdesolas on 2010-04-30
**This was all after the new Security Updates install for Karmic Koala 9.10**

I installed ubuntu, have been dealing with the fact that it set me as Administrator instead of Owner upon installation. I re-installed this twice by the way. Third time I gave up. It's not my cd or files I downloaded from the server.

How the hell do I reset my password for the ROOT? the USER password works... but now with the new update I can't install anything because of authentication not working. Why am I even Administrator and not set to Owner once I installed it...

Please help. I don't want to set Administrator with permissions as "root" for EVERY SINGLE folder or w/e listed in the user and groups manager.. It says "root" and "[username]" to set for permissions. [I](For those that don't know, [username[ is where my username would be which I didn't wish to 
[/I]
It was working fine, but now my "root" password doesn't work and it says Authentication Failure every time.

**I can**'t even** edit the users or groups without "root" password.**
Also I can't get updates now... without this "root password". How can I change this in the terminal or override it?

---

### Post by Smart Viking on 2010-04-30
I don't think you are supposed to be root, i have never had the need for it.

If wanna do something like root, type "sudo [a command]" And **your** password, not root's password. :)

---

### Post by scathdesolas on 2010-04-30
> **Smart Viking said:**
> I don't think you are supposed to be root, i have never had the need for it.

If wanna do something like root, type "sudo [a command]" And **your** password, not root's password. :)

But I can't install updates from the updates manager... without the password. I get authentication failure and then an error saying contact system administrator blah blah blah blah blah.

[B]I tried with the terminal to change the root:

sudo passwd
[sudo] password for loki: 
loki is not in the sudoers file.  This incident will be reported.

[/B]Apparently the security update CHANGED my values or something inside the OS to something other than what I had set before. So now i"m not even an administrator.

---

### Post by Ozymandias_117 on 2010-04-30
> **scathdesolas said:**
> I installed ubuntu, have been dealing with the fact that it set me as Administrator instead of Owner upon installation. I re-installed this twice by the way. Third time I gave up. It's not my cd or files I downloaded from the server.

How the hell do I reset my password for the ROOT? the USER password works... but now with the new update I can't install anything because of authentication not working. Why am I even Administrator and not set to Owner once I installed it...

Please help. I don't want to set Administrator with permissions as "root" for EVERY SINGLE folder or w/e listed in the user and groups manager.. It says "root" and "[username]" to set for permissions. [I](For those that don't know, [username[ is where my username would be which I didn't wish to 
[/I] 
It was working fine, but now my "root" password doesn't work and it says Authentication Failure every time.

I can't follow exactly what you're saying, so... I will try to answer the questions I think that you are posing.

1. Administrator in Linux is Root

2. Ubuntu doesn't have an accessible root account by default

3. Whenever it asks for Root or Administrator privileges and asks for a password, it really wants your user password (Because everything uses sudo, which takes your password and lets you "pretend" (pseudo) to be root)

4. The folders outside of /home/user (aka ~/) SHOULD be limited to root access so you can't accidentally modify them incorrectly, or if you were to ever get a virus, so it can't.

---

### Post by Smart Viking on 2010-04-30
> **scathdesolas said:**
> But I can't install updates from the updates manager... without the password. I get authentication failure and then an error saying contact system administrator blah blah blah blah blah.

You don't need to write the root password. If you are the administrator, just write your log in password. :)

---

### Post by dcstar on 2010-04-30
> **scathdesolas said:**
> [B]
.........
It was working fine, but now my "root" password doesn't work and it says Authentication Failure every time.

Also I can't get updates now... without this "root password". How can I change this in the terminal or override it?

There is no "root" password in Ubuntu becase the root account is disabled by default.

You get all the root access you need with sudo/gksudo/su/gksu using the password you were prompted for at installation time.

If that password has ceased to function, then you have a major problem.

---

### Post by P4man on 2010-04-30
Please, read this carefully:

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

If you have any questions after that, feel free to ask.

---

### Post by scathdesolas on 2010-04-30
> **P4man said:**
> Please, read this carefully:

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

If you have any questions after that, feel free to ask.

Here is the kicker. It set me to the group that is the SAME as my USERNAME, does this matter? I am not an admin anymore I'm guessing since after the update. My username password does not work / recognized as the root password anymore and I'm not in the sudoers list. I can't set anything in the terminal... Do I enter recovery mode or use the editor before full boot?

I tried using usermod commands, sudo commands, same thing. I do not have permission or it'll give me "[B]usermod: cannot lock /etc/passwd; try again later."

I also tried to set myself as root user:
[/B]username@ubuntu:~$ su
Password: 
su: Authentication failure
username@ubuntu:~$

[B]I tried also:
[/B]gksudo
**And the user list does not include the admin group, does it normally do this?**

[B]Add user:
[/B]username@ubuntu:~$ adduser
adduser: Only root may add a user or group to the system. 

It seems like when logged in I have basically no power at all to do anything via the terminal.

---

### Post by Smart Viking on 2010-04-30
If you really need to enable the root account, use

Took that away.

EDIT:

> **Allowing other users to run sudo**

 To add a new user to sudo, open the **Users and Groups** tool from **System->Administration** menu. Then click on the user and then on properties. Choose the **User Privileges** tab. In the tab, find **Administer the system** and check that. I don't know if that is the answer for you not being able to use sudo, but look.

EDIT2: And if the option to eventually check of "Administer the system" is greyed out, you need to press the keys in the bottom and enter your password.

---

### Post by P4man on 2010-04-30
smart viking, explaining how to enable root account violates forum rules, and is not going to help the OP. Please edit your post before other new ubuntu users start thinking they are "clever enough to be root" and end up bricking their system, like the OP.

---

### Post by Smart Viking on 2010-04-30
> **P4man said:**
> smart viking, explaining how to enable root account violates forum rules, and is not going to help the OP. Please edit your post before other new ubuntu start thinking they are "clever enough to be root" and end up bricking their system, like the OP.

Ok, thank you for saying. :oops:

---

### Post by P4man on 2010-04-30
> **scathdesolas said:**
> Here is the kicker. It set me to the group that is the SAME as my USERNAME, does this matter?

That at least is normal. That you are not in sudoers, is not normal, and I suspect you did something wrong trying to enable root.

You can recover from this by booting the **edit**: recovery mode and entering the root terminal and add your user back to the sudoers and admin group and reset your users password (passwd username)

---

### Post by jvc26 on 2010-04-30
> **P4man said:**
> smart viking, explaining how to enable root account violates forum rules, and is not going to help the OP. 

Really? Wow, thats pretty rigid, since it appears the OP isn't in the admin group, he can't add himself to a group without being root... pretty **** situation if the forum won't let you know how to do that!

@op:

```
cat /etc/group | grep admin
```

Will give you a line which may or may not include your username. If it doesnt, you'll have to go in under single user mode to add yourself:

At the GRUB menu, go to the line you want to boot, press e, and on the line for the kernel, go to the end of the line and add 'single' then press b (I think, but it tells you at the bottom of the screen) to boot the kernel. That should bring you into a single user-mode ubuntu. At that point, being root, you should be able to run:

```
adduser loki admin
```

Which will add your 'loki' user to the admin group, hopefully re-enabling sudo. Why this coincided with the update I don't know, might be worth reporting a bug on the issue, if indeed that caused it.

The alternative method is to boot the livecd select 'repair broken system' get yourself a root prompt in your main ubuntu partition (when given the option to during the process), and then run the same adduser command to get yourself back on the admin group.


J

---

### Post by P4man on 2010-04-30
> **jvc26 said:**
> Really? Wow, thats pretty rigid, since it appears the OP isn't in the admin group, he can't add himself to a group without being root... pretty **** situation if the forum won't let you know how to do that!

There is no need to enable the root account to fix his problem. He still has access to recovery mode / root terminal. Besides, he CANT enable the root account if he is not administrator so explaining how to do this wont help him anyway.

---

### Post by sisco311 on 2010-04-30
> **P4man said:**
> That at least is normal. That you are not in sudoers, is not normal, and I suspect you did something wrong trying to enable root.

You can recover from this by booting the **edit**: recovery mode and entering the root terminal and add your user back to the sudoers and admin group and reset your users password (passwd username)

+1

@OP
here is a detailed guide:
[http://www.psychocats.net/ubuntu/fixsudo](http://www.psychocats.net/ubuntu/fixsudo)

---

### Post by scathdesolas on 2010-04-30
I just tried various methods. When I select "e" am I already inside the kernel? Because I believe so since there's a box which has all the different boot lines. And "B" is nto to boot it's CTRL+X I think. I got into the root. I can not access: /etc/sudoers/

I also added 2 usernames with different passwords, etc. I'll try single usermode but I'm on a different name now even and I still can not use or access anything. The problem is this:

Prompt for ROOT PASSWORD... Authentication Failed. I think I just need the root password reset.

I've been to recovery mode. Just loads a lot of lines of text automatically, commands and such. Do I press e or b here then? I'e looked up how to reset the root password as well [located here]("http://burnz.wordpress.com/2008/09/09/how-to-reset-ubuntu-root-password/")

---

### Post by jvc26 on 2010-04-30
> **P4man said:**
> Besides, he CANT enable the root account if he is not administrator so explaining how to do this wont help him anyway.

In this case that is indeed true, single user mode or the recovery console are the best options for him. However the general paranoia about 'root' user seems a little OTT! 

While I obviously appreciate the fact that running as a nonroot user is important from a security perspective, just because your root user has a password doesnt make your system much more insecure than having a sudo user with a password.

J

---

### Post by jvc26 on 2010-04-30
Hmm - right, in which case, boot to the ubuntu cd, choose 'recover broken system' run through the prompts until it asks you what you want to do, of which one of the options will be something like 'root console' or something similar in a given partition, type in the partition you want to get into (the one where ubuntu is installed) and it should bring you up a root console within that partition (a chroot infact I believe). At this point, ```
adduser loki admin
``` should add you back onto the admin group.

J

---

### Post by jvc26 on 2010-04-30
> **sisco311 said:**
> 
@OP
here is a detailed guide:
[http://www.psychocats.net/ubuntu/fixsudo](http://www.psychocats.net/ubuntu/fixsudo)

Heres the man with the plan.

J

---

### Post by P4man on 2010-04-30
> **jvc26 said:**
> In this case that is indeed true, single user mode or the recovery console are the best options for him. However the general paranoia about 'root' user seems a little OTT! 

While I obviously appreciate the fact that running as a nonroot user is important from a security perspective, just because your root user has a password doesnt make your system much more insecure than having a sudo user with a password.

J

Well, I think the OP just proved why its a good idea how to explain using sudo rather than how to become root. 

There is no rule or law against enabling root, and it might be warranted in some cases,  but its a very good idea not to explain it to people who do not know exactly what they are doing so we avoid problems such as these. People who do understand what they are doing dont need to ask, as its rather obvious how to use the root account.

Anyway, policy and rationale very well explained here:
[http://ubuntuforums.org/showthread.php?t=716201](http://ubuntuforums.org/showthread.php?t=716201)

---

### Post by scathdesolas on 2010-04-30
> **jvc26 said:**
> Heres the man with the plan.

J

I am not aware of who suggested it first, but the idea behind the adduser loki admin had worked. 

The recent security update put me in usergroup "loki" rather than usergroup admin. The FULL NAME of my username was set to Administrator therefore I thought I was still an admin when I wasn.t

[B]I fixed this situation by doing this:

Booting into Ubunutu > Loaded Ubuntu [my latest version at top] (Recovery Console) > Pressed down button and entered "root" > then typed adduser loki admin > typed adduser loki root (was already set though).
[/B]
Once I did this it enabled my username pass as the root pass.

Thanks for all the quick replies :) Once my new external comes, I'm using ubuntu from that xD I'm a full converted Ubuntu User now.

**PS** The command line... confusing for most maybe, but windows OS and Mac have nothing on the simplicity and straight forward approach. I freaking love it. :guitar:

[I]Now I can use the latest 10.04 release :) You guys at ubuntu are gods and you bet your **** I'm going to promote with my music label and media company... All sites we build / own will get ubuntu banners and links! Can't wait to make some great funny t-shirt designs comparing Linux over other OS's.
[/I]

---

### Post by Dayofswords on 2010-04-30
> smart viking, explaining how to enable root account violates forum rules
> **jvc26 said:**
> However the general paranoia about 'root' user seems a little OTT! 

I say if they really want to know how, we should be allowed to tell them...
just be required to throw in a warning or something, like:

> Only become root if you know exactly what you are doing, what the consequences of what your doing are and the risk you are taking by being root. This should not be taken lightly. Incorrectly doing something may cause system damage or security problems. 'sudo' and its variants are nearly all the time better than being root.
I don't like the idea of denying knowledge because they may harm their system if they do something wrong

---

### Post by scathdesolas on 2010-04-30
> **Dayofswords said:**
> I say if they really want to know how, we should be allowed to tell them...
just be required to throw in a warning or something, like

Well said Dayofswords. I agree fully. Limiting how or what a user can do defeats the purpose of it being open source, in a very very very tiny way lol But adding a disclaimer would void other peoples responsibility.

---

### Post by jvc26 on 2010-04-30
You may want to remove your user from the 'root' group, as that is unnecessary, the admin group should allow you to do sudo based commands.

J

---

### Post by P4man on 2010-04-30
> **Dayofswords said:**
> I say if they really want to know how, we should be allowed to tell them...
just be required to throw in a warning or something, like:

I don't like the idea of denying knowledge because they may harm their system if they do something wrong

Well, its not likely you;ll bring up an argument that isnt covered here:
[http://ubuntuforums.org/showthread.php?t=716201](http://ubuntuforums.org/showthread.php?t=716201)

Feel free to disagree, but I think the logic is sound.

---

### Post by scathdesolas on 2010-04-30
> **jvc26 said:**
> You may want to remove your user from the 'root' group, as that is unnecessary, the admin group should allow you to do sudo based commands.

J

Hmm yes well I didn't add it, because it was set already as such... So does this matter?

---

### Post by deedeesuzanne on 2010-06-05
I have a question related to this thread: As administrator, I still cannot install applications either. I checked the permissions in Users, but I don't see any options except read-write and read-only. Is there another option somewhere for Execute? And if so, is that why I can't install into my /user/bin directory?

---

### Post by louieb on 2010-06-05
@deedeesuzanne Your probably best served by starting a new thread.  

What do you mean "can't install application" how are you trying to install? Synaptic, Software Center, apt or some downloaded tar-ball. 

Read, write and execute are attributes of files and directories. They are used with the owner and group to determine who can read or write to them.

---

### Post by vaso2 on 2012-01-18
> **Smart Viking said:**
> If you really need to enable the root account, use

Took that away.

EDIT:

I don't know if that is the answer for you not being able to use sudo, but look.

EDIT2: And if the option to eventually check of "Administer the system" is greyed out, you need to press the keys in the bottom and enter your password.

hi there!!! well i have the exact same problem ! i did what you said but when i enter recovery mode there's nothing i can do!!! i cant go up or down so help.... what can i do now???

---

### Post by oldos2er on 2012-01-18
Closed, necromancy. Please start a new thread for your problem.

---

