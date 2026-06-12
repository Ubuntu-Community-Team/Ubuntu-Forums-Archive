---
title: "Archiving over a network with TAR"
date: 2006-04-23
forum: General Help
---

### Post by auberginepop on 2006-04-23
I have a number of Ubuntu boxes on a network. My plan was to backup each box to one of the other machines using TAR and cron.

Most of the machines don't change much so using the -u option (update only newer files) for tar I thought this would mean that on most occasions the command run from cron would execute quickly and not use much network resource.

Unfortunately, even if no files have changed or been added the tar -u command takes seemingly as long to run as when creating a fresh archive and hammers the network the same.

Does anyone know of a way to more efficient way to backup files which don't change too often. I am thinking of something like the archive attribute in Windoze.

---

### Post by GeneralZod on 2006-04-23
Have you looked into rsync? It's specifically designed to be a bandwidth-efficient solution for incremental backups.

---

### Post by auberginepop on 2006-04-23
I hadn't so I'll investigate this possibility. Thanks

---

