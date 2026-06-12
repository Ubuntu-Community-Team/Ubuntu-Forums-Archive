---
title: "Problem with aptdaemon"
date: 2010-10-31
forum: General Help
---

### Post by olex on 2010-10-31
When I try to install a downloaded package FirstClass: fcc-10.009-Linux.i686.deb I get a message saying that there seems to be a programming error in aptdaemon.

When I try to install same package from terminal with dpkg i get the following:

ole@Oles-lap:~$ sudo dpkg -i /home/ole/Hentede\ filer/fcc-10.009-Linux.i686.deb
dpkg: fejl under behandling af /home/ole/Hentede filer/fcc-10.009-Linux.i686.deb (--install):
 unable to open file '/var/lib/dpkg/tmp.ci//.svn': Is a directory
Der opstod fejl under behandlingen:
 /home/ole/Hentede filer/fcc-10.009-Linux.i686.deb

Can anyone help me out here?

---

### Post by pierreu1 on 2010-11-01
I have the same problem! I was able to download it (the .deb files), but extracting or clicking on them produced errors messages. I am adding this so that people understand that this is not just an isolated problem!

I am adding the place from which one can download this. Where is the problem? 

[http://www.firstclass.com/Divisions/Resources/?Plugin=FC&OpenItemURL=S047C50E4](http://www.firstclass.com/Divisions/Resources/?Plugin=FC&OpenItemURL=S047C50E4)

---

### Post by jorgenqv on 2010-11-01
Are you running Ubuntu 10.10 Maverick Meerkat?
If so, this could be a clue to whats wrong: 
[https://bugs.launchpad.net/aptdaemon/+bug/637489](https://bugs.launchpad.net/aptdaemon/+bug/637489)

The workaround is to install the tar-gz package from Open Text.

If you are not comfortable doing tar ball installs, I made a install script for this. Warning: It's brand new and there could be bugs, I am a script noob and it's all in Swedish! :P

[http://sajtverkstan.net/FBNwiki/Autofcc](http://sajtverkstan.net/FBNwiki/Autofcc)

All feedback is appreciated :)

/Jorgen

PS: Running FCC for Windows in Wine 1.3 is a well working alternative.

---

### Post by pierreu1 on 2010-11-11
Hi JOrgen!

Thanks! I am comfortable with using tar packages ... as I have done in the past without difficulty, but, yes, it looks like this is an isolated. I have informed open text 3 weeks ago, but they have not replied or given an explanation.

Thanks for the help!

> **jorgenqv said:**
> Are you running Ubuntu 10.10 Maverick Meerkat?
If so, this could be a clue to whats wrong: 
[https://bugs.launchpad.net/aptdaemon/+bug/637489](https://bugs.launchpad.net/aptdaemon/+bug/637489)

The workaround is to install the tar-gz package from Open Text.

If you are not comfortable doing tar ball installs, I made a install script for this. Warning: It's brand new and there could be bugs, I am a script noob and it's all in Swedish! :P

[http://sajtverkstan.net/FBNwiki/Autofcc](http://sajtverkstan.net/FBNwiki/Autofcc)

All feedback is appreciated :)

/Jorgen

PS: Running FCC for Windows in Wine 1.3 is a well working alternative.

---

### Post by 2sondad on 2010-12-12
The fix for me was to go into Synaptic, use the "broken" filter and have Synaptic find/fix/upgrade the broken packages. Apparently this message is from a broken or incomplete package download.

---

### Post by mima athens on 2010-12-13
thanks dude! u saved me.....!

---

### Post by pierreu1 on 2010-12-13
> **2sondad said:**
> The fix for me was to go into Synaptic, use the "broken" filter and have Synaptic find/fix/upgrade the broken packages. Apparently this message is from a broken or incomplete package download.

I am not too sure how the filter works, but after I clicked on the filter and located the package (.deb), no files including the deb file would be highlighted and therefore could not be chosen. I gather there is more to this filter that meets the eye. :)

I will try one more time with the tar file, just for the heck of it. A fresh download. I just did and got the same result. 

I assume that I have to use the deb file. Can someone tell me if the error might also be in the script that FC is provided because the file # does not look like the one being downloaded! Anyway, su did not work, # su did not work, but sudo did work, but I got an error message!

Thanks for the support!

---

### Post by pierreu1 on 2011-01-03
I continue to have problem installing firstclass. The Tar file continues not to come clean (I am in Asia, so perhaps it is a long ways away or something). The same for the .deb file. Maybe it is another issue. Opentext is very quiet in helping me. Maybe they are not clear as to what could be the problem. Can someone help?

The situation is this one. I am running Maverick on a single PC. I am assuming that I should be loading 386 packages. Is this right? If this is the case, why is FC indicating that I should be downloading a 686 package? Furthermore, the name of the package does not match the name given for the terminal commands! Am I missing something? Also, the dependencies packages required cannot be found on Synaptic. I am assuming that FC is asking me to download a server package. AM I right? I am very confused! 

Thank you for your support!



Here is the [company info]("http://www.firstclass.com/ClientDownloadReadme/readme-us?Plugin=FC"):

Debian Intel (also for use on ubuntu, knoppix, and other debian x86 derivatives):
        # su
        Password: ******
        # dpkg -i fcc-9.124-Linux.i686.deb

Generic Intel:
        # su
        Password: *******        # cd /
        # tar xvfj fcc-9.124-Linux.i686.tar.bz2

Dependencies:
The packages should bring down the appropriate dependencies when installed, in case the generic package is needed, the following dependencies are needed:
QT 3.3
libartsc 1.3.2+
libpng 1.2.8+
libjpeg 6b+

---

### Post by Hamid2547 on 2011-01-27
> **2sondad said:**
> The fix for me was to go into Synaptic, use the "broken" filter and have Synaptic find/fix/upgrade the broken packages. Apparently this message is from a broken or incomplete package download.
i did as you said and the problem fixed,i cancel the downloading package couple of time and package was broken,i reinstall it with Synaptic:smile:

---

### Post by pierreu1 on 2011-01-27
This person wrote this:

Got the same error with a different .deb package. My solution - remove the (unnecessary) .svn folder from the .deb file.
I attached a small script that does just that - opens the deb file, removes the .svn folder from /DEBIAN/.svn and repackages the deb file. at [https://bugs.launchpad.net/aptdaemon/+bug/637489](https://bugs.launchpad.net/aptdaemon/+bug/637489)

Can someone let me know that this is safe and explain to me how to run this? BTW, ant-virus did not flag this! Thanks!

---

### Post by ikt on 2011-03-17
> **pierreu1 said:**
> This person wrote this:

Got the same error with a different .deb package. My solution - remove the (unnecessary) .svn folder from the .deb file.
I attached a small script that does just that - opens the deb file, removes the .svn folder from /DEBIAN/.svn and repackages the deb file. at [https://bugs.launchpad.net/aptdaemon/+bug/637489](https://bugs.launchpad.net/aptdaemon/+bug/637489)

Can someone let me know that this is safe and explain to me how to run this? BTW, ant-virus did not flag this! Thanks!

Yeah I had a quick look over the source and it seems fine, it worked for me as well and allowed the first class client to install.

---

### Post by benjaminblaqk on 2011-10-08
> **2sondad said:**
> The fix for me was to go into Synaptic, use the "broken" filter and have Synaptic find/fix/upgrade the broken packages. Apparently this message is from a broken or incomplete package download.


This just made my life that much easier. Thank you so much.

---

### Post by cpolicari on 2011-11-14
> **2sondad said:**
> The fix for me was to go into Synaptic, use the "broken" filter and have Synaptic find/fix/upgrade the broken packages. Apparently this message is from a broken or incomplete package download.


I'm having exactly the same issue trying to install fcc-10.014-Linux.i686.deb, but I have no idea what this advice means.  I'd like to follow it, since it seems to be working for others.

So far, I've downloaded and attempted an install using the software center in Ubuntu 10.10, resulting in the original error posted here.  Then I opened Synaptic, and couldn't find any broken packages.  I'm probably doing something wrong.

---

### Post by oldos2er on 2011-11-14
For specialized software such as what you're trying to install, it's usually better to go to the company/website in question for help; [https://galacticomm.org/support.html](https://galacticomm.org/support.html)

---

### Post by cpolicari on 2011-11-14
If this is any help, the following error showed up in the terminal after using a GDebi package installer:

```

 unable to open file '/var/lib/dpkg/tmp.ci//.svn': Is a directory

```

---

### Post by cpolicari on 2011-11-15
jorgenqv's script works for installing from tar.  Thanks!  Your instructions translate pretty easily in google :)

---

