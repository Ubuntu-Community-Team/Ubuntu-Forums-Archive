---
title: "(Almost) All downloads corrupted - hardware issue?"
date: 2010-09-03
forum: General Help
---

### Post by kralc on 2010-09-03
Thanks in advance for any assistance on this troubling issue.

System Stats: HP z800 workstation with dual Xeon quad core X5560 @  2.80GHz processors, 24 GB RAM, and four 1T Samsung drives configured in a  RAID 5 using LSI 9650SE controller. Nvidia graphics PCI card.

Current distro: Ubuntu 10.04.1 (note problem began while running 9.10)

Problem: All large (>5 MB ??) programs downloaded from web are corrupted (perhaps truncated) and will not install properly. these include tarballs (e.g., .tgz),  shell scripts of appreciable size (e.g. .sh greater than 10 MB), and other applications (.bin, etc). A few smaller compressed files (perhaps less than 5 MB) seem to download and install ok.

Details: 

This is my lab's principal workstation and is used for multiple applications, mostly for the analysis of molecular data. I have been using the machine for about 6 months and the initial install of 9.10 was relatively straightforward with typical hangups remedied by well-documented solutions.

Initially (while running 9.10), I was able to download files/programs just fine, installing well-known applications such as VBox, Google Earth, etc. as well as other programs specific to my work such as Geneious, SeaView and others. Analyses went fine, although I did notice that the fans never ramped up on heavy processor loads and the temp increased quite a bit (although it never reached a point for auto shutdown). Contacted HP and they said it wasn't an issue.

A few months ago I tried to download and install a .tgz file (~30MB) for a scientific program known as BEAST and I could not extract the file (Error: tar: option requires an argument -- f
Try `tar --help' or `tar --usage' for more information.).

On further inspection, I've come to realize the files are truncated or missing data - I was able to download the exact same file on the same LAN using a Windows PC connected via a switch. Transferring this file to the Linux machine via USB drive and I could extract and install the software just fine. I've had identical results with other files/programs. I've inspected the files in terminal confirming they are indeed truncated.

I first thought it might be a system corruption that I introduced (I've been rather free-wheeling with root), so I decided to do a complete new install of Ubuntu 10.04. For kicks, I tried downloading the iso on the troubled machine and burning a disk image (it was corrupt of course). I then did so on the PC and it was fine.

After rebuilding the RAID 5, I installed 10.04. Had a few moderately difficult problems including the "blank screen issue" and some trouble with shutdowns, etc, all of which I resolved with the help of the on-line documentation and forums (thanks!). Updates seem to work fine (and have never been a problem as far as I can tell).

I began to test download files/programs again, and the same issues were present. I also tried to download and install software that I successfully installed on the new machine when it was new (e.g., VBox, GoogleEarth, and Geneisous) and none of these installed this time (each producing some error or hang up).

I was able to download and install Google Chrome (somehow that worked) and tried downloading files via that browser. Same problem.

This all makes me think it is a hardware issue since it has accumulated over time and persists despite a total new install.

Other tests: Is it the RAID degrading? I pulled the 4 drives and the controller and installed a spare 500 GB Seagate that I had lying around, installed 10.04, and did the basic setup. Tried downloading and installing programs - same deal. Installed 9.10 on this spare drive as well, same deal. Installed Windows 7 and had some install issues (unrelated?) - I was able to download and install Geneious for Windows, however.

I've since re-installed the RAID controller and four drives and am now contemplating what to do next.

I did the basic diagnostic that comes with 10.04, but that didn't tell me much.

Is it the memory? Perhaps a motherboard thing? I plan to contact HP soon, but would like to rule out any software issues or bugs before I start begging them to replace my motherboard.

I'm at a total loss at this point and would appreciate any advice and/or suggestions.

---

### Post by kralc on 2010-09-03
Additional note: While typing the rather long message above, I clicked "submit post" and I was redirected to the log-in page...this has happened before on a separate forum I belong to, FYI. I expected my post to be lost, but I logged back in and it was posted. Related to the above issue? Not sure.

---

### Post by hakermania on 2010-09-03
What about the other PCs in your home connected to the same modem?

---

### Post by kralc on 2010-09-03
> **hakermania said:**
> What about the other PCs in your home connected to the same modem?

This is a system at the organization where I work. All other machines appear to be working fine. I even have an old HP Pentium 4 running 10.04 and it is not having any problems.

---

### Post by krimzonstarr on 2010-09-05
+1
I am running Mint 9 (Lynx-based), but had same issues under Ubuntu 10.04. All files downloaded via http/ftp show incorrect md5/sha256sums. Anything downloaded via torrent, never a problem. Netbook is running on wifi, never have an issue with Windows XP downloads on another netbook, same router.

---

