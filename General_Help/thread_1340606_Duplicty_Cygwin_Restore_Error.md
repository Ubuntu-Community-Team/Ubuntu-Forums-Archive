---
title: "Duplicty Cygwin Restore Error"
date: 2009-11-28
forum: General Help
---

### Post by NertSkull on 2009-11-28
So I have duplicity running in cygwin on a windows XP computer.  Its backing up the data to an external drive attached to that machine.

Out of curiosity I copied the backup files (gpg files) files from that external drive to my ~/Documents/backuptemp

Then I run a restore script in duplicity to restore the files to ~/Documents/restoretemp

If I run the script (restore.sh) strait from terminal I get an Error that says:

Error '[Errno 1] Operation not permitted: ' and it lists the file.  BUT it still restores the files and I can open them up in the restoretemp directory.  So although I get the error, it still actually restores the files.

Now if I run the script as root (sudo restore.sh) I get no errors.  The files restore into 'restoretemp' BUT the folder now is locked and only accesible through the root account.

I'm just curious what is going on here.  Anyone know?  Why do I get the error when not running as sudo?  And is there a way to fix this error?

And if not a way to fix the error, is there a way to have Duplicity not protect the directory when the script is run as root?

Thanks everyone.

(p.s. I've never done anything with ssh, but I want to set up a remote Duplicity back up now.  I just started using duplicity recently and I'm trying to learn as much as I can.  Anyway, if anyone has a source for a good tutorial on how to understand setting up ssh server / client, gpg keys or anything relating to duplicity I would love to read through them,  THANKS!!!)

---

