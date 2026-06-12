---
title: "How do I apt-get --download-only a broken package?"
date: 2010-03-01
forum: General Help
---

### Post by sdaau on 2010-03-01
Hi all, 

I'd like to download a deb package which will otherwise not install on my Ubuntu 9.04, because of an "E: Broken packages" error (problem is some mix up of versions on PPAs)

So, then I'd just like to download it, and so I issue:
```

$ sudo apt-get -d install libqt4-scripttools
Some packages could not be installed. ...
The following packages have unmet dependencies:...
E: Broken packages

```which is the same message I get when I try to install... But why??? I am not trying to install in this case, I'm just trying to download? 

So, how do I persuade apt-get to just download that package, and not install it? 

Thanks,
Cheers!

---

### Post by Enigmapond on 2010-03-01
Wouldn't it just be easier to fix the broken package in synaptic and trying again? Just a thought...

---

### Post by sdaau on 2010-03-01
Hi Enigmapond,

Thanks for your response.

> 
Wouldn't it just be easier to fix the broken package in synaptic and  trying again? Just a thought... 	


Well, the question is how do I download the package, not how do I install it. 

The thing is, I have everything running as I want it, however, I also use ppa's ... And now I want to try this software out - and as usually when there is a apt-get conflict, I simply download the debs, unpack them, and keep putting executables and libraries together until the program starts working :) 

So, if I try to "fix the broken package in synaptic", the only thing conceivable to 'fixing' in my mind, is to actually remove all the programs I have that *are* working (which depend on libraries that conflict with the software I want to try out), in order to try a different one. And then remove that different one should I not like it, and reinstall the old software.

So I would say - no, it is not easier to "fix" the broken package in synaptic.

But back on topic - I'd just like to have a download link for a particular .deb; I could, say, do: 
```

$ apt-cache -f -a show libqt4-scripttools | grep Filename
Filename: pool/main/q/qt4-x11/libqt4-scripttools_4.5.1-1ubuntu4~ppa1~jaunty1_i386.deb
Filename: pool/main/q/qt4-x11/libqt4-scripttools_4.5.0-0ubuntu4.3_i386.deb
Filename: pool/main/q/qt4-x11/libqt4-scripttools_4.5.0-0ubuntu4_i386.deb

```

If it was a vanilla version I needed (say 4.5.0-0ubuntu4.3_i386.deb), no problem - I can just prepend, say, "http://mirrors.kernel.org/ubuntu/" to what is listed under Filename, and all done. 

But I need the download link for "libqt4-scripttools_4.5.1-1ubuntu4~ppa1~jaunty1_i386.deb" which is obviously from a PPA, and I have no idea which one - hence I do not know what URL to prepend to the otherwise very helpful Filename.. 

Well, hope this can get solved eventually ..
Cheers !

---

### Post by sgosnell on 2010-03-01
Google shows it to be in ppa.launchpad.net/freshmedia/ppa/ubuntu/dists/jaunty/.../Packages

---

### Post by Yannick Le Saint kyncani on 2010-03-01
Use aptitude : aptitude download xxx

---

### Post by sdaau on 2010-03-02
Hi guys, 

Thanks for the responses!

> Google shows it to be in  ppa.launchpad.net/freshmedia/ppa/ubuntu/dists/jaunty/.../PackagesI eventually ended up doing this - but say you had to find dependencies as well; how appealing is pasting 10s of package names into search engine and clicking on results until you find the right one? :) 

Besides, the system itself downloads those packages from somewhere - why shouldn't I have easy access to a download link?


