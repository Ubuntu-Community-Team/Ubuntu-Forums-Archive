---
title: "ubuntu software center won't install anything"
date: 2011-11-19
forum: General Help
---

### Post by elliotn on 2011-11-19
suddenly software center won't install apps, I even tried installing .debs but when I click install nothing happens. any help will do

---

### Post by n00b2u on 2011-11-19
Have you tried using the dpkg command in the terminal?  Using the command on the terminal is more verbose, also check /var/log/dpkg.log or /var/log/syslog for clues as to why its not working.  Hope this helps.

Syntax of dpkg:

sudo dpkg -i <pkgname>.deb

---

### Post by raja.genupula on 2011-11-19
Hi man give me out put of 
```
sudo apt-get update
```

& give me output of trying to install something.

Thank you.

---

### Post by asifnaz on 2011-11-19
open terminal

then  write

```
sudo dpkg -i
```

and drag that .deb file into terminal and press enter

---

### Post by elliotn on 2011-11-19
> **asifnaz said:**
> open terminal

then  write

```
sudo dpkg -i
```

and drag that .deb file into terminal and press enter

I can install debs from terminal using the above command it works 

am not infront of a PC but will try to post the outputs tomorrow morning

---

### Post by elliotn on 2011-11-20
terminal output 
```
elliotn@elliotn:~$ software-center
/usr/share/software-center/softwarecenter/app.py:1194: Warning: g_object_set_qdata: assertion `G_IS_OBJECT (object)' failed
  self.window_main.show_all()
2011-11-20 15:54:06,334 - softwarecenter.fixme - WARNING - logs to the root logger: '('/usr/lib/pymodules/python2.7/zeitgeist/client.py', 367, 'reconnect_monitors')'
2011-11-20 15:54:06,334 - zeitgeist.client - INFO - Reconnected to Zeitgeist engine...
/usr/share/software-center/softwarecenter/SimpleGtkbuilderApp.py:50: Warning: g_object_set_qdata: assertion `G_IS_OBJECT (object)' failed
  gtk.main()
2011-11-20 15:54:14,400 - softwarecenter.app - INFO - software-center-agent finished with status 1
2011-11-20 15:54:18,975 - softwarecenter.backend - WARNING - _on_trans_error: org.freedesktop.PolicyKit.Error.Failed: ('system-bus-name', {'name':  ':1.58'}): org.debian.apt.install-or-remove-packages


```
dont know what now

---

### Post by elliotn on 2011-11-20
any advice plz

---

### Post by asifnaz on 2011-11-20
> **elliotn said:**
> any advice plz

give me out put to install anything

for example 

```
sudo apt-get install vlc
```

---

### Post by elliotn on 2011-11-20
> **asifnaz said:**
> give me out put to install anything

for example 

```
sudo apt-get install vlc
```

that works, it does install vlc etc but the problem is with ubuntu software center only, synaptic works also

---

### Post by asifnaz on 2011-11-21
try


```
sudo apt-get clean; sudo apt-get --reinstall software-center
```

---

### Post by elliotn on 2011-11-21
```
sudo apt-get clean; sudo apt-get --reinstall software-center

E: Invalid operation software-center
```

that's the output

---

### Post by raja.genupula on 2011-11-21
> **elliotn said:**
> ```
sudo apt-get clean; sudo apt-get --reinstall software-center

E: Invalid operation software-center
```that's the output

hi man do this 
```

sudo apt-get install --reinstall software-center
```
and try to load it again

---

### Post by asifnaz on 2011-11-21
do what raja said

sudo apt-get install --reinstall software-center

---

### Post by elliotn on 2011-11-21
> **asifnaz said:**
> do what raja said

sudo apt-get install --reinstall software-center

I did that but it doesn't help at all

---

### Post by matt_symes on 2011-11-21
Hi
[FONT=monospace]
[/FONT]> 2011-11-20 15:54:18,975 - softwarecenter.backend - WARNING - _on_trans_error: org.freedesktop.PolicyKit.Error.Failed: ('system-bus-name', {'name':  ':1.58'}): org.debian.apt.install-or-remove-packagesThat looks like a bus failure.

From the terminal type

```
ls -l usr/share/polkit-1/actions/org.debian.apt.policy
```(That is a small L above)

and

```
cat /usr/share/polkit-1/actions/org.debian.apt.policy
```Please post the output back here.

Kind regards

---

