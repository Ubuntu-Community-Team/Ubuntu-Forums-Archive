---
title: "Open Office allows to create document, but not edit"
date: 2009-11-10
forum: General Help
---

### Post by ttry72 on 2009-11-10
Hello folks!

I have a weird problem, at least it looks like.

The thing is following, I can create Open Office document on shared folder (behind SFTP connection) but after saving I am only allowed to read, not edit the document.

But if I do the same thing using by Gedit, I am allowed to handle the document normal way, read and write access works fine.

A big mystery... help me please, my working environment depends on this. Dont want to have Vista back...

And the version is the latest 9.10...

---

### Post by ttry72 on 2009-11-12
> **ttry72 said:**
> Hello folks!

I have a weird problem, at least it looks like.

The thing is following, I can create Open Office document on shared folder (behind SFTP connection) but after saving I am only allowed to read, not edit the document.

But if I do the same thing using by Gedit, I am allowed to handle the document normal way, read and write access works fine.

A big mystery... help me please, my working environment depends on this. Dont want to have Vista back...

And the version is the latest 9.10...

It very weird that Ubuntu's Open Office can open normally documents, which has been created by Open Office's Windows version.

So, the problem seems closely related to Ubuntu Open Office, there is the problem. Are there any settings which could be wrong?

---

### Post by wilee-nilee on 2009-11-12
In what format are they being saved in.

---

### Post by Commander_Keen on 2009-11-12
Can you create a document on your desktop
Can you save it?
How are you saving it.
Can you go back and Edit the file?
If not what are the issue.

---

### Post by anaconda on 2009-11-12
I have the same problem. (with ubuntu 8.04)

It has something to do with the shared network-drive. I can create a document to the shared network-drive, but if I open the document with oo, then it usually opens in read-only mode. 

I have "solved" the problem, by copying the document to my home-directory, editing it there, and then copying it back to the network drive. (overwriting the previous one) 

Sometimes I have had a similar problem with nautilus. eg. nautilus claims that I don't have enough priviledges to eg. delete a file from the network-drive, but if I do the same thing in terminal I have the rights.. and eg. ls -la shows that I am the owner and I have rwx rights

I think this has something to do with the network drive and nfs mounts? not as much with Open-office or nautilus. Maybe openoffice and nautilus check the access rights differently than eg. terminal or gedit..

---

### Post by ttry72 on 2009-11-15
The problem is solved.

The key hint for the problem is here:
[https://help.ubuntu.com/community/SSHFS](https://help.ubuntu.com/community/SSHFS)

It need parameters after sftp command, in my case command sftp -o idmap=user was solution.

---

