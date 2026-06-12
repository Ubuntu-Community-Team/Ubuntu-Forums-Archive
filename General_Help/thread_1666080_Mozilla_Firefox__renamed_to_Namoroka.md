---
title: "Mozilla Firefox  renamed to Namoroka"
date: 2011-01-13
forum: General Help
---

### Post by aldee96 on 2011-01-13
I've just did partial update on ubuntu and My firefox(v.3.6.x) is renamed to namoroka and changed the icon too. but the links on my desktop, Gnome panel still describe it's a firefox like in the screenshot's below. could anyone describe me why and how to returns it like before. namoroka it's something annoying for me.

---

### Post by WorMzy on 2011-01-13
Namoroka is Firefox without the Firefox branding.

Assuming you're using the official packages, you can probably "fix" this by installing firefox-branding.

```
sudo apt-get install firefox-branding
```

---

### Post by aldee96 on 2011-01-13
> **WorMzy said:**
> Namoroka is Firefox without the Firefox branding.

Assuming you're using the official packages, you can probably "fix" this by installing firefox-branding.

```
sudo apt-get install firefox-branding
```

when i put it on the terminal it says that the firefox-branding is the newest update an already installed and on the secondline it tells that it was set to be updated manually why?

---

### Post by lovinglinux on 2011-01-13
The problem is that you are using a ppa for Firefox that install a development version.

Disable *ubuntu-mozilla-daily* in software sources, then re-install Firefox.

```
sudo apt-get install --reinstall firefox
```

---

### Post by aldee96 on 2011-01-13
i was installed firefox 4.0 beta and uninstalled because it mess up my firefox, i  don't want install it again through mozilla PPA, i don't want to see namoroka anymore. could anyone tell me how to install it as firefox too(if it's possible beside the ff 3.6.x like in windows).

---

### Post by wojox on 2011-01-13
Are you using any ppa's?

---

### Post by aldee96 on 2011-01-13
> **lovinglinux said:**
> The problem is that you are using a ppa for Firefox that install a development version.

Disable *ubuntu-mozilla-daily* in software sources, then re-install Firefox.

```
sudo apt-get install --reinstall firefox
```

i've already delete the PPA's, but it's still affect

---

### Post by sarin_cv on 2011-01-13
Din't get your problem exactly...what I did is, downloaded the tar file from mozilla site, extracted it to  folder... U can execute it with ./firefox from that location in terminal or create a shorcut in menu

---

### Post by lovinglinux on 2011-01-13
> **aldee96 said:**
> i've already delete the PPA's, but it's still affect

Try:

```
sudo apt-get update
sudo apt-get install --reinstall firefox
```

If it doesn't work, then execute the following commands and attach the report file created in your Desktop.

```
echo 'Ubuntu Architecture' > ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
uname -a >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
echo 'Ubuntu Version' >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
cat /etc/lsb-release >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
echo 'Firefox Packages' >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
dpkg --get-selections | grep 'firefox*' >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
echo 'Firefox binaries' >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
which firefox >> ~/Desktop/firefox-report.txt
file /usr/bin/firefox >> ~/Desktop/firefox-report.txt
file /usr/local/bin/firefox >> ~/Desktop/firefox-report.txt
file /opt/firefox/firefox >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
echo 'Firefox divertion' >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
file /usr/bin/firefox.ubuntu >> ~/Desktop/firefox-report.txt

```

---

### Post by aldee96 on 2011-01-13
> **sarin_cv said:**
> Din't get your problem exactly...what I did is, downloaded the tar file from mozilla site, extracted it to  folder... U can execute it with ./firefox from that location in terminal or create a shorcut in menu

yes i know but it's replaced the default stable firefox and i want to still using some xtensions on it that's not compatible with the firefox 4

---

### Post by dmizer on 2011-01-13
Threads merged. Please do not post duplicate threads for the same problem.

Thank you :)

---

### Post by celldweller1591 on 2011-01-13
you installed wrong build. Namaroka is not actually FF 4.0, its FF 3.6 Daily testing build. So thats why you landed up in trouble. 
Use this to get actual FF 4.0 i.e Minefield. 
> sudo add-apt-repository ppa:ubuntu-mozilla-daily/ppa
sudo apt-get update
sudo apt-get install firefox4.0

---

### Post by lovinglinux on 2011-01-13
> **aldee96 said:**
> yes i know but it's replaced the default stable firefox and i want to still using some xtensions on it that's not compatible with the firefox 4

See my tutorials on how to install other versions of Firefox:

[http://www.webgapps.org/firefox/installing-other-versions](http://www.webgapps.org/firefox/installing-other-versions)
[http://www.webgapps.org/firefox/installing-firefox-4](http://www.webgapps.org/firefox/installing-firefox-4)

They explain everything you need to know to achieve what you want.

---

### Post by lithopsian on 2011-01-13
Ti run a version of Firefox that uses a separate profile from the one you already have (although it may be too late for that!), execute Firefox with the -P option.  For example, /opt/firefox/firefox -P.  It will show you the profile manager, a small dialog.  You will probably need to create a new profile, which will be empty and have no add-ons, no themes, nonoe of your bookmarks, etc.  This is strongly recommended because Firefox 4 makes changes to your profile which could cause problems for earlier versions.  Also, of course, it is beta and could conceivably corrupt stuff.  You can specify the path to the profile to use after the -P and it will automatically run it without the dialog, so you can code different versions into your start menu for convenience.

You can also run two different versions of Firefox with two different profiles at the same time if you need to, using the no-remote command line option.

I think you'll like FF4.  It is faster than before, although there are a number of UI changes that you might have trouble getting used to.

---