### Post by elliotn on 2011-11-21
> **matt_symes said:**
> Hi
[FONT=monospace]
[/FONT]

That looks like a bus failure.

From the terminal type

```
ls -l cat /usr/share/polkit-1/actions/org.debian.apt.policy
```

(That is a small L above)

and

```
cat /usr/share/polkit-1/actions/org.debian.apt.policy
```

Please post the output back here.

Kind regards

Here it is 
```
elliotn@elliotn:~$ ls -l cat /usr/share/polkit-1/actions/org.debian.apt.policy
ls: cannot access cat: No such file or directory
-rw-r--r-- 1 root root 5573 2011-09-22 07:08 /usr/share/polkit-1/actions/org.debian.apt.policy
elliotn@elliotn:~$ cat /usr/share/polkit-1/actions/org.debian.apt.policy
<?xml version="1.0" encoding="UTF-8"?>
<!DOCTYPE policyconfig PUBLIC
 "-//freedesktop//DTD PolicyKit Policy Configuration 1.0//EN"
 "http://www.freedesktop.org/standards/PolicyKit/1.0/policyconfig.dtd">
<policyconfig>

  <vendor>Apt Daemon</vendor>
  <vendor_url>http://launchpad.net/aptdaemon/</vendor_url>
  <icon_name>package-x-generic</icon_name>

  <action id="org.debian.apt.get-trusted-vendor-keys">
    <description gettext-domain="aptdaemon">List keys of trusted vendors</description>
    <message gettext-domain="aptdaemon">To view the list of trusted keys, you need to authenticate.</message>
    <defaults>
      <allow_any>auth_admin</allow_any>
      <allow_inactive>auth_admin</allow_inactive>
      <allow_active>auth_admin_keep</allow_active>
    </defaults>
  </action>

  <action id="org.debian.apt.clean">
    <description gettext-domain="aptdaemon">Remove downloaded package files</description>
    <message gettext-domain="aptdaemon">To clean downloaded package files, you need to authenticate.</message>
    <defaults>
      <allow_any>auth_admin</allow_any>
      <allow_inactive>auth_admin</allow_inactive>
      <allow_active>yes</allow_active>
    </defaults>
  </action>

  <action id="org.debian.apt.change-config">
    <description gettext-domain="aptdaemon">Change software configuration</description>
    <message gettext-domain="aptdaemon">To change software settings, you need to authenticate.</message>
    <defaults>
      <allow_any>auth_admin</allow_any>
      <allow_inactive>auth_admin</allow_inactive>
      <allow_active>auth_admin_keep</allow_active>
    </defaults>
  </action>

  <action id="org.debian.apt.change-repository">
    <description gettext-domain="aptdaemon">Change software repository</description>
    <message gettext-domain="aptdaemon">To change software repository settings, you need to authenticate.</message>
    <defaults>
      <allow_any>auth_admin</allow_any>
      <allow_inactive>auth_admin</allow_inactive>
      <allow_active>auth_admin_keep</allow_active>
    </defaults>
  </action>

  <action id="org.debian.apt.install-file">
    <description gettext-domain="aptdaemon">Install package file</description>
    <message gettext-domain="aptdaemon">To install this package, you need to authenticate.</message>
    <defaults>
      <allow_any>auth_admin</allow_any>
      <allow_inactive>auth_admin</allow_inactive>
      <allow_active>auth_admin_keep</allow_active>
    </defaults>
  </action>

  <action id="org.debian.apt.update-cache">
    <description gettext-domain="aptdaemon">Update package information</description>
    <message gettext-domain="aptdaemon">To update the software catalog, you need to authenticate.</message>
    <defaults>
      <allow_any>auth_admin</allow_any>
      <allow_inactive>auth_admin</allow_inactive>
      <allow_active>yes</allow_active>
    </defaults>
  </action>

  <action id="org.debian.apt.install-or-remove-packages">
    <description gettext-domain="aptdaemon">Install or remove packages</description>
    <message gettext-domain="aptdaemon">To install or remove software, you need to authenticate.</message>
    <defaults>
      <allow_any>auth_admin</allow_any>
      <allow_inactive>auth_admin</allow_inactive>
      <allow_active>auth_admin_keep</allow_active>
    </defaults>
  </action>

  <action id="org.debian.apt.install-packages-from-new-repo">
    
    <description gettext-domain="aptdaemon">Add a new repository and install packages from it</description>
    <message gettext-domain="aptdaemon">To install software from a new source, you need to authenticate.</message>
    <defaults>
      <allow_any>auth_admin</allow_any>
      <allow_inactive>auth_admin</allow_inactive>
      <allow_active>auth_admin_keep</allow_active>
    </defaults>
  </action>

  <action id="org.debian.apt.install-purchased-packages">
    
    <description gettext-domain="aptdaemon">Add a new repository of purchased software and install packages from it</description>
    <message gettext-domain="aptdaemon">To install purchased software, you need to authenticate.</message>
    <defaults>
      <allow_any>auth_admin</allow_any>
      <allow_inactive>auth_admin</allow_inactive>
      <allow_active>auth_admin_keep</allow_active>
    </defaults>
  </action>

  <action id="org.debian.apt.upgrade-packages">
    <description gettext-domain="aptdaemon">Upgrade packages</description>
    <message gettext-domain="aptdaemon">To install updated software, you need to authenticate.</message>
    <defaults>
      <allow_any>auth_admin</allow_any>
      <allow_inactive>auth_admin</allow_inactive>
      <allow_active>auth_admin_keep</allow_active>
    </defaults>
  </action>

  <action id="org.debian.apt.cancel-foreign">
    <description gettext-domain="aptdaemon">Cancel the task of another user</description>
    <message gettext-domain="aptdaemon">To cancel someone else's software changes, you need to authenticate.</message>
    <defaults>
      <allow_any>auth_admin</allow_any>
      <allow_inactive>auth_admin</allow_inactive>
      <allow_active>auth_admin</allow_active>
    </defaults>
  </action>

  <action id="org.debian.apt.set-proxy">
    <description gettext-domain="aptdaemon">Set a proxy for software downloads</description>
    <message gettext-domain="aptdaemon">To use a proxy server for downloading software, you need to authenticate.</message>
    <defaults>
      <allow_any>auth_admin</allow_any>
      <allow_inactive>auth_admin</allow_inactive>
      <allow_active>auth_admin</allow_active>
    </defaults>
  </action>

</policyconfig>elliotn@elliotn:~$ 

```

