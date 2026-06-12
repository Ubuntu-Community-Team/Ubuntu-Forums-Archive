---
title: "Chinese Language Key in."
date: 2006-04-04
forum: General Help
---

### Post by wcks48 on 2006-04-04
any package of kubuntu/ breezy enable me to write chinese words?
some suggestion pls... thanks

---

### Post by Sutekh on 2006-04-05
You could try [Ubuntu Packages - SCIM](http://packages.ubuntu.com/breezy/utils/scim).  I use this on my PC.

If this is what you want then you can install it by enabling the universe repository, by editing the apt-get sources list
```
sudo cp /etc/apt/sources.list /etc/apt/sources.list_backup
sudo nano /etc/apt/sources.list
```
Look for the lines containing **universe**, like these
```
# deb http://archive.ubuntu.com/ubuntu breezy universe
# deb-src http://archive.ubuntu.com/ubuntu breezy universe

```
and remove the #'s.

Save the file (Ctrl+O) and exit (Ctrl+X).

Finally refresh the repositories and install SCIM and the Chinese module for SCIM
```
sudo apt-get update
sudo apt-get install scim scim-chinese
```

---

### Post by njf on 2006-04-05
Scim only works for Gtk apps...
Too bad the Skim deb is only for Dapper.

---

### Post by bullpa on 2006-04-06
[QUOTE=njf]Scim only works for Gtk apps...
Too bad the Skim deb is only for Dapper.[/QUOTE]
No, that's not correct, although it requires a little tweak for KDE etc.

---

### Post by njf on 2006-04-06
Scim can only be invoked when using Gtk+ apps. Skim deb i'm referring to the deb in official repo. I got Skim working in Breezy, but only after I compiled myself and also went through a lot of hassle.

---

### Post by bullpa on 2006-04-06
[QUOTE=njf]Scim can only be invoked when using Gtk+ apps. Skim deb i'm referring to the deb in official repo. I got Skim working in Breezy, but only after I compiled myself and also went through a lot of hassle.[/QUOTE]

I have no experience with Skim, but have used SCIM for a few years. Normally you need to have scim server running with the xwindow, therefore the CTRAL+Space can involk it. I just came across a web page, FYI I copy the steps here.
```

$sudo apt-get install scim scim-modules-socket scim-modules-table scim-pinyin scim-tables-zh scim-input-pad 

$sudo sh -c " echo 'export XMODIFIERS=@im=SCIM ; export GTK_IM_MODULE="scim" ; scim -d ' > /etc/X11/Xsession.d/95xinput " 

$sudo chmod +755 /etc/X11/Xsession.d/95xinput

```
I used to use KDE, and had no problem with SCIM.

---

### Post by Sutekh on 2006-04-06
[QUOTE=njf]Scim can only be invoked when using Gtk+ apps. Skim deb i'm referring to the deb in official repo.[/QUOTE]
SCIM doesn't seem to think so
[quote=SCIM Package]Currently, SCIM supports XIM, GTK+ immodule, and Qt immodule framework[/quote]

But you *do* have to install GTK libraries to use SCIM.  I didn't fully realise that the OP was using Kubuntu/Breezy and not (what I saw for some reason) Kubuntu/Ubuntu.  

Still you could have a look at this HOWTO to try getting it going

[Ubuntu Forums -  HOWTO: Get SKIM working in breezy](http://www.ubuntuforums.org/showthread.php?t=94447)

Just change the scim-tables-ja for scim-tables-zh (the HOWTO author was using Japanese input)

---

### Post by njf on 2006-04-06
[QUOTE=bullpa]
$sudo apt-get install scim scim-modules-socket scim-modules-table scim-pinyin scim-tables-zh scim-input-pad 

$sudo sh -c " echo 'export XMODIFIERS=@im=SCIM ; export GTK_IM_MODULE="scim" ; scim -d ' > /etc/X11/Xsession.d/95xinput " 

$sudo chmod +755 /etc/X11/Xsession.d/95xinput
[/QUOTE]

I remember I have found this(or one similiar to this) solution on the web, but the fact that the first step doesn't work out of the box already made me believed that this is just another outdated solution and I didn't have the motivation to try to complete the steps.
I uninstalled scim stuff and tried again, and it works now, on qt and gtk apps.
Thanks for the correction, if I have known this earlier I would have recommend Kubuntu to my friends, but it doesn't really matter right now.

---

### Post by ezphilosophy on 2006-04-06
If you want to get scim working for chinese, check [this]("http://ubuntuforums.org/showthread.php?t=25412") out.  Very concise.

Only problem is that it won't work with firefox 1.5.  Though, I haven't checked too much to see what can be done about it.

---

