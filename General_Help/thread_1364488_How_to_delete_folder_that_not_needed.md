---
title: "How to delete folder that not needed ?"
date: 2009-12-25
forum: General Help
---

### Post by chitragurung on 2009-12-25
My computer has so many recup_dir.19 folders. I wanted to remove all of those folders and I got these error message. These kind of folder is created when I try to run Photorec command.


The folder "recup_dir.19" cannot be handled because you do not have permissions to read

---

### Post by taurus on 2009-12-25
You can remove those directories from a terminal with root privilege if you are not the owner or run nautilus with root privilege then.

Applications -> Accessories -> Terminal
```
gksudo nautilus
```
Now, navigate to where those directories/folders are.

---

### Post by chitragurung on 2009-12-26
Thank you very much for your prompt post. It works. 

But I have lost my emails and contacts from evolution. I could not find it in my computer. Is that possible to recover  it ? Do you have any idea

---

### Post by taurus on 2009-12-26
If you removed it with nautilus, chances are it is still in the trash bin.  

```
ls -la ~/.local/share/Trash/files
```

---

### Post by chitragurung on 2009-12-26
I have story. What happen is I used remove duplicates plugin to remove my duplicates mails from evolution. It worked well. Than I used filter making dead line such as older than 2004 or so on and all message gone from sent folder. Than I try to recover using Photorec command from  terminal and it created lots of recup-dir which I just now able to delete. 

I try to back up or find mails from one of  recup-dir folder using evolution import command. whole mails, contacts gone and restarted evolution with fresh and default setting. I found in forum that if we reinstall evolution from software source but still nothing happen. Since yesterday I am working to find it but no any solution found in the forum or even in internet. Some forum recommend use Photorec command but that is too long process and it creats lots of directory which takes lots of space and computer become too slow to work.

So, if you have any idea  that could be highly appreciated.

after following your above command I got the following results but I do not know the next

