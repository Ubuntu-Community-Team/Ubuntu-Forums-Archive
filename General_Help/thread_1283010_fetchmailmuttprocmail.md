---
title: "fetchmail/mutt/procmail"
date: 2009-10-05
forum: General Help
---

### Post by CloudyWind on 2009-10-05
Hi,

Delving in to the deep end of Linux based mail here and having some problems...

want to use Mutt as my mail client to read/send mail from my POP3 enabled gmail account.

I've installed:
procmail - to handle all the folders etc?
mutt - act as my mail client
fetchmail - provide the interface to gmail

Where I am at now:
- Fetchmail configured (.fetchmailrc below)
- Mutt configured (.muttrc below)
- procmail with basic config (.procmail below)

Trying to overcome a fetchmail part - if I run a fetchmail -c it returns 679 messages - I currently have 1 un-read email awaiting.

Am I missing something - I have changed the google setting to "archive emails accessed via pop3" and ideally I would just like to be able to use mutt to read new emails - not concerned about storage of mails (as they are archived by gmail). Insights????

rc files:
.muttrc:
```
# My email address
set pop_user="user.name@gmail.com"

set realname = "JB"
set sendmail = "/usr/bin/msmtp"

set spoolfile = "/var/spool/mail/localuserName"

# Folders!

set folder = "~/Mail"
set record = "+sent"
set postponed = "+postponed"
set move = no

mailboxes ! +Fetchmail +slrn +mutt
set sort_browser=alpha


# Cut out email headers
ignore *
unignore From: To: Cc: Subject: Date: # These are shown in the header

# To ensure mutt does not put localhost in from field
set from="user.email@gmail.com"
set use_from=yes
set envelope_from=yes

# Set vim as text editor
set editor=vim
set edit_headers
set sort_alias=alias

macro index,pager I '<shell-escape> fetchmail -vk<enter>'

```.fetchmailrc
```
poll pop.gmail.com with proto POP3 and options no dns
        user 'user.name@gmail.com' password 'really?' 
        is 'localuser' here
        ssl
        keep
        #fetchlimit 5
        no fetchall
        #fetchall
mda "/usr/bin/procmail -d %T"

```.procmailrc
```
# Env var's assign

PATH=/bin:/usr/local/bin
VERBOSE=off
MAILDIR=$HOME/Mail
LOGFILE=$HOME/.procmaillog

# Recipes
:0:
* ^TOuser.name
mutt

```

---

### Post by CloudyWind on 2009-10-05
I am thinking it might be related to where my mail files are located....

Mutt seems to look at three locations:
- $home/Mail/mutt - created by my procmail
- $home/Mail/Spool-Link - a sym link I created to /var/spool/mail/username
- /var/mail/username - mutt opens here by default....

all three locations have different emails in them....

which should I use? and how should I control the flow to each? Abandon procmail until I get the basics under control and determine what folders I *do* want?

---

### Post by andrew.46 on 2009-10-06
Hi CloudyWind,

> **CloudyWind said:**
> want to use Mutt as my mail client to read/send mail from my POP3 enabled gmail account.

Have you had a read through the following guide:

[Howto] Use Mutt with Gmail
[http://ubuntuforums.org/showthread.php?t=1021746](http://ubuntuforums.org/showthread.php?t=1021746)

I suspect that this would at least get you up and running and the gentleman who wrote the guide is quite approachable :).

Andrew

---

### Post by CloudyWind on 2009-10-07
> **andrew.46 said:**
> Hi CloudyWind,



Have you had a read through the following guide:

[Howto] Use Mutt with Gmail
[http://ubuntuforums.org/showthread.php?t=1021746](http://ubuntuforums.org/showthread.php?t=1021746)

I suspect that this would at least get you up and running and the gentleman who wrote the guide is quite approachable :).

Andrew

Thanks Andrew.... turned out to be a case of too many rc files spoil the broth. Started over from a clean slate and all is good.

---

