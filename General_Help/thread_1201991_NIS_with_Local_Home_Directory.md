---
title: "NIS with Local Home Directory"
date: 2009-07-01
forum: General Help
---

### Post by mswebersd on 2009-07-01
I have setup a server with NIS enabled.  Users are able to access their NIS remote home directories using autofs fine.  I would like to step backward though and automatically create a local /home directory for them.  They will be doing a lot of file reading that would be much too slow over the network. 

Is this possible without changing anything on the NIS server end?  My IT department will definitely not be up for changing anything on the server.

Thanks,
Mike

---

### Post by 480silverton on 2009-08-29
Nfs?

---

