---
title: "TNEF Messages"
date: 2011-08-28
forum: General Help
---

### Post by jwhudgins on 2011-08-28
I use Evolution for my mail with no problems until now.  As of recently (either by an automatic update or happenstance) Microsoft Office attachments (.XLS, etc.) sent to me via email are now being perceived as a winmail.dat file (TNEF attachment).  Now I was receiving these files just fine until just recently.

Any ideas as to how this might have happened?

I did a forum search for this topic with the latest info dating back in 2010.  With the rapid changes that take place in this circle, certainly there is more up-to-date information available as how to remedy this situation.

Note that I am somewhat of a n00b to this circle, so please, be gentle.  :)

Any help will be _greatly_ appreciated.

---

### Post by jwhudgins on 2011-08-28
Ok, I found a solution [here]("http://www.askmeaboutlinux.com/?p=1478"), but has anyone tried this?  Any suggestions before I give it a shot?

--

Microsoft Outlook, at times, uses  a TNEF format that sends email as a winmail.dat file attachment. This format can be opened by email clients such as Microsoft Outlook, Mozilla  Thunderbird and Claws mail on Windows and Linux. However, if you use the Evolution email client on Linux, you can  still open the attachment indirectly, but you need to perform the  following steps (at least till Evolution comes up with a solution):


 Login as root.
[COLOR=Blue]# *yum install ytnef*[/COLOR]
 
 This installs the ytnef program. Use the following command to get to the contents of the winmail.dat file
[COLOR=Blue]$ *ytnef -F -f . winmail.dat*[/COLOR] 
 

The contents of the email will be extracted to your local folder.  Alternatively, if this is not easy for you to do, just open that email  using your email provider’s web front-end.

---

### Post by jwhudgins on 2011-08-29
Ok, so the above didn't work.  I am not saying that the above information is incorrect, but my lack of experience prevented me from figuring it out.
I ended up using the following commands:

[COLOR=Blue]sudo apt-get install yum[/COLOR]

This installed 'yum' but didn't appear to have any relationship with ytnef and couldn't get the ytnef command to work.

Shot in the dark...

[COLOR=Blue]sudo apt-get install tnef[/COLOR]

This installed, but what exactly?  Executed the command with the following switch...

[COLOR=Blue]sudo tnef -f . winmail.dat[/COLOR]  (this did not work at all, incorrect syntax, etc.)

So as to not leave a bunch of stuff on my system that I don't even know what is, I decided to uninstall.

[COLOR=Blue]sudo apt-get remove yum
sudo apt-get remove tnef[/COLOR]

Back to square 1.  What perplexes me is that I _*used*_ to be able to receive .XLS files without any issue, and not until recently that it gets translated into a winmail.dat file.  Go figure.

---------

Edit:
[COLOR=Olive]I did go back and install tnef and used it to unpack my winmail.dat file and it worked like a champ.  Cumbersome when you have to do this with a bunch of files, but it will work in a pinch.[/COLOR]

---

### Post by jwhudgins on 2011-08-30
The experimental plug-in..

[https://launchpad.net/ubuntu/oneiric/+package/evolution-plugins-experimental](https://launchpad.net/ubuntu/oneiric/+package/evolution-plugins-experimental)

Is this plug-in part of the current Evolution distribution included with Ubuntu 11.04, OR is this something I need to download separately?  For whatever reason there are no dates to show how old these versions are.  This is why I started this thread as info regarding this topic seemed to cease in 2010.

This is the one I think I should download for my system...

**evolution-plugins-experimental 3.1.5-0ubuntu2 in i386 (Release)**

Is this old information?  Am I chasing a rabbit?  Someone please chime in. :(

---

### Post by jwhudgins on 2011-09-01
Ok, so I downloaded the file (evolution-plugins-experimental_3.1.5-0ubuntu2_i386.deb) and tried to install via the Software Center only for it to prevent the installation.

**Dependency is not satisfiable:  libcamel-1.2-28(>=3.1)**  *insert explicative here

If I were to install it via a command line, what directory would I install it to?  What would my command be?

Any help would be greatly appreciated.

---

### Post by Slim Odds on 2011-09-01
There is no reason to use "sudo" with tnef.

Just "tnef -f winmail.dat" should work just fine.

I haven't used this in ages, but I did once a long time ago and it worked fine.

---

### Post by Slim Odds on 2011-09-01
> **jwhudgins said:**
> Ok, I found a solution [here]("http://www.askmeaboutlinux.com/?p=1478"), but has anyone tried this?  Any suggestions before I give it a shot?

--

Microsoft Outlook, at times, uses  a TNEF format that sends email as a winmail.dat file attachment. This format can be opened by email clients such as Microsoft Outlook, Mozilla  Thunderbird and Claws mail on Windows and Linux. However, if you use the Evolution email client on Linux, you can  still open the attachment indirectly, but you need to perform the  following steps (at least till Evolution comes up with a solution):


 Login as root.
[COLOR=Blue]# *yum install ytnef*[/COLOR]
 
 This installs the ytnef program. Use the following command to get to the contents of the winmail.dat file
[COLOR=Blue]$ *ytnef -F -f . winmail.dat*[/COLOR] 
 

The contents of the email will be extracted to your local folder.  Alternatively, if this is not easy for you to do, just open that email  using your email provider’s web front-end.

These instructions are for an RPM based linux like Fedora.

Ubuntu is Debian based and uses DEB (.deb files installed with apt-get or synaptic).

See my previous post....

---

