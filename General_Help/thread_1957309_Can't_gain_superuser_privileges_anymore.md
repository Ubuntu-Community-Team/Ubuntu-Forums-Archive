---
title: "Can't gain superuser privileges anymore"
date: 2012-04-12
forum: General Help
---

### Post by Jaxke on 2012-04-12
Hi again! 

Today I was trying to install fastboot files(Android) under my Ubuntu. It was a heck of a mess, and somehow I lost all my superuser permissions(I did have them before. And I am admin)!
For example, if I type "gksudo nautilus" it asks for my password, I type it correctly, and it says "su: Authentication failure". This error happens everytime I use a superuser command like "sudo" or "su".

I tried googling for a solution, but yet I couldn't find anything that helps me.

I hope I was clear enough. All answers appreciated! Thanks.

---

### Post by imachavel on 2012-04-12
here is some troubleshooting:

[http://www.kvarley.co.uk/news/items/ubuntu-fix-gksu-gksudo-password-error.htm](http://www.kvarley.co.uk/news/items/ubuntu-fix-gksu-gksudo-password-error.htm)

I use gksu nautilus all the time to move things into local host and it never rejects my password. Don't know what to tell you

---

### Post by moody_mark on 2012-04-12
What is your current user and group? The /etc/sudoers file contains information about which user has privs to get sudo, usually by default its members of the admin group.

open up a terminal and type "groups"

you should see something like

```
curtis@Homer:~$ groups
curtis adm dialout cdrom plugdev lpadmin admin sambashare dba
```

If your not in the admin group then probably you can boot from a live CD and copy across the /etc/sudoers file.

Further info: [https://help.ubuntu.com/community/Sudoers](https://help.ubuntu.com/community/Sudoers)

---

### Post by Jaxke on 2012-04-12
[B]jaxe@jaxe-Aspire-5750:~$ groups
jaxe adm dialout cdrom plugdev lpadmin admin sambashare

S[/B]eems like I do belong in the admin group... Weird, still it won't accept my password. Any fixes?

@Imachavel thanks, but did not work :(

---

### Post by moody_mark on 2012-04-12
Can you get to the content of your /etc/sudoers file? Try pasting the file contents here, here's mine


```
# /etc/sudoers
#
# This file MUST be edited with the 'visudo' command as root.
#
# See the man page for details on how to write a sudoers file.
#

Defaults	env_reset

# Host alias specification

# User alias specification

# Cmnd alias specification

# User privilege specification
root	ALL=(ALL) ALL

# Allow members of group sudo to execute any command after they have
# provided their password
# (Note that later entries override this, so you might need to move
# it further down)
%sudo ALL=(ALL) ALL
#
#includedir /etc/sudoers.d

# Members of the admin group may gain root privileges
%admin ALL=(ALL) ALL

```

---

### Post by haqking on 2012-04-12
you mention both su and sudo which are different commands.

su means switch user/superuser/setuser and by default if no user is specified goes to root account and so expects root password if you unlocked the root account and gave it one at some point (by default root is locked)

sudo means switch user/superuser/setuser do and as along as you are a admin then you can assume elevated privelege by using sudo and when asks for password it expects your own accounts login password.

So which one are you using and what password are you supplying ?

the gksudo command should be your accounts login password.

Is this what you are doing ?

Peace

---

### Post by Jaxke on 2012-04-12
> **haqking said:**
> you mention both su and sudo which are different commands.

su means switch user and by default if no user is specified goes to root account and so expects root password if you unlocked the root account and gave it one at some point (by default root is locked)

sudo means superuser do and as along as you are a admin then you can assume elevated privelege by using sudo and when asks for password it expects your own accounts login password.

So which one are you using and what password are you supplying ?

the gksudo command should be your accounts login password.

Is this what you are doing ?

Peace
Yeah, sorry about that. I meant command "su", I don't know exactly what does it do(I believe it'll gain superuser for current Terminal session?) but the guide(Android fastboot) told me to type "su". I'm still a noob so... :D

But yeah, I can't open sudoers file either. I remember opening it today, and may have done something to it :redface: 

You said it could be fixed with live CD? I guess it's my only option. But still, I am the supervisor and administrator of the computer, and it sounds odd I can't access the admin files...

Thanks for answers guys! :)

E: And yes, when it asks for a password, I type my login password. I don't have any other passwords.

---

### Post by haqking on 2012-04-12
> **Jaxke said:**
> Yeah, sorry about that. I meant command "su", I don't know exactly what does it do(I believe it'll gain superuser for current Terminal session?) but the guide(Android fastboot) told me to type "su". I'm still a noob so... :D

