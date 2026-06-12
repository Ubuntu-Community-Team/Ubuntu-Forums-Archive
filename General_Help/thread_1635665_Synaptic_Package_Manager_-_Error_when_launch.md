---
title: "Synaptic Package Manager - Error when launch"
date: 2010-12-02
forum: General Help
---

### Post by gnufan on 2010-12-02
[SIZE=2]Hi Guys,
Please help me solved this problem. I can't afford reinstalling my lovely Lucid Lynx. Spent almost a week now to find a working solution.

Thanks![/SIZE]

[B]Ubuntu Lucid Lynx
Synaptic Package Manager returns:[/B]

[I][SIZE=1]An error occurred

The following details are provided:

E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/dpkg/status
E: The package lists or status file could not be parsed or opened.
E: _cache->open() failed, please report[/SIZE][/I]

I searched for resolution, 

ran sudo apt-get clean all  -- Good
then: sudo apt-get install
gives an error:

[I]Reading package lists... Error!
E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/dpkg/status
E: The package lists or status file could not be parsed or opened[/I].


**Contents of /etc/apt/sources.list:**

#deb cdrom:[Ubuntu 10.04.1 LTS _Lucid Lynx_ - Release i386 (20100816.1)]/ lucid main restricted
#See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
#newer versions of the distribution.

