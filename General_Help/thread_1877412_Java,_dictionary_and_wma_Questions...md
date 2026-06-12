---
title: "Java, dictionary and wma Questions.."
date: 2011-11-08
forum: General Help
---

### Post by SA_LinuxNewb on 2011-11-08
Hi!
Im using Lubuntu 11.10 on a MaxData 8100X.

I wanted to install Java (from the Lubuntu Tutorial) but I got following Error:

dominik@dominik-PRO-8100X:~$ sudo apt-get install sun-java6-{jre,bin,plugin,fonts}
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package sun-java6-jre is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source

Package sun-java6-fonts is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source

E: Package 'sun-java6-jre' has no installation candidate
E: Unable to locate package sun-java6-bin
E: Unable to locate package sun-java6-plugin
E: Package 'sun-java6-fonts' has no installation candidate

How can I fix that?

The language I use in Lubuntu is english, but I write a lot of german as well. So the spellcheck is always marking my german als false (obviously).
How can I turn of the spell check in Chrome?
Or better, how can I install a german spellcheck and quickly switch between them when I need it?

When I use Audacious I cant play wma...
how do you install the right codec?
When I'm adding files to the playlist, there is a button with "search" but it doesnt work. How do I fix that? Because I have a big music lib and searching the lib would be nice. (I already installed catfish, but then its always two apps)

How do I change the audio settings? Like standard input device and so on...

Easiest way to install flash? Just select on Adobe Linux 32Bit and then Ubunutu?

Thanks for the help. I use Lubuntu for one week now and its amazing how fast my old laptop is now. I almost like sitting in front of my new PC at home. :)
I just configure the last parts so I can do everything I want with it. :)

---

### Post by Rodney9 on 2011-11-08
I am sorry can not help you with Java, but have you had a look at this page , it may help, -
[https://help.ubuntu.com/community/Java](https://help.ubuntu.com/community/Java)

For spell in Chromium , Select Preferences
Click the Under the Hood tab
click Languages and spell-checker settings
In the Languages and Input dialog that appears, use the "Enable spell checking" checkbox to turn the spell-checker on or off.

For Audacious have you installed lubuntu-restricted-extras ?

Rodney

---

### Post by SA_LinuxNewb on 2011-11-08
I'll look over that Java thing.

Thx for the help in Chromium. :)
I already looked at the settings, but I didnt see that.

I think I clicked "install 3rd Party"-Things when I was installing.
How can I check if I installed lubuntu-restricted-extras?
and if not, how do I isntall it?

---

### Post by Rodney9 on 2011-11-08
> **SA_LinuxNewb said:**
> 
How can I check if I installed lubuntu-restricted-extras?
and if not, how do I isntall it?

Open Synaptic in System Tools on the menu
Click on search and paste ```
lubuntu-restricted-extras
```
in the box, this will show whether or not they are installed. If it  is not installed select it and click apply.

or

You could type in the terminal ```
sudo apt-get install lubuntu-restricted-extras
``` and this will tell you if it is installed or ask you to install.

Rodney

---

### Post by SA_LinuxNewb on 2011-11-09
Thanks!
I havn't installed it yet, its 50mb and I'll wait for the night to use night owl traffic. :D

So the last question is:
Audacious:
When I'm adding files to the playlist, there is a button with "search" but it doesnt work. How do I fix that? Because I have a big music lib and searching the lib would be nice. (I already installed catfish, but then its always two apps)

---

### Post by Rodney9 on 2011-11-09
> **SA_LinuxNewb said:**
> Thanks!
I havn't installed it yet, its 50mb and I'll wait for the night to use night owl traffic. :D

So the last question is:
Audacious:
When I'm adding files to the playlist, there is a button with "search" but it doesnt work. How do I fix that? Because I have a big music lib and searching the lib would be nice. (I already installed catfish, but then its always two apps)

Yes your correct, I can not get it to search either.
I will try  to research this further.

Rodney

---

### Post by SA_LinuxNewb on 2011-11-10
Yeah, because searching your music files is one of the most important things. :D

---

### Post by Rodney9 on 2011-11-10
> **SA_LinuxNewb said:**
> Yeah, because searching your music files is one of the most important things. :D

I am still trying to find out how, there seems to be a lot of contradictory information.

[http://ubuntuforums.org/showthread.php?t=1878541&highlight=lubuntu](http://ubuntuforums.org/showthread.php?t=1878541&highlight=lubuntu)

You can try ctrl f or just j and see if it works for you.

Rodney

---

### Post by Rodney9 on 2011-11-10
I have done some research on other *lightweight* music players with playlists, these four all get good reports -

[http://aqualung.factorial.hu/](http://aqualung.factorial.hu/)

[http://code.google.com/p/quodlibet/](http://code.google.com/p/quodlibet/)

[http://deadbeef.sourceforge.net/](http://deadbeef.sourceforge.net/)

[http://sourceforge.net/projects/guayadeque/](http://sourceforge.net/projects/guayadeque/)

Rodney

---

