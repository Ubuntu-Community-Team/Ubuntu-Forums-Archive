---
title: "Network File Server with User Log-In"
date: 2011-11-09
forum: General Help
---

### Post by DATAjammer on 2011-11-09
*[COLOR=Red]COMPLETE NOOB SO SORRY IF ITS A DAFT QUESTION ;-)[/COLOR]*

I currently have a few PC's with different versions of Windows (XP/Vista and Win7) using a Freecom netdrive (FND) to share files. The FND is on its last legs and having a spare machine, I want to set up a file server with specific user access.

The files only need to be shared within the LAN, not over the internet so I know I can do this with SAMBO but I want to have public shares (Music/Movies/Generic Applications) and also Private Shares (TonyDocs/KeiraDocs/TonyWorkDocs for example) that are only accessible to specific users.

Can ubuntu manage/control these or allow any user to log on to any pc in the house with access to everything.

Ideally I would also like to use Windows on the PC's because my daughter and wife need Windows access, but it doesn't matter where the files are stored for them.

Hope this makes sense.

Tony

---

### Post by SeijiSensei on 2011-11-09
> **DATAjammer said:**
> Can ubuntu manage/control these or allow any user to log on to any pc in the house with access to everything.

Yes.  Samba allows you to create public and private shares and require logins for the latter.

---

### Post by DATAjammer on 2011-11-09
Thanks for your help Sensei :-)

I think I'll have a play.

---

