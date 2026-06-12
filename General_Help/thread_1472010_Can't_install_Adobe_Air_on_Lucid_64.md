---
title: "Can't install Adobe Air on Lucid 64"
date: 2010-05-04
forum: General Help
---

### Post by wersdaluv on 2010-05-04
For some super weird reason, I can't install Adobe Air on my Lucid 64bit. I'm trying to run AdobeAIRInstaller.bin from [http://get.adobe.com/air/](http://get.adobe.com/air/) .

I know the drill. Allow executing file as program and run the .bin as root. I've been doing that since forever. On another Lucid 64 laptop, that's what I did and it worked.

On this laptop, whenever I run it without Allowing the file to be executed as a program I get (the 1st one without sudo, the 2nd one with sudo)
```
user@laptop:~$ '/home/user/Downloads/AdobeAIRInstaller.bin' 
bash: /home/user/Downloads/AdobeAIRInstaller.bin: Permission denied
user@laptop:~$ sudo '/home/user/Downloads/AdobeAIRInstaller.bin' 
sudo: /home/user/Downloads/AdobeAIRInstaller.bin: command not found

```

If I run it after allowing file to be executed as a program, I get (the 1st one without sudo, the 2nd one with sudo)
```
user@laptop:~$ '/home/user/Downloads/AdobeAIRInstaller.bin' 
bash: /home/user/Downloads/AdobeAIRInstaller.bin: No such file or directory
user@laptop:~$ sudo '/home/user/Downloads/AdobeAIRInstaller.bin' 
sudo: unable to execute /home/user/Downloads/AdobeAIRInstaller.bin: No such file or directory
```

Weird outputs, right?

Any idea why? How do I fix this?

---

### Post by darolu on 2010-05-04
What I usually do is navigate to the directory where my binary file is and run it with ./<binary>; anyways there is no 64-bit version of Adobe Air binaries that I'm aware of, this is what I found, I suggest you to follow the instructions:

[http://kb2.adobe.com/cps/408/kb408084.html](http://kb2.adobe.com/cps/408/kb408084.html)

[http://kb2.adobe.com/cps/521/cpsid_52132.html](http://kb2.adobe.com/cps/521/cpsid_52132.html)

> 64-bit binaries of AIR are currently not available. Running 32-bit AIR on 64-bit systems has not been fully tested. However, we expect 32-bit AIR to run on our supported distributions (Fedora Core 11, Ubuntu 9.04 and OpenSuSe 11.1) if the required 32-bit libraries and packages are installed. If you do not have the required 32-bit dependencies on your system, you might see the following errors on running the AIR installer:

With .bin installer:

bash: ./AdobeAIRInstaller.bin: No such file or directory

---

### Post by otoris on 2010-05-04
I have the same issue. The thing is, on my upgraded system (9.10 to 10.04) Adobe Air will install fine with 64-bit. But on my freshly installed 10.04 64 bit system, it refuses to install...

---

### Post by wersdaluv on 2010-05-04
> **darolu said:**
> What I usually do is navigate to the directory where my binary file is and run it with ./<binary>; anyways there is no 64-bit version of Adobe Air binaries that I'm aware of, this is what I found, I suggest you to follow the instructions:

[http://kb2.adobe.com/cps/408/kb408084.html](http://kb2.adobe.com/cps/408/kb408084.html)

[http://kb2.adobe.com/cps/521/cpsid_52132.html](http://kb2.adobe.com/cps/521/cpsid_52132.html)
Thanks :) I'm downloading the dependencies. The download is just taking so long right now.

> **otoris said:**
> I have the same issue. The thing is, on my upgraded system (9.10 to 10.04) Adobe Air will install fine with 64-bit. But on my freshly installed 10.04 64 bit system, it refuses to install...

Both of my computers have fresh 64 bit installs. One was able to install Adobe Air out of the box. This is ridiculously weird.

---

### Post by wersdaluv on 2010-05-04
> **otoris said:**
> I have the same issue. The thing is, on my upgraded system (9.10 to 10.04) Adobe Air will install fine with 64-bit. But on my freshly installed 10.04 64 bit system, it refuses to install...
I think, that's probably because of lack of dependencies. See link from darolu :)

---

