---
title: "OpenOffice won't open files on remote computer"
date: 2010-10-11
forum: General Help
---

### Post by shineymart on 2010-10-11
Using connect to server in 10.04, service type SSH (sftp) from the places menu. This shows my folder and I can double-click pdfs, text files etc from Nautilus. 

But.... if I try to open an ods or odt file it opens the archive manager. It also fails if I open from within OOo. It used to work but has recently stopped.

As an aside, if I export the share via NFS and access it that way, then everything works OK.

Hope someone can help as this is really frustrating.

Martyn

---

### Post by HermanAB on 2010-10-11
Howdy,

OOo is rather more strict in checking for sharing violations than most.  You can override that issue somehow in a configuration file, but I can't remember how.  Some googling for "OpenOffice.org sharing violation" or some such will eventually find you the fix.  

Note however, that this is not an OOo bug, it is a networking problem and doing the override can cause problems in a situation where there are multiple users.

---

### Post by shineymart on 2010-10-13
Thanks for your reply Herman

Hmmmm... not sure its networking though. I'm doing SSH - I have rwx permissions on the share and am effectively doing an sftp login. All other apps open their respective files OK except OOo.

If I connect to the same share via NIS then no issue. If I copy and paste the file I want to edit to my desktop it works OK - this seems to be an gnome<->OOo issue.

Anybody else seen this?

Martyn

---

