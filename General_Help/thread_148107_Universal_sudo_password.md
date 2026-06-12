---
title: "Universal sudo password?"
date: 2006-03-21
forum: General Help
---

### Post by Michael%S on 2006-03-21
Hi all,
I'm in charge of the computers at my school ([Sudbury]("http://en.wikipedia.org/wiki/Sudbury_school") Jerusalem) and today I set up an ol' PIII box that broke down a few months ago and finally got repaired (well, rebuilt), as a clean Ubuntu box. So far I'm pretty much the only one using it and before I start giving people user accounts and letting them on I want to set one single password for sudo, so people who aren't authorized to make changes to the system can get help from people who are, during their own turns and while they are logged in.
I did
```
sudo passwd
```
and changed the password but it still asks for my own password and I now understand that's how it's supposed to work by default. What do I do to make the new password the one and only sudo password?

---

### Post by neoroses on 2006-03-21
instead of setting a sudo password set a SU password:

type

sudo passwd root 

it will then ask you for a new unix password - 

now when u wana do a sudo operation insted of tying sudo type su

:) hope that help :) sorry if it doesnt

---

### Post by Michael%S on 2006-03-21
[quote=neoroses]instead of setting a sudo password set a SU password:

type

sudo passwd root 

it will then ask you for a new unix password - 

now when u wana do a sudo operation insted of tying sudo type su

:) hope that help :) sorry if it doesnt[/quote]
If it's possible, I really prefer to leave the way things are done as-is and only change it so the password is the same for everybody.

---

### Post by barthel on 2006-03-21
[QUOTE=Michael%S]If it's possible, I really prefer to leave the way things are done as-is and only change it so the password is the same for everybody.[/QUOTE]
It's an option that can be set in the /etc/sudoers file (which must be edited with visudo).

Specifically, check out the rootpw, runaspw, and targetpw options in the sudoers man page.

However, given that you're doing this in a school environment, I would **strongly** suggest that you do not give the root password to everyone. Even giving it to your trusted few sudoers will quickly result in everyone having it. Also, someone could change that password and lock every other administrator out.

Although it's a bit more of a headache, you could simply use *su* in a terminal to let them execute commands as themselves. That would be a far safer option.

---

### Post by Michael%S on 2006-03-22
Well, this is a school based on trust and so far even though we have a few different passwords floating around, the only people who know them are supposed to know them.
That said, I'm beginning to think that it would be best to just leave the default configuration as is and try to work with that.
Could you give me a quick rundown of how we'd go about doing superuser things when logged on as regular users? I'm still quite new to all of this and this is as much a learning experience to me as it will be to the rest of the school community.

---

### Post by barthel on 2006-03-22
[QUOTE=Michael%S]Well, this is a school based on trust and so far even though we have a few different passwords floating around, the only people who know them are supposed to know them.
That said, I'm beginning to think that it would be best to just leave the default configuration as is and try to work with that.
Could you give me a quick rundown of how we'd go about doing superuser things when logged on as regular users? I'm still quite new to all of this and this is as much a learning experience to me as it will be to the rest of the school community.[/QUOTE]

Basically, it's just a matter of editing your /etc/sudoers file. (Which must be edited via the visudo command).

Let's assume you have a simple setup where you have a group of trusted users, all of whom are allowed to perform any root function. In that case, this would suffice:
```
# Host alias specification

# User alias specification
User_Alias      SYSOP=user1,user2,...usern

# Cmnd alias specification

# Defaults

# User privilege specification
root            ALL=(ALL) ALL
SYSOP           ALL=(ALL) ALL

```

Then each of them would be prompted for their own password whenever they try to perfom a "root" function via sudo or gksudo.

There are some excellent examples of more complex arrangements where different groups have different priviliges in the sudoers man page (**man sudoers**).

Good luck!

---

### Post by az on 2006-03-22
[QUOTE=Michael%S]Well, this is a school based on trust and so far even though we have a few different passwords floating around, the only people who know them are supposed to know them.
That said, I'm beginning to think that it would be best to just leave the default configuration as is and try to work with that.
Could you give me a quick rundown of how we'd go about doing superuser things when logged on as regular users? I'm still quite new to all of this and this is as much a learning experience to me as it will be to the rest of the school community.[/QUOTE]
As the first user on the computer, you get sudo priviledges.  You can use the users and groups tool to grant the same administrative priviledges to some select users.  They would have to type in their own passwords to escalate their priviledges.

Otherwise, you would need to create a dummy user with sudo priviledges (or root priviledges) and have those select users switch to that user before doing the tast.  It is just one more step to accomplish the same thing.  

If you wanted to revoke that privilege, you would have to change the pasword for that dummy user.  In the way I describe, you would just revoke that user's administration priviledges.

---

