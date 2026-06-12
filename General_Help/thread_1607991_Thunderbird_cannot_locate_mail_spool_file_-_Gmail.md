---
title: "Thunderbird cannot locate mail spool file - Gmail"
date: 2010-10-28
forum: General Help
---

### Post by IVIurdoc on 2010-10-28
I just dl'd Thunderbird and its working fine with my Hotmail account however I'm having some problems with my Gmail account. I can send emails thru gmail just fine but when I click get mail, the error message: Unable to locate mail spool file pops up. The server settings for this account are Server Type: Unix Movemail
                                         Server Name: Local Host
                                         Username: (my gmail email - @gmail.com)
I think this is all set up right, it did it automatically for me. Anyone else encounter this and know how to fix it? Thanks in advance for any help.

---

### Post by IVIurdoc on 2010-10-28
Anyone?

---

### Post by onaridge on 2010-11-08
I have the same problem and no one seems to know the answer and there isn't anything helpful via a Google search. Have you tried Mozilla forums? I would like to use it and can't for that reason. I had the same thing happen with Eudora. Evolution OTOH works fine. So that's what i use but i don't like it much.

---

### Post by rthawkcom on 2012-05-04
That's because by default Thunderbird interfaces to the local Movemail server instead of connecting to an external server like you and the rest of the planet wants.   When Thunderbird is first run, it NEVER offers you the chance to interface to an external mail server.  

Go into account settings, delete the account you have, then click on the bottom "account actions" and add a new account.  If you get the error "account exists", congratulations!  You discovered yet another wonderful Thunderbird bug!  Simply change your email address to "thunderbirdsucks@gmail.com", save it, then edit the account and change it back.

The internal code of Thunderbird is mess.  Hence all the bugs. 

Hope this helps someone, it sure caused me a lot of aggravation.

---

### Post by oldos2er on 2012-05-05
Old thread closed.

---

