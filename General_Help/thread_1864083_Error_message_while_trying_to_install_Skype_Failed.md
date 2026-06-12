---
title: "Error message while trying to install Skype Failed to download package files"
date: 2011-10-18
forum: General Help
---

### Post by Peterfc on 2011-10-18
I have been trying to install Skype before i posted for help i have spent days reading the results of the search i made sadly nothing seems to be of help. 

One reply mentions about the Synaptic package manager while trying to install the Synaptic package manager i get an error message Saying Failed to download packages files Check your Internet connection. I have spent hours today doing a search. I am online while i type this so the connection is ok.

Thansk for reading my post

---

### Post by Lantius on 2011-11-23
> **Peterfc said:**
> I have been trying to install Skype before i posted for help i have spent days reading the results of the search i made sadly nothing seems to be of help. 

One reply mentions about the Synaptic package manager while trying to install the Synaptic package manager i get an error message Saying Failed to download packages files Check your Internet connection. I have spent hours today doing a search. I am online while i type this so the connection is ok.

Thansk for reading my post
Run the following commands (saves a backup of the old lists and creates a new lists folder) and the BADSIG error does not occur:

cd /var/lib/apt
sudo mv lists lists.old
sudo mkdir -p lists/partial
sudo apt-get update

and if you have any troubles with no_pubkey after, check this out: 

[http://www.stefanoforenza.com/solve-your-no_pubkey-ppas-in-a-snap-or-a-script/](http://www.stefanoforenza.com/solve-your-no_pubkey-ppas-in-a-snap-or-a-script/) 

there is a script which solved it in my case. 

source:

[http://askubuntu.com/questions/70553/software-center-not-downloading](http://askubuntu.com/questions/70553/software-center-not-downloading)



greetings

---

### Post by Gatemaze on 2011-11-23
Just my two cents... If you download the archive with the statically linked libs from the skype webpage maybe it will be OK.

---

