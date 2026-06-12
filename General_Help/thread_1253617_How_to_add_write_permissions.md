---
title: "How to add write permissions?"
date: 2009-08-30
forum: General Help
---

### Post by antdgar on 2009-08-30
hi,

I need full read+write access to /home/rt/

How can I make my user 'antdgar' able to do this forever?

---

### Post by Liolikas on 2009-08-30
[http://catcode.com/teachmod/](http://catcode.com/teachmod/)

Also there is gui way: properties something...ask more if really need maybe other remembers.

---

### Post by credobyte on 2009-08-30
```
sudo chmod -R 600 /home/rt

```

---

### Post by scouser73 on 2009-08-30
Go to **Terminal**, copy & paste this command: **gksudo nautilus**

That will open Terminal as root, navigate to your new drive, **Right Click**, select the **Permissions** tab change the **Owner** drop-down menu to your name, **Folder Access** to **Create & Delete Files**, **File Access** to **Read & Write**, **Group** to your name, **Folder Access** to **Create & Delete Files**, **File Access** to **Read & Write** then click **Apply Permissions To Enclosed Files**.

You will now have full access to your drive.

---

