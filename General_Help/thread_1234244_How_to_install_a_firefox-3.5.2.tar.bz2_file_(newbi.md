---
title: "How to install a firefox-3.5.2.tar.bz2 file (newbie question)"
date: 2009-08-07
forum: General Help
---

### Post by ryansdistrict on 2009-08-07
[s]i just wanted to upgrade my firefox i downloaded the file but note sure hwo to install it[/s]thank you this helped but 1 more question 
i have an other version of firefox on my window version i think its impossible to share same database of saved passwords and saved data on both windows 
so how cna i export old firefox data from windows to the new firefox version on ubunto ?

THx

---

### Post by jmszr on 2009-08-07
ryandistrict,

Here are a couple of resources that should help: [http://www.psychocats.net/ubuntu/firefox](http://www.psychocats.net/ubuntu/firefox) and:[http://ubuntumanual.org/posts/197/install-firefox-3-5-1-in-ubuntu-using-ubuntuzilla](http://ubuntumanual.org/posts/197/install-firefox-3-5-1-in-ubuntu-using-ubuntuzilla) .

Hope that helps.

---

### Post by ryansdistrict on 2009-08-07
thank you this helped but 1 more question 
i have an other version of firefox on my window version i think its impossible to share same database of saved passwords and saved data on both windows 
so how cna i export old firefox data from windows to the new firefox version on ubunto ?

THx

---

### Post by jmszr on 2009-08-07
ryansdistrict,

These may be of some help: [https://help.ubuntu.com/community/SwitchingToUbuntu/FromWindows/TransferringFilesAndSettings](https://help.ubuntu.com/community/SwitchingToUbuntu/FromWindows/TransferringFilesAndSettings) this: [http://www.brighthub.com/computing/windows-platform/articles/30318.aspx](http://www.brighthub.com/computing/windows-platform/articles/30318.aspx) and this: [http://www.makeuseof.com/tag/share-you-firefox-data-across-operating-systems-and-computers/](http://www.makeuseof.com/tag/share-you-firefox-data-across-operating-systems-and-computers/) .

Hopefully between the three of them you'll find the info that you need.

---

### Post by lovinglinux on 2009-08-07
> **ryansdistrict said:**
> thank you this helped but 1 more question 
i have an other version of firefox on my window version i think its impossible to share same database of saved passwords and saved data on both windows 
so how cna i export old firefox data from windows to the new firefox version on ubunto ?

THx

If you installed the package downloaded from Mozilla it should use the same profiles as FF 3.0. If you install FF 3.5 from the repositories, then it makes a copy of your profiles from ~/.mozilla/firefox to ~/.mozilla/firefox-3.5. So take a look if you have the second one. It is just a matter of copying the contents from one folder to the other.

I recommend using FEBE for exporting and restoring profiles. See the Firefox tutorial link on my signature for further instructions.

---

