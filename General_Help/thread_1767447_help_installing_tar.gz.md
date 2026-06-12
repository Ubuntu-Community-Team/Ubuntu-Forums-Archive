---
title: "help installing tar.gz"
date: 2011-05-25
forum: General Help
---

### Post by .psd on 2011-05-25
Nothing but dissapointment so far with Ubuntu... :( I've been on the forums for like 2 days posting threads, only to realize I'm asking questions that have been asked for years yet remain unsolved.

I would install straight from some package manager, but Synaptec and USC have outdated versions (thanks again ubuntu....). So I extracted a .tar.gz file, and this is what the read me says (note, this is complete gibberish and so was everything google turned up).

Description
-----------

Lifeograph is a diary program to take personal notes on life. It has all 
essential functionality expected in a diary program and strives to have
a clean and streamlined user interface.



Requirements
------------

Lifeograph requires the following modules to be built:
    * gtkmm,
    * gtkspell, and
    * gcrypt.



Installation
------------

To configure, build, and install, use the following commands:

    ./waf configure [--prefix=path]
    ./waf build
    ./waf install

Square brackets designate optional parts of the commands.

---

### Post by zealibib slaughter on 2011-05-25
> **.psd said:**
> Nothing but dissapointment so far with Ubuntu... :( I've been on the forums for like 2 days posting threads, only to realize I'm asking questions that have been asked for years yet remain unsolved.
 
I would install straight from some package manager, but Synaptec and USC have outdated versions (thanks again ubuntu....). So I extracted a .tar.gz file, and this is what the read me says (note, this is complete gibberish and so was everything google turned up).
 
Description
-----------
 
Lifeograph is a diary program to take personal notes on life. It has all 
essential functionality expected in a diary program and strives to have
a clean and streamlined user interface.
 
 
 
Requirements
------------
 
Lifeograph requires the following modules to be built:
* gtkmm,
* gtkspell, and
* gcrypt.
 
 
 
Installation
------------
 
To configure, build, and install, use the following commands:
 
./waf configure [--prefix=path]
./waf build
./waf install
 
Square brackets designate optional parts of the commands.
 
 
First you need to make sure gtkmm, gtkspell, and gcrypt is installed more than likely by downloading the packages and compiling them.
then in a terminal use the commands given.
so you would type exactly```
 ./waf configure
```and watch for errors if none then ```
./waf build 
```and watch for errors if none then ```
./waf install
```if there is no errors then the install should be sucessful and you can more than likely start the program by typing waf in a terminal.

---

### Post by .psd on 2011-05-25
Oops I forgot to mention I've been using Ubuntu for less than a week and I don't know how to "make sure gtkmm, gtkspell, and gcrypt is installed more than likely by downloading the packages and compiling them." Help?

And once that's done, please assume I'm retarded. So assume I just logged in and opened a terminal, what *exactly* would I type? Do I need to do "cd blahblahblah/blahblahblah/blahblahblah" first?

---

### Post by zealibib slaughter on 2011-05-25
first code in terminal
```
dpkg --get-selections | grep *nameofpackage
```replacing *nameofpackage for the package you want to check to see if it is installed.once you have checked all three dependencies post back which ones aren't installed.

---

### Post by .psd on 2011-05-25
What I typed and copy+pasted everything from the terminal. In other words each command did nothing...?

ngrlvr@ngrlvr-EX58-UD3R:~$ dpkg --get-selections | grep *gtkmm
ngrlvr@ngrlvr-EX58-UD3R:~$ dpkg --get-selections | grep *gtkspell
ngrlvr@ngrlvr-EX58-UD3R:~$ dpkg --get-selections | grep *gcrypt
ngrlvr@ngrlvr-EX58-UD3R:~$

---

### Post by zealibib slaughter on 2011-05-25
try the command without including the *
as in dpkg --get-selections | grep gtkmm

---

### Post by AlphaLexman on 2011-05-25
Do you really need to install the latest version from source code?
Or could you just install the stable version in the repo's?
```
sudo apt-get install lifeograph
```

---

### Post by .psd on 2011-05-25
ngrlvr@ngrlvr-EX58-UD3R:~$ dpkg --get-selections | grep gtkmm
libgtkmm-2.4-1c2a                install
ngrlvr@ngrlvr-EX58-UD3R:~$ dpkg --get-selections | grep gtkspell
libgtkspell0                    install
python-gtkspell                    install
ngrlvr@ngrlvr-EX58-UD3R:~$ dpkg --get-selections | grep gcrypt
libgcrypt11                    install

---

### Post by .psd on 2011-05-25
> **AlphaLexman said:**
> Do you really need to install the latest version from source code?
Or could you just install the stable version in the repo's?
```
sudo apt-get install lifeograph
```
That's what I was trying to say in the OP. I would rather just go through a package manager, but Synaptec and Ubuntu Software Center have outdated versions :(

If I used the code you posted, will it give me version 0.7.2 or one of the outdated versions?

---

### Post by zealibib slaughter on 2011-05-25
ok looks like they are all installed, lets just hope that they are the correct version.
Now you need to cd to the directory you extracted the tar.gz package to.  If you dont know then you can use the file browser to find it and write down the folder its in, but more than likely it will be in your home folder.  You should be in your home folder already so just type ls and look for a directory or file with the packages name. Post back when you find it.

---

### Post by AlphaLexman on 2011-05-25
According to [launchpad]("https://launchpad.net/lifeograph"), 0.7.2 is the latest stable version, if you need a higher developmental version, it is still in beta stages and may not be 100% reliable.

Although I am not familiar with that program what features do you require that the stable version does not offer?

---

### Post by .psd on 2011-05-25
> **zealibib slaughter said:**
> ok looks like they are all installed, lets just hope that they are the correct version.
Now you need to cd to the directory you extracted the tar.gz package to.  If you dont know then you can use the file browser to find it and write down the folder its in, but more than likely it will be in your home folder.  You should be in your home folder already so just type ls and look for a directory or file with the packages name. Post back when you find it.
Directory is /home/ngrlvr/Downloads/lifeograph-0.7.2
Thus, cd /home/ngrlvr/Downloads/lifeograph-0.7.2        ?

If so, cool. Then what?

---

### Post by zealibib slaughter on 2011-05-25
yes cd to there and then try the commands in my first post.  post back with any problems.

---

### Post by .psd on 2011-05-25
> **AlphaLexman said:**
> According to [launchpad]("https://launchpad.net/lifeograph"), 0.7.2 is the latest stable version, if you need a higher developmental version, it is still in beta stages and may not be 100% reliable.

Although I am not familiar with that program what features do you require that the stable version does not offer?
These say they are old versions. If I download them, will they actually be the newest version?
[IMG]http://img94.imageshack.us/img94/7000/screenshotsynapticpackal.png[/IMG]
[IMG]http://img818.imageshack.us/img818/2330/screenshotubuntusoftwar.png[/IMG]

---

### Post by .psd on 2011-05-25
ngrlvr@ngrlvr-EX58-UD3R:~$ cd /home/ngrlvr/Downloads/lifeograph-0.7.2
ngrlvr@ngrlvr-EX58-UD3R:~/Downloads/lifeograph-0.7.2$ ./waf configure
Checking for program g++ or c++          : /usr/bin/g++ 
Checking for program cpp                 : /usr/bin/cpp 
Checking for program ar                  : /usr/bin/ar 
Checking for program ranlib              : /usr/bin/ranlib 
Checking for g++                         : ok  
Checking for gtkmm-2.4 >= 2.16           : Package gtkmm-2.4 was not found in the pkg-config search path.
Perhaps you should add the directory containing `gtkmm-2.4.pc'
to the PKG_CONFIG_PATH environment variable
No package 'gtkmm-2.4' found 
/home/ngrlvr/Downloads/lifeograph-0.7.2/wscript:60: error: the configuration failed (see '/home/ngrlvr/Downloads/lifeograph-0.7.2/build/config.log')

**config.log:**

# project lifeograph (0.7.2) configured on Wed May 25 15:10:43 2011 by
# waf 1.5.18 (abi 7, python 20701f0 on linux2)
# using ./waf configure
#

----------------------------------------
Checking for program g++ or c++
  find program=['g++', 'c++'] paths=[] var='CXX'
  -> '/usr/bin/g++'

----------------------------------------
Checking for program cpp
  find program=['cpp'] paths=[] var='CPP'
  -> '/usr/bin/cpp'

----------------------------------------
Checking for program ar
  find program=['ar'] paths=[] var='AR'
  -> '/usr/bin/ar'

----------------------------------------
Checking for program ranlib
  find program=['ranlib'] paths=[] var='RANLIB'
  -> '/usr/bin/ranlib'

----------------------------------------
Checking for g++ 
ok 

----------------------------------------
Checking for gtkmm-2.4 >= 2.16
pkg-config --errors-to-stdout --print-errors --atleast-version=2.16 gtkmm-2.4
Package gtkmm-2.4 was not found in the pkg-config search path.
Perhaps you should add the directory containing `gtkmm-2.4.pc'
to the PKG_CONFIG_PATH environment variable
No package 'gtkmm-2.4' found
Package gtkmm-2.4 was not found in the pkg-config search path.
Perhaps you should add the directory containing `gtkmm-2.4.pc'
to the PKG_CONFIG_PATH environment variable
No package 'gtkmm-2.4' found


Since Synaptec is supposed to update my packages, and it didn't update these, and it doesn't have the newest versions of a lot of stuff, is there a better third party package manager?

---

### Post by zealibib slaughter on 2011-05-25
give me a few minutes to google.
 
while you wait try sudo apt-get update in a terminal to update the package list and see if that gives you the updated package in synaptic.
 
also try the following
```

sudo apt-get install libgtkmm-2.4-dev

```
that should give you the required version of gtkmm.

---

### Post by .psd on 2011-05-25
ngrlvr@ngrlvr-EX58-UD3R:~/Downloads/lifeograph-0.7.2$ sudo apt-get update
[sudo] password for ngrlvr: 
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) natty InRelease
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security InRelease
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) natty InRelease
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) natty-updates InRelease             
Get:1 [http://extras.ubuntu.com](http://extras.ubuntu.com) natty Release.gpg [72 B]              
Get:2 [http://security.ubuntu.com](http://security.ubuntu.com) natty-security Release.gpg [198 B]           
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) natty Release.gpg
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) natty Release     
Get:3 [http://security.ubuntu.com](http://security.ubuntu.com) natty-security Release [23.2 kB]
Get:4 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) natty-updates Release.gpg [198 B]            
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) natty/main Sources                                           
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) natty Release                          
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) natty/main amd64 Packages                                      
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) natty/main TranslationIndex             
Get:5 [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/main Sources [7,060 B]
Get:6 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) natty-updates Release [27.2 kB]             
Get:7 [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/restricted Sources [14 B]                            
Get:8 [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/universe Sources [2,692 B]                           
Get:9 [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/multiverse Sources [647 B]                           
Get:10 [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/main amd64 Packages [22.2 kB]                       
Get:11 [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/restricted amd64 Packages [14 B]                    
Get:12 [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/universe amd64 Packages [10.1 kB]           
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) natty/main Sources                              
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) natty/restricted Sources                        
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) natty/universe Sources    
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) natty/multiverse Sources  
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) natty/main amd64 Packages 
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) natty/restricted amd64 Packages
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) natty/universe amd64 Packages
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) natty/multiverse amd64 Packages
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) natty/main TranslationIndex
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) natty/multiverse TranslationIndex
Get:13 [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/multiverse amd64 Packages [1,930 B]
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/main TranslationIndex                                  
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/multiverse TranslationIndex                            
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/restricted TranslationIndex
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/universe TranslationIndex
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) natty/restricted TranslationIndex   
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) natty/universe TranslationIndex
Get:14 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) natty-updates/main Sources [30.7 kB]
Get:15 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) natty-updates/restricted Sources [14 B]    
Get:16 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) natty-updates/universe Sources [7,976 B]                
Get:17 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) natty-updates/multiverse Sources [1,362 B]                       
Get:18 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) natty-updates/main amd64 Packages [104 kB]                       
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) natty/main Translation-en_CA                                            
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) natty/main Translation-en                          
Get:19 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) natty-updates/restricted amd64 Packages [14 B]
Get:20 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) natty-updates/universe amd64 Packages [40.6 kB]
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/main Translation-en_CA
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/main Translation-en
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/multiverse Translation-en_CA
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/multiverse Translation-en
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/restricted Translation-en_CA
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/restricted Translation-en
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/universe Translation-en_CA
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/universe Translation-en
Get:21 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) natty-updates/multiverse amd64 Packages [3,661 B]
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) natty-updates/main TranslationIndex
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) natty-updates/multiverse TranslationIndex
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) natty-updates/restricted TranslationIndex
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) natty-updates/universe TranslationIndex
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) natty/main Translation-en_CA
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) natty/restricted Translation-en_CA
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) natty/main Translation-en                                           
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) natty/multiverse Translation-en_CA                                  
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) natty/multiverse Translation-en                                     
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) natty/restricted Translation-en                                     
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) natty/universe Translation-en_CA                                    
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) natty/universe Translation-en                                       
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) natty-updates/main Translation-en_CA                                
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) natty-updates/main Translation-en                                   
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) natty-updates/multiverse Translation-en_CA                          
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) natty-updates/multiverse Translation-en                             
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) natty-updates/restricted Translation-en_CA                          
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) natty-updates/restricted Translation-en                             
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) natty-updates/universe Translation-en_CA                            
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) natty-updates/universe Translation-en                               
Fetched 284 kB in 7s (37.6 kB/s)                                                                     
Reading package lists... Done

Then I tried ./waf configure again with same results as before...
EDIT: super grateful for your help!!

EDIT2: I did notice that it opened Update Manager which lists 3 new updates available: rdp client something for nt/2000 server, gnu assembler linker and binary stuff, network-related giomodules for glib. I haven't updated them yet.

---

### Post by AlphaLexman on 2011-05-25
I owe you an apology, I did not check the repo's for the current ubuntu version versus the latest lifeograph version.

However, I would recommend installing the lifeograph version from the repo's so that you will get all the dependencies resolved, and then upgrade to the latest version of lifeograph.

---

### Post by zealibib slaughter on 2011-05-25
NP man I've been in your shoes.
Ok lets try this
```

sudo apt-get install libgtkmm-2.4-dev

```
then the make command and see what happens
post back if it still wont compile and we will specify the pathway manually

---

### Post by .psd on 2011-05-25
> **AlphaLexman said:**
> I owe you an apology, I did not check the repo's for the current ubuntu version versus the latest lifeograph version.

However, I would recommend installing the lifeograph version from the repo's so that you will get all the dependencies resolved, and then upgrade to the latest version of lifeograph.
No probs ;) How would I upgrade?

---

### Post by oldos2er on 2011-05-25
According to [http://lifeograph.wikidot.com/](http://lifeograph.wikidot.com/), 0.7.2 is the unstable version. Are you sure that's the one you want? There's a PPA (Personal Package Archive) for the latest stable version, [https://launchpad.net/~dmxe/+archive/ppa](https://launchpad.net/~dmxe/+archive/ppa)

---

### Post by .psd on 2011-05-25
@zealibib, getting closer...

ngrlvr@ngrlvr-EX58-UD3R:~/Downloads/lifeograph-0.7.2$ ./waf configure
Checking for program g++ or c++          : /usr/bin/g++ 
Checking for program cpp                 : /usr/bin/cpp 
Checking for program ar                  : /usr/bin/ar 
Checking for program ranlib              : /usr/bin/ranlib 
Checking for g++                         : ok  
Checking for gtkmm-2.4 >= 2.16           : yes 
Checking for gtkspell-2.0                : not found 
/home/ngrlvr/Downloads/lifeograph-0.7.2/wscript:61: error: the configuration failed (see '/home/ngrlvr/Downloads/lifeograph-0.7.2/build/config.log')

maybe the "install"s earlier meant I don't have them...?

@oldos2er Ya I'll be OK with the latest unstable. They haven't updated in like 5 months, and there are pretty big changes since the latest stable...

---

### Post by zealibib slaughter on 2011-05-25
now you need gtkspell so 
```

[FONT=Courier New]sudo apt-get install python-gtkspell [/FONT]
[FONT=Courier New]
```[/FONT]

[FONT=Courier New]and you need gcrypt[/FONT]
[FONT=Courier New]```
[/FONT]
[FONT=Courier New]sudo apt-get install gcrypt[/FONT]
[FONT=Courier New]
```[/FONT]
[FONT=Courier New]that should have you fixed up if not post back with any problems.[/FONT]

---

### Post by dFlyer on 2011-05-25
Information off the Lifeograph wiki

Latest stable version of Lifeograph is 0.6.4 (Released: 12/27/2010). This 

is the fifth stable release in 0.6.X series.
It has the latest translations. Users of previous versions should definitely upgrade to this one.
[http://launchpad.net/lifeograph/0.6/0.6.4](http://launchpad.net/lifeograph/0.6/0.6.4)

Latest unstable version is 0.7.2 (Released: 12/12/2010). This is a beta release so be careful while using it.
[http://launchpad.net/lifeograph/trunk/0.7.2](http://launchpad.net/lifeograph/trunk/0.7.2)

Launchpad site:

[http://launchpad.net/lifeograph](http://launchpad.net/lifeograph)
PPA:

Ubuntu users can add Lifeograph PPA at Launchpad to their repositories list:
[https://launchpad.net/~dmxe/+archive](https://launchpad.net/~dmxe/+archive)
UNSTABLE PPA (BE CAREFUL WHILE USING THIS):

[https://launchpad.net/~dmxe/+archive/lifeograph-unstable](https://launchpad.net/~dmxe/+archive/lifeograph-unstable)

If your going to install a beta program which the site advises against at least use the ppa. That way you will get the update to the beta program. My advise is to stay with the stable version in the ubuntu archives.

---

### Post by .psd on 2011-05-25
ngrlvr@ngrlvr-EX58-UD3R:~/Downloads/lifeograph-0.7.2$ sudo apt-get install python-gtkspell
[sudo] password for ngrlvr: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
python-gtkspell is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
ngrlvr@ngrlvr-EX58-UD3R:~/Downloads/lifeograph-0.7.2$ sudo apt-get install gcrypt
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package gcrypt

---

### Post by zealibib slaughter on 2011-05-25
ok try sudo apt-get install libgtkspell-2.0-dev and I will google gcrypt but I could have sworn that was the right package name.

---

### Post by .psd on 2011-05-25
Hmm that didn't work so I found something close in synaptec, then tried ./waf config and it says gtkspell-2.0 found, now:

ngrlvr@ngrlvr-EX58-UD3R:~/Downloads/lifeograph-0.7.2$ ./waf configure
Checking for program g++ or c++          : /usr/bin/g++ 
Checking for program cpp                 : /usr/bin/cpp 
Checking for program ar                  : /usr/bin/ar 
Checking for program ranlib              : /usr/bin/ranlib 
Checking for g++                         : ok  
Checking for gtkmm-2.4 >= 2.16           : yes 
Checking for gtkspell-2.0                : yes 
Checking for library gcrypt              : not found 
/home/ngrlvr/Downloads/lifeograph-0.7.2/wscript:62: error: the configuration failed (see '/home/ngrlvr/Downloads/lifeograph-0.7.2/build/config.log')

so close...

---

### Post by zealibib slaughter on 2011-05-25
try for gcrypt in synaptic, I know its in there somewhere because I've got it installed.
then that should be it post back and let me know what happens.

---

### Post by .psd on 2011-05-25
Was already on top of that ;)

Done, but it still says library gcrypt not found.

Check synaptec for "gcrypt" only one thing shows up and that's what I installed...

---

### Post by oldos2er on 2011-05-25
.psd, try ```
sudo apt-get build-dep lifeograph
``` then retry ```
.waf configure
```

---

### Post by zealibib slaughter on 2011-05-25
if what oldos2er said doesn't work try 
```

sudo apt-get install libgcrypt11

```

---

### Post by .psd on 2011-05-25
Getting hotter!!

Checking for program g++ or c++          : /usr/bin/g++ 
Checking for program cpp                 : /usr/bin/cpp 
Checking for program ar                  : /usr/bin/ar 
Checking for program ranlib              : /usr/bin/ranlib 
Checking for g++                         : ok  
Checking for gtkmm-2.4 >= 2.16           : yes 
Checking for gtkspell-2.0                : yes 
Checking for library gcrypt              : yes 
Checking for program msgfmt              : /usr/bin/msgfmt 
Checking for program intltool-merge      : not found 
/home/ngrlvr/Downloads/lifeograph-0.7.2/wscript:63: error: The program intltool-merge (intltool, gettext-devel) is mandatory!

EDIT: No wonder this is beta!

---

### Post by zealibib slaughter on 2011-05-25
check synaptic for intltool if not then we may have to install from source.

---

### Post by .psd on 2011-05-25
'configure' finished successfully (0.259s)


*crosses fingers* trying the last 2 steps will post back

---

### Post by zealibib slaughter on 2011-05-25
cool, that should be the end of our dependency hell.:)

---

### Post by .psd on 2011-05-25
The first two steps worked, then:

ngrlvr@ngrlvr-EX58-UD3R:~/Downloads/lifeograph-0.7.2$ /.waf install
bash: /.waf: No such file or directory

---

### Post by zealibib slaughter on 2011-05-25
post output of ls

---

### Post by .psd on 2011-05-25
AUTHORS      build    icons         lifeograph.desktop     makefile      NEWS  README  ui   wscript
backgrounds  COPYING  lifeograph.1  lifeograph.desktop.in  makefile.old  po    src     waf

---

### Post by zealibib slaughter on 2011-05-25
ok run the install again
```
./waf install
```
and copy/paste terminal output here either it isnt finding the directory or its not finding a file.

---

### Post by LordNeo on 2011-05-25
> **.psd said:**
> The first two steps worked, then:

ngrlvr@ngrlvr-EX58-UD3R:~/Downloads/lifeograph-0.7.2$ /.waf install
bash: /.waf: No such file or directory
it's ./waf install, not /.waf install (dot before slash)

Just to clear some stuff, latest version doesn't mean "better version"
If you are new to Ubuntu, try to stick to the versions in the repository, because those are stables, tested and will automatically fix any dependence issues you may have.

If you want to try experimental versions, first try to get the "ppa way" that is just a couple of commands to add those sources and the program. In this particular case just open a terminal and type:

sudo add-apt-repository [B]ppa:dmxe/lifeograph-unstable
[/B]
then:
sudo apt-get update

then
sudo apt-get install lifeograph

That's all, it will install the unstable version (0.7.2)

If you want the less unstable version replace:

**ppa:dmxe/lifeograph-unstable**

with:

**ppa:dmxe/ppa**

it will install the version 0.6.3

Else, just install the stable version from the repository

---

### Post by .psd on 2011-05-25
Copied from where ./waf build completed, the last two ./waf installs were the one you told me to do just now, and then I repeated it just to see what would happen.

'build' finished successfully (8.706s)
ngrlvr@ngrlvr-EX58-UD3R:~/Downloads/lifeograph-0.7.2$ /.waf install
bash: /.waf: No such file or directory
ngrlvr@ngrlvr-EX58-UD3R:~/Downloads/lifeograph-0.7.2$ ls
AUTHORS      build    icons         lifeograph.desktop     makefile      NEWS  README  ui   wscript
backgrounds  COPYING  lifeograph.1  lifeograph.desktop.in  makefile.old  po    src     waf
ngrlvr@ngrlvr-EX58-UD3R:~/Downloads/lifeograph-0.7.2$ ./waf install
Waf: Entering directory `/home/ngrlvr/Downloads/lifeograph-0.7.2/build'
Waf: Leaving directory `/home/ngrlvr/Downloads/lifeograph-0.7.2/build'
Cannot create folder '/usr/local/share/icons/hicolor/16x16/apps' (original error: [Errno 13] Permission denied: '/usr/local/share/icons/hicolor/16x16')
ngrlvr@ngrlvr-EX58-UD3R:~/Downloads/lifeograph-0.7.2$ ./waf install
Waf: Entering directory `/home/ngrlvr/Downloads/lifeograph-0.7.2/build'
Waf: Leaving directory `/home/ngrlvr/Downloads/lifeograph-0.7.2/build'
Cannot create folder '/usr/local/share/icons/hicolor/16x16/apps' (original error: [Errno 13] Permission denied: '/usr/local/share/icons/hicolor/16x16')

---

### Post by zealibib slaughter on 2011-05-25
nice catch @lordNeo I didn't notice the reversed slash dot.

---

### Post by zealibib slaughter on 2011-05-25
> 
ngrlvr@ngrlvr-EX58-UD3R:~/Downloads/lifeograph-0.7.2$ ./waf install
Waf: Entering directory `/home/ngrlvr/Downloads/lifeograph-0.7.2/build'
Waf: Leaving directory `/home/ngrlvr/Downloads/lifeograph-0.7.2/build'
Cannot create folder '/usr/local/share/icons/hicolor/16x16/apps' (original error: [Errno 13] Permission denied: '/usr/local/share/icons/hicolor/16x16')

 
then you need to do ```
sudo ./waf install 
```

---

### Post by .psd on 2011-05-25
> **zealibib slaughter said:**
> then you need to do ```
sudo ./waf install 
```
Perfect it worked! Except:

Now when I start to type in lifeograph in the ubuntu button (top left) it will bring up lifeograph with the correct icon, listed under applications. However when I click that nothing happens... Attempting to drag that icon to the dock, the dock doesn't accept it.

If this is a beta issue I'll just uninstall it and use the stable... otherwise, does it sound like a typical problem with a known fix?

---

### Post by zealibib slaughter on 2011-05-25
does lifeograph start?
as far as the dock goes I can't help you on that since I haven't tried out unity yet, but there should be a way to add it to the dock as long as the program works.
 
try
```
waf
```
in a terminal

---

### Post by .psd on 2011-05-25
Nevermind. I found the launcher in /usr/local/share/applications/lifeograph.desktop it opens Lifeograph which closes IMMEDIATELY so it looks like it's not opening. Probably a beta issue, I'll uninstall and install latest stable.

Is there an automated way to uninstall this mess?

EDIT: Terminal says it doesn't find the command waf

---

### Post by zealibib slaughter on 2011-05-25
if you want to debug the program then you can cd to /usr/local/share/applications in a terminal and run it in terminal by typing lifeograph.desktop
 
If not you should be able to install via synaptic and that will overwrite everything without having to uninstall.

---

### Post by .psd on 2011-05-25
> **zealibib slaughter said:**
> if you want to debug the program then  you can cd to /usr/local/share/applications in a terminal and run it in  terminal by typing lifeograph.desktop
 
If not you should be able to install via synaptic and that will overwrite everything without having to uninstall.
Then it looks like our work here is done. Thank you so much man we've been on this for hours!

Even though it doesn't work (super gay) I still learned and am super thankful!!

Conclusion: going to install latest stable through Synaptec.

Thanks everyone!

(If there's a way to give points or kudos or thanks or whatever, let me know)

---

### Post by zealibib slaughter on 2011-05-25
any time man. at least you learned how to install from source.

---

### Post by .psd on 2011-05-25
Ugh.

I installed the latest stable from source. Even rebooted. The launcher is located in a different area, and it doesn't even make the application flash open for a second like the beta did, although I can drag the "stable" icon to the dock...

Still I think this issue is solved, I'll figure something out as far as getting the program to actually work ;)

---

### Post by LordNeo on 2011-05-25
try to execute lifeograph from a console, that would give you some kind of output, letting you know why it crashed.

---

### Post by .psd on 2011-05-25
Any idea how? It's in /usr/local/share/applications, and it's a .desktop file.

---

### Post by LordNeo on 2011-05-25
> **.psd said:**
> Any idea how? It's in /usr/local/share/applications, and it's a .desktop file.
open an empty terminal and just type "lifeograph"

---

