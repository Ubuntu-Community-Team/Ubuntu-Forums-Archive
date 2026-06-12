---
title: "Set Ownership of files downloaded with Vuze"
date: 2011-02-21
forum: General Help
---

### Post by gschoppe on 2011-02-21
I'm running Ubuntu 9.10 with Vuze 4.2.0.8 and an FTP Server on a remote server with Webmin, ssh, and vnc (for emergencies).

I need to be able to FTP into this box, access newly downloaded torrents, and organize them into my library.  However, for some reason, my user account is not given full permissions over these files when Vuze creates them.

What I need to do is ensure that all files Vuze creates in my torrents directory are set to 777 upon creation (there is no relevant security issue for this application).

how do I go about this without having to SSH in and chown 777 every time I want to sort things?

---

