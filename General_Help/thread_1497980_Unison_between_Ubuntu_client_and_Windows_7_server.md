---
title: "Unison between Ubuntu client and Windows 7 server"
date: 2010-05-31
forum: General Help
---

### Post by stringbeans on 2010-05-31
I am at my wits end, and I pray that you good folk can help me. 

Setup:

Server: Desktop, running 64bit Windows 7, freesshd server, Unison 2.32.53

Client: Netbook, running 32bit Ubuntu 10.04, openssh client, Unison 2.32.53.

I finally got my head around SSH and can connect fine, as well as transfer files using the inbuilt file browser in Ubuntu after opening the server location. 

However now i'm stuck - I can't seem to get Unison working. questions/problems:

1. I don't understand why you need Unison running on both machines? It says it needs to be installed on both, however it doesn't install on Windows, it's just a separate program? am i meant to put this somewhere specific? Does Unison need to be opened on Windows as well as ubuntu when connecting? and if so, i'm confused with the profiles O.o

2. Is my 64bit system the problem?

3. If i try to connect via ubuntu, i get asked for the password, than I get the message:

Fatal error - Received unexpected header form the server: expected "Unison 2.32\n" but received "Unable to execute command or shell on remote system: Failed to Execute process.\r\n", which differs at "Una".
This can happen because you have different versions of Unison installed on the client and server machines, or because your connection is failing and somebody is printing an error message, or because your remote login shell is printing something itself before starting Unison. 

I have NO idea what i'm doing wrong, and I've spent hours trying to find answers, to no avail. HELP!

---

