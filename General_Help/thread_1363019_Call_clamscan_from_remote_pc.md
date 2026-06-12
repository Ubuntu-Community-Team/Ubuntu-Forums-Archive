---
title: "Call clamscan from remote pc"
date: 2009-12-23
forum: General Help
---

### Post by wpsd on 2009-12-23
I have Ubuntu Desktop Client
and Ubuntu Server specially for Anti Virus and Span Assasin

Is it possible to call clamscan from Ubuntu Desktop Client to scan the file in their computer ? 

Any code references I can use ( I'm ok without GUI )

---

### Post by dcstar on 2009-12-23
> **wpsd said:**
> I have Ubuntu Desktop Client
and Ubuntu Server specially for Anti Virus and Span Assasin

Is it possible to call clamscan from Ubuntu Desktop Client to scan the file in their computer ? 

Any code references I can use ( I'm ok without GUI )

What is "their computer"?

Unless you are serving files to Windows users, there isn't much point in virus scanning.

---

### Post by wpsd on 2009-12-24
Ok here's the real prob:

I use HmailServer ( a good open source mail server for Windows ) in Windows 2003

The last Mail Server experience cannot be integrated with antivirus ( performance problem )

So I change to this one and there is option for antivirus , I try using clamwin ( performance problem ) so I close it.Then they ask me to install clamav but I have no idea how to install it in windows. So I prefer to install it on the Ubuntu Server ( I have some experience with bash shell ) which it use less resource less trouble and faster, but I'm not sure how to let the remote computer call the clamscan.

Hmailserver can connect to antivirus using executable scanner command, but they don't have document regarding using remote scanner.

Since I think this is more to the coding and windows -> linux than the mailserver itself, so I ask it here :D:)

---

### Post by dcstar on 2009-12-24
> **wpsd said:**
> Ok here's the real prob:

I use HmailServer ( a good open source mail server for Windows ) in Windows 2003

The last Mail Server experience cannot be integrated with antivirus ( performance problem )

So I change to this one and there is option for antivirus , I try using clamwin ( performance problem ) so I close it.Then they ask me to install clamav but I have no idea how to install it in windows. So I prefer to install it on the Ubuntu Server ( I have some experience with bash shell ) which it use less resource less trouble and faster, but I'm not sure how to let the remote computer call the clamscan.

Hmailserver can connect to antivirus using executable scanner command, but they don't have document regarding using remote scanner.

Since I think this is more to the coding and windows -> linux than the mailserver itself, so I ask it here :D:)

If you are going to do mailserver virus scanning then it must be done on the mailserver platform.

---

