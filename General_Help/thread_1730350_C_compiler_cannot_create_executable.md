---
title: "C compiler cannot create executable"
date: 2011-04-15
forum: General Help
---

### Post by myhieu on 2011-04-15
I try to install git packages, when I type ./configure it gives me the error: 


```
C compiler cannot create executable
```

Search around, and I find a solution, install the g++ packages, simply type:

```
apt-get install g++
```

But it gives me another error

```
The following packages have unmet dependencies:
 g++ : Depends: g++-4.4 (>= 4.4.3-1) but it is not going to be installed
E: Broken packages
```

I also tried

```
apt-get install build-essential
```

But I get another error

```
The following packages have unmet dependencies:
 build-essential : Depends: libc6-dev but it is not going to be installed or
                            libc-dev
                   Depends: g++ (>= 4:4.3.1) but it is not going to be installed
E: Broken packages
```

Now, I don't know what should I do next, please help.

---

### Post by myhieu on 2011-04-15
And instead of compiling the source, I try to install git debian package, but another error


```
dpkg -i git_1.7.4.1-5_i386.deb     
Selecting previously deselected package git.
(Reading database ... 34830 files and directories currently installed.)
Unpacking git (from git_1.7.4.1-5_i386.deb) ...
/var/lib/dpkg/tmp.ci/preinst: 12: dpkg-maintscript-helper: not found
dpkg: error processing git_1.7.4.1-5_i386.deb (--install):
 subprocess new pre-installation script returned error exit status 127
/var/lib/dpkg/tmp.ci/postrm: 14: dpkg-maintscript-helper: not found
dpkg: error while cleaning up:
 subprocess new post-removal script returned error exit status 127
Errors were encountered while processing:
 git_1.7.4.1-5_i386.deb

```

---

### Post by lmarmisa on 2011-04-15
If you know the packages you have to install, use System -> Administration -> Synaptic Package Manager.

I do not know anything about git, but maybe this link could help you:

