---
title: "Mangled system configuration file"
date: 2011-06-16
forum: General Help
---

### Post by Jeff Root on 2011-06-16
I just installed a 64-bit Narwhal, and wanted to
configure part of it the same way I configured my
Meerkat.  So I started the root terminal, typed
"visudo", and added a line to the "sudoers" file
which is located in the /etc folder.  Unfortunately
I made a silly goof when I entered the new line,
and now I can't edit the file anymore.  I can't
even alter the file from my Karmic Koala, which I'm
using right now.  (I deleted the Meerkat to make way
for the Whale, and the purpose of the change to the
"sudoers" file was to make Internet access easier.)
 
How can I either edit the "sudoers" file or replace
it with an unaltered copy?
 
   -- Jeff, in Minneapolis

---

### Post by Jeff Root on 2011-06-16
After 7 hours and only 22 views, this was on page 7,
so I'm resorting to a BUMP.
 
How can I either edit the "sudoers" file or replace
it with an unaltered copy?
 
   -- Jeff, in Minneapolis

---

### Post by oldos2er on 2011-06-16
[https://help.ubuntu.com/community/Sudoers](https://help.ubuntu.com/community/Sudoers)

---

### Post by Slim Odds on 2011-06-16
If you boot with the LiveCD, you can mount your hard drive and edit/copy any files that you want.

---

### Post by Jeff Root on 2011-06-17
Thanks for the link, oldos2er.  It at least tells
me how to edit the file correctly, though not how
to get out of my situation.
 
Slim Odds, I'll certainly try the LiveCD next,
though I expected Karmic Koala to be able to do
the job.  Although I suppose it is possible that
the reason it didn't could be that my Koala is
32-bit while my Narwhal is 64-bit.
 
Thank you!
 
   -- Jeff, in Minneapolis

---

### Post by oldos2er on 2011-06-17
If you read down the page there's a copy of a default sudoers file. It says it's for version 8.04 but I think it will work just fine in Natty.

---

