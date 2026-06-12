---
title: "Easy way to unrar multiple part files?"
date: 2011-07-12
forum: General Help
---

### Post by d0nut on 2011-07-12
Can anyone tell me what to do to unrar  .rar files in ubuntu?  There are multiple parts (i.e. filepart1.rar, filepart2.rar, filepart3.rar,)  How would i successfully unrar these like i used to in windows so that the intended file im unzipping works?  Thank you.

---

### Post by mikenev on 2011-07-12
I usually use the unrar command from the terminal. You may need to install it with 'sudo apt-get install unrar'.

After that you just 'unrar -x filepart1.rar' It will usually detect if it's a multi-file archive and move on to the next file.

---

### Post by d0nut on 2011-07-12
Thanks Mike, I will give this a try!

---

### Post by seawolf167 on 2011-07-12
I just want to add that I've had problems with multipart files created in Windows environments (nothing 100% reproducible though), and have been using 7z for this purpose for a while now.

```
sudo apt-get install p7zip-full
```

---

### Post by d0nut on 2011-07-13
> **seawolf167 said:**
> I just want to add that I've had problems with multipart files created in Windows environments (nothing 100% reproducible though), and have been using 7z for this purpose for a while now.

```
sudo apt-get install p7zip-full
```

Ok thanks but how do i "run" the 7zip program?  Sorry, I'm used to windows still.

---

### Post by seawolf167 on 2011-07-13
> **d0nut said:**
> Ok thanks but how do i "run" the 7zip program?  Sorry, I'm used to windows still.

Here is a [quick guide ]("http://www.thegeekstuff.com/2010/04/7z-7zip-7za-file-compression/")to some of the commands. Note that p7zip supports formats of zip, cab, arj, gzip, bzip2, tar, cpio, rpm and deb (not just the 7z extension listed in the link)

---

### Post by mogdad on 2011-07-24
May or may not be relevant but I had lots of problems with unrar until I found this post [_(link_)]("http://ubuntuforums.org/showpost.php?p=7209121&postcount=2").  I uninstalled unrar-free and installed unrar and since then everything has worked as it should.

---

