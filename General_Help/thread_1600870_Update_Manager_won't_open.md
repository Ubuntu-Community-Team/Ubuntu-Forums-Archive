---
title: "Update Manager won't open"
date: 2010-10-19
forum: General Help
---

### Post by innkeeper on 2010-10-19
I've been using 10.04 for some time, but now Update Manager won't open, nor will Ubuntu Software.  With all the apparent problems, I don't plan to upgrade to 10.10, but I do like to keep my OS updated and current.

---

### Post by sikander3786 on 2010-10-19
Please type

```
update-manager
```

in a terminal and post the output.

---

### Post by innkeeper on 2010-10-19
> **sikander3786 said:**
> Please type

```
update-manager
```in a terminal and post the output.

Thanks much.  Also saw "sudo apt-get- update" and that jarred something loose so the Update Manager AND Software Center both open now.

---

### Post by insomniac768 on 2010-11-21
> **sikander3786 said:**
> Please type

```
update-manager
```in a terminal and post the output.
I am having the same issue. Upgraded today to 10.10 and that is when it started.

Here is the output from the command.

```
update-manager
/usr/bin/update-manager:104: Warning: g_object_unref: assertion `G_IS_OBJECT (object)' failed
  app = UpdateManager(data_dir, options)
/usr/lib/python2.6/dist-packages/UpdateManager/UpdateManager.py:1075: Warning: g_object_notify: assertion `G_IS_OBJECT (object)' failed
  gtk.main_iteration()
/usr/lib/python2.6/dist-packages/UpdateManager/UpdateManager.py:1075: GtkWarning: IA__gtk_tree_view_column_get_expand: assertion `GTK_IS_TREE_VIEW_COLUMN (tree_column)' failed
  gtk.main_iteration()
/usr/lib/python2.6/dist-packages/UpdateManager/GtkProgress.py:68: Warning: g_object_notify: assertion `G_IS_OBJECT (object)' failed
  gtk.main_iteration()
/usr/lib/python2.6/dist-packages/UpdateManager/GtkProgress.py:68: GtkWarning: IA__gtk_tree_view_column_get_expand: assertion `GTK_IS_TREE_VIEW_COLUMN (tree_column)' failed
  gtk.main_iteration()
/usr/lib/python2.6/dist-packages/UpdateManager/UpdateManager.py:866: Warning: g_object_notify: assertion `G_IS_OBJECT (object)' failed
  gtk.main_iteration()
/usr/lib/python2.6/dist-packages/UpdateManager/UpdateManager.py:866: GtkWarning: IA__gtk_tree_view_column_get_expand: assertion `GTK_IS_TREE_VIEW_COLUMN (tree_column)' failed
  gtk.main_iteration()
/usr/lib/python2.6/dist-packages/UpdateManager/UpdateManager.py:466: GtkWarning: IA__gtk_tree_view_column_cell_set_cell_data: assertion `GTK_IS_TREE_VIEW_COLUMN (tree_column)' failed
  gtk.main_iteration()
/usr/lib/python2.6/dist-packages/UpdateManager/UpdateManager.py:466: GtkWarning: IA__gtk_tree_view_column_cell_get_size: assertion `GTK_IS_TREE_VIEW_COLUMN (tree_column)' failed
  gtk.main_iteration()
/usr/lib/python2.6/dist-packages/UpdateManager/UpdateManager.py:466: Warning: g_object_notify: assertion `G_IS_OBJECT (object)' failed
  gtk.main_iteration()
/usr/lib/python2.6/dist-packages/UpdateManager/UpdateManager.py:466: GtkWarning: IA__gtk_tree_view_column_get_expand: assertion `GTK_IS_TREE_VIEW_COLUMN (tree_column)' failed
  gtk.main_iteration()
