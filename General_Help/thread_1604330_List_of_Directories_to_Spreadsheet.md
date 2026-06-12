---
title: "List of Directories to Spreadsheet"
date: 2010-10-23
forum: General Help
---

### Post by johnmata on 2010-10-23
Hi,

I have a large music directory that i'd like to somehow acquire, or generate, a list of each sub-folder within it, and then somehow get the list into a spreadsheet format.  Is there a way to do this?

Thanks,
John

---

### Post by ddoxey on 2010-10-23
Let's assume:
1. your music files are in the directory: ~/Music
2. your files are arranged as: <artist>/<album>/<title>.mp3

```
cd ~/Music
echo "Artist,Album,Title" > spreadsheet.csv
find -name '*.mp3' | awk -F\/ '{print $2","$3","$4}' >> spreadsheet.csv 

```

You can now open the file spreadsheet.csv with your favorite spreadsheet application.

---

