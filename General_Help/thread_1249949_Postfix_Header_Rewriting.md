---
title: "Postfix Header Rewriting"
date: 2009-08-26
forum: General Help
---

### Post by dkirk on 2009-08-26
Hey,

I need to clean up the From address for incoming messages on a Postfix mail server.

A bit of a summary of what I'm trying to do.  I have installed Trac and set it up as a fault tracking system for our I.T. department.  I have installed email2trac to allow internal staff to log tickets via email.

Users authenticate to Trac with Active Directory, so I can login as "david".  When users send an email to Trac through our Exchange server, the From address comes through as "David Kirk" <david@mydomain.com>.  This is what shows up as the Reporter of the ticket.

Staff only have access to view their own tickets, so if they generate a ticket via email and then log in to the web interface, they won't see their ticket.

I need to be able to strip everything from the From address of the incoming email and leave just their login name.

The Trac server is running Postfix.  Can anyone help me with rewriting the From address to remove the full name at the beginning and the domain name at the end to just leave the login name?

I've been reading [http://www.postfix.org/ADDRESS_REWRITING_README.html](http://www.postfix.org/ADDRESS_REWRITING_README.html) but I can't figure it out.

-- 
Thanks

David Kirk

---

