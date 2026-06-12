---
title: "I can't save the file in gedit"
date: 2010-05-15
forum: General Help
---

### Post by samlabs821 on 2010-05-15
Hello.I created the document in gedit and save button is disabled. It says "Changes to document 'Unsaved Document 1' will be permanently lost. saving has been disabled by system administrator"

can anybody help?

Using Ubuntu 10.04

---

### Post by StuartN on 2010-05-15
> **samlabs821 said:**
> Hello.I created the document in gedit and save button is disabled.

What is the full path of the file you are trying to save? Do you have write permission in the folder, and is there any existing file with the same name?

---

### Post by samlabs821 on 2010-05-15
> **StuartN said:**
> What is the full path of the file you are trying to save? Do you have write permission in the folder, and is there any existing file with the same name?

I am tryning to save it to Desktop(home/samlabs821/Desktop) but folder name is '&#1056;&#1072;&#1073;&#1086;&#1095;&#1080;&#1081; &#1089;&#1090;&#1086;&#1083;' in russian

---

### Post by samlabs821 on 2010-05-15
Also i can't save file at my home directory(/home/samlabs821/) which i created before

---

### Post by StuartN on 2010-05-15
> **samlabs821 said:**
> Also i can't save file at my home directory(/home/samlabs821/) which i created before

Can you open a terminal and check the permissions? The first will list the contents of Desktop and the second will list the permissions on the directory itself:

```
whoami
ls -l /home/samlabs821/Desktop/
ls -ld /home/samlabs821/Desktop/
```

Also check /home/samlabs821 because the permissions are inherited from the parent.

---

### Post by samlabs821 on 2010-05-15
> **StuartN said:**
> Can you open a terminal and check the permissions? The first will list the contents of Desktop and the second will list the permissions on the directory itself:

```
whoami
ls -l /home/samlabs821/Desktop/
ls -ld /home/samlabs821/Desktop/
```

Also check /home/samlabs821 because the permissions are inherited from the parent.

```

ls -ld /home/samlabs821/Desktop/
ls: cannot access /home/samlabs821/Desktop/: No such file or directory
ls -ld /home/samlabs821/
drwxr-xr-x 45 samlabs821 samlabs821 4096 2010-05-15 02:48 /home/samlabs821/

```

what does it mean?

---

### Post by howefield on 2010-05-15
What was the output from whoami ?

---

### Post by samlabs821 on 2010-05-15
> **howefield said:**
> What was the output from whoami ?

samlabs821

---

### Post by StuartN on 2010-05-15
> **samlabs821 said:**
> ```

ls -ld /home/samlabs821/Desktop/
ls: cannot access /home/samlabs821/Desktop/: No such file or directory
ls -ld /home/samlabs821/
drwxr-xr-x 45 samlabs821 samlabs821 4096 2010-05-15 02:48 /home/samlabs821/

```

what does it mean?

User samlabs821 can read, write and execute files in /home/samlabs821, as expected, but /home/samlabs821/Desktop does not exist. You appear to have deleted your Desktop folder.

---

### Post by samlabs821 on 2010-05-15
I think the problem in Nautilus because i updated it

---

### Post by AlexDudko on 2010-05-15
> **samlabs821 said:**
> I am tryning to save it to Desktop(home/samlabs821/Desktop) but folder name is '&#1056;&#1072;&#1073;&#1086;&#1095;&#1080;&#1081; &#1089;&#1090;&#1086;&#1083;' in russian

If you have it (the name of your Desktop folder) in Russian the way to it must be:
> /home/samalabs821/&#1056;&#1072;&#1073;&#1086;&#1095;&#1080;&#1081; &#1089;&#1090;&#1086;&#1083;

What's the output of:
> ls /home/samalabs821/&#1056;&#1072;&#1073;&#1086;&#1095;&#1080;&#1081;\ &#1089;&#1090;&#1086;&#1083;
Can you cd to that folder?
Does
> ls /home/samalabs821
show a "&#1056;&#1072;&#1073;&#1086;&#1095;&#1080;&#1081; &#1089;&#1090;&#1086;&#1083;" directory?

---

### Post by John Bean on 2010-05-15
> **samlabs821 said:**
> I am tryning to save it to Desktop(home/samlabs821/Desktop) but folder name is '&#1056;&#1072;&#1073;&#1086;&#1095;&#1080;&#1081; &#1089;&#1090;&#1086;&#1083;' in russian

Which folder is in Russian? You said you couldn't save a file to your desktop - is it literally called "Desktop" or is it actually called something else? Translation may be obscuring the real problem.

Edit: I see this point has already been raised while I was busy typing ;-)

---

### Post by samlabs821 on 2010-05-15
> **AlexDudko said:**
> If you have it (the name of your Desktop folder) in Russian the way to it must be:

What's the output of:

Can you cd to that folder?
Does

show a "&#1056;&#1072;&#1073;&#1086;&#1095;&#1080;&#1081; &#1089;&#1090;&#1086;&#1083;" directory?

yes it show but i removed this directory and created Desktop directory instead...

