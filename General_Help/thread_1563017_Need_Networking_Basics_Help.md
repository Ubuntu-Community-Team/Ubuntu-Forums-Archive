---
title: "Need Networking Basics Help"
date: 2010-08-28
forum: General Help
---

### Post by jsriz on 2010-08-28
Well , we have successfully set up a server and 60 local computers at  our college.There is a guest account on all the 60 systems(all of these  are on the same network) in lab and user accounts on the server so that  one can ssh to the server.
well we having been facing problems off late and i could use a bit of help in the following:

1)***_Proxying_***: the net provided to this server is for  the lab.It is allowed to ssh from the hostels to upload files but people  started using this as a socks server and stealing bandwidth.
After a bit of research I set the allowtcpforwarding to no ,but then  people started running tiny proxy in their accounts how do I stop this  (I don't want to delete the files manually for which I have to open  their home and break into their privacy)?

2)_***Local ssh***_: During lab hours when all the systems  are engaged, users start mischeif by ssh 'ing into other local systems  and kill 'ing processes and ejecting drives.How do i block ssh among  local systems and allow ssh only to the server?

3)when any user is logged in the server through the terminal he is able  to browse through the file system though he cannot edit anything except  for his home folder it is a barge into other users privacy ain't it how  can this be restricted?

4)Is there a way to give ***restricted sudo access***(i.e to  install harmless software like kate gedit etc)on the local machine(the  60 systems) to the users liking.......i dont like the idea of installing  all the softwares on all the systems....
I have described my problems also so suggest any better solutions if any
Please it took a lot of time type out all this atleast bump this thread .....

---

### Post by jsriz on 2010-08-29
Guyz need Some help here

---

### Post by Saprissa on 2010-09-05
For #4 try this sudo primer.

[http://linsec.ca/Using_Sudo_to_Limit_Access]("http://linsec.ca/Using_Sudo_to_Limit_Access")

I could be wrong, but I think in regard to what packages are available for users to install, you would have to define that in the software sources users have access to.

If a user has access to a particular repository, I think they have access to ALL of that repository.

At least you get your bump! ):P

---

### Post by perspectoff on 2010-09-05
See:

[http://ubuntuguide.org/wiki/Ubuntu:Lucid#SSH](http://ubuntuguide.org/wiki/Ubuntu:Lucid#SSH)

or

[http://kubuntuguide.org/Lucid#SSH](http://kubuntuguide.org/Lucid#SSH)

SSH connections can be made secure (and should be). Leaving an open (or merely password-protected) SSH port open is foolish.

---

