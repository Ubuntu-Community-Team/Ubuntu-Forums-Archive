---
title: "flash broken in firefox and chrome"
date: 2010-08-23
forum: General Help
---

### Post by wwwbrowse on 2010-08-23
Usual use chrome for browsing but for some reason this broke, and now flash doesn't even appear on the about:plugins page.

flash doesn't work in firefox and trying to install flash gives the following errors:-

Flash Plugin installed.
nspluginwrapper: no appropriate viewer found for /usr/lib/flashplugin-installer/libflashplayer.so
dpkg: error processing flashplugin-installer (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of flashplugin-nonfree:
 flashplugin-nonfree depends on flashplugin-installer; however:
  Package flashplugin-installer is not configured yet.
dpkg: error processing flashplugin-nonfree (--configure):
 dependency problems - leaving unconfigured

I have tried flash-aid and lots of manual purging reinstalling etc. but to no avail. any help greatly appreciated.

---

### Post by finny388 on 2010-08-23
Did you try installing flashplugin-nonfree?

I believe that's what I did when 10.04 was released.

Wish I could be more help.

---

### Post by lovinglinux on 2010-08-24
[http://ubuntuforums.org/showpost.php?p=9492252&postcount=5](http://ubuntuforums.org/showpost.php?p=9492252&postcount=5)

---

### Post by wwwbrowse on 2010-08-24
I disabled all but main from software source and followed instructions. I got the same error again if using flash-aid, or this is the error I got using the code:-

nspluginwrapper: no appropriate viewer found for /usr/lib/flashplugin-installer/libflashplayer.so
dpkg: error processing flashplugin-installer (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 flashplugin-installer
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by lovinglinux on 2010-08-24
Please provide the output of the following commands and instructions. This will make sure I will have a good understanding of your Firefox and Flash installations, so I don't need to guess what might be happening to your system:

**1 - Flash Version**

Type **about[noparse]:[/noparse]config** in Firefox address bar, then type **plugin.expose_full_path** in the filter, then double-click the same item in the results to make it **true**. Then type **about[noparse]:[/noparse]plugins** in the address bar, find Shockwave Flash, copy the corresponding Path and Version and paste here. it should look lie the image below:

[IMG]http://tinyurl.com/287j7on[/IMG]

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
echo 'Flash packages' >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
dpkg --get-selections | grep 'flash*' >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
echo 'Plugin locations' >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
locate libflashplayer.so  >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
locate flashplugin-alternative.so  >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
echo 'Flash symlinks' >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
file /usr/lib/firefox-addons/plugins/libflashplayer.so  >> ~/Desktop/firefox-report.txt
file /usr/lib/mozilla/plugins/flashplugin-alternative.so  >> ~/Desktop/firefox-report.txt
file /etc/alternatives/mozilla-flashplugin  >> ~/Desktop/firefox-report.txt
file /var/lib/flashplugin-installer/npwrapper.libflashplayer.so  >> ~/Desktop/firefox-report.txt
firefox ~/Desktop/firefox-report.txt
```

---

### Post by wwwbrowse on 2010-08-24
thanks for your time. Here's the info requested.

No flash showing in about:plugins

Firefox version:-

Mozilla/5.0 (X11; U; Linux x86_64; en-GB; rv:1.9.2.8) Gecko/20100723 Ubuntu/10.04 (lucid) Firefox/3.6.8

System info:-

Ubuntu Architecture

Linux david-desktop 2.6.32-24-generic #39-Ubuntu SMP Wed Jul 28 05:14:15 UTC 2010 x86_64 GNU/Linux

Ubuntu Version

DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=10.04
DISTRIB_CODENAME=lucid
DISTRIB_DESCRIPTION="Ubuntu 10.04.1 LTS"

Firefox Packages

firefox						install
firefox-branding				install
firefox-gnome-support				install

Firefox binaries

/usr/bin/firefox
/usr/bin/firefox: symbolic link to `../lib/firefox-3.6.8/firefox.sh'
/usr/local/bin/firefox: ERROR: cannot open `/usr/local/bin/firefox' (No such file or directory)
/opt/firefox/firefox: ERROR: cannot open `/opt/firefox/firefox' (No such file or directory)

Firefox divertion

/usr/bin/firefox.ubuntu: ERROR: cannot open `/usr/bin/firefox.ubuntu' (No such file or directory)

Sources

google-chrome.list
google-chrome.list.save
lucid-partner.list
lucid-partner.list.save
playonlinux.list
playonlinux.list.save

Flash packages

flashplugin-installer				install
flashplugin-nonfree				install

Plugin locations

/usr/lib/flashplugin-installer/libflashplayer.so


Flash symlinks

/usr/lib/firefox-addons/plugins/libflashplayer.so: ERROR: cannot open `/usr/lib/firefox-addons/plugins/libflashplayer.so' (No such file or directory)
/usr/lib/mozilla/plugins/flashplugin-alternative.so: ERROR: cannot open `/usr/lib/mozilla/plugins/flashplugin-alternative.so' (No such file or directory)
/etc/alternatives/mozilla-flashplugin: ERROR: cannot open `/etc/alternatives/mozilla-flashplugin' (No such file or directory)
/var/lib/flashplugin-installer/npwrapper.libflashplayer.so: ERROR: cannot open `/var/lib/flashplugin-installer/npwrapper.libflashplayer.so' (No such file or directory)

---

### Post by lovinglinux on 2010-08-24
Try this:

```
sudo apt-get purge nspluginwrapper
sudo apt-get purge flashplugin-installer
sudo apt-get purge flashplugin-nonfree
sudo apt-get purge adobe-flashplugin
sudo apt-get install flashplugin-nonfree
```

---

### Post by wwwbrowse on 2010-08-24
unfortunately I get the same errors:-


Flash Plugin installed.
nspluginwrapper: no appropriate viewer found for /usr/lib/flashplugin-installer/libflashplayer.so
dpkg: error processing flashplugin-installer (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of flashplugin-nonfree:
 flashplugin-nonfree depends on flashplugin-installer; however:
  Package flashplugin-installer is not configured yet.
dpkg: error processing flashplugin-nonfree (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates it's a follow-up error from a previous failure.
                            Errors were encountered while processing:
 flashplugin-installer
 flashplugin-nonfree
E: Sub-process /usr/bin/dpkg returned an error code (1)

this problem started when I had to shut down Ubuntu by turning off the power because it had become unstable and it wouldn't let me shut down normally.

What does the error:- 

nspluginwrapper: no appropriate viewer found for /usr/lib/flashplugin-installer/libflashplayer.so

 mean? thanks for your help.

---

### Post by lovinglinux on 2010-08-24
Try [http://ubuntuforums.org/showpost.php?p=9751715&postcount=2](http://ubuntuforums.org/showpost.php?p=9751715&postcount=2)

---

### Post by wwwbrowse on 2010-08-24
no change. Ran same script as before and the result is the same.

when I run:-

sudo apt-get -f install

it starts downloading the flash plugin installer and adobe flash plugin. Is this what it should be doing then? I thought it just set up missing dependendies.

---

### Post by dagdeniz on 2010-08-24
By the way, did you try placing libflashplayer.so to the plugins folder manually? For Firefox, it works (you may have to tell Chrome where the plugin is). Just download and extract the file from Adobe's website: 
[http://get.adobe.com/flashplayer/thankyou/?installer=Flash_Player_10.1_for_Linux_%28.tar.gz%29](http://get.adobe.com/flashplayer/thankyou/?installer=Flash_Player_10.1_for_Linux_%28.tar.gz%29)
Then, copy-paste the file into /home/username/.mozilla/plugins (create the plugins folder if it does not exist). 
Then start Firefox and flash should work.

---

### Post by wwwbrowse on 2010-08-24
It seems to be the same error as this:-

[https://bugs.launchpad.net/ubuntu/+source/flashplugin-nonfree/+bug/603393](https://bugs.launchpad.net/ubuntu/+source/flashplugin-nonfree/+bug/603393)

now how do I solve it.

---

### Post by LowSky on 2010-08-24
go to the adobe website and install the deb version
[http://get2.adobe.com/flashplayer/otherversions/](http://get2.adobe.com/flashplayer/otherversions/)

Or if that doesnt work try this:
go here
[http://get2.adobe.com/flashplayer/otherversions/](http://get2.adobe.com/flashplayer/otherversions/)
grab the .tar.gz version

go to /home folder,  press Ctrl+H
find .mozilla folder, open it.
create a new folder named plugins

now open the .tar.gz take the flash file and move it to the new plugins folder


hopefully that works

---

### Post by wwwbrowse on 2010-08-24
tried creating plugins folder and adding flash file there but no luck.

---

### Post by lovinglinux on 2010-08-24
Try to disable the partner repository then repeat the commands below:

```
sudo apt-get purge nspluginwrapper
sudo apt-get purge flashplugin-installer
sudo apt-get purge flashplugin-nonfree
sudo apt-get purge adobe-flashplugin
sudo apt-get install flashplugin-nonfree
```

---

### Post by wwwbrowse on 2010-08-25
makes no difference same errors.

---

### Post by wwwbrowse on 2010-08-25
when I try installing from a get Adobe Flash link from a web page and select apt 9.04+ I get this error :- adobe-flashplugin is virtual.

This error is documented here:- [https://bugs.launchpad.net/ubuntu/+source/apturl/+bug/554449](https://bugs.launchpad.net/ubuntu/+source/apturl/+bug/554449)

When I try installing using the Ubuntu Software Centre I can't ,             adobe flashplugin 10 is not available for this type of computer    (amd64).

So I installed the 64bit Flash as in here:-http://blog.mattrudge.net/2010/05/03/installing-flash-player-on-ubuntu-10-04-64-bit/

Firefox works with this now but no flash in Chrome.

---

