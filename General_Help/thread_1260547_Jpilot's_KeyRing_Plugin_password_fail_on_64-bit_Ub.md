---
title: "Jpilot's KeyRing Plugin password fail on 64-bit Ubuntu"
date: 2009-09-07
forum: General Help
---

### Post by celem on 2009-09-07
I have previously used Jpilot's KeyRing Plugin successfully with a 32-bit install of 8.10 Ubuntu. I am now using a 64-bit 9.04 Ubuntu and I have a problem. The Jpilot sync and load of address, calendar, etc., all work fine. KeyRing's database file ~/.jpilot/Keys-Gtkr.pdb is properly backed up from the Palm (Sony PEG-SJ22/U). When I run the KeyRing Plugin, it prompts for the KeyRing password but the password always fails. With my previous 32-bit 8.10 Ubunto load it worked fine. Also, when I run the java Keyring Editor, it has no problem with the same password on the same Keys-Gtkr.pdb. Nothing has changed on the Palm (Keyring 2.0-pre6). I have tried this with the official jpilot 1.6.0 in the Ubuntu repository AND I compiled/installed the latest 1.6.2 directly from jpilot. Both behave the same, namely jpilot works but the KeyRing plugin fail the password verification.

I am wondering is this a problem with the 64-bit jpilot plugin or a library issue, or a 9.04 issue.

The jpilot.log file doesn't help much:
...
jp_pref_write_rc_file()
KeyRing: plugin gui started, unique_id=0
KeyRing: stat: /home/celem/.jpilot/Keys-Gtkr.pdb
KeyRing: verify_pasword
KeyRing: stat: /home/celem/.jpilot/Keys-Gtkr.pdb
Entering jp_read_DB_files: Keys-Gtkr
Leaving jp_read_DB_files
x=5, y=45
jp_pref_write_rc_file()
...

Has anyone else experienced this problem?

---

### Post by celem on 2009-09-09
Also fails on Slackware and Fedora 11 KDE. Is this some sort of issue with the crypto library? The java KeyRing editor has no problem opening the exact same KeyRing file. The java KeyRing editorreports that the Keys-Gtkr.pdb file is encrypted with Triple DES, format 5. (see attachment).

---

### Post by celem on 2009-10-13
I have resolved the issue. I had switched the version of Keyring on my Palm to version keyring-2.0-pre6-en so that it would work with the java desktop version of the Keyring program, KeyringEditor.jar. This was because KeyringEditor.jar fails to work with database version 4 and requires database version 5, which is supplied by keyring-2.0-pre6-en. Well, JPILOT cannot read database version 4. Once I removed keyring-2.0-pre6-en from my Palm and installed version keyring-1.2.3-en, that uses database version 4, JPILOT's KeyRing plugin works just fine.

The rub is that KeyringEditor.jar is supposed to support database versions 4 & 5, but 4 fails to work.

---

