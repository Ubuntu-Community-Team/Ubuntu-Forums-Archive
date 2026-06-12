---
title: "equivalent for IRIX's 'bstream' command"
date: 2010-07-05
forum: General Help
---

### Post by davidmaxwaterman on 2010-07-05
Is there an equivalent of the IRIX [bstream]("http://techpubs.sgi.com/library/tpl/cgi-bin/getdoc.cgi?coll=0650&db=man&fname=/usr/share/catman/u_man/cat1/bstream.z") command?

---

### Post by btindie on 2010-07-05
What is it you want to use that command to do? - backup to tape?? You can just use *tar* directly along with *mt* to control the drive. Example [here]("http://www.cyberciti.biz/faq/linux-tape-backup-with-mt-and-tar-command-howto/").

---

### Post by davidmaxwaterman on 2010-07-05
> **btindie said:**
> What is it you want to use that command to do? - backup to tape?? You can just use *tar* directly along with *mt* to control the drive. Example [here]("http://www.cyberciti.biz/faq/linux-tape-backup-with-mt-and-tar-command-howto/").

I want to use it as a big fat fuffer in between two commands.

I'm currently trying 'dd bs=1024' which seems to do the trick.

---

