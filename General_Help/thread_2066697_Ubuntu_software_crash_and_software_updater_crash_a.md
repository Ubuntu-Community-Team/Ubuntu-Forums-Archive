---
title: "Ubuntu software crash and software updater crash as well"
date: 2012-10-05
forum: General Help
---

### Post by flamcsd on 2012-10-05
Hello , all 

my Ubuntu software crash and software updater crash as well. 

I got following error message. 

Could not initialise the package information

An unresolvable problem occurred while initialising the package information.

Please report this bug for the 'update-manager' package and try to include the following error message:

'E:Encountered a section with no Package: header, E:Problem with MergeList /var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_precise_main_i18n_Translation-en, E:The package lists or status file could not be parsed or opened.'

---

### Post by jerrrys on 2012-10-05
Hi flamcsd, welcome to the forum  :)

[Open a terminal]("https://help.ubuntu.com/community/UsingTheTerminal#Starting_a_Terminal") and enter:

sudo rm -rf /var/list/apt/lists/*

sudo apt-get update

Now try the software center

---

### Post by flamcsd on 2012-10-05
Hi jerry

thanks for your help. I performed your command in a terminal. I still got some error messages. 

Fetched 1,201 kB in 1s (643 kB/s)                 
Reading package lists... Error!
W: GPG error: [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_precise_main_i18n_Translation-en
E: The package lists or status file could not be parsed or opened.

---

### Post by jerrrys on 2012-10-05
sudo -i 
apt-get clean
 cd /var/lib/apt
 mv lists lists.old
 mkdir -p lists/partial
 apt-get clean
 apt-get update

First link -- method #1

[http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=GPG+error+BADSIG&as_qdr=all&sa=Google+Search&lang=en]("http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=GPG+error+BADSIG&as_qdr=all&sa=Google+Search&lang=en")

---

### Post by flamcsd on 2012-10-05
Thank you jerrrys, 

My problem solved. 

Thanks again for the quick fix. really good help.

---

### Post by jerrrys on 2012-10-05
Good show  :)

Terminal commands come in handy, check it out

[https://help.ubuntu.com/community/AptGet/Howto#Commands](https://help.ubuntu.com/community/AptGet/Howto#Commands)

[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

---

