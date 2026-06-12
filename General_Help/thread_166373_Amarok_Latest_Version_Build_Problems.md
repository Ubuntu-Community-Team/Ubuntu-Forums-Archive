---
title: "Amarok Latest Version Build Problems"
date: 2006-04-26
forum: General Help
---

### Post by toran on 2006-04-26
Hey guys, I'm having problems building the latest version of Amarok.

Here's the error on make:

```
./.libs/libamarok.so: undefined reference to `TagLib::ID3v2::AttachedPictureFrame::description() const'
./.libs/libamarok.so: undefined reference to `TagLib::FileRef::addFileTypeResolver(TagLib::FileRef::FileTypeResolver const*)'
collect2: ld returned 1 exit status
make[4]: *** [amarokapp] Error 1
make[4]: Leaving directory `/home/jon/amarok-1.4-beta3c/amarok/src'
make[3]: *** [all-recursive] Error 1
make[3]: Leaving directory `/home/jon/amarok-1.4-beta3c/amarok/src'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/home/jon/amarok-1.4-beta3c/amarok'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/jon/amarok-1.4-beta3c'
make: *** [all] Error 2

```

Could someone help?

Thanks.

---

### Post by mjm115 on 2006-04-26
You don't have to build it from source.  Just add the following lines to your sources.list:

> 
deb [http://kubuntu.org/packages/amarok-latest](http://kubuntu.org/packages/amarok-latest) breezy main
deb-src [http://kubuntu.org/packages/amarok-latest](http://kubuntu.org/packages/amarok-latest) breezy main


Then you can:

> 
sudo apt-get update
sudo apt-get install amarok


---

### Post by Ramses de Norre on 2006-04-26
The breezy repo disappeared from that url.

---

### Post by mjm115 on 2006-04-26
You're right.  Try:

> 
deb [http://kubuntu.org/packages/amarok](http://kubuntu.org/packages/amarok)**<version that you want>** breezy main
deb-src [http://kubuntu.org/packages/amarok](http://kubuntu.org/packages/amarok)**<version that you want>**breezy main


---

### Post by toran on 2006-04-26
so would the lines be something like this if I wanted 1.4 beta 3?

deb [http://kubuntu.org/packages/amarok-1.4beta3](http://kubuntu.org/packages/amarok-1.4beta3) breezy main
deb-src [http://kubuntu.org/packages/amarok-1.4beta3](http://kubuntu.org/packages/amarok-1.4beta3) breezy main

I tried those lines and apt-get update failed

---

### Post by Ramses de Norre on 2006-04-26
Ignore this ;)

---

### Post by Ramses de Norre on 2006-04-26
[http://kubuntu.org/packages/]("http://kubuntu.org/packages/")
look there to see the possibilities.

---

### Post by mjm115 on 2006-04-26
[QUOTE=toran]so would the lines be something like this if I wanted 1.4 beta 3?

deb [http://kubuntu.org/packages/amarok-1.4beta3](http://kubuntu.org/packages/amarok-1.4beta3) breezy main
deb-src [http://kubuntu.org/packages/amarok-1.4beta3](http://kubuntu.org/packages/amarok-1.4beta3) breezy main

I tried those lines and apt-get update failed[/QUOTE]

It looks like the beta packages for amarok are only available for dapper.  The lateset stable version, 1.3.8, is the last that's available for breezy.  Try:

> 
deb [http://kubuntu.org/packages/amarok-1.3.8](http://kubuntu.org/packages/amarok-1.3.8) breezy main
deb-src [http://kubuntu.org/packages/amarok-1.3.8](http://kubuntu.org/packages/amarok-1.3.8) breezy main


---

### Post by adamkane on 2006-04-26
amaroK 1.4.0 beta is now available for Breezy:
 [http://amarok.kde.org/amarokwiki/index.php/1.4_for_Kubuntu_5.10]("http://amarok.kde.org/amarokwiki/index.php/1.4_for_Kubuntu_5.10")
 
 You can add the czessi repository by adding this line to your sources.list:
 
 > 
 deb [http://archive.czessi.net/]("http://archive.czessi.net/") breezy stable stable-updates testing testing-updates
  
 Add the czessi gpg key:
 
 ```

 cd ~/Desktop 
 wget http://www.czessi.net/kczessi.gpg 
 sudo apt-key add kczessi.gpg 
 sudo apt-get update
 
``` 
 Remove libvisual before you install this version of amarok. Otherwise you'll end up with dependency problems:
 
 ```

 sudo apt-get remove libvisual
 
```

---

### Post by toran on 2006-04-26
Thanks, you're the best! That worked well.

---

### Post by Protostar on 2006-05-06
I did all of that, and it says 1.3.9, instead of 1.4.0

---

### Post by shadow07 on 2006-05-17
@Protostar:

I did the following:

sudo apt-get remove libvisual
sudo echo "deb [http://archive.czessi.net/ubuntu](http://archive.czessi.net/ubuntu) breezy main universe preview" >> /etc/apt/sources.list
wget [http://www.czessi.net/kczessi.gpg](http://www.czessi.net/kczessi.gpg)
sudo apt-key add kczessi.gpg && rm kczessi.gpg
sudo apt-get update
sudo apt-get install amarok amarok-xine 

Did you follow similar steps?  When you search for the installed packages for Amarok, what version is listed?  Also, the shortcut you are using, is it pointing to /usr/bin/amarok?  Or, another location?

---

### Post by jonnyfive on 2006-05-19
I was having the same problem as Protostar where it updated to 1.39 and then I did this: 

[QUOTE=shadow07]@Protostar:

I did the following:

sudo apt-get remove libvisual
sudo echo "deb [http://archive.czessi.net/ubuntu](http://archive.czessi.net/ubuntu) breezy main universe preview" >> /etc/apt/sources.list
wget [http://www.czessi.net/kczessi.gpg](http://www.czessi.net/kczessi.gpg)
sudo apt-key add kczessi.gpg && rm kczessi.gpg
sudo apt-get update
sudo apt-get install amarok amarok-xine 

Did you follow similar steps?  When you search for the installed packages for Amarok, what version is listed?  Also, the shortcut you are using, is it pointing to /usr/bin/amarok?  Or, another location?[/QUOTE]

and it worked like a charm!
Thanks!

---

### Post by Gomek on 2006-05-20
> sudo apt-get remove libvisual
sudo echo "deb [http://archive.czessi.net/ubuntu](http://archive.czessi.net/ubuntu) breezy main universe preview" >> /etc/apt/sources.list
wget [http://www.czessi.net/kczessi.gpg](http://www.czessi.net/kczessi.gpg)
sudo apt-key add kczessi.gpg && rm kczessi.gpg
sudo apt-get update
sudo apt-get install amarok amarok-xine
Awesome.  I was under the impression I'd have to upgrade to Dapper to get 1.4 until I tried this.

---

