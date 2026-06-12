---
title: "I'm not allowed to play mp3 files on ubuntu"
date: 2012-05-03
forum: General Help
---

### Post by venkatnani on 2012-05-03
Hi all ,
I'm new to ubuntu .When I'm trying to play Mp3 files .It asking me like "The play back of this movie requires a MPEG-1 layer3(Mp3)decoder plug in which is not installed ".Could anybody help me how to  solve this problem .

Thanks in advance

---

### Post by mips on 2012-05-03
Copy and paste into terminal,
```
sudo apt-get install ubuntu-restricted-extras
```

You can also install it via the software centre, just search for ubuntu restricted extras which will install all the codecs, dvd, flash and other stuff which they cannot legally distribute with ubuntu.

Some tips you might want to consider,
[http://www.my-guides.net/en/guides/linux/330-ubuntu-1204-precise-pangolin-post-installation-guide](http://www.my-guides.net/en/guides/linux/330-ubuntu-1204-precise-pangolin-post-installation-guide)

---

### Post by rg4w on 2012-05-03
Good news:  this is one of the most common issues with Linux, and thankfully one of the easiest to resolve.

For legal reasons, Ubuntu does not ship with many popular media codecs preinstalled.  But they are available for the user to download through the Ubuntu Software Center.

Check the USC for "Ubuntu Restricted Extras", and report back here if installing that package still doesn't allow you to play those (and many other) file types.

---

### Post by fkurniaaziz on 2012-05-04
if you want, you can try to install audacious, it include many codecs

sudo apt-get install audacious

---

### Post by venkatnani on 2012-05-04
Hi rg4w
I've checked for ubuntu-restricted-extras in Ubuntu software center,but it has shown like "Not  available in the current data".Then searched Ubuntu restricted extras in the following community "https://help.ubuntu.com/community/RestrictedFormats".But I could not prompted to download the package .So could you  please suggest me what to do ...

Thanks in advance .

---

### Post by venkatnani on 2012-05-04
Hi all 
I'm trying to install ubuntu-restricted extras package .But its showing as shown below 

[B]venkat@venkat-desktop:/tmp$ ls
keyring-fNHYej  pulse-kKdXB9xdux60  tmp_Q4gR1
orbit-gdm       pulse-PKdhtXMmr18n  ubuntu-restricted-extras_39_i386.deb
orbit-venkat    ssh-irgBAO1543      virtual-venkat.T5cGmq
venkat@venkat-desktop:/tmp$ sudo apt-get install ubuntu-restricted-extras_39_i386.deb 
[sudo] password for venkat: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package ubuntu-restricted-extras_39_i386.deb
venkat@venkat-desktop:/tmp$ [/B]


Please tell me how to resolve this problem .
Thanks in advance .

---

### Post by carl4926 on 2012-05-04
```
sudo apt-get install ubuntu-restricted-extras
```

---

### Post by gordintoronto on 2012-05-04
What version of Ubuntu?

In Software center, you might need to enable the multiverse repository.

---

### Post by venkatnani on 2012-05-05
Hi 
My question may be stupid ,but I got fed up to finding the package and get installed .Can any one suggest me as naive .

---

### Post by mips on 2012-05-05
[https://help.ubuntu.com/community/Repositories/Ubuntu#Ubuntu_Software_Tab](https://help.ubuntu.com/community/Repositories/Ubuntu#Ubuntu_Software_Tab)

Make sure restrited & multiverse are enabled.

[IMG]https://help.ubuntu.com/community/Repositories/Ubuntu?action=AttachFile&do=get&target=SoftwareSources-UbuntuSoftware.png[/IMG]

Try installing again.

---

### Post by howefield on 2012-05-05
Threads merged.

---

### Post by venkatnani on 2012-05-05
I've checked .They were already enabled .

I'm downloading the package from

" http://packages.ubuntu.com/lucid/i386/ubuntu-restricted-extras/download"

And installing as 

sudo apt-get install ubuntu-restricted extras in a terminal .I couldn't figure out where could be the problem...

---

### Post by venkatnani on 2012-05-05
I'm using ubuntu 9.10 version

---

### Post by forrestcupp on 2012-05-05
> **venkatnani said:**
> I've checked .They were already enabled .

I'm downloading the package from

" http://packages.ubuntu.com/lucid/i386/ubuntu-restricted-extras/download"

And installing as 

sudo apt-get install ubuntu-restricted extras in a terminal .I couldn't figure out where could be the problem...

> **venkatnani said:**
> I'm using ubuntu 9.10 version
If you're using 9.10, you're using Karmic, and you shouldn't be installing a Lucid package.

You don't need to manually download anything at all to install this. In your last command, you left out a hyphen. Highlight and copy the following command, then open a terminal and press Shift+Ctrl+V to paste the command in the terminal, then press enter to install it:
```
sudo apt-get install ubuntu-restricted-extras
```

---

### Post by aysiu on 2012-05-05
> **venkatnani said:**
> I'm using ubuntu 9.10 version
That version is no longer supported. Its end-of-life was April, 2011.

---

