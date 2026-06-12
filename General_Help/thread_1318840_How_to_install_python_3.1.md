---
title: "How to install python 3.1?"
date: 2009-11-07
forum: General Help
---

### Post by mahela007 on 2009-11-07
I tried looking in kpackage kit but all it shows is the old 2.x version. I went to the python website and found a "source tarball package" and am going to download it. However, i don't even know what a source tarball package is so I'd like to know how to install python 3.1 after downloading this package... Better yet, I'd like to know how to install python using kpackagekit...
By the way, why doesn't kpackage kit show python 3.1? I tried searching for firefox but even firefox 3.5 is not shown.

---

### Post by amingv on 2009-11-07
What version of Kubuntu are you using? python3.1 has been available for me since jaunty (maybe even before that, don't quite remember).
FF was also released some time ago.

---

### Post by lovemylady on 2009-11-07
> **mahela007 said:**
> I tried looking in kpackage kit but all it shows is the old 2.x version. I went to the python website and found a "source tarball package" and am going to download it. However, i don't even know what a source tarball package is so I'd like to know how to install python 3.1 after downloading this package... Better yet, I'd like to know how to install python using kpackagekit...
By the way, why doesn't kpackage kit show python 3.1? I tried searching for firefox but even firefox 3.5 is not shown.


Well for firefox there is an installer just click on it system/internet/firefoxinstall and yea firefox 3.5 will be installed  :p

In the python thing I can't help you cause I dunno that too :p

---

### Post by mahela007 on 2009-11-07
I'm using kubuntu 9.04

---

### Post by amingv on 2009-11-07
> **mahela007 said:**
> I'm using kubuntu 9.04

Oh, wait. My mistake.
Python 3.0 is what was available for jaunty (9.04).

Look in kpackagekit for a package called "python3.0".

For 3.1 you'd need to upgrade to karmic (9.10)

---

### Post by mahela007 on 2009-11-08
How can I install python 3.1 on kubuntu 9.04?

---

### Post by amingv on 2009-11-08
You can try downloading it and installing manually. Download it from here instead of compiling it from source (link for downloading at the bottom):
[http://packages.ubuntu.com/karmic/python3.1](http://packages.ubuntu.com/karmic/python3.1)

Any dependencies, you can get there, too.

I can't be 100% positive it will work but really can't see why it wouldn't, so I guess it's worth a shot.

---

### Post by mahela007 on 2009-11-08
I'm not really sure what I should do after visiting that link.. What are the packages I should download? and what should I do after I download them?

---

### Post by amingv on 2009-11-08
> **mahela007 said:**
> I'm not really sure what I should do after visiting that link.. What are the packages I should download? and what should I do after I download them?

Here are direct download links (you can access them at the bottom of the page where it says "Download python3.1"), just click on amd64 or i386 depending on the architecture you installed (if you're unsure, it's likely to be i386).

i386:
[http://mirrors.kernel.org/ubuntu/pool/universe/p/python3.1/python3.1_3.1.1-0ubuntu4_i386.deb](http://mirrors.kernel.org/ubuntu/pool/universe/p/python3.1/python3.1_3.1.1-0ubuntu4_i386.deb)

amd64:
[http://mirrors.kernel.org/ubuntu/pool/universe/p/python3.1/python3.1_3.1.1-0ubuntu4_amd64.deb](http://mirrors.kernel.org/ubuntu/pool/universe/p/python3.1/python3.1_3.1.1-0ubuntu4_amd64.deb)

That will give you a .deb file, open it to start the installation process.

Post any errors you may encounter.

---

### Post by mahela007 on 2009-11-10
Thanks... I'll check this out and post back as soon as i can.

---

### Post by mahela007 on 2009-11-10
no luck...  double clicking that deb file just raises an error.. 
I don't get any message.. it just says "an error occured".
I tried installing with the Gdebi package installer. It said "dependency not satisfied."..

---

### Post by amingv on 2009-11-10
You have unmet dependencies. There's a list of all needed dependencies in the first page I gave you ([http://packages.ubuntu.com/karmic/python3.1]("http://packages.ubuntu.com/karmic/python3.1"), all the packages with a red dot next to it.) You can get all of those through the package manager in jaunty except for these:

python3.1-minimal
i386: [http://mirrors.kernel.org/ubuntu/pool/universe/p/python3.1/python3.1-minimal_3.1.1-0ubuntu4_i386.deb](http://mirrors.kernel.org/ubuntu/pool/universe/p/python3.1/python3.1-minimal_3.1.1-0ubuntu4_i386.deb)
amd64: [http://mirrors.kernel.org/ubuntu/pool/universe/p/python3.1/python3.1-minimal_3.1.1-0ubuntu4_amd64.deb](http://mirrors.kernel.org/ubuntu/pool/universe/p/python3.1/python3.1-minimal_3.1.1-0ubuntu4_amd64.deb)

libreadline6
i386: [http://mirrors.kernel.org/ubuntu/pool/main/r/readline6/libreadline6_6.0-5_i386.deb](http://mirrors.kernel.org/ubuntu/pool/main/r/readline6/libreadline6_6.0-5_i386.deb)
amd64: [http://mirrors.kernel.org/ubuntu/pool/main/r/readline6/libreadline6_6.0-5_amd64.deb](http://mirrors.kernel.org/ubuntu/pool/main/r/readline6/libreadline6_6.0-5_amd64.deb)

Needed by other packages:

zlib1g:
i386: [http://mirrors.kernel.org/ubuntu/pool/main/z/zlib/zlib1g_1.2.3.3.dfsg-13ubuntu3_i386.deb](http://mirrors.kernel.org/ubuntu/pool/main/z/zlib/zlib1g_1.2.3.3.dfsg-13ubuntu3_i386.deb)
amd64: [http://mirrors.kernel.org/ubuntu/pool/main/z/zlib/zlib1g_1.2.3.3.dfsg-13ubuntu3_amd64.deb](http://mirrors.kernel.org/ubuntu/pool/main/z/zlib/zlib1g_1.2.3.3.dfsg-13ubuntu3_amd64.deb)

libssl0.9.8
i386: [http://mirrors.kernel.org/ubuntu/pool/main/o/openssl/libssl0.9.8_0.9.8g-16ubuntu3_i386.deb](http://mirrors.kernel.org/ubuntu/pool/main/o/openssl/libssl0.9.8_0.9.8g-16ubuntu3_i386.deb)
amd64: [http://mirrors.kernel.org/ubuntu/pool/main/o/openssl/libssl0.9.8_0.9.8g-16ubuntu3_amd64.deb](http://mirrors.kernel.org/ubuntu/pool/main/o/openssl/libssl0.9.8_0.9.8g-16ubuntu3_amd64.deb)

Although you should have no problems after meeting all dependencies, I think it's worth to mention that sticking with python3.0 (available in jaunty) may be the easiest and less troublesome solution, after all 3.0 is the mayor revision.

---

### Post by mahela007 on 2009-11-14
Thanks for your help.
I'm going to try my best to install python 3.1 because as stated in the python documentation 3.0 is not being developed.. it's 3.1 that everyone is concentrating on. (right)?

---

