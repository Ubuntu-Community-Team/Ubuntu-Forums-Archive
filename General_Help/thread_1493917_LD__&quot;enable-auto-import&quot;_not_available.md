---
title: "LD : &quot;enable-auto-import&quot; not available?"
date: 2010-05-26
forum: General Help
---

### Post by KalithDemoren on 2010-05-26
Hi !

I'm programming a cross platform application (supports Windows and Ubuntu), but I work with Windows most of the time.
Today I decided to check if my app was still compilable on Ubuntu. Before all that, I updated the system to the latest release (from 9.4 (or something) Hardy).

The problem is : since the update, I can compile my application just fine, but linkage fails because LD (v2.20.1) is missing several options :

[LIST]
[*]--enable-runtime-pseudo-reloc
[*]--enable-auto-image-base
[*]--enable-auto-import
[*]--add-stdcall-alias
[/LIST]
 I'm not entierly sure, but I think those commands used to work on Ubuntu. I've been using them on Windows with MinGW for a long time, and MinGW seems to have an earlier version of GCC than Ubuntu.
I've searched for a long time, but I couldn't find any site mentioning these were deprecated, or anything else that could explain why they are missing.

I hope you can enlight me a little,
Thanks.

---

