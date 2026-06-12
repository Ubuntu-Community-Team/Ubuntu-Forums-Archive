---
title: "Error: Please Help (Cannot download the metalink and therefore the ISO)"
date: 2010-08-05
forum: General Help
---

### Post by Vol Vox on 2010-08-05
Hello everyone!

I've visited the Ubuntu a few times in the past - but always shied away from trying it out due to how it seemed that I'd either have to delete my Windows XP or do a bunch of complicated stuff. Recently (read: tonight) however I found Wubi, which seems like it would be great.

The only problem is that when I tried to install (after choosing username/password, and language) it came up with an error. I will put an image of the error below, and transcribe it into text right after that.

--

[IMG]http://i36.tinypic.com/fa3ee0.png[/IMG]

**Ubuntu Installer**
An error occured:
Cannot download the metalink and therefore the ISO
For more information, please see the log file: c:\docume~1\andrewu\locals~1\temp\wubi-10.04-rev189.log

--

I tried going to the file it mentioned 'for more information' but couldn't find the docume~1 folder. I apologize for having to bother you folks with what hopefully will turn out to be an easily resolved and silly problem, but I'm quite technologically illiterate, at least when it comes to these type of things. ;)

I am running Windows XP Home Edition on an EeePC Netbook, with 0.99 GB of RAM. I tried (separately) installing both normal Ubuntu and Ubuntu Netbook. If any of that info helps. If there is any needed information that I need to post, please mention it and I'll try.

Thanks for any help with resolving this issue!

---

### Post by bcbc on 2010-08-06
> **Vol Vox said:**
> Hello everyone!

I've visited the Ubuntu a few times in the past - but always shied away from trying it out due to how it seemed that I'd either have to delete my Windows XP or do a bunch of complicated stuff. Recently (read: tonight) however I found Wubi, which seems like it would be great.

The only problem is that when I tried to install (after choosing username/password, and language) it came up with an error. I will put an image of the error below, and transcribe it into text right after that.

--

[IMG]http://i36.tinypic.com/fa3ee0.png[/IMG]

**Ubuntu Installer**
An error occured:
Cannot download the metalink and therefore the ISO
For more information, please see the log file: c:\docume~1\andrewu\locals~1\temp\wubi-10.04-rev189.log

--

I tried going to the file it mentioned 'for more information' but couldn't find the docume~1 folder. I apologize for having to bother you folks with what hopefully will turn out to be an easily resolved and silly problem, but I'm quite technologically illiterate, at least when it comes to these type of things. ;)

I am running Windows XP Home Edition on an EeePC Netbook, with 0.99 GB of RAM. I tried (separately) installing both normal Ubuntu and Ubuntu Netbook. If any of that info helps. If there is any needed information that I need to post, please mention it and I'll try.

Thanks for any help with resolving this issue!

You get to the log file by entering %temp% in the address bar of windows explorer. If it can't download the metalink it means there is a problem accessing the internet. Wubi requires internet access unless you download the .iso separately and run it from a disk. (It verifies the md5 checksum of the .iso). 

Downloading the .iso is a good idea anyway - to create a live CD/USB - and also if you have to reinstall it doesn't have to download it each time.

PS. I think there is a special version of ubuntu for the eeepc -  I saw some reference to it recently: [http://www.auroraos.org/](http://www.auroraos.org/) - don't know if it's still ubuntu or a new linux flavour. In fact, I know nothing about it - but thought i'd share the info.

---

### Post by 3rdalbum on 2010-08-06
download   the   ISO   yourself,   burn   it   to   CD,   and   then   you   can   run   Wubi   from   the   CD   itself.

It's   not   hard  to   do   a real   dual-boot  installation,   at   least   not   these   days,   so   you   could  boot   your   computer   from   CD   and   do   a real   Ubuntu  installation   if   you   want.

---

### Post by Vol Vox on 2010-08-06
bcbc, thanks for the tip. Unfortunately, the ISO file link on the Wubi site is broken, and I can't seem to find a download for just the ISO on the Ubuntu site. Do you happen to know where I can find it? Oh, and thanks for the Aurora tip. If this doesn't work I'll look into that.

3rdalbum, unfortunately my netbook doesn't have a CD drive, and 'dual boot' seems to complicated in any case. Thanks though.

---

### Post by bcbc on 2010-08-06
> **Vol Vox said:**
> bcbc, thanks for the tip. Unfortunately, the ISO file link on the Wubi site is broken, and I can't seem to find a download for just the ISO on the Ubuntu site. Do you happen to know where I can find it? Oh, and thanks for the Aurora tip. If this doesn't work I'll look into that.

3rdalbum, unfortunately my netbook doesn't have a CD drive, and 'dual boot' seems to complicated in any case. Thanks though.

I didn't think the wubi site had a link to download the .iso

You can get the desktop or netbook versions here:
[http://www.ubuntu.com/desktop/get-ubuntu/download](http://www.ubuntu.com/desktop/get-ubuntu/download)
[http://www.ubuntu.com/netbook/get-ubuntu/download](http://www.ubuntu.com/netbook/get-ubuntu/download)

---

### Post by Vol Vox on 2010-08-06
Wow, awesome. Between the Wubi FAQ and your help, I was able to install Ubuntu! I'm actually typing this in Firefox on Ubuntu right now. Thanks a bunch. 

I'm still trying to get used to it - it's definitely different than Windows. I'm also looking to see if there is a way to switch between the Netbook desktop view and the normal - so I can see both. But, you've done me a huge favor, so I'll just make a new thread for that.

Again, thanks a bunch bcbc. :D

---

### Post by bcbc on 2010-08-06
> **Vol Vox said:**
> Wow, awesome. Between the Wubi FAQ and your help, I was able to install Ubuntu! I'm actually typing this in Firefox on Ubuntu right now. Thanks a bunch. 

I'm still trying to get used to it - it's definitely different than Windows. I'm also looking to see if there is a way to switch between the Netbook desktop view and the normal - so I can see both. But, you've done me a huge favor, so I'll just make a new thread for that.

Again, thanks a bunch bcbc. :D

you're welcome :)
I've been browsing the forums and it appears that you can <...deleted...> and then, whenever you login, you can select in a sessions drop-down whether to login to Netbook or Ubuntu.

I'll try it myself and post back.

---

### Post by bcbc on 2010-08-06
Actually you don't need to install ubuntu-desktop.
Just click on your user name when you login, look below and select "Gnome" from the session drop down box and you're in standard desktop mode.

---

### Post by Vol Vox on 2010-08-07
I found that out after relogging, forgot to post and say so though. Thanks a bunch bcbc! I'm using Ubuntu and loving it.

---

