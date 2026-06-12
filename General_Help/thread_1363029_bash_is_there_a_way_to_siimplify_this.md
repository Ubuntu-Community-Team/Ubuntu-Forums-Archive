---
title: "bash: is there a way to siimplify this?"
date: 2009-12-23
forum: General Help
---

### Post by david90 on 2009-12-23
```
echo "" > tempout
echo "[Server Health Report Summary]" >> tempout
echo $(date) >> tempout
echo "[$RAID_CHK] Fileserver Raid" >> tempout
echo "[$BACKUP_CHK] Fileserver Backup System " >> tempout

echo "[$DISK_USAGE_CHK] Server Hard Disks Usage " >> tempout
echo "    $RAID_DISK disk size: $RAID_DISK_SIZE (Gigabyte).free Space: $RAID_FREE_DISK_SPACE (Gigabyte). $RAID_FREE_DISK_PERCENTAGE Used" >> tempout
echo "    $BACKUP_DISK disk size: $BACKUP_DISK_SIZE (Gigabyte). free Space: $BACKUP_FREE_DISK_SPACE (Gigabyte). $BACKUP_FREE_DISK_PERCENTAGE Used" >> tempout
echo "" >> tempout
echo "" >> tempout

echo "[RAID TECHNICAL INFORMATION]" >> tempout
echo $(cat /proc/mdstat) >> tempout
echo "" >> tempout

echo "[BACKUP TECHNICAL INFORMATION]" >> tempout
echo $(ls -l $BACKUP_MNT_LOCATION) >> tempout
echo "" >> tempout
echo "Backup directory check returns (1=bad, 0=good): $BACKUP_DIR_CHECK" >> tempout
echo "Number of backups: $NUM_BACKUP_ENTRY_CHK" >> tempout
echo "Latest backup age: $DAY0_AGE_CHK2" >> tempout
```Is there a way to simplify the code above?  As you can see, the script outputs each line of text to a file.  How do you put all the strings into one variable and this just execute "echo <var> > tempout" once?

---

### Post by falconindy on 2009-12-23
At the top of the file, you can do the following:

```
exec > tempout
```
This redirects all standard output to the file tempout, which means all your echo statements will be output to the file 'tempout' without the need for redirection on each line.

---

### Post by david90 on 2009-12-24
edited

---

