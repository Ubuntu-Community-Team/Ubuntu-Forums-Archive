---
title: "Deleting viruses after scanning."
date: 2010-04-03
forum: General Help
---

### Post by karthick87 on 2010-04-03
I am using clamav antivirus to scan my NTFS drives in which i have some datas.After scanning, it shows some of my files were infected.I would like to remove the infected files,so wat command should i use to remove the infected files and how can i see the name of the infected files?


```


 ----------- SCAN SUMMARY -----------  
 Known viruses: 753403  
 Engine version: 0.95.1  
 Scanned directories: 1516  
 Scanned files: 16416  
 Infected files: 16
 Data scanned: 3529.21 MB  
 Data read: 4862.38 MB (ratio 0.73:1)  
 Time: 662.828 sec (11 m 2 s)  
 
```

---

### Post by karthick87 on 2010-04-05
Bump for a move.!

---

### Post by NightwishFan on 2010-04-05
I think you need to add a parameter in the actually command before you run the scan. You can have them move to a specific folder or automatically be deleted. Be careful if you have them be automatically deleted in the odd chance it removes something that is not a virus. Check the man page.
```
man *nameofcommand*
```



I wish I could tell you more but I have not used this program in a long time.

---

### Post by Herman on 2010-04-05
It's not always as simple as just removing the infected files, although that would be a good starting off point. It all depends on the nature of the particular virus you're trying to remove. They're all different.

Sometimes you can find a website with instructions for removing certain viruses by looking up the name of the virus and googling. 
If you decide you can trust the instructions from a website you may find yourself editing the Windows registry. You can install a program called '[chntpw]("http://home.eunet.no/pnordahl/ntpasswd/")', in Ubuntu to do that with.  It can give a person a satisfying sense of achievement if the operation turns out to be successful  and you're able to get a disabled Windows computer working again.

Most of the time though, Windows won't be quite as good as new after its ordeal, and you could waste a lot of time messing around without doing any good.

If you are counting your time in dollars, it's much more economical just to back up the files, nuke the hard drive with zeros and re-install. That's the best way to ensure a good result too. Windows seems to be an operating system that requires frequent re-installs.

EDIT: I re-read your post and I think I can give you a more appropriate answer now.

[ClamAV]("https://help.ubuntu.com/community/ClamAV#Using%20ClamAV") - Ubuntu Community Docs says, 
> To check files in the all users home directories,
```
clamscan -r /home
```To check all files on the computer, displaying the name of each file, 
```
sudo clamscan -r / 
```To check all files on the computer, but only display infected files and ring a bell when found,
```
sudo clamscan -r --bell -i /
```And to remove files infected with viruses you can add --remove to the clamscan or clamdscan commandline. 

---

