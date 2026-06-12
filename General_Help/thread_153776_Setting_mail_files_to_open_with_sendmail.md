---
title: "Setting mail files to open with sendmail"
date: 2006-04-01
forum: General Help
---

### Post by Ian Maxwell on 2006-04-01
I'm trying to set up files containing mail to be sendable by right-clicking them and choosing "open with sendmail". My first attempt was to add the following custom open command: "sendmail -t <"

This doesn't work; it seems the < is read as a recipient, not a redirection operator. (Note that actually typing in "sendmail -t < foo" works just fine.) How should I set this up?

---

### Post by dcstar on 2006-04-01
[QUOTE=Ian Maxwell]I'm trying to set up files containing mail to be sendable by right-clicking them and choosing "open with sendmail". My first attempt was to add the following custom open command: "sendmail -t <"

This doesn't work; it seems the < is read as a recipient, not a redirection operator. (Note that actually typing in "sendmail -t < foo" works just fine.) How should I set this up?[/QUOTE]
Try %f

[http://standards.freedesktop.org/desktop-entry-spec/latest/ar01s06.html](http://standards.freedesktop.org/desktop-entry-spec/latest/ar01s06.html)

---

### Post by Ian Maxwell on 2006-04-01
Thanks for the suggestion, but I got the same result (except that now %f was seen as a recipient as well).

Actually, I managed to solve the problem by just writing a shell script to handle it.

---

