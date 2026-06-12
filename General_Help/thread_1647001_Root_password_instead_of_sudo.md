---
title: "Root password instead of sudo"
date: 2010-12-16
forum: General Help
---

### Post by MauserM98 on 2010-12-16
When i install or upgrade the system I want to be asked for the root password instead of just the normal password for sudo. The reason for this is that the kids and so on uses my system and know my password. They do not know my root password though. I do not want them to install or mess up my system by pure fumbling, so is this possible to do. A simple change in who runs the updater/install features...

---

### Post by cogier on 2010-12-16
Why not just change your password to one the kids don't know. Go to **System>Preferences>Password** enter your present password then your new one.

You can set up users for your kids at **System>Administration>Users and Groups** so that they have their own space and you can control their access.

(Menu as on 10.04LTS)

---

### Post by matt_symes on 2010-12-16
Hi

> Why not just change your password to one the kids don't know. Go to **System>Preferences>Password** enter your present password then your new one.

You can set up users for your kids at **System>Administration>Users and Groups** so that they have their own space and you can control their access.

(Menu as on 10.04LTS)

+1 to this suggestion. And just remove your children from the admin group. That is the joy of a multi user system.

Kind regards

---

### Post by wojox on 2010-12-16
Don't grant administrative rights to a normal user. Learn about user permissions. ;)

---

### Post by MauserM98 on 2010-12-16
> **cogier said:**
> Why not just change your password to one the kids don't know. Go to **System>Preferences>Password** enter your present password then your new one.

You can set up users for your kids at **System>Administration>Users and Groups** so that they have their own space and you can control their access.

(Menu as on 10.04LTS)

I know this. But my PC is on all day long. I do not want to log in and out all day, I have nothing to hide for my kids so that is not an issue. The question is still the same or is this impossible to do?

Is it possible for me to remove my administrative rights as a user, but invoke them by starting the updater as root?
I do not need a gui to do this I guess it is possible to do this in terminal by typing apt-get update or?

---

### Post by mmsmc on 2010-12-16
press cntrl+alt+f1 to put it into a locked mode
then press cntrl+alt+f7 to unlock it without entering a password, be sure to change your password before doing this

---

### Post by Slim Odds on 2010-12-16
> **MauserM98 said:**
> I know this. But my PC is on all day long. I do not want to log in and out all day, I have nothing to hide for my kids so that is not an issue. The question is still the same or is this impossible to do?

I think that you're missing the point. The proper mechanism is there to do what you want, use it. You can make all of your files accessible to everyone if you want, but YOUR PASSWORD needs to be secure since it's the one that can control the system.

---

### Post by matt_symes on 2010-12-16
Hi

What you could do is create a new account with admin privileges, remove admin privileges from your account and just log into the other account that has the admin privileges when you need to administor the system. 

Is that an option?

Kind regards

---

### Post by MauserM98 on 2010-12-16
> **Slim Odds said:**
> but YOUR PASSWORD needs to be secure since it's the one that can control the system.

I thought my password was intended to administer my user and the that the root user was the system administer. This is if you say so a security blunder in Ubuntu...

---

### Post by Joeb454 on 2010-12-16
> **MauserM98 said:**
> I thought my password was intended to administer my user and the that the root user was the system administer. This is if you say so a security blunder in Ubuntu...

It's the way sudo was designed, not a flaw in Ubuntu

See [https://wiki.ubuntu.com/RootSudo](https://wiki.ubuntu.com/RootSudo) for more information

---

### Post by matt_symes on 2010-12-16
Hi
> 
 I thought my password was intended to administer my user and the that the  root user was the system administer. This is if you say so a security  blunder in Ubuntu...It does not quite work like that because if you are a member of the admin group then your password is also used to administer the system as well, as well as logging into the system.

As i stated, you can create another user with admin rights and a new password, remove admin rights from your account and the every time you want to administer the system you will have to enter the password from the new admin account (and not your own), or you can just log in to the account directly.

Kind regards

---

### Post by matt_symes on 2010-12-16
Duplicate post....

---

### Post by MauserM98 on 2010-12-16
> **matt_symes said:**
> Hi

What you could do is create a new account with admin privileges, remove admin privileges from your account and just log into the other account that has the admin privileges when you need to administor the system. 

Is that an option?

Kind regards

Best answer so far.
That might be the answer. For my needs.
Or is it possible to have another password on sudo than the user password?

---

### Post by matt_symes on 2010-12-16
Hi

> Or is it possible to have another password on sudo than the user password?

Not as far as i'm aware, but others might know better.

Kind regards

---

### Post by bodhi.zazen on 2010-12-16
> **MauserM98 said:**
> When i install or upgrade the system I want to be asked for the root password instead of just the normal password for sudo. The reason for this is that the kids and so on uses my system and know my password. They do not know my root password though. I do not want them to install or mess up my system by pure fumbling, so is this possible to do. A simple change in who runs the updater/install features...

My first piece of advice is to create a unique account for each user. This is an important concept on shared computers and is the 'proper' way. It has a number of (obvious) advantages including security, privacy, and perhaps most important, keeping all a users documents/settings/themes/icons/music lists/etc in their respective home, allowing each user to have his or her own profile for programs, etc. This will become more important over time as the children learn to set backgrounds and theme firefox (it is amazing how fast they learn, but no I do not wish to use my daughter's pink theme).

On shared computers, use "switch user".

If this is too inconvenient, make a shared account or use the guest account. If you wish to sysadmin from there su to your admin account.

---

### Post by bodhi.zazen on 2010-12-16
> **MauserM98 said:**
> Or is it possible to have another password on sudo than the user password?

It is possible, read the man page, target_pw. Usually we do not advise you read the man page, but for something like sudo it is important.

It is, however, perhaps more effort then it is worth as I think there are better solutions (see my previous post).

---

### Post by WorMzy on 2010-12-16
> **bodhi.zazen said:**
> Usually we do not advise you read the man page

Whaaaat? Telling users to rtfm is like the default state of being on these forums. :P

Although we put it a lot more subtly than that.

---

### Post by matt_symes on 2010-12-16
Hi

@Bodhi. Interesting. I never knew that.

For OP

man sudoers

and look for targetpw

I would recommend multiple accounts though. Its the standard way of doing things.

Kind regards

---

### Post by Krytarik on 2010-12-16
[http://www.sudo.ws/sudo/sudoers.man.html](http://www.sudo.ws/sudo/sudoers.man.html)

[http://www.ducea.com/2006/06/18/linux-tips-password-usage-in-sudo-passwd-nopasswd/](http://www.ducea.com/2006/06/18/linux-tips-password-usage-in-sudo-passwd-nopasswd/)

Some people were obviously faster to post, while I searched for the option.;)

---

