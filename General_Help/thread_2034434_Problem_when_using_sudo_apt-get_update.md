---
title: "Problem when using sudo apt-get update"
date: 2012-07-28
forum: General Help
---

### Post by danbrownlow on 2012-07-28
Hey there,

Not really a big problem (yet) but I noticed I had a message on my status bar telling me that I may need to manually update so I clicked, "Checked for updates now". That didn't seem to do anything as the message was still there so I tried opening from Software updater.

When I opened the Software Updater, the message on top reads, "Software updates may be available for your computer. The package information was last updated 7 days ago".

A quick check online told me to run "Sudo apt-get update" followed by "Sudo apt-get upgrade".

When I tried to run "Sudo apt-get update" I got the following message in the terminal

```
 W: GPG error: http://archive.canonical.com precise Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: An error occurred during the signature verification. The repository is not updated and the previous index files will be used. GPG error: http://extras.ubuntu.com precise Release: The following signatures were invalid: BADSIG 16126D3A3E5C1192 Ubuntu Extras Archive Automatic Signing Key <ftpmaster@ubuntu.com>

W: GPG error: http://ppa.launchpad.net precise Release: The following signatures were invalid: BADSIG F192197F81992645 Launchpad love-stable
W: GPG error: http://ppa.launchpad.net precise Release: The following signatures were invalid: BADSIG 5C92FC592AE51AB5 Launchpad PPA for consindo
W: GPG error: http://ppa.launchpad.net precise Release: The following signatures were invalid: BADSIG 5C92FC592AE51AB5 Launchpad PPA for consindo
W: GPG error: http://ppa.launchpad.net precise Release: The following signatures were invalid: BADSIG 508A982D7A617FF4 Launchpad official ppa for pcsx2 team
W: GPG error: http://ppa.launchpad.net precise Release: The following signatures were invalid: BADSIG 3BDAAC08614C4B38 Launchpad otto06217
W: GPG error: http://ppa.launchpad.net precise Release: The following signatures were invalid: BADSIG 8CD60EC948894010 Launchpad PPA for Scopes Packagers
W: GPG error: http://ppa.launchpad.net precise Release: The following signatures were invalid: BADSIG 464AD83D4631BBEA Launchpad equinoxart
W: GPG error: http://ppa.launchpad.net precise Release: The following signatures were invalid: BADSIG 6AF0E1940624A220 Launchpad PPA for TualatriX
W: GPG error: http://ppa.launchpad.net precise Release: The following signatures were invalid: BADSIG E840828F81E7FE09 Launchpad PPA for Ubuntu Vi&#7879;t Nam
W: GPG error: http://ppa.launchpad.net precise Release: The following signatures were invalid: BADSIG C2518248EEA14886 Launchpad VLC
W: GPG error: http://ppa.launchpad.net precise Release: The following signatures were invalid: BADSIG C2518248EEA14886 Launchpad VLC
W: Failed to fetch http://extras.ubuntu.com/ubuntu/dists/precise/Release  

W: Some index files failed to download. They have been ignored, or old ones used instead.
dan@inn0min4t3:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded. 
```

The only thing I've changed recently was the location of the servers, as I installed Ubuntu in Vietnam and now I'm in the UK, so I tried to change the location of the server.

Thanks for any help.

---

### Post by Old_Grey_Wolf on 2012-07-28
Try these commands one at a time
```
sudo apt-get clean

cd /var/lib/apt

sudo mv lists lists.old

sudo mkdir -p lists/partial

sudo apt-get clean

sudo apt-get update
```

---

### Post by danbrownlow on 2012-07-28
Thanks a lot, that worked perfectly.

---

