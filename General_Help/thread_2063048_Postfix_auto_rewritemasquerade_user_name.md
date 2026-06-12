---
title: "Postfix auto rewrite/masquerade user name"
date: 2012-09-26
forum: General Help
---

### Post by szafran on 2012-09-26
Hi,

I've successfully configured postfix to forward any system mail warnings/messages (eg. from mdadm monitor, smartmontools etc.) from root account to my gmail account.
I've also setup a rewrite rule for the field "from" e-mail adress using:

in /etc/postfix/main.cf:
```
smtp_generic_maps = hash:/etc/postfix/generic
```

in /etc/postfix/generic:
```
@some.domain.org root@some.other.domain.org
```

This config works fine (no errors while forwarding, and even gmails spam filters don't treat those mail by default as spam).

Now every sent e-mail in the "from" field has 2 things:
```
From: Anacron <root@some.other.domain.org>
```

I'd like to know how to write a rule for that second thing (let's call it a NAME - in the example above it's "Anacron"). It would be nice to configure it to add something before that given NAME (eg. "[SERVER1] Anacron" or "[WORKSTATION4] Anacron" instead of just "Anacron"). The NAME's are different (eg. "Anacron" "root" etc), so the additional text needs to be added in front of what's allready there.

Unfortunatelly I didn't find anything on how to rewrite/masquerade this part of the "from" field, so I'm writing here, and maybe someone did (or knows how to do it) something like this before, and would like to share.

Thanks in advance for any help.

---