deb [http://ph.archive.ubuntu.com/ubuntu/](http://ph.archive.ubuntu.com/ubuntu/) lucid main restricted
deb-src [http://ph.archive.ubuntu.com/ubuntu/](http://ph.archive.ubuntu.com/ubuntu/) lucid main restricted

##Major bug fix updates produced after the final release of the
## distribution.
deb [http://ph.archive.ubuntu.com/ubuntu/](http://ph.archive.ubuntu.com/ubuntu/) lucid-updates main restricted
deb-src [http://ph.archive.ubuntu.com/ubuntu/](http://ph.archive.ubuntu.com/ubuntu/) lucid-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://ph.archive.ubuntu.com/ubuntu/](http://ph.archive.ubuntu.com/ubuntu/) lucid universe
deb-src [http://ph.archive.ubuntu.com/ubuntu/](http://ph.archive.ubuntu.com/ubuntu/) lucid universe
deb [http://ph.archive.ubuntu.com/ubuntu/](http://ph.archive.ubuntu.com/ubuntu/) lucid-updates universe
deb-src [http://ph.archive.ubuntu.com/ubuntu/](http://ph.archive.ubuntu.com/ubuntu/) lucid-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://ph.archive.ubuntu.com/ubuntu/](http://ph.archive.ubuntu.com/ubuntu/) lucid multiverse
deb-src [http://ph.archive.ubuntu.com/ubuntu/](http://ph.archive.ubuntu.com/ubuntu/) lucid multiverse
deb [http://ph.archive.ubuntu.com/ubuntu/](http://ph.archive.ubuntu.com/ubuntu/) lucid-updates multiverse
deb-src [http://ph.archive.ubuntu.com/ubuntu/](http://ph.archive.ubuntu.com/ubuntu/) lucid-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://ph.archive.ubuntu.com/ubuntu/](http://ph.archive.ubuntu.com/ubuntu/) lucid-backports main restricted universe multiverse
# deb-src [http://ph.archive.ubuntu.com/ubuntu/](http://ph.archive.ubuntu.com/ubuntu/) lucid-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) lucid partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) lucid partner

deb [http://ph.archive.ubuntu.com/ubuntu/](http://ph.archive.ubuntu.com/ubuntu/) lucid-security main restricted
deb-src [http://ph.archive.ubuntu.com/ubuntu/](http://ph.archive.ubuntu.com/ubuntu/) lucid-security main restricted
deb [http://ph.archive.ubuntu.com/ubuntu/](http://ph.archive.ubuntu.com/ubuntu/) lucid-security universe
deb-src [http://ph.archive.ubuntu.com/ubuntu/](http://ph.archive.ubuntu.com/ubuntu/) lucid-security universe
deb [http://ph.archive.ubuntu.com/ubuntu/](http://ph.archive.ubuntu.com/ubuntu/) lucid-security multiverse
deb-src [http://ph.archive.ubuntu.com/ubuntu/](http://ph.archive.ubuntu.com/ubuntu/) lucid-security multiverse
deb [http://download.virtualbox.org/virtualbox/debian](http://download.virtualbox.org/virtualbox/debian) lucid non-free

---

### Post by Elfy on 2010-12-02
Try this 
```

cd /var/lib/dpkg
sudo mv status status-bad
sudo mv status-old status
sudo apt-get update
```

---

### Post by gnufan on 2010-12-02
I just did. Error after update:

[I]Reading package lists... Error!
E: Could not open file /var/lib/dpkg/status - open (2: No such file or directory)
E: The package lists or status file could not be parsed or opene[/I]d.

---

### Post by Elfy on 2010-12-02
Can you run and paste the output of ```
ls /var/lib/dpkg/status*
```

---

### Post by gnufan on 2010-12-02
ls: cannot access /var/lib/dpkg/status*: No such file or directory

---

### Post by Elfy on 2010-12-02
mmm 

Can you close and open a terminal and run 

```
tail .bash_history
```

---

### Post by plucky on 2010-12-02
@forestpiskie 

```
sudo mv /var/lib/dpkg/status-old status
```


should be ```
sudo mv /var/lib/dpkg/status-old /var/lib/dpkg/status
```
as you are not in the correct directory.

And the first command should be ```
sudo mv /var/lib/dpkg/status /var/lib/dpkg/status-bad
```

Good Luck

---

### Post by gnufan on 2010-12-02
**Results:**
sudo mv /var/lib/dpkg/status-old /var/lib/dpkg/status
mv: cannot stat `/var/lib/dpkg/status-old': No such file or directory

sudo mv /var/lib/dpkg/status /var/lib/dpkg/status-bad
mv: cannot stat `/var/lib/dpkg/status': No such file or directory

[B]
bash history:[/B]
sudo apt-get update
gedit /etc/apt/sources.list
cd /var/lib/apt/lists/
ls
sudo rm gb.archive.ubuntu.com_ubuntu_dists_maverick_main_i18n_Translation-en%5fGB
gksudo nautilus /var/lib/apt/lists

---

### Post by Elfy on 2010-12-02
whoops - not enough coffee - thanks plucky

@gnufan 

Check if the file is in your home

```
ls -al ~/status
```



If you get a result with the correct timestamp move it back. If you get any other result - then let us know

```
sudo mv ~/status /var/lib/dpkg/status
sudo apt-get update
```

---

### Post by gnufan on 2010-12-02
hmm.. not in there :(

*ls: cannot access /home/******/status: No such file or directory*

**Synaptics now gives error:**
E: Could not open file /var/lib/dpkg/status - open (2: No such file or directory)
E: The package lists or status file could not be parsed or opened.
E: _cache->open() failed, please report.

---

### Post by Elfy on 2010-12-02
```
sudo updatedb
locate status-*
```

To find where status-bad went as I got it all wrong earlier. Likely that the status file will be there as well

---

### Post by gnufan on 2010-12-02
sudo updatedb
locate status-*-->No output/result

Should I include any specific directory/path where it should look into?

---

### Post by Elfy on 2010-12-02
Try 

```
locate -b '\status-*'
```

---

### Post by gnufan on 2010-12-02
/usr/lib/rhythmbox/plugins/status-icon
/usr/lib/rhythmbox/plugins/status-icon/status-icon-preferences.ui
/usr/lib/rhythmbox/plugins/status-icon/status-icon-ui.xml
/usr/lib/rhythmbox/plugins/status-icon/status-icon.rb-plugin
/usr/share/gnome/help/empathy/C/status-icons.page
/usr/share/gnome/help/empathy/ca/status-icons.page
/usr/share/gnome/help/empathy/cs/status-icons.page
/usr/share/gnome/help/empathy/de/status-icons.page
/usr/share/gnome/help/empathy/el/status-icons.page
/usr/share/gnome/help/empathy/en_GB/status-icons.page
/usr/share/gnome/help/empathy/es/status-icons.page
/usr/share/gnome/help/empathy/fi/status-icons.page
/usr/share/gnome/help/empathy/fr/status-icons.page
/usr/share/gnome/help/empathy/it/status-icons.page
/usr/share/gnome/help/empathy/ru/status-icons.page
/usr/share/gnome/help/empathy/sv/status-icons.page
/var/lib/defoma/status-cache

---

### Post by Elfy on 2010-12-02
Please post your bash history from just before I got you to run sudo mv /var/lib/dpkg/status status-bad

Look for a cd command prior to that and paste it from there please.

---

### Post by gnufan on 2010-12-02
Thanks for the patience in resolving this issue. :)

here's the **bash history:**
cd ~
sudo dpkg --configure -a
gedit dpkg
gedit dpkg --configure -a
gedit dpkg --configure
gedit dpkg -configure
gedit dpkg configure
gedit /var/lib/dpkg/status
su
quit
exit
sudo get-apt install
nslookup
sudo rm /var/lib/apt/lists/* -vf
sudo apt-get clean all
sudo apt-get update
gksu gedit /etc/apt/sources.list
sudo apt-get clean all
sudo apt-get update
**sudo mv /var/lib/dpkg/status status-bad**
sudo mv /var/lib/dpkg/status-old status
sudo apt-get update

---

### Post by plucky on 2010-12-02
> sudo mv /var/lib/dpkg/status status-bad
sudo mv /var/lib/dpkg/status-old status

There should be a files called status-bad and status in your /home directory

From a terminal ```
cd ~
ls
```

If there is a file called status,and only if ,then ```
sudo mv status /var/lib/dpkg/status
```

and then try running ```
sudo apt-get update
```

Good Luck

---

### Post by gnufan on 2010-12-03
I don't have status and status-old in /var/lib/dpkg.

*mv: cannot stat `/var/lib/dpkg/status': No such file or directory*

---

### Post by plucky on 2010-12-03
> **gnufan said:**
> I don't have status and status-old in /var/lib/dpkg.

*mv: cannot stat `/var/lib/dpkg/status': No such file or directory*

That is because you moved them out into your /home folder when you ran Forestpiskie's commands.

It should be in your /home directory

```
cd ~
ls
``` and see if they are there.

If they are there then run the second command which should move it out of the /home directory and back into the correct directory.

If there are not there post back the output of the ls command.We will have to search for it.


Good Luck

---

### Post by gnufan on 2010-12-03
my /home directory does not contain it as well.

But good news is.. it's already **SOLVED**! :D 
Solution:
I found *dpkg.status.0 *file in /var/backups;
    >  cp dpkg.status.0 /var/lib/dpkg
     mv dpkg.status.0 statusand I have a fresh copy of status in /var/lib/dpkg

Tried Synaptics, no error return.
Now running update <sudo apt-get update>

Thanks for your help guys. :D

---

