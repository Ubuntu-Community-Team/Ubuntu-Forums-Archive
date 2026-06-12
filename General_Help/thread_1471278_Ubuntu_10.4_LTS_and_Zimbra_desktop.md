---
title: "Ubuntu 10.4 LTS and Zimbra desktop"
date: 2010-05-03
forum: General Help
---

### Post by badaveil on 2010-05-03
I did not get much help from Zimbra forum so I'm trying my luck here:

1. I downloaded zdesktop_1_0_4_build_1833_linux_i686.sh
2. Under terminal I typed "sudo install /zdesktop_1_0_4_build_1833_linux_i686.sh"
3. I am requested and enter administrator password and get reply "install: missing destination file operand after `/zdesktop_1_0_4_build_1833_linux_i686.sh'"

I'm lost. What do I do now?

---

### Post by P4man on 2010-05-03
> **badaveil said:**
> I did not get much help from Zimbra forum so I'm trying my luck here:

1. I downloaded zdesktop_1_0_4_build_1833_linux_i686.sh
2. Under terminal I typed "sudo install /zdesktop_1_0_4_build_1833_linux_i686.sh"
3. I am requested and enter administrator password and get reply "install: missing destination file operand after `/zdesktop_1_0_4_build_1833_linux_i686.sh'"

I'm lost. What do I do now?

assuming that is an install shell script, try this:

```
sudo ./zdesktop-etc-etc-press-TAB-key to avoid typing all this 
```

note the ".". dot slash means current directory, where as what you typed, slash, refers to the root.

---

### Post by badaveil on 2010-05-03
> **P4man said:**
> assuming that is an install shell script, try this:

```
sudo ./zdesktop-etc-etc-press-TAB-key to avoid typing all this 
```

note the ".". dot slash means current directory, where as what you typed, slash, refers to the root.

Well, I got this:

user@pc:~$ sudo ./zdesktop_1_0_4_build_1833_linux_i686.sh
[sudo] password for user: 
sudo: ./zdesktop_1_0_4_build_1833_linux_i686.sh: command not found
user@pc:~$

---

### Post by P4man on 2010-05-04
That command only works in the directory where you put that file in. If you downloaded it to, say, /home/yourname/Downloads then you have to change directoty there first

```
cd Downloads
```

you can list the files in your current directory by typing

```
ls
```

Also note everything in linux is case sensitive. If that file, or the folder you downloaded it to has an UPPERCASE somewehere, you must type it as such

---

### Post by badaveil on 2010-05-04
> **P4man said:**
> That command only works in the directory where you put that file in. If you downloaded it to, say, /home/yourname/Downloads then you have to change directoty there first

```
cd Downloads
```

you can list the files in your current directory by typing

```
ls
```

Also note everything in linux is case sensitive. If that file, or the folder you downloaded it to has an UPPERCASE somewehere, you must type it as such

I don't understand something and understand something:

1. The file is at /home/user/downloads/zdesktop_1_0_4_build_1833_linux_i686.sh

But to change the directory from there to where? I'm confused here.

2. I terminal-ed the "ls" and got the following:

user@pc:~$ ls
Administraton  examples.desktop      macgdi    Templates
Desktop        googleearth           Music     ubuntu-10.04-desktop-i386.iso
Documents      google-earth          Pictures  Videos
Downloads      GoogleEarthLinux.bin  Public
user@pc:~$ 

Right, next step please.

---

### Post by polki@mac.com on 2010-05-04
The little squiggle tells you that you are in your home (/home/yourusername/) so all you have to do is:

```
cd Downloads
```

Please note that Linux considers "d" and "D" two different letters.
Hope this helps a bit.

---

### Post by P4man on 2010-05-04
> 1. The file is at /home/user/downloads/zdesktop_1_0_4_build_1833_linux_i686.sh

But to change the directory from there to where? I'm confused here.

When you open a terminal, your current directory is your home directory. The full path of that is 

/home/yourusername

(since your username seems to be "user" that is /home/user)

Since this is quite an often used directory, there is a shorthand for it, the tilde (~).

You see that in the prompt:
user@pc:[COLOR="Red"]**~**[/COLOR]$ 

The installer you downloaded is in a subfolder of your homefolder called Downloads. As mentioned above, its case sensitive.

So either you change the current directory and then execute the command, or you give the instruction with the full path. BTW, I think I forgot to mention you need to add "sh" to execute the script in a (root) shell.

So first change the current directory:

```
cd Downloads
```

You should see the prompt change to

user@pc:~/Downloads$ 

then execute the script in a shell as root (administrator)

```
sudo sh ./zdesktop-etc-etc
```

Please note you dont have to type all that. Type the first few characters of a file name or directory name, and hit the TAB key to complete the namee. If there are more than one matches for the letters you typed, hit tab again and you will see a list of matching file and directory names. That also ensures you make no typing error.

Note two. The "./" in front of the filename may make you wonder why its needed. dot slash (./) denotes the current directory. Strange as it may seem, if you run a command in the shell, the interpreter will look in all directories in your path (you remember that from Dos?) but it will not look in the currect directory unless you specify it. The current directory is not in the search path. took me a while before I figured that out, so I thought Id mention :)

---

### Post by badaveil on 2010-05-04
P4man

Firstly, thank you very much for your help. I have never done this cd Downloads thing before in my life and my own errors were staring me in the face for some time. I must have been mentally blind but after doing a fresh terminal, got the results below. A new problem has arisen is that the Zimbra icon surprisingly does not appear anyway under the Main menu,sub-folders or sub-sub folders but that is a different issue I ought not to bother you with. Thanking you again for your help.

