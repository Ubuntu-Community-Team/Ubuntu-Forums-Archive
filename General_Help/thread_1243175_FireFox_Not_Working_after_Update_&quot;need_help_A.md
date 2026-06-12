---
title: "FireFox Not Working after Update &quot;need help ASAP&quot;"
date: 2009-08-18
forum: General Help
---

### Post by Jeanprixx on 2009-08-18
hi guys! i have a problem about firefox last night it was working well but after i update using synaptic manager this morning my firefox is not responding/running when i click the icon for firefox nothing happens the loading icon show but firefox does not open.

i try some command and try to fix it but nothing changed

sudo apt-get remove mozilla-firefox && sudo apt-get install mozilla-firefo
rm -rf .mozilla
sudo nautilus /opt/firefox/plugins/

when i try the above commands the therminal reply something about "dpkg errors".

please help.

---

### Post by HiImTye on 2009-08-18
try

```
sudo rm /var/cache/*/* && firefox -safe-mode
```

in a terminal (accessories > terminal)

---

### Post by Jeanprixx on 2009-08-18
> **HiImTye said:**
> try

```
sudo rm /var/cache/*/* && firefox -safe-mode
```in a terminal (accessories > terminal)

rm: cannot remove '/var .........................................................
rm: cannot remove '/var .........................................................
rm: cannot remove '/var .........................................................
rm: cannot remove '/var .........................................................

so on and so on still cant access firefox

---

### Post by HiImTye on 2009-08-18
yeah, it won't remove folders without the switch to do so

so removing cache and running it in safe mode isnt helping... 

what exact errors are you getting?

try opening firefox in a terminal by just typing firefox. post the results here

---

### Post by Jeanprixx on 2009-08-18
> **HiImTye said:**
> yeah, it won't remove folders without the switch to do so

so removing cache and running it in safe mode isnt helping... 

what exact errors are you getting?

try opening firefox in a terminal by just typing firefox. post the results here

running firefox in terminal - could not find compatible GRE between version 1.9.0.1 and 1.9.0.*.

---

### Post by HiImTye on 2009-08-18
try [this]("http://blog.mymediasystem.net/uncategorized/solved-firefox-could-not-find-compatible-gre-after-ubuntu-810-upgrade/")

---

### Post by Jeanprixx on 2009-08-18
i dont have xulrunner that why i need to install it before running the command.

apt-get install xulrunner

and try it but this "dpkg errors" still shows

E: dpkg was interrupted, you must manually run "dpkg --configure -a to correct the problem

---

### Post by HiImTye on 2009-08-18
did you run
> **Jeanprixx said:**
> dpkg --configure -a
?

---

### Post by Jeanprixx on 2009-08-18
> **HiImTye said:**
> did you run

?

got all the command running and also firefox are now running 

thanks for the help dude! i really appreciate it! :lolflag:

---

### Post by HiImTye on 2009-08-18
you're welcome :)

---

