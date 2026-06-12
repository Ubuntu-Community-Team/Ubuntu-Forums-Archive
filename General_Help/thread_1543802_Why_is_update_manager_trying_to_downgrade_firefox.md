---
title: "Why is update manager trying to downgrade firefox?"
date: 2010-08-01
forum: General Help
---

### Post by Schrute Farms on 2010-08-01
Hello,
I am running Karmic 64 bit on my old desktop.  Not too long ago the update manager upgraded Firefox to version 3.6.7.  Everything is working just fine.  Now my upgrade manager wants to downgrade it back to version 3.5.
Does anyone know why that is?  Is there anyway I can remove those from the upgrade manager?  Or could the upgrade manager just be giving me bad information?
I want to keep the version I have & get those update options out of the upgrade manager.
Thanks in advance.

---

### Post by lovinglinux on 2010-08-01
It is not trying to do that here (Karmic 64bit on a VM).

Please provide the output of the following commands and instructions. This will make sure I will have a good understanding of your Firefox installation, so I don't need to guess what might be happening to your system:

**1 - Firefox version and architecture**

To find Firefox version and architecture, click "Help >> About Mozilla Firefox" in the menu. The info will be located at the bottom of the info dialog:

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

### Post by Bachstelze on 2010-08-01
> **lovinglinux said:**
> 
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

lolwut?

---

### Post by lovinglinux on 2010-08-01
> **Bachstelze said:**
> lolwut?

I know, not elegant, but it is better than trying to figure out what users have done before asking for help. I have created this script after helping an user that was complaining about flash not being able to work. After several attempts to find the problem, I realized he was running a 32bit version of Firefox, on a 64bit system, installed on the /opt folder. Nevertheless, the most bizarre issue I have found related to flash was from a couple of users running flash from Wine.

---

### Post by Schrute Farms on 2010-08-01
Hello,
I'm not sure how to make the screenshot show here in the post, but I uploaded it as an attachment.  As you can see, all it says is that it's Firefox 3.6.7.  It doesn't give any of the other information shown.  I can tell you that it upgraded by the Update manager.

When I run your commands I get this:

Ubuntu Architecture

Linux basement 2.6.31-22-generic #60-Ubuntu SMP Thu May 27 02:41:03 UTC 2010 x86_64 GNU/Linux

Ubuntu Version

DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=9.10
DISTRIB_CODENAME=karmic
DISTRIB_DESCRIPTION="Ubuntu 9.10"

Firefox Packages

firefox						install
firefox-3.5					install
firefox-3.5-branding				install
firefox-3.5-gnome-support			install
firefox-branding				install
firefox-gnome-support				install

Firefox binaries

/usr/bin/firefox
/usr/bin/firefox: symbolic link to `../lib/firefox-3.6.7/firefox.sh'
/usr/local/bin/firefox: ERROR: cannot open `/usr/local/bin/firefox' (No such file or directory)
/opt/firefox/firefox: ERROR: cannot open `/opt/firefox/firefox' (No such file or directory)

Firefox divertion

/usr/bin/firefox.ubuntu: ERROR: cannot open `/usr/bin/firefox.ubuntu' (No such file or directory)

Sources

---

### Post by Schrute Farms on 2010-08-01
Ok, I figured out the "about Firefox" glitch.  I just had to make the window bigger.  See the attachment.  If I'm reading it right, it is the 64 bit version of Firefox.

Many thanks.

---

### Post by lovinglinux on 2010-08-02
> **Schrute Farms said:**
> 
firefox						install
firefox-3.5					install
firefox-3.5-branding				install
firefox-3.5-gnome-support			install
firefox-branding				install
firefox-gnome-support				install


Don't worry. Firefox 3.5 is just a dummy package. You should go ahead and accept the updates. They will in fact update your 3.6.7 to 3.6.8.

---

### Post by Schrute Farms on 2010-08-02
Thank you very much.  That is what I wanted to hear.  I tried the update and it did what you said it would.  Now running 3.6.8

---

### Post by lovinglinux on 2010-08-02
> **Schrute Farms said:**
> Thank you very much.  That is what I wanted to hear.  I tried the update and it did what you said it would.  Now running 3.6.8

;)

---

