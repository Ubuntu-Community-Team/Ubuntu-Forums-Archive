---
title: "Installing APT sources.list"
date: 2006-05-11
forum: General Help
---

### Post by burnt1ce85 on 2006-05-11
Hi. i'm relatively new to linux and need help installing [http://parker1.co.uk/myth/sources.list](http://parker1.co.uk/myth/sources.list). I was told by this website, [http://www.beginningubuntu.com/software_13.html](http://www.beginningubuntu.com/software_13.html), to run this command: **sudo apt-get install sources.list** (provided that i have already downloaded sources.list into my current directory). 

But this doesn't work, i get the following error:

[B]Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package sources.list
[/B]

So how do i solve this?

---

### Post by linuxcity on 2006-05-11
If you are using Ubuntu  Breezy 5.10 , you can follow these steps: [http://easylinux.info/wiki/Ubuntu#How_to_add_extra_repositories](http://easylinux.info/wiki/Ubuntu#How_to_add_extra_repositories)

Ubuntu Dapper 6.06 Beta
[http://easylinux.info/wiki/Ubuntu_dapper#How_to_add_extra_repositories](http://easylinux.info/wiki/Ubuntu_dapper#How_to_add_extra_repositories)

to get to the console click on Applications | Accessories | Terminal and issue the commands as instructed

---

### Post by Isoss on 2006-05-11
Run Terminal
Type:
```
sudo gedit /etc/apt/source.list
```
type the password.
Then Copy and Paste the content of [http://parker1.co.uk/myth/sources.list](http://parker1.co.uk/myth/sources.list)
(ofcourse this shall overwrite what is already listed in source.list.)
Then save and close
then run:
```
sudo apt-get update
```
and wait untill the update is done (you have to be online ofcourse).

---

### Post by 5-HT on 2006-05-11
sources.list is a file, not a package.
The file contains information about which software repositories you would like to use. To use that particular sources.list:
[LIST=1]
[*]Backup your old one for good measure ```
 sudo cp /etc/apt/sources.list /etc/apt/sources.list.backup 
```
[*]Save the sources.list you linked to as "sources.list" in your home folder's Desktop directory from your web browser*
[*]Copy the new sources.list into the right place ```
 sudo cp ~/Desktop/sources.list /etc/apt/sources.list 
```[/LIST]That's it.
To use those repositories using apt-get: ```
 sudo apt-get update 
``` If you use synaptic or another package manager, you can update the list through those as well. If you don't know how to do so, post which package manager you are using and someone will be able to walk you through it.

*If the file did not save as ASCII text, just copy the linked sources.list into your preferred text editor and save it that way.

HTH

---

### Post by Isoss on 2006-05-12
[QUOTE=Isoss]Run Terminal
Type:
```
sudo gedit /etc/apt/source.list
```
type the password.
Then Copy and Paste the content of [http://parker1.co.uk/myth/sources.list](http://parker1.co.uk/myth/sources.list)
(ofcourse this shall overwrite what is already listed in source.list.)
Then save and close
then run:
```
sudo apt-get update
```
and wait untill the update is done (you have to be online ofcourse).[/QUOTE]
I am sorry, there was a mistake. The correct command must be:
```
sudo gedit /etc/apt/sources.list
```
So it's sources.list, not source.list

---

