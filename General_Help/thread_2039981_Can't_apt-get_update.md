---
title: "Can't apt-get update"
date: 2012-08-10
forum: General Help
---

### Post by mjpatey on 2012-08-10
Hi, all-

It's been so long since I've had any trouble with Ubuntu that I can't figure out how to get around this one...

When I try to update everything (sudo apt-get update), I get the usual pings, followed by the following messages:

```
Reading package lists... Done
W: Duplicate sources.list entry http://dl.google.com/linux/chrome/deb/ stable/main amd64 Packages (/var/lib/apt/lists/dl.google.com_linux_chrome_deb_dists_stable_main_binary-amd64_Packages)
W: Duplicate sources.list entry http://dl.google.com/linux/chrome/deb/ stable/main i386 Packages (/var/lib/apt/lists/dl.google.com_linux_chrome_deb_dists_stable_main_binary-i386_Packages)
W: You may want to run apt-get update to correct these problems

```

Any idea how to fix this? I can't find the good old "Software Sources", the Software Center is no help, and peeking at /etc/apt/sources.list, there's no mention of these PPAs anywhere, just the stock Ubuntu sources.

Thanks in advance for any light you can shed!

-Mark

---

### Post by 2F4U on 2012-08-10
This sounds promising:

[http://askubuntu.com/questions/120621/w-duplicate-sources-list-entry-http-archive-ubuntu-com-ubuntu-precise-update](http://askubuntu.com/questions/120621/w-duplicate-sources-list-entry-http-archive-ubuntu-com-ubuntu-precise-update)

---

### Post by plucky on 2012-08-10
Open **Software Updater** and select the **System Settings** button should open **Software Sources**

Good luck

---

### Post by johnathansmith on 2012-08-10
Hi, type ```
sudo editor /etc/apt/sources.list
```, then find the line that's duplicated in you case it should be :
```
W: Duplicate sources.list entry http://dl.google.com/linux/chrome/deb/ stable/main amd64 Packages (/var/lib/apt/lists/dl.google.com_linux_chrome_deb_dists_stable_main_binary-amd64_Packages)
W: Duplicate sources.list entry http://dl.google.com/linux/chrome/deb/ stable/main i386 Packages (/var/lib/apt/lists/dl.google.com_linux_chrome_deb_dists_stable_main_binary-i386_Packages)

```

Delete one of them, depend what release you have. If you using 32bit then delete this one ```
http://dl.google.com/linux/chrome/deb/ stable/main amd64 Packages (/var/lib/apt/lists/dl.google.com_linux_chrome_deb_dists_stable_main_binary-amd64_Packages)
```

---

### Post by cortman on 2012-08-10
If it's not in sources.list, it's likely an individual file in the sources.list.d directory.

---

### Post by smoka on 2012-11-29
I had the same problem, had installed chrome by doing the following:

```
wget -q -O - https://dl-ssl.google.com/linux/linux_signing_key.pub | sudo apt-key add -
sudo sh -c 'echo "deb http://dl.google.com/linux/chrome/deb/ stable main" >> /etc/apt/sources.list.d/google.list'
sudo apt-get update
sudo apt-get install google-chrome-stable
```

After getting the same error I could see that there were 2 files created:

ll /etc/apt/sources.list.d/google*
-rw-r--r-- 1 root root 176 Nov 29 11:27 /etc/apt/sources.list.d/google-chrome.list
-rw-r--r-- 1 root root  55 Nov 29 11:23 /etc/apt/sources.list.d/google.list

Seemed to both contain the same entry:

cat /etc/apt/sources.list.d/google-chrome.list 
[I]### THIS FILE IS AUTOMATICALLY CONFIGURED ###
# You may comment out this entry, but any other modifications may be lost.
deb [http://dl.google.com/linux/chrome/deb/](http://dl.google.com/linux/chrome/deb/) stable main[/I]

cat /etc/apt/sources.list.d/google.list
*deb [http://dl.google.com/linux/chrome/deb/](http://dl.google.com/linux/chrome/deb/) stable main*

Commented out the line as follows and now seems to work okay:
cat /etc/apt/sources.list.d/google-chrome.list 
### THIS FILE IS AUTOMATICALLY CONFIGURED ###
# You may comment out this entry, but any other modifications may be lost.
***#deb [http://dl.google.com/linux/chrome/deb/](http://dl.google.com/linux/chrome/deb/) stable main***

---

