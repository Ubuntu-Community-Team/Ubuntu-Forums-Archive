---
title: "GUI for clamscan"
date: 2010-05-10
forum: General Help
---

### Post by cong06 on 2010-05-10
I'm working on a script that will allow people to easily clean up their flash drives:
```
#!/bin/bash
title="Virus Scan"

zenity --info --title="$title" --text="This will scan a flash drive for viruses.\n\nPlease press \"OK\" and then choose the drive."
scan=`zenity --title="Choose the folder to Scan" --file-selection --directory`

scan_name=`echo "$scan" | sed -e "s/\//-/g"`
date=`date --rfc-3339=seconds | sed -e "s/ /@/g"`
dump="/var/clamscan/${date}-${scan_name}"
mkdir -p $dump/

clamscan --recursive --move=$dump/ --detect-broken=yes --detect-pua=yes $scan

if [ $? -eq 0 ]; then
    zenity --info --title="$title" --text="There were no viruses. The flash drive selected is clean."
    exit 0
else
    zenity --info --title="$title" --text="Please check through the folder now, and see if any important files are missing.\n\nPlease see a Technician to help you recover any missing files."
    nautilus --browser $scan/ &
fi

```
It uses clamscan and zenity to make it fairly easy to allow people to scan their drives/folders on their own.

The main issue at this point is that I can't figure out a good way to handle the pause while it's searching. Since the script will be run from a "*.desktop" file, no terminal output will be shown.
If a computer sits and works without showing any difference, the general user will complain that the computer froze, so I want to show that the computer is working.

So far the best I can come up with is forcing it to be printed in xterm:
```

xterm -e clamscan --recursive --move=$dump/ --detect-broken=yes --detect-pua=yes $scan

```
Any ideas?
Or any ideas on the script in general?

---

