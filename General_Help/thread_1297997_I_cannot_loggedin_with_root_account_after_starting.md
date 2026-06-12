---
title: "I cannot loggedin with root account after starting my system."
date: 2009-10-22
forum: General Help
---

### Post by mlinuxuser on 2009-10-22
I cannot logged in with root account after starting my system. How to login? What are all the benefits of login as root ?

---

### Post by phillw on 2009-10-22
No benefits - lots of dis-advantages

Always log in as yourself.

use sudo, for when you need root access - It gives you that few extra vital seconds to think something through before you do something real dumb (Speaking from painful experience).

Read this thread - I wish I had !!!!

[http://ubuntuforums.org/showthread.php?t=716201](http://ubuntuforums.org/showthread.php?t=716201)

Welcome to Ubuntu and to this forum.

Phill.

---

### Post by ColdFFF on 2009-10-22
Ubuntu is designed in such a way that you do NOT log in as root.

Instead, the account you create during installation is an admin account, from which you can perform root commands by typing "sudo" before the command.

---

### Post by alphaniner on 2009-10-22
```
No benefits - lots of dis-advantages
```

Way to go objectivity!

---

See also [https://wiki.ubuntu.com/RootSudo]("https://wiki.ubuntu.com/RootSudo")

---

### Post by tarps87 on 2009-10-22
> **phillw said:**
> No benefits - lots of dis-advantages

Always log in as yourself.

use sudo, for when you need root access - It gives you that few extra vital seconds to think something through before you do something real dumb (Speaking from painful experience).

Read this thread - I wish I had !!!!

[http://ubuntuforums.org/showthread.php?t=716201](http://ubuntuforums.org/showthread.php?t=716201)

Welcome to Ubuntu and to this forum.

Phill.

There are advantages and a fair few disadvantages with the way sudo is implemented, but in the case of a new user there is no noticeable advantage.

---

### Post by mlinuxuser on 2009-10-22
OK. So the ubuntu developers can login as root in their system. right? I think the ubuntu development team is running this forum, isn't? If they dont want users to login as root they why still they give such account in system? Correct me If I'm wrong

---

### Post by ColdFFF on 2009-10-22
The root login is still there, however for 99% of the things you need it for you can just use sudo.

Additionally [there is a forum policy on log-in-as-root tutorials]("http://ubuntuforums.org/showthread.php?t=716201") linked in a previous post.
> To sum it up, if you can't figure out how to log in as root in Ubuntu, then you should be educated on how to use Ubuntu's sudo security model properly; and if you can figure out how to log in as root in Ubuntu and want to, then you certainly don't need a tutorial on how to do it.

---

### Post by tarps87 on 2009-10-22
> **mlinuxuser said:**
> OK. So the ubuntu developers can login as root in their system. right? I think the ubuntu development team is running this forum, isn't? If they dont want users to login as root they why still they give such account in system? Correct me If I'm wrong

I don't know if they all do.
The Ubuntu development team is not running the forum, yes is is supported by Canonical and there may be some developers here but I would say the majority are not developers.
Freedom, that's why you can unlock the root account. It is against the forum code to say how to.
If you search around you can find the facts about root and sudo, then you can make up your own mind.

---

### Post by mlinuxuser on 2009-10-22
I will be happy If I informed with question,What security threat will happen If all know the way to login as root. Note that  I dont ask about the way to login as root.

I am sure that I wont broke the forum rules by asking the questions more on this.

---

### Post by mlinuxuser on 2009-10-22
thanks for the kind response guys and Since I am new to this forum, I just now aware of this rule.

---

### Post by P4man on 2009-10-22
> **mlinuxuser said:**
> I will be happy If I informed with question,What security threat will happen If all know the way to login as root. Note that  I dont ask about the way to login as root.

I am sure that I wont broke the forum rules by asking the questions more on this.

All the answers you could wish for here:
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by tarps87 on 2009-10-22
Although this won't apply to all users, say said user logged in as root then ran some commands to fix their graphics card, now they saw another command which removes all the files of the hard drive, the idea is that using sudo will make said user think about it.
I can't remember the word for it but it is basically physiological security.
Or at least this is my understanding.

---

### Post by mlinuxuser on 2009-10-22
UBUNTU is interesting indeed

---

### Post by P4man on 2009-10-22
From my above link: 
> 
Benefits of using sudo

Some benefits of leaving root logins disabled by default include the following:

    * The Ubuntu installer has fewer questions to ask.
    * Users don't have to remember an extra password (i.e. the root password), which they are likely to forget.
    *

      It avoids the "I can do anything" interactive login by default (e.g. the tendency by users to login as an "Administrator" user in Microsoft Windows systems), you will be prompted for a password before major changes can happen, which should make you think about the consequences of what you are doing.
    *

      sudo adds a log entry of the command(s) run (in /var/log/auth.log). If you mess up, you can always go back and see what commands were run. It is also nice for auditing.
    *

      **Every cracker trying to brute-force their way into your box will know it has an account named root and will try that first**. What they don't know is what the usernames of your other users are. Since the root account password is locked, this attack becomes essentially meaningless, since there is no password to crack or guess in the first place.
    *

      Allows easy transfer for admin rights, in a short term or long term period, by adding and removing users from groups, while not compromising the root account.
    * sudo can be setup with a much more fine-grained security policy.
    * The root account password does not need to be shared with everybody who needs to perform some type of administrative task(s) on the system (see the previous bullet).
    * The authentication automatically expires after a short time (which can be set to as little as desired or 0); so i**f you walk away from the terminal after running commands as root using sudo, you will not be leaving a root terminal open indefinitely. **

---

### Post by mlinuxuser on 2009-10-22
> **P4man said:**
> From my above link:

Benefits of using sudo

Some benefits of leaving root logins disabled by default include the following:

    * The Ubuntu installer has fewer questions to ask.
    * Users don't have to remember an extra password (i.e. the root password), which they are likely to forget.
    *

 It avoids the "I can do anything" interactive login by default (e.g. the tendency by users to login as an "Administrator" user in Microsoft Windows systems), you will be prompted for a password before major changes can happen, which should make you think about the consequences of -what you are doing.
    ----- ------------ ----


thanks for the information. I am learning a lot nowadays after started using ubuntu. I think that;s why   they call these as opensource. Really UBUNTU is interesting. The Core Development team and other developers must be appreciated .

---

### Post by aysiu on 2009-10-22
The forum policy and the community documentation have been posted. Read those, and you will know everything you need to know about root logins.

---