But yeah, I can't open sudoers file neither. I remember opening it today, and may have done something to it :redface: 

You said it could be fixed with live CD? I guess it's my only option. But still, I am the supervisor and administrator of the computer, and it sounds odd I can't access the admin files...

Thanks for answers guys! :)

yeah well as i said.

Su and sudo are different.

Sudo requires your own login password and gives you admin access if you are in the sudo group.

su will switch user which if no account name provided defaults to root, so requires root password if it has one.

If you never gave root a password then it doesnt have one and root is therefore still locked

In Ubuntu you should use sudo for admin tasks.

So when it asks you to use su then use sudo instead and give it your own login password.

If its a graphical app then use gksudo.

Peace

---

### Post by Jaxke on 2012-04-12
> **haqking said:**
> yeah well as i said.

Su and sudo are different.

Sudo requires your own login password and gives you admin access if you are in the sudo group.

su will switch user which if no account name provided defaults to root, so requires root password if it has one.

If you never gave root a password then it doesnt have one and root is therefore still locked

In Ubuntu you should use sudo for admin tasks.

So when it asks you to use su then use sudo instead and give it your own login password.

If its a graphical app then use gksudo.

Peace
Ah, ok. I apologise I read your post wrong :D Thanks for the info, made one thing clearer.

---

### Post by Jaxke on 2012-04-12
Oh, dammit, I can't recover sudo even from recovery mode. I have really screwed something up.

---

### Post by haqking on 2012-04-12
[http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword)

[http://www.psychocats.net/ubuntu/fixsudo](http://www.psychocats.net/ubuntu/fixsudo)

---

### Post by Jaxke on 2012-04-12
OK, thanks guys for help! 

I got it fixed with my live pen drive("live cd"). I just edited a few lines of sudoers file, and now it's working again! :guitar:

---

### Post by haqking on 2012-04-12
> **Jaxke said:**
> OK, thanks guys for help! 

I got it fixed with my live pen drive("live cd"). I just edited a few lines of sudoers file, and now it's working again! :guitar:

cool glad you got it working.

Peace

---

### Post by bab1 on 2012-04-12
> **haqking said:**
> ..sudo means superuser do
This is not true.  Sudo means *_switch user_* and do.  From the main [**_[COLOR="DarkSlateGray"]sudo website[/COLOR]_**]("http://www.gratisoft.us/sudo/") > Sudo (su "do") allows a system administrator to delegate authority to give certain users (or groups of users) the ability to run some (or all) commands as root **or another user** while providing an audit trail of the commands and their arguments. 
More from [**[COLOR="DarkSlateGray"]Wikipedia[/COLOR]**]("http://en.wikipedia.org/wiki/Sudo")

---

### Post by haqking on 2012-04-12
> **bab1 said:**
> This is not true.  Sudo means *_switch user_* and do.  From the main [**_[COLOR="DarkSlateGray"]sudo website[/COLOR]_**]("http://www.gratisoft.us/sudo/")  
More from [**[COLOR="DarkSlateGray"]Wikipedia[/COLOR]**]("http://en.wikipedia.org/wiki/Sudo")

well yeah you are correct and doing what i do which is be pedantic ;-)


sudo is a concatenation of "su" and "do" and su means switch user amongst other meanings.

however it is also referred to as superuser do as you are elevating privelege for the logged on user and not switching user, as "su" means superuser or switch user or set user.

