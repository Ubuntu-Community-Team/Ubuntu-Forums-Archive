---
title: "Samba and NFS at the same time"
date: 2010-10-26
forum: General Help
---

### Post by holocene on 2010-10-26
At home, I have multiple Linux and Windows clients.
 
I want to serve files from one Linux host to those clients.
 
I know that I can share files with Samba to win clients, and NFS to Linux clients.
 
Questions:
1. Can I share some of the same files simultaneously with both protocols?
2. I heard it's better to share files with NFS to Linux clients, vs Samba. So, is it still better to have both protocols running, vs serving all clients with just Samba?
 
thanks
Steve.

---

### Post by SeijiSensei on 2010-10-26
I do it all the time, particularly when exporting home directories.  The only problem I can see is if two people open the same file for editing, one via Samba and the other via NFS, and both try to save it at the identical time.  Since the two servers use different methods of file locking, I'm not sure how this would work out.  Obviously this is more a theoretical problem than one that would occur in real life.

As to your second question, Linux should be using NFS since it presents the same filesystem interface as other *nix filesystems including permissions, symlinks, etc.

---

### Post by holocene on 2010-10-26
> **SeijiSensei said:**
> As to your second question, Linux should be using NFS since it presents the same filesystem interface as other *nix filesystems including permissions, symlinks, etc.
 
So, I should not hesitate to run BOTH protocols, when possibly Samba could serve both kinds of clients? Trying to keep it simple. 
 
Sorry if I am being silly about this.
Steve.

---

### Post by srs5694 on 2010-10-26
Samba and the Linux CIFS filesystem have been building Unix/Linux-style features for a while now, so in some cases they can handle all you might need even for Linux clients; however, the last I checked there were still some rather clunky limitations in this because this approach essentially "translates" Unix/Linux features into Microsoftese, as it were, and then "translates" back. Something is inevitably lost in the translation.

Overall, I'd say that if your needs are simple, using Samba alone is probably adequate; users will be able to read and save most files just fine, and if your security needs are simple, there shouldn't be any major problems. If you rely on subtle or advanced filesystem security features, though, you'll be better off sticking with NFS for Linux clients and using Samba's large number of workarounds to get things to work tolerably for Windows clients.

---

### Post by HermanAB on 2010-10-26
Howdy,

NFS is so much simpler and easier to get to work than Samba, that I use it for everything.  To enable NFS support on Windows, install Services for UNIX from the Microsoft web site.[https://www.microsoft.com/downloads/en/details.aspx?FamilyID=896c9688-601b-44f1-81a4-02878ff11778](https://www.microsoft.com/downloads/en/details.aspx?FamilyID=896c9688-601b-44f1-81a4-02878ff11778)

---

### Post by SeijiSensei on 2010-10-26
> **holocene said:**
> So, I should not hesitate to run BOTH protocols, when possibly Samba could serve both kinds of clients? Trying to keep it simple.

Yes, unless you choose to adopt HermanAB's approach and use NFS on Windows as well.  If you have people used to Windows networking conventions, like browsing shares or mapping drives, I'd run both NFS and Samba on the server.

---

