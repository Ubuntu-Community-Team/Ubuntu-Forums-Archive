---
title: "Cannot gain access to terminal"
date: 2011-04-07
forum: General Help
---

### Post by Wuxin on 2011-04-07
[FONT=Times New Roman][SIZE=3]I've recently created a new user's account in Ubuntu because of some difficulties I was having with network communications.  Apparently this has affected my ability to get into a terminal because now, when I submit my user name I get the following:

 [OPTIONS] [PASSWORD-FILES]
--single                   "single crack" mode
--wordlist=FILE --stdin    wordlist mode, read words from FILE or stdin
--rules                    enable word mangling rules for wordlist mode
--incremental[=MODE]       "incremental" mode [using section MODE]
--external=MODE            external mode or word filter
--stdout[=LENGTH]          just output candidate passwords [cut at LENGTH]
--restore[=NAME]           restore an interrupted session [called NAME]
--session=NAME             give a new session the NAME
--status[=NAME]            print status of a session [called NAME]
--make-charset=FILE        make a charset, FILE will be overwritten
--show                     show cracked passwords
--test                     perform a benchmark
--users=[-]LOGIN|UID[,..]  [do not] load this (these) user(s) only
--groups=[-]GID[,..]       load users [not] of this (these) group(s) only
--shells=[-]SHELL[,..]     load users with[out] this (these) shell(s) only
--salts=[-]COUNT           load salts with[out] at least COUNT passwords only
--format=NAME              force hash type NAME: DES/BSDI/MD5/BF/AFS/LM/NT/mscash/NETLM/NETNTLM/bfegg/DOMINOSEC/lotus5/raw-MD5/raw-sha1/IPB2/nsldap/openssha/HDAA
--save-memory=LEVEL        enable memory saving, at LEVEL 1..3 

I've always been able to just install my name and password and things worked
smoothly.  What is this about and what do I need to do to restore my ability to 
use a terminal?  Thank you kindly in advance.

[/SIZE][/FONT]

---

### Post by techunit on 2011-04-07
how were you adding the preplacement account? if you didn't set the permissions correctly you may need to reboot into the restore console and add those permissions to the account.

---

### Post by WorMzy on 2011-04-07
Is your username "john"?

Have you installed the john package?

Why are you entering your username at the terminal prompt anyway?

---

