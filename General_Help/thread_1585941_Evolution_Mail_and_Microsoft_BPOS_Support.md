---
title: "Evolution Mail and Microsoft BPOS Support"
date: 2010-10-01
forum: General Help
---

### Post by jmcdonald@mbcsolutions on 2010-10-01
I've successfully had MS-Exchange and Evolution work together a number of times.  Recently we switched to Microsoft's Business Productivity Online Suite (BPOS).  It's been a great product and our uptime has been 100%.  However, I can no longer get it to work with the Evolution Mail system.  Here's what I've done so far:

I have the Exchange MAPI plugin installed.
I've used the OWA settings [https://red001.mail.microsoftonline.com/owa](https://red001.mail.microsoftonline.com/owa) 
Used my user name and password
Tried to authenticate and I get an error: "Could not locate server. Make sure the server name is spelled correctly and try again."

I've searched the Microsoft site and they don't support Evolution Mail, Firefox, or Linux.  So, I've had no joy there.

Any ideas?

---

### Post by dcstar on 2010-10-02
> **jmcdonald@mbcsolutions said:**
> I've successfully had MS-Exchange and Evolution work together a number of times.  Recently we switched to Microsoft's Business Productivity Online Suite (BPOS).  It's been a great product and our uptime has been 100%.  However, I can no longer get it to work with the Evolution Mail system.  Here's what I've done so far:

I have the Exchange MAPI plugin installed.
I've used the OWA settings [https://red001.mail.microsoftonline.com/owa](https://red001.mail.microsoftonline.com/owa) 
Used my user name and password
Tried to authenticate and I get an error: "Could not locate server. Make sure the server name is spelled correctly and try again."

I've searched the Microsoft site and they don't support Evolution Mail, Firefox, or Linux.  So, I've had no joy there.

Any ideas?

Do you have the **evolution-mapi** package installed?

---

### Post by ouff on 2010-10-07
I'm trying to accomplish the same thing.  I have tried both the OWA server name and the MAPI server using Outlook Connection plugin and MAPI plugin for Evolution.  What adds to the confusion is that, when using the MAPI Exchange plugin to create an account, there is a required "Domain" field.  BPOS domains are somewhat complicated, so I'm not sure what to put in there.  It could be microsoftonline.com, or [mycompanysname].microsoftonline.com, or [mycompanysname].com, but I'm really not sure which.

This whole thing is quite frustrating as it is the only thing that is holding me back from ditching Windows completely at work.  Has anyone else made any progress with this?

---

### Post by aimaz on 2010-10-20
I'd love to hear how someone did this if they have it working. As the BPOS OWA client is crippled in browsers other than IE.

> **ouff said:**
>  it is the only thing that is holding me back from ditching Windows completely at work.

I don't think it's particularly cynical to say that's probably the point.

---

### Post by ouff on 2010-10-20
> **aimaz said:**
> 
I don't think it's particularly cynical to say that's probably the point.

Well, that could come back to bite them in the *** as they are not the only cloud-based service out there.  Heck, they're not even the only Exchange cloud-based service out there.

I did file a formal service request with them to try to resolve this issue.  They, predictably, responded that they don't list Linux as an operating system supported by their service.  They did offer to create a design change request on my behalf, which I accepted.  I can't imagine anything will come of that though, at least not any time soon.  Most likely, someone far more proficient than I will hack it well before MSOL starts offering official support.

---

### Post by ravikiran189 on 2011-10-16
Any 1 got success configuring Evolution with BPOS by chance...

Thanks

---

### Post by nothingspecial on 2011-10-16
Hi,

Please make a new thread of your own rather than digging up an old one.

Closed.

---

