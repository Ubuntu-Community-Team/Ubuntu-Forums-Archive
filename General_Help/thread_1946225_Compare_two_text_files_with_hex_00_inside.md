---
title: "Compare two text files with hex 00 inside"
date: 2012-03-24
forum: General Help
---

### Post by Paddy Landau on 2012-03-24
I have two files that appear to be text (gedit can read them), but every character is followed by hex 00. See screen-shot:

[attach]214852[/attach]

(These files are exports of the Windows Registry.)

According to *file*, the files are "Little-endian UTF-16 Unicode text, with CRLF line terminators".

How can I compare these two files *as text*? They are large files (53Mb) with, I believe, few differences.

I have tried [Winhex]("http://www.x-ways.net/winhex/") (a Windows program but it compares the files as hex); iconv -f UTF16LE (it fails partway through); Diffuse Merge Tool; and Meld Diff Viewer.

I am stumped. Can you help please?

---

### Post by Dave_L on 2012-03-24
Do you want something like this?

That's a screen shot of a comparison made with BeyondCompare.

---

### Post by Paddy Landau on 2012-03-25
> **Dave_L said:**
> Do you want something like ... BeyondCompare.
Perfect! Thank you, Dave.

---

