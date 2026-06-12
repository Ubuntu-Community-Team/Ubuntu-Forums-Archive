---
title: "Draftsight for AMD64"
date: 2011-03-30
forum: General Help
---

### Post by kris kincaid on 2011-03-30
I'm trying to get [Draftsight]("http://www.3ds.com/products/draftsight/download-draftsight/") working on my AMD64 machine, and am running into an error. I followed the procedure posted on [THIS THREAD]("http://ubuntuforums.org/showthread.php?p=10555266#post10555266"), and I get this error:



```
user@ubuntu-AMD64:~/Downloads$ sudo dpkg -i --force-architecture DraftSight.deb
dpkg: warning: overriding problem because --force enabled:
 package architecture (i386) does not match system (amd64)
dpkg: regarding DraftSight.deb containing dassault-systemes-draftsight:i386, pre-dependency problem:
 dassault-systemes-draftsight:i386 pre-depends on libexpat1 (>= 2.0.1-4)
dpkg: error processing DraftSight.deb (--install):
 pre-dependency problem - not installing dassault-systemes-draftsight:i386
Errors were encountered while processing:
 DraftSight.deb
```

The version of libexpat1 I have installed is 2.0.1-7ubuntu3, which is the latest in the repository. I also tried installing the Debian version of libexpat1 ([Debian version 2.0.1-7]("http://packages.debian.org/sid/libexpat1")) and still get the same results as above.

I'm using 11.04 with an AMD64 processor. If anybody has any suggestions, I'm all ears. Thanks :)

---

### Post by killer0007 on 2011-04-12
I have your same problem, I think the problem is the new version of ubuntu.
 I asked for help on the Italian forum (I'm Italian) but also there for the moment no solution

l[http://forum.ubuntu-it.org/index.php/topic,453833.0.html](http://forum.ubuntu-it.org/index.php/topic,453833.0.html)

---

### Post by ampcook on 2011-05-07
I have the same problem with my Acer Aspire 5551-4873 and Ubuntu 11.04 DraftSight can not be installed.

DraftSight run perfect on Ubuntu 10.10 and same Acer (AMD Turion II P520 Dual-Core)

Both Ubuntu 64 bits

---

### Post by Shocker on 2011-05-28
Hi guys!

This is the workaround I used to fix the installation of DraftSight on Ubuntu 11.04 64 bit (Natty Narwhal).


1) I installed the yeoworks-ubuntu-solutions scrip from here:

[http://www.yeoworks.cz.cc/products.php](http://www.yeoworks.cz.cc/products.php)

2) I downloaded the .deb file from the site and moved to the Desktop

3) I used the yeoworks script to convert a 32 deb package in one for the 64 bit architecture.

4) I installed the new .deb package with Ubuntu Software Center

5) Choose to  "ignore" the warnings.

6) The installation ended up without any other problem and now I can run the program :P .

Bye

Shocker

---

### Post by Gemnoc on 2011-05-29
Hi,

This solution is intriguing, but I'm weary of installing such a software (couldn't find any info on the license). From the screen capture listing all the operations possible with this utility, I'm pretty sure all it does is run scripts of existing system commands.

I found this thread on Stackoverflow (a well respected site for technical answers) where multiple people say that converting a 32-bit package to a 64-bit one is only possible by recompiling from the actual sources (which are not available since DraftSight is a free but closed proprietary program):

