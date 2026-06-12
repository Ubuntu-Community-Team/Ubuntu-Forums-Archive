---
title: "wget help"
date: 2011-01-15
forum: General Help
---

### Post by yma981 on 2011-01-15
Hello

I generally use the following in order to download multiple file using wget 


wget -w 2 -i filename

i am trying to use that in order to ddl multiple files, the issue is that i need to wait more than 30 min between files.

when i am doing

wget -w 1900 -i filename

the download isn't starting! Any idea how to solve this issue?

Regards

---

### Post by zeroK on 2011-01-15
-w seems also to apply if fetching a single file requires following redirects. So for instance if the first file in your download list is only reachable after following a redirect, wget will wait 1900 seconds to follow the redirect it received after the first request. Does this sound like something the first entry in your download list might look like? :-)

---

