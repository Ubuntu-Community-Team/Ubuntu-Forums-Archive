---
title: "Can't get Hula installed :-("
date: 2006-02-23
forum: General Help
---

### Post by galume on 2006-02-23
Hi,

I'm not having any luck getting Hula to work on Ubuntu 5.01 Gnome and have a couple of noob questions...

I've read the wikis and tried all the installation instructions but something or other fails each time, so first off- do I need to have the server version of Ubuntu installed to do this?

If so, I assume that was a setup option I must have overlooked, please correct me if I'm wrong.

If it can be installed on the desktop install, what's going on?    Here's the output from  a couple of install attempts- I did them according to wiki instructions both here and on the Hula site:

**1st try**
sudo apt-get install hula libhula0 hula-cil-agents
Reading package lists... Done
Building dependency tree... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  hula-cil-agents: Depends: libhula-cil (>= 0.1.0+svn700) but it is not going to  be installed
E: Broken packages

**2nd try**
sudo apt-get --yes install automake1.7 autoconf libtool openssl libssl-dev
Reading package lists... Done
Building dependency tree... Done
Package automake1.7 is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package automake1.7 has no installation candidate

**3rd try**
mkdir hula
cd hula/
/hula$ svn checkout svn+ssh://anonymous@forgesvn1.novell.com/svn/hula/trunk/hula
bash: svn: command not found

Does anyone have any suggestions & can see what's wrong?  I can see that on the third set of instructions I don't have svn, and the instructions said it was in the package manager but it's not.  Any help out there?

Thanks in advance- Galume
](*,)

---

### Post by lamego on 2006-02-23
I see problems on all of your options, lets keep with the first:
To install hula you only need:
```
sudo apt-get install hula
```
Why are you specifing the other packages ?

---

### Post by galume on 2006-02-23
Hi Lamego,

I was following the instructions on the wiki...

[https://wiki.ubuntu.com/InstallingHula](https://wiki.ubuntu.com/InstallingHula)
:???:

---

### Post by galume on 2006-02-23
OK, I used your commands and it worked! :o  Here's the output:

sudo apt-get install hula
Password: XXXXXXXX
Reading package lists... Done
Building dependency tree... Done
The following extra packages will be installed:
  libhula0
Suggested packages:
  hula-mta hula-cil-agents
The following NEW packages will be installed:
  hula libhula0
0 upgraded, 2 newly installed, 0 to remove and 0 not upgraded.
Need to get 4504kB of archives.
After unpacking 13.5MB of additional disk space will be used.
Do you want to continue [Y/n]? y
WARNING: The following packages cannot be authenticated!
  libhula0 hula
Install these packages without verification [y/N]? y
Get:1 [http://www.alcoholicsunanimous.com](http://www.alcoholicsunanimous.com) debs/ libhula0 0.1.0+svn862-1 [792kB]
Get:2 [http://www.alcoholicsunanimous.com](http://www.alcoholicsunanimous.com) debs/ hula 0.1.0+svn862-1 [3712kB]
Fetched 4504kB in 47s (93.9kB/s)

Preconfiguring packages ...
Selecting previously deselected package libhula0.
(Reading database ... 56914 files and directories currently installed.)
Unpacking libhula0 (from .../libhula0_0.1.0+svn862-1_i386.deb) ...
Selecting previously deselected package hula.
Unpacking hula (from .../hula_0.1.0+svn862-1_i386.deb) ...
Setting up libhula0 (0.1.0+svn862-1) ...
Setting up hula (0.1.0+svn862-1) ...
Hula has not been configured; not attempting to update schema


Do you have a recomendation on the next steps?  The above wiki lists the following as configuration steps: 

Step 3: Configuring Hula

Before you can start using Hula, you need to configure Hula with the information for your domain. You can do this using the hulasetup command.

sudo hulasetup --domain=yourdomain.com

You need to replace yourdomain.com with your domain name (like ubuntu.com). This must NOT include www. or [WWW] http://
Step 4: Running Hula

There is an init.d script included with Hula. So, to start Hula, you just run (in a terminal):

sudo /etc/init.d/hula start


Proceed?

---

### Post by lamego on 2006-02-23
Hi galume,
yes the rest seems fine
(Please note that I didn't install hula myself yet, I am going to try it today because it looks nice :p )

---

### Post by galume on 2006-02-23
Thanks lamego, all looks good. Now just a matter of reading the configuration docs...

\\:D/

---

### Post by lamego on 2006-02-23
Btw, After reading the wiki I noticed that the ubuntu packages are REALLY old.
Please keep the entry on apt sources.list as suggested on the wiki beforing doing the apt-get install ...

---

### Post by dgermann on 2006-03-01
Hi--

Do the calendars have to be published to the Web somewhere, or can it simply be set to fictitious.com, which resides on the network server?

If so, is something else required to be installed first?

Thanks!

---

