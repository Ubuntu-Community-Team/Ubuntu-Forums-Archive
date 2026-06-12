---
title: "How to access NTFS drives from virtual box"
date: 2010-12-09
forum: General Help
---

### Post by karthick87 on 2010-12-09
Curently i am using lucid.Also I have installed maverick in my virtual box for my testing purposes.In lucid i can see all my NTFS drives but in maverick(which is installed in virtual box)i cant see any of my NTFS partition.Can anybody help me?

---

### Post by sikander3786 on 2010-12-09
You mean to access Host drives from Guest OS?

[http://www.virtualbox.org/manual/ch05.html#vdis](http://www.virtualbox.org/manual/ch05.html#vdis)

---

### Post by karthick87 on 2010-12-09
Yes i want to access host drives from my Guest OS.

---

### Post by karthick87 on 2010-12-09
I have read that post.But i am not sure on how to do it.Can someone help me?

---

### Post by wangsuda on 2010-12-09
You have to tell the virtual machine to "see" the drives. This is simple. First, open VB. Highlight, but do not start, the virtual machine you wish had access to the drives. Second, click on "Machine>Settings>Shared Folders" On the right hand side of the window, there is a file folder icon with a plus sign on it. Click on that icon and add the desired folders. If you want to add more than folders, then:

Click on "Machine>Settings>Storage" and add the desired disks.

I hope this works for you.

---

### Post by Vishnu V on 2010-12-09
For share files in virtual box we need to install guest addition
Devices->Install guest addition 

After installation share the folder you want to use for that
go to settings- >shared folder  select add select path and give a name to that drive say windows
now open terminal in maveric installed in virtual box and use command 

```

sudo mkdir /media/windows
sudo mount -t vboxsf windows /media/windows

```

Now you can access it from /media/windows

---

### Post by karthick87 on 2010-12-09
When i click Guest Additions from devices it just shows a cd drive in my nautilus browser,

[[IMG]http://hosting11.imagecross.com/image-hosting-57/9226Screenshot.png[/IMG]]("http://www.imagecross.com/")
What should i do now?

---

### Post by tajiknomi on 2010-12-09
[SIZE=2]This is self-Explanatory > [/SIZE][http://helpdeskgeek.com/linux-tips/install-virtualbox-guest-additions-in-ubuntu/](http://helpdeskgeek.com/linux-tips/install-virtualbox-guest-additions-in-ubuntu/)

---

### Post by karthick87 on 2010-12-09
Thankyou tajiknomi it worked :) but i cant see them in my nautilus.All the files are present there in /media/windows.

Also in terminal, i got two errors,

```
bash: /etc/bash_completion.d/lvm: line 172: syntax error near unexpected token `newline'
bash: /etc/bash_completion.d/lvm: line 172: `        --metadatacopie'
```

---

### Post by tajiknomi on 2010-12-09
> **karthick87 said:**
> Thankyou tajiknomi it worked :) but i cant see them in my nautilus.All the files are present there in /media/windows.

Also in terminal, i got two errors,

```
bash: /etc/bash_completion.d/lvm: line 172: syntax error near unexpected token `newline'
bash: /etc/bash_completion.d/lvm: line 172: `        --metadatacopie'
```

[SIZE=2]I haven't tried it yet....but you can make a try > Access from nautilus to your /media/windows, right-click on desire share-folder and select "***make-a-link***" and drag it to desktop[/SIZE], [SIZE=2]i am not sure, but you can try it[/SIZE]...

---

### Post by karthick87 on 2010-12-11
Thank you :)

---