huh

---

### Post by matt_symes on 2011-11-21
Hi

I cannot see anything wrong with those file.

> 
suddenly software center won't install appsWhat exactly is happening ? Is the software center opening ? Are you seeing programs to install ? Is the password window popping up ? Is it accepting your password, trying to install and then failing ?

Please be far more descriptive as to what is happening when you try to install software.

Kind regards

---

### Post by asifnaz on 2011-11-21
I suggest you to update

```
sudo apt-get update 
```

and past output here

---

### Post by elliotn on 2011-11-21
> **matt_symes said:**
> Hi

I cannot see anything wrong with those file.

What exactly is happening ? Is the software center opening ? Are you seeing programs to install ? Is the password window popping up ? Is it accepting your password, trying to install and then failing ?

Please be far more descriptive as to what is happening when you try to install software.

Kind regards

software center does load and I can find any software I want but upon clicking on a program I want to install nothing happens not even the password box, it just does nothing

---

### Post by matt_symes on 2011-11-21
Hi

> **elliotn said:**
> software center does load and I can find any software I want but upon clicking on a program I want to install nothing happens not even the password box, it just does nothing

That may well be related to that dbus failure. I don't think it's and issue with the software center itself (but i may be wrong).

From the terminal type

```
ps aux | grep policy
```Post back results.

Kind regards

---

### Post by elliotn on 2011-11-21
> **matt_symes said:**
> Hi



That may well be related to that dbus failure. I don't think it's and issue with the software center itself (but i may be wrong).

From the terminal type

```
ps aux | grep policy
```Post back results.

Kind regards

here it is
```
elliotn@elliotn:~$ ps aux | grep policy
root       944  0.0  0.1  23388  3688 ?        Sl   19:07   0:00 /usr/lib/policykit-1/polkitd
elliotn  13615  0.0  0.0   4156   864 pts/0    S+   22:05   0:00 grep --color=auto policy
elliotn@elliotn:~$
```

---

### Post by matt_symes on 2011-11-21
Hi

What version of Ubuntu are you using ?

```
cat /etc/lsb-release
```

I am running 11.10 and i have an extra polkit service running.

