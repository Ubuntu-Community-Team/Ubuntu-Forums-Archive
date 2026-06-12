---
title: "Telnet not working from remote(windows) system"
date: 2011-02-25
forum: General Help
---

### Post by mswamy78 on 2011-02-25
Hello,

I have installed Ubuntu 10.10 Maverick Meerkat. I am unable to connect using telnet from the remote pc (windows), it says connection lost.
However if i use telnet from ubuntu installed system to connect another linux m/c it works.
Am I missing any installation/packages in ubuntu installed m/c?

Please help to resolve it. 
Thanks in Advance.

---

### Post by HermanAB on 2011-02-25
howdy,

Try:
$ sudo iptables -F

to flush all rules from your netfiler and try again.  If it now works, then you have an incoming 'firewall' problem.  Firewalls usually allow anything outgoing.

---

### Post by dcstar on 2011-02-25
> **mswamy78 said:**
> Hello,

I have installed Ubuntu 10.10 Maverick Meerkat. I am unable to connect using telnet from the remote pc (windows), it says connection lost.
However if i use telnet from ubuntu installed system to connect another linux m/c it works.
Am I missing any installation/packages in ubuntu installed m/c?

Please help to resolve it. 


How about installing the telnet server package?

Do not assume that every single thing is installed.

---

### Post by mswamy78 on 2011-02-28
Hello David,
Thanks for the reply.
Could you suggest where can I get telnet packages for Ubuntu 10.10 Maverick Meerkat. Also i found that under /usr/bin/ there is a telnet and telnet.netkit installed.
Please suggest whether apart from this i need to install something.
Thanks,
Swamy

---

### Post by mswamy78 on 2011-02-28
Hello Herman,
Actually I am able to connect to internet via Firefox web browser. I also executed the command $ sudo iptables -F. After this I tried to connect the telnet and it failed. Do I need to modify any firewall settings?
Thanks,
Swamy

---

### Post by gmargo on 2011-02-28
You'll need to install a telnet server package.  There are several to choose from.  Try installing the [**telnetd**]("http://packages.ubuntu.com/maverick/telnetd") package.

