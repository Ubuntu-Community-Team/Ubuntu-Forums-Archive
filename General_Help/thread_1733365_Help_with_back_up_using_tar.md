---
title: "Help with back up using tar"
date: 2011-04-19
forum: General Help
---

### Post by pssturges on 2011-04-19
Hi,

I'm trying to create a very simple back up script to back up the contents of one folder on my system to an NTFS formatted external hdd. I want to keep the ownerships and permissions of the files I'm backing up intact so I'm putting them into a tar archive. Compression is not necessary as I have plenty of space for the backup.

I have created the initial backup with the following command:
```

tar -cpf $bupath/backup.tar $sourcepath
```

This seemed to work quite well with the resulting file being about 170gb and took about 5hrs.

For subsequent backups, the files are probably only going to change by about 10% at most so it seems inefficient to create a whole new backup from scratch. I would like to be able to just update my existing archive with any new/altered files. I have tried using the update mode (-u) with tar like so:

```
tar -upf $bupath/backup.tar $sourcepath

```
So far this has been running for about 10hrs and the archive has grown to approx 220gb! What's going wrong here? I was expecting the update to take 30mins max and there be no significant change in the archive size. Am I perhaps misinterpreting the purpose of update mode in tar, or is there something wrong with my command? Is there a better/easy way to accomplish this?

Thanks in advance
Phil

---

### Post by mendhak on 2011-04-19
This isn't a direct answer to your question, but what about using rsync or Unison to perform these backups? I believe both can preserve file permissions and they both do incremental backups based on comparisons.  So if a file exists in the source and destination, it won't overwrite.  If the source has changed, then it can overwrite the changes to the destination.

---

### Post by sj1410 on 2011-04-19
this may help

[http://www.gnu.org/software/automake/manual/tar/Incremental-Dumps.html](http://www.gnu.org/software/automake/manual/tar/Incremental-Dumps.html)

---

### Post by Ghost_Mazal on 2011-04-19
Rsync unfortunately wont work for him as his destination is an NTFS drive , hence permissions won't be preserved I believe.

---

### Post by pssturges on 2011-04-19
Yes, I did think that was the case, although I wasn't 100% certain myself.

sj1410, that does look like what I'm looking for, although I'm not sure I quite have my head around it. After the initial archive is created, is an additional archive created containing the "differences" for each time the command is run, therefore increasing the total amount of space consumed by the backup? Or, is the first subsquent archive overwritten by be each additional subsequent archive? I hope that makes sense?

Phil

---

