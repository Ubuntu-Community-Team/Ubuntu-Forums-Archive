---
title: "Couldn't install .deb packages using Gdebi."
date: 2011-10-17
forum: General Help
---

### Post by krizanand on 2011-10-17
[SIZE="2"]As the title goes, a new problem with Oneiric that I couldn't install .deb packages. I get a message that 'package could be corrupted/ you don't have permissions'..... Digging deep on this forum I was able to install latest Opera through terminal but the same don't work for Chrome, I get dependency error, errors encountered in installation. To my surprise Ubuntu software center couldn't install .deb files either. Is this a bug in Oneiric? Anyway I can get around this silly problem.[/SIZE]

Thanks.

---

### Post by Diametric on 2011-10-17
If I'm not mistaken you don't need an application to install a .deb - provided you have the permissions etc....all you have to do is double click it.

You tried Synaptic and it failed on a .deb installation, too?  What .deb is it - from the repositories or some other source?

---

### Post by Gyokuro on 2011-10-17
Hi,

you can install deb packages via terminal:

sudo dpkg -i package.deb

but I'm stilling wondering why are you installing downloaded debs as you can install both browsers via your Ubuntu Software Center. Maybe you have not enabled the partner reps.

---

### Post by krizanand on 2011-10-17
I downloaded Opera and Google chrome .deb packages from official links. Before I installed Gdebi package installer I was getting an option to open via Ubuntu software center which throws up errors, it applies to any .deb file I tried to open. I managed to install Opera without problems, Chrome with dependency errors, with sudo dpkg -i filename from the terminal. Now, it looks like only way to install .deb packages through terminal. How can I get rid of permission/ file corrupt messages and install .deb packages using Gdebi or Ubuntu software center?.

---

### Post by gandaran on 2011-10-17
I had no problem at all installing Opera with gdebi yesterday.
one question the chrome .deb and opera where the latest releases?

---

### Post by Gyokuro on 2011-10-17
Ok,

maybe something is not working correct. In such a case you can try in a terminal:

sudo apt-get clean 
sudo apt-get update # you can have all in one line sudo apt-get clean && apt-get update

which will clean up some files and directories. Afterwards try to search again in your Ubuntu Software Center for Google Chrome or Chromium Browser and it would be nice whether you can post your error messages to help you further.

---

### Post by Gyokuro on 2011-10-17
> **gandaran said:**
> I had no problem at all installing Opera with gdebi yesterday.
one question the chrome .deb and opera where the latest releases?

The debs which you download from google.com or opera.com are always the latest one (stable release)

---

### Post by mc4man on 2011-10-17
The issue with google-chrome is it needs, I believe, 2 or 3 additional packages that you likely didn't have installed prior to using dpkg
dpkg -i will not install add. deps.

If you have synaptic installed then open it, edit > fix broken packages & it will install what's needed.

if synaptic isn't installed you could try
```
sudo apt-get -f install
```

---

### Post by ruario on 2011-10-19
The problem is an issue with Gdebi and Software Centre (which I believe share some code).

See here for more information:
[http://my.opera.com/community/forums/findpost.pl?id=10564932](http://my.opera.com/community/forums/findpost.pl?id=10564932)

You can fix this by installing xz-lzma, lzma or by simply setting up a symlink as follows:

```

cd /usr/bin
sudo ln -s xz lzma

```

This will allow Gdebi and Software Centre to use xz to decompress the data.tar.lzma within some packages.

P.S. Here is the bug report if you want to track it [https://bugs.launchpad.net/ubuntu/+source/software-center/+bug/868188](https://bugs.launchpad.net/ubuntu/+source/software-center/+bug/868188)

---

### Post by krizanand on 2011-10-19
[SIZE="2"]Thanks for your helpful responses guys, I'm quite baffled here Chrome got installed inspite of those dependency errors but not sure how?[/SIZE]. I'm learning stuff in Ubuntu day by day by visiting this forum,few replies in this thread will help me to fix any problem in the future. Once again thanks for the responses :).

---

### Post by ruario on 2011-10-19
Your profile states that you run Ubuntu 10.10 Maverick Meerkat, which includes the lzma package by default. This became a problem with Ubuntu 11.10 (Oneiric Ocelot) as it does not. So you may have had another issue.

---

### Post by krizanand on 2011-10-19
I'm now using 11.10, I can't change my profile info as a I haven't crossed 50 posts. Lzma compression could be the only reason as I did a fresh install but don't know how it got installed, nevertheless I'm using Chrome which is what I need :)

---

