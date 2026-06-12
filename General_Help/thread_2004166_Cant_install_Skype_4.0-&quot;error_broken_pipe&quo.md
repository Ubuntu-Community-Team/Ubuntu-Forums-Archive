---
title: "Cant install Skype 4.0-&quot;error broken pipe&quot;"
date: 2012-06-15
forum: General Help
---

### Post by typos1 on 2012-06-15
Keep getting a broken pipe error when I try to install the latest version of Skype, anyone know whats wrong ?

---

### Post by na5h on 2012-06-15
Could you give more details on the installation?

Did you uninstall any previous versions of Skype before attempting to install 4.0?

---

### Post by Habitual on 2012-06-15
> **typos1 said:**
> ...anyone know whats wrong ?

beta software.
[http://www.skype.com/go/getskype-linux-beta-ubuntu*](http://www.skype.com/go/getskype-linux-beta-ubuntu*)

---

### Post by typos1 on 2012-06-15
Habitual, version 2.2 has been replaced with version 4, I m trying to upgrade to version 4, the link you gave was for version 2.2, which I had.

I tried installing using software centre with the previous version still installed, got broken pipe error, tried with gdebi, got the error, unistalled the previous version tried with software centre, still got error, tried with gdebi and still got it. 

That was yesterday, tried again today, still get the error.

---

### Post by Azdour on 2012-06-15
Hi,

I believe v4 is not a beta. I've installed it and unlike in v2 looking at the about dialog there is no mention of the word beta.

The only beta word on the skype website is on:

[http://www.skype.com/intl/en-gb/get-skype/on-your-computer/linux/](http://www.skype.com/intl/en-gb/get-skype/on-your-computer/linux/)

And that is because they have not updated the page to say v4 instead of v2

I've installed v4 from their website today without any issues. I already had v2.2 installed. So I download the 32bit deb and got the software centre to open it and upgrade it.

How are you installing it?

If if helps my md5sum for the deb is:

ed3a85eb19d95f42923379824115daff  skype-ubuntu_4.0.0.7-1_i386.deb

Edit:

There is an old thread regarding installing skype and getting a broken pipe:

[http://ubuntuforums.org/showthread.php?t=963403](http://ubuntuforums.org/showthread.php?t=963403)

---

### Post by typos1 on 2012-06-15
Yes, its not beta, but I cant install it, but I could install 2.2.

Wont install using software centre or gdebi

---

### Post by raja.genupula on 2012-06-15
could you give us the terminal code of what you have entered and what you got ?

---

### Post by Azdour on 2012-06-15
Hi,

That old thread I found seemed to hint at having to remove skype including skype-common before they were able to install a newer version of skype. 

Not sure why you are having the problem when it worked fine with me so the above may be the solution.

---

### Post by typos1 on 2012-06-15
used gdebi to install this is what it says in the terminal:

(Reading database ... 417086 files and directories currently installed.)
Unpacking skype (from .../skype-ubuntu_4.0.0.7-1_amd64.deb) ...
dpkg: error processing /home/typos1/Desktop/skype-ubuntu_4.0.0.7-1_amd64.deb (--install):
 trying to overwrite '/etc/dbus-1/system.d/skype.conf', which is also in package skype-bin:i386 2.2.0.35-0precise3
dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
Errors were encountered while processing:
 /home/typos1/Desktop/skype-ubuntu_4.0.0.7-1_amd64.deb

seems to suggest the system hasnt fully un-installed skype 2.2

---

### Post by Vader79 on 2012-06-15
The problem is uninstalling does not remove all the files. To do this open a terminal and type ```
sudo apt-get autoremove
``` once that is complete then install Skype 4.0

---

### Post by typos1 on 2012-06-15
Tried that and all I get is this :


Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 3 not upgraded.

---

### Post by na5h on 2012-06-16
Make sure that you have removed any previous version of Skype by using the following command:
```
sudo apt-get purge skype
```

Then go to skype.com and download and install the latest version for Ubuntu. The easiest way is to open the downloaded package with Software Center (right-click and choose open with Software Center? Should be default...)

---

### Post by typos1 on 2012-06-16
The version in software centre is the old 2.2 version (or at least it was a ew days ago when I started the thread). 

Gdebi is much easier and quicker than software centre, which has been very very slow since it was heavily revised a few versions ago. I had tried installing with software centre and gdebi as I said in previous posts, but both gave the broken pipe error.

I ll try purging skype then installing version 4.0 . . .

Used the purge command like you said and still get this error :

Reading package lists... Done
Building dependency tree        
Reading state information... Done
Package skype is not installed, so not removed
0 upgraded, 0 newly installed, 0 to remove and 3 not upgraded

Software centre says skype has been removed from my system, I ve checked its removed in the terminal, but its still listed in applications and it still starts when I click on the icon this is very weird.

---

### Post by Paddy Landau on 2012-06-19
autoremove by itself is unlikely to do much.

Try this command to fully remove (purge) Skype before installing Skype 4:
```
sudo apt-get purge skype skype-common skype-bin skype-bin:i386
```Reboot after reinstalling Skype 4.

---

### Post by typos1 on 2012-06-19
Great, thanks, thats sorted it !!

---

