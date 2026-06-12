---
title: "How to install an application?"
date: 2010-02-07
forum: General Help
---

### Post by rockpoper on 2010-02-07
Hi. I'm new to Ubuntu, and also new to Linux.
So basically I have many many Questions to ask.
So I describe myself as a new human being in this Linux world.

Today I found out when I download an application, it comes in "tar.gz" format,
so I searched for solution, and the only answer I get is to go to the package manager and download the package. well... that is not a relevant answer.

Then I went to try out the Firefox, so I found out that the Firefox was out-of-date, it was only v3.5 , I went to Help> and where is the check for update option, I was like Huh!? Where is that button? So I googled it and found out the update website, then I downloaded the file, before I open it, I saw "tar.gz" o.O!!??

Nevermind, I plug in my pendrive to play some music, then the movie player came out and gave me an error message that I have to download some files to play this mp3 format. Ok, I guess a 600MB operating installer doesn't comes with everything, and I clicked download.
Dang! Error! Could not locate the file .... Uhhg....

Ok, I switched back to windows, went to Youtube to search for solution on how to install tar.gz files. The video showed me, first you extract the file to anywhere, then you open the file, then you *blah blah blah* the terminal, type this command XYZABC^#*    (@.@)?!!!?? 

So, my main question is how to install an application downloaded from a website? 
Don't tell me it's package manager because there are many things I can't download there.

---

### Post by Silvertones on 2010-02-07
Do not download applications willy nilly and install. If there not in synaptic you don't need them.

---

### Post by TeoBigusGeekus on 2010-02-07
Installing software:
[http://www.psychocats.net/ubuntu/installingsoftware]("http://www.psychocats.net/ubuntu/installingsoftware")

MP3 and other proprietary formats: 
Ubuntu cannot ship with all the necessary codecs to play mp3s, dvds, etc.
You must install them yourself.
Open a terminal and type
```
sudo apt-get install ubuntu-restricted-extras
```
This command will install them along with other useful things (flash, microsoft fonts, etc.)

---

### Post by erik2912 on 2010-02-07
Untarring (tar zxvf {tar package})
going to that dir with a terminal
read README
mostly 
./configure
make
make install
is enough
Or just use the PACKAGE MANAGER!!!
This keeps your ubuntu working good, it keeps your programs up-to-date and your ubuntu secure.

---

### Post by rockpoper on 2010-02-07
Anyway, thanks guys. Although it's the same answer i got, i guess that's the only way to get it done...:neutral:
I'll try;) until i get it.

---

### Post by JeyPeyy on 2010-02-07
> **rockpoper said:**
> Today I found out when I download an application, it comes in "tar.gz" format,
so I searched for solution, and the only answer I get is to go to the package manager and download the package. well... that is not a relevant answer.

Well, the first thing to do is always to look in the package manager. Of course, if you can't find the application there you'll have to search the web. Always try to find a package made specially for Ubuntu or Debian. "tar.gz" often means that it's the source code, which is not the easiest way to install software in Ubuntu. Ubuntu packages comes in ".deb" format. 

> **rockpoper said:**
> Then I went to try out the Firefox, so I found out that the Firefox was out-of-date, it was only v3.5 , I went to Help> and where is the check for update option, I was like Huh!? Where is that button? So I googled it and found out the update website, then I downloaded the file, before I open it, I saw "tar.gz" o.O!!??
Ubuntu comes with a new version every 6 mconths. During those 6 months you only get security and bug fixes. If you want to have more updates you will have to add repositories. You can find the repository for Firefox [here]("https://launchpad.net/~mozillateam/+archive/firefox-stable/").

> **rockpoper said:**
> Nevermind, I plug in my pendrive to play some music, then the movie player came out and gave me an error message that I have to download some files to play this mp3 format. Ok, I guess a 600MB operating installer doesn't comes with everything, and I clicked download.
Dang! Error! Could not locate the file .... Uhhg....
Actually it's not about Ubuntu being small, it's about the law in some countries (such as USA and Japan) not allowing Ubuntu to distribute those codecs. 
Could you please post the whole error message?

> **rockpoper said:**
> So, my main question is how to install an application downloaded from a website? 
Don't tell me it's package manager because there are many things I can't download there.
As I said above, you should look for a ".deb" or a repository. Ubuntu Software Center is not complete in Ubuntu 9.10, so I recommend looking in Synaptic. 

It's not Ubuntu's fault if some developers don't make deb-packages, but it's a shame. If they all made deb-packages, installing software would always be easy.

BTW, what software are you trying to install. It's easier to help if we know what it is.

---

### Post by rockpoper on 2010-02-07
_Thx_ for the info JeyPevy.
At least I understand more now.:)

It's just I could not download the codec, some internet problem.
I guess maybe it's because Ubuntu was downloading and installing my graphic driver when I was trying to get those codec.
Anyway I will try again when I'm free.

I was trying to install the firefox, adobe flash player for youtube.
And in my another Laptop, I wanted to install a driver, I downloaded it from
[http://ipw2200.sourceforge.net/](http://ipw2200.sourceforge.net/)

---

### Post by Ordes on 2010-02-07
for a lot of applications, you just need to add the repository, and than it will be available inside synaptic.
e.g firefox 
add this to repos

ppa:ubuntu-mozilla-daily/ppa

than update the package list.you can now either install ff 3.6, or run the update manager, it will than update your firefox to 3.6.
the repo i got here:
[https://launchpad.net/~ubuntu-mozilla-daily/+archive/ppa](https://launchpad.net/~ubuntu-mozilla-daily/+archive/ppa)
---
if there is no repo at all for a package, than u can install manually as mentioned above. however most manual installs come with a readme that u should look at...

edit:
Repos
System > Software Source > Third Party > Add

---

### Post by ok_dr on 2010-02-07
Well for most well known popular applications the graphical Software Center and Synaptic manager are enough and they do everything automatically no tar.gz files, so easy for a beginner. Are you talking maybe about some specific rare applications not available in synaptic or haven't you looked in software center and synaptic at all, cause you don't seem to mention them in your post.
As for Firefox it should be enough to update your system by opening the update manager (system/administration) and done, no need to go at the firefox site and download tar.gz files. (actually I think the update manager asks if you want to get new updates itself by default so there shouldn't even be any need to open it yourself).

---

### Post by Ordes on 2010-02-07
> **ok_dr said:**
> As for Firefox it should be enough to update your system by opening the update manager (system/administration) and done

He wants a version update, 3.5 > 3.6; not an security update. If you want the version update update manager wont do  it... in the moment...

---

### Post by rockpoper on 2010-02-07
Yup, it's not really a rare application, it a driver to support my old wireless.

---

### Post by ok_dr on 2010-02-07
> **Ordes said:**
> He wants a version update, 3.5 > 3.6; not an security update. If you want the version update update manager wont do  it... in the moment...

I guess you're right. Having been using mostly Google chrome for a long time now, I'm a little out of date on Firefox progressions, didn't know 3.6 was available.

---

### Post by Silvertones on 2010-02-07
For Firefox & Thunderbird Ubuntuzilla will get you the latest and it's safe.

---

