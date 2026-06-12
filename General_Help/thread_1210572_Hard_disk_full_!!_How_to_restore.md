---
title: "Hard disk full !! How to restore ??"
date: 2009-07-11
forum: General Help
---

### Post by mirkko22 on 2009-07-11
Hi

Yersterday I have make some test with some backup software...And today I can not do nothing with my PC...Impossible to save anything because my hard disk seem to be full !! It seem I have make some confusion with my test and now some data are present somewhere and full my hard disk...

I am totally newbie and don't know how to solve this problem...I would like if possible just restore my hard disk like it was 48h before...

Is possible to do with a specific command ??? I run Ubuntu 9.04..

thanks for help

---

### Post by irv on 2009-07-11
It sound like you backed up to the wrong location. If you backed up to your hard drive you might of filled it up. What did you use for the backup? or Did you do it at a command prompt? You may want to search your hard drive for .bak files.

---

### Post by ibutho on 2009-07-11
I don't think you can easily revert back to 48 hours ago, but you could just delete any files you do not need. If you have problems doing it from within the installation, you could boot using a live cd, mount your Ubuntu paritions and then delete any files you do not need.

---

### Post by mirkko22 on 2009-07-11
I have try to install and use the software "backuppc" but is was complexe and I have stop install and config by closing teh terminal...

I see inside folder "var" a folder called "backup" marked with a "X" and if I try to look inside I get a message "you don't have enough right".... It appear all data are stored inside and I just need to delete this folder...But how I can do ? I must be as root but in this case how to do ??

thanks

---

### Post by ssri on 2009-07-11
open terminal
cd into the backup directory

then type:

rm -r .

or

cd /var

sudo rm -r X

helps?

---

### Post by mirkko22 on 2009-07-11
Beautiful guys...thanks a lot !!! I have delete folder backup and now am able to use my pc.....cool...

I must analyze well how to do backup for avoid this problem in future....

I would like just use a tools permitting me to make regular data backup and store them on my external hard disk...I would like a tools using incremental process for avoid make backup of non changed data...

I am newbie and I would like a simple tools in graphical mode if possible...

Do you have some advice please ???

---

### Post by irv on 2009-07-11
Check out these links:
[http://backintime.le-web.org/]("http://backintime.le-web.org/")
[http://backintime.le-web.org/download_page/]("http://backintime.le-web.org/download_page/")
This might be what you are looking for.

---

### Post by mirkko22 on 2009-07-11
Thank for suggestion...it appear simple and cool....but seem to not manage incremental backup...Anyway I will test it...

---

