---
title: "Permissions problem"
date: 2010-06-21
forum: General Help
---

### Post by knetcozd on 2010-06-21
Hi guys , i am using Xampp on ubuntu 10.04 and i have set my document root to a folder in my home directory for ease of use with netbeans . There are several times where i have to manually go and change the permission to 755. If you just place a file in the directory it does not default to 755 , seems odd since the document root folder is in my home directory.

chmod works fine but i was wondering is their a way to make all files or folders added to my document root to default to 755 ?

---

### Post by Smart Viking on 2010-06-21
Hi, the "/home" directory, is owned by root, and that is the way it should be. The folder "/home/<username>" however, is yours, and that is where you should put your files.

So since i can't tell which of those directories you are talking about, if it is your "/home" folder, i would not recommend using it as a place to store your files. Of it is your "/home/<username>" folder however you are talking about, then something is obviously wrong. 

So, the "/home" folder is not made for storing files and i don't recommend doing it. Use the "/home/<username>" directory instead, unless i have misunderstood something. :)

---

### Post by knetcozd on 2010-06-22
i am talking about /home/<username>/ - i kinda figured out why this permission problem occurred in the first place , i named the file ".docroot"  purely so that it is hidden from my normal day to day folder view. I think this is what caused the problem in the first place but i am not 100% sure - gonna change it and see what happens  , wonder why i didn't think of this before ](*,)

---

