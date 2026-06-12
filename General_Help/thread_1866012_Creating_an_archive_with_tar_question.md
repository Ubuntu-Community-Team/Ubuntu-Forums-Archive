---
title: "Creating an archive with tar question"
date: 2011-10-20
forum: General Help
---

### Post by jacatone on 2011-10-20
If you make a tar backup of your home directory, would that restore your system to a previous version? I'm looking for a way to backup my system in the event of a crash and re-install? Thanks.

---

### Post by dniMretsaM on 2011-10-20
You would simply have to unarchive it to your home directory. It should work quite nicely.

---

### Post by agillator on 2011-10-20
What do you mean by 'restore to a previous version'? It would restore the files in the tar to the versions in the tar given the proper option(s). It would not delete any files already there that were not in the tar. See the man page for tar. If those files restored were configuration or data files for a program then, yes, the program could be configured as before if the program file was also restored. Simply restoring your home directory does not necessarily restore to a previous system version. One thing you might consider looking at is rsync or some backup program based on it such as rsnapshot. But even there, to go back to a previous version you need to restore everything that might have changed since that version, for example the operating system, all programs that have been updated since then, all configuration files that may have changed since then, and so on. And also understand that browsers, email clients and other programs often store data in your home directory, so you would lose any such data that may have changed since you made the tar. Perhaps I have misunderstood what you were really asking. If so, I apologize. Ask again with a little more specificity.

---

### Post by lovinglinux on 2011-10-20
If you are using Ubuntu 11.10, I would take a look at Déjà Dup Backup. It seems to work nicely.

---

