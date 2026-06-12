---
title: "ubuntu repo"
date: 2009-08-08
forum: General Help
---

### Post by ankscorek on 2009-08-08
helo  i am using ubuntu repo through tor network

the downloading is very slow through tor

i tried everything available with apt-get to shut down my tor and connect to tor

however i m unable to do so

i am using ubuntu jaunty

can some1 please guide me a method to undo what i had done...conect directly to ubuntu repo

---

### Post by Sidewinder1 on 2009-08-08
Have you tried going into Synaptic Package Mgr. and marking tor for total removal?

---

### Post by ankscorek on 2009-08-08
you mean to say i purge tor and nvidilia and then rebuild the repo

incase this doesnot work then i am disconnected from the repos

incase it fails then what is a work around

tor=="the onion router"

---

### Post by wojox on 2009-08-08
You can go to System > Admin > Software Sources 
The first Tab: Ubuntu Software.
Look for Download from:
Find a server closer to you.
As far as tor I know nothing about but try to disconnect from it.

---

### Post by harry2006 on 2009-08-08
selecting the closest repo server should fix the issue.

---

### Post by ankscorek on 2009-08-09
nopes still not helping it is still ignoring few repositories

i switched off tor and tried a local server it did not help

---

### Post by 3rdalbum on 2009-08-09
DO NOT download files through Tor, this is a misuse of other people's internet connections. And it's slower.

---

### Post by ankscorek on 2009-08-09
that is xactly what i want to do

but how

i have cleared all my sources.list file and i have removed all the keys

so please help m ein building these files from start

 first box i checked in my softaware sources and when i reloaded this error i got

Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/jaunty/main/binary-amd64/Packages](http://archive.ubuntu.com/ubuntu/dists/jaunty/main/binary-amd64/Packages)  503 Forwarding failure
Some index files failed to download, they have been ignored, or old ones used instead.

#############################################################
################### OFFICIAL UBUNTU REPOS ###################
#############################################################

###### Ubuntu Main Repos
deb [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) jaunty main restricted universe multiverse 
deb-src [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) jaunty main restricted universe multiverse 

###### Ubuntu Update Repos
deb [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) jaunty-security main restricted universe multiverse 
deb [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) jaunty-updates main restricted universe multiverse 
deb [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) jaunty-proposed main restricted universe multiverse 
deb [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) jaunty-backports main restricted universe multiverse 
deb-src [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) jaunty-security main restricted universe multiverse 
deb-src [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) jaunty-updates main restricted universe multiverse 
deb-src [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) jaunty-proposed main restricted universe multiverse 
deb-src [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) jaunty-backports main restricted universe multiverse 

###### Ubuntu Partner Repo
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner


these are official ubuntu sites and i am getting forwarding failure when i do apt-get update..i think key problem..please help me out

here is the error i get when i try an apt-get update
W: Failed to fetch [http://archive.canonical.com/ubuntu/dists/hardy/partner/i18n/Translation-en_IN.bz2](http://archive.canonical.com/ubuntu/dists/hardy/partner/i18n/Translation-en_IN.bz2)  Could not connect to localhost:8118 (127.0.0.1). - connect (111 Connection refused)

so this indicates network proxy ..i disabled it and enabled direct internet connections in the preferences still the same


anyways tahnx for the response the problem got solved by uninstalling tor and privoxy and again updating the repo

---