[http://packages.ubuntu.com/search?keywords=telnetd&searchon=names&section=all](http://packages.ubuntu.com/search?keywords=telnetd&searchon=names&section=all)

---

### Post by mswamy78 on 2011-02-28
I downloaded telnetd_0.17-36build1_i386.deb from [http://packages.ubuntu.com/maverick/i386/telnetd/download](http://packages.ubuntu.com/maverick/i386/telnetd/download)...
Can you tell me what is the procedure to install and to which directory. As I am new to this I am not sure of the installation.

---

### Post by aeiah on 2011-02-28
is there any real reason why you must use telnet? it's insecure, and has been replaced with ssh

---

### Post by mswamy78 on 2011-02-28
There is no such reason, i can install SSH also. Let me know the way for it.

---

### Post by btindie on 2011-02-28
Take a look at [https://help.ubuntu.com/community/InstallingSoftware](https://help.ubuntu.com/community/InstallingSoftware) to learn how to install software under Ubuntu, you don't have to manually download deb files from the web.

The easiest way to install SSH is to type
```
# apt-get install openssh-server
```If you want to then connect to it via a Windows box then you'll need something like [PuTTY]("http://www.chiark.greenend.org.uk/%7Esgtatham/putty/") which is an SSH client.

Windows still uses telnet which is insecure and should be avoided at all cost unless absolutely necessary.

---

### Post by gmargo on 2011-02-28
> **mswamy78 said:**
> 
Can you tell me what is the procedure to install and to which directory.

Let the packaging software do all the work:
```

sudo apt-get install telnetd

```

---

### Post by mswamy78 on 2011-03-01
I am getting this error after i execute the command 
**sudo apt-get install openssh-server**
please help..

root@ubuntu-OptiPlex-745:/# sudo apt-get install openssh-server
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package openssh-server is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source

E: Package 'openssh-server' has no installation candidate
root@ubuntu-OptiPlex-745:/#

---

### Post by silbak04 on 2011-03-01
> **mswamy78 said:**
> I am getting this error after i execute the command 
**sudo apt-get install openssh-server**
please help..

root@ubuntu-OptiPlex-745:/# sudo apt-get install openssh-server
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package openssh-server is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source

E: Package 'openssh-server' has no installation candidate
root@ubuntu-OptiPlex-745:/#

You seem to be already running as root, so there is not reason for you to have to put "sudo" in front of that command. You only put "sudo" when you're not running as root. Therefore, if you still are running as root, try just running:

```

aptitude install openssh-server

```

---

### Post by btindie on 2011-03-01
> **mswamy78 said:**
> 
Package openssh-server is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source

E: Package 'openssh-server' has no installation candidate
root@ubuntu-OptiPlex-745:/#

Try running the following to update the package cache
```
apt-get update
```then the other command again.

---

### Post by mswamy78 on 2011-03-01
After running **apt-get update** I get error on Proxy Authentication required. For your information I am able to open the internet. Please help.


root@ubuntu-OptiPlex-745:~# apt-get update
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) maverick Release.gpg
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) maverick Release.gpg
Ign [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security Release.gpg
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/main Translation-en                                                 
Ign [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) maverick/main Translation-en                                                        
Ign [http://extras.ubuntu.com/ubuntu/](http://extras.ubuntu.com/ubuntu/) maverick/main Translation-en                                           
Ign [http://extras.ubuntu.com/ubuntu/](http://extras.ubuntu.com/ubuntu/) maverick/main Translation-en_IN                                                         
Ign [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) maverick/main Translation-en_IN                                                     
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/main Translation-en_IN                                              
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) maverick Release                                                                                
Ign [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) maverick/multiverse Translation-en                                                  
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/multiverse Translation-en                                           
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) maverick/main Sources                                                                           
Ign [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) maverick/multiverse Translation-en_IN                               
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) maverick/main i386 Packages                                                                     
Ign [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) maverick/restricted Translation-en                                                  
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) maverick/main Sources                                                                           
Ign [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) maverick/restricted Translation-en_IN                                               
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) maverick/main i386 Packages                                                                     
Ign [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) maverick/universe Translation-en                                                    
Err [http://extras.ubuntu.com](http://extras.ubuntu.com) maverick/main Sources                                                                           
  407  Proxy Authentication Required
Ign [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) maverick/universe Translation-en_IN                                                 
Err [http://extras.ubuntu.com](http://extras.ubuntu.com) maverick/main i386 Packages                                                                     
  407  Proxy Authentication Required

---

### Post by btindie on 2011-03-01
Do you use a proxy on your network?

Run the following and paste the result
```
sudo env | grep proxy
sudo apt-config dump | grep -i proxy

```It may be that you have apt configured to use a proxy. If that's the case then it may be defined in /etc/apt.

---

### Post by matt_symes on 2011-03-01
Hi

```
Err http://extras.ubuntu.com maverick/main Sources 
407 Proxy Authentication Required 
Err http://extras.ubuntu.com maverick/main i386 Packages 
```

Are you sure there are not 2 malformed lines in your sources.list file ? 

Can you post this back here. 

```
cat /etc/apt/sources.list
```

I might be missing something but that does not look correct.

BTW: I concur. I use ssh to configure my headless server and use Putty on windows to talk to it. Telnet is pretty dead.

Kind regards

---

### Post by mswamy78 on 2011-03-02
After running,

[B][COLOR=Red]# sudo env | grep proxy
# sudo apt-config dump | grep -i proxy
[/COLOR]
I got following messages..

Acquire::http::proxy "http://autoproxy-apac.delphiauto.net:8080/";
Acquire::ftp::proxy "ftp://autoproxy-apac.delphiauto.net:8080/";
Acquire::https::proxy "https://autoproxy-apac.delphiauto.net:8080/";

[/B]
**[COLOR=Red]# cat /etc/apt/sources.list[/COLOR]**

# deb cdrom:[Ubuntu 10.10 _Maverick Meerkat_ - Release i386 (20101007.1)]/ maverick main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) maverick main restricted
deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) maverick main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) maverick-updates main restricted
deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) maverick-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) maverick universe
deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) maverick universe
deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) maverick-updates universe
deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) maverick-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) maverick multiverse
deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) maverick multiverse
deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) maverick-updates multiverse
deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) maverick-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) maverick-backports main restricted universe multiverse
# deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) maverick-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) maverick partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) maverick partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) maverick main
deb-src [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) maverick main

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) maverick-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) maverick-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) maverick-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) maverick-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) maverick-security multiverse
deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) maverick-proposed restricted main multiverse universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) maverick-security multiverse

---

### Post by mswamy78 on 2011-03-02
-

---

### Post by btindie on 2011-03-02
> **mswamy78 said:**
> After running,

[B][COLOR=Red]# sudo env | grep proxy
# sudo apt-config dump | grep -i proxy
[/COLOR]
I got following messages..

Acquire::http::proxy "http://autoproxy-apac.delphiauto.net:8080/";
Acquire::ftp::proxy "ftp://autoproxy-apac.delphiauto.net:8080/";
Acquire::https::proxy "https://autoproxy-apac.delphiauto.net:8080/";
[/B]

Your system is configured to use a proxy. Is that something you setup?

Run the following to identify which file it's defined in:
```
cd /etc/apt/apt.conf.d
grep -l Proxy *

```Then edit the file listed above to remove the proxy lines. You can then update and install openssh.
```
sudoedit <file_from_above_output>
sudo apt-get update
sudo apt-get install openssh-server

```

---

### Post by mswamy78 on 2011-03-03
Thanks everyone for the replies. Finally I was able to resolve the issue.
I had not provided the username and password under #/etc/apt/apt.conf
 
Acquire::http::proxy "[http://Domain\Name:Password@proxy.net:8080/](http://Domain\Name:Password@proxy.net:8080/)";
After this i was able to download the packages.
Thanks once again everyone for the feedbacks.

---

