---
title: "Mail Merge in Linux with Abiword"
date: 2011-10-08
forum: General Help
---

### Post by thornbush on 2011-10-08
I have been trying to do a Mail Merge in Linux through this week.
Finally, I was able to do with Abiword.
In order to accomplish a direct mail with Abiword, create a database file .csv (maybe with openoffice calc or gnumeric, saving as csv - comma separated values), write the "main text" and, at the terminal, execute:
# abiword -m file.csv --to=txt --to=mailing.txt file.abw
Or, if you would prefer it in post script:
# abiword -m file.csv --to=ps --to=mailing.ps file.abw

Note that -m is the parameter to the merge. After, there is the name of the .csv file (with path), ant the the parameters --to=ps and --to=[file name]. This parameter --to is an innovation of Abiword 2.8. In old wikis, I have found the parameter -p, about which the shell system announces that it is no more used in Abiword 2.8.

From: [http://forums.debian.net/viewtopic.php?f=16&t=71068&p=397248#p397248]("http://forums.debian.net/viewtopic.php?f=16&t=71068&p=397248#p397248")

---

