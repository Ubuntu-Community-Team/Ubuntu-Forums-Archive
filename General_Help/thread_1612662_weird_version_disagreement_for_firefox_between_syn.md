---
title: "weird version disagreement for firefox between synaptic and firefox itself"
date: 2010-11-03
forum: General Help
---

### Post by Lynx Phoenix on 2010-11-03
firefox tells me its version 3.6.3 from the about box and when i check for updates it tells me there is a security etc. update available but i dont have the permissions to install it. so i check the firefox website and it says the latest is 3.6.12. i check synaptic and 3.6.12 is the version it says i have installed - so what gives?

running firefox with sudo lets me update normally, but i dont wanna run the update since synaptic tells me it already has the latest version. so how do i get them to agree on a version so i dont have duplicates and weird version disagreements running around?

edit - 
_**[SIZE=3]SOLUTION:[/SIZE]**_ thanks to lovinglinux for the help on this. 

The above version disagreement is caused by the fact that vanilla firefox and the ubuntuzilla version use different repositories. Go to [this page on the ubuntuzilla wiki]("http://sourceforge.net/apps/mediawiki/ubuntuzilla/index.php?title=Main_Page#Background") for how to include the ubuntuzilla repository and update firefox to the latest version.

PS: for those who dont read the rest of the thread - READ IT! important information about why NOT to run firefox from the terminal like i did and how to do it if you have to.

---

### Post by Lynx Phoenix on 2010-11-03
ok, i kept that session of firefox through sudo running for a few hours now and when i remembered it was sudoed i decided i was an complete idiot and i closed it (from File->Quit so that it would keep my tabs). then i ran it again through the terminal with just "firefox". and all the settings were wiped clean - there is only one profile in the folder, the default.

i dont understand how the heck this can happen. i ran "sudo firefox" and it ran fine but just "firefox" and it wipes my settings clean? and now each time i run "firefox" from the terminal it does the same thing again.

running it from the menu or top bar doesnt cause the setting reset. i checked the link's command line and it runs "firefox %u" which as far as i could tell from poking around a bit, has nothing to do with anything except the home page. even so, it doesnt make sense that running it with sudo once is ok, but every other time, with either sudo or not, wipes it all clean.

careful guys, dont use the terminal with firefox.

edit - btw, it still says 3.6.3...

edit2 - forgot to mention i wasnt on /home/username when i ran it; AFAIK that shouldnt affect anything and again, it ran fine the first time.

---

### Post by sikander3786 on 2010-11-03
Nice title :-)

You don't ever need to run user applications as super user. Don't put sudo infront of browsers, media players, games etc as they put the setting in the wrong directory, not /home.

If you wanted to run firefox from terminal, *firefox* was sufficient.

---

### Post by lovinglinux on 2010-11-03
NEVER use sudo for graphical interfaces, specially Firefox. When you run Firefox with sudo, it changes your profile folder ownership to root, so problems like you are experiencing happen.

To fix that, see the first item on [this list]("http://firefox-tutorials.blogspot.com/2010/05/common-issues-solutions.html").

I also don't recommend installing updates from Firefox built-in updater. It is disabled for a reason. Updates should be performed by the package manager.

About the version, type **about:** in the address bar and hit enter.

Also execute the following commands then copy the generated file, named **firefox-report.txt** from your Desktop and upload it here or paste the contents, so I can have an idea of your Firefox install setup.

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

### Post by Lynx Phoenix on 2010-11-06
ok, sorry for the very late reply. here's the output:  
```
Ubuntu Architecture

Linux lynx-desktop 2.6.35-23-generic #36-Ubuntu SMP Tue Oct 26 17:03:18 UTC 2010 i686 GNU/Linux

Ubuntu Version

DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=10.10
DISTRIB_CODENAME=maverick
DISTRIB_DESCRIPTION="Ubuntu 10.10"

Firefox Packages

firefox                        install
firefox-branding                install
firefox-gnome-support                install
firefox-mozilla-build                install

Firefox binaries

/usr/bin/firefox
/usr/bin/firefox: symbolic link to `/opt/firefox/firefox'
/usr/local/bin/firefox: ERROR: cannot open `/usr/local/bin/firefox' (No such file or directory)
/opt/firefox/firefox: POSIX shell script text executable

Firefox divertion

/usr/bin/firefox.ubuntu: symbolic link to `../lib/firefox-3.6.12/firefox.sh'

Sources

ubuntu-wine-ppa-lucid.list
ubuntu-wine-ppa-lucid.list.distUpgrade
ubuntu-wine-ppa-lucid.list.save
```i like your use of the terminal btw :cool: - anyway, it says the installed version is 3.6.12 but as i said in my above posts, firefox reports version 3.6.3 with "about:" and from the menu as well.

and to justify why i did used sudo - i know sudo is not supposed to be used lightly and i refrain from using it as much as i can, i even use "sudo -k" after using it cause, coming from windows, i get itchy about having my user password in the system for more than its needed. i tried sudo this time because i didnt want to just come crying to the forums before actually trying to solve the problem myself. i was lucky this time i guess. it didnt lose anything except my settings so all the addons and stuff are still there (but i did back up everything again just in case) so i just remade the settings. the primary reason i want to know why this happened with firefox is so i know what to suspect if it ever happens again.

---

### Post by lovinglinux on 2010-11-06
> **Lynx Phoenix said:**
> i like your use of the terminal btw :cool: - anyway, it says the installed version is 3.6.12 but as i said in my above posts, firefox reports version 3.6.3 with "about:" and from the menu as well.

The reason for that is because your default Firefox version is firefox-mozilla-build, which was installed by Ubuntuzilla repository. You need to update that package or remove it to go back to vanilla 3.6.12.

> **Lynx Phoenix said:**
> and to justify why i did used sudo - i know sudo is not supposed to be used lightly and i refrain from using it as much as i can, i even use "sudo -k" after using it cause, coming from windows, i get itchy about having my user password in the system for more than its needed. i tried sudo this time because i didnt want to just come crying to the forums before actually trying to solve the problem myself. i was lucky this time i guess. it didnt lose anything except my settings so all the addons and stuff are still there (but i did back up everything again just in case) so i just remade the settings. the primary reason i want to know why this happened with firefox is so i know what to suspect if it ever happens again.

If you ever need to use Firefox with administrative rights, use gksudo and not sudo. Be careful tho, since running the browser with root privileges is a major security risk.

---

### Post by Lynx Phoenix on 2010-11-07
thanks mate, that worked perfectly. i found out how to do it from the ubuntuzilla mediawiki on sourceforge. it seems its exactly what they expect will happen unless you add the proper repository and update through that. guess i was a bit too quick to blame ubuntu :P

anyway, i'm marking this thread solved.

---

