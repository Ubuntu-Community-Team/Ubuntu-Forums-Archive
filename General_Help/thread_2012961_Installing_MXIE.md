---
title: "Installing MXIE"
date: 2012-06-30
forum: General Help
---

### Post by gkahacho on 2012-06-30
Hi, I am trying to install application called MXIE from Zultys.com on Ubuntu 12.04 but am having lots of issues with it. eg. when converting the files from .rpm to .deb, I get this warning: Skipping conversion of scripts in package mxieqt4: postinst preinst prerm.

Any help will do.

Has anyone installed MXIE on Ubuntu?

thanks,

gkahacho

---

### Post by BTux on 2012-07-16
What version of MXIE are you trying to install?  Are you running x86 or x64 version of Ubuntu?  I had the same problem and I can send you my converted deb file you if you like :)

---

### Post by gkahacho on 2012-07-16
BTux,

Thanks. Am running on MXIE version 7.0.7 and x86 Ubuntu. Any help will do - I have talked to Zultys - the MXIE vendor and they said that they don't support Ubuntu OS for MXIE.

If you have a step-by-step instruction on how you installed MXIE on your Ubuntu, I would be glad to try it.

Regards,

---

### Post by BTux on 2012-07-17
This is what I did on my x64 Ubuntu.   Since you said you are on x86 you will not need to perform the first apt-get in the list below.  

Open up a terminal then copy each one and press enter after it has been pasted

sudo apt-get install ia32-libs

sudo apt-get install libstdc++5

sudo apt-get install alien

I am running 7.0.2 but this should work the same.  Open up a terminal and in the terminal you need to navigate to where the RPM file is stored (mine is stored in /home/bill/Downloads). Next type:

sudo alien -t mxie-7.0.2-0.i386.rpm 

BUT 

replace the version number with yours.  If you want to be lazy (like me!) I opened nautilus, right clicked on the file, selected rename and just copied the file name. and pasted it in the command line. :-)

This will create mxieqt4-7.0.2.tgz (you number will most likely be different).  Now right click on this file and extract.  It will extract to a new folder called usr.  Open the folder and you'll be in local, then you will have two folders, copy them.

Open terminal and type

sudo nautilus

This will open up nautilus with root access.  Look for filesystem, then /usr/local/ 

Paste the contents in that folder.    

You may need to open up synaptic package manager (sudo apt-get install synaptic) and search for libjpeg then install libjpeg and the dev package also.

Since I am running the x64 OS I also needed to copy a file called libjpeg.so.62 inside the lib folder located inside the Zultys folder that was copied.  Since you are x86 you should not have to copy this file.

In a terminal type sudo mxie then type your password and you should be up & running :-)

I hope this helps out.  Please let me know your results.  I am using MXIE and it works exactly as the Windows version except for the soft phone feature.  Good Luck!

---

### Post by gkahacho on 2012-07-17
I have gone through the entire process as you detailed but am getting this error when I try to launch MXIE:

/usr/local/zultys/bin/mxie: error while loading shared libraries: libcrypto.so.10: cannot open shared object file: no such file or directory.

What am I missing?

thanks:o

---

### Post by gkahacho on 2012-07-17
/usr/local/zultys/bin/mxie: error while loading shared libraries: libcrypto.so.10: cannot open shared object file: No such file or directory.

---

### Post by gandalf3 on 2012-07-17
what kind processor are you using? (64/32 bits? amd/intel?)

---

### Post by BTux on 2012-07-18
You need to install SSL.  Open up your package manager (Synaptic if you followed my previous post) and search libcrypto.  Install SSL (libssl).

Let me know if this helps :D

---

### Post by BTux on 2012-07-18
You can always download those files by doing a simple google search or by following my follow up post in the other thread.

---

### Post by SeijiSensei on 2012-07-18
> **gkahacho said:**
> /usr/local/zultys/bin/mxie: error while loading shared libraries: libcrypto.so.10: cannot open shared object file: No such file or directory.

If this file is running from /usr/local then either you compiled it from source, or you obtained it from some place other than a standard Ubuntu repository.  It's looking for the crypto library that was used when the program was compiled.  (I suspect it's a [Fedora]("http://rpmfind.net/linux/rpm2html/search.php?query=libcrypto.so.10&submit=Search+...&system=&arch=") build.)

