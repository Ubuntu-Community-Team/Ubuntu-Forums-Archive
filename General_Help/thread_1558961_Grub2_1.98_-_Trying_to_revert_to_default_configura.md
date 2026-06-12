---
title: "Grub2 1.98 - Trying to revert to default configuration"
date: 2010-08-22
forum: General Help
---

### Post by dopplerPanda on 2010-08-22
I made an error trying to add password protection to Grub2 1.98 in Ubuntu. Now when I try to run the synaptic package manager I get this error message.    > E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem.  E:_cache->open() failed, please report.  When I go into the terminal and run 'sudo dpkg --configure -a', as instructed, I get this.   > Setting up empathy (2.30.2-0ubuntu1) ...  Setting up libk5crypto3 (1.8.1+dfsg-2ubuntu0.2) ...  Processing triggers for python-central ... Setting up grub-pc (1.98-lubuntu7) ... Installation finished. No error reported. Generating grub.cfg ...  And then it hangs...  I know, Stupid me, before I get chastised, I forgot to make a backup of the file before I started on my attempt to add the passwords. After a day of tweaking trying to fix it on my own, I'm sure I'm in more trouble than when I started. BUT, I can still boot so I cant be totally up the creek without a paddle.  Whats the best way to fix this. Would it be easiest to just c/p a copy of grub.d in its default configuration? If so how would I go about this. My grub.cfg wasnt heavily modified to begin with so it would be easy to recreate the helpful changes I have made to it thus far (sans trying to add passwords)   edit: sorry about the formatting in the quotes, It doesent seem to want to display the returns ive entered...

---

### Post by rtimai on 2010-08-23
dopperPanda, 

Here's the Grub2 manual (easier than entering 'info grub' in Terminal.)

> [https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

See the table of Contents. I'm thinking you might revert to GRUB LEGACY, then re-upgrade to GRUB2. BUT... you might wait for a second opinion... Good luck!

---

### Post by dopplerPanda on 2010-08-23
> See the table of Contents. I'm thinking you might revert to GRUB LEGACY, then re-upgrade to GRUB2. BUT... you might wait for a second opinion... Good luck!   Thanks for the suggestion but the directions they have on their website call for using the pakage manager, and since I am prevented from using the package manager until I get a fix, their directions are not going to be of any help.

---

### Post by JBAlaska on 2010-08-23
Before grub you need to fix your package manager, try these:
```
sudo apt-get clean
sudo apt-get autoclean
sudo apt-get autoremove
sudo apt-get check
sudo apt-get -f install
```

If you still can't clear apt.


Last resort:
Open a terminal and type in the following:
```
gksu gedit /var/lib/dpkg/status

```

Search and remove any references to grub-pc, save and rerun:
```
sudo dpkg --configure -a
```

---

### Post by dopplerPanda on 2010-08-23
Hey JBAlaska i tried all of your suggestions but none of them seemed to do the trick, even your measure of last resort ended in the instances of grub-pc repopulating on their own  any other suggestions?

---

