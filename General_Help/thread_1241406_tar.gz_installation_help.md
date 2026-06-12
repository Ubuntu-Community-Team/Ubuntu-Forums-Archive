---
title: "tar.gz installation help"
date: 2009-08-15
forum: General Help
---

### Post by Enigmapond on 2009-08-15
I am. new to Ubuntu and so very thankful to be rid of Micro-Gates. I have read previous posts regarding the installation of programs and here's my problem:

I'm trying to install BitWise IM. I downloaded the tarball and have extracted it to a directory. I ' cd ' to that directory and try to ./configure but that's where it ends. States no such file found. What I need is a step-by-step to installing this program. I have checkinstall...and I think have all needed to compile but I have no clue as to how to proceed. This is the only thing holding me up on the wonderful OS. If someone would be so kind, I will be grateful.


Thank you in advance!

Cheers!:confused:

---

### Post by coldReactive on 2009-08-15
Thight might help:

[https://answers.launchpad.net/ubuntu/+question/61293](https://answers.launchpad.net/ubuntu/+question/61293)

---

### Post by lensman3 on 2009-08-15
Was it maybe ./.configure (dot-shash-dot-configure)?


Sometimes the configure is .configure (with the leading dot so that it is hidden).

---

### Post by oldos2er on 2009-08-16
According to readme.txt, it's already compiled. Run ./BitWise

---

### Post by Enigmapond on 2009-08-16
I read that as well and noticed no configure file. When I did as you instructed. this was the error I received:

./BitWise: error while loading shared libraries: libexpat.so.0: cannot open shared object file: No such file or directory
 Does this mean this mean  libexpat.so.0 is a dependency?

---

### Post by mrbiggbrain on 2009-08-16
> **Enigmapond said:**
> I read that as well and noticed no configure file. When I did as you instructed. this was the error I received:

./BitWise: error while loading shared libraries: libexpat.so.0: cannot open shared object file: No such file or directory
 Does this mean this mean  libexpat.so.0 is a dependency?

yes, its a dependancy :-) you'll need to get that and all the other files it requires.

---

### Post by Enigmapond on 2009-08-16
> **mrbiggbrain said:**
> yes, its a dependancy :-) you'll need to get that and all the other files it requires.

This would be easy to fix however, in searching both my PC and Ubuntu, there is no "libexpat.so.0" and I have "libexpat.so.1"...I'm at a loss. I also read where "Wink" was having the same problem and people were symbolically linking the one to the other with mixed results.

If there is a kind soul who would install BitWise IM and tell me what they did, maybe that would help....I have installed other programs from tar.gz and all went well.

---

### Post by oldos2er on 2009-08-16
You can search for libexpat in Synaptic, and install it from there.

---

### Post by Enigmapond on 2009-08-20
I want to thank all who responded to my request.

I fixed the problem with Bitwise IM. It was easier than I thought it would be and less problems than installing the Linux version. I installed the Windows version through Wine. I forwarded port 4137 on my router and made the proper rules in the firewall. It has a few glitches on the platform level, i.e. some buttons and icons fail to appear but it works great and the Direct Connect feature is working as well. If anyone else needs help with this application, feel free to contact me.

Again, Thank you all so much for your help. I love this OS and will never go back to Microsoft

Cheers!!

---

