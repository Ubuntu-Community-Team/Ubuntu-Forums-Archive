---
title: "Quieting configuration dialogues with apt-get/dpkg"
date: 2010-10-07
forum: General Help
---

### Post by Tipo on 2010-10-07
Hello,

I am trying to write a script that configures my ubuntu machines with LDAP and Kerberos (via this guide [https://help.ubuntu.com/community/SingleSignOn](https://help.ubuntu.com/community/SingleSignOn))

My problem is that when I run the apt-get to install the required packages, dpkg spawns up configuration dialogue tui's like the one [pictured here]("https://help.ubuntu.com/community/SingleSignOn#Installing%20required%20packages").

I am going to be doing the configuration in another part of the script, so I don't want to configure the utilities with the tui -- I just want the packages to get installed. Is there any way I can silence apt/dpkg to prevent those dialogues from appearing?

Thanks in advance.

---

### Post by P4man on 2010-10-07
From man apt-get:

> 
 -y, --yes, --assume-yes
           Automatic yes to prompts; assume "yes" as answer to all prompts and
           run non-interactively. If an undesirable situation, such as
           changing a held package, trying to install a unauthenticated
           package or removing an essential package occurs then apt-get will
           abort. Configuration Item: APT::Get::Assume-Yes.


-q, --quiet
           Quiet; produces output suitable for logging, omitting progress
           indicators. More q's will produce more quiet up to a maximum of 2.
           You can also use -q=# to set the quiet level, overriding the
           configuration file. Note that quiet level 2 implies -y, you should
           never use -qq without a no-action modifier such as -d, 

But maybe you want to have a look at remastering ubuntu instead?

---

### Post by Tipo on 2010-10-08
Thanks -- I'll give this a shot.

I've been running CentOS on my workstations for a while, which was an easy setup with kickstart -- remastering might be the way I want to go. Thanks for the tip.

---