[http://stackoverflow.com/questions/2529707/how-to-convert-64-bit-deb-file-into-32-bit-deb-file](http://stackoverflow.com/questions/2529707/how-to-convert-64-bit-deb-file-into-32-bit-deb-file)

Looking some more, I found this post on Facebook (of all sites!) that may explain what is done by your utility:

[http://www.facebook.com/note.php?note_id=150046881725890](http://www.facebook.com/note.php?note_id=150046881725890)

Which seems to indicate that the package is not converted, it's just a hack in the control file to change the architecture from i386 to "all".

When I finally manage to upgrade to Natty, I'll try the "manual way".

---

### Post by GGsalas on 2011-05-31
Hi, here is the solution in [english]("http://ubuntuforums.org/showthread.php?p=10555266#post10555266") and [español]("http://wp.me/p9MkM-ly")

---

### Post by Gemnoc on 2011-05-31
Hi GGsalas,

What you posted is the known solution for Ubuntu 10.04 LTS and Ubuntu 10.10 64-bit. It does not work on Ubuntu 11.04.

---

### Post by GGsalas on 2011-06-01
> **Gemnoc said:**
> Hi GGsalas,

What you posted is the known solution for Ubuntu 10.04 LTS and Ubuntu 10.10 64-bit. It does not work on Ubuntu 11.04.

I do it exactly [what I say]("http://wp.me/p9MkM-ly") and works perfectly on Ubuntu 11.04 64 bits

Here my screenshot:

---

### Post by Gemnoc on 2011-06-01
I'll take your word for it! :)

And sorry, I just realized I got confused. I only read your English link, and only the #2 post which was describing the --force architecture way. Now I understand you were talking about the solution in post #8 which extracts the .deb.

I haven't tried to install it on Natty 64-bit yet (just installed it on my laptop this weekend), but I've had many people on my blog complaining they weren't able to install DraftSight anymore after they migrated to Natty.

---

### Post by Gemnoc on 2011-06-05
I just tried the method explained in the Facebook post I linked to in post #5 and it works in Natty!

In my opinion it's actually a lot simpler because you don't need to copy files to the File system or run scripts from there. You can work out of your Home folder. You get a new package that can be installed the usual way with GDebi or the Software Center.

First, in the folder where your DraftSight.deb file is, create a tmp folder.

In the terminal, go to the same directory where your DraftSight.deb file is, then extract it to the tmp folder using dpkg:
```
dpkg-deb -x DraftSight.deb tmp
```
Extract the control files:
```
dpkg-deb &#8212;control DraftSight.deb tmp/DEBIAN
```
Now with Nautilus or your file manager of choice, go to the tmp/DEBIAN folder and edit (with Gedit) the file named "control". On the 5th line, replace the following:
```
Architecture: i386
```
with
```
Architecture: all
```
Save and close. Now repackage the .deb file under a new name (it may take a couple minutes):
```
dpkg -b tmp DraftSight_all.deb
```
And all that is left is to install it.

---

### Post by Gemnoc on 2011-06-06
Well guys, someone on the Ubuntu-fr wiki contributors mailing list gave me a much simpler solution to install DraftSight on Ubuntu 11.04 64-Bit:

```
sudo dpkg -i --force-architecture,depends DraftSight.deb
```

The "depends" option appended to "--force-architecture" treats the depends problems as warnings and makes dpkg continue with the install. You'll get a lot of errors but installation will work. Only the configure step at the end isn't completed, and actually it's just the .desktop file in /usr/local/share/applications that's missing (and the icons in I don't remember what location). Easy enough to add through the Main Menu (Alt+F2 then type "alacarte"), create a new launcher in Applications/Graphics with the following:

Type: Application
Name: DraftSight
Command: "/opt/dassault-systemes/draftsight/bin/DraftSight"
Comment: what you want (original text is "Editing CAD images", which makes no sense!)

And as for the icon, you can find it in

/opt/dassault-systemes/draftsight/mime/pixmaps/48x48/dassault-systemes_draftsight.png

This will make the app available in Dash and then you'll be able to add it to your Unity launcher.

When launched on the console, there are a few Gtk-ERRORs showing up, but the app loads and seems to work fine, although I haven't thoroughly tested it. (these errors could possibly show on 32-Bit Natty too, but I don't have a 32-Bit system to check that out)

BTW if you want to uninstall DraftSight, you need to do it in the terminal since it's not visible in the Software Center or Synaptic:

```
sudo dpkg -r dassault-systemes-draftsight
```

---

### Post by kapz on 2011-06-09
superb workaround Gemnoc!

Thanks a lot for sharing this, worked like a charm.  :)

*Edit*   " Well guys, someone on the Ubuntu-fr wiki contributors mailing list gave  me a much simpler solution to install DraftSight on Ubuntu 11.04 64-Bit:"
Nope that does not work on 11.04 (used to work on 10.10), it keeps complaining that libexpat1 needs to be installed even if it's already been installed. *Edit*

---

### Post by Gemnoc on 2011-06-09
Hi kapz,

I'm confused by your edit. Could you give more details about what you tried? Have you tried launching the software? Even with the bunch of warnings, the software does install.

With the "force-depends" option along with the "force-architecture" one that I wrote about in post #11, I don't have a problem with libexpat1 anymore.

BTW I've been given other things to try in the mailing list, so when I have the time to test I'll follow up here.

---

### Post by GGsalas on 2011-06-15
> **Gemnoc said:**
> I just tried the method explained in the Facebook post I linked to in post #5 and it works in Natty!

In my opinion it's actually a lot simpler because you don't need to copy files to the File system or run scripts from there. You can work out of your Home folder. You get a new package that can be installed the usual way with GDebi or the Software Center.

First, in the folder where your DraftSight.deb file is, create a tmp folder.

In the terminal, go to the same directory where your DraftSight.deb file is, then extract it to the tmp folder using dpkg:
```
dpkg-deb -x DraftSight.deb tmp
```
Extract the control files:
```
dpkg-deb —control DraftSight.deb tmp/DEBIAN
```
Now with Nautilus or your file manager of choice, go to the tmp/DEBIAN folder and edit (with Gedit) the file named "control". On the 5th line, replace the following:
```
Architecture: i386
```
with
```
Architecture: all
```
Save and close. Now repackage the .deb file under a new name (it may take a couple minutes):
```
dpkg -b tmp DraftSight_all.deb
```
And all that is left is to install it.

I do it a deb with your method and[ published the deb in my web]("http://wp.me/p9MkM-mw"). Thanks. [http://wp.me/p9MkM-mw](http://wp.me/p9MkM-mw)

---

### Post by Gemnoc on 2011-06-15
GGsalas,

Remember this is a proprietary piece of software, this is not open source! By posting a modified .deb you are infringing the DraftSight End User License Agreement. You have no right to redistribute this software. I advise you to pull it out before you get in trouble.

(The EULA is located in /opt/dassault-systemes/draftsight/Eula/english/eula.htm)

---

### Post by GGsalas on 2011-06-15
> **Gemnoc said:**
> GGsalas,

Remember this is a proprietary piece of software, this is not open source! By posting a modified .deb you are infringing the DraftSight End User License Agreement. You have no right to redistribute this software. I advise you to pull it out before you get in trouble.

(The EULA is located in /opt/dassault-systemes/draftsight/Eula/english/eula.htm)

Thanks for alert me. It's a pity, but there it is proprietary software. Something to remember. Thanks again.

---

### Post by Gemnoc on 2011-06-15
NP.

It is a pity, and if they had compiled a proper 64-Bit .deb we wouldn't have to jump through hoops to get this working. Let's hope that they release such a package eventually.

---

### Post by GGsalas on 2011-06-15
Now[ i have translated to spanish your instructions]("http://wp.me/p9MkM-mw") to generate the .deb file. 

Thanks again.

---

### Post by knezmej on 2011-07-06
Above solutions does not worked in fresh install of natty narwhale 11.04 64 bit.


  System crashed after attempts: dpkg with force & make deb file for all architectures & trying alien rpm to deb & (re)installation and configuration libraries for i386 (supposed it destroyed system).
I rescue system with reinstallation and configuration libraries for amd64 & update and upgrade system. 
  !Ubuntu 11.04 Natty and DraftSight works!


_You can try install libc6 for i386_ (simultaneously to already installed libc6 for amd64) _from synaptic_. I *guess* it helps in my case.

---

### Post by rephil on 2011-07-26
Grrr.  New update 2011.5.1081 doesn't install well at all.  Did the control file hack last time on 11.04 AMD_64, no problem.  This time it segfaults and lots of wrong ELF class msgs.  Tried other methods, same problem.  Anyone seen this, or did my system go change somewhere in the meantime?

---

### Post by agsansoo on 2011-08-05
I can't seem to get this working ! Please help !


root@rup-64:/home/rup# dpkg -i --force-architecture,depends DraftSight_all.deb 
(Reading database ... 188728 files and directories currently installed.)
Unpacking dassault-systemes-draftsight (from DraftSight_all.deb) ...
access control disabled, clients can connect from any host
access control disabled, clients can connect from any host
/var/lib/dpkg/tmp.ci/preinst: line 21: /var/lib/dpkg/tmp.ci/ShowLicence: No such file or directory
access control enabled, only authorized clients can connect
access control enabled, only authorized clients can connect
dpkg: error processing DraftSight_all.deb (--install):
 subprocess new pre-installation script returned error exit status 127
Errors were encountered while processing:
 DraftSight_all.deb

---

### Post by agsansoo on 2011-08-09
OK I used this:

[http://courira.ca/en/2011/03/draftsight-for-linux-how-to-install-on-ubuntu-64-bit]("http://courira.ca/en/2011/03/draftsight-for-linux-how-to-install-on-ubuntu-64-bit")

Now I'm up and running ! :)

---

### Post by Gemnoc on 2011-08-09
Glad my blog helped. :)

But it doesn't work on Ubuntu 11.04 (Natty) 64-Bit. I discussed the 64-Bit problem with a Dassault representative on [this blog's comment section]("http://worldcadaccess.typepad.com/blog/2011/07/that-free-draftsight-keeps-getting-better.html") (the blog is maintained by a well-known CAD journalist). Unfortunately from what few answers I could get, there won't be a 64-Bit DraftSight package anytime soon.

Interesting numbers, they got 1 million download of DraftSight since last year, and 6% of that on Linux. Considering the Linux version was published a lot later than the Windows and Mac ones, it's all the more significant.

---

### Post by agsansoo on 2011-08-09
> **Gemnoc said:**
> Glad my blog helped. :)

