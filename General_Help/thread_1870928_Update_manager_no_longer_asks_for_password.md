---
title: "Update manager no longer asks for password"
date: 2011-10-28
forum: General Help
---

### Post by astrochase on 2011-10-28
In 11.10, update-manager no longer always asks for credentials when it's about to do an update. This is new behavior that is unexpected. Is this normal?

---

### Post by mjuhasz on 2011-10-28
This is supposed to increase the usability of the system. Local admins are allowed to update already installed software without password.

It's a change that happened in the [policykit]("https://launchpad.net/ubuntu/oneiric/+source/policykit-desktop-privileges/+changelog") in the Oneiric cycle.

Other tweaks include allowing local admins to create and edit system-wide NetworkManager connections or to do the less harmful usb-creator actions (mounting and writing image) without a password.

---

### Post by bryncoles on 2011-10-28
Really?  That sounds like a silly idea!  Why don't we also allow remote access to the system for everyone too, in case someone wants to do some 'administration' from [s]their botnet[/s] away from their desk?

Is there a simple, straightforward way to fix this security flaw?

---

### Post by mjuhasz on 2011-10-28
For inspiration you can see the current policykit config here: /var/lib/polkit-1/localauthority/10-vendor.d/com.ubuntu.desktop.pkla

You can make system-wide changes by placing your own config in /etc/polkit-1/localauthority/50-local.d/

You can read about the syntax and more about policykit [here]("http://manpages.ubuntu.com/manpages/oneiric/man8/pklocalauthority.8.html").


BTW, for installing software you still need password, just like for any other action that can potentially change (in wrong hands, cause harm to) your system.
Updating the already installed software by the admin is considered safe and should be done with the least inconvenience. The assumption is that if you are part of the admin group you are part of it for a reason: you know how to administer your system and your tools should support you and not get into your way.

---

### Post by dcstar on 2011-10-28
> **mjuhasz said:**
> 
...........
Updating the already installed software by the admin is considered safe and should be done with the least inconvenience. **The assumption** is that if you are part of the admin group you are part of it for a reason: you know how to administer your system and your tools should support you and not get into your way.

Really?, I reckon that "the assumption" is that users migrating from other OSs complain about all the security the Linux has (which usually protects them from the idiot things that an OS like Windows allows them to do) and it could be part of a steady reduction in Linux security to reduce the noise from the complainers.

Non-admin users can already wipe pluggable drives without an admin password on the "assumption" that anything plugged into an external port deserves this convenience. I put in a bug report highlighting this as a security issue (one user could wipe another user's data) but was told quite firmly that it was no issue at all.

---

### Post by t0p on 2011-10-28
A small but real danger is that a sploit could be installed if it's disguised as an update.  I realise that removing the password requirement from update manager isn't going to save most users from this attack vector (most users tend to believe what update manager tells them and the password requirement is pretty much a rubber stamp exercise) but at least the password requirement acts to make the user pause for a moment.

---

### Post by BillyBoa on 2011-10-28
Before that we had a small discrepancy. For manual update it was needed a password, but for automatic updates, no!

---

### Post by Bobhuber on 2011-10-28
Glad to see someone getting a little sense. I've been using Ubuntu for quite a few years and the first thing I do is disable all password requirements on MY system. For those of you that want to have total control of everything on a multi user system you still have that capability as Administrator. And yes that is what the term is for and means. Linux (Ubuntu included) has migrated from a server based platform to a realy nice desktop environment . The everyday user does not want to enter a password to scratch his nose or load new software. Some of the security requirements in Ubuntu are good, some go way overboard.  This has nothing to do with migrating from another system and in fact discourages a lot of people from using Ubuntu.
I started out programing in Basic and was a System administrator using  Novel  3.11 before Windows was even around so no I'm by no means a noobe

---

### Post by Gremlinzzz on 2011-10-28
I don't really bother to read all updates anyways:popcorn:
so password for me is irrelevant:popcorn:

---

### Post by christophevr on 2012-01-29
Persons Can say what they wan't,

This now is a real heavy security bridge. It's one off the reasons why windows is so vulnerable.

The only and only User which should be allowed to override and or install any lib should be the super user only. 

The only possible next step will be that we will need and actif guardian off all ports. Perhaps is it the intention to make a commercial antivirus ???

Each ubuntu system is now very vulnerable to the standard lamers who are dooing nothing else as scanning the network world wide to force somwhere an entry.

Foor all Iff YOU care about SAFETY Turns this possibility off. I now simply removed this program completely

---

### Post by krizze on 2012-02-02
Well, I feel safe enough, knowing that I'm asked for a password if I'm trying to install something new. Also, repositories are signed, so packages signed with other keys will not be installed, at least not without warning.

PPA's are another thing, though, and if the user adds several PPA's,
it's easier for someone to put something malicious into an update.
Writing the password once more, though, does not prevent this.

---

