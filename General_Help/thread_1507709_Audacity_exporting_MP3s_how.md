---
title: "Audacity exporting MP3s how?"
date: 2010-06-11
forum: General Help
---

### Post by daldude on 2010-06-11
How do you export a MP3 file in Audacity? When I try to export it asks for the location of the file libmp3lame.so.0. I found the file and told Audacity where to look for it but when I hit Ok it gave me an error message Could not open MP3 encoding library!
I've gotten it to work before but forgot what I did to get it to be able to export to MP3 format, I think maybe it just started to work or maybe after I installed some program.

I had to reinstall Ubuntu and that is why Audacity can't export to MP3 any more because what ever I did to get it working was lost when I had to reinstall Ubuntu.

---

### Post by dcstar on 2010-06-12
> **daldude said:**
> How do you export a MP3 file in Audacity? When I try to export it asks for the location of the file libmp3lame.so.0. I found the file and told Audacity where to look for it but when I hit Ok it gave me an error message Could not open MP3 encoding library!
.........

Probably because you have not installed the **lame** packages.

---

### Post by daldude on 2010-06-12
How do I install LAME Packages? The Audacuty Webpage only has Windows and MAC OS instructions.

> **dcstar said:**
> Probably because you have not installed the **lame** packages.

---

### Post by oldos2er on 2010-06-12
```
sudo apt-get install lame
```

---

### Post by bab1 on 2010-06-12
> **oldos2er said:**
> ```
sudo apt-get install lame
```

As described in [**_this guide_**]("http://ubuntuforums.org/showthread.php?t=677609").  It is in the multiverse repos.

---

### Post by daldude on 2010-06-26
I still can't export MP3s I typed this 
sudo apt-get install lame


 in a terminal window but Audacity still gives me the error message 
"Could not open MP3 encoding library!"

---

### Post by bab1 on 2010-06-26
> **daldude said:**
> I still can't export MP3s I typed this 
sudo apt-get install lame


 in a terminal window but Audacity still gives me the error message 
"Could not open MP3 encoding library!"

This is a little dated but it you basically have to tell Audacity where the LAME libs are located.  Look under Edit>>Preferences--->Libraries 

See [**_here_**]("http://wiki.audacityteam.org/index.php?title=Lame_Installation#GNU.2FLinux.2FUnix_instructions").  Look for the section: **Setting Audacity up to use LAME**.

---

### Post by daldude on 2010-06-27
> **bab1 said:**
> This is a little dated but it you basically have to tell Audacity where the LAME libs are located.  Look under Edit>>Preferences--->Libraries 

See [**_here_**]("http://wiki.audacityteam.org/index.php?title=Lame_Installation#GNU.2FLinux.2FUnix_instructions").  Look for the section: **Setting Audacity up to use LAME**.

That did the trick, Thanks.:guitar:

It's annoying that it is so complicated and difficult to get this to work if you are not using a for profit popular operating system. With Windows and MAC it's all automated by Audacity but with the free operating system you have to do it all manually and know something about how the operating system works.

Thanks again for the solution to my problem.):P:p

---

### Post by bab1 on 2010-06-27
> **daldude said:**
> That did the trick, Thanks.:guitar:

It's annoying that it is so complicated and difficult to get this to work if you are not using a for profit popular operating system. With Windows and MAC it's all automated by Audacity but with the free operating system you have to do it all manually and know something about how the operating system works.

Thanks again for the solution to my problem.):P:p

I think you will find that the installation of LAME is basically the same regardless of the OS type.  The LAME libs are not part of Audacity per se.  They always have to be downloaded and then located to be used properly.  

The only difference is the MS version uses a .exe file and .dlls whilst Linux uses the LAME libs libmp3lame0.  This is more a packaging difference than a design difference.

---

