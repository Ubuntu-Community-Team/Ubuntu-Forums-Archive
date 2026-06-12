---
title: "No Input Methods in SKIM"
date: 2006-02-18
forum: General Help
---

### Post by OneWingedAngel on 2006-02-18
I've just installed SKIM (with anthy and tomoe as backends), and I can't get it to show the IM menu. I made sure my locale ( en_GB.UTF-8 ) was in the supported locales in the config dialog, set LANG & LC_CTYPE in /etc/environment, set the XIM vars in /etc/X11/Xsession.d, and still no joy. I don't remember it being this difficult in Debian, and since it's basically the same system I can't see what I'm doing wrong here.

I've probably forgotten something really obvious, so can anyone help?

BTW, I built the whole setup from source, since the breezy packages are broken, out of date and SKIM-less.

---

### Post by Single on 2006-02-18
Which version of Skim are you using? I had the same problem with Skim 1.4.3. But the latest version automagically works. \\:D/

---

### Post by OneWingedAngel on 2006-02-18
Using scim/skim 1.4.4, scim-anthy 0.9.0, skim-scim-anthy 0.9.0.1 & scim-tomoe 0.2.0

What do you have in /etc/environment & /etc/X11/Xsession.d/75custom-scim_init?

I really miss being able to type Japanese :(

---

### Post by Single on 2006-02-18
I use scim-tables-0.5.6 and scim-pinyin-0.5.91.
Does your scim work on Gtk apps? Just to make sure that it is not a backend problem.

```

jenfoong@ubuntu:~$ cat /etc/environment
LANGUAGE="en"

LANG=en_US.UTF-8
LC_CTYPE=zh_CN.UTF-8

jenfoong@ubuntu:~$ cat /etc/X11/Xsession.d/75custom-scim_init
export XMODIFIERS="@im=SCIM"
export GTK_IM_MODULE="scim"
export XIM_PROGRAM="scim -d"
jenfoong@ubuntu:~$

```

---

### Post by OneWingedAngel on 2006-02-18
Doesn't work in GTK apps (1 or 2). Your files are pretty much the same as mine, except I have an extra 'QT_IM_MODULE=xim' in /etc/Xsession.d/environment, and my locale stuff is set to en_GB.UTF-8 (I enabled this locale in skim, which worked for both Debian and Gentoo).
I'm going to try putting the XIM stuff in ~/.kde/Autostart (I remember doing this in Debian).
--EDIT--
No joy :(

---

### Post by Single on 2006-02-19
What is the content of your /etc/gtk-2.0/gtk.immodules ?

From [http://www.scim-im.org/wiki/documentation/installation_and_configuration/ubuntu_kubuntu]("http://www.scim-im.org/wiki/documentation/installation_and_configuration/ubuntu_kubuntu")
> 
Gtk and Qt configuration
Gtk
 As root, execute the following:
 
# gtk-query-immodules-2.0 > /etc/gtk-2.0/gtk.immodules

Qt
 If the qtconfig package is not already installed, install it with Synaptic, Kynaptic or apt-get.
Run qtconfig, and in the Interface tab, choose Over-the-spot as the XIM input style. // I did this as well

End of the configuration
 Restart your X session or reboot.       // quite important I guess , as my skim only started to work after the reboot.
You can now invoke scim with Ctrl+Space   // if the window focus is on Gtk apps, it shows the scim input window, otherwise it show skim input window on Kde apps.


I had problems with Skim, but Scim has never failed. It always shows up on launch of Gtk apps. Maybe you should make sure scim works first.

Note that I use Kde 3.5.1, and I haven't put scim or skim in AutoStart. In the Configure window, under "X Window", tick the checkbox "Start skim ..." , and it starts itself after login.

---

### Post by OneWingedAngel on 2006-02-19
I did the GTK setup (must have missed that step), and now it works in GTK apps. I'd already done the Qt step, though.

After quitting GIMP, the little keyboard icon stayed (I thought it was fixed then), but Ctrl-Space didn't make the IM popup appear in KWord, so I must be missing something on the Qt side. No joy with GTK 1 stuff either, so I'm guessing XIM isn't set up right.

---

### Post by Single on 2006-02-19
I don't know much so I don't know how to help.

I attach the config files here for your reference.

~/.scim/config
~/.scim/global
~/.kde/share/config/skimrc

---

### Post by OneWingedAngel on 2006-02-23
Thanks, but it didn't help. I've tried a few more things:

I noticed im-switch was undoing the stuff in Xsession.d, so rather than work against it, I put the IM stuff into ~/.xinput.d/en_GB . Result: now SCIM is the default IM in GTK 2 apps (no change in other apps).

I built custom Qt packages with the immodule patch, then built & installed scim-qtimm. Result: starting a Qt/KDE app in Konsole brings up the message:

ScimInputContextPlugin()

So it should be working, but doesn't (Ctrl+Space does nothing).

I suppose having input in GTK 2 apps is a start, but seeing as I use mainly Qt ones, it's not really enough.

Any one have any more ideas? (I'm out of them for now)

---

### Post by Single on 2006-02-24
I searched Dapper repo and found that Skim 1.4.4 is there. You might want to give it a shot and "apt-get source" it, though I can't guarantee anything.

---

### Post by OneWingedAngel on 2006-04-03
I found out what the problem was! :KS 

My home-made Qt packages (with Immodule patch) were borked. I backported the Dapper ones (it seems Ubuntu are now pre-patching the Qt libraries), along with official, non-checkinstall versions of scim, scim-anthy, skim and scim-qtimm, rebooted and it works!
I had to disable it, though (it made most of KDE, including Konqueror & Konsole) throw SIGABRTs on startup). Oh well... :-|

---

