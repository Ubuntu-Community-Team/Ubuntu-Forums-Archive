---
title: "sftp protocol with kmfclient"
date: 2006-03-11
forum: General Help
---

### Post by sithia on 2006-03-11
I've been looking for an answer to this but I have yet to locate one. I've got a bunch of filenames with UTF8 (Japanese) characters in them. When I create them on my desktop they look fine. When I create them on my laptop they look fine. When I look at the desktop's files over sftp in kmfclient the names are completely garbled. The same filenames over ssh in a terminal look fine. Is this just kmfclient or the sftp protocol downgrading the characters into ASCII? Is there any way I can change this so the UTF8 encodings are preserved?

---