```
matthew@matthew-Aspire-7540:~$ ps aux | grep polkit
root      1111  0.0  0.1  23908  3588 ?        Sl   23:38   0:00 /usr/lib/policykit-1/polkitd
matthew   1642  0.0  0.2  29304  6224 ?        Sl   23:38   0:00 /usr/lib/policykit-1-gnome/polkit-gnome-authentication-agent-1
matthew   3104  0.0  0.0   4196   784 pts/0    S+   23:56   0:00 grep --color=auto polkit
matthew@matthew-Aspire-7540:~$
```

Can you post the output of

```
ls -l /usr/lib/policykit-1-gnome/polkit-gnome-authentication-agent-1
```

That is a small L above.

I believe you may need this running for software center.

Kind regards

---

### Post by ken631 on 2011-11-22
Hi, I have the same problem with not only software center, but also update manager, and synaptic.  Where as synaptic worked as did update manager but suddenly quit like software center.  The problem, click install, the mouse changes to busy icon then nothing, the password box doesn't appear.  I found a work around where I had to open terminal and type gksudo update-manager or gksudo synaptic or gksudo software-center.  Its a bummer.

---

### Post by elliotn on 2011-11-22
> **matt_symes said:**
> Hi

What version of Ubuntu are you using ?

```
cat /etc/lsb-release
```

I am running 11.10 and i have an extra polkit service running.

```
matthew@matthew-Aspire-7540:~$ ps aux | grep polkit
root      1111  0.0  0.1  23908  3588 ?        Sl   23:38   0:00 /usr/lib/policykit-1/polkitd
matthew   1642  0.0  0.2  29304  6224 ?        Sl   23:38   0:00 /usr/lib/policykit-1-gnome/polkit-gnome-authentication-agent-1
matthew   3104  0.0  0.0   4196   784 pts/0    S+   23:56   0:00 grep --color=auto polkit
matthew@matthew-Aspire-7540:~$
```

Can you post the output of

```
ls -l /usr/lib/policykit-1-gnome/polkit-gnome-authentication-agent-1
```

That is a small L above.

I believe you may need this running for software center.

Kind regards

```
elliotn@elliotn:~$ ls -l /usr /lib/policykit-1- gnome/polikit-gnome-authentication-agent-1
ls: cannot access /lib/policykit-1-: No such file or directory
ls: cannot access gnome/polikit-gnome-authentication-agent-1: No such file or directory
/usr:
total 216
drwxr-xr-x   2 root root 69632 2011-11-21 13:41 bin
drwxr-xr-x   2 root root  4096 2011-11-19 13:37 games
drwxr-xr-x  75 root root  4096 2011-11-20 08:58 include
drwxr-xr-x 263 root root 98304 2011-11-21 11:37 lib
drwxr-xr-x   3 root root  4096 2011-05-06 13:57 lib64
drwxr-xr-x  10 root root  4096 2011-05-06 13:42 local
drwxr-xr-x   2 root root 12288 2011-11-21 13:41 sbin
drwxr-xr-x 402 root root 12288 2011-11-21 11:35 share
drwxrwsr-x  15 root src   4096 2011-11-20 16:16 src
```

---

### Post by elliotn on 2011-11-22
copy paste
```
elliotn@elliotn:~$ ls -l /usr/lib/policykit-1-gnome/polkit-gnome-authentication-agent-1
-rwxr-xr-x 1 root root 39076 2011-09-07 07:48 /usr/lib/policykit-1-gnome/polkit-gnome-authentication-agent-1

```

---

### Post by matt_symes on 2011-11-22
Hi

From the terminal can you post back the results of these commands

```
ls -l /etc/xdg/autostart/polkit-gnome-authentication-agent-1.desktop
```
```

cat /etc/xdg/autostart/polkit-gnome-authentication-agent-1.desktop
```

What version of Ubuntu are you using ?

```
cat /etc/lsb-release
```

Kind regards

---

### Post by elliotn on 2011-11-23
I am using 11.04

---

### Post by T.exe on 2011-11-23
I am facing the same problem too... There is no response from UBUNTU SOFTWARE CENTER even after clicking the''INSTALL' button.... I was using Unity then switched to GNOME3, later switched to KDE.. the MUON package manager for KDE is working perfectly though!

---

### Post by linuxuser12345 on 2011-11-23
What GUI are you running? Are you running KDE? If so, I have the same problem :(

---

### Post by matt_symes on 2011-11-23
Hi

Not sure about KDE but the rest of you, can you post back the command from my past post. It will eliminate/ implicate another potential problem.

Kind regards

---

