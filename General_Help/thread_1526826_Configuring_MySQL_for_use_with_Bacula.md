---
title: "Configuring MySQL for use with Bacula"
date: 2010-07-08
forum: General Help
---

### Post by johnyd on 2010-07-08
I'm the Network Administrator for a medium sized business (AD network) and I'm trying to integrate more and more Linux solutions as I would be crazy not to take advantage of the versatility and usefulness of Linux, and more especially, Ubuntu.

Currently I'm trying to replace my legacy Backup Exec 11D with Bacula. My setup is as follows:

Ubuntu 10.04 Desktop
Bacula 5.0.1
MySQL 5.1.41

During the install of Bacula (through SPM) I am prompted to create (or authenticate?) multiple MySQL accounts for Bacula. At first I thought they were prompts to create the accounts. Now I'm thinking that I need to create those accounts ahead of time. If I just enter passwords for the accounts, without having done any MySQL configuration prior to this whatsoever, the configuration fails. 

I looked at the Bacula main reference and then attempted to configure MySQL prior to Bacula installation. I ran the command: 

sudo /usr/sbin/mysqld

to start the MySQL daemon. It took quite some time for the command to finish and no output was given... I can only assume it completed. The next step I performed was to set up the default database through the command:

sudo mysql_install_db

This command completed successfully. However, when I tried to set the root password with the command:

sudo mysqladmin -u root password 'mypassword'

I receive the error: *Access denied for user 'root'@'localhost' (using password: NO)*

I'm baffeled as to what to do next. Does anyone have experience with setting up Bacula on Lucid? I would really appreciate any help. If there is any further information that I can provide please do not hesitate to ask.

Thank you very much,

John

---

### Post by gordintoronto on 2010-07-08
When you install mysql, you set up the root password, if memory serves.

---

### Post by johnyd on 2010-07-09
So is it better to install MySQL both separately and before installing Bacula?

And what commands would I issue to prepare MySQL for use by Bacula? Initialize tables? Build first DB? Create root account / assign password? Start daemon? I have some experience with Linux but very little with MySQL. Thank you.

---

### Post by gordintoronto on 2010-07-09
Just give it a root password during installation.

---

