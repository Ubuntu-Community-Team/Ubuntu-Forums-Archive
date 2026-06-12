---
title: "Vim text editor - use of wildcards"
date: 2010-08-01
forum: General Help
---

### Post by MeKino on 2010-08-01
Hi,

I'm struggling with the Vim find/replace command using wildcards.

I have several, big html files with lots of instances of:
<p stuffiwanttoremove>

I've been trying the Vim command:
%s/<p *>/<p>/ge

but it doesn't seem to work.

Does anybody know what I'm doing wrong?

I realise there may be alternatives to this (eg a bash script) so anything which works would be much appreciated!

Thanks.

---

### Post by PaulW2U on 2010-08-01
> **MeKino said:**
> 
I have several, big html files with lots of instances of:
<p stuffiwanttoremove>

I've been trying the Vim command:
%s/<p *>/<p>/ge

Your regular expression is missing a period. What you want to remove should be represented by .* and not *

Try: %s/<p **[COLOR="Red"].[/COLOR]***>/<p>/ge

Hope that helps.

---

### Post by MeKino on 2010-08-01
Brilliant! You're a star...

---

