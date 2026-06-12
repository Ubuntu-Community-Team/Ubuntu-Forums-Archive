---
title: "System-&gt;Administration woes"
date: 2006-03-04
forum: General Help
---

### Post by EastKY_DO on 2006-03-04
Hello All,

I'm a newcomer to ubuntu although I have been using Linux for a while now.  The distro that I have been using is Mepis.  I decided to give ubuntu a trial and generally like it quite well.  I do have a significant frustration though.  Every time that I try to use one of the tools in the System -> Administration menu, it asks for a password.  I have entered the password for my user account (after reading the wiki about sudo) and to my frustration nothing happens.  The programs simply don't load and run.  If I use the root password created at intallation, the system tells me it's the wrong password.  I also found out today that the CUPS server is unavailable.  I think this may be related to the above problem, since I'm unable to setup anything in the admin section.  I'm ready to toss ubuntu if I can't find a solution to this problem.  I appreciate anyones help.

Doc :???:

---

### Post by Xian on 2006-03-04
First I would verify that your sudoers file is in order.
Try a simple command from a terminal:

$ sudo gedit

Does this work by opening the text editor with admin privileges?

AFAIK the cups admin is uniquely prohibitive of sudo usage in Breezy.
The rest of your admin functions should be accessible.

---

### Post by EastKY_DO on 2006-03-04
$ sudo gedit  does exactly nothing.  It just drops down to the next line and a new prompt.  What next?

---

### Post by Xian on 2006-03-04
That's not good. It should have asked for your user pass.
You need to possibly edit your sudoers file....

To get access you'll have to get admin privileges.
Boot Ubuntu in recovery mode and at the shell prompt:

$ visudo

That will open the sudoers file.
It should look similar to the one below.

Any questions?? Type 'man sudoers'.

```
# /etc/sudoers
#
# This file MUST be edited with the 'visudo' command as root.
#
# See the man page for details on how to write a sudoers file.
#

# Host alias specification

# User alias specification

# Cmnd alias specification

# Defaults

Defaults	!lecture,!tty_tickets,!fqdn

# User privilege specification
root	ALL=(ALL) ALL

# Members of the admin group may gain root privileges
%admin	ALL=(ALL) ALL
```

---

### Post by EastKY_DO on 2006-03-04
Okay,  I looked at the file and it was missing the last two lines.

# Members of the admin group may gain root privileges
%admin  ALL=(ALL) ALL

So, I used the su command and logged into a terminal window as root.  Then I used gedit from there to add the lines to the file.  I saved the file and rebooted the system.  After the reboot, nothing has changed.  Any other thing I'm missing? :confused:

---

### Post by EastKY_DO on 2006-03-04
I forgot to mention that it did ask for my password.  I entered it and nothing happened.  I think the reason that it didn't ask for my password before is because I had entered it from menu Sys->Admin dialog and it was still in the 15 min cache.  Also, if I logged into recovery mode and tried to use vi(le)  I would be lost.  ( I never learned to use vi. )  :-?

---

### Post by dante on 2006-03-04
Are you using sudo from the user account
you created during install?  If you're doing
it from a user you created,
make sure you're in the admin group.

Use the groups command at the command line
to see the groups you are a member of.

You shouldn't be having this problem provided
you are using sudo as the user you first created
during install (which will automatically be a member
of the admin group).

Note: *never* edit sudoers with gedit or any other
means other than the visudo command -- it ensures
the formatting of the file is correct before saving
(sudoers is sensitive to tabs vs spaces, etc).  
It uses vi commands, but you only need to know a
few basics to do a quick edit.

If the sudoers file is out of wack from trying to edit
directly, you can get into quite a mess (learned that
the hard way).

---

### Post by EastKY_DO on 2006-03-04
Yep, I'm in the adm group.  Thanks for the advise on sudoers.  I'll go change it with vi.

Doc

---

### Post by EastKY_DO on 2006-03-04
After I added the following to the sudoers file

# Members of the admin group may gain root privileges
 %admin ALL=(ALL) ALL

I later noticed that the term admin is reported in the groups file as adm  so I edited the sudoers file to the following and now the admin portion of the system menu works like it should.

# Members of the admin group may gain root privileges
 %adm ALL=(ALL) ALL

Thanks to all of you for the help!  :-D

Doc

---

### Post by pbransford on 2006-03-04
Vim commands? ick! For something that important with no other ways to do it should use something much simpler, like nano does it. Or at least have the option.

---

### Post by dante on 2006-03-04
[QUOTE=EastKY_DO]Yep, I'm in the adm group.  Thanks for the advise on sudoers.  I'll go change it with vi.

Doc[/QUOTE]

I didn't explain that very well.   To clarify, use the command
visudo to edit sudoers.  Among other protections, visudo will
not allow the file to be saved in a corrupt way after editing it.

The name of the utility implies vi, but it may in fact invoke
a different editor, depending on your environment.   I have
the EDITOR environment variable set to vi on my systems,
so visudo opens sudoers in vi for me.  In other words, using
vi is not protecting you when editing sudoers, using visudo is
(see man visudo).

In any case, glad you got things working.

---

