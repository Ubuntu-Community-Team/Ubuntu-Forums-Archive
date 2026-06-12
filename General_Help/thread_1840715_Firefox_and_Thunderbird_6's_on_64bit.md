---
title: "Firefox and Thunderbird 6's on 64bit"
date: 2011-09-08
forum: General Help
---

### Post by HappyLinux on 2011-09-08
How do I get Firefox 6 and Thunderbird 6 installed on Ubuntu via a repository due to me being on 64bit?

Sure, I can download the latest versions from the Mozilla websites, but they don't necessarily work well on 64bit that way. As far as I know, the best way is through a repository.

However, the only repository I come across is the daily build one, which I don't want.

Can anyone point me int he right direction please?

---

### Post by 2F4U on 2011-09-08
What about this official Mozilla ppa

ppa:mozillateam/firefox-stable

As far as I can see, they have Firefox 6 for Lucid, Maverick and Natty.

Here is the complete url

[https://launchpad.net/~mozillateam/+archive/firefox-stable?field.series_filter=maverick]("https://launchpad.net/%7Emozillateam/+archive/firefox-stable?field.series_filter=maverick")

---

### Post by cottfcfan on 2011-09-08
And for Thunderbird:
[https://launchpad.net/~mozillateam/+archive/thunderbird-stable](https://launchpad.net/~mozillateam/+archive/thunderbird-stable)

---

### Post by HappyLinux on 2011-09-08
> **2F4U said:**
> What about this official Mozilla ppa

ppa:mozillateam/firefox-stable

As far as I can see, they have Firefox 6 for Lucid, Maverick and Natty.

Here is the complete url

[https://launchpad.net/~mozillateam/+archive/firefox-stable?field.series_filter=maverick]("https://launchpad.net/%7Emozillateam/+archive/firefox-stable?field.series_filter=maverick")

> **cottfcfan said:**
> And for Thunderbird:
[https://launchpad.net/~mozillateam/+archive/thunderbird-stable](https://launchpad.net/~mozillateam/+archive/thunderbird-stable)

what the?? I searched for those, but couldn't find them. Like I said, all I could find were the daily builds.

---

### Post by HappyLinux on 2011-09-09
I've managed to update to version 6 on both. However, Thunderbird doesn't look any different. Thunderbird in Windows has a new interface, but under Linux, it doesn't.

Am I missing something??

---

### Post by u2nTu on 2011-09-09
Is it really installed? Running all same, also trying to get TB 6. When I try the expected:[INDENT]sudo add-apt-repository ppa:mozillateam/thunderbird-stable
sudo apt-get update
sudo apt-get upgrade
[/INDENT]the 'upgrade' throws this error:[INDENT][B]The following packages have been kept back:
  thunderbird thunderbird-locale-en-us[/B]
[/INDENT]Don't see a 'force' option. (This should be easy.)

---

### Post by cottfcfan on 2011-09-10
Try installing them from synaptic.
The latest Thunderbird should be 6.0.2.
the Global menu & Locales are the same build and all install perfectly on my machine.

---

### Post by uRock on 2011-09-10
> **u2nTu said:**
> Is it really installed? Running all same, also trying to get TB 6. When I try the expected:[INDENT]sudo add-apt-repository ppa:mozillateam/thunderbird-stable
sudo apt-get update
sudo apt-get upgrade
[/INDENT]the 'upgrade' throws this error:[INDENT][B]The following packages have been kept back:
  thunderbird thunderbird-locale-en-us[/B]
[/INDENT]Don't see a 'force' option. (This should be easy.)

You have to run sudo apt-get dist-upgrade to get Thunderbird to upgrade. Not sure as to the reasoning, but that is what I had to do.> **cottfcfan said:**
> Try installing them from synaptic.
The latest Thunderbird should be 6.0.2.
the Global menu & Locales are the same build and all install perfectly on my machine.
If the OP still has maverick, then Synaptic will show T-Bird 3.* without installing the PPA.

---

### Post by HappyLinux on 2011-09-10
I'm currently running Ubuntu 11.04, whatever name that is. You'll find attached a screenshot of my now current version of Thunderbird. I enlarged the version window to hide my emails, but still keeping the interface visible. As you can see, it's the same interface used with version 3.x.

---

### Post by uRock on 2011-09-10
They haven't changed the looks of Thunderbird.

---

### Post by u2nTu on 2011-09-10
> **uRock said:**
> [QUOTE=u2nTu;11236392]Is it really installed? Running all same, also trying to get TB 6. When I try the expected:[INDENT]     sudo add-apt-repository ppa:mozillateam/thunderbird-stable
    sudo apt-get update
    sudo apt-get upgrade 
[/INDENT]the 'upgrade' throws this error:[INDENT]*The following packages have been kept back:*
*     thunderbird thunderbird-locale-en-us *
[/INDENT]Don't see a 'force' option. (This should be easy.)
You have to run sudo apt-get dist-upgrade to get Thunderbird to upgrade. Not sure as to the reasoning, but that is what I had to do.
If the OP still has maverick, then Synaptic will show T-Bird 3.* without installing the PPA.[/QUOTE]
Thanks, uRock. (You rock.) This worked.

Ya, running Maverick so didn't work like cottfcfan's with Natty. (Waiting for 11.1 to upgrade.)

Now TB 6.02 looks the same as on wife's Window$ laptop.

New rule: Always use **dist**-upgrade when downloading from an unofficial ppa. (Thanks again.)

---

### Post by HappyLinux on 2011-09-12
> **u2nTu said:**
> Thanks, uRock. (You rock.) This worked.

Ya, running Maverick so didn't work like cottfcfan's with Natty. (Waiting for 11.1 to upgrade.)

Now TB 6.02 looks the same as on wife's Window$ laptop.

New rule: Always use **dist**-upgrade when downloading from an unofficial ppa. (Thanks again.)

Does your TB6.0.2 look the same as mine?

---

### Post by uRock on 2011-09-12
> **HappyLinux said:**
> Does your TB6.0.2 look the same as mine?

It looks the same. There were no theme changes in the Linux, nor the Windows versions.

---

### Post by u2nTu on 2011-09-13
> **uRock said:**
> [QUOTE=HappyLinux;11244329]Does your TB6.0.2 look the same as mine?
It looks the same. There were no theme changes in the Linux, nor the Windows versions.[/QUOTE]

Yep, looks and works the same in both.

---

### Post by HappyLinux on 2011-09-16
I'll have to get a screen grab of what TB6.0.2 looks like on my dad's machine and show you how different they look.

---

