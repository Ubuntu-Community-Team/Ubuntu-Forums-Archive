---
title: "apt-get update fails"
date: 2011-06-22
forum: General Help
---

### Post by ddjolley on 2011-06-22
When I do "apt-get update" I get:

Reading package lists... Error!
E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_natty_main_binary-i386_Packages
E: The package lists or status file could not be parsed or opened.

What is this error message telling me and what do I need to do to fix it?  Thanks.

         ... doug

---

### Post by e79 on 2011-06-22
I could be wrong but there seems to be a 'space' afte the 'a' and before the 'r' in the section highlithed in red.
> E: Problem with MergeList /var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_natty_main_[COLOR=Red]bina  ry-i386[/COLOR]_Packages

I am not sure it is related (or possibly how to fix it) but could you post the result of your sources.list file ?
```
cat /etc/apt/sources.list
```

---

### Post by jerrrys on 2011-06-22
try this

gksudo nautilus and navigate to the problem file.

create a new folder and put this problem file in it.  this way you can restore if necessary.

now try an update

---

### Post by ddjolley on 2011-06-22
> I could be wrong but there seems to be a 'space' afte the 'a' and before
>  the 'r' in the section highlithed in red.

I am not sure; but, if there is it was somehow a result of the copy and paste operation.  No such space appears in the actual output.

> Could you post the result of your sources.list file?

# deb cdrom:[Ubuntu 11.04 _Natty Narwhal_ - Release i386 (20110427.1)]/ natty main restricted

# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty-updates universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty-updates multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) natty-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) natty-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) natty-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) natty-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) natty-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) natty-security multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) natty partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) natty partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) natty main
deb-src [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) natty main

[FONT=monospace]Thanks.

      ... doug
[/FONT]

---

### Post by ddjolley on 2011-06-22
> try this

If I understand the essence of your suggestion, what you want me to do is to make a backup copy of the problem file, remove it, and then re-try "apt-get update".  I have tried that.  What happens is that I get the same error message except that it references a new problem file.

Thanks.

       ... doug

---

### Post by jerrrys on 2011-06-22
ok, no go.

i tend to get a little crazy.  so i would next remove or copy (however you want to do it)

/var/lib/apt/lists

---

### Post by e79 on 2011-06-22
Try this please and tell us if it solve your problem :

Open a Terminal and type :

1. ```
cd ~
```
2. ```
mkdir lists
```
3. ```
cd /var/lib/apt/lists
```
4. ```
sudo cp -r * /home/username/lists
```(**make sure to replace 'username' with your actual username**)
5. ```
sudo rm -r *
```(**Make sure that you still are in '/var/lib/apt/lists' before executing this command !**)
6. ```
sudo apt-get update && sudo apt-get dist-upgrade
```

Does it work ?

---

### Post by ddjolley on 2011-06-22
> Does it work?

Yes.  It appears to solve the problem.

So, now I need to understand what I have done and what else I need to do.  I understand that I backed up the directory /var/lib/apt/lists and then cleared it out.  That's easy.  What did I accomplish with 'apt-get update' and 'apt-get dist-upgrade'?  What should I do with my backup copy of /var/lib/apt/lists?  

For want of a better description, I think that what I did was sort of "start over".   What influence does /etc/apt/sources.list have over this?  Thanks.

        ... doug

---

### Post by plucky on 2011-06-23
> So, now I need to understand what I have done and what else I need to do. I understand that I backed up the directory /var/lib/apt/lists and then cleared it out. That's easy. What did I accomplish with 'apt-get update' and 'apt-get dist-upgrade'? What should I do with my backup copy of /var/lib/apt/lists? 

"apt-get update" reloaded the list files from the repository servers and "apt-get dist-upgrade" installed any upgrades that it found when it compared the installed status file with the list files.

> What should I do with my backup copy of /var/lib/apt/lists? 

You can now delete it.

> What influence does /etc/apt/sources.list have over this?

That determines which repository server is used for updates.The mirror servers sometimes get out of step with the main server, which causes problems,but are faster to download from than the main server.


Good luck

---

### Post by e79 on 2011-06-23
> **ddjolley said:**
> So, now I need to understand what I have done and what else I need to do
You have nothing else to do as far as I know  :)

> **ddjolley said:**
> What did I accomplish with 'apt-get update' and 'apt-get dist-upgrade'?

'apt-get update' = Fetch the list of all upgradable packages on your system
'apt-get upgrade/dist-upgrade' = Update the packages from the lists of 'apt-get update'

> **ddjolley said:**
> What should I do with my backup copy of /var/lib/apt/lists?

Now that everything is back to normal, you can safely trash it.

> **ddjolley said:**
> For want of a better description, I think that what I did was sort of  "start over".   What influence does /etc/apt/sources.list have over  this?

The file '/etc/apt/sources.list' contains all the URLs/places Ubuntu will look when updating your system.  For what is inside the '/var/lib/apt/lists', as far as I can understand, it seems to be a description of all the packages you can download/update from the URLs '/etc/apt/sources.list' is providing and the extra sources (Sources of updates for softwares Canonical does update itself   ex:Chromium) you might have added.

For some reason, one of your file in '/var/lib/apt/lists' got corrupted, therefore, could not be parsed by the system so Ubuntu could not provide the list of upgradable packages provided by the URL in '/etc/apt/sources.list'... I hope I make sense...

In any way, what I told you to do, was to basically clean that folder and tell Ubuntu to fetch back all the packages descriptions so you have a clean copy of them. So to answer your question, yes, we can consider it as a 'start over' of fecthing the information on what to update on your system.

Lets simply hope the issue does not reoccurs again, I am still unsure of what could have cause that to be honest.

> **ddjolley said:**
> Thanks.

The pleasure is all mine :P

e79

---

### Post by ddjolley on 2011-06-23
> I am still unsure of what could have cause that to be honest.

Unfortunately my wife has a Windows machine on the network.  (It seems that Windows machines are the primary source of most problems.)  Anyway, she contracted a virus which caused our Internet service provider to suspend service.  After the virus was removed and service was restored, I noticed that both of my Ubuntu machines had this same identical problem.  I'm like you in that I don't understand specifically what would cause this problem; but, the events surrounding the service outage certainly seem suspect.

Thanks to all who responded.

BTW, I get these notices to mark a thread SOLVED.  How do I do that?  Thanks.

        ... doug

---

### Post by ddjolley on 2011-06-24
> I am still unsure of what could have cause that to be honest.

 	I thought that I had responded to this; but, I don't see the reply.  My wife has a Windows machine.  (It seems that all problems ultimately stem from Windows machines.).  Anyway, she contracted a virus which resulted in our ISP suspending service until we got that fixed which took about a day.  When the smoke all cleared the problem we have been discussing was present on my only 2 Ubuntu machines.  I don't know that that had anything to do with it; but, it certainly seems suspect.

I am told that I should label the thread as SOLVED.  How do I do that?

Thanks.

          ... doug

---

