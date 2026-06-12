---
title: "Likewise-open + Sabayon any suggestions?"
date: 2010-10-02
forum: General Help
---

### Post by jeight on 2010-10-02
I have an LTSP server installed with Active directory authentication thanks to Likewise-Open.  The problem comes when trying to use the Sabayon user profile editor.  The editor only sees the AD builtin groups and groups designated to my ltsp host server. My Windows domain is SPARKY and my host is LTSP.  The only options the editor gives for groups are these:

BUILTIN\Administrators
BUILTIN\Backup Operators
BUILTIN\Guests
BUILTIN\Users
LTSP\Likewise Users
LTSP\Students

The only group that Sabayon with work with is the BUILTIN\Users because it is used to authinticate AD users. I made the SPARKY\Students part of my LTSP\Students group. LTSP\Students does recognize the users, but it still will not work with Sabayon menu editor. I'm at a loss here.
LOL I'm confusing myself. I hope someone out there understands this.

---

### Post by jeight on 2010-10-04
I figured this one out on my own. I had to manually include domain users and groups into the /etc/groups file. That allows things to work.

---

### Post by jprinty on 2011-03-22
Could you please go into more detail of how you did this. I am having the same issues. This is my first time for using Edubuntu in an AD environment and I have only been using Ubuntu for about 6 months, so i am still learning a lot. 

Thanks

---

### Post by pyperdown on 2011-04-18
> **jeight said:**
> I figured this one out on my own. I had to manually include domain users and groups into the /etc/groups file. That allows things to work.

I can't speak to likewise-open, but in an openldap environment if you want LDAP-py things to work you better dig a bit deeper.  You need to PULL the groups from ldap and not manually maintain your groups file.

Look at /etc/nsswitch.conf

Mine (actually all 200 linux boxen) look like this
[FONT=Fixedsys]
[FONT=Courier New]passwd:         compat files **ldap**
group:          compat files **ldap**
shadow:         compat files **ldap**[/FONT][/FONT]

Now don't just copy this, though it may work.  Find out what likewise-open wants.

But hand-editing /etc/group is the fast track to pain and suffering for you AND your users.

A quick query at [http://www.likewise.com/resources/documentation_library/manuals/open/likewise-open-guide.html](http://www.likewise.com/resources/documentation_library/manuals/open/likewise-open-guide.html) shows some guidelines for this. From what I read THERE it seems it uses dns for this, though that may simply be for machine resolution.

Do groups resolve outside of sabayon?

---

### Post by Bufke on 2011-08-17
I'm having this issue too, using OpenLDAP. Groups resolve just fine. When I type in "groups" I get exactly as I expect. However sabayon ignores them.

When you say hand editing /etc/group are you literally adding each user to a group? Doing so does allow sabayon to work, but defeats the entire purpose of LDAP.

---