> Use aptitude : aptitude download xxx     Thanks - this seems to be the answer. This is what I am doing:
```

$ aptitude -V -vvvv show libqt4-scripttools | grep -i "version\|archive\|filename"
Version: 4.5.1-1ubuntu4~ppa1~jaunty1
Filename: pool/main/q/qt4-x11/libqt4-scripttools_4.5.1-1ubuntu4~ppa1~jaunty1_i386.deb
Archive: <NULL>
Version: 4.5.0-0ubuntu4.3
Filename: pool/main/q/qt4-x11/libqt4-scripttools_4.5.0-0ubuntu4.3_i386.deb
Archive: jaunty-updates
Version: 4.5.0-0ubuntu4.3
Filename: pool/main/q/qt4-x11/libqt4-scripttools_4.5.0-0ubuntu4.3_i386.deb
Archive: jaunty-security
Version: 4.5.0-0ubuntu4
Filename: pool/main/q/qt4-x11/libqt4-scripttools_4.5.0-0ubuntu4_i386.deb
Archive: jaunty

```And then, say I wanted to download libqt4-scripttools_4.5.0-0ubuntu4.3_i386.deb, I would do: 
```

$ aptitude -t jaunty-updates download libqt4-scripttools
...
Get:1 http://us.archive.ubuntu.com jaunty-updates/main libqt4-scripttools 4.5.0-0ubuntu4.3 [220kB]
Fetched 220kB in 0s (412kB/s)        

```meaning - I should specify "Archive" under "-t" parameter of aptitude, in order to choose a specific version. Notice, however, I do *not* get a full download link. 

If I do not use the "-t" argument, then the first package in list is downloaded (in this case, the PPA version): 
```

$ aptitude download libqt4-scripttools
...
Get:1 http://ppa.launchpad.net jaunty/main libqt4-scripttools 4.5.1-1ubuntu4~ppa1~jaunty1 [220kB]
Fetched 220kB in 0s (316kB/s)       

```Now, the interesting part here, is that the 'default' package (first in show list) actually has "Archive: <NULL>" as it is from a PPA. 

