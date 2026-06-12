---
title: "Hula and Ubuntu....Stable?"
date: 2006-05-16
forum: General Help
---

### Post by 8bit on 2006-05-16
How stable is the current version of Hula. I would like to use it for our company mail server but I need it to be rock solid stable.

Can anyone comment on the current stability of Hula? Thanks,

Also, does the Calendar sharing work well with Outlook 2002 and 2003?

---

### Post by bluenova on 2006-05-16
**When will Hula be production ready?**

Not for a while. The code needs to be stabilized and the missing source code added that has not yet been scrubbed. See the [scrub list](http://www.hula-project.org/Scrub_List) for an idea of what is still to be added.

**Are there plans to make Outlook work with Hula?**

We would like Hula to work with Outlook. If you want to help kick-start a Outlook/Hula project, send an email to the hula-dev mailing list ([http://forge.novell.com/modules/xfmod/maillist/subscribe.php?group_id=1613&list=hula-dev](http://forge.novell.com/modules/xfmod/maillist/subscribe.php?group_id=1613&list=hula-dev)) and suggest how you can help.

The Outlook connector should be a set of MAPI providers that speak native Hula NMAP protocol to the Hula server. The work we are doing for CalDav Support will provide the underpinnings for the Hula calendar, which the Outlook connector will use.

Basic high level requirements for the Hula Outlook connector are

    * Address book, Transport, and message store MAPI providers
    * Offline caching mode support
    * Calendaring
          o send/receive appointments
          o Busy search 
    * Shared calendars/folders
          o public shares
          o private shares 
    * Install/uninstall using MSI

---

