---
title: "question about non functional ubuntu 11.04 software center"
date: 2011-10-01
forum: General Help
---

### Post by noone1976 on 2011-10-01
Ubuntu software center does not load and when i write

sudo apt-get update && sudo apt-get apgrade

loads a bunch of stuff and says ....

                                 SystemError: E:Encountered a section with no Package: header, E:Problem with MergeList /var/lib/apt/lists/extras.ubuntu.com_ubuntu_dists_natty_main_binary-i386_Packages, E:The package lists or status file could not be parsed or opened.


what does this mean ??
Thnx everyone.. 

I know it probably is stupid but I just started using linux / ubuntu yesterday..):P

---

### Post by nitstorm on 2011-10-01
Try this on your terminal

```
sudo rm /var/lib/apt/lists/* -vf
sudo apt-get update
sudo apt-get upgrade
```

The above code will remove the entries of the listings and then update a fresh set of lists and then perform the updates.

Source: [ihaveapc.com]("http://www.ihaveapc.com/2011/05/how-to-fix-problem-with-mergelist-varlibaptlists-error-in-ubuntu-11-04/")

---

### Post by Catherine Waymouth on 2011-10-02
[FONT=monospace]Hi,

I have been using Ubuntu for a few months but have no idea what I am doing! I have tried to update but get the following message and my software centre doesn't do anything except pretend it's loading :-)

E: Unable to parse package file /var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_natty_main_binary-i386_Packages (1)
E: The package lists or status file could not be parsed or opened.

Is this the same error or a different one?

Thank you for any help :-)
[/FONT]

---

### Post by mörgæs on 2011-10-02
It is most likely the same error. 

Please boot the computer, close all windows which might open and run the commands written above.

---

