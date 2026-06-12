---
title: "Svn client authentication problem"
date: 2010-08-22
forum: General Help
---

### Post by Neon John on 2010-08-22
Running v9.10

I'm having a SubVersion authentication problem.  I have my svn server installed on my web hosting service.  I only use the svn client under Ubuntu.

Until now I had one big project in which I version controlled everything that needed controlling.  I decided to break things up into individual projects.

I created a second project on my web server using their web panel.  No problems there.  I imported a little utility that I've written in C.  That went fine. 

The problem is that svn is not caching my credentials.  I have to supply a  username and password upon every invocation.

The SVN books says that credentials are stored in ~/.subversion/auth. Not under Ubuntu.  Apparently it uses Gnu keyring.  I can see the new credential in Keyring ( applications->accessories->passwords and encryption keys ) but svn is apparently not paying attention to this credential.

I've tried deleting the credential in keyring and running svn again.  The credential is re-created but is ignored.

I don't know what else to do.  Help please!

Thanks
John

---

