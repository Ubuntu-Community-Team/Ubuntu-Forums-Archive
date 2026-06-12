---
title: "Can't install chromium-browser from PPA :("
date: 2009-11-25
forum: General Help
---

### Post by sprince09 on 2009-11-25
Hi guys,

I've been using Chromium on all of my PC's for a while now, but when I recently tried to install it on my EEE pc running Jaunty, I got the following error:

```

scott@aristotle:~$ sudo aptitude install chromium-browser
[sudo] password for scott: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
The following packages are BROKEN:
  chromium-browser 
The following NEW packages will be installed:
  chromium-codecs-ffmpeg{a} 
0 packages upgraded, 2 newly installed, 0 to remove and 0 not upgraded.
Need to get 10.7MB of archives. After unpacking 37.8MB will be used.
The following packages have unmet dependencies:
  chromium-browser: Depends: libnss3-1d (>= 3.12.3) but 3.12.2~rc1-0ubuntu2 is installed.
Unable to resolve dependencies!  Giving up...
The following packages are BROKEN:
  chromium-browser 
The following NEW packages will be installed:
  chromium-codecs-ffmpeg{a} 
0 packages upgraded, 2 newly installed, 0 to remove and 0 not upgraded.
Need to get 10.7MB of archives. After unpacking 37.8MB will be used.
aptitude failed to find a solution to these dependencies.  You can solve them yourself by hand or type 'n' to quit.
The following packages have unmet dependencies:
  chromium-browser: Depends: libnss3-1d (>= 3.12.3) but 3.12.2~rc1-0ubuntu2 is installed.
Resolve these dependencies by hand? [N/+/-/_/:/?] N
Abort.
scott@aristotle:~$

```

It's odd, because I went through the exact same procedure (add the PPA to sources.list, get the key, etc...) on my other computer, which is also running Jaunty, and it installed fine. I tried installing the libnss3-1d package from the above error message, but aptitude tells me it's already installed... so I'm not quite sure what the solution is here. Anyone have any ideas?

---

### Post by fragos on 2009-11-25
I don't have an answer but I have some suggestions to try. I'd 1st check that Software Sources has universe and multiverse selected. You might also try adding the Google repository:

deb [http://dl.google.com/linux/deb/](http://dl.google.com/linux/deb/) stable main non-free

---

### Post by cmcanulty on 2009-11-25
If you install Ubuntu tweak you can add the repository real easily and install Chrome, I did it and it works fine, makes a lot of other settings easy to do also, email me if you need more help on this
[http://ubuntu-tweak.com/downloads](http://ubuntu-tweak.com/downloads)

---

### Post by mkvnmtr on 2009-11-25
The terminal is telling you that you need to uninstall a package and install another for the browser to work. You will need to find what repository has the package you need and enable it. Then uninstall the one package and install the other.

---

### Post by sprince09 on 2009-11-26
Think I found the problem: I installed Adobe's version of flashplayer from their website (which I never do) instead of from the repositories. I don't have time to verify right now but this website describes the exact problem I have along with a viable looking solution.

[http://www.webupd8.org/2009/09/dependency-is-not-satisfiable-libnss3.html](http://www.webupd8.org/2009/09/dependency-is-not-satisfiable-libnss3.html)


Also, Ubuntu-tweak is pretty awesome, even though it didn't help, so thanks for that suggestion :)

---

### Post by fragos on 2009-11-26
Install "flashplugin-installer" with Synaptic and you'll have the latest flash player that works with my installed Chromium, Firefox and Epiphany.

---

### Post by sprince09 on 2009-11-26
Yup, I just finished going through the instructions on the link I just posted and I can confirm that that solved my problem. To summarize, you need to:

purge any flash player packages you have installed

run "sudo aptitude install -f" to clean out any leftovers and fix any broken dependencies.

install the latest version of libnss3-1d (google search will get you there)

add the chromium ppa and install chromium-browser

Thanks all :)

---

### Post by sprince09 on 2009-11-26
Yup, I just finished going through the instructions on the link I just posted and I can confirm that that solved my problem. To summarize, you need to:

purge any flash player packages you have installed

run "sudo aptitude install -f" to clean out any leftovers and fix any broken dependencies.

install the latest version of libnss3-1d (google search will get you there)

add the chromium ppa and install chromium-browser

Thanks all :)



** Edit **

fragos' suggestion may also work, but I'm not going to test it on my system since I've got mine working now...

---

### Post by fragos on 2009-11-26
I don't blame you for sticking with what worked for you. The important thing is that you're up and running again.

---

### Post by sprince09 on 2009-11-29
Yeah, I think my problem was that I installed flash player from Adobe's website. Usually I just install the 'flashplugin-installer' package with aptitude and have no problems. Live and learn...

---

### Post by badrra on 2010-04-03
all you need to do is to go to this site 

[https://launchpad.net/ubuntu/+source/nss](https://launchpad.net/ubuntu/+source/nss)

Choose the package hat matches your ubuntu ver, install it and then install google chrome. Its just a dependency that needs to be satisfied.

---

