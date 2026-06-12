---
title: "Install mutt without mail-transport-agent dependency?"
date: 2009-09-23
forum: General Help
---

### Post by josecanuc on 2009-09-23
I would like to install the mutt mailreader, but it insists on having a mail-transport-agent as a dependency of the mutt package.

On this particular system, I installed postfix from source, not from the repository. I want to have mutt ONLY as a local-folder mailreader; I won't be sending any emails or connecting to any email server with it.

In what way I can get around apt-get (or aptitude) trying to resolve the mail-transport-agent dependency when I try to install the mutt package from the repository?

---

### Post by andrew.46 on 2009-09-23
Hi josecanuc,

> **josecanuc said:**
> On this particular system, I installed postfix from source, not from the repository. I want to have mutt ONLY as a local-folder mailreader; I won't be sending any emails or connecting to any email server with it.

If you have the skill to install postfix from source perhaps you should also install mutt from source? This way you could install version 1.5.20 which in my experience is quite stable.

All the best,

Andrew

---

