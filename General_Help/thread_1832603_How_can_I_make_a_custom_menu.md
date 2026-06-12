---
title: "How can I make a custom menu?"
date: 2011-08-25
forum: General Help
---

### Post by GrantStoner on 2011-08-25
I currently have the (useful) tools included in Back|Track installed to my Natty box. Instead of having to open a terminal and navigate to the directory and do a "./foo" for each time I want to use something, I want to build a menu for it instead. I've tried many different combinations, but for the most part - they all result the same way. I navigate to the program in the menu I just created, it opens a terminal and asks for password, and then closes immediately. I've tried with a few different programs thinking maybe just aircrack-ng or skipfish couldn't handle it. Where am I going wrong? How do I keep the terminal open? I've included screenshots as attachments so you can see how I tried to do it. The "run in terminal" dialog is check-marked, but what else am I missing?

---

### Post by GrantStoner on 2011-08-25
Bumpidy bump bump bump. Anyone, anyone? C'mon, no one knows how to make a menu in Kubuntu? Still I'm getting the same results - terminal opens, asks for pw, then closes.

---

### Post by Azdour on 2011-08-26
Hi,

My answer is based on Ubuntu 10.04 Gnome. The launchers there only support simple commands and anything involving the 'cd' command I usually find I have to write a script for and get the launcher to call that script.

---

### Post by Lampi on 2011-08-26
The change directory command is unnecessary, that's what the work path setting is for in the advanced tab. But you'll have to call skipfish with the full path then, since the directory is not part of your path environment.

instead of "su -c" I recommend "kdesudo -c" - it will take better care of file ownership than "su -c"

Last but not least you asked for the konsole terminal to be kept open, this is done by the "noclose" parameter: add --noclose to the terminal options in the advanced tab.

Maybe you also add your username to "run as different user" ,so skipfish will not run with root permissions, thus take better care of file permissions+ownership.

---

### Post by GrantStoner on 2011-08-26
Thanks, I will try what you said. I did, however, I did have skipfish to run as root on purpose. It's in a "/pentest/" directory with root permissions. But I suppose I shall use kdesudo if I'm opening konsole. Thanks again.

---

### Post by GrantStoner on 2011-08-26
> **Azdour said:**
> Hi,

My answer is based on Ubuntu 10.04 Gnome. The launchers there only support simple commands and anything involving the 'cd' command I usually find I have to write a script for and get the launcher to call that script.
I tried to put it in a script and run it that way too - with the same output as previously posted.

---

### Post by GrantStoner on 2011-08-27
I've tried many variations of everything and I'm still getting random hangs and errors. I'm about to Download Back|Track and/or SECmic to see how they do their KDE menus for CLI apps. More interested in the way SECmic does it because it's on a more recent version of Kubuntu and they have a separate pentest menu on the bottom panel.

---

