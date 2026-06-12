---
title: "Turn off all password asking"
date: 2010-10-12
forum: General Help
---

### Post by maconga on 2010-10-12
I am running Ubuntu 10.10 in a VM and I want to disable ALL password prompts.

I understand ALL the security risks, and I accept them.

---

### Post by Old_Grey_Wolf on 2010-10-12
After looking at your join date, I'm surprised you don't know better than ask that question on this forum. You need to google elsewhere.

If you got an answer to your post, you may understand the security risks, and accept them; however, someone unknowingly may execute the same commands without understanding the risks.

---

### Post by WorMzy on 2010-10-12
```
sudo visudo
```

---

### Post by yetiman64 on 2010-10-12
> **maconga said:**
> I am running Ubuntu 10.10 in a VM and I want to disable ALL password prompts.

**I understand ALL the security risks, and I accept them**.

[http://www.asamad.net/?p=47](http://www.asamad.net/?p=47) for passwordless sudo access (while still in a user account)

Please have a look at the link #4 (Rootsudo documentation) in my sig as it has good information for you regarding sudo. yetiman64.

---

### Post by wheels666 on 2010-10-15
Me too - I'm running Ubuntu 10.04  and I want to disable ALL password prompts.

Any nice straight forward answers, preferably involving menus rather than terminal much appreciated

( I have four dual boot computers, and my data is all on an external HD which someone - with some difficulty - could steal, but that HD is backed up to another HD and kept in a safe in another building - now that's my idea of security - what is a password on my Ubuntu o/s going to do? - if anyone gets to my computer, that they might update my packages is the least of my worries!)

Sorry if i freak anyone out, but this Linux password mania is perplexing

---

### Post by wheels666 on 2010-10-15
**it sounds so simple..BUT.... **

"Find the line that says %admin ALL=(ALL) ALL" really is a bit of a killer!
that and the bit where the cursor sticks on the first # thing so i couldn't edit it anyway...


**the easy instructions**

[COLOR=#000000][FONT=Times New Roman][FONT=Tahoma]Open the terminal window from Applications --> accessories --> terminal, run the command:
[INDENT]sudo visudo
[/INDENT]Find the line that says
[INDENT]%admin ALL=(ALL) ALL
[/INDENT]and change it to
[INDENT]%admin ALL=(ALL) NOPASSWD: ALL
[/INDENT][/FONT][/FONT][/COLOR]
**what's in my terminal**


# /etc/sudoers
#
# This file MUST be edited with the 'visudo' command as root.
#
# See the man page for details on how to write a sudoers file.
#

Defaults        env_reset

# Host alias specification

# User alias specification

# Cmnd alias specification

# User privilege specification
root    ALL=(ALL) ALL


:confused:
i'm sure this bugs some Linux users, but windows users have sort of survived without passwords for many years, and we don't really care about the security risks, it's quite normal - until i give up my xp dual boots all this extra security is only theoritical

---

### Post by SeijiSensei on 2010-10-15
> **wheels666 said:**
> i'm sure this bugs some Linux users, but windows users have sort of survived without passwords for many years, and we don't really care about the security risks, it's quite normal - until i give up my xp dual boots all this extra security is only theoritical

That's the attitude that leads to [millions of computers]("http://www.microsoft.com/security/sir/keyfindings/default.aspx#section_5_1") being herded into botnets and used to flood the Internet with spam and conduct extortionate denial-of-service attacks against websites. *You* may have "survived," but the Internet as a whole has suffered greatly from such cavalier attitudes toward security.  What about the thousands of people who routinely pay places like BestBuy hundreds of dollars a year to clean the crap they've collected off their computers?  I don't think they'd agree they've not been harmed if they understood why it happened.

---

### Post by kerry_s on 2010-10-15
press the down arrow key or maximize your terminal before you run the command.

you don't need the "(ALL)" part.

---

### Post by ActionParsnip on 2010-10-16
If you do do this your system will lose ALL security, including online security and user security. All your SSL cookies will be fully accessible to any malicious code which may be in Javascript or flash items in websites and any IRC hacks that succeed will have 100% to ANYTHING in your system including your keyring which may have passwords for web based servers and local systems, giving them further access to PCs on the LAN you are connected to

What you are doing is completely NOT advised. You clearly do NOT understand the implications AT ALL.

---

### Post by cariboo on 2010-10-16
The way Linux is designed, it to not only protect your data, but to protect the rest of us on the internet too. It would be pretty trivial for a bad guy to take over your system to use in a bot net, or turn it into a spam relay the way you want to set it up. 

When your system gets taken over, and it will. Please don't come back here looking for help to fix your system.

---

### Post by 3rdalbum on 2010-10-16
> **Old_Gray_Wolf said:**
> After looking at your join date, I'm surprised you don't know better than ask that question on this forum. You need to google elsewhere.

If you got an answer to your post, you may understand the security risks, and accept them; however, someone unknowingly may execute the same commands without understanding the risks.

Congratulations, Old Grey Wolf was correct and we now have Windows users turning off their security on Linux. What a great time to write some Linux aware.

---

### Post by Smartflight on 2010-10-16
> **cariboo907 said:**
> The way Linux is designed, it to not only protect your data, but to protect the rest of us on the internet too. It would be pretty trivial for a bad guy to take over your system to use in a bot net, or turn it into a spam relay the way you want to set it up. 

When your system gets taken over, and it will. Please don't come back here looking for help to fix your system.

I second that.
It's annoying that I have to write the password so many times- but  that's okay. It's for my security..and it feels right to be "protected"

---

### Post by pnguine on 2010-10-16
What about the keyring thing?

---

### Post by yetiman64 on 2010-10-16
> **pnguine said:**
> What about the keyring thing?

@ pnguine, If your system is set up correctly you won't get asked for a password re the keyring (just checked, my keyring has 3 entries for logins), only when there is a setup error on my machine does that happen (I have googled using site tags for UF to fix that problem myself in the past).

@ everyone else,
I do not support the turning off of passwords myself for the very reasons others above me have stated. [B]

The only reason for my previous post was the OP indicated the use of a VM [/B](which has the ability to take snapshots of the Ubuntu install and reinstall in very little time if compromised). My post was also held back for about 2 - 2.5 hours while I PM'ed a moderator for an opinion on it.

**Using that info on a full install is foolhardy IMO.**

Cheers, yetiman64

---

