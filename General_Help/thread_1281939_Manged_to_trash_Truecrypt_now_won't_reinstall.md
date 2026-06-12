---
title: "Manged to trash Truecrypt now won't reinstall"
date: 2009-10-03
forum: General Help
---

### Post by Steve00 on 2009-10-03
I ran Computer Janitor under System (Ubuntu 9.04). Afterwards, I discovered that Truecrypt was gone. I downloaded it again from the Truecrypt website. Before, I could double-click on the file. Now, when I double-click it opens in archive manager. Right click only finds Archive Manger and Archive Mounter as choices. Open With does not provide any choices for installing a program.

Now what?

Thanks!

--Steve

---

### Post by credobyte on 2009-10-03
Hmm ..

```
sudo chmod +x truecrypt_executable
```
** Adjust the file name & path to whatever you have there ..

---

### Post by Steve00 on 2009-10-03
No effect. The filename is truecrypt-6.2a-ubuntu-x86.tar.gz 

Originally, I could double click on that file name and it would install with some kind of package manger (which I now cannot remember) or I could right click and chose to install on that same package manager. The package manager appeared to disappear along with my original truecrypt.

---

### Post by credobyte on 2009-10-03
No, it wouldn't. Extract it and let us know what you have there ( don't remember what was inside it .. haven't used it for quite a long time ).

---

### Post by Steve00 on 2009-10-03
I tried that as well. No luck. The extracted file name is:

truecrypt-6.2a-setup-ubuntu-x86

file properties indicates it is a "shell script (application/x-shellscript)"

Thanks!

--Steve

---

### Post by credobyte on 2009-10-03
> **Steve00 said:**
> I tried that as well. No luck. The extracted file name is:

truecrypt-6.2a-setup-ubuntu-x86

file properties indicates it is a "shell script (application/x-shellscript)"

Thanks!

--Steve

Try this:
```
sudo chmod +x truecrypt-6.2a-setup-ubuntu-x86.sh
./truecrypt-6.2a-setup-ubuntu-x86.sh
```

---

### Post by Steve00 on 2009-10-03
Once again, no luck. Here is what I get:

comp@comp:~/Desktop$ sudo chmod +x truecrypt-6.2a-setup-ubuntu-x86.sh ./truecrypt-6.2a-setup-ubuntu-x86.sh
chmod: cannot access `truecrypt-6.2a-setup-ubuntu-x86.sh': No such file or directory

---

### Post by credobyte on 2009-10-03
> **Steve00 said:**
> Once again, no luck. Here is what I get:

comp@comp:~/Desktop$ sudo chmod +x truecrypt-6.2a-setup-ubuntu-x86.sh ./truecrypt-6.2a-setup-ubuntu-x86.sh
chmod: cannot access `truecrypt-6.2a-setup-ubuntu-x86.sh': No such file or directory

Post the output of the following command.
```
ls -al $HOME/Desktop
```

---

### Post by Steve00 on 2009-10-03
Thanks for your help! Here are the results:

comp@comp:~/Desktop$ ls -al $HOME/Desktop
total 1590452
drwxr-xr-x  3 comp comp      4096 2009-10-03 19:21 .
drwxr-xr-x 42 comp comp      4096 2009-10-03 19:21 ..
-rwxrwxrwx  1 comp comp  52328448 2009-09-29 14:44 dsl-4.4.10.iso
-rwxrwxrwx  1 comp comp    248655 2009-05-06 22:23 JDarkRoom.jar
drwxr-xr-x  2 comp comp      4096 2009-09-28 22:01 My_Virtual_Machine
-rw-r--r--  1 comp comp      4277 2009-09-28 20:16 My_Virtual_Machine.zip
-rwxrwxrwx  1 comp comp   2169915 2009-09-26 17:34 SetupImgBurn_2.5.0.0.exe
-rwxr-xr-x  1 comp comp   2523567 2009-06-15 04:39 truecrypt-6.2a-setup-ubuntu-x86
-rw-r--r--  1 comp comp   2496781 2009-10-03 18:23 truecrypt-6.2a-ubuntu-x86.tar.gz
-rw-r--r--  1 comp comp 733882368 2009-10-02 22:34 ubuntu-8.04.3-alternate-i386.iso
-rw-r--r--  1 comp comp 732239872 2009-10-02 22:35 ubuntu-8.04.3-desktop-i386.iso
-rw-r--r--  1 comp comp 101075736 2009-09-28 20:34 VMware-Player-2.5.3-185404.i386.bundle

---

### Post by credobyte on 2009-10-03
My last shot ( off to bed ):
```
cd $HOME/Desktop && chmod +x truecrypt-6.2a-setup-ubuntu-x86 && ./truecrypt-6.2a-setup-ubuntu-x86

```

---

### Post by Steve00 on 2009-10-03
That did it! Thanks!

Now, why did the Package Installer disappear from my 'open with' choices when I right clicked on the file? I nosed around on the Synaptic Package Manager and could not find anything. Obviously, its in there somewhere as the last command ran the Package Installer wizard.

--Steve

---

### Post by solitaire on 2009-10-03
The Package installer is looking for *.deb files (Debian installer file) and you had a "tar.gz" (which is a compressed file). The contect menu seen that it was a compressed file and gave you the Archive options. the Package installer will be there for *.deb files ^_^

---

### Post by Steve00 on 2009-10-03
Got it! Thanks!

--Steve

---