chitra@chitra:~$ ls -la ~/.local/share/Trash/files
total 938184
drwxr-xr-x 20 chitra chitra      4096 2009-12-25 22:33 .
drwxr-xr-x  4 chitra chitra      4096 2009-10-06 09:01 ..
-rw-r--r--  1 chitra chitra    120870 2009-10-04 21:50 0001.jpg
-rw-r--r--  1 chitra chitra    106333 2009-10-06 21:06 0003.jpg
-rw-r--r--  1 chitra chitra     88568 2009-10-10 13:58 0004.jpg
-rw-------  1 chitra chitra  13728428 2009-12-24 08:57 0 - 00 - Unknown Artist - Unknown Title.new.wav
-rw-------  1 chitra chitra  13728428 2009-12-24 08:52 0 - 00 - Unknown Artist - Unknown Title.wav
-rw-r--r--  1 chitra chitra     16873 2009-12-08 08:44 05_business_letter.ott
drwx------  5 chitra chitra      4096 2009-12-08 08:49 05_business_letter.ott_FILES
drwx------  7 chitra chitra      4096 2009-10-31 08:40 Adobe Acrobat 7.0 Pro
-rwx------  1 chitra chitra 190989312 2009-10-05 13:07 archive.pst
-rw-r--r--  1 chitra chitra       428 2007-05-09 16:23 chrome.manifest
-rw-r--r--  1 chitra chitra    204087 2009-10-30 09:55 cnxtinstall(2).run
-rw-r--r--  1 chitra chitra    204087 2009-10-30 08:45 cnxtinstall.run
drwxr-xr-x  2 chitra chitra      4096 2007-07-27 21:11 components
drwxr-xr-x  2 chitra chitra      4096 2007-05-22 19:31 content
-rw-r--r--  1 chitra chitra    637171 2008-10-20 11:44 Copy of DSCN3329.JPG
-rw-r--r--  1 chitra chitra    654118 2008-10-20 11:45 Copy of DSCN3330.JPG
-rw-r--r--  1 chitra chitra    704524 2008-10-21 11:38 Copy of DSCN3331.JPG
-rw-r--r--  1 chitra chitra    687553 2008-10-21 15:40 Copy of DSCN3332.JPG
-rw-r--r--  1 chitra chitra    697933 2008-10-22 06:30 Copy of DSCN3333.JPG
-rw-r--r--  1 chitra chitra    828229 2008-10-22 06:32 Copy of DSCN3334.JPG
-rw-r--r--  1 chitra chitra    639741 2008-10-22 08:57 Copy of DSCN3336.JPG
-rw-r--r--  1 chitra chitra    664112 2008-10-22 10:37 Copy of DSCN3337.JPG
-rw-r--r--  1 chitra chitra    595106 2008-10-22 14:27 Copy of DSCN3339.JPG
-rw-r--r--  1 chitra chitra    770652 2008-10-23 05:55 Copy of DSCN3340.JPG
-rw-r--r--  1 chitra chitra    766075 2008-10-23 06:19 Copy of DSCN3341.JPG
-rw-r--r--  1 chitra chitra    386085 2008-10-23 06:22 Copy of DSCN3342.JPG
-rw-r--r--  1 chitra chitra    539279 2008-10-23 06:22 Copy of DSCN3343.JPG
-rw-r--r--  1 chitra chitra    666124 2008-10-23 06:23 Copy of DSCN3344.JPG
-rw-r--r--  1 chitra chitra    657277 2008-10-23 06:24 Copy of DSCN3345.JPG
-rw-r--r--  1 chitra chitra    624887 2008-10-23 06:24 Copy of DSCN3346.JPG
-rw-r--r--  1 chitra chitra    677709 2008-10-23 06:25 Copy of DSCN3348.JPG
-rw-r--r--  1 chitra chitra    632192 2008-10-23 06:27 Copy of DSCN3349.JPG
-rw-r--r--  1 chitra chitra    350928 2008-10-23 09:39 Copy of DSCN3352.JPG
drwxr-xr-x  2 chitra chitra      4096 2009-09-24 03:28 courier-analog-0.16
-rw-r--r--  1 chitra chitra      9523 2009-12-02 07:20 DellDriverDownloadManager(2).application
-rw-r--r--  1 chitra chitra      9523 2009-12-02 07:17 DellDriverDownloadManager.application
-rw-r--r--  1 chitra chitra    241664 2009-10-30 19:03 Exchange Program Xplore India Nepal 2009 26-10-2009.doc
-rwx------  1 chitra chitra       765 2009-09-10 17:32 extend.dat
drwxr-xr-x  4 chitra chitra      4096 2009-10-19 21:35 glink
drwxr-xr-x  2 chitra chitra      4096 2009-11-30 09:37 Holland
-rw-------  1 chitra chitra       196 2009-12-25 22:31 Inbox.ev-summary
-rw-------  1 chitra chitra        36 2009-12-25 22:31 Inbox.ev-summary-meta
-rw-r--r--  1 chitra chitra       991 2007-10-18 14:32 install.rdf
-rw-------  1 chitra chitra    274711 2009-10-29 11:09 Invoice2.pdf
-rw-------  1 chitra chitra    274016 2009-10-30 13:17 Invoice.pdf
-rwxrwxrwx  1 chitra chitra    569060 2008-08-29 18:59 libscmssc (copy).2.so
-rwxrwxrwx  1 chitra chitra    569060 2008-08-29 18:59 libscmssc (copy).so
-rwxrwxrwx  1 chitra chitra    606152 2008-08-29 18:59 libscmssf (copy).2.so
-rwxrwxrwx  1 chitra chitra    606152 2008-08-29 18:59 libscmssf (copy).so
drwxr-xr-x  4 chitra chitra      4096 2009-11-25 17:53 linkback
-rw-r--r--  1 chitra chitra      2028 2009-11-29 09:55 linkback.zip
drwxr-xr-x  4 chitra chitra      4096 2007-04-02 20:45 locale
drwxr-xr-x 75 chitra chitra     32768 2009-10-04 10:09 My Tour Files
drwx------ 76 chitra chitra     32768 2009-12-18 10:29 My Tour Files.2
-rw-r--r--  1 chitra chitra    390381 2009-10-07 11:50 Outlook contats.ldif
-rwx------  1 chitra chitra 658260992 2009-10-05 13:05 Outlook.pst
drwxr-xr-x  3 chitra chitra      4096 2009-10-07 11:29 personal folders.sbd
drwxr-xr-x  4 chitra chitra      4096 2007-04-02 14:01 platform
-rw-r--r--  1 chitra chitra   5971968 2009-11-03 14:06 Poojalama1.mpg
-rwxrwxrwx  1 chitra chitra      8456 2008-09-17 19:38 pscms (copy)
-rwxrwxrwx  1 chitra chitra      8456 2008-09-17 19:38 pscms (copy).2
-rw-r--r--  1 chitra chitra   1083439 2008-03-18 19:28 pst-import_1.2.xpi
-rw-r--r--  1 chitra chitra   1077079 2009-10-10 11:09 pst-import_1.2.xpi.tar.gz
-rw-r--r--  1 chitra chitra   5845890 2009-12-01 16:07 Puja_lama_Scandal.zip
-rwxrwxrwx  1 chitra chitra     52280 2008-09-17 19:38 rastertosamsunginkjet (copy)
-rwxrwxrwx  1 chitra chitra     52280 2008-09-17 19:38 rastertosamsunginkjet (copy).2
-rwxrwxrwx  1 chitra chitra     34324 2008-09-17 19:38 rastertosamsungpcl (copy)
-rwxrwxrwx  1 chitra chitra     34324 2008-09-17 19:38 rastertosamsungpcl (copy).2
-rwxrwxrwx  1 chitra chitra    106616 2008-09-17 19:38 rastertosamsungsplc (copy)
-rwxrwxrwx  1 chitra chitra    106616 2008-09-17 19:38 rastertosamsungsplc (copy).2
-rwxrwxrwx  1 chitra chitra     54376 2008-09-17 19:38 rastertosamsungspl (copy)
-rwxrwxrwx  1 chitra chitra     54376 2008-09-17 19:38 rastertosamsungspl (copy).2
-rw-r--r--  1 chitra chitra        85 2007-05-02 21:04 README
drwxr-xr-x  4 chitra chitra      4096 2007-11-05 05:39 remove-duplicates-plugin-0.0.4
-rw-r--r--  1 chitra chitra    364093 2009-10-10 10:21 remove-duplicates-plugin-0.0.4.tar.gz
drwxrwxrwx  4 chitra chitra      4096 2007-11-05 05:39 remove-duplicates-plugin-0.2.0.4
drwxrwxrwx  4 chitra chitra      4096 2007-11-05 05:39 remove-duplicates-plugin-0.3.0.4
-rw-r--r--  1 chitra chitra   1856808 2009-12-02 09:30 rename_your_file(2).2.mp3
-rw-r--r--  1 chitra chitra   1856808 2009-12-02 09:13 rename_your_file(2).mp3
-rw-r--r--  1 chitra chitra     81716 2009-10-29 17:20 scanModem.2.gz
-rw-r--r--  1 chitra chitra     81716 2009-10-15 20:35 scanModem.gz
drwxr-xr-x  2 chitra chitra      4096 2007-05-02 13:57 src
-rw-r--r--  1 chitra chitra      5710 2009-12-01 16:39 test.html
-rw-r--r--  1 chitra chitra    704711 2009-11-21 15:45 tharu stick dance chitwan.mp3
-rw-r--r--  1 chitra chitra  30149710 2009-10-08 09:16 UnifiedLinuxDriver(2).tar.gz
-rw-r--r--  1 chitra chitra      3192 2009-10-20 08:45 Unsaved Document 1
drwx------  2 chitra chitra      4096 2009-10-14 22:27 USB_based
-rw-r--r--  1 chitra chitra         0 2009-10-14 21:55 USB_based.rar
-rw-r--r--  1 chitra chitra     36048 2009-10-17 16:49 usb-modeswitch_1.0.2.orig(2).tar.gz
-rw-r--r--  1 chitra chitra     36048 2009-10-17 16:40 usb-modeswitch_1.0.2.orig.tar.gz
-rwx------  1 chitra chitra   3416523 2009-11-21 10:33 video2 tharu.flv
-rwx------  1 chitra chitra  12980652 2009-11-21 10:30 video.flv
chitra@chitra:~$ ls -la ~/.local/share/Trash/files
chitra@chitra:~$

---

### Post by Claus7 on 2010-02-10
Hello,

probably you have solved your problem, yet photorec seems and ideal tool to use in your situation. You could buy and external hdd and recover there the missing files. You will have to have in mind that photorec will bring back to life all the files that it can recover, not only those you are interested in. You could use testdisk as well and see what you can get. The process can take long, so you might have to do it overnight.

Always in these situations you have in mind that the more you write on the hdd the more your data follow the road to oblivion.

Regards!

---

