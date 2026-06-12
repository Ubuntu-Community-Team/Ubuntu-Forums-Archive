---
title: "ubuntu &amp; firefox .. versions confuse"
date: 2010-09-17
forum: General Help
---

### Post by Ordes on 2010-09-17
ubuntu lucid, firefox 3.6...

but it seems the firefox 3.6 is not a complete 3.6 as its gecko is 3.0...;
so whenever i want to install a update that is for ff >= 3.5, i always get, that this addon is not available for ff 3.0...

my question:
1. is it normal that the ff 3.6 is running on gecko 3.0 on ubuntu? cuz in windows the ff 3.6 also has the 3.6 gecko

2. if so.. how can i update that gecko?

txs

---

### Post by lovinglinux on 2010-09-17
> **Ordes said:**
> ubuntu lucid, firefox 3.6...

but it seems the firefox 3.6 is not a complete 3.6 as its gecko is 3.0...;
so whenever i want to install a update that is for ff >= 3.5, i always get, that this addon is not available for ff 3.0...

my question:
1. is it normal that the ff 3.6 is running on gecko 3.0 on ubuntu? cuz in windows the ff 3.6 also has the 3.6 gecko

2. if so.. how can i update that gecko?

txs

I don't understand the question and your situation. If you are referring to the Gecko engine, then the version should be 1.9.2. Firefox 4, which is under development, comes with Gecko 2.0.

Add-ons compatibility are based on Firefox version number, not Gecko's. Are you trying to install an addon from the repositories or from Mozilla site? Could you please provide a link?

Please provide the output of the following commands and instructions. This will make sure I will have a good understanding of your Firefox installations, so I don't need to guess what might be happening to your system:


**2 - Firefox version and architecture**

To find Firefox version and architecture, click "Help >> About Mozilla Firefox" in the menu. The info will be located at the bottom of the info dialog (you need to resize the window to see it):

[IMG]http://tinyurl.com/26b85o2[/IMG]


**3 - System Info**

Execute the following commands then copy the generated file, named **firefox-report.txt** from your Desktop and upload it here or paste the contents.

To execute those commands, select the entire content below, then go to "Applications >> Accessories >> Terminal" and click the terminal with the middle-mouse button.

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
echo '' >> ~/Desktop/firefox-report.txt
echo 'Sources' >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
ls /etc/apt/sources.list.d >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
firefox ~/Desktop/firefox-report.txt
```

---

### Post by Ordes on 2010-09-17
@loving txs for the help..

> i tried to install some addons from the modzilla site.
> i misread the "firefox - about" i thought that was gecko ^^ but here u can see the screenshot:

[IMG]http://gong-fu.eu/scr.jpg[/IMG]

and here is the output from terminal

```

Ubuntu Architecture

Linux Desktop 2.6.32-24-generic #42-Ubuntu SMP Fri Aug 20 14:24:04 UTC 2010 i686 GNU/Linux

Ubuntu Version

DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=10.04
DISTRIB_CODENAME=lucid
DISTRIB_DESCRIPTION="Ubuntu 10.04.1 LTS"

Firefox Packages

firefox                        install
firefox-3.0                    deinstall
firefox-3.5                    deinstall
firefox-branding                install
kubuntu-firefox-installer            install

Firefox binaries

/usr/bin/firefox
/usr/bin/firefox: symbolic link to `../lib/firefox-3.6.10/firefox.sh'
/usr/local/bin/firefox: ERROR: cannot open `/usr/local/bin/firefox' (No such file or directory)
/opt/firefox/firefox: ERROR: cannot open `/opt/firefox/firefox' (No such file or directory)

Firefox divertion

/usr/bin/firefox.ubuntu: ERROR: cannot open `/usr/bin/firefox.ubuntu' (No such file or directory)

Sources

getdeb.list
getdeb.list.distUpgrade
getdeb.list.save
mozillateam-firefox-stable-lucid.list
mozillateam-firefox-stable-lucid.list.save
pidgin-developers-ppa-lucid.list
pidgin-developers-ppa-lucid.list.save
pidgin-ppa.list
pidgin-ppa.list.distUpgrade
pidgin-ppa.list.save
team-xbmc-ppa-karmic.list
team-xbmc-ppa-karmic.list.distUpgrade
team-xbmc-ppa-karmic.list.save
ubuntu-mozilla-daily-ppa-karmic.list
ubuntu-mozilla-daily-ppa-karmic.list.distUpgrade
ubuntu-mozilla-daily-ppa-karmic.list.save

```

and screenshot of installed packages in synaptic

[IMG]http://gong-fu.eu/scr2.jpg[/IMG]

my ubu is 10.04; i never made changes to ff; except ones; i was using the launchpad-ppa modzilla daily; but than there was this big "flash-bug" so i removed the repo; deinstalled FF; and reinstalled FF using software center; not sure if this is connected to the problem; the modzilla daily listed above is disabled..;

txs so far

---

### Post by lovinglinux on 2010-09-17
Looks like you are using User Agent Switcher to fool some web site that requires Windows. Disable it and try to install the extensions again.

---

### Post by Ordes on 2010-09-18
> User Agent Switch. Not using that.

> I think the main problem is that ff states on top 3.6.8, but on the bottom 3.0.7. Dont know how to upgrade this. Just remved ff completly and reinstalled it through Software Center. But still the same :( 
3.6 top; 3.0.7 bottom :(

---

### Post by lovinglinux on 2010-09-18
> **Ordes said:**
> > User Agent Switch. Not using that.

> I think the main problem is that ff states on top 3.6.8, but on the bottom 3.0.7. Dont know how to upgrade this. Just remved ff completly and reinstalled it through Software Center. But still the same :( 
3.6 top; 3.0.7 bottom :(

Is worse than that, since it says you have the Windows version of Firefox.

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=169856&stc=1&d=1284826276[/IMG]

Try this:

```
sudo apt-get purge firefox
sudo apt-get purge firefox-3.0
sudo apt-get purge firefox-3.5
sudo apt-get install firefox
```

---

### Post by Ordes on 2010-09-19
ah ok... understand now..

fixed the problem by creating a new profile.. before i used parts of my windows ff profile.. that must have triggered it... and as there had been no problem so far when i was using it, i didnt think about that,...

txs for the help..

---

### Post by lovinglinux on 2010-09-19
> **Ordes said:**
> ah ok... understand now..

fixed the problem by creating a new profile.. before i used parts of my windows ff profile.. that must have triggered it... and as there had been no problem so far when i was using it, i didnt think about that,...

txs for the help..

You are welcome.

---

