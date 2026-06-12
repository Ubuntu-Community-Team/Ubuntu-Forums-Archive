---
title: "Ubuntu 9.10 java installation Help"
date: 2010-02-21
forum: General Help
---

### Post by HenneBaby02 on 2010-02-21
Hi everyone, im a new user to the linux world. ive tried ubuntu 7.10 a while ago and liked that. But anyway - my main problem using ubuntu 9.10 is getting the sun java 6 package installed. for the most part everything else i had trouble figuring out,  i found but this java is giving me trouble and i tried searching but not getting much luck but the same helps in different sites, so if someone can help i will greatly appreciate it. ill list wat i tried below.

ive looked up the repositories an
d all but wen i enter ```
sudo apt-get install sun-java6-jre sun-java6-plugin sun-java6-fonts
``` i get 

```
lugin sun-java6-fonts
[sudo] password for henne: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package sun-java6-plugin is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package sun-java6-plugin has no installation candidate
```


anyone got a solve for this, would be much appreciated

---

### Post by claracc on 2010-02-22
Here you have a link [http://sites.google.com/site/easylinuxtipsproject/java](http://sites.google.com/site/easylinuxtipsproject/java) explaining howto install sun java in karmic Koala.

---

### Post by gadolinio on 2010-02-22
Maybe you can find some help in the official website, where you can download the installer and read the installation instructions.
[http://java.com/en/download/linux_manual.jsp?locale=es&host=java.com:80](http://java.com/en/download/linux_manual.jsp?locale=es&host=java.com:80)
Hope you find this useful...

---

### Post by HenneBaby02 on 2010-02-22
> **claracc said:**
> Here you have a link [http://sites.google.com/site/easylinuxtipsproject/java](http://sites.google.com/site/easylinuxtipsproject/java) explaining howto install sun java in karmic Koala.

thanks so far i progressed alot further  it installed... but still got a little bump

this is how far i've gotten using the link in the qoutes. I did steps 1-7 on the left hand side (assuming thats for the ps3 lol) but now after i enter the command to run the java file

```
[SIZE=3][COLOR=#000000][COLOR=#0000FF]sudo ./jre-6u18-linux-i586.bin[/COLOR][/COLOR][/SIZE]
```
now after entering "yes" for the java disclaimer i get..
```
Do you agree to the above license terms? [yes or no]
yes
Unpacking...
Checksumming...
Extracting...
./install.sfx.1632: 1: Syntax error: "(" unexpected
Failed to extract the files.  Please refer to the Troubleshooting section of
the Installation Instructions on the download page for more information.

```

i do appreciate the help and im trying to catch on (still stuck in the ways of windows) =P

---