[https://help.ubuntu.com/community/Git](https://help.ubuntu.com/community/Git)

Best regards,

Luis

---

### Post by myhieu on 2011-04-15
I configure the vps through ssh, so command line only :(

---

### Post by lmarmisa on 2011-04-15
I recommend not to download the packages if they are included in Ubuntu. 

Try this command:

```

sudo apt-get install git

```

---

### Post by myhieu on 2011-04-15
I tried and it said the package is not available

---

### Post by lmarmisa on 2011-04-15
I am running Ubuntu 10.10. Which is your Ubuntu version?.

---

### Post by myhieu on 2011-04-16
I use Ubuntu 10.04, my sources.list of repositories is

```
## main & restricted repositories
deb http://us.archive.ubuntu.com/ubuntu/ lucid main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ lucid main restricted

deb http://security.ubuntu.com/ubuntu lucid-updates main restricted
deb-src http://security.ubuntu.com/ubuntu lucid-updates main restricted

deb http://security.ubuntu.com/ubuntu lucid-security main restricted
deb-src http://security.ubuntu.com/ubuntu lucid-security main restricted

## universe repositories - uncomment to enable
deb http://us.archive.ubuntu.com/ubuntu/ lucid universe
deb-src http://us.archive.ubuntu.com/ubuntu/ lucid universe

deb http://us.archive.ubuntu.com/ubuntu/ lucid-updates universe
deb-src http://us.archive.ubuntu.com/ubuntu/ lucid-updates universe

deb http://security.ubuntu.com/ubuntu lucid-security universe
deb-src http://security.ubuntu.com/ubuntu lucid-security universe

deb http://archive.canonical.com/ubuntu lucid partner
deb http://ppa.launchpad.net/zentyal/2.0/ubuntu lucid main


```

---

### Post by lmarmisa on 2011-04-16
If you are using 10.04, the link [https://help.ubuntu.com/community/Git](https://help.ubuntu.com/community/Git) should be useful for you.

This link recommends this command:

```

sudo apt-get -y install git-core gitosis

```

---

### Post by vivek.pandey on 2011-04-16
here it seems your g++ package is broken .. so try dpkg it.... also i think you should do this first--> though even i have g++ compiled but i am forgetting whether the name of package was g++ or something else . to know it type g++.. you will get a list of packages ..install one from them

---

### Post by myhieu on 2011-04-16
> **lmarmisa said:**
> If you are using 10.04, the link [https://help.ubuntu.com/community/Git](https://help.ubuntu.com/community/Git) should be useful for you.

This link recommends this command:

```

sudo apt-get -y install git-core gitosis

```

Thank you, it works like a charm. Git package is installed properly, but do you know how to fix the error "C compiler cannot create executables" ?

---

### Post by lmarmisa on 2011-04-16
Did you install cc compiler from the Ubuntu repositories?.

I recommend this test. Prepare a tiny and trivial C program named main.c.

Then type this command:

```

cc main.c

```

A file named a.out should be created. If this test is successful, your cc compiler is running properly.

---

### Post by myhieu on 2011-04-16
> **vivek.pandey said:**
> here it seems your g++ package is broken .. so try dpkg it.... also i think you should do this first--> though even i have g++ compiled but i am forgetting whether the name of package was g++ or something else . to know it type g++.. you will get a list of packages ..install one from them

When I install g++, by "sudo apt-get install g++", it said my g++ depends on some other packages like


```
The following packages have unmet dependencies:
 g++ : Depends: g++-4.4 (>= 4.4.3-1) but it is not going to be installed
```


```
The following packages have unmet dependencies:
 g++-4.4 : Depends: libstdc++6-4.4-dev (= 4.4.3-4ubuntu5) but it is not going to be installed

```

```
The following packages have unmet dependencies:
 libc6-dev : Depends: libc6 (= 2.11.1-0ubuntu7.8) but 2.13-0ubuntu13 is to be installed
             Depends: libc-dev-bin (= 2.11.1-0ubuntu7.8) but it is not going to be installed

```

---

### Post by myhieu on 2011-04-16
> **lmarmisa said:**
> Did you install cc compiler from the Ubuntu repositories?.

I recommend this test. Prepare a tiny and trivial C program named main.c.

Then type this command:

```

cc main.c

```

A file named a.out should be created. If this test is successful, your cc compiler is running properly.

I practice your guide, then

```

// main.c
#include <stdio.h>
int main() {
        printf("Hello wordl");
        return 0;
}

```

```
cc main.cc
```

```
main.c:1:19: error: stdio.h: No such file or directory
main.c: In function 'main':
main.c:4: warning: incompatible implicit declaration of built-in function 'printf'

```

---

### Post by lmarmisa on 2011-04-16
You should fix the broken packages.

Please type these commands:

```

sudo apt-get install -f

```or

```

sudo apt-get install --fix-missing

```Then repeat the install command:

```

sudo apt-get update
sudo apt-get install g++ build-essential 

```

---

### Post by myhieu on 2011-04-16
```
root@vpmhieu:~# apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
root@vpmhieu:~# apt-get install --fix-missing
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```

```

root@vpmhieu:~# apt-get update
....
root@vpmhieu:~# apt-get install g++ build-essential
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 build-essential : Depends: libc6-dev but it is not going to be installed or
                            libc-dev
 g++ : Depends: g++-4.4 (>= 4.4.3-1) but it is not going to be installed
E: Broken packages

```

And if I try to install libc6-dev and g++-4.4 package, it'll throw errors which I include in post I reply to vivek.pandey.

---

### Post by lmarmisa on 2011-04-16
Please, post the results of the commands:

```
sudo apt-get install -f 
```and

```

sudo apt-get install --fix-missing

```

Forget it. I did not read completely your last post.

---

### Post by lmarmisa on 2011-04-16
Try the solution to fix the broken packages proposed by Gazneth in this thread:

[http://ubuntuforums.org/showthread.php?t=947124](http://ubuntuforums.org/showthread.php?t=947124)

---

### Post by myhieu on 2011-04-16
> **lmarmisa said:**
> Try the solution to fix the broken packages proposed by Gazneth in this thread:

[http://ubuntuforums.org/showthread.php?t=947124](http://ubuntuforums.org/showthread.php?t=947124)

Finally, I re-install the linux, and every thing is fine now. Thanks for your help very much, it helps me a lot :guitar:

---

### Post by myhieu on 2011-04-16
> **lmarmisa said:**
> Try the solution to fix the broken packages proposed by Gazneth in this thread:

[http://ubuntuforums.org/showthread.php?t=947124](http://ubuntuforums.org/showthread.php?t=947124)

Finally, I re-install the linux, and every thing is fine now. Thanks for your help very much, it helps me a lot :guitar:

---

