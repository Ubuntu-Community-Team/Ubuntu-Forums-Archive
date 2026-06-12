---
title: "Xubuntu &amp; Libreoffice"
date: 2011-12-13
forum: General Help
---

### Post by s0563764 on 2011-12-13
I can't access the help file, or use spell check, is xubuntu not compatible with this office suite?

---

### Post by Azdour on 2011-12-13
Hi,

When installing Libreoffice on Ubuntu 10.04 I have to remember to install the following packages as well:

```

libreoffice-l10n-en-gb
libreoffice-help-en-gb
language-support-en

```

That installs the english (en-gb) help and spelling for me. I wonder if it's the same for xubuntu?

---

### Post by s0563764 on 2011-12-13
I don't know, I just tried xubuntu for this comp. How would I install them? I tried downloading the packages from the site, and Ubuntu software told me the dependency does not satisfy or something

---

### Post by Azdour on 2011-12-13
Hi,

I usually install libreoffice via Synaptic (or in a terminal using apt-get). Did you download via their website, if so I do not know if installing those packages will help or cause you even more issues. Maybe someone else can confirm if this is the correct thing to do and how to install them.

---

### Post by s0563764 on 2011-12-13
no I used the software centre, then I tried using their forums. The ubuntu computers can use it fine in my house.

---

### Post by Azdour on 2012-05-08
Hi,

As a follow-up I recently had to install Xubuntu and sure enough after installing libreoffice from the ppa:libreoffce/ppa spell-checking did not work.

It turns out for me that myspell-en-gb was not installed.

---

### Post by hyperreal on 2012-05-08
> **s0563764 said:**
> I don't know, I just tried xubuntu for this comp. How would I install them? I tried downloading the packages from the site, and Ubuntu software told me the dependency does not satisfy or something

Go to the Terminal and enter these commands:
```

$  sudo apt-get install libreoffice-l10n-en-gb libreoffice-help-en-gb language-support-en

```

Alternatively, you can run Synaptic Package Manager and enter in 'libreoffice-l10n-en-gb' in the search bar.  Click on the package to install it.  Do this for each package you need.  When you've selected all your needed packages, click on the Apply button on the toolbar.  This will install the software for you.

This should fix the issue.  You will need to restart Libreoffice if you have it running.

---

