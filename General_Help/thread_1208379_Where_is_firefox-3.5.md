---
title: "Where is firefox-3.5 ?"
date: 2009-07-09
forum: General Help
---

### Post by Orange Kingdom on 2009-07-09
Hi,

Where can i find firefox-3.5 for Ubuntu 9.04 ?
Is it available for Ubuntu? 

No firefox-3.5 in the update manager or package manager.

thnx

---

### Post by credobyte on 2009-07-09
```
sudo apt-get install firefox-3.5
```

[COLOR=Blue]aptitude search[/COLOR] is an art :lolflag:

---

### Post by Soul-Sing on 2009-07-09
There should be a 3.5 firefox in synaptic packagemanager.
I recommend installing the final 3.5 next to the "old"one.
There are several threads on this forum about howto install etc.
: [http://ubuntuforums.org/showthread.php?t=1193567&highlight=FOT](http://ubuntuforums.org/showthread.php?t=1193567&highlight=FOT)

---

### Post by squaregoldfish on 2009-07-09
In Synaptic you can find the firefox-3.5 package, which is what you're after.

This isn't an officially-supported package, so it will be installed alongside your existing Firefox installation. The executable is firefox-3.5

Steve.

---

### Post by Villiam on 2009-07-09
I haven't done it on my ubuntu by after installing 3.5 on xp disabled many of my extension (add-ons). Just a word of caution if you have some important extensions installed.

[ubuntu]("http://www.linux-archive.org/ubuntu-user/")

---

### Post by lovinglinux on 2009-07-09
> **Orange Kingdom said:**
> Hi,

Where can i find firefox-3.5 for Ubuntu 9.04 ?
Is it available for Ubuntu? 

No firefox-3.5 in the update manager or package manager.

thnx

You need to enable the universe repository to install it via Synaptic.

The 4 most popular methods of installation of Firefox 3.5 (Psychocats, Ubuntuzilla, Repository, Shiretoko/Swiftfox) are available in the "Install Other Versions" section of the [**[COLOR="DarkRed"]Firefox optimization and troubleshooting thread[/COLOR]**](http://ubuntuforums.org/showthread.php?t=1193567). 

There is also a detailed explanation of each installation method provided, comparing the most important differences. I personally tested all of them and they work like a charm, but I recommend methods 1 (Psychocats) and 2 (Ubuntuzilla).

---

### Post by KarenAK on 2009-07-09
sudo apt-get install firefox-3.5
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E:** [COLOR=Red]Couldn't find package firefox-3.5[/COLOR]**


[IMG]http://i107.photobucket.com/albums/m312/KarenAK/Temp/Repositories.png[/IMG]


is it available only for Jaunty Jackalope ?

---

### Post by lovinglinux on 2009-07-09
> **KarenAK said:**
> sudo apt-get install firefox-3.5
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E:** [COLOR=Red]Couldn't find package firefox-3.5[/COLOR]**


[IMG]http://i107.photobucket.com/albums/m312/KarenAK/Temp/Repositories.png[/IMG]


is it available only for Jaunty Jackalope ?

Yes, but...

> From: [https://help.ubuntu.com/community/FirefoxNewVersion](https://help.ubuntu.com/community/FirefoxNewVersion)

Please check back here in a few days.
The Ubuntu Mozilla Team is working to make Firefox 3.5 available for older releases. 

Nevertheless, you can install through methods #1 and #2 from the "Installing Other Versions" section of the [**[COLOR="DarkRed"]Firefox optimization and troubleshooting thread[/COLOR]**](http://ubuntuforums.org/showthread.php?t=1193567). They work pretty well.

---

### Post by KarenAK on 2009-07-09
All right !! 

I have a "Minefield" on my comp now LOL

Thank you :-)

---

### Post by Orange Kingdom on 2009-07-09
Thanks but i thought Firefox is supported by Ubuntu. It is not if i am correct.

I did this: sudo apt-get install firefox-3.5
It installed 3.5 but when i start Firefox it is still the old one.

Apperently it doesn't upgrage the old one i suppose.

---

### Post by Refreshment on 2009-07-09
Hi comunity:

Used Synaptic. Typed mozilla firefox 3.5. Don´t remember exactly bu there was a package that sai:¨free webbrowser¨ or something. I installed it and nothing happened.

---

### Post by KarenAK on 2009-07-09
If you installed it correctly. you will find it in your Applications | Internet folder.

It is called: Minefield 3.5 Web Browser

Run it parallel to the old Firefox until it is fully integrated.

---

### Post by lovinglinux on 2009-07-09
> **Orange Kingdom said:**
> Thanks but i thought Firefox is supported by Ubuntu. It is not if i am correct.

Firefox 3.0 is, but Firefox 3.5 is new and will only be official in the next release of Ubuntu.


> **Orange Kingdom said:**
> Thanks but i thought Firefox is supported by Ubuntu. It is not if i am correct.

I did this: sudo apt-get install firefox-3.5
It installed 3.5 but when i start Firefox it is still the old one.

Apperently it doesn't upgrage the old one i suppose.

I recommend reading the "Install Other Versions" section of the [**[COLOR="DarkRed"]Firefox optimization and troubleshooting thread[/COLOR]**](http://ubuntuforums.org/showthread.php?t=1193567). It explains the differences between the most common methods of installation and answers your questions.

---

### Post by scouser73 on 2009-07-09
I suggest that you follow the instructions in [Kabatology](http://www.kabatology.com/07/01/a-single-command-install-of-firefox-3-5-on-ubuntu/)

---

### Post by brad1138 on 2009-07-10
> **KarenAK said:**
> If you installed it correctly. you will find it in your Applications | Internet folder.

It is called: Minefield 3.5 Web Browser

Run it parallel to the old Firefox until it is fully integrated.

When 3.5 becomes available through update manager what happens to Minefield? will they conflict at all?

thanks,
Brad

---

### Post by lovinglinux on 2009-07-10
> **brad1138 said:**
> When 3.5 becomes available through update manager what happens to Minefield? will they conflict at all?

thanks,
Brad

No, they won't conflict with each other because they are installed side-by-side, they have their own launchers, installation folders and user profiles. By the time 3.5 becomes available through the update manager, Minefield will probably be another version already (3.5.x).

---

### Post by masterton on 2009-07-10
> **Villiam said:**
> I haven't done it on my ubuntu by after installing 3.5 on xp disabled many of my extension (add-ons). Just a word of caution if you have some important extensions installed.

Most addons don't work because they haven't updated the maxversion piece of information Most works flawlessly if you bypass this check. [MR Tech's Toolkit - Firefox addon]("http://www.mrtech.com/extensions/local_install/") helps you to do that.

If a few addons still don't work after the above method try to search for a dev build. Some developers offer it to install on the new Firefox 3.5

I installed fairly many addons and all my addons have been successfully transported to the new environment after using both methods.

Firefox 3.5 is much faster, load Flash faster and use 50% less memory usage. It's worth upgrading.

---

### Post by saf-t scissors on 2009-07-10
Lovinglinux, I looked at your thread and frankly, that's nonsense. I should just be able to go to Help -> Check for Updates and let FF upgrade itself. Unfortunately, Ubuntu prevents this.

People can attempt to make rolling distro arguments all they want, but it's ridiculous to think that I should have to install a second instance of FF until Ubuntu deems it "safe" for me to upgrade through FF or the package manager.

---

### Post by pjalegria on 2009-07-10
I have to agree with you... wrong way canonical ;)

---

### Post by lovinglinux on 2009-07-10
> **saf-t scissors said:**
> Lovinglinux, I looked at your thread and frankly, that's nonsense. I should just be able to go to Help -> Check for Updates and let FF upgrade itself. Unfortunately, Ubuntu prevents this.

People can attempt to make rolling distro arguments all they want, but it's ridiculous to think that I should have to install a second instance of FF until Ubuntu deems it "safe" for me to upgrade through FF or the package manager.

> **pjalegria said:**
> I have to agree with you... wrong way canonical ;)

And here we ago again...

I will refrain myself from this discussing this. There are enough threads with this subject.

[http://www.asoftsite.org/s9y/archives/161-FAQ-Why-is-my-firefox-3.5-still-called-Shiretoko.html](http://www.asoftsite.org/s9y/archives/161-FAQ-Why-is-my-firefox-3.5-still-called-Shiretoko.html)

---

### Post by wongpk on 2009-07-10
A quick question (sorry if it sound off topic)

I installed FireFox 3.5 in my Ubuntu 8.10, the font looks crip instead of smooth. Any idea?

---

### Post by lovinglinux on 2009-07-11
> **wongpk said:**
> A quick question (sorry if it sound off topic)

I installed FireFox 3.5 in my Ubuntu 8.10, the font looks crip instead of smooth. Any idea?

Everyone is having the same problem. Try this [http://ubuntuforums.org/showpost.php?p=7544051&postcount=3](http://ubuntuforums.org/showpost.php?p=7544051&postcount=3)

---

