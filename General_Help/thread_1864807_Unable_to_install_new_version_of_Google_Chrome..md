---
title: "Unable to install new version of Google Chrome."
date: 2011-10-19
forum: General Help
---

### Post by Th3Professor on 2011-10-19
I currently have Google Chrome 9.0.597.45 beta installed.
I would like to install the most recent version.
It lists dependencies.
I try installing the dependencies but it says they're already installed.

Here's the output from the initial attempt at installing the new version:

```
$ sudo apt-get install google-chrome-stable 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  google-chrome-stable: Depends: libasound2 (> 1.0.22) but 1.0.20-3ubuntu6.1 is to be installed
                        Depends: libc6 (>= 2.11) but 2.10.1-0ubuntu19 is to be installed
                        Depends: libfontconfig1 (>= 2.8.0) but 2.6.0-1ubuntu12 is to be installed
                        Depends: libatk1.0-0 (>= 1.30.0) but 1.28.0-0ubuntu1 is to be installed
E: Broken packages
```

I understand that I do not have to remove the old Chrome before installing the new Chrome. On their help page they say to just install the new one. I'm guessing that means it just overwrites the older version files.

How do I get the new version installed?

---

### Post by linuxwin2 on 2011-10-19
Try to add repository
```

$wget -q -O - https://dl-ssl.google.com/linux/linux_signing_key.pub | sudo apt-key add -
$sudo sh -c 'echo "deb http://dl.google.com/linux/deb/ stable main" >> /etc/apt/sources.list.d/google.list'
$sudo apt-get update 
$sudo apt-get install google-chrome-stable 


```

---

### Post by collisionystm on 2011-10-19
try

sudo apt-get install -f

---

### Post by Th3Professor on 2011-10-20
> **linuxwin2 said:**
> Try to add repository
```

$wget -q -O - https://dl-ssl.google.com/linux/linux_signing_key.pub | sudo apt-key add -
$sudo sh -c 'echo "deb http://dl.google.com/linux/deb/ stable main" >> /etc/apt/sources.list.d/google.list'
$sudo apt-get update 
$sudo apt-get install google-chrome-stable 


```
I tried those steps and after the last step this happened:

```
$ sudo apt-get install google-chrome-stable
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  google-chrome-stable: Depends: libasound2 (> 1.0.22) but 1.0.20-3ubuntu6.1 is to be installed
                        Depends: libc6 (>= 2.11) but 2.10.1-0ubuntu19 is to be installed
                        Depends: libfontconfig1 (>= 2.8.0) but 2.6.0-1ubuntu12 is to be installed
                        Depends: libatk1.0-0 (>= 1.30.0) but 1.28.0-0ubuntu1 is to be installed
E: Broken packages
```> **collisionystm said:**
> try

sudo apt-get install -f

I tried with the -f and this happened:

```
$ sudo apt-get install -f google-chrome-stable
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  google-chrome-stable: Depends: libasound2 (> 1.0.22) but 1.0.20-3ubuntu6.1 is to be installed
                        Depends: libc6 (>= 2.11) but 2.10.1-0ubuntu19 is to be installed
                        Depends: libfontconfig1 (>= 2.8.0) but 2.6.0-1ubuntu12 is to be installed
                        Depends: libatk1.0-0 (>= 1.30.0) but 1.28.0-0ubuntu1 is to be installed
E: Broken packages
```

---

### Post by rlshosting on 2011-10-20
What happens if you download it on this page and install it?
[http://www.google.com/chrome](http://www.google.com/chrome)

---

### Post by mc4man on 2011-10-20
Looks like your are on some release of ubuntu earlier than lucid, 9.04 or 9.10 which is not supported by the .deb you have.

Whether there are builds that support your install I don't know, maybe somewhere though wouldn't be surprised if there wasn't.

---

### Post by rlshosting on 2011-10-20
> **bkerensa said:**
> You get a error when it tries to install via Software Center.

Eh. That's bad. :(

---

### Post by Th3Professor on 2011-10-28
> **mc4man said:**
> Looks like your are on some release of ubuntu earlier than lucid, 9.04 or 9.10 which is not supported by the .deb you have.

Whether there are builds that support your install I don't know, maybe somewhere though wouldn't be surprised if there wasn't.

I'm on 9.10. Upgrading is not an option at present. I've tried a variety of attempts at installing. I removed the old beta chrome and tried adding the old stable chrome and received the same message for dependencies as with the new stable chrome.

I enabled all repositories. No luck.

How do I manually add the dependencies listed in the attached image?

---

### Post by mc4man on 2011-10-28
> **Th3Professor said:**
> I'm on 9.10. Upgrading is not an option at present. I've tried a variety of attempts at installing. I removed the old beta chrome and tried adding the old stable chrome and received the same message for dependencies as with the new stable chrome.

I enabled all repositories. No luck.

How do I manually add the dependencies listed in the attached image?

You don't, or not easily - those are lucid package versions as the min. required. (& generally a very poor idea to upgrade libc6

Maybe take a glance thru here & try to find the latest one whose dep.'s are satisfied in karmic

Edit: - it appears those are just old windows versions - sorry - maybe you can locate something similar for linux (.deb's)

[http://www.oldapps.com/google_chrome.php](http://www.oldapps.com/google_chrome.php)

---

### Post by bbmak on 2011-10-28
I am on Lubuntu 11.10, try to use "apt-get install chromium-browser"

---

