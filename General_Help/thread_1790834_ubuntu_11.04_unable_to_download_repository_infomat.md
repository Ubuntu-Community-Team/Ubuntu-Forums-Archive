---
title: "ubuntu 11.04 unable to download repository infomation"
date: 2011-06-25
forum: General Help
---

### Post by deep07004 on 2011-06-25
I have just installed ubuntu 11.04. Package manager unable to download repo information
while in the same network ubuntu 10.04 is working fine .

Can anybody help ?

---

### Post by Yellow Pasque on 2011-06-25
What is the output of:
```
sudo apt-get update
```
Also, do other net apps connect? Do you use a proxy?

---

### Post by deep07004 on 2011-06-25
Error output is ...
***********

Ign [http://archive.ubuntu.com]("http://archive.ubuntu.com/") natty InRelease                                  
Ign [http://extras.ubuntu.com]("http://extras.ubuntu.com/") natty InRelease                                   
Err [http://extras.ubuntu.com]("http://extras.ubuntu.com/") natty Release.gpg       
  Connection failed
Ign [http://archive.ubuntu.com]("http://archive.ubuntu.com/") natty-updates InRelease
Ign [http://archive.ubuntu.com]("http://archive.ubuntu.com/") natty-security InRelease
Ign [http://extras.ubuntu.com]("http://extras.ubuntu.com/") natty Release          
Err [http://archive.ubuntu.com]("http://archive.ubuntu.com/") natty Release.gpg      
  Connection failed [IP: 91.189.92.169 80]
Err [http://archive.ubuntu.com]("http://archive.ubuntu.com/") natty-updates Release.gpg
  Connection failed [IP: 91.189.92.171 80]
Err [http://archive.ubuntu.com]("http://archive.ubuntu.com/") natty-security Release.gpg
  Connection failed [IP: 91.189.88.31 80]
Ign [http://extras.ubuntu.com]("http://extras.ubuntu.com/") natty/main TranslationIndex
Ign [http://archive.ubuntu.com]("http://archive.ubuntu.com/") natty Release          
Ign [http://archive.ubuntu.com]("http://archive.ubuntu.com/") natty-updates Release  
Ign [http://archive.ubuntu.com]("http://archive.ubuntu.com/") natty-security Release
Ign [http://archive.ubuntu.com]("http://archive.ubuntu.com/") natty/main TranslationIndex                      
Ign [http://archive.ubuntu.com]("http://archive.ubuntu.com/") natty/multiverse TranslationIndex                
Err [http://extras.ubuntu.com]("http://extras.ubuntu.com/") natty/main Sources     
  Connection failed
Err [http://extras.ubuntu.com]("http://extras.ubuntu.com/") natty/main i386 Packages
  Connection failed
Ign [http://archive.ubuntu.com]("http://archive.ubuntu.com/") natty/restricted TranslationIndex
Ign [http://archive.ubuntu.com]("http://archive.ubuntu.com/") natty/universe TranslationIndex
Err [http://extras.ubuntu.com]("http://extras.ubuntu.com/") natty/main Translation-en_IN                      
  Connection failed
Err [http://extras.ubuntu.com]("http://extras.ubuntu.com/") natty/main Translation-en                         
  Connection failed
Ign [http://archive.ubuntu.com]("http://archive.ubuntu.com/") natty-updates/main TranslationIndex
Ign [http://archive.ubuntu.com]("http://archive.ubuntu.com/") natty-updates/multiverse TranslationIndex
Ign [http://archive.ubuntu.com]("http://archive.ubuntu.com/") natty-updates/restricted TranslationIndex
Ign [http://archive.ubuntu.com]("http://archive.ubuntu.com/") natty-updates/universe TranslationIndex
Ign [http://archive.ubuntu.com]("http://archive.ubuntu.com/") natty-security/main TranslationIndex
Ign [http://archive.ubuntu.com]("http://archive.ubuntu.com/") natty-security/multiverse TranslationIndex
Ign [http://archive.ubuntu.com]("http://archive.ubuntu.com/") natty-security/restricted TranslationIndex
Ign [http://archive.ubuntu.com]("http://archive.ubuntu.com/") naErr [http://archive.ubuntu.com]("http://archive.ubuntu.com/") natty/main Sources      
  Connection failed [IP: 91.189.88.31 80]
Err [http://archive.ubuntu.com]("http://archive.ubuntu.com/") natty/restricted Sources
  Connection failed [IP: 91.189.88.45 80]
Err [http://archive.ubuntu.com]("http://archive.ubuntu.com/") natty/universe Sources
  Connection failed [IP: 91.189.92.169 80]
Err [http://archive.ubuntu.com]("http://archive.ubuntu.com/") natty/multiverse Sources
  Connection failed [IP: 91.189.92.171 80]
Err [http://archive.ubuntu.com]("http://archive.ubuntu.com/") natty/main i386 Packages
  Connection failed [IP: 91.189.88.31 80]
Err [http://archive.ubuntu.com]("http://archive.ubuntu.com/") natty/restricted i386 Packages
  Connection failed [IP: 91.189.88.45 80]
Err [http://archive.ubuntu.com]("http://archive.ubuntu.com/") natty/universe i386 Packages
  Connection failed [IP: 91.189.92.169 80]
Err [http://archive.ubuntu.com]("http://archive.ubuntu.com/") natty/multiverse i386 Packages
  Connection failed [IP: 91.189.92.171 80]
Err [http://archive.ubuntu.com]("http://archive.ubuntu.com/") natty-updates/main Sources
  Connection failed [IP: 91.189.88.31 80]
Err [http://archive.ubuntu.com]("http://archive.ubuntu.com/") natty-updates/restricted Sources
  Connection failed [IP: 91.189.88.45 80]
Err [http://archive.ubuntu.com]("http://archive.ubuntu.com/") natty-updates/universe Sources
  Connection failed [IP: 91.189.92.169 80]
Err [http://archive.ubuntu.com]("http://archive.ubuntu.com/") natty-updates/multiverse Sources
  Connection failed [IP: 91.189.92.171 80]
Err [http://archive.ubuntu.com]("http://archive.ubuntu.com/") natty-updates/main i386 Packages
  Connection failed [IP: 91.189.88.31 80]
Err [http://archive.ubuntu.com]("http://archive.ubuntu.com/") natty-updates/restricted i386 Packages
  Connection failed [IP: 91.189.88.45 80]
Err [http://archive.ubuntu.com]("http://archive.ubuntu.com/") natty-updates/universe i386 Packages
  Connection failed [IP: 91.189.92.169 80]
Err [http://archive.ubuntu.com]("http://archive.ubuntu.com/") natty-updates/multiverse i386 Packages
  Connection failed [IP: 91.189.92.171 80]
Err [http://archive.ubuntu.com]("http://archive.ubuntu.com/") natty-security/main Sources
  Connection failed [IP: 91.189.88.31 80]
Err [http://archive.ubuntu.com]("http://archive.ubuntu.com/") natty-security/restricted Sources
  Connection failed [IP: 91.189.88.45 80]
Err [http://archive.ubuntu.com]("http://archive.ubuntu.com/") natty-security/universe Sources
  Connection failed [IP: 91.189.92.169 80]
Err [http://archive.ubuntu.com]("http://archive.ubuntu.com/") natty-security/multiverse Sources
  Connection failed [IP: 91.189.92.171 80]
Err [http://archive.ubuntu.com]("http://archive.ubuntu.com/") natty-security/main i386 Packages
  Connection failed [IP: 91.189.88.31 80]
Err [http://archive.ubuntu.com]("http://archive.ubuntu.com/") natty-security/restricted i386 Packages
  Connection failed [IP: 91.189.88.45 80]
Err [http://archive.ubuntu.com]("http://archive.ubuntu.com/") natty-security/universe i386 Packages
  Connection failed [IP: 91.189.92.169 80]
Err [http://archive.ubuntu.com]("http://archive.ubuntu.com/") natty-security/multiverse i386 Packages
  Connection failed [IP: 91.189.92.171 80]
Err [http://archive.ubuntu.com]("http://archive.ubuntu.com/") natty/main Translation-en_IN
  Connection failed [IP: 91.189.88.31 80]
Err [http://archive.ubuntu.com]("http://archive.ubuntu.com/") natty/main Translation-en
  Connection failed [IP: 91.189.88.45 80]
Err [http://archive.ubuntu.com]("http://archive.ubuntu.com/") natty/multiverse Translation-en_IN
  Connection failed [IP: 91.189.92.169 80]
Err [http://archive.ubuntu.com]("http://archive.ubuntu.com/") natty/multiverse Translation-en
  Connection failed [IP: 91.189.92.171 80]
Err [http://archive.ubuntu.com]("http://archive.ubuntu.com/") natty/restricted Translation-en_IN
  Connection failed [IP: 91.189.88.31 80]
Err [http://archive.ubuntu.com]("http://archive.ubuntu.com/") natty/restricted Translation-en
  Connection failed [IP: 91.189.88.45 80]
Err [http://archive.ubuntu.com]("http://archive.ubuntu.com/") natty/universe Translation-en_IN
  Connection failed [IP: 91.189.92.169 80]
Err [http://archive.ubuntu.com]("http://archive.ubuntu.com/") natty/universe Translation-en
  Connection failed [IP: 91.189.92.171 80]
Err [http://archive.ubuntu.com]("http://archive.ubuntu.com/") natty-updates/main Translation-en_IN
  Connection failed [IP: 91.189.88.31 80]
Err [http://archive.ubuntu.com]("http://archive.ubuntu.com/") natty-updates/main Translation-en
  Connection failed [IP: 91.189.88.45 80]
Err [http://archive.ubuntu.com]("http://archive.ubuntu.com/") natty-updates/multiverse Translation-en_IN
  Connection failed [IP: 91.189.92.169 80]
Err [http://archive.ubuntu.com]("http://archive.ubuntu.com/") natty-updates/multiverse Translation-en
  Connection failed [IP: 91.189.92.171 80]
Err [http://archive.ubuntu.com]("http://archive.ubuntu.com/") natty-updates/restricted Translation-en_IN
  Connection failed [IP: 91.189.88.31 80]
Err [http://archive.ubuntu.com]("http://archive.ubuntu.com/") natty-updates/restricted Translation-en
  Connection failed [IP: 91.189.88.45 80]
Err [http://archive.ubuntu.com]("http://archive.ubuntu.com/") natty-updates/universe Translation-en_IN
  Connection failed [IP: 91.189.92.169 80]
Err [http://archive.ubuntu.com]("http://archive.ubuntu.com/") natty-updates/universe Translation-en
  Connection failed [IP: 91.189.92.171 80]
Err [http://archive.ubuntu.com]("http://archive.ubuntu.com/") natty-security/main Translation-en_IN
  Connection failed [IP: 91.189.88.31 80]
Err [http://archive.ubuntu.com]("http://archive.ubuntu.com/") natty-security/main Translation-en
  Connection failed [IP: 91.189.88.45 80]
Err [http://archive.ubuntu.com]("http://archive.ubuntu.com/") natty-security/multiverse Translation-en_IN
  Connection failed [IP: 91.189.92.169 80]
Err [http://archive.ubuntu.com]("http://archive.ubuntu.com/") natty-security/multiverse Translation-en
  Connection failed [IP: 91.189.92.171 80]
Err [http://archive.ubuntu.com]("http://archive.ubuntu.com/") natty-security/restricted Translation-en_IN
  Connection failed [IP: 91.189.88.31 80]
Err [http://archive.ubuntu.com]("http://archive.ubuntu.com/") natty-security/restricted Translation-en
  Connection failed [IP: 91.189.88.45 80]
Err [http://archive.ubuntu.com]("http://archive.ubuntu.com/") natty-security/universe Translation-en_IN
  Connection failed [IP: 91.189.92.169 80]
Err [http://archive.ubuntu.com]("http://archive.ubuntu.com/") natty-security/universe Translation-en
  Connection failed [IP: 91.189.92.171 80]
W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dis...ty/Release.gpg]("http://archive.ubuntu.com/ubuntu/dists/natty/Release.gpg")  Connection failed [IP: 91.189.92.169 80]

W: Failed to fetch [http://extras.ubuntu.com/ubuntu/dists/natty/Release.gpg](http://extras.ubuntu.com/ubuntu/dists/natty/Release.gpg)  Connection failed

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dis...es/Release.gpg]("http://archive.ubuntu.com/ubuntu/dists/natty-updates/Release.gpg")  Connection failed [IP: 91.189.92.171 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dis...ty/Release.gpg]("http://archive.ubuntu.com/ubuntu/dists/natty-security/Release.gpg")  Connection failed [IP: 91.189.88.31 80]

W: Failed to fetch [http://extras.ubuntu.com/ubuntu/dist...source/Sources]("http://extras.ubuntu.com/ubuntu/dists/natty/main/source/Sources")  Connection failed

W: Failed to fetch [http://extras.ubuntu.com/ubuntu/dist...-i386/Packages]("http://extras.ubuntu.com/ubuntu/dists/natty/main/binary-i386/Packages")  Connection failed

W: Failed to fetch [http://extras.ubuntu.com/ubuntu/dist...nslation-en_IN]("http://extras.ubuntu.com/ubuntu/dists/natty/main/i18n/Translation-en_IN")  Connection failed

W: Failed to fetch [http://extras.ubuntu.com/ubuntu/dist...Translation-en]("http://extras.ubuntu.com/ubuntu/dists/natty/main/i18n/Translation-en")  Connection failed

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dis...source/Sources]("http://archive.ubuntu.com/ubuntu/dists/natty/main/source/Sources")  Connection failed [IP: 91.189.88.31 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dis...source/Sources]("http://archive.ubuntu.com/ubuntu/dists/natty/restricted/source/Sources")  Connection failed [IP: 91.189.88.45 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dis...source/Sources]("http://archive.ubuntu.com/ubuntu/dists/natty/universe/source/Sources")  Connection failed [IP: 91.189.92.169 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dis...source/Sources]("http://archive.ubuntu.com/ubuntu/dists/natty/multiverse/source/Sources")  Connection failed [IP: 91.189.92.171 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dis...-i386/Packages]("http://archive.ubuntu.com/ubuntu/dists/natty/main/binary-i386/Packages")  Connection failed [IP: 91.189.88.31 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dis...-i386/Packages]("http://archive.ubuntu.com/ubuntu/dists/natty/restricted/binary-i386/Packages")  Connection failed [IP: 91.189.88.45 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dis...-i386/Packages]("http://archive.ubuntu.com/ubuntu/dists/natty/universe/binary-i386/Packages")  Connection failed [IP: 91.189.92.169 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dis...-i386/Packages]("http://archive.ubuntu.com/ubuntu/dists/natty/multiverse/binary-i386/Packages")  Connection failed [IP: 91.189.92.171 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dis...source/Sources]("http://archive.ubuntu.com/ubuntu/dists/natty-updates/main/source/Sources")  Connection failed [IP: 91.189.88.31 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dis...source/Sources]("http://archive.ubuntu.com/ubuntu/dists/natty-updates/restricted/source/Sources")  Connection failed [IP: 91.189.88.45 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dis...source/Sources]("http://archive.ubuntu.com/ubuntu/dists/natty-updates/universe/source/Sources")  Connection failed [IP: 91.189.92.169 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dis...source/Sources]("http://archive.ubuntu.com/ubuntu/dists/natty-updates/multiverse/source/Sources")  Connection failed [IP: 91.189.92.171 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dis...-i386/Packages]("http://archive.ubuntu.com/ubuntu/dists/natty-updates/main/binary-i386/Packages")  Connection failed [IP: 91.189.88.31 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dis...-i386/Packages]("http://archive.ubuntu.com/ubuntu/dists/natty-updates/restricted/binary-i386/Packages")  Connection failed [IP: 91.189.88.45 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dis...-i386/Packages]("http://archive.ubuntu.com/ubuntu/dists/natty-updates/universe/binary-i386/Packages")  Connection failed [IP: 91.189.92.169 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dis...-i386/Packages]("http://archive.ubuntu.com/ubuntu/dists/natty-updates/multiverse/binary-i386/Packages")  Connection failed [IP: 91.189.92.171 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dis...source/Sources]("http://archive.ubuntu.com/ubuntu/dists/natty-security/main/source/Sources")  Connection failed [IP: 91.189.88.31 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dis...source/Sources]("http://archive.ubuntu.com/ubuntu/dists/natty-security/restricted/source/Sources")  Connection failed [IP: 91.189.88.45 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dis...source/Sources]("http://archive.ubuntu.com/ubuntu/dists/natty-security/universe/source/Sources")  Connection failed [IP: 91.189.92.169 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dis...source/Sources]("http://archive.ubuntu.com/ubuntu/dists/natty-security/multiverse/source/Sources")  Connection failed [IP: 91.189.92.171 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dis...-i386/Packages]("http://archive.ubuntu.com/ubuntu/dists/natty-security/main/binary-i386/Packages")  Connection failed [IP: 91.189.88.31 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dis...-i386/Packages]("http://archive.ubuntu.com/ubuntu/dists/natty-security/restricted/binary-i386/Packages")  Connection failed [IP: 91.189.88.45 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dis...-i386/Packages]("http://archive.ubuntu.com/ubuntu/dists/natty-security/universe/binary-i386/Packages")  Connection failed [IP: 91.189.92.169 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dis...-i386/Packages]("http://archive.ubuntu.com/ubuntu/dists/natty-security/multiverse/binary-i386/Packages")  Connection failed [IP: 91.189.92.171 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dis...nslation-en_IN]("http://archive.ubuntu.com/ubuntu/dists/natty/main/i18n/Translation-en_IN")  Connection failed [IP: 91.189.88.31 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dis...Translation-en]("http://archive.ubuntu.com/ubuntu/dists/natty/main/i18n/Translation-en")  Connection failed [IP: 91.189.88.45 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dis...nslation-en_IN]("http://archive.ubuntu.com/ubuntu/dists/natty/multiverse/i18n/Translation-en_IN")  Connection failed [IP: 91.189.92.169 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dis...Translation-en]("http://archive.ubuntu.com/ubuntu/dists/natty/multiverse/i18n/Translation-en")  Connection failed [IP: 91.189.92.171 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dis...nslation-en_IN]("http://archive.ubuntu.com/ubuntu/dists/natty/restricted/i18n/Translation-en_IN")  Connection failed [IP: 91.189.88.31 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dis...Translation-en]("http://archive.ubuntu.com/ubuntu/dists/natty/restricted/i18n/Translation-en")  Connection failed [IP: 91.189.88.45 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dis...nslation-en_IN]("http://archive.ubuntu.com/ubuntu/dists/natty/universe/i18n/Translation-en_IN")  Connection failed [IP: 91.189.92.169 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dis...Translation-en]("http://archive.ubuntu.com/ubuntu/dists/natty/universe/i18n/Translation-en")  Connection failed [IP: 91.189.92.171 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dis...nslation-en_IN]("http://archive.ubuntu.com/ubuntu/dists/natty-updates/main/i18n/Translation-en_IN")  Connection failed [IP: 91.189.88.31 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dis...Translation-en]("http://archive.ubuntu.com/ubuntu/dists/natty-updates/main/i18n/Translation-en")  Connection failed [IP: 91.189.88.45 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dis...nslation-en_IN]("http://archive.ubuntu.com/ubuntu/dists/natty-updates/multiverse/i18n/Translation-en_IN")  Connection failed [IP: 91.189.92.169 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dis...Translation-en]("http://archive.ubuntu.com/ubuntu/dists/natty-updates/multiverse/i18n/Translation-en")  Connection failed [IP: 91.189.92.171 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dis...nslation-en_IN]("http://archive.ubuntu.com/ubuntu/dists/natty-updates/restricted/i18n/Translation-en_IN")  Connection failed [IP: 91.189.88.31 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dis...Translation-en]("http://archive.ubuntu.com/ubuntu/dists/natty-updates/restricted/i18n/Translation-en")  Connection failed [IP: 91.189.88.45 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dis...nslation-en_IN]("http://archive.ubuntu.com/ubuntu/dists/natty-updates/universe/i18n/Translation-en_IN")  Connection failed [IP: 91.189.92.169 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dis...Translation-en]("http://archive.ubuntu.com/ubuntu/dists/natty-updates/universe/i18n/Translation-en")  Connection failed [IP: 91.189.92.171 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dis...nslation-en_IN]("http://archive.ubuntu.com/ubuntu/dists/natty-security/main/i18n/Translation-en_IN")  Connection failed [IP: 91.189.88.31 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dis...Translation-en]("http://archive.ubuntu.com/ubuntu/dists/natty-security/main/i18n/Translation-en")  Connection failed [IP: 91.189.88.45 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dis...nslation-en_IN]("http://archive.ubuntu.com/ubuntu/dists/natty-security/multiverse/i18n/Translation-en_IN")  Connection failed [IP: 91.189.92.169 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dis...Translation-en]("http://archive.ubuntu.com/ubuntu/dists/natty-security/multiverse/i18n/Translation-en")  Connection failed [IP: 91.189.92.171 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dis...nslation-en_IN]("http://archive.ubuntu.com/ubuntu/dists/natty-security/restricted/i18n/Translation-en_IN")  Connection failed [IP: 91.189.88.31 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dis...Translation-en]("http://archive.ubuntu.com/ubuntu/dists/natty-security/restricted/i18n/Translation-en")  Connection failed [IP: 91.189.88.45 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dis...nslation-en_IN]("http://archive.ubuntu.com/ubuntu/dists/natty-security/universe/i18n/Translation-en_IN")  Connection failed [IP: 91.189.92.169 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dis...Translation-en]("http://archive.ubuntu.com/ubuntu/dists/natty-security/universe/i18n/Translation-en")  Connection failed [IP: 91.189.92.171 80]

E: Some index files failed to download. They have been ignored, or old ones used instead.

---

### Post by BrokenKingpin on 2011-06-25
I am getting the same things :(.

---

### Post by deep07004 on 2011-06-26
any solution ....................
it's really sucking  ..............

---

### Post by philinux on 2011-06-26
> **deep07004 said:**
> any solution ....................
it's really sucking  ..............

Change to a different server in software sources.

---

### Post by deep07004 on 2011-06-26
already tried  
doesn't work
same output

---

### Post by gandaran on 2011-06-26
maybe your local servers are down, you can either wait another day then try again or change your local country server in software sources to the main ubuntu server.

---

### Post by deep07004 on 2011-06-26
> **gandaran said:**
> maybe your local servers are down, you can either wait another day then try again or change your local country server in software sources to the main ubuntu server.

I have tried with both local and main server. But results are same

---

### Post by deep07004 on 2011-06-26
hay guys any idea ...........................
I'm literally frustrated ..............................

---

### Post by dFlyer on 2011-06-26
Are you using wifi or are you hardwired to the network? I get that response when my wifi is down.

---

### Post by deep07004 on 2011-06-26
R U guys really online ????????
somebody reply

---

### Post by deep07004 on 2011-06-26
> **dFlyer said:**
> Are you using wifi or are you hardwired to the network? I get that response when my wifi is down.

 no it's lane
Ununtu 10.04 on another machine in the same network is working fine

---

### Post by deep07004 on 2011-06-26
Thanks to all  those who replied in this thread ..
I'm going back to 10.04(LTS)

---

### Post by Wandere on 2011-07-21
When inputting ```
sudo apt-get update
``` I got as a result:
```
Ign http://archive.ubuntu.com jaunty InRelease
Ign http://archive.canonical.com natty InRelease
Ign http://archive.canonical.com maverick InRelease                  
Ign http://us.archive.ubuntu.com natty InRelease                     
Ign http://us.archive.ubuntu.com natty-updates InRelease
Ign http://us.archive.ubuntu.com natty-security InRelease
Ign http://archive.ubuntu.com jaunty Release.gpg
Hit http://archive.canonical.com natty Release.gpg
Hit http://us.archive.ubuntu.com natty Release.gpg
Ign http://archive.ubuntu.com jaunty Release   
Hit http://archive.canonical.com maverick Release.gpg
Hit http://us.archive.ubuntu.com natty-updates Release.gpg
Ign http://archive.ubuntu.com jaunty/universe Sources/DiffIndex      
Hit http://archive.canonical.com natty Release                       
Hit http://us.archive.ubuntu.com natty-security Release.gpg
Ign http://archive.ubuntu.com jaunty/universe i386 Packages/DiffIndex          
Ign http://archive.ubuntu.com jaunty/universe TranslationIndex       
Hit http://us.archive.ubuntu.com natty Release                       
Hit http://archive.canonical.com maverick Release                              
Hit http://us.archive.ubuntu.com natty-updates Release                         
Hit http://archive.canonical.com natty/partner i386 Packages                   
Ign http://archive.canonical.com natty/partner TranslationIndex      
Hit http://us.archive.ubuntu.com natty-security Release              
Hit http://us.archive.ubuntu.com natty/main Sources                            
Hit http://us.archive.ubuntu.com natty/restricted Sources                      
Hit http://us.archive.ubuntu.com natty/universe Sources                        
Hit http://us.archive.ubuntu.com natty/multiverse Sources                      
Hit http://archive.canonical.com maverick/partner Sources                      
Hit http://us.archive.ubuntu.com natty/main i386 Packages            
Hit http://us.archive.ubuntu.com natty/restricted i386 Packages
Hit http://us.archive.ubuntu.com natty/universe i386 Packages        
Hit http://us.archive.ubuntu.com natty/multiverse i386 Packages      
Ign http://us.archive.ubuntu.com natty/main TranslationIndex         
Ign http://us.archive.ubuntu.com natty/multiverse TranslationIndex   
Ign http://us.archive.ubuntu.com natty/restricted TranslationIndex   
Ign http://us.archive.ubuntu.com natty/universe TranslationIndex     
Hit http://us.archive.ubuntu.com natty-updates/main Sources          
Hit http://us.archive.ubuntu.com natty-updates/restricted Sources    
Hit http://us.archive.ubuntu.com natty-updates/universe Sources      
Hit http://us.archive.ubuntu.com natty-updates/multiverse Sources    
Hit http://us.archive.ubuntu.com natty-updates/main i386 Packages    
Hit http://us.archive.ubuntu.com natty-updates/restricted i386 Packages
Hit http://us.archive.ubuntu.com natty-updates/universe i386 Packages
Hit http://us.archive.ubuntu.com natty-updates/multiverse i386 Packages
Ign http://us.archive.ubuntu.com natty-updates/main TranslationIndex 
Ign http://us.archive.ubuntu.com natty-updates/multiverse TranslationIndex
Ign http://us.archive.ubuntu.com natty-updates/restricted TranslationIndex
Ign http://us.archive.ubuntu.com natty-updates/universe TranslationIndex
Hit http://us.archive.ubuntu.com natty-security/main Sources         
Hit http://us.archive.ubuntu.com natty-security/restricted Sources   
Hit http://us.archive.ubuntu.com natty-security/universe Sources     
Hit http://us.archive.ubuntu.com natty-security/multiverse Sources   
Hit http://us.archive.ubuntu.com natty-security/main i386 Packages   
Hit http://us.archive.ubuntu.com natty-security/restricted i386 Packages
Hit http://us.archive.ubuntu.com natty-security/universe i386 Packages
Hit http://us.archive.ubuntu.com natty-security/multiverse i386 Packages
Ign http://us.archive.ubuntu.com natty-security/main TranslationIndex
Ign http://us.archive.ubuntu.com natty-security/multiverse TranslationIndex
Ign http://us.archive.ubuntu.com natty-security/restricted TranslationIndex
Ign http://us.archive.ubuntu.com natty-security/universe TranslationIndex
Ign http://archive.canonical.com natty/partner Translation-en_US     
Ign http://archive.canonical.com natty/partner Translation-en        
Err http://archive.ubuntu.com jaunty/universe Sources
  404  Not Found [IP: 91.189.88.40 80]
Err http://archive.ubuntu.com jaunty/universe i386 Packages
  404  Not Found [IP: 91.189.88.40 80]
Ign http://archive.ubuntu.com jaunty/universe Translation-en_US
Ign http://archive.ubuntu.com jaunty/universe Translation-en
Ign http://us.archive.ubuntu.com natty/main Translation-en_US
Ign http://us.archive.ubuntu.com natty/main Translation-en
Ign http://us.archive.ubuntu.com natty/multiverse Translation-en_US
Ign http://us.archive.ubuntu.com natty/multiverse Translation-en
Ign http://us.archive.ubuntu.com natty/restricted Translation-en_US
Ign http://us.archive.ubuntu.com natty/restricted Translation-en
Ign http://us.archive.ubuntu.com natty/universe Translation-en_US
Ign http://us.archive.ubuntu.com natty/universe Translation-en
Ign http://us.archive.ubuntu.com natty-updates/main Translation-en_US
Ign http://us.archive.ubuntu.com natty-updates/main Translation-en
Ign http://us.archive.ubuntu.com natty-updates/multiverse Translation-en_US
Ign http://us.archive.ubuntu.com natty-updates/multiverse Translation-en
Ign http://us.archive.ubuntu.com natty-updates/restricted Translation-en_US
Ign http://us.archive.ubuntu.com natty-updates/restricted Translation-en
Ign http://us.archive.ubuntu.com natty-updates/universe Translation-en_US
Ign http://us.archive.ubuntu.com natty-updates/universe Translation-en
Ign http://us.archive.ubuntu.com natty-security/main Translation-en_US
Ign http://us.archive.ubuntu.com natty-security/main Translation-en
Ign http://us.archive.ubuntu.com natty-security/multiverse Translation-en_US
Ign http://us.archive.ubuntu.com natty-security/multiverse Translation-en
Ign http://us.archive.ubuntu.com natty-security/restricted Translation-en_US
Ign http://us.archive.ubuntu.com natty-security/restricted Translation-en
Ign http://us.archive.ubuntu.com natty-security/universe Translation-en_US
Ign http://us.archive.ubuntu.com natty-security/universe Translation-en
W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/jaunty/universe/source/Sources  404  Not Found [IP: 91.189.88.40 80]

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/jaunty/universe/binary-i386/Packages  404  Not Found [IP: 91.189.88.40 80]

E: Some index files failed to download. They have been ignored, or old ones used instead.

```I'm using a wi-fi internet connection and I'm sure it's working, as I am able to get other software updates. The problem seems to be limited to the jaunty repository.

---