user@pc:~/Downloads$ sudo sh ./zdesktop_1_0_4_build_1833_linux_i686.sh
[sudo] password for user: 
Unpacking JRE ...
Preparing JRE ...
Starting Installer ...
ij version 10.3
ij> CONNECT 'jdbc:derby:/root/zimbra/zdesktop/derby;create=true';
ij> RUN '/root/zimbra/zdesktop/db/db.sql';
ij> --
-- ***** BEGIN LICENSE BLOCK *****
--
-- Zimbra Collaboration Suite Server
-- Copyright (C) 2007 Zimbra, Inc.
--
-- The contents of this file are subject to the Yahoo! Public License
-- Version 1.0 ("License"); you may not use this file except in
-- compliance with the License.  You may obtain a copy of the License at
-- [http://www.zimbra.com/license](http://www.zimbra.com/license).
--
-- Software distributed under the License is distributed on an "AS IS"
-- basis, WITHOUT WARRANTY OF ANY KIND, either express or implied.
--
-- ***** END LICENSE BLOCK *****
--

CALL SYSCS_UTIL.SYSCS_SET_DATABASE_PROPERTY('derby.storage.pageSize', '16384');
0 rows inserted/updated/deleted
ij> CALL SYSCS_UTIL.SYSCS_SET_DATABASE_PROPERTY('derby.storage.pageCacheSize', '1000');
0 rows inserted/updated/deleted
ij> CALL SYSCS_UTIL.SYSCS_SET_DATABASE_PROPERTY('derby.language.logQueryPlan', 'true');
0 rows inserted/updated/deleted
ij> CALL SYSCS_UTIL.SYSCS_SET_DATABASE_PROPERTY('derby.language.logStatementText', 'true');
0 rows inserted/updated/deleted
ij> CREATE SCHEMA zimbra;
0 rows inserted/updated/deleted
ij> SET SCHEMA zimbra;
0 rows inserted/updated/deleted
ij> -- -----------------------------------------------------------------------
-- volumes
-- -----------------------------------------------------------------------

-- list of known volumes
CREATE TABLE volume (
   id                     SMALLINT NOT NULL GENERATED BY DEFAULT AS IDENTITY,
   type                   SMALLINT NOT NULL,      -- 1 = primary msg, 2 = secondary msg, 10 = index
   name                   VARCHAR(255) NOT NULL,
   path                   VARCHAR(32672) NOT NULL,
   file_bits              SMALLINT NOT NULL,
   file_group_bits        SMALLINT NOT NULL,
   mailbox_bits           SMALLINT NOT NULL,
   mailbox_group_bits     SMALLINT NOT NULL,
   compress_blobs         SMALLINT NOT NULL,
   compression_threshold  BIGINT NOT NULL,

   CONSTRAINT pk_volume PRIMARY KEY (id),
   CONSTRAINT ui_volume_name UNIQUE (name),
   CONSTRAINT ui_volume_path UNIQUE (path)
);
0 rows inserted/updated/deleted
ij> -- This table has only one row.  It points to message and index volumes
-- to use for newly provisioned mailboxes.
CREATE TABLE current_volumes (
   message_volume_id            SMALLINT NOT NULL,
   secondary_message_volume_id  SMALLINT,
   index_volume_id              SMALLINT NOT NULL,
   next_mailbox_id              INTEGER NOT NULL,

   CONSTRAINT pk_current_volumes_message_volume_id PRIMARY KEY (message_volume_id),
   CONSTRAINT fk_current_volumes_message_volume_id FOREIGN KEY (message_volume_id) REFERENCES volume(id),
   CONSTRAINT fk_current_volumes_secondary_message_volume_id FOREIGN KEY (secondary_message_volume_id) REFERENCES volume(id),
   CONSTRAINT fk_current_volumes_index_volume_id FOREIGN KEY (index_volume_id) REFERENCES volume(id)
);
0 rows inserted/updated/deleted
ij> CREATE INDEX i_message_volume_id ON current_volumes(message_volume_id);
0 rows inserted/updated/deleted
WARNING 01504: The new index is a duplicate of an existing index: SQL100504174157750.
ij> CREATE INDEX i_secondary_message_volume_id ON current_volumes(secondary_message_volume_id);
0 rows inserted/updated/deleted
WARNING 01504: The new index is a duplicate of an existing index: SQL100504174157752.
ij> CREATE INDEX i_index_volume_id ON current_volumes(index_volume_id);
0 rows inserted/updated/deleted
WARNING 01504: The new index is a duplicate of an existing index: SQL100504174157753.
ij> -- -----------------------------------------------------------------------
-- mailbox info
-- -----------------------------------------------------------------------

CREATE TABLE mailbox (
   id                 INTEGER NOT NULL,
   group_id           INTEGER NOT NULL,           -- mailbox group
   account_id         VARCHAR(127) NOT NULL,          -- e.g. "d94e42c4-1636-11d9-b904-4dd689d02402"
   index_volume_id    SMALLINT NOT NULL,
   item_id_checkpoint INTEGER NOT NULL DEFAULT 0,
   contact_count      INTEGER DEFAULT 0,
   size_checkpoint    BIGINT NOT NULL DEFAULT 0,
   change_checkpoint  INTEGER NOT NULL DEFAULT 0,
   tracking_sync      INTEGER NOT NULL DEFAULT 0,
   tracking_imap      SMALLINT NOT NULL DEFAULT 0,
   last_backup_at     INTEGER,                    -- last full backup time, UNIX-style timestamp
   comment            VARCHAR(255),               -- usually the main email address originally associated with the mailbox
   last_soap_access   INTEGER NOT NULL DEFAULT 0,
   new_messages       INTEGER NOT NULL DEFAULT 0,
   idx_deferred_count INTEGER NOT NULL DEFAULT 0,

   CONSTRAINT pk_mailbox PRIMARY KEY (id),
   CONSTRAINT ui_mailbox_account_id UNIQUE (account_id),
   CONSTRAINT fk_mailbox_index_volume_id FOREIGN KEY (index_volume_id) REFERENCES volume(id)
);
0 rows inserted/updated/deleted
ij> CREATE INDEX i_mailbox_index_volume_id ON mailbox(index_volume_id);
0 rows inserted/updated/deleted
WARNING 01504: The new index is a duplicate of an existing index: SQL100504174158192.
ij> CREATE INDEX i_last_backup_at ON mailbox(last_backup_at, id);
0 rows inserted/updated/deleted
ij> -- -----------------------------------------------------------------------
-- deleted accounts
-- -----------------------------------------------------------------------

CREATE TABLE deleted_account (
    email VARCHAR(255) NOT NULL,
    account_id VARCHAR(127) NOT NULL,
    mailbox_id INTEGER NOT NULL,
    deleted_at INTEGER NOT NULL,      -- UNIX-style timestamp
   
    CONSTRAINT pk_deleted_account PRIMARY KEY (email)
);
0 rows inserted/updated/deleted
ij> -- -----------------------------------------------------------------------
-- mailbox metadata info
-- -----------------------------------------------------------------------

CREATE TABLE mailbox_metadata (
   mailbox_id  INTEGER NOT NULL,
   section     VARCHAR(64) NOT NULL,       -- e.g. "imap"
   metadata    CLOB,

   CONSTRAINT pk_metadata PRIMARY KEY (mailbox_id, section),
   CONSTRAINT fk_metadata_mailbox_id FOREIGN KEY (mailbox_id) REFERENCES mailbox(id) ON DELETE CASCADE
);
0 rows inserted/updated/deleted
ij> -- -----------------------------------------------------------------------
-- out-of-office reply history
-- -----------------------------------------------------------------------

CREATE TABLE out_of_office (
  mailbox_id  INTEGER NOT NULL,
  sent_to     VARCHAR(255) NOT NULL,
  sent_on     TIMESTAMP NOT NULL,

  CONSTRAINT pk_out_of_office PRIMARY KEY (mailbox_id, sent_to),
  CONSTRAINT fk_out_of_office_mailbox_id FOREIGN KEY (mailbox_id) REFERENCES mailbox(id) ON DELETE CASCADE
);
0 rows inserted/updated/deleted
ij> CREATE INDEX i_out_of_office_sent_on ON out_of_office(sent_on);
0 rows inserted/updated/deleted
ij> -- -----------------------------------------------------------------------
-- etc.
-- -----------------------------------------------------------------------

-- table for global config params
CREATE TABLE config (
  name         VARCHAR(255) NOT NULL,
  value        CLOB,
  description  CLOB,
  modified     TIMESTAMP,

  CONSTRAINT pk_config PRIMARY KEY (name)
);
0 rows inserted/updated/deleted
ij> -- Tracks scheduled tasks
CREATE TABLE scheduled_task (
   class_name      VARCHAR(255) NOT NULL,
   name            VARCHAR(255) NOT NULL,
   mailbox_id      INTEGER NOT NULL,
   exec_time       TIMESTAMP,
   interval_millis INTEGER,
   metadata        CLOB,

   CONSTRAINT pk_scheduled_task PRIMARY KEY (name, mailbox_id, class_name),
   CONSTRAINT fk_st_mailbox_id FOREIGN KEY (mailbox_id)
      REFERENCES mailbox(id) ON DELETE CASCADE
);
0 rows inserted/updated/deleted
ij> CREATE INDEX i_scheduled_task_mailbox_id ON scheduled_task(mailbox_id);
0 rows inserted/updated/deleted
WARNING 01504: The new index is a duplicate of an existing index: SQL100504174159611.
ij> RUN '/root/zimbra/zdesktop/db/directory.sql';
ij> --
-- ***** BEGIN LICENSE BLOCK *****
--
-- Zimbra Collaboration Suite Server
-- Copyright (C) 2007 Zimbra, Inc.
--
-- The contents of this file are subject to the Yahoo! Public License
-- Version 1.0 ("License"); you may not use this file except in
-- compliance with the License.  You may obtain a copy of the License at
-- [http://www.zimbra.com/license](http://www.zimbra.com/license).
--
-- Software distributed under the License is distributed on an "AS IS"
-- basis, WITHOUT WARRANTY OF ANY KIND, either express or implied.
--
-- ***** END LICENSE BLOCK *****
--


-- -----------------------------------------------------------------------
-- directory
-- -----------------------------------------------------------------------

CREATE TABLE directory (
   entry_id    INTEGER NOT NULL GENERATED BY DEFAULT AS IDENTITY,
   entry_type  CHAR(4) NOT NULL,
   entry_name  VARCHAR(128) NOT NULL,
   zimbra_id   CHAR(36),
   modified    SMALLINT NOT NULL,

   CONSTRAINT pk_directory PRIMARY KEY (entry_id),
   CONSTRAINT ui_directory_entry_type_name UNIQUE(entry_type, entry_name)
);
0 rows inserted/updated/deleted
ij> CREATE UNIQUE INDEX ui_directory_zimbra_id ON directory(zimbra_id);
0 rows inserted/updated/deleted
ij> CREATE TABLE directory_attrs (
   entry_id    INTEGER NOT NULL,
   name        VARCHAR(255) NOT NULL,
   value       VARCHAR(32672) NOT NULL,

   CONSTRAINT fk_dattr_entry_id FOREIGN KEY (entry_id) REFERENCES directory(entry_id)
      ON DELETE CASCADE
);
0 rows inserted/updated/deleted
ij> CREATE INDEX i_dattr_entry_id_name ON directory_attrs(entry_id, name);
0 rows inserted/updated/deleted
ij> CREATE INDEX i_dattr_name ON directory_attrs(name);
0 rows inserted/updated/deleted
ij> CREATE TABLE directory_leaf (
   entry_id    INTEGER NOT NULL GENERATED BY DEFAULT AS IDENTITY,
   parent_id   INTEGER NOT NULL,
   entry_type  CHAR(4) NOT NULL,
   entry_name  VARCHAR(128) NOT NULL,
   zimbra_id   CHAR(36) NOT NULL,

   CONSTRAINT pk_dleaf PRIMARY KEY (entry_id),
   CONSTRAINT ui_dleaf_zimbra_id UNIQUE (zimbra_id),
   CONSTRAINT ui_dleaf_parent_entry_type_name UNIQUE (parent_id, entry_type, entry_name),
   CONSTRAINT fk_dleaf_entry_id FOREIGN KEY (parent_id) REFERENCES directory(entry_id)
      ON DELETE CASCADE
);
0 rows inserted/updated/deleted
ij> CREATE TABLE directory_leaf_attrs (
   entry_id    INTEGER NOT NULL,
   name        VARCHAR(255) NOT NULL,
   value       VARCHAR(32672) NOT NULL,

   CONSTRAINT fk_dleafattr_entry_id FOREIGN KEY (entry_id) REFERENCES directory_leaf(entry_id)
      ON DELETE CASCADE
);
0 rows inserted/updated/deleted
ij> CREATE INDEX i_dleafattr_entry_id_name ON directory_leaf_attrs(entry_id, name);
0 rows inserted/updated/deleted
ij> CREATE INDEX i_dleafattr_name ON directory_leaf_attrs(name);
0 rows inserted/updated/deleted
ij> CREATE TABLE directory_granter (
   granter_name  VARCHAR(128) NOT NULL,
   granter_id    CHAR(36) NOT NULL,
   grantee_id    CHAR(36) NOT NULL,

   CONSTRAINT pk_dgranter PRIMARY KEY (granter_name, grantee_id)
);
0 rows inserted/updated/deleted
ij> CREATE INDEX i_dgranter_gter_name ON directory_granter(granter_name);
0 rows inserted/updated/deleted
ij> CREATE INDEX i_dgranter_gter_id ON directory_granter(granter_id);
0 rows inserted/updated/deleted
ij> CREATE INDEX i_dgranter_gtee_id ON directory_granter(grantee_id);
0 rows inserted/updated/deleted
ij> RUN '/root/zimbra/zdesktop/db/versions-init.sql';
ij> -- AUTO-GENERATED .SQL FILE - Generated by the Derby versions tool
INSERT INTO zimbra.config(name, value, description) VALUES
	('db.version', '53', 'db schema version'),
	('index.version', '2', 'index version'),
	('redolog.version', '1.24', 'redolog version'),
	('offline.db.version', '3', 'offline db schema version');
4 rows inserted/updated/deleted
ij> INSERT INTO volume (id, type, name, path, file_bits, file_group_bits,
			    mailbox_bits, mailbox_group_bits, compress_blobs, compression_threshold)
			  VALUES (1, 1, 'message1', '/root/zimbra/zdesktop/store', 12, 8, 12, 8, 0, 4096);
1 row inserted/updated/deleted
ij> INSERT INTO volume (id, type, name, path, file_bits, file_group_bits,
			    mailbox_bits, mailbox_group_bits, compress_blobs, compression_threshold)
			  VALUES (2, 10, 'index1', '/root/zimbra/zdesktop/index', 12, 8, 12, 8, 0, 4096);
1 row inserted/updated/deleted
ij> INSERT INTO current_volumes (message_volume_id, index_volume_id, next_mailbox_id) VALUES (1, 2, 1);
1 row inserted/updated/deleted
ij> EXIT;
user@pc:~/Downloads$

---

### Post by P4man on 2010-05-04
Well, if no icon is created, its because the install script doesnt do it. Have to keep in mind the primary way to install software in ubuntu is the software center. unfortunately, zimbra isnt available there, and nor can I find an ubuntu package for it, so you are left with a generic installer that requires a command line and might not even work becuase of dependency issues..

assuming the app actually works when you launch it from the command line (does it?), you can create your own launcher easily though. Just right click the main menu, edit menu's and create a new item. Or create a launcher on your desktop or panel, whereever you want it. Do feel free to ask, we're here to help :)

---

### Post by P4man on 2010-05-04
btw, it seems to setup the app for user "root", not for your user. Are you sure you need to run the install script as root (using sudo?). You may try running it again without sudo. It looks like a java app, it may not need root privileges to install.

---

### Post by badaveil on 2010-05-04
> **P4man said:**
> btw, it seems to setup the app for user "root", not for your user. Are you sure you need to run the install script as root (using sudo?). You may try running it again without sudo. It looks like a java app, it may not need root privileges to install.


[IMG]http://lh3.ggpht.com/_yJ5Rhn3UxL4/S9_6Qsb571I/AAAAAAAADDk/rPa5oborT3c/s800/Screenshot-1.png[/IMG]

Yes, I got it this time! Thanks to you telling me to re-do it again but less "sudo".I placed the files under /home/user/zdesktop because it rejected the default path into /root. A proper Zimbra desktop icon didn't appear as you can see but now I know the command by looking up the icon properties. I've already created a Zimbra Desktop launcher in the Main Menu and for some strange reason that earlier desktop icon didn't work though the command I took to create the launcher does :D.

I'm so happy getting up to here, I just need to jot down the incoming mail server's name from my dept's IT administrator tomorrow.

P4man, You're a swell guy. Thanks again.

user@pc:~$ cd Downloads
user@pc:~/Downloads$ sh ./zdesktop_1_0_4_build_1833_linux_i686.sh
Unpacking JRE ...
Preparing JRE ...
Starting Installer ...
Warning: Cannot convert string "-b&h-lucidasans-medium-r-normal-sans-*-140-*-*-p-*-iso8859-1" to type FontStruct
/usr/share/themes/Ambiance/gtk-2.0/gtkrc:71: Failed to parse property value " GTK_SHADOW_NONE " for `GtkToolbar::shadow-type'
/usr/share/themes/Ambiance/gtk-2.0/gtkrc:72: Failed to parse property value " GTK_SHADOW_NONE " for `GtkMenuBar::shadow-type'
/usr/share/themes/Ambiance/gtk-2.0/gtkrc:75: error: lexical error or unexpected token, expected valid token
ij version 10.3
ij> CONNECT 'jdbc:derby:/home/user/zdesktop/derby;create=true';
ij> RUN '/home/user/zdesktop/db/db.sql';
ij> --
-- ***** BEGIN LICENSE BLOCK *****
--
-- Zimbra Collaboration Suite Server
-- Copyright (C) 2007 Zimbra, Inc.
--
-- The contents of this file are subject to the Yahoo! Public License
-- Version 1.0 ("License"); you may not use this file except in
-- compliance with the License.  You may obtain a copy of the License at
-- [http://www.zimbra.com/license](http://www.zimbra.com/license).
--
-- Software distributed under the License is distributed on an "AS IS"
-- basis, WITHOUT WARRANTY OF ANY KIND, either express or implied.
--
-- ***** END LICENSE BLOCK *****
--

CALL SYSCS_UTIL.SYSCS_SET_DATABASE_PROPERTY('derby.storage.pageSize', '16384');
0 rows inserted/updated/deleted
ij> CALL SYSCS_UTIL.SYSCS_SET_DATABASE_PROPERTY('derby.storage.pageCacheSize', '1000');
0 rows inserted/updated/deleted
ij> CALL SYSCS_UTIL.SYSCS_SET_DATABASE_PROPERTY('derby.language.logQueryPlan', 'true');
0 rows inserted/updated/deleted
ij> CALL SYSCS_UTIL.SYSCS_SET_DATABASE_PROPERTY('derby.language.logStatementText', 'true');
0 rows inserted/updated/deleted
ij> CREATE SCHEMA zimbra;
0 rows inserted/updated/deleted
ij> SET SCHEMA zimbra;
0 rows inserted/updated/deleted
ij> -- -----------------------------------------------------------------------
-- volumes
-- -----------------------------------------------------------------------

-- list of known volumes
CREATE TABLE volume (
   id                     SMALLINT NOT NULL GENERATED BY DEFAULT AS IDENTITY,
   type                   SMALLINT NOT NULL,      -- 1 = primary msg, 2 = secondary msg, 10 = index
   name                   VARCHAR(255) NOT NULL,
   path                   VARCHAR(32672) NOT NULL,
   file_bits              SMALLINT NOT NULL,
   file_group_bits        SMALLINT NOT NULL,
   mailbox_bits           SMALLINT NOT NULL,
   mailbox_group_bits     SMALLINT NOT NULL,
   compress_blobs         SMALLINT NOT NULL,
   compression_threshold  BIGINT NOT NULL,

   CONSTRAINT pk_volume PRIMARY KEY (id),
   CONSTRAINT ui_volume_name UNIQUE (name),
   CONSTRAINT ui_volume_path UNIQUE (path)
);
0 rows inserted/updated/deleted
ij> -- This table has only one row.  It points to message and index volumes
-- to use for newly provisioned mailboxes.
CREATE TABLE current_volumes (
   message_volume_id            SMALLINT NOT NULL,
   secondary_message_volume_id  SMALLINT,
   index_volume_id              SMALLINT NOT NULL,
   next_mailbox_id              INTEGER NOT NULL,

   CONSTRAINT pk_current_volumes_message_volume_id PRIMARY KEY (message_volume_id),
   CONSTRAINT fk_current_volumes_message_volume_id FOREIGN KEY (message_volume_id) REFERENCES volume(id),
   CONSTRAINT fk_current_volumes_secondary_message_volume_id FOREIGN KEY (secondary_message_volume_id) REFERENCES volume(id),
   CONSTRAINT fk_current_volumes_index_volume_id FOREIGN KEY (index_volume_id) REFERENCES volume(id)
);
0 rows inserted/updated/deleted
ij> CREATE INDEX i_message_volume_id ON current_volumes(message_volume_id);
0 rows inserted/updated/deleted
WARNING 01504: The new index is a duplicate of an existing index: SQL100504183557410.
ij> CREATE INDEX i_secondary_message_volume_id ON current_volumes(secondary_message_volume_id);
0 rows inserted/updated/deleted
WARNING 01504: The new index is a duplicate of an existing index: SQL100504183557412.
ij> CREATE INDEX i_index_volume_id ON current_volumes(index_volume_id);
0 rows inserted/updated/deleted
WARNING 01504: The new index is a duplicate of an existing index: SQL100504183557413.
ij> -- -----------------------------------------------------------------------
-- mailbox info
-- -----------------------------------------------------------------------

CREATE TABLE mailbox (
   id                 INTEGER NOT NULL,
   group_id           INTEGER NOT NULL,           -- mailbox group
   account_id         VARCHAR(127) NOT NULL,          -- e.g. "d94e42c4-1636-11d9-b904-4dd689d02402"
   index_volume_id    SMALLINT NOT NULL,
   item_id_checkpoint INTEGER NOT NULL DEFAULT 0,
   contact_count      INTEGER DEFAULT 0,
   size_checkpoint    BIGINT NOT NULL DEFAULT 0,
   change_checkpoint  INTEGER NOT NULL DEFAULT 0,
   tracking_sync      INTEGER NOT NULL DEFAULT 0,
   tracking_imap      SMALLINT NOT NULL DEFAULT 0,
   last_backup_at     INTEGER,                    -- last full backup time, UNIX-style timestamp
   comment            VARCHAR(255),               -- usually the main email address originally associated with the mailbox
   last_soap_access   INTEGER NOT NULL DEFAULT 0,
   new_messages       INTEGER NOT NULL DEFAULT 0,
   idx_deferred_count INTEGER NOT NULL DEFAULT 0,

   CONSTRAINT pk_mailbox PRIMARY KEY (id),
   CONSTRAINT ui_mailbox_account_id UNIQUE (account_id),
   CONSTRAINT fk_mailbox_index_volume_id FOREIGN KEY (index_volume_id) REFERENCES volume(id)
);
0 rows inserted/updated/deleted
ij> CREATE INDEX i_mailbox_index_volume_id ON mailbox(index_volume_id);
0 rows inserted/updated/deleted
WARNING 01504: The new index is a duplicate of an existing index: SQL100504183557922.
ij> CREATE INDEX i_last_backup_at ON mailbox(last_backup_at, id);
0 rows inserted/updated/deleted
ij> -- -----------------------------------------------------------------------
-- deleted accounts
-- -----------------------------------------------------------------------

CREATE TABLE deleted_account (
    email VARCHAR(255) NOT NULL,
    account_id VARCHAR(127) NOT NULL,
    mailbox_id INTEGER NOT NULL,
    deleted_at INTEGER NOT NULL,      -- UNIX-style timestamp
   
    CONSTRAINT pk_deleted_account PRIMARY KEY (email)
);
0 rows inserted/updated/deleted
ij> -- -----------------------------------------------------------------------
-- mailbox metadata info
-- -----------------------------------------------------------------------

CREATE TABLE mailbox_metadata (
   mailbox_id  INTEGER NOT NULL,
   section     VARCHAR(64) NOT NULL,       -- e.g. "imap"
   metadata    CLOB,

   CONSTRAINT pk_metadata PRIMARY KEY (mailbox_id, section),
   CONSTRAINT fk_metadata_mailbox_id FOREIGN KEY (mailbox_id) REFERENCES mailbox(id) ON DELETE CASCADE
);
0 rows inserted/updated/deleted
ij> -- -----------------------------------------------------------------------
-- out-of-office reply history
-- -----------------------------------------------------------------------

CREATE TABLE out_of_office (
  mailbox_id  INTEGER NOT NULL,
  sent_to     VARCHAR(255) NOT NULL,
  sent_on     TIMESTAMP NOT NULL,

  CONSTRAINT pk_out_of_office PRIMARY KEY (mailbox_id, sent_to),
  CONSTRAINT fk_out_of_office_mailbox_id FOREIGN KEY (mailbox_id) REFERENCES mailbox(id) ON DELETE CASCADE
);
0 rows inserted/updated/deleted
ij> CREATE INDEX i_out_of_office_sent_on ON out_of_office(sent_on);
0 rows inserted/updated/deleted
ij> -- -----------------------------------------------------------------------
-- etc.
-- -----------------------------------------------------------------------

-- table for global config params
CREATE TABLE config (
  name         VARCHAR(255) NOT NULL,
  value        CLOB,
  description  CLOB,
  modified     TIMESTAMP,

  CONSTRAINT pk_config PRIMARY KEY (name)
);
0 rows inserted/updated/deleted
ij> -- Tracks scheduled tasks
CREATE TABLE scheduled_task (
   class_name      VARCHAR(255) NOT NULL,
   name            VARCHAR(255) NOT NULL,
   mailbox_id      INTEGER NOT NULL,
   exec_time       TIMESTAMP,
   interval_millis INTEGER,
   metadata        CLOB,

   CONSTRAINT pk_scheduled_task PRIMARY KEY (name, mailbox_id, class_name),
   CONSTRAINT fk_st_mailbox_id FOREIGN KEY (mailbox_id)
      REFERENCES mailbox(id) ON DELETE CASCADE
);
0 rows inserted/updated/deleted
ij> CREATE INDEX i_scheduled_task_mailbox_id ON scheduled_task(mailbox_id);
0 rows inserted/updated/deleted
WARNING 01504: The new index is a duplicate of an existing index: SQL100504183559361.
ij> RUN '/home/user/zdesktop/db/directory.sql';
ij> --
-- ***** BEGIN LICENSE BLOCK *****
--
-- Zimbra Collaboration Suite Server
-- Copyright (C) 2007 Zimbra, Inc.
--
-- The contents of this file are subject to the Yahoo! Public License
-- Version 1.0 ("License"); you may not use this file except in
-- compliance with the License.  You may obtain a copy of the License at
-- [http://www.zimbra.com/license](http://www.zimbra.com/license).
--
-- Software distributed under the License is distributed on an "AS IS"
-- basis, WITHOUT WARRANTY OF ANY KIND, either express or implied.
--
-- ***** END LICENSE BLOCK *****
--


-- -----------------------------------------------------------------------
-- directory
-- -----------------------------------------------------------------------

CREATE TABLE directory (
   entry_id    INTEGER NOT NULL GENERATED BY DEFAULT AS IDENTITY,
   entry_type  CHAR(4) NOT NULL,
   entry_name  VARCHAR(128) NOT NULL,
   zimbra_id   CHAR(36),
   modified    SMALLINT NOT NULL,

   CONSTRAINT pk_directory PRIMARY KEY (entry_id),
   CONSTRAINT ui_directory_entry_type_name UNIQUE(entry_type, entry_name)
);
0 rows inserted/updated/deleted
ij> CREATE UNIQUE INDEX ui_directory_zimbra_id ON directory(zimbra_id);
0 rows inserted/updated/deleted
ij> CREATE TABLE directory_attrs (
   entry_id    INTEGER NOT NULL,
   name        VARCHAR(255) NOT NULL,
   value       VARCHAR(32672) NOT NULL,

   CONSTRAINT fk_dattr_entry_id FOREIGN KEY (entry_id) REFERENCES directory(entry_id)
      ON DELETE CASCADE
);
0 rows inserted/updated/deleted
ij> CREATE INDEX i_dattr_entry_id_name ON directory_attrs(entry_id, name);
0 rows inserted/updated/deleted
ij> CREATE INDEX i_dattr_name ON directory_attrs(name);
0 rows inserted/updated/deleted
ij> CREATE TABLE directory_leaf (
   entry_id    INTEGER NOT NULL GENERATED BY DEFAULT AS IDENTITY,
   parent_id   INTEGER NOT NULL,
   entry_type  CHAR(4) NOT NULL,
   entry_name  VARCHAR(128) NOT NULL,
   zimbra_id   CHAR(36) NOT NULL,

   CONSTRAINT pk_dleaf PRIMARY KEY (entry_id),
   CONSTRAINT ui_dleaf_zimbra_id UNIQUE (zimbra_id),
   CONSTRAINT ui_dleaf_parent_entry_type_name UNIQUE (parent_id, entry_type, entry_name),
   CONSTRAINT fk_dleaf_entry_id FOREIGN KEY (parent_id) REFERENCES directory(entry_id)
      ON DELETE CASCADE
);
0 rows inserted/updated/deleted
ij> CREATE TABLE directory_leaf_attrs (
   entry_id    INTEGER NOT NULL,
   name        VARCHAR(255) NOT NULL,
   value       VARCHAR(32672) NOT NULL,

   CONSTRAINT fk_dleafattr_entry_id FOREIGN KEY (entry_id) REFERENCES directory_leaf(entry_id)
      ON DELETE CASCADE
);
0 rows inserted/updated/deleted
ij> CREATE INDEX i_dleafattr_entry_id_name ON directory_leaf_attrs(entry_id, name);
0 rows inserted/updated/deleted
ij> CREATE INDEX i_dleafattr_name ON directory_leaf_attrs(name);
0 rows inserted/updated/deleted
ij> CREATE TABLE directory_granter (
   granter_name  VARCHAR(128) NOT NULL,
   granter_id    CHAR(36) NOT NULL,
   grantee_id    CHAR(36) NOT NULL,

   CONSTRAINT pk_dgranter PRIMARY KEY (granter_name, grantee_id)
);
0 rows inserted/updated/deleted
ij> CREATE INDEX i_dgranter_gter_name ON directory_granter(granter_name);
0 rows inserted/updated/deleted
ij> CREATE INDEX i_dgranter_gter_id ON directory_granter(granter_id);
0 rows inserted/updated/deleted
ij> CREATE INDEX i_dgranter_gtee_id ON directory_granter(grantee_id);
0 rows inserted/updated/deleted
ij> RUN '/home/user/zdesktop/db/versions-init.sql';
ij> -- AUTO-GENERATED .SQL FILE - Generated by the Derby versions tool
INSERT INTO zimbra.config(name, value, description) VALUES
	('db.version', '53', 'db schema version'),
	('index.version', '2', 'index version'),
	('redolog.version', '1.24', 'redolog version'),
	('offline.db.version', '3', 'offline db schema version');
4 rows inserted/updated/deleted
ij> INSERT INTO volume (id, type, name, path, file_bits, file_group_bits,
			    mailbox_bits, mailbox_group_bits, compress_blobs, compression_threshold)
			  VALUES (1, 1, 'message1', '/home/user/zdesktop/store', 12, 8, 12, 8, 0, 4096);
1 row inserted/updated/deleted
ij> INSERT INTO volume (id, type, name, path, file_bits, file_group_bits,
			    mailbox_bits, mailbox_group_bits, compress_blobs, compression_threshold)
			  VALUES (2, 10, 'index1', '/home/user/zdesktop/index', 12, 8, 12, 8, 0, 4096);
1 row inserted/updated/deleted
ij> INSERT INTO current_volumes (message_volume_id, index_volume_id, next_mailbox_id) VALUES (1, 2, 1);
1 row inserted/updated/deleted
ij> EXIT;
user@pc:~/Downloads$

---

### Post by 3L33T on 2010-06-11
Install zimbra using "sh ./<zimbra install file.sh>"

Do not install as root.  Zimbra will install in the $HOME directory.

---

### Post by badaveil on 2010-06-12
> **3L33T said:**
> Install zimbra using "sh ./<zimbra install file.sh>"

Do not install as root.  Zimbra will install in the $HOME directory.

You are right, do not install as root!;)

---

### Post by doublewitt on 2010-07-11
I just downloaded and installed it - very nice software!

---

### Post by doublewitt on 2010-07-11
I have taken a good look at this APP and it's neat - overall... but I think I will stay with my Kmail - it's so good... and lots more customizable. Nonetheless, Zimbra is definately worth considering...

---

### Post by shtywi on 2010-08-10
thanks all for good information ...finally :D

---

### Post by badaveil on 2010-08-10
> **shtywi said:**
> thanks all for good information ...finally :D

It's still in beta mode so we have to be patient and wait until the chat function is operational;)

---

### Post by WillemHart on 2010-09-13
Badaveil,  you say....

*Yes, I got it this time! Thanks to you telling me to re-do it again but  less "sudo".I placed the files under /home/user/zdesktop because it  rejected the default path into /root. A proper Zimbra desktop icon  didn't appear as you can see but now I know the command by looking up  the icon properties. I've already created a Zimbra Desktop launcher in  the Main Menu and for some strange reason that earlier desktop icon  didn't work though the command I took to create the launcher does *:grin:.

.... What do you mean by "[SIZE=2] now I know the command[/SIZE]"??  How do you use it (command) to execute Zimbra?  

And how did you create a [SIZE=2]Desktop Launcher in the main menu[/SIZE]?  I am new to this (Linux/Ubuntu)... pse guide me through your solution.

---

### Post by badaveil on 2010-09-15
> **WillemHart said:**
> Badaveil,  you say....

*Yes, I got it this time! Thanks to you telling me to re-do it again but  less "sudo".I placed the files under /home/user/zdesktop because it  rejected the default path into /root. A proper Zimbra desktop icon  didn't appear as you can see but now I know the command by looking up  the icon properties. I've already created a Zimbra Desktop launcher in  the Main Menu and for some strange reason that earlier desktop icon  didn't work though the command I took to create the launcher does *:grin:.

.... What do you mean by "[SIZE=2] now I know the command[/SIZE]"??  How do you use it (command) to execute Zimbra?  

And how did you create a [SIZE=2]Desktop Launcher in the main menu[/SIZE]?  I am new to this (Linux/Ubuntu)... pse guide me through your solution.

An icon was created on the desktop by Zimbra.I right click that icon and copied its properties which is 

"/home/user/zdesktop/linux/prism/zdclient" -webapp "/home/user/zdesktop/zdesktop.webapp" -override "/home/user/zdesktop/zdesktop.webapp/override.ini" -profile "/home/user/zdesktop/profile"

Then I right clicked the main menu icon/edit menu/ made a new item under main menu called "others" followed by a sub-item under others called "zimbra desktop" in "Name" and pasted the above command under "Command" where Type is "Application".

Close it then test it. It works fine with me.

---

### Post by FrancoNero on 2010-11-20
one wonders why on earth they don't offer a .deb or a ppa for this...  all these installation scripts etc are so 1980s

---

### Post by badaveil on 2010-11-20
> **FrancoNero said:**
> one wonders why on earth they don't offer a .deb or a ppa for this...  all these installation scripts etc are so 1980s

Simple, this developer has not adapted to the time and tune to the needs of the general user who are not keyboard entry people

---

### Post by P4man on 2010-11-20
> **FrancoNero said:**
> one wonders why on earth they don't offer a .deb or a ppa for this...  all these installation scripts etc are so 1980s

Because its a java app. The idea of java is write once, run anywhere. Packaging your app for every conceivable OS, distribution, version and 32/64 bit variants kinda defeats that purpose.

---

### Post by FrancoNero on 2010-11-21
but the .deb installation process could just simply take care of all that terminal nonsense you need to do to get this installed. I constantly hear all these excuses, what about the other gazillion applications you can comfortably install via the "for human beings" way....

---

### Post by P4man on 2010-11-21
> **FrancoNero said:**
> what about the other gazillion applications you can comfortably install via the "for human beings" way....

Well those apps wont run on red hat, or suse, or windows, or OS-X or android or chromeOS or or or. If someone wants to package it for those OS's, than great. If no is volunteering and the devs too busy writing the app that they dont want to support a gazillion platforms, binaries and installers, be happy you can run the app on any OS you want. 

If anything this is the OS's fault for not making it easier to "install" and run a java app.

---

### Post by 3L33T on 2010-12-09
> **FrancoNero said:**
> one wonders why on earth they don't offer a .deb or a ppa for this...  all these installation scripts etc are so 1980s

Whats wrong with that? WE HAVE 1980's era ksh scripts on unix machines that are bulletproof and ARE STILL running.

---

### Post by evets on 2011-09-21
> **doublewitt said:**
> I have taken a good look at this APP and it's neat - overall... but I think I will stay with my Kmail - it's so good... and lots more customizable. Nonetheless, Zimbra is definately worth considering...

Does Kmail receive Yahoo (free)? That's the only reason I use Zimbra.

---

