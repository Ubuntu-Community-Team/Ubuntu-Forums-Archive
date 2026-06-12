---
title: "Thunderbird 3 menu display + memory"
date: 2010-05-02
forum: General Help
---

### Post by Greenroomman on 2010-05-02
I've upgraded to Ubuntu 10.04 and everything is working fine... except Thunderbird 3!
It is super slow (memory leak?) and the majority of the submenus dont appear (as well as any pop-up boxes' buttons). I've tried to google, but no luck. Please help as I'm stuck....
Thanks in advance,

---

### Post by Greenroomman on 2010-05-02
Took a screenshot of thunderbird. Have a look at toolbar (or lack of...)

---

### Post by scouser73 on 2010-05-02
I've seen this previously on my PC, did you install Thunderbird through Synaptic Package Manager?

---

### Post by Greenroomman on 2010-05-02
It happened after Ubuntu upgrade. I have re-installed it, but no luck.

---

### Post by scouser73 on 2010-05-02
Did you reinstall it via Synaptic Package Manager or did you download the file from the Thunderbird website?

---

### Post by Greenroomman on 2010-05-02
I used Synaptic...

---

### Post by scouser73 on 2010-05-02
Go to Synaptic Package Manager, search for and remove Thunderbird then follow these instructions.

Download the **.tar.bz2** file from

[[COLOR="Red"]**Mozilla Messaging: Thunderbird 3.04**[/COLOR]]("http://www.mozillamessaging.com/en-US/thunderbird/all.html")


**1** - Extract the **.tar.bz2** file

**2** - Enter **gksudo nautilus** in terminal

**3** - Go to the folder **/opt**

**4** - Copy & paste the Thunderbird file that you extracted to **/opt**

**5 -** Enter these commands into **Terminal** > **sudo -i**

*Enter your password if asked.*

> **cd /opt**
> **chown -R username filename**

[COLOR="Red"]**Obviously the username refers to you, and the filename to the file**[/COLOR]

**6** - Go to **System > Preferences > Main Menu**

**7** - In Main Menu, click on **New Item**

**8** - In the **Name** field enter **Mozilla Thunderbird Mail/News**

**9** - In the **Command** field enter **/opt/thunderbird/thunderbird**

**10** - In the **Comment** field enter **Mozilla Thunderbird Mail/News**

[[IMG]http://img121.imageshack.us/img121/7329/screenshot2c.png[/IMG]](http://img121.imageshack.us/img121/7329/screenshot2c.png/)

---

### Post by Greenroomman on 2010-05-02
Solved it... uninstall & re-installed using the tar.gz file from website. It works 100%.

---

### Post by scouser73 on 2010-05-02
Nice one, glad you've sorted it. Can you please mark this as being solved now by using the thread tools.

---

### Post by mscir on 2010-07-17
Thank you very much for the clear and thorough instructions, that worked perfectly on my Lucid.

---

