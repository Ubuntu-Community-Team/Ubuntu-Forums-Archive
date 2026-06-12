---
title: "How do I start fetchmail for everyone at boot?"
date: 2011-10-20
forum: General Help
---

### Post by AlexBooton on 2011-10-20
Hi,

I just rebooted my server and fetchmail didn't start.

I have a /etc/fetchmailrc file with directives to retrieve mail for all users.  This file does not have a dot (i.e. it is NOT .fetchmailrc).

I had set the owner to root because the last time I started it from the command line I got a message that /etc/fetchmailrc had to be owned by the user.  Accordingly I changed the owner to root.

Then I rebooted and fetchmail didn't start.  I checked and found that the owner had been changed to fetchmail.  

I'm pretty sure I didn't do that.  Did fetchmail do it?

So what do I do now?  Who is supposed to own fetchmailrc?  How do I set it to start at boot?

Thanks,

AB

---

### Post by dcstar on 2011-10-21
> **AlexBooton said:**
> Hi,

I just rebooted my server and fetchmail didn't start.

I have a /etc/fetchmailrc file with directives to retrieve mail for all users.  This file does not have a dot (i.e. it is NOT .fetchmailrc).

I had set the owner to root because the last time I started it from the command line I got a message that /etc/fetchmailrc had to be owned by the user.  Accordingly I changed the owner to root.

Then I rebooted and fetchmail didn't start.  I checked and found that the owner had been changed to fetchmail.  

I'm pretty sure I didn't do that.  Did fetchmail do it?

So what do I do now?  Who is supposed to own fetchmailrc?  How do I set it to start at boot?

Thanks,

AB

[http://ubuntuforums.org/showthread.php?t=1198625](http://ubuntuforums.org/showthread.php?t=1198625)

---

### Post by AlexBooton on 2011-10-21
> **dcstar said:**
> [http://ubuntuforums.org/showthread.php?t=1198625](http://ubuntuforums.org/showthread.php?t=1198625)

Thanks, 

That was a big help.

But I still have a question regarding the ownership of /etc/fetchmailrc.

When I try to start the daemon from the command line with:
   fetchmail -d 60 -f /etc/fetchmailrc

I get "file /etc/fetchmailrc must be owned by you"

I am root when I do this.

OK, I can understand that message.  BUT what happens when I have the same command in /etc/rc.local.  Who is the user running rc.local.  I assume that would be root.  So does that require that root be the owner of fetchmailrc? 

I mentioned in my first message that I had changed the owner of fetchmailrc to root but somehow it got changed to fetchmail.

So will it run as root?

Thanks,

AB

---