i noticed that print button is also disabled in gedit... it means the problem in gedit??

But when i run gedit with sudo there is no problem...

---

### Post by AlexDudko on 2010-05-15
Desktop stands for Russian "&#1056;&#1072;&#1073;&#1086;&#1095;&#1080;&#1081; &#1089;&#1090;&#1086;&#1083;", this is due to Russian system language, which made all automatically created folders in user's home directory be in Russian.

Didn't you create the Desktop folder in sudo mode?
Try to 
> sudo chown samalabs821:samalabs821 /home/samalabs821/Desktop

---

### Post by StuartN on 2010-05-15
> **samlabs821 said:**
> yes it show but i removed this directory and created Desktop directory instead...

What is the output from ls -l /home/samlabs821 ? Did you create Desktop or desktop?

---

### Post by samlabs821 on 2010-05-15
> **StuartN said:**
> What is the output from ls -l /home/samlabs821 ? Did you create Desktop or desktop?

-rwxr-xr-x  1 samlabs821 samlabs821       731 2010-05-15 00:52 autorun.inf
-rwxr-xr-x  1 samlabs821 samlabs821    114440 2010-05-14 09:34 db.sql
drwxrwxrwx  2 samlabs821 samlabs821      4096 2010-05-15 01:56 Desktop
drwxr-xr-x  2 samlabs821 samlabs821      4096 2010-05-15 07:23 Distr
-rwxr-xr-x  1 samlabs821 samlabs821 197521410 2009-10-31 15:13 eclipse-jee-galileo-SR1-linux-gtk.tar.gz
-rw-r--r--  1 samlabs821 samlabs821       179 2010-05-14 03:06 examples.desktop
drwx------  2 samlabs821 samlabs821      4096 2010-05-14 18:46 fbreader
drwx------  2 samlabs821 samlabs821      4096 2010-05-14 22:54 Frank Lampard
-rw-r--r--  1 samlabs821 samlabs821        11 2010-05-15 03:30 hjg.txt
drwx------  4 samlabs821 samlabs821      4096 2010-03-10 09:24 javaRSS
-rwxr-xr-x  1 samlabs821 samlabs821 133614094 2009-05-23 20:18 jboss-5.1.0.GA-jdk6.zip
-rwxr-xr-x  1 samlabs821 samlabs821 117266344 2009-10-29 11:08 jboss-seam-2.2.0.GA.zip
-rwxr-xr-x  1 samlabs821 samlabs821  84738557 2010-03-06 18:28 jdk-6u18-linux-i586.bin
-rwxr-xr-x  1 samlabs821 samlabs821  16728640 2010-05-14 09:35 lib.zip
drwx------  6 samlabs821 samlabs821      4096 2010-05-14 22:55 need
-rwxr-xr-x  1 samlabs821 samlabs821 213536768 2009-05-06 00:20 netbeans-6.7_m3-linux.sh
-rw-r--r--  1 samlabs821 samlabs821         0 2010-05-15 02:40 new file
drwx------  8 samlabs821 samlabs821      4096 2010-05-06 15:01 Sam
drwx------  2 samlabs821 samlabs821      4096 2010-05-14 22:52 savira
drwx------  2 samlabs821 samlabs821      4096 2010-05-11 23:28 sgpkjmr
-rwxr-xr-x  1 samlabs821 samlabs821  19944012 2009-11-02 10:19 skype-ubuntu-intrepid_2.1.0.47-1_i386.deb
-rwxr-xr-x  1 samlabs821 samlabs821 102081998 2010-03-06 18:37 sun-j2sdk1.6_1.6.0+update18_i386.deb
-rwxr-xr-x  1 samlabs821 samlabs821    792122 2010-05-14 09:41 ubuntu-tweak_0.5.4.1-1_all.deb
-rw-r--r--  1 samlabs821 samlabs821         8 2010-05-14 04:26 Unsaved Document 1
drwx------ 20 samlabs821 samlabs821      4096 2010-05-14 08:40 workspace_b
-rwxr-xr-x  1 samlabs821 samlabs821  59209971 2009-05-06 02:07 xampp-linux-1.7.1.tar.gz
drwxr-xr-x  2 samlabs821 samlabs821      4096 2010-05-14 03:10 &#1042;&#1080;&#1076;&#1077;&#1086;
drwxr-xr-x  2 samlabs821 samlabs821      4096 2010-05-14 03:10 &#1044;&#1086;&#1082;&#1091;&#1084;&#1077;&#1085;&#1090;&#1099;
drwxr-xr-x  2 samlabs821 samlabs821      4096 2010-05-14 03:10 &#1047;&#1072;&#1075;&#1088;&#1091;&#1079;&#1082;&#1080;
drwxr-xr-x  2 samlabs821 samlabs821      4096 2010-05-14 03:10 &#1050;&#1072;&#1088;&#1090;&#1080;&#1085;&#1082;&#1080;
drwx------  3 samlabs821 samlabs821      4096 2010-05-14 22:58 &#1051;&#1080;&#1073;&#1088;&#1091;&#1089;&#1077;&#1082;
drwxr-xr-x  2 samlabs821 samlabs821      4096 2010-05-14 03:10 &#1052;&#1091;&#1079;&#1099;&#1082;&#1072;
drwxr-xr-x  2 samlabs821 samlabs821      4096 2010-05-14 03:10 &#1054;&#1073;&#1097;&#1077;&#1076;&#1086;&#1089;&#1090;&#1091;&#1087;&#1085;&#1099;&#1077;
drwxr-xr-x  2 samlabs821 samlabs821      4096 2010-05-14 03:10 &#1064;&#1072;&#1073;&#1083;&#1086;&#1085;&#1099;

