---
title: "how does apt-get determine something is up to date?"
date: 2010-12-31
forum: General Help
---

### Post by ixxalnxxi on 2010-12-31
root@tipu_ubuntu:/var/cache/apt/archives# apt-get -y install ruby1.8-dev ruby1.8 ri1.8 rdoc1.8 irb1.8 libreadline-ruby1.8 libruby1.8 libopenssl-ruby
Reading package lists... Done
Building dependency tree
Reading state information... Done
ruby1.8-dev is already the newest version.
ruby1.8 is already the newest version.
ri1.8 is already the newest version.
rdoc1.8 is already the newest version.
irb1.8 is already the newest version.
libreadline-ruby1.8 is already the newest version.
libruby1.8 is already the newest version.
libopenssl-ruby is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 64 not upgraded.

However, what I did was i did

"whereis ruby.8", as well as "whereis ruby"

and i rm everything that came up, (what i thought i was doing was uninstalling it). now that it's done, i would like to reinstall it. so i'm curious about what it is that apt-get looks at to determine that those files are there and up to date.

---

### Post by germanix on 2010-12-31
The packaging system uses a private database to keep track of which packages are installed, which are not installed and which are available for installation. The apt-get program uses this database to find out how to Apt-get install packages requested by the user and to find out which additional packages are needed in order for a selected package to work properly.

To update this list, you would use the command apt-get update. This command looks for the package lists in the archives found in /etc/apt/sources.list; see The /etc/apt/sources.list file.

It's a good idea to run this command regularly to keep yourself and your system informed about possible package updates, particularly security updates.

---

### Post by NFN_NLN on 2010-12-31
Just do "apt-get remove ..." to remove the package and try installing again.

/var/lib/apt/lists/
      storage area for state information  for  each  package  resource
      specified     in	   sources.list(5)     Configuration	 Item:
      Dir::State::Lists.

---

