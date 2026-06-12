---
title: "Mutual Backup authentication Q"
date: 2006-04-01
forum: General Help
---

### Post by mbailey on 2006-04-01
I have two ubuntu boxen and would like them to do a little mutual backing up. I'd like them to copy home directories (very few files there) each way and push the mysql database that's storing my photos for gallery2 to the server that doesn't host it. I'm thinking rsync or just cron and rcp. My question is, how do I avoid the need for authentication when using these so I can batch this without having a plaintext password in the cron job. I've a feeling that in pre-history, hosts.equiv used to allow you to name users on specific servers that were trusted so that you could login via rsh without needing to authenticate. Can anyone tell me what the 2006 ubuntu equivalent is?

---

