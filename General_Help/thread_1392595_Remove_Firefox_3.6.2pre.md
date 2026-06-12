---
title: "Remove Firefox 3.6.2pre"
date: 2010-01-28
forum: General Help
---

### Post by Rui Gonçalves on 2010-01-28
Hi there!

Can anyone please tell me how can I remove Firefox 3.6.2pre from my system?

Thanks in advance for the help,
Best regards!
:)

---

### Post by skymera on 2010-01-28
Have you installed Firefox 3.6.2pre from the Mozilla Daily PPA?

Use this for latest Firefox stable

```
https://launchpad.net/~mozillateam/+archive/firefox-stable
```

---

### Post by Rui Gonçalves on 2010-01-28
Hi there!

But how can I remove the current Firefox? Does this PPA replace this version for a stable one?

Thanks for the help,
Best regards!

---

### Post by skymera on 2010-01-28
> **Rui Gonçalves said:**
> Hi there!

But how can I remove the current Firefox? Does this PPA replace this version for a stable one?

Thanks for the help,
Best regards!

Hello
This PPA is the latest stable Firefox, it will automatically update

To remove your current Firefox

Open up synaptic (System > Administration > Synaptic Manager)
Search for "Firefox" without the quotes.

Remove anythingn that says Firefox, Firefox-3.6 etc

Add the Firefox Stable PPA from the link i posted before.

```
 sudo apt-get update 
```
```
sudo apt-get install firefox 
```

That should download and install Firefox 3.6 stable, not the prerelease.

Just a question, how did you install Firefox 3.6.2pre?

---

### Post by bhmildy on 2010-02-15
How did I (different person than original poster) install FF Namroka 3.6.2pre?

[http://smartproteam.com/installing-firefox-3-6-on-ubuntu/](http://smartproteam.com/installing-firefox-3-6-on-ubuntu/)

googled, ubuntugeek didn't work for me, found digg article leading me to above article.  Wanted to install regular old 3.6  Oops. Think that I'll keep it the way it is though.  Seems nice, and FF is just a backup to Chrome for me.

---

### Post by vishvesh on 2010-03-01
I had used a option similar to this [http://smartproteam.com/installing-firefox-3-6-on-ubuntu/](http://smartproteam.com/installing-firefox-3-6-on-ubuntu/) option to install firefox 3.62 on ubuntu 9.04.

Unfortunately there aren't many plug-ins available for firefox 3.62 so I had to downgrade to a lower version of firefox.

The steps I took to downgrade to lower version were

1. Open up software source (System-> Administrative->Software Sources->Third-Party Software)
2. Uncheck the following URL's
     [http://ppa.launchpad.net/ubuntu-mozilla-daily/ppa/ubuntu](http://ppa.launchpad.net/ubuntu-mozilla-daily/ppa/ubuntu)
     [http://ppa.launchpad.net/chromium-daily/ppa/ubuntu](http://ppa.launchpad.net/chromium-daily/ppa/ubuntu)
If any of these url's repeat uncheck them too
3. Open up synaptic (System -> Administration-> Synaptic Manager)
4. Search for "Firefox" and mark it for complete removal and select apply.
5. After 4, Either from terminal or synaptic install the required lower version of firefox.

---

