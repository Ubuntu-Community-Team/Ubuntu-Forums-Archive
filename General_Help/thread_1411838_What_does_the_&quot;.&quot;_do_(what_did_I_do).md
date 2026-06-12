---
title: "What does the &quot;.&quot; do? (what did I do?)"
date: 2010-02-20
forum: General Help
---

### Post by zoomiest on 2010-02-20
I was just going through a Unix textbook, reviewing tar archiving for backups, and running some examples on my samba share, and something bad happened.

There was an example that had a trailing period, and it seemed to have brought down my system when I used it(!)

Question: What does that trailing period do?

```
allan@HP-G60:~/c_allan$ tar cvf simply3.tar Simply .
Simply/
Simply/forms/
Simply/forms/CAN/
Simply/forms/CAN2009/
Simply/forms/CAN2009/schema.ini
Simply/forms/CAN2008/
Simply/forms/CAN2008/schema.ini
Simply/DbVerifier/
Simply/DbVerifier/Logs/
Simply/DbVerifier/Logs/0000.log
Simply/DbVerifier/Backups/
./
./NAD-C300.pdf
./Phone Backup/
./Phone Backup/841A679-Memory Stick (TM)/
./Phone Backup/841A679-Memory Stick (TM)/VIDEO/
./Phone Backup/841A679-Memory Stick (TM)/DCIM/
./Phone Backup/841A679-Memory Stick (TM)/PICTURE/
./Phone Backup/841A679-Memory Stick (TM)/MUSIC/
./Networking Proposals.htm
./6F438DB8.tmp
./Remote Assistance Logs/
./Remote Assistance Logs/20090929212824.xml
./Desktop/
./Desktop/Samba-Guide.pdf
./Desktop/Samba3-HOWTO.pdf
tar: simply3.tar: Cannot write: Host is down
tar: Error is not recoverable: exiting now
allan@HP-G60:~/c_allan$ 

```

See the error message? 

Here is the command without the trailing period...
```
allan@HP-G60:~/c_allan$ tar cvf simply.tar Simply
Simply/
Simply/forms/
Simply/forms/CAN/
Simply/forms/CAN2009/
Simply/forms/CAN2009/schema.ini
Simply/forms/CAN2008/
Simply/forms/CAN2008/schema.ini
Simply/DbVerifier/
Simply/DbVerifier/Logs/
Simply/DbVerifier/Logs/0000.log
Simply/DbVerifier/Backups/
allan@HP-G60:~/c_allan$ ls Simply

```

I opened up another terminal, and tried to list files. My samba server seemed to have eventually come back up, after a minute or two...

```
allan@HP-G60:~$ ls
ls: cannot access c_jr: Host is down
ls: cannot access c_music: Host is down
ls: cannot access c_speech: Host is down
c_allan      examples.desktop
c_family     gdocs.dat
c_jr         Invoice For Khem.odt
c_laura      music
c_music      other
c_paul       Pictures
c_pictures   Public
c_resumes    Start Download Manager.html
c_speech     Templates
Desktop      Ubuntu One
Documents    videos
Downloads    VMware-VMvisor-Installer-4.0.0.Update01-208167.x86_64.iso.dlm
en_CA.UTF-8  vorbis

```

If anyone can tell me what happened, I would appreciate it very much!

---

### Post by Barriehie on 2010-02-20
. is the current directory.  .. is up 1 directory level.  .. is contained in . so you have to be careful of recursion!

---

### Post by zoomiest on 2010-02-20
So, I inadvertently attempted to archive most of the contents of the server, and it temporarily stalled (took all the cpu cycles of) my samba server?

---

### Post by Barriehie on 2010-02-20
> **zoomiest said:**
> So, I inadvertently attempted to archive most of the contents of the server, and it temporarily stalled (took all the cpu cycles of) my samba server?

I don't do windows so I can't help you with anything regarding samba!

---

### Post by lisati on 2010-02-20
> **Barriehie said:**
> I don't do windows so I can't help you with anything regarding samba!

Um.... Ubuntu has samba too.....

---

### Post by Barriehie on 2010-02-20
> **lisati said:**
> Um.... Ubuntu has samba too.....

Yes, and I understand that samba allows linux/windows machines to comm. seamlessly, no windows anything connected to this box!

---

