---
title: "Can login to the squirrelmail webmail interface, but cannot send/recieve!"
date: 2009-07-01
forum: General Help
---

### Post by rancidguy on 2009-07-01
I am running a hardy heron box with LAMP, courier for IMAP, postfix & squirrelmail. Everything is configured for localhost, I have not binded an IP to the apache server. I am interested in getting two account I've created on the box to be able to log in to the webmail interface & send & recieve email between the two accounts. After I get that to work I will assign an IP for use over a secure network in the lab at my school.

This is the squirrelmail configtest output:

This script will try to check some aspects of your SquirrelMail configuration and point you to errors whereever it can find them. You need to go run conf.pl in the config/ directory first before you run this script.

SquirrelMail version:    1.4.19
Config file version:    1.4.0
Config file last modified:    30 June 2009 13:08:11
Checking PHP configuration...
    PHP version 5.2.4-2ubuntu5.6 OK.
    display_errors: 1
    error_reporting: 6135
    variables_order OK: EGPCS.
    PHP extensions OK. Dynamic loading is disabled.

    ERROR: You have enabled any one of magic_quotes_runtime, magic_quotes_gpc or magic_quotes_sybase in your PHP configuration. We recommend all those settings to be off. SquirrelMail may work with them on, but when experiencing stray backslashes in your mail or other strange behaviour, it may be advisable to turn them off.
Checking paths...
    Data dir OK.
    Attachment dir OK.
    Plugins are not enabled in config.
    Themes OK.
    Default language OK.
    Base URL detected as: [http://localhost/webmail/src](http://localhost/webmail/src) (location base autodetected)
Checking outgoing mail service....
    SMTP server OK (220 elitesecurity.com ESMTP Postfix (Ubuntu))
Checking IMAP service....
    IMAP server ready (* OK [CAPABILITY IMAP4rev1 UIDPLUS CHILDREN NAMESPACE THREAD=ORDEREDSUBJECT THREAD=REFERENCES SORT QUOTA IDLE ACL ACL2=UNION STARTTLS] Courier-IMAP ready. Copyright 1998-2005 Double Precision, Inc. See COPYING for distribution information.)
    Capabilities: * CAPABILITY IMAP4rev1 UIDPLUS CHILDREN NAMESPACE THREAD=ORDEREDSUBJECT THREAD=REFERENCES SORT QUOTA IDLE ACL ACL2=UNION STARTTLS
Checking internationalization (i18n) settings...
     gettext - Gettext functions are available. On some systems you must have appropriate system locales compiled.
     mbstring - Mbstring functions are available.
     recode - Recode functions are available.
     iconv - Iconv functions are available.
     timezone - Webmail users can change their time zone settings.
Checking database functions...
    not using database functionality.

Congratulations, your SquirrelMail setup looks fine to me!


This is the error I recieve when I try to send:
ERROR:
Message not sent. Server replied:

    Requested action aborted: error in processing
    451 4.3.5 Server configuration error

What have I configured improperly?

---

### Post by rancidguy on 2009-07-01
Any help on this would be greatly appreciated...

---

### Post by rancidguy on 2009-07-08
Does no one have any advice for me at all???

---

