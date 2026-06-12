---
title: "chmod complication.. help??"
date: 2010-10-03
forum: General Help
---

### Post by LinLou on 2010-10-03
Hello,

I have been trying to create a directory named filenames able to be written and read. But each time i am typing on the terminal 

"  chmod 777 ~/filenames "

I get a message " chmod: cannot access `/root/filenames': No such file or directory "

Can some please tell me what am i doing wrong? 

thank you!

---

### Post by cj.surrusco on 2010-10-03
Is the file in your home directory? Because when you use root privileges in a terminal, ~ = home directory of root. So if you want to access a file in your home directory while using root privileges, you would need to make it look like this "chmod 777 /home/USER_NAME/file"

Hope this helps.

---

### Post by andrewthomas on 2010-10-03
> **LinLou said:**
> Hello,

I have been trying to create a directory named filenames able to be written and read. But each time i am typing on the terminal 

"  chmod 777 ~/filenames "

I get a message " chmod: cannot access `/root/filenames': No such file or directory "

Can some please tell me what am i doing wrong? 

thank you!
Have you created the directory?
Use mkdir.

Why are you root?

---

### Post by LinLou on 2010-10-03
Shouldnt i be root?

when i am trying to give those priviledges to the file i am exactly where the file is, so i will not have to type the path as well.. 

for example:
"/home/USER_NAME/NetBeans/Filenames"

and whenever i used " mkdir ~/filenames" it creates a folder not a .txt file.

so i have created the .txt file by right clicking etc.. and then i opened the terminal, i went to the filder that the file is located and i typed "chmod 777 ~/filename".

Is that wrong? :)

Thanks again.

---

### Post by LinLou on 2010-10-03
> **cj.surrusco said:**
> Is the file in your home directory? Because when you use root privileges in a terminal, ~ = home directory of root. So if you want to access a file in your home directory while using root privileges, you would need to make it look like this "chmod 777 /home/USER_NAME/file"

Hope this helps.

I tried this.. i get the same message.. even if i am not root i get the same message.

doesnt work..  :(

---

### Post by efflandt on 2010-10-03
You should not be running as root.

Even if you created the filenames directory in /root, the root directory only has permissions for root (which you should not change), so others would not have access to a subdirectory there.

If you want a public directory that anyone can read/write files to, put it somewhere else in a publicly accessible path.

---

### Post by LinLou on 2010-10-03
> **efflandt said:**
> You should not be running as root.

Even if you created the filenames directory in /root, the root directory only has permissions for root (which you should not change), so others would not have access to a subdirectory there.

If you want a public directory that anyone can read/write files to, put it somewhere else in a publicly accessible path.

Oh my god! it works! :) thank you so much.. 

I have been stuck on this for 2 days.. 

thanks again! :)

---

