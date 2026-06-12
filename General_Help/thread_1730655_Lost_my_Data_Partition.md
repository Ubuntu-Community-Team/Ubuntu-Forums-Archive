---
title: "Lost my Data Partition"
date: 2011-04-16
forum: General Help
---

### Post by Shurdhaqi on 2011-04-16
I installed Ubuntu 10.10 inside windows 7 in my C: partition. my hole HDD is 250 GBB and before installing Ubuntu I had 2 partitions C: (bootable with windows) and D: (not bootable, there was all my data there) and now ubuntu is installed in hole dhe HDD 250 GB. Help me how can I have back my D partition with my data undeleted!! I don't care about win 7 I just want my data back! Help me please!!!

---

### Post by oldfred on 2011-04-16
If you installed a new operating system to the entire drive you repartitioned the entire drive.

Stop using hard drive as all activity is overwriting your data.

Ubuntu does not necessarily install to the first part of the drive where c: was so you may have overwritten parts of d:.

Two tools are available to repair. Testdisk restores partitions, but the internal structure has to be ok. Photorec which may work in your case, if you overwrote entire drive, scans drive for anything that looks like a file and copies that. You have to have another drive of the size required to recover the data.

To see what you have post this from liveCD:

Boot Info Script courtesy of forum members meierfra & Gert Hulselmans
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt in a New Reply, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the New Reply Edit toolbar and then paste the contents between the generated [ code] paste here [ /code] tags.

---

### Post by Shurdhaqi on 2011-04-18
Thanks for helping!! I solved it! It was just a change of file system from NTFS to ext4 and I changed it back with the Testdisk tool. Then I boot from a windows cd and I'm gonna reinstall Ubuntu 10.10 again in a special partition, not aside windows.

---

### Post by oldfred on 2011-04-18
Normally you should have good backups (Do as I say not as I do as Mom told me:) or do not find my other posts about my recovering data). But especially before system changes, you should make a good backup.

Some good links on installs:

Installs -----------------------
[https://help.ubuntu.com/community/GraphicalInstall](https://help.ubuntu.com/community/GraphicalInstall)

Some examples of installs and issues:
Issues on dual boot in same drive:
[http://ubuntuforums.org/showthread.php?t=1622388](http://ubuntuforums.org/showthread.php?t=1622388)
From kansasnoob:
[http://ubuntuforums.org/showpost.php?p=10145206&postcount=15](http://ubuntuforums.org/showpost.php?p=10145206&postcount=15)
Trust me here! If you choose either "Use entire partition" or "Use entire disc" you are not likely to end up with "Alongside" anything! You will most likely lose the OS and any data contained therein!

Ubuntu Install steps - then choose guide, close to what you want.
[http://members.iinet.net/~herman546/index.html](http://members.iinet.net/~herman546/index.html)
Installs with good screenshots/examples:
[http://members.iinet.net.au/~herman546/p22.html](http://members.iinet.net.au/~herman546/p22.html)
with separate /home from aysiu
[http://www.psychocats.net/ubuntu/installseparatehome](http://www.psychocats.net/ubuntu/installseparatehome)

---

### Post by Shurdhaqi on 2011-05-02
Thanks for helping... But I sad I solved it and now have another problem... now I upgraded to Ubuntu 11.04 in online mode. It took 1h and 45min to get the packages and 1h 15min to install them (don't understand why so much) but I think something is going wrong with Mozilla Firefox, it is tooooo slowly and any time crashes, is it going something wrong with resources or what. I have a 1Mbps internet line and didn't have this problem with Ubuntu 10.10 or Win 7. SOS!!!

---

### Post by oldfred on 2011-05-02
New installs pick a server to install from. Have you tried to change to an optimal one?

System, Administration, Update Manager. Click on settings button on bottom left and in first tab - Ubuntu Software is a combo box on site used to update. Click on combo box and choose other. Then Select Best Server.

---

### Post by Shurdhaqi on 2011-05-03
I did it, but the problem is not only while I'm downloading the system updates but even when I surf in the web, I think that it's not a problem with the internet line but with the browser (Mozilla) AND with the system itself, it seems too slowly, not like it used to be with Ubuntu 10. Is that any tool or other software that allows me fix it cuz God Damn it I have 3 GB RAM DDR2 and Intel Core 2 Duo 2.0 GHz processor, it shouldn't be so slowly... Thanks for helping again!!!

---

### Post by oldfred on 2011-05-03
check memory use to see if swap is being used as that is 10 times slower, then check what is running with top (q to exit).

free -m

top

---