so we are both correct as "su" means switch user/set user but if you dont supply an account name it means superuser

oh and try not to rely on wikipedia too much you know anyone can edit it right ;-)

Peace

---

### Post by winh8r on 2012-04-12
> **haqking said:**
> well yeah you are correct and doing what i do which is be pedantic ;-)

Peace


And there is nothing wrong with that.

The problem only arises when people fail to admit that they can be pedantic!!

you're safe here :lolflag:

---

### Post by bab1 on 2012-04-12
> **haqking said:**
> well yeah you are correct and doing what i do which is be pedantic ;-)


sudo is a concatenation of "su" and "do" and su means switch user.

however it is also referred to as superuser do as you are elevating privelege for the logged on user and not switching user.

Peace
While the default is to *switch user *to root, it doesn't change its name or it operating characteristics.

If you are teaching (and I assume your are on this forum) you could at least be correct in your pedanticism.  :-)

If not you help to perpetuate incorrect thought.

---

### Post by haqking on 2012-04-12
> **bab1 said:**
> While the default is to *switch user *to root, it doesn't change its name or it operating characteristics.

If you are teaching (and I assume your are on this forum) you could at least be correct in your pedanticism.  :-)

If not you help to perpetuate incorrect thought.

the su from sudo means switch user yes but also superuser and/or set user

[http://www.computerhope.com/unix/usu.htm#01](http://www.computerhope.com/unix/usu.htm#01)
[http://en.wikipedia.org/wiki/Su_(Unix](http://en.wikipedia.org/wiki/Su_(Unix)) (I hate wikipedia)


but we could go back and forth linking resources all day.

I dont want to argue, i stand by my original post.

And i believe the teaching i did worked as it explained the point.

OH you couold also read the original code for "su" from dennis ritchie and ken thompson [http://pthree.org/2009/12/31/the-meaning-of-su/](http://pthree.org/2009/12/31/the-meaning-of-su/)

at end of day you can use any of the terms we have used for it.

Peace

---

### Post by bab1 on 2012-04-12
> **haqking said:**
> ...

OH you couold also read the original code for "su" from dennis ritchie and ken thompson [http://pthree.org/2009/12/31/the-meaning-of-su/](http://pthree.org/2009/12/31/the-meaning-of-su/)

I agree we are both "beating a dead horse" here and may never really agree.

Who is Aaron Toponce to provide the definition of sudo?  I would think that would be the province of the sudo developers: [**_[COLOR="DarkSlateGray"]http://www.gratisoft.us/sudo/[/COLOR]_**]("http://www.gratisoft.us/sudo/").

There are many comments and oddities in the original code of primitive unix.  Many functions were, and still are inspiration for later efforts.  The primitive ***su's*** pointed out in Topance's piece certainly point this out.

In short The name and definition is in the eye of the creator (owner), not the user.

I do agree this is enough of this discussion.  ;-)

Pedantically,

---

### Post by haqking on 2012-04-12
> **bab1 said:**
> I agree we are both "beating a dead horse" here and may never really agree.

Who is Aaron Toponce to provide the definition of sudo?  I would think that would be the province of the sudo developers: [**_[COLOR="DarkSlateGray"]http://www.gratisoft.us/sudo/[/COLOR]_**]("http://www.gratisoft.us/sudo/").

There are many comments and oddities in the original code of primitive unix.  Many functions were, and still are inspiration for later efforts.  The primitive ***su's*** pointed out in Topance's piece certainly point this out.

In short The name and definition is in the eye of the creator (owner), not the user.

I do agree this is enough of this discussion.  ;-)

Pedantically,

Su was created by Ritchie and thompson (eye of the creator), the original purpose and meaning was superuser.

Over time it has changed especially with Linux and all terms used superuser/switch-user/setuser are all valid.

oh and i wasnt concerned with Aaron Toponce definitions merely the fact the source code was there, ive seen it before and couldnt find the original.

The end.

Peace

---

