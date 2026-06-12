---
title: "aMSN trouble - pop-ups don't show all components"
date: 2009-10-21
forum: General Help
---

### Post by Anne1392 on 2009-10-21
Hello all,

I use Ubuntu 8.10 (no, I cannot update, because it doesn't support my monitor) and aMSN 0.97.2. Somehow, though, it doesn't show pop-ups right, resulting in not being able to change my username or other settings. An example is shown in the attachments. 

I already tried removing all files related to amsn (complete removal from synaptic + manual removal of other files) and then installing it again: no result.

I hope someone here knows how to solve this. I really do need aMSN, since I need to save my contact list, so I can import it in another account.

Thanks!
Anne

[[URL=http://img24.imageshack.us/i/schermafdruk1b.png/][IMG]http://img24.imageshack.us/img24/1701/schermafdruk1b.th.png[/IMG]]("http://img24.imageshack.us/i/schermafdruk1b.png/")
[/URL]

---

### Post by Stemp on 2009-10-21
[https://launchpad.net/~amsn-daily/+archive/ppa](https://launchpad.net/~amsn-daily/+archive/ppa) ?

---

### Post by Anne1392 on 2009-10-22
Okay, I failed at this :P. I tried adding the repository. Then I added the signing key with the terminal, but it doesn't recognize it:

```
anne@anne-desktop:~$ sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 28CBC482
Executing: gpg --ignore-time-conflict --no-options --no-default-keyring --secret-keyring /etc/apt/secring.gpg --trustdb-name /etc/apt/trustdb.gpg --keyring /etc/apt/trusted.gpg --keyserver keyserver.ubuntu.com --recv-keys 28CBC482
gpg: opvragen sleutel 28CBC482 van hkp sleutelserver keyserver.ubuntu.com
gpg: sleutel 28CBC482: “Launchpad PPA for aMsn Daily” niet veranderd
gpg: Totaal aantal verwerkt: 1
gpg:              Onveranderd: 1
```

I'm sorry, it's in Dutch (I only just realized that). It says that it processed it, but that it's not changed.

I have no idea how I should do this :/.

---

### Post by Stemp on 2009-10-22
Sorry, I used to understand flemish when I was a kid, not anymore ;)

But the message seems to be : processed, unchanged. Meaning the key was already present.

Could you please do in a terminal (it's easier to spot the errors) :

```
sudo apt-get update
```

then if you don't see keys errors :

```
sudo apt-get upgrade
```

aMSN should be updated to the new version 0.98b-svn11138

---

### Post by Anne1392 on 2009-10-22
After I did the update, it said that there was no public key present:

```

Pakketlijsten worden ingelezen... Klaar
W: GPG-fout: http://ppa.launchpad.net intrepid Release: De volgende ondertekeningen konden niet geverifieerd worden omdat de publieke sleutel niet beschikbaar is: NO_PUBKEY 9423A34CCA967634
W: U kunt misschien 'apt-get update' uitvoeren om deze problemen te verhelpen

```
And it suggests to use apt-get update to solve the problems. Except, when I do that, it says that it couldn't open '/var/lib/apt/lists/lock',  because access was denied.

---

### Post by Stemp on 2009-10-22
```
gpg --keyserver keyserver.ubuntu.com --recv-keys 9423A34CCA967634
```

But that's not the aMSN PPA key, it's the KDE4 Kubuntu members PPA keys ;)

---

### Post by Anne1392 on 2009-10-22
I don't get it... You mean that the one it refused to update wasn't the one I just added? 

In that case apt-get upgrade should work, but it didn't update amsn. How should I do that?

My god, I'm such a newbie :P.

---

### Post by Stemp on 2009-10-22
> **Anne1392 said:**
> I don't get it... You mean that the one it refused to update wasn't the one I just added? 
Yes exactly ;)

> **Anne1392 said:**
> In that case apt-get upgrade should work, but it didn't update amsn. How should I do that?

My god, I'm such a newbie :P.

It's not you, packages are sometimes quite frustating.

Try :

> apt-policy amsn

It will give you the amsn versions you have (sorry about all these terminal commands, but it's easier to get the errors).

---

### Post by Anne1392 on 2009-10-22
```
anne@anne-desktop:~$ sudo apt-policy amsn
sudo: apt-policy: command not found
```

---

### Post by Stemp on 2009-10-22
Oooops,

```
apt-cache policy amsn
```

No sudo needed ;)

---

### Post by Anne1392 on 2009-10-22
Hehe ](*,).

```

anne@anne-desktop:~$ apt-cache policy amsn
amsn:
  Geïnstalleerd: 0.97.2~debian-0ubuntu3
  Kandidaat: 0.98b-svn11138~iiamsn3
  Versietabel:
     0.98b-svn11138~iiamsn3 0
        500 http://ppa.launchpad.net intrepid/main Packages
 *** 0.97.2~debian-0ubuntu3 0
        500 http://nl.archive.ubuntu.com intrepid/universe Packages
        100 /var/lib/dpkg/status

```
Geïnstalleerd = installed
Kandidaat = candidate
Versietable = version table

Seems quite obvious :P.

---

### Post by Stemp on 2009-10-22
Ok so the PPA version is Kandidaat \o/

an upgrade and you'll have it ;)

```
sudo apt-get upgrade
```

---

### Post by Anne1392 on 2009-10-22
```
Pakketlijsten worden ingelezen... Klaar
Boom van vereisten wordt opgebouwd       
De status informatie wordt gelezen... Klaar
De volgende pakketten zijn achtergehouden:
  amsn amsn-data
0 pakketten opgewaardeerd, 0 pakketten nieuw geïnstalleerd, 0 te verwijderen en 2 niet opgewaardeerd.
```

It says that it didn't update amsn and amsn-data, doesn't give a reason. In the end, the conclusion says: 0 upgraded, 0 newly installed, 0 to be deleted and 2 not upgraded.

---

### Post by Stemp on 2009-10-24
/o\ I missed your message :D

Could you try with aptitude and give all the messages from the full upgrade ?
(I add the LANG=C command to get the messages in English, and aptitude is better for dependencies)

```
sudo aptitude update
```

And

```
LANG=C sudo aptitude full-upgrade
```

---

### Post by Anne1392 on 2009-10-25
Okay, so it worked:

```
anne@anne-desktop:~$ apt-cache policy amsn

amsn:
  Geïnstalleerd: 0.98.1-0~iiamsn3
  Kandidaat: 0.98.1-0~iiamsn3
  Versietabel:
 *** 0.98.1-0~iiamsn3 0
        500 http://ppa.launchpad.net intrepid/main Packages
        100 /var/lib/dpkg/status
     0.97.2~debian-0ubuntu3 0
        500 http://nl.archive.ubuntu.com intrepid/universe Packages
```

The problem is still there >.<".

---

