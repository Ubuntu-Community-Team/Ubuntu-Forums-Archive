---
title: "dpkg issue"
date: 2009-06-30
forum: General Help
---

### Post by mrmishap on 2009-06-30
I've looked around and i'm not the first person to have this error, but previous fixes in the thread wern't fixing whatever has happened to my specific machine:

e: dpkg was interrupted, you must manually run ' sudo dpgk --configure -a' to correct this problem
e: _cache->open()failed, please report.

when I use the command it gives me this:
setting up openoffice.org-emailmerge(1:3.0.1-9ubuntu3)
adding extension /usr/lib/openoffice/basis3.0/program/mailmerge.py...

then everything hangs and i have to hit the reset button....

This started happening after somthing interupted my openoffice install.
I can not make any changes, adding , removing or updating with out getting this error.

this is true for
the main add/remove program
the updater
apt-get
and synaptic package magnager.

I normally just read past posts and not post myself... but i'm very stuck this time.
ty

---

### Post by thespirit3 on 2009-06-30
Hi,

I had a similar issue recently with a crapped out install of VirtualBox.

I had to remove the entry in /var/lib/dpkg for the corrupt install.

In my case I did this:-

cd /var/lib/dpkg
cp -R info info.bak
cd info
rm virtualbox-2.2.*

The dpkg install then ran smoothly.

As above, I'd back up the original directory though - as screwing with package management is generally a bad idea.

Hope that helps.


Steve

---

### Post by mrmishap on 2009-06-30
Thanks! this fixed the issue!

Now I ran into another one... :(
Once i was able to update and install i updated the os and removed open office.
everything was going well.
but when i went to reinstall open office again.  the install hung my machine. so since the installation was again interrupted i have the same problem...again! atleast i know how to fix this now. however, has anyone else heard of open office install issues?

ty agian!

---

### Post by cactusgal on 2009-10-27
> **mrmishap said:**
> Thanks! this fixed the issue!

Now I ran into another one... :(
Once i was able to update and install i updated the os and removed open office.
everything was going well.
but when i went to reinstall open office again.  the install hung my machine. so since the installation was again interrupted i have the same problem...again! atleast i know how to fix this now. however, has anyone else heard of open office install issues?

ty agian!
Well, I'm having the same problem exactly as you've stated. Being quite new to Ubuntu, I tried previous suggestions with no success at all so finally re-installed the whole OS thinking I'd try again from scratch only to have it happen again and I only tried to install 'writer' this time not the whole suite but I guess it's the crux of the issue. So now what!? Everything just freezes and I have to restart the system. Also for a newbie, could someone please tell me exactly how that last line in thespirit3's fix should read? mailmerge.python-uno? Cuz if this keeps happening I'll have to scratch the idea of OpenOffice. But is there another word processor I can use instead besides just Text Editor?

cactusgal

---

### Post by philinux on 2009-10-27
On a new install open office is installed as default. Apps>Office.

---

### Post by cactusgal on 2009-10-27
> **philinux said:**
> On a new install open office is installed as default. Apps>Office.
Guess I forgot to mention I'm using Ubuntu Studio 9.10 so openoffice isn't part of the package.

cactusgal

---

### Post by philinux on 2009-10-27
Try installing abiword. Cant understand why office wont install though.

---

### Post by cactusgal on 2009-10-27
> **philinux said:**
> Try installing abiword. Cant understand why office wont install though.
Thanks for the suggestion. But in the meantime, short of doing another OS install, how do I get rid of this problem? Very new so sorry to sound stupid but I know the terminal commands must be precise so would it be?:

cd /var/lib/dpkg
cp -R info info.bak
cd info
mailmerge.python-uno

cactusgal

---

### Post by philinux on 2009-10-27
Run these commands one at a time and post back any errors.

```
sudo apt-get update

then

sudo apt-get upgrade
```

---

### Post by cactusgal on 2009-10-27
> **philinux said:**
> Run these commands one at a time and post back any errors.

```
sudo apt-get update

then

sudo apt-get upgrade
```
sudo apt-get update gets me this message: E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem.

sudo apt-get upgrade gets me the same message

cactusgal

---

### Post by philinux on 2009-10-27
Ok so run that and post back the errors.

```
sudo dpkg --configure -a
```

Post back the full list of errors.

---

### Post by cactusgal on 2009-10-27
> **philinux said:**
> Ok so run that and post back the errors.

```
sudo dpkg --configure -a
```

Post back the full list of errors.
Well, I've already tried this any number of times without success. It goes: 'setting up openoffice.org-emailmerge(1:3.0.1-9ubuntu3)
adding extension /usr/lib/openoffice/basis3.0/program/mailmerge.py...' and then just hangs there and ends up freezing everything so I have to re-boot.

cactusgal

---

