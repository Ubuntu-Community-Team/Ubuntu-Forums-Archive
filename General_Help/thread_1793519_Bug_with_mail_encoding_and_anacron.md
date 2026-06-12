---
title: "Bug with mail encoding and anacron"
date: 2011-06-29
forum: General Help
---

### Post by ygoe on 2011-06-29
Hi,

there is an error in Ubuntu 10.4's anacron. It doesn't send the correct encoding header in e-mails. The system encoding is UTF-8 (by default) but the e-mails sent out by anacron don't have any encoding or content-type headers. So by default, ISO-8859-1 will be considered here, which does not match the content.

Even specifying the CONTENT_TYPE environment variable in the anacrontab file doesn't help (although it does - and is still required, which it should not be - in the crontab file).

Since this leads to wrong or unreadable e-mail messages sent, I consider this a bug that should be fixed. Does anybody disagree?

Unfortunately, I cannot report a bug in Launchpad. The link "report a bug" in linked with a Wiki page that talks a lot but doesn't let me report a bug. I guess somebody else with a more privileged account than mine is supposed to do that.

Recently, my unattended-upgrade job has started to talk in German with me, which it hasn't done before, and I don't know why. That's not a problem, but now I could need the correct character encoding for all sorts of information it prints out. In English this wasn't a problem.

---

### Post by dcstar on 2011-06-30
> **LonelyPixel said:**
> Hi,

there is an error in Ubuntu 10.4's anacron. It doesn't send the correct encoding header in e-mails. The system encoding is UTF-8 (by default) but the e-mails sent out by anacron don't have any encoding or content-type headers. So by default, ISO-8859-1 will be considered here, which does not match the content.
........

AFAIK plain text email does not require - or should require - encoding.

---

### Post by ygoe on 2011-06-30
Of course plain text (or any) e-mail requires encoding. You probably won't see the problem very often if English is the only language you use, because mapping bytes (what you get) to characters (what you need) is usually done using the single-byte character set ISO-8859-1 if not specified otherwise. But imagine some non-latin languages (Russian, Arabic, Chinese, ...) - you won't get anywhere without specifying an encoding. No matter what content type you use (at least plain text and HTML).

---