So my question here is - say aptitude shows *two* PPA versions for a package; assuming both of them will have "Archive: <NULL>", how can I specify which one I want downloaded (or, as an alternative, how can I obtain their full download URL's) ...

Thanks for all the help, 
Cheers!

---

### Post by Yannick Le Saint kyncani on 2010-03-02
No idea how to get the full package url.

Aptitude will always download the package that gets installed, meaning the one with the higher version number and the first repo if two repos can offer the highest version number.

You can specify which package version you want to download if you want but this won't give you a download url. I don't know if you can specify a repo (there should not be any need to do that).

Example downloading a specific version :

/home/kyncani/tmp/my/ > ls
/home/kyncani/tmp/my/ > apt-cache policy avidemux
avidemux:
  Installed: 1:2.5.1+repack-0ubuntu2.1
  Candidate: 1:2.5.1+repack-0ubuntu2.1
  Version table:
 *** 1:2.5.1+repack-0ubuntu2.1 0
        500 [http://fr.archive.ubuntu.com](http://fr.archive.ubuntu.com) karmic-updates/multiverse Packages
        100 /var/lib/dpkg/status
     1:2.5.1+repack-0ubuntu2 0
        500 [http://fr.archive.ubuntu.com](http://fr.archive.ubuntu.com) karmic/multiverse Packages
/home/kyncani/tmp/my/ > aptitude download avidemux
Reading package lists... Done
Building dependency tree
Reading state information... Done
Reading extended state information
Initializing package states... Done
Get:1 [http://fr.archive.ubuntu.com](http://fr.archive.ubuntu.com) karmic-updates/multiverse avidemux 1:2.5.1+repack-0ubuntu2.1 [940kB]
Fetched 940kB in 1s (659kB/s)
/home/kyncani/tmp/my/ > ls
avidemux_1%3a2.5.1+repack-0ubuntu2.1_amd64.deb
/home/kyncani/tmp/my/ > aptitude download avidemux=1:2.5.1+repack-0ubuntu2
Reading package lists... Done
Building dependency tree
Reading state information... Done
Reading extended state information
Initializing package states... Done
Get:1 [http://fr.archive.ubuntu.com](http://fr.archive.ubuntu.com) karmic/multiverse avidemux 1:2.5.1+repack-0ubuntu2 [939kB]
Fetched 939kB in 1s (668kB/s)
/home/kyncani/tmp/my/ > ls
avidemux_1%3a2.5.1+repack-0ubuntu2.1_amd64.deb  avidemux_1%3a2.5.1+repack-0ubuntu2_amd64.deb
/home/kyncani/tmp/my/ >

---

### Post by sgosnell on 2010-03-02
You installed the ppa, so you presumably know the url from that.  You can't expect Ubuntu to keep track of every ppa you install manually.  That's your responsibility.  When you install ppa's, make a note of them somewhere so you can recall the information when you need it.

---

### Post by sdaau on 2010-03-09
Hi guys, 

Thanks for the responses!

First, a quick summary - I originally wanted to download a .deb from a given package and version, where the 'official' apt-get tool failed due to dependency problems. Thus, I was either looking for another tool that will download the package - or if no such tool is found, a tool retrieving a download link for a given package. 

Turns out 
```

aptitude -t <<archive-name>> download 

```works quite fine to download 'official' packages that have an archive name. 

A secondary problem appears with this, since PPA archives actually do not have an archive name assigned - which is all fine as long as the PPA version is the "latest" and thus "default" for installation; but otherwise there will be no way to specify the PPA version for downloading (especially if it turns out that there are two PPA versions in 'aptitude show', if that is at all possible) . (note I tried to change the topic title to reflect this, however it seems the original thread title cannot be changed) 

Also, I have said earlier
> 
Notice, however, I do *not* get a full download link. 
 lets note that I do get parts of the download link if I execute 'aptitude .. download': ```
$ mylink=$(aptitude download libqt4-scripttools | grep Get)
$ echo $mylink
Get:1 http://ppa.launchpad.net jaunty/main libqt4-scripttools 4.5.1-1ubuntu4~ppa1~jaunty1 [220kB]
$ echo $mylink | cut -d " " -f 1
Get:1
$ echo $mylink | cut -d " " -f 2
http://ppa.launchpad.net
$ echo $mylink | cut -d " " -f 3
jaunty/main
$ echo $mylink | cut -d " " -f 4
libqt4-scripttools
$ echo $mylink | cut -d " " -f 5
4.5.1-1ubuntu4~ppa1~jaunty1

```However, this particular deb refers to [ppa.launchpad.net/freshmedia/ppa/ubuntu/pool/main/q/qt4-x11/libqt4-scripttools_4.5.1-1ubuntu4~ppa1~jaunty1_i386.deb]("http://ppa.launchpad.net/freshmedia/ppa/ubuntu/pool/main/q/qt4-x11/libqt4-scripttools_4.5.1-1ubuntu4%7Eppa1%7Ejaunty1_i386.deb")
 ... And since I can retrieve the "Filename: pool/main/q/qt4-x11/libqt4-scripttools_4.5.1-1ubuntu4~ppa1~jaunty1_i386.deb" by grepping through 'aptitude show ..', I'm still missing the "/freshmedia/ppa/ubuntu/" part for a full URL. 

> **Yannick Le Saint kyncani said:**
> No idea how to get the full package url.
Aptitude will always download the package that gets installed, meaning the one with the higher version number and the first repo if two repos can offer the highest version number.

You can specify which package version you want to download if you want but this won't give you a download url. I don't know if you can specify a repo (there should not be any need to do that).


Thanks for the tips. Well, the whole thing with the download link is that it would be nice to have it, if the official tools fail - as then wget or similar can be used (but also nice for building scripts and such); but as long as the tools get me the .deb I want, I can live without the link :) 

> **sgosnell said:**
> You installed the ppa, so you presumably know the url from that. 

I'd like to disagree with this statement - quite often, I install something from a PPA, then forget about it completely; then after 6 months I look at /etc/apt/sources.list and decide I should clean up, and of course, delete those apt lines that were the sources of the packages :) 

> **sgosnell said:**
>  You can't expect Ubuntu to keep track of every ppa you install manually. 

I agree with that, as long as it is my fault for deleting the source line in /etc/apt/sources.list. 

However, here I'm looking for the download link of a package that the system *already* recognizes *and* downloads: 
```

$ aptitude download libqt4-scripttools
...
Get:1 http://ppa.launchpad.net jaunty/main libqt4-scripttools 4.5.1-1ubuntu4~ppa1~jaunty1 [220kB]
Fetched 220kB in 0s (316kB/s)

```The system just download and fetched a file, from a PPA - from **where**? If the system knows the download link, why shouldn't I? I don't want to go to a search engine (or fire up Wireshark) to find a particular package link, every time I run into this kind of problem :) 

Thanks again for the comments and lively discussion ! :D

Cheers!

---

### Post by sgosnell on 2010-03-09
Well, I'm just playing devil's advocate here.  If you install a ppa, the developers could assume that you have made a note of the address, and they aren't responsible for keeping track of it.  There are lots of ppas, few of which are maintained offically.  They can be used by people who use any distro, not just Ubuntu or Fedora or whatever.  I don't know of any distro which keeps track of all this.  It might be convenient for you, but it's not for the developers.  Good luck with getting it included.

---

### Post by sdaau on 2010-03-09
Hi sgosnell, 

Thanks for the response - and for playing the devil's advocate :) 

To defend (and clarify) my position - I am not asking for the developers to keep track of what I install; I ask to know the link of those packages that the system *already* keeps track of. 

I was thinking of writing a longer discourse on why this should be possible, however, reading the man apt-get and man aptitude finally pointed to a solution :) Namely, the information about packages is kept in var/lib/apt/lists/ - in filenames that *already contain the URL* in their names :) 

Thus, one could run the following script: 
```

PCKGNAME="libqt4-scripttools" # package name we're searching for 
for file in $(find /var/lib/apt/lists/* -type f) 
do  
    match=$(grep --no-messages "Package: ${PCKGNAME}\|Filename: \(.*\)${PCKGNAME}*" $file) 
    if [ -n "$match" ]; then  
        # echo "$match";  
        ma=($match) # convert string match to array ma 
        echo "${ma[0]} ${ma[1]}" # writes out Package: name.. 
        # echo ${ma[2]} # just Filename: 
        # echo $file;  # filename in /var/lib/apt/lists/ which contains URL 
        urlbase=${file#/var/lib/apt/lists/} 
        urlb=$(echo $urlbase | sed "s/_/\//g") # replace _ with / 
        urlbb=$(echo $urlb | sed "s/dists\(.*\)//g") # get rid of all after /dists .. 
        #echo ${ma[3]} # URL path to deb file  
        deblink="http://${urlbb}${ma[3]}" 
        echo $deblink; 
        echo;  
    fi;  
done 

```and then by running it, we get 
```

Package: libqt4-scripttools
http://us.archive.ubuntu.com/ubuntu/pool/main/q/qt4-x11/libqt4-scripttools_4.5.0-0ubuntu4_i386.deb

Package: libqt4-scripttools
http://us.archive.ubuntu.com/ubuntu/pool/main/q/qt4-x11/libqt4-scripttools_4.5.0-0ubuntu4.3_i386.deb

Package: libqt4-scripttools
http://ppa.launchpad.net/freshmedia/ppa/ubuntu/pool/main/q/qt4-x11/libqt4-scripttools_4.5.1-1ubuntu4~ppa1~jaunty1_i386.deb  <====== HERE !!!!!!!!!!!

Package: libqt4-scripttools
http://security.ubuntu.com/ubuntu/pool/main/q/qt4-x11/libqt4-scripttools_4.5.0-0ubuntu4.3_i386.deb

```and so the download link has been obtained - and as long as this is how the policy is, it should work for multiple ppa's containing a reference to a package (which is what concerned me). 

So, problem solved - and no need to nag the devs :D

Thanks again for the fruitful discussion,
Cheers!

---