Segmentation fault
```

---

### Post by sikander3786 on 2010-11-22
> **insomniac768 said:**
> I am having the same issue. Upgraded today to 10.10 and that is when it started.

Here is the output from the command.

...........
Did you try reinstalling update-manager by

```
sudo apt-get install --reinstall update-manager
```

---

### Post by insomniac768 on 2010-11-22
> **sikander3786 said:**
> Did you try reinstalling update-manager by

```
sudo apt-get install --reinstall update-manager
```

Yes, tried that, but it didn't work. I finally figured it out though. When I upgraded it only did a partial upgrade for some reason. So I went into the package manager and clicked status and saw that several packages needed upgraded. So I marked them all to be upgraded and ran it. Once it finished everything was working again as it should be. :popcorn:

---

### Post by hub_cap on 2011-05-03
fred@D610:~$ update-manager
Traceback (most recent call last):
  File "/usr/bin/update-manager", line 29, in <module>
    import gtk
  File "/usr/lib/pymodules/python2.6/gtk-2.0/gtk/__init__.py", line 30, in <module>
    import gobject as _gobject
  File "/usr/lib/python2.6/dist-packages/gobject/__init__.py", line 26, in <module>
    from glib import spawn_async, idle_add, timeout_add, timeout_add_seconds, \
  File "/usr/lib/python2.6/dist-packages/glib/__init__.py", line 22, in <module>
    from glib._glib import *
ImportError: /usr/lib/python2.6/dist-packages/glib/_glib.so: undefined symbol: _pyglib_generic_ptr_richcompare
fred@D610:~$ 


Still can't get update manager to open

---

### Post by mörgæs on 2011-05-04
You need to provide us with more information.

Which Ubuntu?
How was it installed?
Can you update from the command line?
And so on...

If D610 refers to a Dell Latitute D610, then I can from personal experience say that everything should work.

---

### Post by gpsvn on 2011-05-06
I have the same problem

[IMG]http://uppix.net/1/b/8/7d79d3e2312fed6fbc6605a8ac578.png[/IMG]

---

### Post by gpsvn on 2011-05-06
sudo apt-get install --reinstall update-manager
[sudo] password for gpsvn: 
Reading package lists... Error!
E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/qa.archive.ubuntu.com_ubuntu_dists_natty_main_binary-i386_Packages
E: The package lists or status file could not be parsed or opened.

---

### Post by mörgæs on 2011-05-07
Have you tried to boot the machine and run

```
sudo apt-get clean
sudo apt-get update
sudo apt-get upgrade
```

?

---

### Post by dannyx on 2011-05-09
> **mörgæs said:**
> Have you tried to boot the machine and run

```
sudo apt-get clean
sudo apt-get update
sudo apt-get upgrade
```?

:KSWorked!:KS
:popcorn:

---

### Post by gpsvn on 2011-05-20
Works

Thank you.

---

### Post by andremsantos on 2011-05-20
Hey, i'm using ubuntu 11.04 and te picture that gpsvn put also apear to me when i try to update... i've tryed the commands 

sudo apt-get clean
sudo apt-get update
sudo apt-get upgrade

and when i do the 2nd, it show the message "A ler as listas de pacotes... Erro !
E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/archive.canonical.com_ubuntu_dists_natty_partner_binary-amd64_Packages
E: As listas de pacotes ou o ficheiro de status não pôde ser analisado ou aberto"

How can i fix it?

---

### Post by linuxinstalledfromhdd on 2011-05-20
Check your source.list file.

Post results here so we can check it for you..

sudo gedit /etc/apt/source.list

---

### Post by andremsantos on 2011-05-20
say: "sudo: gedit/etc/apt/source.list: command not found"

---

### Post by linuxinstalledfromhdd on 2011-05-20
try:
sudo apt-get install gedit
sudo gedit /etc/apt/source.list

---

### Post by andremsantos on 2011-05-20
give me the same message from my 1st post!

---

### Post by linuxinstalledfromhdd on 2011-05-20
if you don't have a source.list file, you need to reinstall Ubuntu.

Might I suggest you try this first:

[http://cinderbox.net/2010/12/23/to-do-list-after-installing-ubuntu-10-10-aka-maverick-meerkat/](http://cinderbox.net/2010/12/23/to-do-list-after-installing-ubuntu-10-10-aka-maverick-meerkat/)

---

### Post by plucky on 2011-05-20
> **andremsantos said:**
> say: "sudo: gedit/etc/apt/source.list: command not found"

There should be a space between gedit and /etc

Also as it is a GUI apt you should use gksudo not sudo.

So ```
gksudo gedit /etc/apt/sources.list
```

Good Luck

---

### Post by linuxinstalledfromhdd on 2011-05-20
I saw that space missing. I reposted it again with a space. 

If they can't find their source.list file, there isn't much anyone here can do. :)

---

### Post by andremsantos on 2011-05-21
hey! I've reintalled and the same problem apears today... when i put the code, this is what it shows:

# deb cdrom:[Ubuntu 11.04 _Natty Narwhal_ - Release amd64 (20110427.1)]/ natty main restricted

# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.
deb [http://pt.archive.ubuntu.com/ubuntu/](http://pt.archive.ubuntu.com/ubuntu/) natty main restricted
deb-src [http://pt.archive.ubuntu.com/ubuntu/](http://pt.archive.ubuntu.com/ubuntu/) natty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://pt.archive.ubuntu.com/ubuntu/](http://pt.archive.ubuntu.com/ubuntu/) natty-updates main restricted
deb-src [http://pt.archive.ubuntu.com/ubuntu/](http://pt.archive.ubuntu.com/ubuntu/) natty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://pt.archive.ubuntu.com/ubuntu/](http://pt.archive.ubuntu.com/ubuntu/) natty universe
deb-src [http://pt.archive.ubuntu.com/ubuntu/](http://pt.archive.ubuntu.com/ubuntu/) natty universe
deb [http://pt.archive.ubuntu.com/ubuntu/](http://pt.archive.ubuntu.com/ubuntu/) natty-updates universe
deb-src [http://pt.archive.ubuntu.com/ubuntu/](http://pt.archive.ubuntu.com/ubuntu/) natty-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://pt.archive.ubuntu.com/ubuntu/](http://pt.archive.ubuntu.com/ubuntu/) natty multiverse
deb-src [http://pt.archive.ubuntu.com/ubuntu/](http://pt.archive.ubuntu.com/ubuntu/) natty multiverse
deb [http://pt.archive.ubuntu.com/ubuntu/](http://pt.archive.ubuntu.com/ubuntu/) natty-updates multiverse
deb-src [http://pt.archive.ubuntu.com/ubuntu/](http://pt.archive.ubuntu.com/ubuntu/) natty-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://pt.archive.ubuntu.com/ubuntu/](http://pt.archive.ubuntu.com/ubuntu/) natty-backports main restricted universe multiverse
# deb-src [http://pt.archive.ubuntu.com/ubuntu/](http://pt.archive.ubuntu.com/ubuntu/) natty-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) natty-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) natty-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) natty-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) natty-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) natty-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) natty-security multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) natty partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) natty partner

## Uncomment the following two lines to add software from Ubuntu's
## 'extras' repository.
## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
# deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) natty main
# deb-src [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) natty main


What should i do? thank guys!

---

### Post by DabNab on 2011-05-21
Well my Ubuntu Software Centre My Update manager and printing wont open

---

### Post by linuxinstalledfromhdd on 2011-05-21
I think you may have gotten to the point where reinstallation is a really good idea in your situation.  This time follow a step by step guide like:

[FONT=monospace]http://cinderbox.net/2011/04/03/to-do-list-after-installing-ubuntu-11-04-aka-natty-narwhal/[/FONT]

---

### Post by mörgæs on 2011-05-21
If the problem is

> **andremsantos said:**
> 
E: Problem with MergeList /var/lib/apt/lists/archive.canonical.com_ubuntu_dists_natty_partner_binary-amd64_Packages


try running 

```
sudo rm /var/lib/apt/lists/* -vf
sudo apt-get clean
sudo apt-get update
sudo apt-get upgrade
```

---

### Post by jMerlin4 on 2011-09-29
I'm running Ubuntu 10.4 (Lucid Lynx) and when I ran "sudo gedit /etc/apt/source.list" in terminal, my source.list popped up, but the file is blank. What does this mean?

---

### Post by plucky on 2011-09-29
> **jMerlin4 said:**
> I'm running Ubuntu 10.4 (Lucid Lynx) and when I ran "sudo gedit /etc/apt/source.list" in terminal, my source.list popped up, but the file is blank. What does this mean?

The file is **sources.list** not source.list and you should use gksudo instead of sudo for graphical applications.


Good luck

---

### Post by jMerlin4 on 2011-09-30
I did that and the window that is attached showed up. I hit "Retry" several times, but to no avail. The only time something did show in the file is when I highlighted " Western (ISO-8859-15)" and hit retry. But I was under the impression this isn't the file I'm meant to see when issuing that command. Was I wrong?

---

### Post by plucky on 2011-09-30
> **jMerlin4 said:**
> I did that and the window that is attached showed up. I hit "Retry" several times, but to no avail. The only time something did show in the file is when I highlighted " Western (ISO-8859-15)" and hit retry. But I was under the impression this isn't the file I'm meant to see when issuing that command. Was I wrong?

What does ```
ls -l /etc/apt
cat /etc/apt/sources.list
``` from a terminal show you?

---

### Post by jMerlin4 on 2011-09-30
plucky, I owe you a huge debt of thanks for attempting to help correct my programming illiteracy. At first I wasn't sure what fixed the problem, but I was in another thread trying to find instructions to fix yet *another  *problem that's been giving me the blues and, inadvertently, fixed this one. However, if I could ask yet another boon, I'll tell you what I found that fixed it and you tell me whether or not this is a good solution, or if I should go on the hunt for something else.

I've got an iPod Classic 160gb and I've been having trouble adding music to it using various Ubuntu programs for close to a week and a half. I've been scouring the web and the forums trying to find some instructions on this (installed gtkpod; can add music fine but it won't play; still working on that one) and came across this thread: [http://ubuntuforums.org/showthread.php?t=906217&highlight=ubuntu+ipod+classic+160gb](http://ubuntuforums.org/showthread.php?t=906217&highlight=ubuntu+ipod+classic+160gb). It was following the instructions listed first (under the "Update your sources" heading) that fixed the problem I was having w/ my Update Manager. Not being 100% sure exactly what "hardy" is, my questions are these:

1) Should I continue looking for ways to fix the problem I was having, in the even that this particular solution doesn't "take" over the long-term? 2) Is there something specific I did in the past that I can avoid doing in the future to keep this problem from happening again?

Any help is greatly appreciated.

---

### Post by plucky on 2011-09-30
> It was following the instructions listed first (under the "Update your sources" heading) that fixed the problem I was having w/ my Update Manager. Not being 100% sure exactly what "hardy" is

Hardy is version 8.04 so if you are using that list,then it is out of date.

As you are running Lucid (10.04),you will have to replace your sources list with one that uses the Lucid repositories.

Go [Here](http://repogen.simplylinux.ch/) to generate another sources.list for your Lucid system.

This is what my sources.list contains on my system running Lucid ```
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://gb.archive.ubuntu.com/ubuntu/ lucid main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://gb.archive.ubuntu.com/ubuntu/ lucid-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://gb.archive.ubuntu.com/ubuntu/ lucid universe
deb http://gb.archive.ubuntu.com/ubuntu/ lucid-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://gb.archive.ubuntu.com/ubuntu/ lucid multiverse
deb http://gb.archive.ubuntu.com/ubuntu/ lucid-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb http://archive.canonical.com/ubuntu lucid partner


deb http://security.ubuntu.com/ubuntu/ lucid-security restricted main multiverse universe

```

Good Luck

---

### Post by jMerlin4 on 2011-09-30
Got it to work. And thanks for that link. It made available a few repositories I didn't know about.

---