But it doesn't work on Ubuntu 11.04 (Natty) 64-Bit. 

Yes it does ... I'm running Ubuntu 11.04 (Natty) 64-Bit.

root@rup-64:/home/rup# uname -a
Linux rup-64 2.6.38-11-generic #48-Ubuntu SMP Fri Jul 29 19:02:55 UTC 2011 x86_64 x86_64 x86_64 GNU/Linux

root@rup-64:/home/rup# cat /etc/issue
Ubuntu 11.04 \n \l

---

### Post by agsansoo on 2011-08-09
I did install the Draftsight_all.deb, with the above instructions.

[IMG]http://i162.photobucket.com/albums/t257/agsansoo/Screenshot-1.png[/IMG]

---

### Post by dlodge on 2011-08-14
#10 worked for me on 11.04 (Natty) AMD64 - thanks Gemnoc. I needed to manually install:

libdirectfb-extra
libxcb-render-util0
sendmail

I haven't seen the sendmail requirement described in other posts.

---

### Post by Smask on 2011-08-25
I installed the latest DS and I get this response when I run DS:

```
/opt/dassault-systemes/draftsight/bin/DraftSight.bin: error while loading shared
libraries: libGL.so.1: cannot open shared object file: No such file or directory

```I'm running on 64-Bit Natty with xorg-edgers PPA.

