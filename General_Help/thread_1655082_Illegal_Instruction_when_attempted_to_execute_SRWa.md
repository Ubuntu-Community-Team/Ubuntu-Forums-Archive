---
title: "Illegal Instruction when attempted to execute SRWare Iron"
date: 2010-12-29
forum: General Help
---

### Post by nEoTeChMaN on 2010-12-29
Hi all,

My first attempted to run Xubuntu XFCE 10.10 and love it a lot.

Works well on PIII, 1GB RAM and 60GB HD using Edimax wireless device. All work out of the box.

Anyway, my problem is when I downloaded the latest SRWare Iron browser and attempted to run it. Nothing happens.

This is what I have tried...

./iron

it came back with 'illegal Instruction'

What is wrong?

---

### Post by QLee on 2010-12-29
[QUOTE=nEoTeChMaN]...
Anyway, my problem is when I downloaded the latest SRWare Iron browser and attempted to run it. Nothing happens.
...[/QUOTE]

OK, so if I understand your post correctly, you downloaded a beta of software that has nothing to do with Ubuntu and you decide to post here rather than the SRWare Iron forum.

I don't follow your logic.

---

### Post by nEoTeChMaN on 2010-12-29
It is perfectly logic since I could be using the **wrong Ubuntu** command to execute a file.

Giving a file a permission especially an executable permission is to do with Ubuntu.

Again, I am trying to understand if I have missed a command to allow a program to execute.

Do you understand my perfectly reasonable logic?

---

### Post by tredegar on 2010-12-29
Please tell us what you downloaded and where from.
A link would be useful.

---

### Post by knutschr on 2010-12-29
I am using Ironweb too.
I use to start it by using a file manager, find where i downloaded it, and click on the program Iron.
[http://www.srware.net/en/software_srware_iron.php](http://www.srware.net/en/software_srware_iron.php)

---

### Post by nEoTeChMaN on 2010-12-29
> **knutschr said:**
> I am using Ironweb too.
I use to start it by using a file manager, find where i downloaded it, and click on the program Iron.
[http://www.srware.net/en/software_srware_iron.php](http://www.srware.net/en/software_srware_iron.php)

That is exactly what I did and SRWare comes from SRware site. Where else?

It is version 8.0.555.0 and I have extracted it. I should be able to double-click on the 'iron' file, which is "suppose" to be executable.

It worked flawlessly on Mint Linux 9 and 10, but with Ubuntu or Xubuntu it doesn't.

So again, yes... it is to DO with the Linux operating system.

---

### Post by knutschr on 2010-12-29
Try using a terminal.
cd into the right directory.
./iron there
Look at the output

---

### Post by nEoTeChMaN on 2010-12-29
> **knutschr said:**
> Try using a terminal.
cd into the right directory.
./iron there
Look at the output

That is the exact output I got... 'Illegal Instruction' after typed in ./iron

---

### Post by oldos2er on 2010-12-29
Did you make it executable? **chmod +x iron**

---

### Post by QLee on 2010-12-29
[QUOTE=nEoTeChMaN]...
It worked flawlessly on Mint Linux 9 and 10, but with Ubuntu or Xubuntu it doesn't.[/QUOTE]

Would have been good information to have included with original post.

I'm not familiar with the file manager in a default Xbuntu install, is there a way to check the permissions of a file to verify that it is in fact marked executable? Or maybe from a command line in the directory with, ls -l. Just to verify that your extracted file is marked as it is supposed to be.

[QUOTE=nEoTeChMaN]So again, yes... it is to DO with the Linux operating system.[/QUOTE]

Yes, I hear you. On the other hand, your post sat there for two hours without reply and now there are replies and you didn't even have to wait 24 hours for a bump.

---

### Post by Spyderkid on 2010-12-29
Make sure its executable by going onto properties and clicking the box on the permissions tab.

Make sure you've extracted it if you need to.

double click on the file.



also try to use the repositories if possible :)


...

---

### Post by SRWare on 2010-12-29
I have recompiled it with P3 cflags. It should work on P III now. Just redownload the package.

---

### Post by nEoTeChMaN on 2010-12-29
> **SRWare said:**
> I have recompiled it with P3 cflags. It should work on P III now. Just redownload the package.

Fantastic! It is working beautiful now. Thank you! :popcorn:

Thanks everyone else for their inputs as well.

---

