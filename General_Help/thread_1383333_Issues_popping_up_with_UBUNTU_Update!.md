---
title: "Issues popping up with UBUNTU Update!?"
date: 2010-01-17
forum: General Help
---

### Post by Saurabhdua on 2010-01-17
Hi Folks!;)

Please refer to the attached screenshots & help me determine the exact reason behind the Update failure & that RED Notification besides N/W Icon!?

Also, have a sneak peek at::

[http://ubuntuforums.org/showthread.php?t=1377254]("http://ubuntuforums.org/showthread.php?t=1377254")

...*which **could** be probable cause of the current issue..??*?:(

Help me decipher & alleviate this misery(now growing manifolds with each passing day).):P):P):P

---

### Post by jamesisin on 2010-01-17
Did you run sudo dpkg --configure -a in a terminal?

---

### Post by Saurabhdua on 2010-01-17
Hello Folks!

I seem to lose battle ground forever..since I encounter 2 more Error messages,albeit similar looking..

Check out:::What Iam able to gather is, something is surely broken somewhere BUT where...I don know?

Take me through OR else...I'll say a FINAL GOODBYE to Ubuntu..!!!

---

### Post by jamesisin on 2010-01-17
After you run the command in the other thread I posted for your benefit, run sudo apt-get -f install and you should be back in order.

---

### Post by Saurabhdua on 2010-01-18
This is what I get in return----ONLY Cursor blinking for just nothing!


saurabhdua@saurabhdua-desktop:~$ sudo dpkg --configure -a
[sudo] password for saurabhdua: 
saurabhdua@saurabhdua-desktop:~$ sudo dpkg --configure -a
saurabhdua@saurabhdua-desktop:~$

---

### Post by Saurabhdua on 2010-01-18
Hi There..again!

What Iam able to get over here is "Super Cows"...! These are already found in large Nos. on the Streets of India..so nothing SPECIAL over here..

saurabhdua@saurabhdua-desktop:~$ sudo apt-get -f
[sudo] password for saurabhdua: 
apt 0.7.20.2ubuntu6 for i386 compiled on Apr 17 2009 04:25:29
Usage: apt-get [options] command
       apt-get [options] install|remove pkg1 [pkg2 ...]
       apt-get [options] source pkg1 [pkg2 ...]

apt-get is a simple command line interface for downloading and
installing packages. The most frequently used commands are update
and install.

Commands:
   update - Retrieve new lists of packages
   upgrade - Perform an upgrade
   install - Install new packages (pkg is libc6 not libc6.deb)
   remove - Remove packages
   autoremove - Remove automatically all unused packages
   purge - Remove packages and config files
   source - Download source archives
   build-dep - Configure build-dependencies for source packages
   dist-upgrade - Distribution upgrade, see apt-get(8)
   dselect-upgrade - Follow dselect selections
   clean - Erase downloaded archive files
   autoclean - Erase old downloaded archive files
   check - Verify that there are no broken dependencies

---

### Post by sliketymo on 2010-01-18
Good Bye!

---

### Post by warfacegod on 2010-01-18
Go to: System> Admin.> Synaptic> Edit> Fix Broken Packages

---

### Post by bvanaerde on 2010-01-18
> **Saurabhdua said:**
> Take me through OR else...I'll say a FINAL GOODBYE to Ubuntu..!!!
You really expect to get any help at all, after posting something like this? Kudos to those who still want help you, but I'm sure a lot of people here don't think its worth it anymore.

---

### Post by timgood on 2010-01-18
Have you installed any external packages (not in the repositories) such as Adobe Air?

---

### Post by 3rdalbum on 2010-01-18
Your solution is here:

[http://www.lmgtfy.com/?q=%22broken+package+on+your+system!%22]("http://www.lmgtfy.com/?q=%22broken+package+on+your+system!%22")

---

### Post by john newbuntu on 2010-01-18
Now that you have typed the configure command, try
```
sudo apt-get update
```
twice.
Then, as the other post suggests, type 
```
sudo apt-get -f install
```
to fix any broken dependencies.  Follow this up with a final:
sudo apt-get update

---

### Post by terrapin893 on 2010-01-18
The great thing about open source is that you haven't paid anything for this operating system . . . . thusly you are not entitled to anything.  If you are looking for a place to feel entitled I hear Microsoft would take you in.

---

### Post by warfacegod on 2010-01-18
> **terrapin893 said:**
> The great thing about open source is that you haven't paid anything for this operating system . . . . thusly you are not entitled to anything.  If you are looking for a place to feel entitled I hear Microsoft would take you in.

...And promptly tell you to piss off when you call them because Windows broke...again.

---

### Post by Leppie on 2010-01-18
> **warfacegod said:**
> ...And promptly tell you to piss off when you call them because Windows broke...again.
was it ever fixed???

---

### Post by Saurabhdua on 2010-01-19
But how do I select or know that what all packages need to be fixed? Choosing the option brings me back to the Original screen that says::"No Packages are selected"!

Please help..!

---

### Post by Leppie on 2010-01-19
in Synaptic did you go to the "custom filters" section and then "broken packages"?
you will then get a list of broken packages, select all and then click the apply button (in the toolbar at the top).

---

### Post by Saurabhdua on 2010-01-19
Yes..perhaps that's TRUE! Anyways, KUDOS to you that have upgraded to Karmic & have been able to use Internet still!?

It never worked with my "Bridge Mode" settings of Router & that's how my impression took Nosedive!

---

### Post by Leppie on 2010-01-19
> **Saurabhdua said:**
> Yes..perhaps that's TRUE! Anyways, KUDOS to you that have upgraded to Karmic & have been able to use Internet still!?
what is true?

i never upgraded to karmic, it's the first ubuntu install i personally use. before i just had debian.

---

### Post by bvanaerde on 2010-01-19
I think there's a bit of a communication problem :|

---

### Post by Saurabhdua on 2010-01-20
Ya that's TRUE. My that post is intended for you - The bvanaerde.
Now lets come on to the point:::

After successfully fixing the 'Broken Packages', still the Synaptic Manager is not allowing me to quit, quoting::some marked changes have yet to be applied.Will get lost if I quit Synaptic.

What NEXT....Sir!?

---

### Post by Ownager on 2010-01-20
I got a feeling... You are using a live cd. That's why you got this message right after memory was full. You kept downloading too many stuff. You should have installed Ubuntu 100%. You will be able to download many stuff. But you would have to check your hard drive and make sure that it's not full. You should do it wisely.

And you should do as you are told by Leppie. 

> Leppie says: in Synaptic did you go to the "custom filters" section and then "broken packages"?
you will then get a list of broken packages, select all and then click the apply button (in the toolbar at the top).

Broken packages can be found in Status via Synaptic Packages too.

---

### Post by cariboo on 2010-01-20
Please don't create multiple threads on the same subject, I have merged your two threads.

---

### Post by Saurabhdua on 2010-01-20
OK Fine...! Now since I have got the exact resolution vide [http://ubuntuforums.org/showthread.php?t=1385803]("http://ubuntuforums.org/showthread.php?t=1385803"), I would like to Thank You all in the most modest of ways!

WoW>>>Ubuntu ROCKS!...& Never Bugs anyone(Hope some day somebody will make my Internet work with Karmic as well....?)

---

