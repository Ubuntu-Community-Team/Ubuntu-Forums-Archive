---
title: "Thunderbird 3"
date: 2009-12-21
forum: General Help
---

### Post by nirkir on 2009-12-21
Hi,

I'm trying to use thunderbird3. I managed to install the version downloaded from mozilla website but now I can't install traybiff add on.

Any clue on one of the following?
1) how can I install traybiff without going through synaptic (it has dependency on thunderbird2)
2) when would thunderbird3 packages will be available in Ubuntu

BTW I'm using v 9.1 (64 bit although TB is 32 bit, I use ia_32)

I don't want to add ppa - I want a stable version :-)

Thanks

---

### Post by scouser73 on 2009-12-21
Download the **.tar.bz2** file from

[[COLOR="Red"]**Mozilla Messaging: Thunderbird 3**[/COLOR]]("http://en-gb.www.mozillamessaging.com/en-GB/thunderbird/")

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

### Post by nirkir on 2009-12-21
As I mentioned in my original post, I was able to install TB3. 

The problem I'm having is with traybiff add-on, which is available through synaptic (but not on Mozilla website). Installing from synaptic would force installation (due to it dependency on) TB 2. 

I was wondering whether I can install this without TB2 (e.g. instruct synaptic to ignore dependencies).

---

### Post by michael37 on 2009-12-21
I doubt that what you are trying to do will work at all.  Traybiff for your 64-bit system is 64-bit code for Thunderbird 2.  You are using 32-bit Thunderbird 3.  Even if you manage to download traybiff, it won't work with your Thunderbird.

---

