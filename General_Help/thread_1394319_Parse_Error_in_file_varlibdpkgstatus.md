---
title: "Parse Error in file var/lib/dpkg/status"
date: 2010-01-30
forum: General Help
---

### Post by jonny_bowes on 2010-01-30
When I tried to update i got this error.

Parse Error in file var/lib.dpkg/status near line 36571 package 'language-pack-gnome-en'

I have performed some trouble shooting with the people on #ubuntu-ie to no avail.

We followed the trouble shooting from [http://ubuntuforums.org/archive/index.php/t-474587.html](http://ubuntuforums.org/archive/index.php/t-474587.html)

and tried to re-do the script from [http://linuxmafia.com/faq/Debian/package-database-rebuild.html](http://linuxmafia.com/faq/Debian/package-database-rebuild.html)

but running that script gives

# Test existence of any subdirs in /var. If they exist, exit, otherwise
# risk destroying an active system. If they don't exist, the remainder
# of this script is safe.

function create_new_dir () {
./New_Status: 31: Syntax error: "(" unexpected

This is the line with the error : $1 exists, aborting" 1>&2

Can someone help me out on this as my next step will be a re-install I think?

Thanks in advance:)

---

### Post by jonny_bowes on 2010-01-30
> **jonny_bowes said:**
> When I tried to update i got this error.

Parse Error in file var/lib.dpkg/status near line 36571 package 'language-pack-gnome-en'

I have performed some trouble shooting with the people on #ubuntu-ie to no avail.

We followed the trouble shooting from [http://ubuntuforums.org/archive/index.php/t-474587.html](http://ubuntuforums.org/archive/index.php/t-474587.html)

and tried to re-do the script from [http://linuxmafia.com/faq/Debian/package-database-rebuild.html](http://linuxmafia.com/faq/Debian/package-database-rebuild.html)

but running that script gives

# Test existence of any subdirs in /var. If they exist, exit, otherwise
# risk destroying an active system. If they don't exist, the remainder
# of this script is safe.

function create_new_dir () {
./New_Status: 31: Syntax error: "(" unexpected

This is the line with the error : $1 exists, aborting" 1>&2

Can someone help me out on this as my next step will be a re-install I think?

Thanks in advance:)

Bump;)

---

### Post by paul_in_london on 2010-01-30
Try this:

```
sudo cp /var/lib/dpkg/status-old /var/lib/dpkg/status
sudo aptitude update
sudo aptitude safe-upgrade

```

---

### Post by jonny_bowes on 2010-01-30
> **paul_in_london said:**
> Try this:

```
sudo cp /var/lib/dpkg/status-old /var/lib/dpkg/status
sudo aptitude update
sudo aptitude safe-upgrade

```

Just tried it but no change

dpkg: parse error, in file '/var/lib/dpkg/status' near line 36571 package 'language-pack-gnome-en':
 newline in field name `
E: Sub-process /usr/bin/dpkg returned an error code (2)
A package failed to install.  Trying to recover:
dpkg: parse error, in file '/var/lib/dpkg/status' near line 36571 package 'language-pack-gnome-en'

 :frown: I think maybe both status files are corrupt.

---

### Post by paul_in_london on 2010-01-30
Instead of **/var/lib/dpkg/status-old** try **/var/backups/dpkg.status.0**

It'll just mean reapplying a few more updates. Btw, you can do full-upgrade instead of safe-upgrade.

---

### Post by jonny_bowes on 2010-01-31
> **paul_in_london said:**
> Instead of **/var/lib/dpkg/status-old** try **/var/backups/dpkg.status.0**

It'll just mean reapplying a few more updates. Btw, you can do full-upgrade instead of safe-upgrade.

Hi Paul,I tried what you said and then did apt-get update and full-upgrade etc but got this at the end of the process.

dpkg: parse error, in file '/var/lib/dpkg/status' near line 36571 package 'language-pack-gnome-en':
 newline in field name `
E: Sub-process /usr/bin/dpkg returned an error code (2)
A package failed to install.  Trying to recover:
dpkg: parse error, in file '/var/lib/dpkg/status' near line 36571 package 'language-pack-gnome-en':
 newline in field name `

---

### Post by paul_in_london on 2010-01-31
Hi Jonny,

How long ago did this happen? In /var/backups there are other backups of the status file (dpkg.status.1.gz, dpkg.status.2.gz etc). Try unzipping one or more of those and replacing your corrupted status file with an even older one.

This is the corresponding part of my status file to give you an idea how it should look:

```
Package: language-pack-gnome-en
Status: install ok installed
Priority: optional
Section: translations
Installed-Size: 36
Maintainer: Language pack maintainers <language-packs@ubuntu.com>
Architecture: all
Version: 1:10.04+20100109
Replaces: language-pack-en (<< 1:10.04+20100109), language-pack-en-base (<< 1:10.04+20100109), language-pack-gnome-en (<< 1:10.04+20100109), language-pack-gnome-en-base, language-pack-kde-en (<< 1:10.04+20100109), language-pack-kde-en-base (<< 1:10.04+20100109)
Depends: language-pack-gnome-en-base (>= 1:10.04+20100109), language-pack-en-base (>= 1:10.04+20100109)
Pre-Depends: dpkg (>= 1.10.27ubuntu1)
Description: GNOME translation updates for language English
 Translation data updates for all supported GNOME packages for:
 English
 .
 language-pack-gnome-en-base provides the bulk of translation data
 and is updated only seldom. This package provides frequent translation
 updates.
 .
 Please note that you should install language-support-en
 to get full support for this language.

Package: wireless-tools
```

If you compare it with your entry for this package you might be able to fix your status file with some manual edits. I'm using Lucid so not every detail will be the same.

Before you update again with a different status file, I would also suggest that you boot into recovery mode, select netroot from the menu and run your commands from there.

HTH

---

### Post by jonny_bowes on 2010-01-31
I looked in the back-ups and there are 5 or 6 of those back ups dating back to 17/01/2010. This issue started 3 or 4 days ago so I will pick one a few days before that again to be sure.

Thanks and I'll report back with my findings:-k

---

### Post by jonny_bowes on 2010-01-31
Paul you are a legend!!

It all looks fine and update/upgrade ok.


Should I remove the corrupt ones now?

---

### Post by paul_in_london on 2010-01-31
Glad it worked. If you've updated and upgraded ok then /var/lib/dpkg/status-old and /var/lib/dpkg/status will have sorted themselves out. You could now do something like:

```
sudo cp /var/lib/dpkg/status /var/lib/dpkg/status.ok.31012010
```

so that you'll have another one to fall back on and then just delete any corrupt backups you may have found in /var/backups

---

### Post by jonny_bowes on 2010-01-31
> **paul_in_london said:**
> Glad it worked. If you've updated and upgraded ok then /var/lib/dpkg/status-old and /var/lib/dpkg/status will have sorted themselves out. You could now do something like:

```
sudo cp /var/lib/dpkg/status /var/lib/dpkg/status.ok.31012010
```

so that you'll have another one to fall back on and then just delete any corrupt backups you may have found in /var/backups

Thanks Paul,
I shall gladly mark this as solved!!

Big up to the community!!:D

---

### Post by Paul Coleman on 2010-07-14
I am running Ubuntu 10.4 amd64 and had this same issue. The suggestion to use one of the /var/backups/*.gz files worked perfectly. It was also much easier than running some of the suggested perl/bash scripts mentioned in another thread. My system is back up and updated. Thanks for the information.

---

### Post by mlb on 2012-08-19
It helped me with Ubuntu 12.04, too :D

Thanks!

---

