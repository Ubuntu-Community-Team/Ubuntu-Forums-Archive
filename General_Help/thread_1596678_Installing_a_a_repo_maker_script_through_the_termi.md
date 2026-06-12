---
title: "Installing a a repo maker script through the terminal"
date: 2010-10-14
forum: General Help
---

### Post by djdan2k8 on 2010-10-14
Hi im really in need of some help.

Im trying to install a small bash script on my laptop using ubuntu im struggling with the following commands i have a clean install of the latest Ubuntu.

Any help would be great below i have pasted the install instructions


**Introduction**

    Repo Maker Script is a little bash script to help you creating your own Cydia Repository 
    main features are, creating a new repo, making new folders for  Apps, Themes and SBSettings Themes, bulk creating deb's and of course  upload and update the files to your server (config file needed)
            **How To's**

    Here is how to use the script basically
    the first thing you have to do after downloading it is to run the  script with the -install option, this creates all needed files and  folders for you. 
    cd Downloads 
 ./repo -install
    will create the working dirs for the script:
/apt
/apt/apps
/apt/upload
/apt/upload/deb
/apt/updatedebs
    If you dont have Fink installed you can get it here: or simple use the dpkg package provided by the scrpts command -getdpkg  if you have Fink installed you can skipp this step
    to get dpkg from the script you can just type (if you run -install first)    
sudo su 
   repo -getdpkg
    the script than downloads the provided package and installs it to /usr/bin (uninstall with -deldpkg)

---

### Post by bruno9779 on 2010-10-14
Those are the instructions, but you haven't said what your problem is

Any errors when doing that in a terminal?

Can you add a download link to know what version you are trying to install?

---

### Post by djdan2k8 on 2010-10-14
When running     cd downloads
                           ./repo -install  iget the message below


bash: ./repo: No such file or directory

The link to the script is :-   
[http://cytec.us/tools/repo/repo.zip](http://cytec.us/tools/repo/repo.zip)

the link to the help page is:- [http://cytec.us/tools/repo/help.html](http://cytec.us/tools/repo/help.html)

thanks for the quick reply bruno:)

---

### Post by bruno9779 on 2010-10-14
Ok, your link is for a .zip file. 
You will need to unpack it first. When you download it, choose to open it with archive manager, click the file, than the icon "extract" and then "~/Downloads" folder as your destination.

After this just follow the instructions

---

### Post by bruno9779 on 2010-10-14
If the previous didn't work, and you have a "repo" file in "~/Downloads", than it could be a permission issue, so you would need to run a command like:

```
sudo chmod +x repo
```

in the "~/Downloads" folder.

Than follow the instructions.

---

### Post by djdan2k8 on 2010-10-15
Hi bruno thanks for the info i did all that but get a syntax error after running the following 

danharris83@ubuntu:~/Downloads/repo$ sudo ./repo -install

./repo: 18: Syntax error: "(" unexpected

could that be my error or developrs error

---