---

### Post by StuartN on 2010-05-15
> **samlabs821 said:**
> drwxrwxrwx  2 samlabs821 samlabs821      4096 2010-05-15 01:56 Desktop

Clearly there is an entry "Desktop" in /home/samlabs821 and it is a directory and it is owned by samlabs821 with rwx permissions, so it should be possible to save the file - unless there is a file within Desktop that is not (over)writable.

Previously this appeared not to exist:
> **samlabs821 said:**
> ```

ls -ld /home/samlabs821/Desktop/
ls: cannot access /home/samlabs821/Desktop/: No such file or directory
```

---

### Post by samlabs821 on 2010-05-15
> **StuartN said:**
> Clearly there is an entry "Desktop" in /home/samlabs821 and it is a directory and it is owned by samlabs821 with rwx permissions, so it should be possible to save the file - unless there is a file within Desktop that is not (over)writable.

Previously this appeared not to exist:


then what should I do?

---

### Post by samlabs821 on 2010-05-15
```

vim /home/samlabs821/Desktop/gedit.desktop

#!/usr/bin/env xdg-open
[Desktop Entry]
Name=gedit
GenericName=Text Editor
Comment=Edit text files
Exec=gedit %U
Terminal=false
Type=Application
StartupNotify=true
MimeType=text/plain;
Icon=accessories-text-editor
Categories=GNOME;GTK;Utility;TextEditor;
X-GNOME-DocPath=gedit/gedit.xml
X-GNOME-FullName=gedit Text Editor
X-GNOME-Bugzilla-Bugzilla=GNOME
X-GNOME-Bugzilla-Product=gedit
X-GNOME-Bugzilla-Component=general
X-GNOME-Bugzilla-Version=2.30.0
X-GNOME-Bugzilla-ExtraInfoScript=/usr/share/gedit-2/gedit-bugreport
X-Ubuntu-Gettext-Domain=gedit

```

---

### Post by StuartN on 2010-05-15
> **samlabs821 said:**
> then what should I do?

I assumed you must have created the directory since staring this thread - if not, then I do not understand the output from both commands. Try this:

```
whoami
ls -ld /home/samlabs821
ls -l /home/samlabs821
ls -ld /home/samlabs821/Desktop
ls -l /home/samlabs821/Desktop
echo "Some text" > /home/samlabs821/Desktop/temp.txt
```

---

### Post by TeoBigusGeekus on 2010-05-15
Try this
```
sudo chown -R yourusername /home
```
to change the ownership of your entire home folder.

---

### Post by samlabs821 on 2010-05-15
> **StuartN said:**
> I assumed you must have created the directory since staring this thread - if not, then I do not understand the output from both commands. Try this:

```
whoami
ls -ld /home/samlabs821
ls -l /home/samlabs821
ls -ld /home/samlabs821/Desktop
ls -l /home/samlabs821/Desktop
echo "Some text" > /home/samlabs821/Desktop/temp.txt
```


the file is created and saved...

then i opened with gedit, and the same story, the save button is disabled ((

---

### Post by samlabs821 on 2010-05-15
> **TeoBigusGeekus said:**
> Try this
```
sudo chown -R yourusername /home
```to change the ownership of your entire home folder.
```

sudo chown -R samlabs821 /home
[sudo] password for samlabs821: 
chown: cannot access `/home/samlabs821/.gvfs': Permission denied

```

---

### Post by TeoBigusGeekus on 2010-05-15
Can you try to save again with gedit?

---

### Post by samlabs821 on 2010-08-09
I found the solution!
try this:

gconftool-2 --toggle /desktop/gnome/lockdown/disable_save_to_disk

---

### Post by NexusN on 2011-01-16
> **samlabs821 said:**
> I found the solution!
try this:

gconftool-2 --toggle /desktop/gnome/lockdown/disable_save_to_disk

A good one buddy!
This solved my problem which I suffered for days, thank you:p

---

### Post by nmmarkin on 2013-03-16
I have exactly the same problem but the solution above doesn't work for me
Is there any thoughts about some digging directions?

---

### Post by Impavidus on 2013-03-16
Please start a new thread. An old thread marked as solved won't attract much attention.

---

### Post by nmmarkin on 2013-03-16
started a new thread here [http://ubuntuforums.org/showthread.php?t=2126289&p=12560522#post12560522](http://ubuntuforums.org/showthread.php?t=2126289&p=12560522#post12560522)

---

### Post by wildmanne39 on 2013-03-16
Old thread closed!

---

