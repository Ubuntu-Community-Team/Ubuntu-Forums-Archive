---
title: "MSN wont work on Pidgin[HELP]"
date: 2010-11-20
forum: General Help
---

### Post by SNOOPY817 on 2010-11-20
Well this has been going on for five days already, I can't sign in MSN through pidgin it give me this error..

[IMG]http://i56.tinypic.com/2q9kkex.png[/IMG]

Anyone else getting this problem? Know any solutions to this?

---

### Post by mikewhatever on 2010-11-20
Check out the link: [http://www.omgubuntu.co.uk/2010/11/fix-pidgin-ssl-error/](http://www.omgubuntu.co.uk/2010/11/fix-pidgin-ssl-error/).

---

### Post by ebasa on 2010-11-20
Under Pidgin tools menu go to certificated. delete the one in the error message shutdown try again. Worked for me.

---

### Post by SNOOPY817 on 2010-11-20
Thanks guys, worked. :D

---

### Post by Artemis3 on 2010-11-21
[http://developer.pidgin.im/wiki/MSNCertIssue](http://developer.pidgin.im/wiki/MSNCertIssue)

---

### Post by marin123 on 2010-11-21
> **Artemis3 said:**
> [http://developer.pidgin.im/wiki/MSNCertIssue](http://developer.pidgin.im/wiki/MSNCertIssue)

thanks! this worked for me :)

---

### Post by Artemis3 on 2010-11-22
[http://developer.pidgin.im/wiki/ChangeLog](http://developer.pidgin.im/wiki/ChangeLog)

> version 2.7.6 (11/21/2010)
[list]
[*] **General**:
[list][*] Included Microsoft Internet Authority 2010 and Microsoft Secure Server Authority 2010 intermediate CA certificates to our bundle. This fixes the "Unable to validate certificate" error for omega.contacts.msn.com. ([#12906](http://developer.pidgin.im/ticket/12906)) 
[/list]
[/list]


> version 2.7.7 (11/23/2010)
[list]
[*] **General**:
[list][*]  Allow multiple CA certificates to share the same Distinguished Name (DN). Partially fixes remaining MSN issues from [#12906](http://developer.pidgin.im/ticket/12906). 
[/list]
[/list]


PD: Latest version is in [Getdeb](http://www.getdeb.net), not pidgin-developers/ppa -_-

---

### Post by sgwebb on 2010-11-27
[http://www.omgubuntu.co.uk/2010/11/f...gin-ssl-error/](http://www.omgubuntu.co.uk/2010/11/f...gin-ssl-error/)

Worked for me.. version 2.7.7 should be out soon with the perm fix

---

### Post by Sava on 2010-11-28
> **sgwebb said:**
> [http://www.omgubuntu.co.uk/2010/11/f...gin-ssl-error/](http://www.omgubuntu.co.uk/2010/11/f...gin-ssl-error/)

Worked for me.. version 2.7.7 should be out soon with the perm fix


2.7.7 is out there already. Well, not officially, technically :D

---

### Post by VinnyJ1701 on 2010-11-28
> **mikewhatever said:**
> Check out the link: [http://www.omgubuntu.co.uk/2010/11/fix-pidgin-ssl-error/](http://www.omgubuntu.co.uk/2010/11/fix-pidgin-ssl-error/).

Thank you.  Worked for me

---

