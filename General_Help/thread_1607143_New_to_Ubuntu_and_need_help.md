---
title: "New to Ubuntu and need help"
date: 2010-10-27
forum: General Help
---

### Post by Bri4life on 2010-10-27
I have taken the plunge of trying Ubuntu after thinking about it for a while and I have to say I like what I see so far, it is fast and runs smooth.

One thing I am having trouble with is updating drivers or software, I tried to run an app on facebook and I was told I would have to install flash. I have look and found a place to get the driver but I am having trouble downloading it.

when click on the link at Adobe I get the following

Adobe flash plugin

Available from "maverick.partner" source

Click on to use the source (which I did) and I am asked for a password?

How do I get the password to download and install this file?

With thanks

Brian

---

### Post by gradysghost on 2010-10-27
Quick answer:

Install the flash plugin from the repository.  You can do this through the Ubuntu Software Center, searching for "Adobe Flash Plugin" and installing it there.  You're new, so I don't know how comfortable with the terminal you are.  If you're open to using the terminal, you can also run this command there:

```
sudo apt-get install flashplugin-nonfree
```

---

### Post by KaiO on 2010-10-27
As much as possible you should use Ubuntu's own program managers to administer software.
Go to your software center and search for flash.

Or you could install it from a terminal window with:
sudo apt-get install flashplugin-installer

---

### Post by gradysghost on 2010-10-27
Long answer:

Most Linux distributions (there are hundreds, if not thousands, and Ubuntu is only one) use some sort of software management system.  In Linux, software is referred to as "packages".  Each package contains something useful, whether this is just a library of functions that other software can utilize or it's a full application with a graphical user interface.  A good distribution has lots of these packages available in a repository - a huge database of packages on the Internet.

Ubuntu uses a package manager called APT (Advanced Packaging Tool) that manages all of this software for you.  When you install software from the repositories, your computer can later check for updates to that software.  This means that when you install Flash (or anything else) through the command that I posted earlier, through the Ubuntu Software Center, or through other applications like Synaptic (and you can investigate these things on your own time; feel free to experiment), your system can later check for newer versions of these programs and update them all simultaneously.

If you're used to using Windows, you're probably used to seeing Flash create an icon in your system tray (next to the clock) and ask you to update.  Flash does this as well as Adobe Reader and Java and all of the Google products, et cetera.  With Ubuntu and most Linuxes, all of these programs have one single update mechanism, and that is done by using the repositories as decribed in my previous post.

An additional benefit of using the repositories comes in the form of security.  When you download third-party applications from the Internet and install them, you may not know that they're actually safe to install.  When you get programs from the repository, you know they're safe to the extent that the maintainers (for Ubuntu, the maintainers work for Canonical, Inc.) have tested them, which is often quite extensively.

If this is confusing, just ask for clarification.  This is what the community is here for.  Hope you enjoy Ubuntu!

---

