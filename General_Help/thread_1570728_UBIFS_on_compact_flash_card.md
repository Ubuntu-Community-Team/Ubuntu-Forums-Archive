---
title: "UBIFS on compact flash card"
date: 2010-09-08
forum: General Help
---

### Post by feh on 2010-09-08
Hi folks.

I'm building an embedded system which uses a CF card for storage. I'm trying to determine what file system to use.

From what I've read, UBIFS is the ticket for MTD devices, but I'm not sure if the CF card qualifies. From what I understand, the controllers built into CF cards take care of wear leveling, which the UBI file system also addresses. Is it a bad idea to use them in conjunction?

Thanks!

---