On my 12.04 machine, libcrypto functions are provided by /lib/i386-linux-gnu/libcrypto.so.1.0.0.  (On a 64-bit machine the "i386-linux-gnu" directory would be replaced with "x86_64-linux-gnu".)  Sometimes you can avoid missing library problems by creating a symlink to the current version of the library.  In my case I would try:

```

cd /usr/lib
sudo ln -s ../../lib/i386-linux-gnu/libcrypto.so.1.0.0 libcrypto.so.10

```

and see if that works.  If you can't fix this problem, you either need to install an Ubuntu version of the program, or compile a new version from source.

---

### Post by gkahacho on 2012-07-18
Am using a 32 bit machine with Intel Centrino Duo processor.

---

### Post by gkahacho on 2012-07-18
Am using a 32 bit [machine]("http://ubuntuforums.org/showthread.php?t=2012961&page=2#") with Intel Centrino Duo processor.

---

### Post by gkahacho on 2012-07-18
BTux,

I have installed both libssl and libcrypto file using Synaptic Package Manager - but when I launch MXIE, I still get the same error:** error while loading shared libraries: libcrypto.so.10: cannot open shared object file. No such file or directory.**

---

### Post by BTux on 2012-07-18
Run this from a terminal:
 
 sudo apt-get install prelink
  sudo execstack -c /usr/lib/libcrypto.so.10

---

### Post by BTux on 2012-07-18
Can you check this location to see if the file exists?

/lib/i386-linux-gnu

Thanks

---

### Post by gkahacho on 2012-07-18
sudo apt-get install prelink - this install okay
sudo execstack -c/usr/lib/libcrypto.so.10 - I get this error: **sudo: execstack-c/usr/lib/libcrypto.so.10: command not found.**

---

### Post by gkahacho on 2012-07-18
Yes, the file: **/lib/i386-linux-gnu exists and I can navigate to it through the terminal**

---

### Post by BTux on 2012-07-18
Copy the file to /usr/local/zultys/lib dir and try to fire up the program again!

---

### Post by gkahacho on 2012-07-18
I have tried that and it didn't work - still getting the same error.

Q. When I fire up MXIE, this is the PATH shown:** /usr/local/zultys/bin/mxie:** BUT when I navigate through the File System, there is no MXIE directory at the end - should there be a MXIE directory?

---

### Post by BTux on 2012-07-18
I noticed a syntax error one of the previous msgs.  It should be:

