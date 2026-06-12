---
title: "How do I remove swiftfox as installed by the script?"
date: 2006-06-18
forum: General Help
---

### Post by Steveire on 2006-06-18
I used the script [here](http://pykeylogger.sourceforge.net/wiki/index.php/Ubuntu:Chronicles#Install_Swiftfox) to install swiftfox on my box in the hope that it would [open folders in konqueror](http://ubuntuforums.org/showthread.php?t=194334) as I expected. It doesn't. That's an ongoing issue.

Swiftfox made my font's crap, and I have not seen any increased optimisation as a result of using it, so I want to remove it. Looking at the script, it seems to make some symbolic links to make my box launch swiftfox when I open firefox.

```

echo -e "\nLinking plugins\n"
cd /opt/swiftfox/plugins/
sudo ln -s -f $PLUGINPATH/* .
check_exit_status

echo -e "\nLinking firefox launcher to Swiftfox\n"
sudo dpkg-divert --divert /usr/bin/firefox.ubuntu --rename /usr/bin/firefox
check_exit_status
sudo ln -s /opt/swiftfox/firefox /usr/bin/firefox
check_exit_status
sudo dpkg-divert --divert /usr/bin/mozilla-firefox.ubuntu --rename /usr/bin/mozilla-firefox
check_exit_status
sudo ln -s /opt/swiftfox/firefox /usr/bin/mozilla-firefox
check_exit_status

```
It seems to me that if I remove the symbolic links, i'll be using my old firefox again, but I don't have any experience or making or removing symbolic links or using dpkg-divert.

Can you help me?

---

### Post by it.henrik on 2006-06-18
A tip for the future... ;)

usually its not a very good idea to run scripts that does something you do not understand. ESPECIALLY if it wants your root password.

---

### Post by yopnono on 2006-06-18
Just uninstall remove the swiftfox. Then reinstall the dapper firefox.

---

### Post by Steveire on 2006-06-18
Well I had a look at it beforehand and I was happy that it wasn't malicious.

I can currently use my previous installation by running firefox.ubuntu. So I assume I can do something like
```

sudo rm /usr/bin/firefox
sudo rm /usr/bin/mozilla-firefox
sudo dpkg-divert --divert /usr/bin/firefox --rename /usr/bin/firefox.ubuntu
sudo dpkg-divert --divert /usr/bin/mozilla-firefox --rename /usr/bin/mozilla-firefox.ubuntu
sudo rm -Rf /opt/swiftfox

```
I'm not worried about the plugin links, because they'd be deleted if I removed the /opt/swiftfox directory. I've never used dpkg-divert before though, so I want to know if that is correct use.

---

### Post by aysiu on 2006-06-18
I think it'd be something like this: ```
sudo rm /usr/bin/firefox
sudo dpkg-divert --rename --remove /usr/bin/firefox
sudo rm /usr/bin/mozilla-firefox
sudo dpkg-divert --rename --remove /usr/bin/mozilla-firefox
sudo rm -rf /opt/swiftfox
```

---

