---
title: "Installing Adobe Flash for firefox, on Ubuntu 9.04"
date: 2009-09-09
forum: General Help
---

### Post by Carpentr on 2009-09-09
I just re-installed Ubuntu 9.04 after a few months of using a different operating system. I installed it with a Ubuntu disc I had laying around the house. When I go to install Adobe's Flash player (using the .deb file I downloaded from their official website) I get the following error: 

Error: Wrong architecture 'i386'

This leads me to believe I am running a 64-bit version of Ubuntu 9.04 and the installer only works on 32-bit versions. Problem is, I can't remember which version(32-bit or 64-bit) I burned on to my CD before I installed Ubuntu. Could that possibly be the reason why flash will not install? If so, how would I go about installing flash on a 64-bit system?

I am using Firefox if that helps.

Thank you.

---

### Post by tuxxy on 2009-09-09
> **Carpentr said:**
> I just re-installed Ubuntu 9.04 after a few months of using a different operating system. I installed it with a Ubuntu disc I had laying around the house. When I go to install Adobe's Flash player (using the .deb file I downloaded from their official website) I get the following error: 

Error: Wrong architecture 'i386'

This leads me to believe I am running a 64-bit version of Ubuntu 9.04 and the installer only works on 32-bit versions. Problem is, I can't remember which version(32-bit or 64-bit) I burned on to my CD before I installed Ubuntu. Could that possibly be the reason why flash will not install? If so, how would I go about installing flash on a 64-bit system?

I am using Firefox if that helps.

Thank you.

Firstly we need to find out which Ubuntu version you did install, open up a terminal and run this command;

```
uname -m
```

If the output is something like x86_64 then congratulations you are on 64-Bit, good choice :D

Now to install Flash there is no need to use Adobes website, if you are on 64-Bit then you simply need to download [this file]("http://labs.adobe.com/downloads/flashplayer10.html") and extract it to your /usr/lib/mozilla/plugins directory.  This is the official 64-Bit Flash driver from Adobe and is very good.

If however you were on 32-Bit Ubuntu then load your terminal backup and run this command;

```
sudo apt-get install flashplugin-nonfree
```

---

### Post by Carpentr on 2009-09-09
It seems that I am running Ubuntu 9.04 64-bit. I extracted the file you instructed me to download to my desktop, and then tried to copy and paste it to the specified directory you gave me but I keep getting the following error:
```

There was an error moving the file into /usr/lib/mozilla/plugins
Error moving file: Permission denied

```

Thank you.

---

### Post by tuxxy on 2009-09-09
> **Carpentr said:**
> It seems that I am running Ubuntu 9.04 64-bit. I extracted the file you instructed me to download to my desktop, and then tried to copy and paste it to the specified directory you gave me but I keep getting the following error:
```

There was an error moving the file into /usr/lib/mozilla/plugins
Error moving file: Permission denied

```

Thank you.

Excellent choice on 64-Bit bud :D ok yes it should give you this error as your attempting to move it to your filesystem and as you know you dont have permission.  To do this the easy way open a terminal and run this command

```
gksudo nautilus /usr/lib/mozilla/plugins
```

Now a root nautilus window will open and you will be in the correct directory already, so just drag and drop it in.  Don't forget to close this new nautilus window once you have moved the file.

You could also do this solely via terminal depending on how familiar you are with its use, if you fancy trying it then would be something like this;

```
sudo mv /home/user/Desktop/libflashplayer.so /usr/lib/mozilla/plugins
```

Obviously you will need to replace the "user" with your account username.  If you stick to the first method though you can't go wrong :D

---

### Post by Carpentr on 2009-09-09
> **tuxxy said:**
> 

```
sudo mv /home/user/Desktop/libflashplayer.so /usr/lib/mozilla/plugins
```


Worked like a charm. Thanks a lot for your help.

---

### Post by tuxxy on 2009-09-09
> **Carpentr said:**
> Worked like a charm. Thanks a lot for your help.

hehe glad it worked bud, btw you should really install ubuntu-restricted-extras package on a fresh install, it will provide flash, java, codecs etc

The only issue with this package on 64-Bit is that it includes 32-bit Flash however it only takes a moment to remove the 32-bit flashplugin-nonfree package :D

oh and you might like [this link]("http://ubuntuforums.org/group.php?groupid=258") :D

---

### Post by Carpentr on 2009-09-09
> **tuxxy said:**
> hehe glad it worked bud, btw you should really install ubuntu-restricted-extras package on a fresh install, it will provide flash, java, codecs etc

The only issue with this package on 64-Bit is that it includes 32-bit Flash however it only takes a moment to remove the 32-bit flashplugin-nonfree package :D

oh and you might like [this link]("http://ubuntuforums.org/group.php?groupid=258") :D
Alright, and thanks for the link as well. I just joined the user group. It should be helpful; I still got a lot to learn.

---

### Post by tuxxy on 2009-09-09
No problem bud we all still learning :D

---

