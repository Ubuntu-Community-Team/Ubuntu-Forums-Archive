---
title: "Reset Software Sources"
date: 2011-08-28
forum: General Help
---

### Post by Bucic on 2011-08-28
I shamelessly started a new topic because I spent half an hour searching for a solution here and no existing topic provided one. 

Long story short restoring a "clean" sources.list file does not work. **What is the method for a real software sources reset? Sources, settings, keys, downloaded packages - everything.** And as an "ultimate way to reset updates" probably never did for anyone. I used this [http://repogen.simplylinux.ch/index.php](http://repogen.simplylinux.ch/index.php) To make sure the sources.list has really been altered I issued
```
sudo gedit /etc/apt/sources.list

```
Which gave me 
```
#############################################################
################### OFFICIAL UBUNTU REPOS ###################
#############################################################

###### Ubuntu Main Repos
deb http://pl.archive.ubuntu.com/ubuntu/ natty main restricted 

###### Ubuntu Update Repos
deb http://pl.archive.ubuntu.com/ubuntu/ natty-security main restricted 
deb http://pl.archive.ubuntu.com/ubuntu/ natty-updates main restricted 

###### Ubuntu Partner Repo
deb http://archive.canonical.com/ubuntu natty partner
```

I also issued 
```
sudo rm /var/lib/apt/lists/* -vf


```

**and yet I get all kind of trash in the GUI for the Software Sources, some sources that are definitely not in the sources.list anymore.**


The updater easily turning into a mess (just do a search for "failed to fetch") tells me I should go for resetting everything to the state closest to the state of a clean install. I'll appreciate any assistance to get me there.

---

### Post by haqking on 2011-08-28
i dont understand your question.

However when using gedit as it is graphical you should use:

gksudo

not sudo.

also you can modify your sources from the the GUI by removing the ticks from unwanted sources

---

### Post by Bucic on 2011-08-28
OP edit: What is the method for a real software sources reset?

gksudo:
It didn't matter in my case.
```
sudo gedit /etc/apt/sources.list
```
confirms the same content I pasted above. Below is an example of set of errors I get with the new sources.list
```
W:GPG error: http://archive.ubuntu.com natty Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>, W:GPG error: http://archive.ubuntu.com natty-updates Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>, W:Failed to fetch copy:/var/lib/apt/lists/partial/ppa.launchpad.net_cafuego_inkscape_ubuntu_dists_natty_main_binary-amd64_Packages  Hash Sum mismatch
, E:Some index files failed to download. They have been ignored, or old ones used instead.
```

---

### Post by haqking on 2011-08-28
> **Bucic said:**
> OP edit: What is the method for a real software sources reset?

gksudo:
It didn't matter in my case.
```
sudo gedit /etc/apt/sources.list
```confirms the same content I pasted above.

it does matter, i know it shows the same content.

The point is to prevent potential issues you should always run graphical apps with gksudo and not sudo.

as for a reset ?

just comment out what you dont want.

sources change all the time when you add ppa etc.

Anything you dont want then place a # at the beginning of the line.

When you have it how you want it based on your software install then back it up

---

### Post by Bucic on 2011-08-28
I get errors regarding sources that are not in the sources.list, in any form. I can't imagine a simpler way to describe the problem.

---

### Post by snowpine on 2011-08-28
/etc/apt/sources.list is the main file, but you also need to look in the /etc/apt/sources.list.d/ folder. Sometimes there are additional software sources in that folder.

Also be sure to do a "sudo apt-get update" after making the changes.

---

### Post by haqking on 2011-08-28
> **Bucic said:**
> I get errors regarding sources that are not in the sources.list, in any form. I can't imagine a simpler way to describe the problem.


it doesnt look like a source issue but a key issue.

however you can use update manager to modify your ppa from other software tab on settings or update your key for that ppa.

---

### Post by Bucic on 2011-08-29
Yes, there are two problems:
1. Reseting source.list not actually resetting software sources.
2. Authentication keys problems. (inadvertently came up in this topic)

Ad.1.
I think snowpine nailed it in #6. Now what I'd need to mark the topic as solved is a method to empty downloaded packages cache and other software sources related elements, if applicable. (are there any?)

Ad.2.
The problem most probably comes from users not issuing **sudo apt-get update** after adding a new software source / repository / ppa. The command is needed for the system to fetch authentication keys of the newly added sources. Please correct me if I'm wrong.


One more thing. Can someone clarify what is the role of 
```
sudo rm /var/lib/apt/lists/* -vf
```
in software sources related troubleshooting?

---

### Post by haqking on 2011-08-29
> **Bucic said:**
> Yes, there are two problems:
1. Reseting source.list not actually resetting software sources.
2. Authentication keys problems. (inadvertently came up in this topic)

Ad.1.
I think snowpine nailed it in #6. Now what I'd need to mark the topic as solved is a method to empty downloaded packages cache and other software sources related elements, if applicable. (are there any?)

Ad.2.
The problem most probably comes from users not issuing **sudo apt-get update** after adding a new software source / repository / ppa. The command is needed for the system to fetch authentication keys of the newly added sources. Please correct me if I'm wrong.


One more thing. Can someone clarify what is the role of 
```
sudo rm /var/lib/apt/lists/* -vf
```in software sources related troubleshooting?

you are removing everytyhing in the lists directory.

the switch -v means verbose (explain what its doing as its doing it) and -f forces the removal

after this command you should do a

sudo apt-get update

---

### Post by Bucic on 2011-08-29
> **haqking said:**
> you are removing everytyhing in the lists directory.

the switch -v means verbose (explain what its doing as its doing it) and -f forces the removal

after this command you should do a

sudo apt-get update
What it does per se I knew but what is that directory role/contents compared to the */etc/apt/*.

---

### Post by haqking on 2011-08-29
> **Bucic said:**
> What it does per se I knew but what is that directory role/contents compared to the */etc/apt/*.

it deletes the old entries for packages/lists etc

etc/apt is where the sources.list file is kept as there other other package sources than that entered into the sources.list such as various ppa etc

---

### Post by Bucic on 2011-08-29
OK.

So to really reset software sources stuff one needs to "do":
[LIST=1]
[*]/etc/apt/sources.list
[*]/var/lib/apt/lists/*
[*]/etc/apt/sources.list.d/ <?>
[/LIST]

---

### Post by haqking on 2011-08-29
> **Bucic said:**
> OK.

So to really reset software sources stuff one needs to "do":
[LIST=1]
[*]/etc/apt/sources.list
[*]/var/lib/apt/lists/*
[*]/etc/apt/sources.list.d/ <?>
[/LIST]


I just back mine up on a clean install as well as image my system ;-)

if i make any changes or things become corrupt i replace it with the original.

---

### Post by Bucic on 2011-08-30
By referring to this page I guess one could set the GUI settings back to default [https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu)


Later I'll browse through http://[SIZE="3"]**askubuntu.com**[/SIZE]/search?q=+software+sources+default

---

### Post by haqking on 2011-08-30
> **Bucic said:**
> By referring to this page I guess one could set the GUI settings back to default [https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu)


Later I'll browse through [http://[SIZE=3]](http://[SIZE=3])**askubuntu.com**[/SIZE]/search?q=+software+sources+default

The default will vary based on your version

---

### Post by Bucic on 2011-08-30
> **haqking said:**
> The default will vary based on your version
There's not much aspects that can differ, are they? :) What I mean is I don't recall any since 10.10.

---

