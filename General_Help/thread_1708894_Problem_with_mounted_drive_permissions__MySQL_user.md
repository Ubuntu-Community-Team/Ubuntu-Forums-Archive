---
title: "Problem with mounted drive permissions / MySQL user"
date: 2011-03-17
forum: General Help
---

### Post by trift on 2011-03-17
**Problem Overview:**
MySQL cannot access the drive that contains the database files, or MySQL cannot create the socket file in [FONT=Courier New]/var/run/mysqld[/FONT].

**System:**
Dell laptop, dual booting Ubuntu 10.10 and Win Vista.

**The Problem:**
I was using Windows for developing websites and now I wish to develop the same sites when I am booted into Ubuntu. The database files area located on the Vista partition but MySQL cannot access them because the drive gets mounted owned by the user account I am logged in as. If I try to change the user that mysqld runs as (via [FONT=Courier New]my.conf[/FONT]) I get permission errors when it tries to create the socket file in [FONT=Courier New]/var/run/mysqld[/FONT] because that dir is owned by user [FONT=Courier New]mysql[/FONT]. If I change the ownership to the regular user account then the ownership gets changed back to user [FONT=Courier New]mysql[/FONT] whenever I run [FONT=Courier New]service mysql start[/FONT]. If I change the permissions of [FONT=Courier New]/var/run/mysqld[/FONT] and then manually run the [FONT=Courier New]mysqld[/FONT] command then it functions normally.

**What I would like (in order of preference):**
1) Set it so that when I mount the Vista partition using the "Places" menu the permissions are sufficient that the [FONT=Courier New]mysql[/FONT] user account can access the drive.
2) Change mysqld to run under a different user account.

---

### Post by trift on 2011-06-17
Bump.

---

### Post by trift on 2011-07-19
Bump

---

