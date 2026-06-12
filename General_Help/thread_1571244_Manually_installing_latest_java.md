---
title: "Manually installing latest java"
date: 2010-09-09
forum: General Help
---

### Post by ybh305 on 2010-09-09
Hi,

I've been trying to install the latest JRE as the one Ubuntu brings is out of date. I've been following these steps: [http://ubuntuforums.org/showthread.php?t=539423](http://ubuntuforums.org/showthread.php?t=539423)

Unfortunately, I was not unable to do the firefox plugin step as the directory structure has changed so when I visited a site that needed java, it could not find the appropriate plugin. I thought that if I only installed the firefox plugin that it would recognize that I already had installed the latest java (update 21 at this time) but it didn't and it reverted me back to update 18.

I was able to follow the majority of the steps (creating the links etc). I was wondering, if it reverted me back to update 18, would all the links I created be erased? I'm not trying to bloat my system all up with unused links, if that makes any sense.

In addition, I wasn't able to do step #1, "sudo apt-get remove sun-java*" here is the message for that:

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Note, selecting sun-javadb-doc for regex 'sun-java*'
Note, selecting sun-javadb-demo for regex 'sun-java*'
Note, selecting sun-javadb-client for regex 'sun-java*'
Note, selecting sun-javadb-core for regex 'sun-java*'
Note, selecting sun-java5-jre for regex 'sun-java*'
Note, selecting sun-javadb-common for regex 'sun-java*'
Note, selecting sun-java6-doc for regex 'sun-java*'
Note, selecting sun-java6-jdk for regex 'sun-java*'
Note, selecting sun-java6-jre for regex 'sun-java*'
Note, selecting sun-javadb-javadoc for regex 'sun-java*'
Note, selecting sun-java6-fonts for regex 'sun-java*'
E: Couldn't find package sun-java*

It's an old post so I believe that's half of the problem. Can someone direct me on where I can find a solution for this?

Thanks

---

### Post by scouser73 on 2010-09-09
This is the website I use - [http://sites.google.com/site/easylinuxtipsproject/java](http://sites.google.com/site/easylinuxtipsproject/java)

---

### Post by ybh305 on 2010-09-09
Thanks, that seems to have done it.

I noticed the page you provided does not create any links for you. Was it necessary in the first place? (based on the link I provided earlier)

EDIT:

I can't seem to get the firefox plugin to work correctly. I tried the way the above linked instructed me to do so but it did not work. So I tried the following:

$ cd /usr/lib/firefox-3.6.8/plugins
$ ln -s /usr/lib/jvm/jre1.6.0_21/lib/i386/ns7/libjavaplugin_oji.so libjavaplugin_oji.so

and restarted firefox it did not work. I'm not sure what else to do in order for firefox to recognize the new JRE.

---

### Post by ybh305 on 2010-09-09
bump.

---

### Post by allanforever on 2010-09-15
Today I have Sun's Java installed on my Ubuntu, but in the past i kept trying to install it for a long time. Then I read someone's comment in a forum that just said: install it with dpkg.
Then I run into repositories and downloaded *.deb files that everyone having troubles to install java on Ubuntu have read before (bin, jre, fonts, plugin).
Some days ago I updated the java from 6.20 to 6.21.
If you do like I did, the sun-java* packages will be listed on synaptic repositories, then it's just uninstall it and run the command below to update Sun's Java:
```
sudo dpkg -i sun-java6-bin_6.21-1_i386.deb sun-java6-fonts_6.21-1_all.deb sun-java6-jre_6.21-1_all.deb sun-java6-plugin_6.21-1_i386.deb
```
It's an alternative, but it works very fine.
If you don't know where to look to download the *.deb files try [ftp://ftp.debian.org/debian/pool/non-free/s/sun-java6/](ftp://ftp.debian.org/debian/pool/non-free/s/sun-java6/)
Hope that helps (sorry for my bad English).

---

