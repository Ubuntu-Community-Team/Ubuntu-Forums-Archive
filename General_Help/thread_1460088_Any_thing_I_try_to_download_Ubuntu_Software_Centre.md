---
title: "Any thing I try to download Ubuntu Software Centre  centre says &quot;Not available in the"
date: 2010-04-22
forum: General Help
---

### Post by aydee on 2010-04-22
[SIZE=2]Anything I try to download Ubuntu Software Centre  centre says "Not available in the curent data" I get this when I go to any software download, ex. Get Free Software >>> Accessories >>> 7zip and I get:[/SIZE]

[SIZE=5]7zip
[SIZE=2][B]not available in current data
[/B]licence: open
price free


canonical does not....
[/SIZE][/SIZE]

---

### Post by Dragonbite on 2010-04-22
It means your repository listing has not been updated.

You can go into **System **> **Update Manager** and click **Check **(then put in your sudo password).

You can also update it in **Synaptic**, also located under the System menu.

If you prefer the terminal, then you need to type ```
sudo apt-get update
```

That should work.

I am hoping that this is added to the Software Center in Lucid if they ever hope to replace Synaptic with it.


Oh, and depending on what this program is, it may be located in a specific repository.  From the [_http://packages.ubuntu.com_]("http://packages.ubuntu.com") I see it is in the [**[COLOR="Red"]universe[/COLOR]**] repository which you should have already available.

If you refresh the repository information and it is still not there, then look under **System** > **Software Sources** and make sure the **universal** repository is selected.

---

### Post by aydee on 2010-04-22
thanks it could be a wile as I have 3H 14M 13S of download time.

---

### Post by 3rdalbum on 2010-04-22
> **aydee said:**
> thanks it could be a wile as I have 3H 14M 13S of download time.

It certainly shouldn't take more than a couple of minutes to get the package list; are you sure you did "sudo apt-get update" and not "sudo apt-get upgrade"? The latter will upgrade the packages on your system to their latest versions.

Also you should note that 7zip is just a backend on Linux - it provides the ability to File Roller (Archive Manager) to deal with 7z archives. It's NOT like it is on Windows.

---

### Post by aydee on 2010-04-22
I am using the update manager and it has 259 files on slow internet(it also droped down to 1h pretty quickly too) Also 7zip was the first thing I clicked, I don't actually intend on downloading it. Thanks for the help though

---

### Post by aydee on 2010-04-22
thank you all it works!!!!

---

### Post by Dragonbite on 2010-04-22
> **aydee said:**
> thank you all it works!!!!

Great to hear!

One thing, can you mark the thread as [SOLVED]?  It just keeps things clean, and helpful in case anybody else comes along with a similar issue.

---

### Post by skotu on 2010-05-01
I created a USB Startup disk using the 9.10 live cd. All software showed up as "Not available in current data".

> **Dragonbite said:**
> 
If you prefer the terminal, then you need to type ```
sudo apt-get update
```That should work.

The sources were updated but still same problem.
> **Dragonbite said:**
> 
If you refresh the repository information and it is still not there, then look under **System** > **Software Sources** and make sure the **universal** repository is selected.
That worked for me!

---

