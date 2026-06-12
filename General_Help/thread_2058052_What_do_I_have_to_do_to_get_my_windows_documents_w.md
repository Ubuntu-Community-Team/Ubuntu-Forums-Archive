---
title: "What do I have to do to get my windows documents while in Ubuntu?"
date: 2012-09-14
forum: General Help
---

### Post by rickw137 on 2012-09-14
I am new to Ubuntu and I like it, but I am looking for a step by step instruction on how (if possible) to get my Windows files while in Ubuntu? Please? Thanks!

---

### Post by spjackson on 2012-09-15
I'll assume that you are using Ubuntu 12.04 with the default desktop and that you are dual booting with your Windows documents on the same computer. Obviously, if the documents are on another computer or a USB stick, then the instructions will be different.

Click on the Dash Home icon. Type in Disk Utility and start the Disk Utility program. Select your hard disk in the left hand pane. This should then show the various "partitions" on your disk. Click on the one that looks like the Windows partition. Mine shows as Windows7_OS and NTFS. Now click on the Mount Volume button. This should add a hard disk icon to your Dash. Click on that.

You should now be able to browse to your documents. On Windows 7 you probably want /Users/<username>/Documents. The path might be different for older Windows versions.

LibreOffice can open Micrososft Office documents reasonably well. So you should just have to browse to the document you want and click on it. If you actually want to install Windows software under Linux, then that's a different ballgame.

---

### Post by jerrrys on 2012-09-15
Hello rickw137; welcome to the forums :)

Here are some more links that might help.

[http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=access+windows&as_qdr=all&sa=Google+Search&lang=en&siteurl=http%3A%2F%2Fwww.googlubuntu.com%2F](http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=access+windows&as_qdr=all&sa=Google+Search&lang=en&siteurl=http%3A%2F%2Fwww.googlubuntu.com%2F)

---

### Post by rickm1945 on 2012-09-15
> **rickw137 said:**
> I am new to Ubuntu and I like it, but I am looking for a step by step instruction on how (if possible) to get my Windows files while in Ubuntu? Please? Thanks!
If you are using Ubuntu 12.04, click on your Home folder, on the left side you will see several folder listings at top left you will see devices. Under that, on mine, is System, then the Windows partition, on mine it says 186Gb, yours will say something like that. Double click on it and you will see all you Windows files. Hope this helps you and good luck. 
BTW, if you want to copy your documents folder from Windows to Ubuntu just open the Windows Documents Folder highlight all the files and press ctrl-C and then open the documents folder in Ubuntu and simply paste them into your Ubuntu Documents folder. ctrl-V will paste them.

---

### Post by oldfred on 2012-09-15
Just be sure not to have Windows in hibernation and write something back into it. The hibernation cannot see any changes and then they are lost or you corrupt system.

Because the NTFS driver shows all files and folders, like the administration user and does not hide the system files & folders like Windows you also have to be careful not to move a system file. In Windows I would always turn on view all the files and then click and drag too quick and move something where it should not. Creates lots of fun trying to fix Windows when you cannot find what file got moved. :)

Many suggest a separate shared data partition or d: in Windows. Then you can set c: as read only from Ubuntu and use the shared data as read/write. I still have my shared NTFS partition even though I do not boot XP. I have my Firefox & Thunderbird profiles so I had same email & bookmarks.

---

