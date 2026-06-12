---
title: "Sopcast - a definitive guide to installing please?!"
date: 2010-05-16
forum: General Help
---

### Post by kmarzi on 2010-05-16
Hello,

Ubuntu/Linux newbie here and I'm having difficulties with installing  Sopcast. Can somebody PLEASE help me?! I have tried EVERYTHING. I have  used this forum, as well as wider internet searches. Nothing seems to  work. I still can't install Sopcast! Help...

I have used this PPA (whatever the heck that means/is!)  [https://launchpad.net/~jason-scheunemann/+archive/ppa](https://launchpad.net/~jason-scheunemann/+archive/ppa).

When I go to the Ubuntu Software Centre (through Applications), I can  try and install from here. But the message "Package dependencies cannot  be resolved" appears. The PPA for Flyguy97 is there. But, again, when I  try to install, the same message appears.

I have used terminal commands too - still no joy.

Can anyone please help with an installation guide? I know I'm a newbie  to linux, but I'm quite computer literate and installing programs in  Ubuntu is, well, difficult to say the least. But, installing Sopcast is,  IMHO, pretty much impossible!

Any help would be greatly appreciated and would stop me having to boot  up Windows in order to use Sopcast.

Thanks in advance for your help.

Kmarzi

---

### Post by simonchimera on 2010-08-21
I also have the exact same issue, did you manage to get a fix for this?

Any help would be appreciated!

---

### Post by simonchimera on 2010-08-21
Sorted, make sure you install [this deb]("http://packages.ubuntu.com/jaunty/i386/libstdc++5/download") before sopcast installation

---

### Post by kmarzi on 2010-08-23
Simonchimera,

My friend actually installed Sopcast for me a while ago. I have no idea what he did but it works.

Thanks for your post. I know that I couldn't manage to install it myself. Could you possibly post some further instructions for users who might also struggle with this (including me if I buy a new PC!)?

Thanks again.

Kmarzi

---

### Post by lykeion on 2010-08-23
**Install Sopcast in Ubuntu Lucid**

1. Install libstdc++5 dependecy manually
Browse to either one of these:
[http://packages.ubuntu.com/jaunty/i386/libstdc++5/download](http://packages.ubuntu.com/jaunty/i386/libstdc++5/download)
[http://packages.ubuntu.com/maverick/i386/libstdc++5/download](http://packages.ubuntu.com/maverick/i386/libstdc++5/download)

Note: these are i386 packages. If you need amd64 packages change i386 -> amd64 in the url

Pick a site near you and download libstdc++5
Doubleclick the downloaded file to install it

2. Add PPA repository
Applications > Accessories > Terminal
Copy and paste this line into the terminal
```
sudo add-apt-repository ppa:jason-scheunemann/ppa
```

3. Install sopcast
Still in terminal copy and paste this
```
sudo apt-get update
sudo apt-get install sopcast-player
```
This would install dependencies like sp-auth and vlc automatically

---

### Post by kmarzi on 2010-08-26
[COLOR=black][lykeion]("http://ubuntuforums.org/member.php?u=102981")[/COLOR], thanks for posting these instructions...

Kmarzi

---

### Post by WaCope on 2010-08-26
Thanks, that libstdc++5 dependency has been driving me nuts.  Finally got it working again.

---

### Post by lykeion on 2010-09-02
@ kmarzi
Fine that it worked out for you. 
You might want to tag this thread as solved also 
(to let others easily find the solution).

---