sudo execstack -c /usr**/lib/i386-linux-gnu/**libcrypto.so.10

---

### Post by gkahacho on 2012-07-19
Btux,

Still getting the same error.

Another issue I have noticed - the **libcrypto.so.10 file inside the i386-linux-gnu directory has an 'X'** on it - probably its broken. Could this be the problem its not executing? If so, how do I re-install it to correct it?

thanks,

---

### Post by gkahacho on 2012-07-19
Actually when I go to properties for the libcrypto.so.10 file - its type: **link (broken) (inode/symlink)** - how do I fix this?

---

### Post by BTux on 2012-07-19
I found this from another post.  Hopefully the fix is that simple!

"How to fix: Simply delete the broken symlink and recreate it again."

---

### Post by gkahacho on 2012-07-19
I have repaired the broken symlink - but now its asking for others files - it asked for **libssl.so.10** - I installed it - now its asking for **libQt3Support.so.4**

Not sure why the difficulty in getting MXIE installed here -but I will keep on working on it. Any more ideas on how to proceed?

thanks,

---

### Post by BTux on 2012-07-19
Normally it isn't a pain but it does have a lot package requirements.  Using Synaptic (or whatever package manager) you should search for libQT and install it.

---

### Post by gkahacho on 2012-07-19
Installed libQT and finally MXIE launched from the terminal.....

Thanks so much for staying with me on this....am  pretty new on Linux world and trying to get my hands dirty and learn as much as I can.

One more last thing -- is it possible to have the MXIE icon on the desktop and launch it from there by double-clicking on it or I have to always access it from the terminal?

---

### Post by BTux on 2012-07-19
Congrats on getting it running!!! That wasn't too bad looking back on it.

I just found a way to create a link to an app on my desktop.  I am using Kubuntu but it should be similar for you.

Install gksu (sudo apt-get install gksu

Once gksu is installed create a link to an application and use this syntax:

gksudo mxie

In Ubuntu you can make it start with the computer by using that command :)

---

### Post by BTux on 2012-07-19
I have been using MXIE for a while on Linux.  It seems to work better with KDE (in my opinion) and I noticed some minor bugs.  I cannot click on a link in an IM, I need to copy and paste into the browser.  In Ubuntu there is no tray icon, but I haven't tried to get it to work either.  In Kubuntu the tray icon works great!

Hopefully this helps anyone else having a problem installing MXIE but I'll do my best to help out anyone who needs my assistance.  I am not exactly an expert but am learning quite rapidly :P

---

### Post by gandalf3 on 2012-07-19
> **gkahacho said:**
> Am using a 32 bit machine with Intel Centrino Duo processor.
sorry, was looking for a .deb file or something for the required packages..
glad you got the correct packages installed.. :)

---

### Post by gkahacho on 2012-07-19
**Once gksu is installed create a link to an [application]("http://ubuntuforums.org/showthread.php?t=2012961&page=3#") and use this syntax:** - How do I create the link to the application? I have installed [B]gksu.
[/B]
thanks,

---

### Post by gkahacho on 2012-07-19
Thanks, the application is now running and am trying to figure out on how to have it on the desktop and launch it from there instead to always go through the terminal.

---

### Post by stevaa on 2012-07-19
_/usr/local/zultys/bin/mxie: [COLOR=black][ error]("http://www.bot-area.net")[/COLOR] while loading shared libraries: libcrypto.so.10: cannot open  shared object file: No such file or directory._

Can someone maybe help me?

---

### Post by gkahacho on 2012-07-19
Try and run this code and see if it helps:

     Code:
     [B]cd /usr/lib 
    sudo ln -s ../../lib/i386-linux-gnu/libcrypto.so.1.0.0 libcrypto.so.10[/B]

---

### Post by BTux on 2012-07-19
I made this on my Kubuntu laptop and shared this with a co-worker today running Ubuntu 12.04 x86 and it fired up perfect for him.  Right click and save this file to your desktop:

[http://www.atcostnetworksllc.com/linux/MXIE.desktop](http://www.atcostnetworksllc.com/linux/MXIE.desktop)

I will find a way to make one when I'm back in front of an Ubuntu desktop again :)

---

### Post by BTux on 2012-07-19
> **stevaa said:**
> _/usr/local/zultys/bin/mxie: [COLOR=black][ error]("http://www.bot-area.net")[/COLOR] while loading shared libraries: libcrypto.so.10: cannot open  shared object file: No such file or directory._

Can someone maybe help me?

What version of MXIE are you running? What version of Ubuntu and is it x86 or x64?

Regardless of which version, etc did you install libssl?

---

### Post by Arerierug on 2012-07-19
cyECCp  [helpful web]("http://elsa7er.dr-ho.org/entry.php?1512-prada-bags-for-man") rrUSCq  [helpful web]("http://printerforum.co.uk/entry.php?63239-prada-bags-with-celebrities") ooXHNe  [prada backpack]("http://www.incazzati.it/blogs/jefexercehobe/25936-prada-bags-sale-south-africa.html") mjEGWj  [prada men]("http://www.les-survivalistes.com/entry.php?6186-latest-prada-bags-2008") wmEESh  [origin]("http://xtragfx.com/user/gagoNobiowvow/") yxGLSy  [prada tote]("http://www.hitfix.com/motion-captured") cbHAZj  [prada handbags outlet]("http://kythuatbentre.com/entry.php?5210-price-of-prada-bags-in-singapore") cdMRFa  [prada purse]("http://webinitiate.dikshatechnologies.com/entry.php?9190-prada-bags-xxl") grJRIt  [prada outlet]("http://gxsachau.com/entry.php?13144-prada-bags-for-sale-manila") asOJNq  [prada handbag]("http://dacsancactinh.vn/entry.php?30395-cheap-prada-bags-singapore") jvDNAt  [http://hoohi-mach.com/user/enlaneinY/](http://hoohi-mach.com/user/enlaneinY/) rgTISo  [http://www.thebbwforum.com/entry.php?31571-prada-handbags-cheap](http://www.thebbwforum.com/entry.php?31571-prada-handbags-cheap) bvGHAb  [http://diendan.sieutruyenthong.com/entry.php?b=35582](http://diendan.sieutruyenthong.com/entry.php?b=35582) brCFQs  [http://muktie.com/entry.php?26870-prada-bags-russia](http://muktie.com/entry.php?26870-prada-bags-russia) ugLSWm  [http://www.gasheating.co.uk/gas/entry.php?33207-prada-bags-nyc](http://www.gasheating.co.uk/gas/entry.php?33207-prada-bags-nyc) qdRNGq  [http://diendan.tim24h.com/entry.php?18448-prada-bags-for-sale](http://diendan.tim24h.com/entry.php?18448-prada-bags-for-sale) sjJJCa  [http://ediscussion.net/blogs/mypegycle/44009-prada-bags-discount-uk.html](http://ediscussion.net/blogs/mypegycle/44009-prada-bags-discount-uk.html) jnABHx  [http://alluwant.info/entry.php?13516-prada-bags-discounted](http://alluwant.info/entry.php?13516-prada-bags-discounted) avGFTt  [http://bringpoker.com/entry.php?30523-prada-bags-2010](http://bringpoker.com/entry.php?30523-prada-bags-2010) muXNGf  [http://triocycle.com/entry.php?10330-prada-bags-official-website](http://triocycle.com/entry.php?10330-prada-bags-official-website)

---

### Post by Tgersun on 2012-07-20
All that you do, do with your might; things done by halves are never done right. 
R. H. Stoddard, American poet¡¡ 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
--------------------------------------------------------------- 
It's my favorite -----Mulberry Bags 
Mulberry still always hire outstanding local artists and craftsmen to build brand set up a new banner style, a practical, comfortable design and originality, show its brand value. 
The Mulberry outlet([http://www.allmulberrybags.com/](http://www.allmulberrybags.com/)) have many kind of Bags of Mulberry sale!! 
My favorite Bags: 
[Mulberry Alexa Mini Conker Leather Satchel Bag M211](http://www.allmulberrybags.com/mulberry-alexa-mini-conker-leather-satchel-bag-m211---467.html) 
 
 
Unfortunate Lana Del Rey bag aside, [Mulberry Outlet](http://www.allmulberrybags.com/) sent what seemed like dozens of fun, mostly awesome handbags down its runway for Mulberry Fall 2012 over the weekend in London. Not everything worked perfectly (I¡¯m looking at you, trompe l¡¯oeil flaps and buckles), but there were so many options available that it seems as though everyone should be able to find a covetable piece within this collection.

---

### Post by toolfan2k4 on 2012-08-09
BTux, I would greatly appreciate some assistance! I am attempting to run it on Ubuntu 12.04 64-bit. I got myself past the libjpeg errors but now I am stuck on the libcrypto error.

```
/usr/local/zultys/bin/mxie: error while loading shared libraries: libcrypto.so.10: cannot open shared object file: No such file or directory.

```

I have, I believe installed libssl correctly. Could you perhaps give some commands to A. Reinstall the correct package, and B. Any other fixes you can come up with. Also are you using MXIE with a softphone? If so which 3-rd party softphone do you recommend?

---

### Post by BTux on 2012-08-14
Hello toolfan2k4,

I sent a PM with instructions and a link containing an image of what I installed to rid myself of the libcrypto.so error :-)

---

### Post by maitawa on 2012-12-20
I just made symlinks from libcrypto.so.1.0.0 to libcryptoo.so.10 and same for libssl and it works.

I'm using 12.04 amd64 with multilib.
My path for i386 libs is /lib/i386-linux-gnu.
sudo ln -s /lib/i386-linux-gnu/libcrypto.so.1.0.0 /lib/i386-linux-gnu/libcrypto.so.10

An easy way to install i386 version of libjpeg62 is sudo apt-get install libjpeg62:i386

About the rest I just extracted rpm with "alien -g" and copied usr/local/zultys to /usr/local

---

