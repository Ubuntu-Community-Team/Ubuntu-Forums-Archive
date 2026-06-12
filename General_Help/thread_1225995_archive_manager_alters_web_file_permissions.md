---
title: "archive manager alters web file permissions"
date: 2009-07-29
forum: General Help
---

### Post by StGeorge on 2009-07-29
I use CMS installations for my websites.

If I migrate a website from one host to another the Archive Manager changes permissions on files from 644 to 666 when I archive my local directories.

When I upload and extract the archive all the file permissions come out 666.

When I had ftp'd the original files the permissions were 644.

Any ideas out there or does someone know of a better archiver than file roller/archive manager?

The files are normally uploaded as tar.gz.

I am sick of chmodding all the files again.

---

### Post by nikhilk on 2009-07-29
The man page for tar has this information:
-p, --preserve-permissions, --same-permissions extract information about file permissions (default for superuser)

--same-owner try extracting files with the same ownership

See if those options help.

---

### Post by StGeorge on 2009-07-29
Thanks for the prompt reply.
Unfortunately the extraction process is done by the host server.
The files are in my Windows environment.
The Ubuntu I use is an upgraded Portable Ubuntu running inside Windows with CoLinux handling the RAM.
It could be that the permissions are being misread by the Archiver.
When I upload from the web file folders without archiving I get no problems.
The web file partition is mounted and from there I archive with File Roller.
The reason I tried file roller is my Windows 7zip or WinRar strip all permissions on archiving, (no options to retain permissions).

You have given me a clue how to retain permissions though so I will look into Man.

Thanks again.

---

### Post by nikhilk on 2009-07-29
> **StGeorge said:**
> You have given me a clue how to retain permissions though so I will look into Man.

Thanks again.

You are welcome. Let us know how it goes mate.

---

