---
title: "Weird issue with ftp transfers"
date: 2010-08-09
forum: General Help
---

### Post by costre on 2010-08-09
[SIZE="1"](This is a windows XP issue, both on client and server side)[/SIZE]

I'm getting desperate. I am trying to setup a script in Auto FTP Manager ( [www.deskshare.com/afm.aspx](www.deskshare.com/afm.aspx) ) to download files from an ftp server, but run into weird problems.

The login and password are correct, the list of files to download is created properly by the program, the folders to be filled with files are created on my drive as they should, but the only files that get downloaded are the really small ones, <1kB.

The error message for large files reads:

[19:27:44] [Status] File Transfer Started from [SERVERNAME.DYNDNS.ORG:LOGINNAME]/FOLDERNAME/FILETOBEDOWNLOADED.EXT
[19:27:44] [Status] Failed: FTP Protocol error: 550 Could not find requested file. Don't use RETR /sub/dir/filename.ext : FILETOBEDOWNLOADED.EXT

When I connect manually with the exact same protocol/login/password/port I can download whatever I want. I have sent a message to DeskShare, but havent received any reply yet.

First I thought there was a limit to the file size because it was a trial version, but I have now purchased the full vesion, and the problem remains. It's the same issue with another auto-FTP program I tried.

One thing I can think of is that I don't have full permission to write to the remote disk, but that shouldn't affect downloads, or could it?

Tips on this issue?

---

### Post by dcstar on 2010-08-10
> **costre said:**
> (This is a windows XP issue, both on client and server side)
.........
And this is a forum specifically for Ubuntu Linux issues, not Windows ones:
[I][B]
General Help[/B]
All your general support questions for Ubuntu, Kubuntu, Edubuntu and Xubuntu.[/I]

---

### Post by HermanAB on 2010-08-10
Howdy,

You could install Cygwin and use 'wget'.

---

