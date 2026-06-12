---
title: "Home Folder Filled Up"
date: 2011-03-14
forum: General Help
---

### Post by shredderbond on 2011-03-14
Sorry if i am reposting, but its weird but when i am trying to do 
sudo du -sch * in my main home folder i get the output:

du: cannot access `vishram/.gvfs': Permission denied
11G    vishram
11G    total

while if i do it inside /home/vishram/ folder (vishram is the username) i get the output:

0    BLts3z
6.2M    Desktop
4.0K    Documents
7.2M    Downloads
4.0K    edid.bin
4.0K    examples.desktop
932K    Firefox_wallpaper.png
0    KVKOFr
4.0K    Music
1.5G    ns-3
16K    perl
8.0K    Pictures
4.0K    Public
4.0K    Templates
20K    test
38M    themes
4.0K    Ubuntu One
4.0K    Videos
0    Wj24sP
1.5G    total

I am not sure where is the space going.. I have deleted the trash of user and root. 
I have already checked if there is a big log file. checked if there is any file > 1 GB of size. But no such thing exist.

Also Disk Usage Analyzer shows the following output:
Folder                usage                     size

home                 12.3%                     10.4 GB
home/vishram     100%                      10.4 GB


while inside the vishram folder all the files sum up to only 1.5 GB (Checked through DUA and du utilities) ..  Still the total size shown comes to 11 GB, which int urn gives me the warning that i am running out of space.

Please help me.
Thanking you in anticipation.



[IMG]file:///home/vishram/Desktop/Screenshot.png[/IMG]

---

### Post by plucky on 2011-03-15
This [link](http://ubuntuforums.org/showthread.php?t=898573&highlight=drs305) is always useful for disk full problems.

Good Luck

---

