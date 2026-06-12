---
title: "how to change permissions of a folder that I'm not the owner of"
date: 2010-03-23
forum: General Help
---

### Post by unpresedented on 2010-03-23
hi,
I notice something weird on Linux world (i'm not comer) why there are a lot of files and folders that prevent me from creating content in ?!! i right click it and choose properties, I notice in the permissions tab that something like : "you are not the owner ... "
in my case, I want to create files and folders inside : /var/www folder but it prevents me from doing so ... I used the command "chmod 777 www" and hit enter in the terminal, and refreshed the folder but nothing changed ...
can anyone help me to change that folder's permissions so that I can create content (files and folders) in it ... ?

plus, I want to know why ubuntu behaves like this ? (tell me that I'm not the owner; although I'm the admin and the only user on machine)
thank you so much in advance ..

---

### Post by MelDJ on 2010-03-23
in linux, the adminstrator is root. root can do anything. like spiderman, root has great power and great responsibility. hence, running as root and not knowing what you are doing can damage your OS.

to change permission, go to apps-accesories-terminal. 
there type:
```
gksu nautilus
```a window will open up. navigate to the folder and right click it and select properties. 
under the permissions tab, change the owner to your username
(might work)

---

### Post by philinux on 2010-03-23
> **unpresedented said:**
> hi,
I notice something weird on Linux world (i'm not comer) why there are a lot of files and folders that prevent me from creating content in ?!! i right click it and choose properties, I notice in the permissions tab that something like : "you are not the owner ... "
in my case, I want to create files and folders inside : /var/www folder but it prevents me from doing so ... I used the command "chmod 777 www" and hit enter in the terminal, and refreshed the folder but nothing changed ...
can anyone help me to change that folder's permissions so that I can create content (files and folders) in it ... ?

plus, I want to know why ubuntu behaves like this ? (tell me that I'm not the owner; although I'm the admin and the only user on machine)
thank you so much in advance ..

Ubuntu behaves like this for security.
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

I'm not familiar with the /var/www folder. Someone else may chime in.

However there is plenty of info on this.
[http://www.google.co.uk/search?q=ubuntu+%2Fvar%2Fwww&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:official&client=firefox-a](http://www.google.co.uk/search?q=ubuntu+%2Fvar%2Fwww&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:official&client=firefox-a)

---

### Post by philinux on 2010-03-23
> **MelDJ said:**
> 
```
sudo nautilus
```



Should be gksudo or gksu nautilus

[http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

---

### Post by scouser73 on 2010-03-23
> **unpresedented said:**
> hi,
I notice something weird on Linux world (i'm not comer) why there are a lot of files and folders that prevent me from creating content in ?!! i right click it and choose properties, I notice in the permissions tab that something like : "you are not the owner ... "
in my case, I want to create files and folders inside : /var/www folder but it prevents me from doing so ... I used the command "chmod 777 www" and hit enter in the terminal, and refreshed the folder but nothing changed ...
can anyone help me to change that folder's permissions so that I can create content (files and folders) in it ... ?

plus, I want to know why ubuntu behaves like this ? (tell me that I'm not the owner; although I'm the admin and the only user on machine)
thank you so much in advance ..

**1** - Go to **Terminal**, copy & paste this command: **gksudo nautilus** that will open Terminal as root

**2** - Navigate to your  folder/file/drive, **Right Click**, select the **Permissions** tab 

**3** - Change the **Owner** drop-down menu to your name, then change **Folder Access** to **Create & Delete Files**, then **File Access** to **Read & Write**, then **Group** to your name, **Folder Access** to **Create & Delete Files**, **File Access** to **Read & Write** then click **Apply Permissions To Enclosed Files**.

You will now have full access to your folder/file/drive.

---

### Post by unpresedented on 2010-03-24
thank you for your replies .. yes it worked .. I can now change the directory permissions using the GUI, but is it going to be recursive ?

---

### Post by eksasol on 2010-03-24
Look at the bottom of Permission window, there should be a button "Apply Permissions to Enclosed Files".

Ps. I think it should be "chmod 777 /var/www", that's why nothing happened. I recommend 755 though, but if you want to know what the numbers does, here is a chmod calculator: [http://www.classical-webdesigns.co.uk/resources/whatchmod.html](http://www.classical-webdesigns.co.uk/resources/whatchmod.html)

---

### Post by Aped on 2010-03-24
If you don't want to fool with permissions, making your system less safe, you can just 'sudo -i' in order to modify things and then 'exit' out of root terminal mode afterwards. Little more complex but kind of worth it. 

Or 'sudo chown' it to yourself, so you're the owner. 

Also sudo nautilus should do it, I don't think gksudo is necessary?

---

### Post by unpresedented on 2010-03-24
> **eksasol said:**
> Look at the bottom of Permission window, there should be a button "Apply Permissions to Enclosed Files".

Ps. I think it should be "chmod 777 /var/www", that's why nothing happened. I recommend 755 though, but if you want to know what the numbers does, here is a chmod calculator: [http://www.classical-webdesigns.co.uk/resources/whatchmod.html](http://www.classical-webdesigns.co.uk/resources/whatchmod.html)
thank you for this cool reply

---

