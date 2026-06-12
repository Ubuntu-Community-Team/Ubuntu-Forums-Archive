---
title: "How to migrate all Outlook email into Ubuntu"
date: 2010-10-18
forum: General Help
---

### Post by Andy06 on 2010-10-18
I am installing Ubuntu on a bunch of computers for some people and they all have tonnes of email on their HDDs in Outlook.

How/What is the best way to migrate all of the email to Ubuntu? Also which app would you recommend on Linux for desktop email (Thunderbird, Evolution, something else?)

I have no idea about desktop email since I only ever use webmail.

I've read some online guides but they seemed unnecessarily complicated. Nevertheless, links to such guides are much appreciated if you can provide them :)

---

### Post by amauk on 2010-10-19
In outlook, export all email as a CSV (comma separated values) file

Then you can import this into any mail program you like

As for which mail client to use
that's really personal preference, but Evolution is the most "outlook-like"

---

### Post by aysiu on 2010-10-19
I'd recommend installing Thunderbird in Windows to import the Outlook mail:
[https://wiki.mozilla.org/Thunderbird:Help_Documentation:Migrating_to_Mozilla_Thunderbird#Importing_Your_E-mail](https://wiki.mozilla.org/Thunderbird:Help_Documentation:Migrating_to_Mozilla_Thunderbird#Importing_Your_E-mail)

And then copying the Thunderbird user folder from Windows to Ubuntu.
[http://support.mozillamessaging.com/en-US/kb/Profiles#Where_is_my_profile_stored_](http://support.mozillamessaging.com/en-US/kb/Profiles#Where_is_my_profile_stored_)

---

### Post by Andy06 on 2010-10-19
@amauk @aysiu

I heard some bad cases of profile corruption and errors when transferring the profile across OSes. I have no experience with Thunderbird (or any desktop email client) but I know transferring Firefox profiles from Windows to Linux is a 95% affair (Works 95% of the time).....

---

### Post by dcstar on 2010-10-20
> **aysiu said:**
> I'd recommend installing Thunderbird in Windows to import the Outlook mail:
[https://wiki.mozilla.org/Thunderbird:Help_Documentation:Migrating_to_Mozilla_Thunderbird#Importing_Your_E-mail](https://wiki.mozilla.org/Thunderbird:Help_Documentation:Migrating_to_Mozilla_Thunderbird#Importing_Your_E-mail)

And then copying the Thunderbird user folder from Windows to Ubuntu.
[http://support.mozillamessaging.com/en-US/kb/Profiles#Where_is_my_profile_stored_](http://support.mozillamessaging.com/en-US/kb/Profiles#Where_is_my_profile_stored_)

Yep, the Evolution Help has a specific section on importing Outlook mail data (if only people would **read** it), and it basically says to do what you have just outlined.

---

### Post by kumaryu on 2010-10-20
1. On each computer, make sure that Outlook is using *.pst files to store the mailbox. If the mail clients are connecting to MS Exchange, they probably aren't.

2. Prep:
a. Make sure you've located ALL the .pst files the user/client is using. If the mailboxes have been in use for a long time, its quite likely that there are several .pst files in use. (Some may be copies of old mailboxes or archives.)

b. If you are migrating a number of PCs, make sure you've located all the .pst files on all the PCs before starting the migration of the first machine.
 
c. If you have a spare PC of an equivalent spec, use that for the first user. (This assumes that its an office/company type environment...) That way, you can ensure that the user is happy before wiping the HD on the old PC. If the migrations are on private/personal PCs, make an image of the HD using CloneZilla or Ghost. Its always a good idea to have the images of the old HDs stored somewhere for a while, just in case.

d. Do the migration one by one, so as to avoid having more than one machine out of service at any given time.


3. Before doing anything with the files, make a copy of the .pst files. Work on the copy and not the original. Name them clearly if there are more than one. By working on a copy, you will always have a working mailbox (with Outlook) to go back to.

4. If the mailbox files are stored as *.pst files, you should be able to import them into Thunderbird. From Thunderbird, to Evolution. This is usually the best method since it tends to keep the integrity of mail and folder attributes the best.

---

### Post by HermanAB on 2010-10-20
Howdy,

You can use Thunderbird to do a conversion, but you will get varying levels of success due to occational funny characters in the Outlook folder names.

The best way to transfer mail is via an IMAP server.  To do this, open a Google mail account, then use Outlook and click-drag-drop the mail from the old account to the new Google IMAP account and in Evolution, do the reverse, click-drag-drop from the Google IMAP account to the local account.  Do not forward the mail - use drag and drop.

If you set up a local mail server with for example Citadel then you only need to copy the mail once.

---

### Post by Andy06 on 2010-10-20
Wait, One of you said .csv files and one said .pst
I have also heard both in real life (as advice for migrating)

Which is better?
I think these people are actually moving from Outlook EXPRESS rather than outlook, so basically the precursor of Windows Live Mail (the consumer client), does this mean I should move them to Thunderbird instead of Evolution?

---

### Post by kumaryu on 2010-10-21
Outlook Express and Outlook mailbox files are stored as *.pst files.

Thunderbird is able to import *.pst files.

Thunderbird stores mailbox files in mbox format. Mbox is a  standard file format for mailbox storage.

Evolution is able to read/import mbox files.

*.csv (comma separated values) is a text file in which separate data items are delimited by a comma. Its frequently used as a  simple export/import file format.

---

### Post by TNT1 on 2010-10-21
Evo imports .pst files.

---

### Post by kumaryu on 2010-10-21
I understand that Import PST feature (plugin) was announced for Evolution some time ago but there were some issues relating to its dependency on libpst. Looking at the version Evolution (2.30.3) in Maverick, the single file import feature does not offer .pst as one of the file formats supported. (This however may be specific to my installation)

One issue appears to be that .pst files come in different flavour depending on the version of Outlook used. As a proprietary format, keeping up with the changes imposed by MS appears to be posing some issues for those maintaining this feature.

It would be good to know what the current status is.


BTW, about Outlook (pst) >> Thunderbird migration: 
1. Use Windows version of Thunderbird (in Windows) to import .pst files.
2. Thunderbird mailbox files in Windows are normally kept:
%USERPROFILE%\ApplicationData\Thunderbird\Profiles\XXXXXXXX.default\Mail\
3. Each mailbox folder is stored as two files. The mail data is kept in the one without extensions. The .msf file contains metadata specific to Thunderbird and is not needed for migration.

---

### Post by kumaryu on 2010-10-21
Although this thread has been a discussion about migration of Outlook "email" to Ubuntu (Thunderbird or Evolution), I think it would be appropriate to add that such a migration in the real world  would most likely require the migration of Outlook Contacts and  Calendar data as well.

Contacts:
Outlook contacts are stored either in .pst files or in .pab files.
Outlook can export Contacts as .csv, .ldif, or .vcf (vCard) files.
Thunderbird (windows): can directly read Outlook address book files. So this may be the easiest inter-change method.
Evolution can import .vcf formats. If you have multiple .vcf files exported from Outlook, you can use:
 cat *.vcf > contacts.vcf
at the terminal in the directory where the .vcf files are stored to combine them into a single "contacts.vcf" file. You can just import this single file into Evolution.

Calendar:
Outlook calendars may be exported as .ics (iCal) or .csv files.
Thunderbird supports import from .ics and .csv formats.
Evolution is able to import .ics files.

---

