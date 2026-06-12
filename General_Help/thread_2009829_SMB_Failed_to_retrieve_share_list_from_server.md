---
title: "SMB: Failed to retrieve share list from server"
date: 2012-06-25
forum: General Help
---

### Post by nilism on 2012-06-25
I know there are a few posts lurking on this one but I haven't found a solution to this problem. I'm also pretty new at linux, so my trouble shooting skills are still limited as I learn command line. 

Currently I am running 12.04 (gnome), although this problem has persisted from the 11.x days (clean install). I am using the samba config utility 1.2.63 from the repository. My network consists of an ubuntu box, a vista box, and a win7 box, as well as various phones tablets etc. Everything works well in two way communication with the ubuntu box, with the exception of the vista box. 

The vista box can see files on the ubuntu box no problem.  The ubuntu box can only see shares on the vista box if it has been restarted somewhat recently, otherwise the ubuntu box will throw the error "Failed to retrieve share list from server".  If I restart the vista box it works fine again. 

I'm going to guess the problem is on the vista box but I really don't have the ability to troubleshoot this one.  lol I don't even know how samaba works or what it does.  =p 

So, where should I start?

Thanks in advance. (o:

---

### Post by maverickaddicted on 2012-06-27
> **nilism said:**
> I know there are a few posts lurking on this one but I haven't found a solution to this problem. I'm also pretty new at linux, so my trouble shooting skills are still limited as I learn command line. 

Currently I am running 12.04 (gnome), although this problem has persisted from the 11.x days (clean install). I am using the samba config utility 1.2.63 from the repository. My network consists of an ubuntu box, a vista box, and a win7 box, as well as various phones tablets etc. Everything works well in two way communication with the ubuntu box, with the exception of the vista box. 

The vista box can see files on the ubuntu box no problem.  The ubuntu box can only see shares on the vista box if it has been restarted somewhat recently, otherwise the ubuntu box will throw the error "Failed to retrieve share list from server".  If I restart the vista box it works fine again. 

I'm going to guess the problem is on the vista box but I really don't have the ability to troubleshoot this one.  lol I don't even know how samaba works or what it does.  =p 

So, where should I start?

Thanks in advance. (o:

Is your Ubuntu machine connected to Workgroup? If yes, then what is the name of your workgroup and also paste the content of your smb.conf file here.

---

