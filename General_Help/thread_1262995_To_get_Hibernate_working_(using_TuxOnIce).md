---
title: "To get Hibernate working (using TuxOnIce)"
date: 2009-09-10
forum: General Help
---

### Post by james.exe on 2009-09-10
Hi, I'm an Ubuntu newbie. I've been trying to get UNR9.04 running flawlessly on my AAOZA3 but it's all just too complicated for me. The only Aspire One guide I could find assumes that the reader has programming knowledge which I lack. 

**"To get Hibernate working (using TuxOnIce)**

[LIST=1]
[*]Make sure that you have a swap partition set up (it doesn't have to be as big as 2xRAM) 
[*]Add the [TuxOnIce]("https://help.ubuntu.com/community/TuxOnIce") PPA repositories (and don't forget to add the auth key), which you can find here: [https://launchpad.net/~tuxonice/+archive/ppa]("https://launchpad.net/%7Etuxonice/+archive/ppa") 
[*]Follow the instructions here: [http://lists.tuxonice.net/lurker/message/20090409.181125.d20e0bbe.en.html](http://lists.tuxonice.net/lurker/message/20090409.181125.d20e0bbe.en.html) 
[/LIST]
After that hibernate should work correctly!"


Quite frankly, I haven't the slightest idea how to set up a swap partition and add the TuxOnIce PPA repositories. I also took a look at the instructions link and that only lost me even more. I have withstood about a month of no hibernate function and I can't take it anymore. The exact problem with my hibernate is that my computer won't resume after it has been hibernating. Instead, I get a black screen with a green bar on top and the only option I have is to hold down the power button until it turns off. I think I'm causing my computer a great deal of damage by doing this :P


[B]Can anyone _please_ help?
[/B]

---

### Post by P4man on 2009-09-10
Disclaimer: I dont know tux on ice, i got no idea if this is the best plan or not, but find out..

1. swap
You probably dont have to do anything, a default install will create a swap partition. But let's check nonetheless, and see if its big enough. 

Go to System > administration > System montitor.

Click on the last tab, file systems (actually hoping jaunty has that :s ) and see if there is a partition with type "swap" and tell us how big it is. If you can't see a tab called "file systems", then check in "resources", below the middle graph you'll see "swap" and then some numbers. Eg "150Mb, 4% of **3.6GiB**". Make sure the size is bigger than the amount of RAM you have.

2. To add the repositories:

Open System > Administration > Software Sources.

Click the Third Party Software tab.

Click the Add button.

Paste this line in the textbox:

```
deb http://ppa.launchpad.net/tuxonice/ppa/ubuntu jaunty main 
```

click the Add Source button.

When prompted, reload the software sources information. Don't worry if you see a warning about unverified software sources; we're going to fix that next.

Now Ubuntu knows about the PPA. It also needs to know how to check the software hasn't been tampered with since Launchpad built it.

Open a terminal (applications > accessories > terminal)

Copy this line:

```
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys DEC8FAAC  
```

(you can copy/paste in a terminal through edit/paste or by pressing shift+control+v)

Now tell Ubuntu to re-load the details of each software archive it knows about. still in the terminal type or copy paste:
```

sudo apt-get update
```

And install the app:

```
sudo apt-get install tuxonice-userui
```

**edit:** corrected last command

---

### Post by james.exe on 2009-09-10
When I check on the system monitor, it just displays one partition
**/dev/sda1**
Type:ext3
Total:141.1GiB
Free:137.5GiB
Available:130.4GiB
Used:3.5GiB

I downloaded the GParted partition editor and it shows me 3 partitions:
/dev/sda1 ext3 142.32GiB
/dev/sda2 extended 5.73GiB
/dev/sda5 linux-swap 5.73GiB

---

### Post by P4man on 2009-09-10
> **james.exe said:**
> When I check on the system monitor, it just displays one partition
**/dev/sda1**
Type:ext3
Total:141.1GiB
Free:137.5GiB
Available:130.4GiB
Used:3.5GiB

I downloaded the GParted partition editor and it shows me 3 partitions:
/dev/sda1 ext3 142.32GiB
/dev/sda2 extended 5.73GiB
/dev/sda5 linux-swap 5.73GiB

Doh, turns out the system monitor partition thing doesnt show swap heh. My bad; I just wanted to save you from the command line :D. But you got swap and unless you get 6+ GB of RAM, you're good to go.

---

### Post by james.exe on 2009-09-10
**When prompted, reload the software sources information.**
I followed the steps exactly as explained but it's not prompting me to reload the software sources information. I closed software sources and just went ahead with the next steps.

james@james-netbook:~$ sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys DEC8FAAC
Executing: gpg --ignore-time-conflict --no-options --no-default-keyring --secret-keyring /etc/apt/secring.gpg --trustdb-name /etc/apt/trustdb.gpg --keyring /etc/apt/trusted.gpg --keyserver keyserver.ubuntu.com --recv-keys DEC8FAAC
gpg: requesting key DEC8FAAC from hkp server keyserver.ubuntu.com
gpg: key DEC8FAAC: "Launchpad PPA for TuxOnIce" not changed
gpg: Total number processed: 1
gpg:              unchanged: 1
james@james-netbook:~$ sudo apt-get update
E: Could not get lock /var/lib/apt/lists/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the list directory

this is what i get in the terminal

---

### Post by james.exe on 2009-09-10
How would I go about resizing my swap partition to be larger than 6gigs?
I tried using GParted but all of the options seem to be grayed out for some reason.

---

### Post by james.exe on 2009-09-10
bump

---

### Post by james.exe on 2009-09-10
bump

---

### Post by P4man on 2009-09-11
Please don't bump every 2 hours, its considered rude.

> **james.exe said:**
> **When prompted, reload the software sources information.**
I followed the steps exactly as explained but it's not prompting me to reload the software sources information. I closed software sources and just went ahead with the next steps.

IT should have asked you when clicking the close button, but we'll update them later anyway.

> james@james-netbook:~$ sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys DEC8FAAC
Executing: gpg --ignore-time-conflict --no-options --no-default-keyring --secret-keyring /etc/apt/secring.gpg --trustdb-name /etc/apt/trustdb.gpg --keyring /etc/apt/trusted.gpg --keyserver keyserver.ubuntu.com --recv-keys DEC8FAAC
gpg: requesting key DEC8FAAC from hkp server keyserver.ubuntu.com
gpg: key DEC8FAAC: "Launchpad PPA for TuxOnIce" not changed
gpg: Total number processed: 1
gpg:              unchanged: 1
james@james-netbook:~$ sudo apt-get update
E: Could not get lock /var/lib/apt/lists/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the list directory

this is what i get in the terminal

That message means you have another copy of apt running.Perhaps synaptic package manager, or the add/remove programs or software sources. Just close all other windows and try again.
> 
How would I go about resizing my swap partition to be larger than 6gigs?
I tried using GParted but all of the options seem to be grayed out for some reason

Why would you? 6 GBs is overkill already, the only reason you may need that much, is for hibernating (assuming you have 4 GB Ram ?).

Anyway, if you insist, boot from a live cd, right click the swap partition in gparted and swapoff. Then resize your partitions. You may need to resize the extended (light blue) partition first, if your swap is inside the extneded partition (an extended partition is like a container).

---

### Post by james.exe on 2009-09-11
W: GPG error: [http://packages.medibuntu.org](http://packages.medibuntu.org) jaunty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2EBC26B60C5A2783
W: Failed to fetch [http://archive.canonical.com/ubuntu/dists/dapper/Release](http://archive.canonical.com/ubuntu/dists/dapper/Release)  Unable to find expected entry  commercial/binary-i386/Packages in Meta-index file (malformed Release file?)

E: Some index files failed to download, they have been ignored, or old ones used instead.



Thats what I get after I run
sudo apt-get update 
in the terminal. is that normal? is there anything i can do to fix it or work around that?

---

### Post by james.exe on 2009-09-12
bump

---

### Post by P4man on 2009-09-12
First warning is ok, from my previous post ". Don't worry if you see a warning about unverified software sources; we're going to fix that next."

You also seem to have  ubuntu dapper (6.06) repositories in your sources? LOL. Its not really a problem, but you probably want to remove those Go back to software sources, third party, and find the deb line with "http://archive.canonical.com" for dapper. Remove it. Dapper is no longer supported, those repo's no longer work.

---

### Post by james.exe on 2009-09-13
I did everything word for word and ran: **sudo shutdown -r now **in the terminal and still no hibernate :(
I even removed Dapper. What can be wrong?

---

### Post by P4man on 2009-09-13
"sudo shutdown -r now" is a command to reboot the machine, not to hibernate it. Why did you try that? At least I hope it rebooted?

Like I said earlier, i don't know tux on ice, or how to use it, I just helped you with the questions you had. But a quick on their website shows you should do something very different. Try this:

```
sudo /usr/local/sbin/hibernate 
```

If that fails, have you tried  uswusp yet?

If not, have a look here:
[https://help.ubuntu.com/community/PowerManagement/Hiberate#uswsusp](https://help.ubuntu.com/community/PowerManagement/Hiberate#uswsusp)


The short version, try:

```
sudo aptitude install uswsusp
```

and then

```
sudo s2disk
```

---

### Post by james.exe on 2009-09-13
I figured that maybe I had to reboot for the changes to take effect. At first, I thought the issue was finally resolved, but I realized that the computer was turning back on as I opened it and not when I pressed the power button. I thought that maybe the computer wasn't hibernating and the screen was just powering off. When I clicked on the home button, all of the icons and names were blanked out messed up. I shut down my system and now the desktop doesn't even load. My computer is pretty much unusable now... I'll post pictures up soon.

---

### Post by james.exe on 2009-09-13
[http://i31.tinypic.com/ei17o9.jpg](http://i31.tinypic.com/ei17o9.jpg)
It's as if my computer is just a terminal now. I trust that there is some way to reverse this effect?
I type in my login/password and still no desktop.

---

### Post by P4man on 2009-09-14
try

sudo /etc/init.d/gdm restart

to get a gui again.

the uswusp thing, there is no real need to reverse it, if you dont use it, it shouldnt interfer (although you can uninstall it with "sudo apt-get remove uswsusp"). As for tuxonice, I have no idea. It seems more complicated to install and remove (and btw, the howto you were following was for ubuntu intrepid)

---

