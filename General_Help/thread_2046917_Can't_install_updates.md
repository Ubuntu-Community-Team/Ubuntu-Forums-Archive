---
title: "Can't install updates"
date: 2012-08-23
forum: General Help
---

### Post by TimEnid on 2012-08-23
When trying to install updates i get the following:


```
installArchives() failed: 
Extracting templates from packages: 37%%
Extracting templates from packages: 74%%
Extracting templates from packages: 100%%
Preconfiguring packages ...

Extracting templates from packages: 37%%
Extracting templates from packages: 74%%
Extracting templates from packages: 100%%
Preconfiguring packages ...

Extracting templates from packages: 37%%
Extracting templates from packages: 74%%
Extracting templates from packages: 100%%
Preconfiguring packages ...

Extracting templates from packages: 37%%
Extracting templates from packages: 74%%
Extracting templates from packages: 100%%
Preconfiguring packages ...
dpkg: warning: 'tar' not found in PATH or not executable.
dpkg: error: 1 expected program not found in PATH or not executable.
Note: root's PATH should usually contain /usr/local/sbin, /usr/sbin and /sbin.
Error in function: 

```

I tried thru the terminal as well, and it still wont install the full update. Any suggestions?

---

### Post by Marqin on 2012-08-23
Try before update:
```
sudo apt-get install tar
```

---

### Post by TimEnid on 2012-08-23
> **Marqin said:**
> Try before update:
```
sudo apt-get install tar
```

I get this


```
tim@tim:~$ sudo apt-get install tar
[sudo] password for tim: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
tar is already the newest version.
The following packages were automatically installed and are no longer required:
  gstreamer0.10-fluendo-mp3:i386 liboil0.3:i386 lib32stdc++6
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 81 not upgraded.
1 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Do you want to continue [Y/n]? y
dpkg: warning: 'tar' not found in PATH or not executable.
dpkg: error: 1 expected program not found in PATH or not executable.
Note: root's PATH should usually contain /usr/local/sbin, /usr/sbin and /sbin.
E: Sub-process /usr/bin/dpkg returned an error code (2)
```

---

### Post by TimEnid on 2012-08-25
can anyone help?

---

### Post by wojox on 2012-08-25
What does this tell you?
```
echo $PATH
```

---

### Post by TimEnid on 2012-08-25
> **wojox said:**
> What does this tell you?
```
echo $PATH
```

```
tim@tim:~$ sudo echo $PATH
[sudo] password for tim: 
/usr/lib/lightdm/lightdm:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games
```

---

### Post by wojox on 2012-08-25
Hmmm, is this a VM by chance?

---

### Post by TimEnid on 2012-08-26
> **wojox said:**
> Hmmm, is this a VM by chance?

Nope, running ubuntu 12.04 only.

Thinking i might have to do a clean install of the OS

---

### Post by TimEnid on 2012-08-27
Any other suggestions before i restart from scratch?

---

