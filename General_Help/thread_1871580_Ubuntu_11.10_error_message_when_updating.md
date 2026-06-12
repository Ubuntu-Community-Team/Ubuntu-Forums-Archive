---
title: "Ubuntu 11.10 error message when updating"
date: 2011-10-29
forum: General Help
---

### Post by Panawe on 2011-10-29
Since upgrading to 11.10 I get this error message whenever I update...

GConf error: Configuration server couldn't be contacted: D-BUS error: Method "Set" with signature "s(ib)" on interface "org.gnome.GConf.Database" doesn't exist

Anyone know what's going on?

---

### Post by garvinrick4 on 2011-10-29
Go into software sources and try changing mirror you are using.
Here is screenshot, click tab on right of "Download from" and change:Here are mirrors to choose from [Mirrors of Ubuntu : Ubuntu]("https://edge.launchpad.net/ubuntu/+archivemirrors")

---

### Post by Panawe on 2011-10-29
> **garvinrick4 said:**
> Go into software sources and try changing mirror you are using.
Here is screenshot, click tab on right of "Download from" and change:Here are mirrors to choose from [Mirrors of Ubuntu : Ubuntu]("https://edge.launchpad.net/ubuntu/+archivemirrors")

I have changed software sources "download from" from "server for united kingdam" to "main server". 
Wait and see I suppose?

---

### Post by garvinrick4 on 2011-10-29
> I have changed software sources "download from" from "server for united kingdam" to "main server". 
Wait and see I suppose?     ```
sudo apt-get update
```all go smooth if not report errors here.

---

### Post by Panawe on 2011-10-29
> **garvinrick4 said:**
> ```
sudo apt-get update
```all go smooth if not report errors here.

Cool, done that and no error massage :)

---

### Post by garvinrick4 on 2011-10-29
> Cool, done that and no error massage
Fine now mark as Solved in upper right of page under Thread Tools so others
with same may benefit. Enjoy your Ubuntu.

---