---

### Post by BigBopper on 2011-08-30
I've got it installed and running, but am having display issues.  Once the cursor enters the black drafting area, I lose it.  I can create lines and objects, but am doing so blind, which is quite difficult.

Any thoughts?

Al

---

### Post by kacperpl1 on 2011-09-09
I've got it working with chrooted i386 natty, however for just this draftsight it would be an overkill to setup chroot(I've done it for few other apps) so if you have some spare time u can try chroot method.

---

### Post by pbu on 2011-09-10
Hi, 

This may be useful.
I updated from previous version of DraftSight. The program
/opt/dassault-systemes/draftsight/bin/DraftSight
was crashing at startup time.

The solution was to run:
DraftSight -style plastique

---

### Post by chicoff on 2011-09-25
hi, 
there is a problem with some themes, I solved editing the start script:

```
sudo gedit /opt/dassault-systemes/draftsight/bin/DraftSight
```

replace this line:
  ```
"$BINARY" "$@"
```

with this:
```
"$BINARY" -style dummy "$@"
```

and this:
```
"$BINARY"
```

with this:
 ```
"$BINARY" -style dummy
```

---

### Post by Psycho Game on 2011-10-02
> **Smask said:**
> I installed the latest DS and I get this response when I run DS:

```
/opt/dassault-systemes/draftsight/bin/DraftSight.bin: error while loading shared
libraries: libGL.so.1: cannot open shared object file: No such file or directory

```I'm running on 64-Bit Natty with xorg-edgers PPA.

I've had this problem as well.
There's a simple solution to this problem.
first in the terminal go to the bin folder:
cd /opt/dassault-systemes/draftsight/bin
in this folder execute the following command:
sudo ln -s /usr/lib/i386-linux-gnu/mesa/libGL.so.1 libGL.so.1
This will make a symbolic link to where the libGL.so.1 file is located.
After this you should be able to start DraftSight again.

Greetings Psycho Game

---

### Post by mahdiar on 2011-11-19
Thanks to pbu it solved for me !!!
After installation I type below code :

```
/opt/dassault-systemes/draftsight/bin/DraftSight -style plastique 	
```

---

### Post by Smask on 2011-11-29
> **Psycho Game said:**
> I've had this problem as well.
There's a simple solution to this problem.
first in the terminal go to the bin folder:
cd /opt/dassault-systemes/draftsight/bin
in this folder execute the following command:
sudo ln -s /usr/lib/i386-linux-gnu/mesa/libGL.so.1 libGL.so.1
This will make a symbolic link to where the libGL.so.1 file is located.
After this you should be able to start DraftSight again.

Greetings Psycho Game

Well, I made the symlink and promptly got bit by the ancient ia32libs that Ubuntu ships with natty. Ubuntu-xorg-edgers PPA + old ia32libs + ATI Radeon HD5750 = garbled graphics.

---

