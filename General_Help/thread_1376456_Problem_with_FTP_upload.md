---
title: "Problem with FTP upload"
date: 2010-01-09
forum: General Help
---

### Post by W.S.M. on 2010-01-09
I uploaded some script to my web folder. But, when I run the script, it didn't work. I asked the supporter of my host provider, and he said that my file has corrupted. I tried 3 different FTP client: gFTP, FileZilla, FireFTP, and my file still corrupt. And I've tried some other host, my file still corrupt. So, I think the problem is about my system :( . Can anyone help me?

Btw, sorry for my bad English, I'm Vietnamese ;)

---

### Post by aaronp on 2010-01-09
Sounds like it may be the ASCII vs Binary issue that can corrupt some files when they are uploaded to webservers via FTP.
If you haven't already, try changing the mode from ASCII to binary (or vice versa) in your FTP client.

---

### Post by Dayofswords on 2010-01-09
> **W.S.M. said:**
> Btw, sorry for my bad English, I'm Vietnamese ;)

you speak better than most first language english speakers that i hear;)


bit sad really, but funny

---

### Post by HiImTye on 2010-01-09
if your file contains any non-ascii characters then you must transfer it using binary
this is for media, pdf files, doc files, etc
ascii uses only the first 7 bits in a standard byte so if your file is 8;16;32 bit, it will cut the remainder off

ascii is useful in that it is slightly faster than binary transfers and it formats the end of line/file characters into the native file systems character

---

### Post by W.S.M. on 2010-01-09
> **aaronp said:**
> Sounds like it may be the ASCII vs Binary issue that can corrupt some files when they are uploaded to webservers via FTP.
If you haven't already, try changing the mode from ASCII to binary (or vice versa) in your FTP client.

I has tried both binary and ASCII mode, but my file still corrupt :(

---

### Post by dcstar on 2010-01-10
> **W.S.M. said:**
> I has tried both binary and ASCII mode, but my file still corrupt :(

Upload it and then download it to your PC and see what the corruption is.

---

### Post by W.S.M. on 2010-01-15
Hi, sorry for long time no reply ;)
I have solved the problem myself. The file was not corrupt. 1 of my script has a bug in it, therefore I can't run the script.

---

