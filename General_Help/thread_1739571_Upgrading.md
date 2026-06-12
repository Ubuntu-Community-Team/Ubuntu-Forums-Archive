---
title: "Upgrading"
date: 2011-04-26
forum: General Help
---

### Post by Jonker on 2011-04-26
Hello,

I want to know, which is the best method of upgrading to the next never Version. Do you recommend a fresh install (how do I get all the programs installed again), an upgrade within Ubuntu (network), or an CD-upgrade (alternate cd).

Dose it make a difference if you are upgrading from, let’s say 10.04 to 10.10 or from 10.10 to 11.04. Or are all the upgrades basically the same?

Thanks for your help

Jonker

---

### Post by Matt__ on 2011-04-26
My personal preference is always a clean install, but it depends on where and what data you have on your system (all mine is stored on a separate partition).

Open a terminal to easily create a list of installed packages like this-
```
dpkg --get-selections > installed-software
```
Save the created list on some external media/email it to yourself etc.
Install the version of your choice from cd, open a terminal and;
```
dpkg --set-selections < installed-software
```
no your system knows what it needs to install so continue with;
```
sudo dselect
```
Dselect session will open, type / and allow it to install your packages form the list and when its done q and enter to quit the session.

Remember to ALWAYS back up your important data before you do anything major to your system!


//edit: the first dpkg can be edited to this if you want to send the list direct to your email account---
dpkg &#8211;get-selections | grep -v deinstall > ubuntu-files; cat ubuntu-files | mailx -s &#8220;ubuntu-files&#8221; [email]my.mail@my.addres[/email]s (from [http://www.arsgeek.com](http://www.arsgeek.com))

---

### Post by 3rdalbum on 2011-04-26
> **Matt__ said:**
> My personal preference is always a clean install, but it depends on where and what data you have on your system (all mine is stored on a separate partition).

Open a terminal to easily create a list of installed packages like this-
```
dpkg --get-selections > installed-software
```

This advice is nearly obsolete: You see, the Ubuntu 11.04 installer can do this all for you.

If you boot up the 11.04 CD and run the installer, it will detect that you've already got an older version of Ubuntu installed. One of the options it gives you is to do an Upgrade. The Upgrade is actually a clean install that preserves your /home (even if it's on the same partition as your /), AND it reinstalls all the repository software that you had on the older version.

---

### Post by veggen on 2011-04-26
Hmm, this sounds a bit shaky. I have a ton of software from third party repos, I can imagine it will run into a world of trouble when it tries reinstalling those packages.

---

### Post by Ronalddig on 2011-04-26
guys , my query :

since i am new i just ,ade 2 partition swap and / (root )


but now i see that you should make separate partition for /home.

my question is if i make separate partition for /home , and now let say i decide to do fresh install of new release

so 1. do i delete only swap and root  ?
2. on fresh installation, do i only make swp and / partition, so would home partition be visible to it

3. so how much space should be given to root then ?

---

### Post by stoneage on 2011-04-26
> **veggen said:**
> Hmm, this sounds a bit shaky. I have a ton of software from third party repos, I can imagine it will run into a world of trouble when it tries reinstalling those packages.

It will simply disable all your non standard software sources then attempt to implement the same ones for Natty. It will also tell you what it is doing, but it will leave all your old, obsolete ppa's commented out on the sources.list for you to clean up later. You can either re-enable them if they are relevant, or delete them if they are not.

---

### Post by Jonker on 2011-04-26
I think, that I'll go for the absolute clean install. I have got quite allot of programs installed from the software centre, so I don't think, that the list will be a problem. You see, I have already upgraded to the 11.04 Beta 2. And then I installed gnome 3. Since both are still in development and the final releases will be out soon, I'll wait for dose and then make a fresh installe. So would Gnome3 and unity appear to in this list?

Tanks for your quick responces.

Jonker

---

### Post by abhilashm86 on 2011-04-26
At this point of time, it would be better to wait for couple more days before trying out ubuntu 11.04. Since there might be mighty bugs along with unity which a beginner user cannot handle at times and can lead his system to crash. 


But if you want to give it a shot, then fresh vanilla install/install on a virtualbox would be better, you can try ubuntu 11.04 here online which runs on amazon cloud and its free [http://try-ubuntu-beta.ec42.net/](http://try-ubuntu-beta.ec42.net/) . 

I too played with jaunty and 8.10 which lead to some issues but finally  learnt to handle the bugs, good luck mate.

---

### Post by Jonker on 2011-04-26
But would it be possible, to once download all the programs, which are save on the list I created and save these to a CD or DVD ( or even an USB). Then you only would to download the future updates. Plus you could install the apps from the CD. Would this work?
 
thx

---

