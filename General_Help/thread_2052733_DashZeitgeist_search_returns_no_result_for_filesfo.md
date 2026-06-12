---
title: "Dash/Zeitgeist search returns no result for files/folders (the rest is OK)"
date: 2012-09-03
forum: General Help
---

### Post by Iceberg76 on 2012-09-03
So far I tried:

-rm -rf ~/.local/share/zeitgeist

-installing unity-place-applications, unity-place-files

-logout/login

There is no privacy setting blocking zeitgeist recording any file.

In .xsession-errors:

** (zeitgeist-datahub:13996): WARNING **: zeitgeist-datahub.vala:227: Unable to get name "org.gnome.zeitgeist.datahub" on the bus!

Is there a way of maybe reset it? It has worked in the past and so.

---

### Post by Iceberg76 on 2012-09-04
Got the answer from another forum, and I'm posting it here for the record.

Ubuntu 12.04 uses unity-lens-*, instead of unity-place-*, where * can be music, applications, files, or video. Just substitute it for whatever is not working.

Run:

sudo apt-get purge unity-lens-files && sudo apt-get install unity-lens-files

(subtitute files for music, applciations, or video, if that's the case)

---

