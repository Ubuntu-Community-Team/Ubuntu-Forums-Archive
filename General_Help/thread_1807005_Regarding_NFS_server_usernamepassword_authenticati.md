---
title: "Regarding NFS server username/password authentication"
date: 2011-07-18
forum: General Help
---

### Post by ajaypadvi on 2011-07-18
Hi;
I had set up NFS server in one ubuntu box and mounted few directories using it.
In order to access those directories across the network i m using j-ftp(an open source java network client) from other boxes in the same network.I am able to view my mounted directories in the server through it.
I want to know if there is a way in NFS server where by i can provide username/password authentication so that only authorized users will be able to view my mount share in NFS server.I searched the api of j-ftp client where i found "pcnfsd" may prove useful for it but i am not able to find any thing on that regarding NFS server authentication from client for Ubuntu.

following is the login method in the api of j-ftp:

com.sun.nfs
Class XFileExtensionAccessor

public boolean loginPCNFSD(String host,
String username,
String password)
Sets the user's RPC credential from Login name and password. Every NFS request includes a "credential" that identifies the user. An AUTH_SYS credential includes the user's UID and GID values. These are determined from the user's login name (and password) by the PCNFSD service that must be available on a local server. Once the credential is set, it is assigned globally to all future NFS XFile objects.
If this method is not called, a default credential is assigned with a UID and GID of "nobody".

Parameters:
Returns:
true if the login succeeded, false otherwise.

Please help me if der is ne way to provide an authentication from NFS server in Ubuntu box for which i will be very thankful.

Thanks in advance;
Ajay

---

