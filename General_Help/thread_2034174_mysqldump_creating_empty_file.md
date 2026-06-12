---
title: "mysqldump creating empty file"
date: 2012-07-28
forum: General Help
---

### Post by Snoman314 on 2012-07-28
I've got a python script to backup a mediawiki database, running on an EC2 instance. I want the database etc to be backed up on shutdown, so that my instance can go offline and then restore everything on startup.

My problem is that every time I reboot, the output file from mysqldump is empty.
HOWEVER, when the same script is run by anacron, the file is full as expected.

I've pasted the script below.
I've got symlinks to the script in /etc/rc0.d and /etc/rc6.d.
In /etc/cron.hourly/ I have the following script:
```

#!/bin/bash

sudo /etc/init.d/backup-wiki.py

sudo /etc/init.d/s3-back

exit 0

```

I have this script there to ensure the wiki backup file is created before the files are backed up to S3 (external storage).
(in rc0.d and rc6.d, I have named the symlinks so that the wiki is backed up before the files are copied to S3).

Here's the code for /etc/init.d/backup-wiki.py:
```

#!/usr/bin/env python

import subprocess
import os

wiki_home = '/var/lib/mediawiki/'
settings_file_loc = '/etc/mediawiki/LocalSettings.php'
read_only_phrase = '$wgReadOnly = \'Site backup in progress\';\n'

sql_dump = '/home/ubuntu/sql.dump'
file_dump = '/home/ubuntu/file.dump'
xml_dump = '/home/ubuntu/xml.dump'
wiki_backup = '/home/ubuntu/wiki_bak.tgz'

mysqldump = '/usr/bin/mysqldump'
tar = '/bin/tar'
php = '/usr/bin/php'

# First, set the wiki to read-only

set_file = open(settings_file_loc, 'a')
set_file.write(read_only_phrase)
set_file.close()

# Then make a database dump

dump_file = open(sql_dump, 'w')
command = [mysqldump, '-u', 'root', '--all-databases', '--add-drop-table', '-B', '-c', '--default-character-set=latin1']
subprocess.call(command, stdout=dump_file)

# Then backup the filesystem

command = [tar, 'zcPf', file_dump, wiki_home + 'images/', wiki_home + 'extensions/', settings_file_loc]
subprocess.call(command)

# Then make the wiki writeable again

set_file = open(settings_file_loc, 'r')
lines = set_file.readlines()
set_file.close()

set_file = open(settings_file_loc, 'w')
for line in lines:
        if line != read_only_phrase:
                set_file.write(line)
set_file.close()

# Then do something with the various outputs generated above

command = [tar, 'zcPf', wiki_backup, sql_dump, file_dump]
subprocess.call(command)

os.remove(sql_dump)
os.remove(file_dump)
```

This script runs fine when I run it manually, or when it is run hourly by anacron. However, when it runs on shutdown or reboot the 'sql.dump' is 0 bytes.

I am stumped. Can anyone help?

---

### Post by Snoman314 on 2012-07-28
After reading some more, it seems like the problem might be due to Upstart shutting down mysql before my script gets a chance to run.

unfortunately I've no idea how upstart works. Can anyone suggest how I can get a script to run before mysql is shutdown?

---

