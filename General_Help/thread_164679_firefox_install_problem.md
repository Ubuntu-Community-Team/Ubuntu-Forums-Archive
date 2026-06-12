---
title: "firefox install problem"
date: 2006-04-23
forum: General Help
---

### Post by mitjab on 2006-04-23
mitjab@ubuntu:~/Šola/tmp$ sudo apt-get -f install
Branje seznama paketov... Narejeno
Gradnja drevesa odvisnosti... Narejeno
0 nadgrajenih, 0 na novo nameš&#269;enih, 0 bo odstranjenih in 1 ne nadgrajenih.
1 ne popolnoma nameš&#269;enih ali odstranjenih.
Potrebno je dobiti 0B arhivov.
Po odpakiranju bo uporabljenega 0B dodatnega prostora na disku.
Setting up firefox (1.0.8-0ubuntu5.10) ...
Updating mozilla-firefox chrome registry.../usr/sbin/update-mozilla-firefox-chro me: line 106: 15503 Segmentation fault      firefox-bin -register >/dev/null 2>& 1
E: Registration process existed with status: 139
E: /usr/lib/mozilla-firefox/extensions/installed-extensions.txt still present. R egistration might have gone wrong.
mv: statusa ,/usr/lib/mozilla-firefox/defaults.ini` ni mo&#269; ugotoviti s stat: No such file or directory
dpkg: error processing firefox (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 firefox
E: Sub-process /usr/bin/dpkg returned an error code (1)



what to do?

---

### Post by jazzmuzik on 2006-04-23
Why are you using the -f option? That doesn't sound like a good idea.

Also, you show:

sudo apt-get install

But where is firefox specified? It should be:

sudo apt-get install firefox

How can you install something without the program name?

---

### Post by Ramses de Norre on 2006-04-23
The -f flag is used to fix broken packages, how come you get this error? What did you do before? Try sudo apt-get remove --purge firefox && sudo apt-get install firefox.
Why did you uninstall it in the first place?

---

### Post by jazzmuzik on 2006-04-23
Oh. I read the -f option as a way to ignore unmet dependencies.

---

### Post by dracule on 2006-04-23
Im trying to install firefox 1.5 but when i replace the folder "firefox" in .mozilla in home, firefox 1.0.8 automatically replaces it when i go to internet-->firefox.
I tried to update with synaptic but that only got me to 1.0.8

---

### Post by Sef on 2006-04-23
Read this to install firefox 1.5.0.2.

[https://wiki.ubuntu.com/FirefoxNewVersion?highlight=%28firefox%29]("https://wiki.ubuntu.com/FirefoxNewVersion?highlight=%28firefox%29")

---

### Post by dracule on 2006-04-23
nevermind i used automatix and it installed it for me, thanks anyways.

---

