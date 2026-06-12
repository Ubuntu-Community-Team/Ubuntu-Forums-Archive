---
title: "Apache 2.2 cgi-bin gets sucked down rabbithole"
date: 2010-08-02
forum: General Help
---

### Post by grikdog on 2010-08-02
I have a curious situation.  Until Lucid, this always worked.  My Apache 2.2 cgi-bin directory is the normal /usr/lib/cgi-bin.  I run Ruby 1.8.7 scripts from there.  One of those scripts includes the line

puts `/usr/bin/calendar`

However only one line from the entire output of calendar is added to my html file!  The stuff above and below that one call works fine, including other embedded system calls.

Why would the calendar program be truncated at one middle line?

This code works fine from the command line, but when piped through Firefox 3.6.8 it exits crippled.

Any ideas?

---

