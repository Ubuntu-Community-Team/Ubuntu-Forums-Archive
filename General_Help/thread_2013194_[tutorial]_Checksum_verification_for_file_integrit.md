---
title: "[tutorial] Checksum verification for file integrity"
date: 2012-06-30
forum: General Help
---

### Post by twipley on 2012-06-30
Whenever performing backups,

> **Habitual said:**
> New hard drive or not,
Warnings or not,
Backup what you got.
Or you will be hot.

one might want to supplement their practices with file-hashes auditing, just in order to be in peace of mind regarding possible data-alteration happenstances, introduced either during transmission or storage. Auditing refers to the action of inspecting data integrity, comparing the state of current files to a set of past states.

A great tool in that respect is hashdeep, which can be installed and used following the below command guidelines. Note that the installation document should be executed as a program (be referred to the permissions tab of the file properties), and ran from the same folder as the source package.

```
# first off, the source package should be updated over at: http://sourceforge.net/projects/md5deep/files/latest/download?source=files
# then, this script file, placed into the same folder as the downloaded package file, is to be "ran in terminal;"

sudo apt-get install build-essential

tar -xf md5deep-*.tar.gz

cd ./md5deep-*

./configure

make

sudo make install

cd ..

mv md5deep-*/ temp

sudo rm -r temp

```


```
navigate to the parent folder relative to the one to be hashed: cd /path/to/parent/folder

create a list of file hashes (to be used in the future): hashdeep -r -l ./name_of_target_directory > name_of_hashes_list


navigate to the parent folder relative to the one to be audited: cd /path/to/parent/folder

perform an audit using a list of known hashes: hashdeep -v -v -r -l -a -k name_of_hashes_list ./name_of_target_directory

```

---

