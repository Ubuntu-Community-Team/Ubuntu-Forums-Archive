---
title: "Synchronise folders / FTP (alternative for Dropbox)"
date: 2010-08-31
forum: General Help
---

### Post by wjhulzebosch on 2010-08-31
Hi there,

I'm using a computer, and 2 notebooks. All off them have dropbox installed to synchronize my files, but i want more space. Luckily i have an FTP server at home, with more then enough space, and a lot off bandwith, but here it is: How do i synchronize a folder on my desktop/notebook with FTP? 

All i want is a simple program that runs in the background, detects file changes, and upload it to the FTP. When a newer version is detected on the FTP, it should download it. When i delete a file localy, it should be deleted on the FTP, and delete it on the other workstations to. This way, every file is stored localy, so i can use it, whether i have internet access or not, and when i have internet access, it synchronizes everything.

On my desktop i run Ubuntu 10.04 64-bit, on my notebooks i run 9.04 x86. I can use the command line (once or twice), but after that, i want the process to run automated (like dropbox). Is there anything like that available? I've heard about rsync, but that doesn't seem to be automated. All the  solutions i've seen so far, don't give me the same options and  easy-to-use-interface as Dropbox. This question has been around for 2 or  3 years on the internet now, so i suppose there would be a nice simple  program around about now. Any ideas?

---

### Post by wjhulzebosch on 2010-09-03
Anybody?

---

### Post by KeyserSoze93 on 2010-09-03
The command line app lftp has support for mirroring a directory, though I have not tried it.

Lftp is scriptable, so you can automate the task if it works to your satisfaction.

Install it from the repos and check out the manpage section of mirroring.

Hope it helps. If you have the option of enabling ssh access in addition to FTP, nothing beats rsync.

---

