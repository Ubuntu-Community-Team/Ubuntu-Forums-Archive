---
title: "failed installing Wine, Package dependencies cannot be resolved"
date: 2012-10-13
forum: General Help
---

### Post by mlm5 on 2012-10-13
I have ubuntu on my new chromebox.
I installed wine stable v1.4, deleted it and reinstalled 1.5.1.
Now I deleted again, trying to install v1.4 again.
But I am getting "Package dependencies cannot be resolved" msg.


user@ChrUbuntu:~$ sudo apt-get install wine1.4
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help resolve the situation:

The following packages have unmet dependencies:
 wine1.4 : Depends: wine1.4-amd64 (= 1.4.1-0ubuntu1~precise1~ppa3)
           Depends: wine1.4-i386 (= 1.4.1-0ubuntu1~precise1~ppa3)
E: Unable to correct problems, you have held broken packages.

---

### Post by Hekabe on 2012-10-13
Use ```
sudo apt-get autoremove
``` and then try again.

---

### Post by mlm5 on 2012-10-13
Thank you, Hekabe.
This is result of your code:

Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.


But the same error:

user@ChrUbuntu:~$ sudo apt-get install wine1.4
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help resolve the situation:

The following packages have unmet dependencies:
 wine1.4 : Depends: wine1.4-amd64 (= 1.4.1-0ubuntu1~precise1~ppa3)
           Depends: wine1.4-i386 (= 1.4.1-0ubuntu1~precise1~ppa3)
E: Unable to correct problems, you have held broken packages.

---

### Post by Hekabe on 2012-10-13
Have you tried manually removing/reinstalling the packages (wine-1.4-amd64 and wine-1.4-i386) listed?

---

### Post by mlm5 on 2012-10-13
It might be stupid question, but I am new to Linux...

I just manually deleted the packages using:
```

sudo mv /var/lib/dpkg/info/wine1.4-amd64.* /tmp/
sudo mv /var/lib/dpkg/info/wine1.4-i386.* /tmp/
sudo dpkg --remove --force-remove-reinstreq wine1.4-amd64
sudo dpkg --remove --force-remove-reinstreq wine1.4-i386

```

But I don't know how to reinstall packages...
and installing wine is still not working.
Thank you for your help, Hekabe

---

### Post by critin on 2012-10-13
> E: Unable to correct problems, you have held broken packages.

how to fix broken packages

[http://www.thepowerbase.com/2012/04/...ntu-or-debian/]("http://www.thepowerbase.com/2012/04/how-to-fix-broken-packages-in-ubuntu-or-debian/")

Go to Synaptic Package Manager and open Edit--Fix broken packages.
Take a look at the help menu there and it may have the answer. 

Quoted from Synaptic Help:
 *[COLOR=#3C3C3C][FONT=sans-serif]Synaptic Package Manager[/FONT][/COLOR][COLOR=#3C3C3C][FONT=sans-serif] will not allow any further changes to the system before all broken packages are fixed.[/FONT][/COLOR]*

---

