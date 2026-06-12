---
title: "Perplexed with Seamonkey version 2.8 in .tar.bz2 format!"
date: 2012-04-08
forum: General Help
---

### Post by Saurabhdua on 2012-04-08
Hello Folks!

Iam with version 10.10 of Ubuntu Linux. Have just downloaded Seamonkey's installer, version 2.8 in "Weird" .tar.bz2 format!?:confused:

Could you please let me know on what to do next?? Archive Manager do not yields any significant file to be installed; & Archive Mounter has simply mounted a "Solid Plate" over my Desktop!

What kind of "NO Struggle" steps to be followed in order to install the same?

---

### Post by kc1di on 2012-04-08
> **Saurabhdua said:**
> Hello Folks!

Iam with version 10.10 of Ubuntu Linux. Have just downloaded Seamonkey's installer, version 2.8 in "Weird" .tar.bz2 format!?:confused:

Could you please let me know on what to do next?? Archive Manager do not yields any significant file to be installed; & Archive Mounter has simply mounted a "Solid Plate" over my Desktop!

What kind of "NO Struggle" steps to be followed in order to install the same?
Hi,
the file you downloaded is a compressed file. Seamonkey is available in the Ubuntu repositories and my suggestion is you install the one from there but if you want 2.8 then all you have to do is expand the package with the archive manager to your home folder will do for now.  After it is unpacked you can navigate to the folder and look for a file name seamonkey.  click on that and it will run.  Now you will have to make links to the proper directories and folders if you want it complete intergrated with Ubuntu. 
good Luck

---

### Post by raja.genupula on 2012-04-08
> **Saurabhdua said:**
> Hello Folks!

Iam with version 10.10 of Ubuntu Linux. Have just downloaded Seamonkey's installer, version 2.8 in "Weird" .tar.bz2 format!?:confused:

Could you please let me know on what to do next?? Archive Manager do not yields any significant file to be installed; & Archive Mounter has simply mounted a "Solid Plate" over my Desktop!

What kind of "NO Struggle" steps to be followed in order to install the same?

[http://www.seamonkey-project.org/releases/seamonkey1.1.7/installation#linux_install_manual](http://www.seamonkey-project.org/releases/seamonkey1.1.7/installation#linux_install_manual)

---

### Post by Peripheral Visionary on 2012-04-08
I use Xubuntu 10.04 and installed Seamonkey 2.8 from the [Ubuntuzilla]("http://sourceforge.net/apps/mediawiki/ubuntuzilla/index.php?title=Main_Page") repository! It's the easiest way to get up-to-date versions of the Mozilla software for Ubuntu. I don't know why Seamonkey hasn't been updated in the Ubuntu repositories yet, but simply add this PPS and you're off and running.

Four commands in your terminal:

```
echo -e "\ndeb  http://downloads.sourceforge.net/project/ubuntuzilla/mozilla/apt all  main" | sudo tee -a /etc/apt/sources.list > /dev/null 
```

Then

```
sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com C1289A29
```

Then 
```
 sudo apt-get update 
```

and finally

```
sudo apt-get install seamonkey-mozilla-build
```

Done! Enjoy!

---

### Post by raja.genupula on 2012-04-08
> **peripheral visionary said:**
> i use xubuntu 10.04 and installed seamonkey 2.8 from the [ubuntuzilla]("http://sourceforge.net/apps/mediawiki/ubuntuzilla/index.php?title=main_page") repository! It's the easiest way to get up-to-date versions of the mozilla software for ubuntu. I don't know why seamonkey hasn't been updated in the ubuntu repositories yet, but simply add this pps and you're off and running.

Four commands in your terminal:

```
echo -e "\ndeb  http://downloads.sourceforge.net/project/ubuntuzilla/mozilla/apt all  main" | sudo tee -a /etc/apt/sources.list > /dev/null 
```

then

```
sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com c1289a29
```

then 
```
 sudo apt-get update 
```

and finally

```
sudo apt-get install seamonkey-mozilla-build
```

done! Enjoy!

+1

---

### Post by kc1di on 2012-04-08
Thanks for the tip Peripheral Visionary,
Works fine in 12.04 also . ;)

---

### Post by maureenc on 2012-04-16
Hi,

Is it my misunderstanding, or does the repository method force the download of Firefox and Thunderbird as well as Seamonkey?

It seems to consist of an joint installation package and you don't seem to be able to just download/install Seamonkey on it's own.

I've  already removed Firefox in favour of Midori and plan to remove Thunderbird and install Sylpheed or Claws..... I only want to download Seamonkey as it has some good Cookie blocking and other useful features that Midori doesn't currently have.

I run Ubuntu on an AC100 Netbook and Firefox and Thunderbird are just too bloated.... I have Seamonkey on a very old re-claimed laptop and it runs beautifully so should be "slim" enough for the netbook.

Guess it will have to be the Tar method? Am I right in assuming that Synaptic will pick the download up once it has been "de-compressed" into it's folders?

---

### Post by raja.genupula on 2012-04-16
synaptic will gives you only what you want . 

after downloading only it will do execution process.

---

### Post by vlad3647 on 2013-01-05
thanks so much:popcorn:

---

