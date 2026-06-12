---
title: "A Simple Newbie Question"
date: 2010-02-14
forum: General Help
---

### Post by bmak on 2010-02-14
Hello All,

I have a newbie question for you.

When I am logged into my Ubuntu desktop (v8.10) as me and I create a folder for example; mkdir Bob. I go back to review the new folder only to find that it's owner is root.

If I create a folder in my account should I not be the owner?

Thanks and apologies for the banality.

BMAK

---

### Post by giammy on 2010-02-14
Hi,

when you create a folder, the owner is the user that created it:
if you run the command "whoami" which is the result?

bye

---

### Post by cjhabs on 2010-02-14
Does the command "whoami" return your user name?
What is your uid? You can check this by "cat /etc/passwd" and looking at the 3rd field for your username. I assume it is not 0?
Also run "alias | grep mkdir" Does this return anything - this will show if mkdir is aliased to do something different that what you expect.

---

### Post by OpSecShellshock on 2010-02-14
Are you running the mkdir command from somewhere in your home directory (and without elevating your privileges beforehand)?

---

### Post by bmak on 2010-02-14
Hi Folks,

Thanks for the very speedy response.

As you might expect, now that I have asked the question I can't reproduce the problem!

Here is the background.

I am trying to configure Amanda Enterprise Backup. The system is in place and functions at a basic level.

As a next step I need to configure a NAS device to act as the VTL repository. I have gathered information on this process and it appears that one creates a local folder (*in my example, "Bob"*) and then mounts the NAS shared folder in the local folder.

I have practiced this and it seems to work, but the Amanda system won't backup to the mapped drive, it keeps generating an error about permissions. So I have been trying to figure this out. 

It is clear that at some stage the is an issue with folder permissions (*or at least, that is how Amanda sees it*) but I can't find out where the problem is.

The strange thing is that I was trying to look at the permissions for the local folder and it kept telling me that the folder belonged to 'root' even though it was created in the amandabackup user account.

Anyway, thanks for the response. Most impressive.

BMAK

---

### Post by bmak on 2010-02-14
> **OpSecShellshock said:**
> Are you running the mkdir command from somewhere in your home directory (and without elevating your privileges beforehand)?

OpSecShellshock - Actually you may be onto something here. Before creating the folder I have had to mess about with several other setting and will have included 'su' prior to the actual command.

I have also been trying to get the right access by using a 'chmod' statement as recommended by Amanda support.

It's possible that this effected who owns the folder. 

As you may have guessed, I am trying to learn as I go along here - I am not a native Linux user and many of the subtleties are lost on me.

Regards

BMAK

---

### Post by pirateghost on 2010-02-14
> **bmak said:**
> OpSecShellshock - Actually you may be onto something here. Before creating the folder I have had to mess about with several other setting and will have included 'su' prior to the actual command.

I have also been trying to get the right access by using a 'chmod' statement as recommended by Amanda support.

It's possible that this effected who owns the folder. 

As you may have guessed, I am trying to learn as I go along here - I am not a native Linux user and many of the subtleties are lost on me.

Regards

BMAK

su will actually create it AS root

try sudo chown amandabackupuser -R /path/to/directory

---

### Post by bmak on 2010-02-14
> **pirateghost said:**
> su will actually create it AS root

try sudo chown amandabackupuser -R /path/to/directory

Hi pirateghost

This seemed to work well, but as with all things, it generated a new problems.

It would appear that the folder needs to be exclusive to no-one but the 'amandabackup' account. I am seeing the following error;

"*must not be accessible to any group or user other than 'amandabackup' (mode=40755). This check can be disabled using the "Show Security Warnings" setting on Admin|Preferences.*"

Is there a way to make a folder exclusive to a specific user?

BMAK

---

### Post by sandyd on 2010-02-14
> **bmak said:**
> Hi pirateghost

This seemed to work well, but as with all things, it generated a new problems.

It would appear that the folder needs to be exclusive to no-one but the 'amandabackup' account. I am seeing the following error;

"*must not be accessible to any group or user other than 'amandabackup' (mode=40755). This check can be disabled using the "Show Security Warnings" setting on Admin|Preferences.*"

Is there a way to make a folder exclusive to a specific user?

BMAK
chmod 664

---

### Post by tekkidd on 2010-02-14
make sure you DONT do sudo mkdir xxxxx or execute su beforehand this will make all files you create owned by root 

also if you create a file and it is owned by the wrong person do sudo chown <newuser> <filename>

---

