---
title: "cron job deletes folder sometimes"
date: 2009-07-22
forum: General Help
---

### Post by mishkin on 2009-07-22
find /home/mishkin/.wine/drive_c/torrent/download/ mmin +800 -exec rm -rf {} \;

sometimes that deletes the folder ...download/ ... atm it seems to always do it... so I'm thinking if it finds nothing with mod time past 800 it deletes the folder...

because I have some brand new ones in there with little mod time and they are being deleted along with the folder

the folder being deleted breaks all my newer torrents and prevents new ones from being created

edit: it needs to be able to delete anything within /download/ including folders with folders in them

---

### Post by poosietgp on 2009-07-22
hi did you intentionally put the rm -rf there? i think the rm -rf is doing the deletions.

---

### Post by mishkin on 2009-07-23
well i never used to have a problem with this... i got it from a coder and many people use it

I'll try removing that but I'm thinking without it folders within folders won't get deleted???

"      -r, -R, --recursive
              remove directories and their contents recursively"

"    -f, --force
              ignore nonexistent files, never prompt"

edit: Yeah there was stuff older than 800min and it just wiped the whole folder again.... it never used to do that

edit: DOH just compared to origonal I'm missing the - infront of mmin... so -mmin +X .... 

but still if the folder ends up empty it will delete it (had this problem in the past) is there a way to make the folder undeletable by root or a way to make the search not default to finding the folder it's looking in?

---

