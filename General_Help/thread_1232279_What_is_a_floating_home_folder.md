---
title: "What is a floating home folder?"
date: 2009-08-05
forum: General Help
---

### Post by tarekeldeeb on 2009-08-05
Hello all,

A friend of mine once told me about a linux network configuration that I want to implement. There is a file+authentication server, a processing server and many client PCs.

[Part-1]
Your home folder is stored at the file server, but you can login from any client PC, the auth. server will grant the access and copy ALL the home folder (from the file server) to the client PC you use. You can then login and work normally. At logout, the home folder goes back to the file server. Client PCs do not hold copies of home folders except at a running session.

[Part-2]
Moreover, processing hungry tools are run on the processing server (has multi-core CPU + much RAM). So the client PCs act as dummy terminals with not much resources. The auth. server permits the access to the processing server as well.

How this implementation can be reproduced? Is it called 'floating home'?
Which packages are needed?

Please help,

Thanks in advance,

Tarek

---

### Post by Mighty_Joe on 2009-08-05
> **tarekeldeeb said:**
> 
[Part-1]
Your home folder is stored at the file server, but you can login from any client PC, 

This is known as a [Thin Client]("http://tldp.org/HOWTO/Thinclient-HOWTO.html")

> **tarekeldeeb said:**
> 
[Part-2]
Moreover, processing hungry tools are run on the processing server (has multi-core CPU + much RAM).


This is accomplished with [X tunneling]("http://tldp.org/HOWTO/Remote-X-Apps.html#toc9")

Google for those terms and you'll get tons of examples, how-to's and other useful info.
Personally, I just share out a directory on my file server via SMB and I can connect to it from Ubuntu or Windows.

---

### Post by tarekeldeeb on 2009-08-05
> **Mighty_Joe said:**
> This is known as a [Thin Client]("http://tldp.org/HOWTO/Thinclient-HOWTO.html")

The exposed folder /tftpboot/user1, does it have a complete linux installation files? Or maybe just symbolic links and a home folder? 
I don't want too much duplicated data for users.

I thought the Client PC has its own installation files, and just needs the home folder from the server, no the complete linux. Ie, Client PC can boot normally, but start a session with a remote home folder.

Will a 100Mbps ethernet network lead to speed degradation?

> **Mighty_Joe said:**
> This is accomplished with [X tunneling]("http://tldp.org/HOWTO/Remote-X-Apps.html#toc9")

yes .. exactly. But in this case, my home has to be mounted on the remote server .. right?
May be if the processing server is the file server, it will be faster ..

Am I getting things wrong?
Are there different techniques?
Doe ubuntu offer zero-config packages for such implementation?

Thanks Mighty_Joe,

Tarek

---

### Post by Mighty_Joe on 2009-08-05
> **tarekeldeeb said:**
> Ie, Client PC can boot normally, but start a session with a remote home folder.

What you would probably do is configure the client pc to mount the remote home on some path and configure your user to use that mounted directory as home.  I'm sure there are many other ways.

> **tarekeldeeb said:**
> 
Will a 100Mbps ethernet network lead to speed degradation?

Couldn't tell you.

> **tarekeldeeb said:**
> 
yes .. exactly. But in this case, my home has to be mounted on the remote server .. right?


X does not care where home folder is.  It is designed to run applications across the network.

---

