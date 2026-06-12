---
title: "What  triggers &quot;you have mail/no mail?&quot;"
date: 2010-11-27
forum: General Help
---

### Post by joseph blow on 2010-11-27
When logging on to some command line accounts, I always get a message about mail, telling me either  I   have new mail, or  I have no new mail. Other accounts don't display this message.  All of the accounts are using the same shell and the same profile/rc scripts.

Could anyone tell me exactly what it is that triggers the display of the message? 

Cheers,
Joey

---

### Post by mobilediesel on 2010-11-27
> **joseph blow said:**
> When logging on to some command line accounts, I always get a message about mail, telling me either  I   have new mail, or  I have no new mail. Other accounts don't display this message.  All of the accounts are using the same shell and the same profile/rc scripts.

Could anyone tell me exactly what it is that triggers the display of the message? 

Cheers,
Joey

The accounts that don't display anything about mail probably don't have postfix installed. The ones that DO tell you whether or not you have mail probably do have postfix installed.

---

### Post by joseph blow on 2010-11-27
> **mobilediesel said:**
> The accounts that don't display anything about mail probably don't have postfix installed. The ones that DO tell you whether or not you have mail probably do have postfix installed.

I don't quite follow what you mean by not having postfix installed. Postfix is installed on the system. It's not installed on a per-account basis.  I did wonder it it was some kind of per-account postfix config file that was causing the behaviour, but I'm not aware of any such files.

---

### Post by mobilediesel on 2010-11-27
> **joseph blow said:**
> I don't quite follow what you mean by not having postfix installed. Postfix is installed on the system. It's not installed on a per-account basis.  I did wonder it it was some kind of per-account postfix config file that was causing the behaviour, but I'm not aware of any such files.

There might be a per-account config file but I'm not sure. I didn't get the notices about having or not having mail until I installed postfix. I don't remember having to mess with a config file for it to do anything.

---

### Post by gmargo on 2010-11-27
It's based entirely on the presence and time stamps and size of the configured mail file(s), which defaults to /var/mail/$USER.  The login shell is doing the work - it checks the mail file(s) and periodically rechecks.  It has nothing to do with postfix, but the association is understandable, since you need some sort of [Mail Transfer Agent]("http://en.wikipedia.org/wiki/Mail_transfer_agent") to add content to the mail file.

---

### Post by joseph blow on 2010-11-27
Thanks for that. It does help, somewhat. It seems that "*su -*" is not behaving how I expected to. If I log in as *userx* I see the message. If I log in as another user and then "*su - userx*", I don't see the message. I'd always understood that "*su -*" ran the same scripts as a clean login, but that must not be the case. Or if it the case, then the mail-checking scripts are checking whether or not they're being called as the result of a login. I still haven't been able to find the code that actually checks the files in /var/mail and prints the message.

---

### Post by gmargo on 2010-11-27
> **joseph blow said:**
> I still haven't been able to find the code that actually checks the files in /var/mail

See mailcheck.c in the bash source code.

---

### Post by joseph blow on 2010-11-29
I didn't realise it was hardcoded into the shell itself. Now that I realise that it's the triggered by login rather than su -, I can see that the behaviour is consistent. Thanks for your help.

---

### Post by nothingspecial on 2010-11-29
From the login man page

```
  After a successful login, you will be informed of any system messages
       and the presence of mail. You may turn off the printing of the system
       message file, /etc/motd, by creating a zero-length file .hushlogin in
       your login directory. The mail message will be one of "You have new
       mail.", "You have mail.", or "No Mail." according to the condition of
       your mailbox.
```

---

### Post by joseph blow on 2010-11-29
Yes.  I know that you get the message when you login. I expected I would also get the message with "*su -*" because "*su -*" almost always has the same effect as a fresh login. It turns out that as far as the new mail message is concerned "*su -*" doesn't have the same effect as a fresh login.

---

### Post by nothingspecial on 2010-11-29
> **joseph blow said:**
> Yes.  I know that you get the message when you login. I expected I would also get the message with "*su -*" because "*su -*" almost always has the same effect as a fresh login. 

  su does not invoke a login shell

From gnu.org/software/coreutils/manual
> 
By default, su does not change the current directory.  It sets the environment variables HOME and SHELL from the password entry for user, and if user is not the super-user, sets USER and LOGNAME to user.  By default, the shell is not a login shell.If you want to trigger a login shell use the -l flag

> &#8216;-l&#8217;&#8216;--login&#8217; Make the shell a login shell.  This means the following.  Unset all environment variables except TERM, HOME, and SHELL (which are set as described above), and USER and LOGNAME (which are set, even for the super-user, as described above), and set PATH to a compiled-in default value.  Change to user's home directory.  Prepend &#8216;-&#8217; to the shell's name, intended to make it read its login startup file(s).

[http://www.gnu.org/software/coreutils/manual/html_node/su-invocation.html](http://www.gnu.org/software/coreutils/manual/html_node/su-invocation.html)

---

### Post by nothingspecial on 2010-11-29
In my haste I missed the "-"

But then, discussions of this nature are dodgy on this forum.

I`m bowing out, see here -

[http://ubuntuforums.org/showthread.php?t=716201](http://ubuntuforums.org/showthread.php?t=716201)

No disrespect to yourself, it is posting stuff on these boards that is frowned upon.

Cheers :D

---

### Post by joseph blow on 2010-11-29
"*su -l*" is synonymous with *"su -*". From the man page:

"[I]-, -l, --login
           Provide an environment similar to what the user would expect had the user logged in directly.[/I]" 

But neither of them will trigger the mail message. The only way to trigger the mail message is to use "*login*" to log in again.

---

### Post by nothingspecial on 2010-11-29
I know.

I said I missed it.

Night night.

---

### Post by joseph blow on 2010-11-29
#13 was in reply to #11.  You must have posted #12 while I was composing #13. I'm happy to leave it there. I'm clear about what it's doing now.

Cheers.

---

### Post by btsbits on 2012-06-05
this is done via PAM module and can be disabled by commenting out the following line in /etc/pam.d/sshd

    session    optional     pam_mail.so standard noenv # [1]


Sorry to bump an old thread but i was looking for the answer and finally found it. I hope this will help someone else.

---

### Post by lisati on 2012-06-05
Back to sleep, old thread.

---

