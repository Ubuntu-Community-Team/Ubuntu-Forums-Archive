---
title: "Need search term - Network Drive - Desktop w/LAMP, Etc..."
date: 2009-09-18
forum: General Help
---

### Post by jph989 on 2009-09-18
I am a novice but I have been playing with Ubuntu for about 4 years so I normally find what I need via this forum and Google... However today my GoogleFu is weak!

I have a new project box that I am playing around with and I want to create a web accessible network drive... Let me re-state that in case I have used the wrong terms, I want to go to my Windows laptop, my Mac Book, and my Ubuntu desktop and set up a desktop icon that when I click on it will prompt me for a password and then conect me to a remote storage point that is located on my server box.  A remote drive!  That way I can  store files and then access then from any computer in the world that I am on.

Can someone tell me where I can find a tutorial or other "how to" docs on this subject.... OR if it is easy could someone outline the steps here.  

PS. eventhough this box has the Juanty Jackalope desktop installed, I will be working, for the next few weeks, via the comand line over ssh.  so please omit any GUI options.  thank-you

JPH

---

### Post by Liolikas on 2009-09-18
Many ways but some of them hard some of them fail to work on windows etc. problems.

My favorite is to set up **pure-ftpd** on Linux system and then use ftp soft like simple browser to enter it. Super clasic way works on everything. On Linux and I think Mac you can even mount ftp like drive still not sure about windows.

In case we forget windows things tend to get simple with **nfs** network file system.

Also you can try it in "windows way" with **samba**.

etc.

---

### Post by jph989 on 2009-09-18
I guess I should let everyone know that I already have vsftpd installed and running. However I have no problem uninstalling and trying something new..

let me know what you think

JPH

---

