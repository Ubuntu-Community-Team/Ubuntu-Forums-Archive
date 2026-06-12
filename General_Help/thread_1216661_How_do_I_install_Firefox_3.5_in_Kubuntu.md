---
title: "How do I install Firefox 3.5 in Kubuntu?"
date: 2009-07-18
forum: General Help
---

### Post by Cityscape on 2009-07-18
Hi guys,

How do I install a .tar.bz2 program?

I'm a beginner so if you could tell me how as simply as possible that be awesome.

---

### Post by wojox on 2009-07-18
Right click on it and choose extract here.

---

### Post by snowpine on 2009-07-18
tar.bz is an archive file format (like .zip in windows). Literally anything could be inside the archive.

Please provide more details about what you're trying to install, and maybe we can help you.

Generally in Ubuntu, we install new applications using the Synaptic Package Manager or Add/Remove Programs. Either of these methods will install tested and trusted software from the Ubuntu repositories.

---

### Post by jerome1232 on 2009-07-18
Tar.bz2 is just an archive, like a zip file. 

So the answer depends on what is in that archive? Extract the contents out out and show us. What is this program and where was it downloaded from?

---

### Post by Cityscape on 2009-07-18
[SIZE=1]> **jerome1232 said:**
> Tar.bz2 is just an archive, like a zip file. 
So the answer depends on what is in that archive? Extract the contents out out and show us. What is this program and where was it downloaded from? [/SIZE]
Program is Mozilla Firefox, downloaded from mozilla.com.
I want to install it in Kubuntu.
Attached are the contents of the .tar file.

I see these .tar.bz2 files often and want to know how to install them.

---

### Post by snowpine on 2009-07-18
It is easier and safer to install Firefox from the repositories. As I mentioned earlier, use Synaptic or Add/Remove Programs. Or, if you like using the terminal:

> sudo apt-get install firefox

There is no "how to install .tar.bz2" because anything could be inside the archive. Usually there is a README or executable installer. Downloading and installing applications from the internet is a "windows" way of doing things; Ubuntu uses a repository of tested and trusted applications (which is one reason Linux has the reputation for stability and security).

---

### Post by jerome1232 on 2009-07-18
> **Cityscape said:**
> [SIZE=1][/SIZE]
Program is Mozilla Firefox, downloaded from mozilla.com.
I want to install it in Kubuntu.
Attached are the contents of the .tar file.

I see these .tar.bz2 files often and want to know how to install them.

As mentioned you can install that version of firefox from the repos, it's called firefox-3.5, you can search for it in synaptic, install it then set it as your default browser.

If you wanted to install the one you downloaded it's rather easy since that's just the program it self. Just a matter of making a symlink in ~/bin for just your user or copying the program to /usr/local and making a symlink to /usr/local/bin for a system wide install.

---

### Post by SunnyRabbiera on 2009-07-18
Yeh usually installing apps in linux is different then windows, granted you can find installers inside of .tar filesbut it depends on the application.
Just keep in mind ubuntu usually sticks to "stable" versions of the applications as opposed to "latest and greatest"
Especially if you use hardy.
But yeh for most applications use package managers, only use .tars when there is no other alternative.

---

### Post by snowpine on 2009-07-18
As SunnyR hinted, in Ubuntu, new versions of apps are typically "bundled" together into a new release every six months. It would be unusual for an application to "jump" to a major new version within a release.

---

### Post by Cityscape on 2009-07-18
> **jerome1232 said:**
> copying the program to /usr/local and making a symlink to /usr/local/bin for a system wide install.
Can you please expain to me exactly how to do this?
Like i said before I am very new to Linux world.

---

### Post by colin.p on 2009-07-18
> **Cityscape said:**
> Can you please expain to me exactly how to do this?
Like i said before I am very new to Linux world.

If all you are trying to do is install FF, then just follow these instructions [http://www.psychocats.net/ubuntu/firefox](http://www.psychocats.net/ubuntu/firefox)

---

### Post by jerome1232 on 2009-07-18
I would really recommend installing it from the repos, if you wanted to do that then this would get it done:

```
sudo apt-get install firefox-3.5
```

If you want to install your downloaded copy, first stick the folder on your desktop, and rename the folder to firefox-3.5

```
sudo -i
mv ~/Desktop/firefox-3.5 /usr/local
ln -s /usr/local/firefox-3.5/firefox /usr/local/bin/firefox-3.5
exit

```

---

### Post by lovinglinux on 2009-07-18
The 4 most popular methods of installation of Firefox 3.5 (Psychocats, Ubuntuzilla, Repository, Shiretoko/Swiftfox) are available in the "Install Other Versions" section of the [**[COLOR="DarkRed"]Firefox optimization and troubleshooting thread[/COLOR]**](http://ubuntuforums.org/showthread.php?t=1193567). 

There is also a detailed explanation of each installation method provided, comparing the most important differences. I personally tested all of them and they work like a charm, but I recommend methods 1 (Psychocats) and 2 (Ubuntuzilla).

---

### Post by Cityscape on 2009-07-18
Okay, something weird happened, this post is now called "How do I install Firefox 3.5 in Kubuntu". I never did name it this.

And to make it clear I am not installing Firefox 3.5, I hate Firefox 3.5.
I'm installing firefox 3.0

---

### Post by Cityscape on 2009-07-18
sudo apt-get install firefox-3.5
Cool, I didn't know I could install using such a simple code!
It worked, I just typed 3.0 instead of 3.5

But i couldn't find it in my package manager.

---

### Post by snowpine on 2009-07-18
> **Cityscape said:**
> sudo apt-get install firefox-3.5
Cool, I didn't know I could install using such a simple code!
It worked, I just typed 3.0 instead of 3.5

But i couldn't find it in my package manager.

Firefox 3.0.11 is simply called "firefox" in the package manager, as it's the default.

---

