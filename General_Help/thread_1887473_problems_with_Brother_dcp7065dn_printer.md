---
title: "problems with Brother dcp7065dn printer"
date: 2011-11-27
forum: General Help
---

### Post by Ralph Boland on 2011-11-27
I am running Ubuntu 11.04 on a standard box.
I have been trying print to a Brother dcp7065dn printer without success.
I first fetched and attempted to install the lpr driver from the Brother 
website.  This failed.

I ran:
   dpkg -i -force-all dcp7065dnlpr-2.1.0-1.i386.deb
and got:
   Unpacking replacement dcp7065dnlpr-2.1.0-1.i386 ...
   start: Unknown job: lpd
   dpkg: warning: subprocess old post-removal script returned error exit  
   status 1
   dpkg - trying script from the new package instead ...
   start: Unknown job: lpd
   dpkg: error processing dcp7065dnlpr-2.1.0-1.i386.deb (--install):
   subprocess new post-removal script returned error exit status 1
   start: Unknown job: lpd
   dpkg: error while cleaning up:
   subprocess new post-removal script returned error exit status 1
   Errors were encountered while processing:
   dcp7065dnlpr-2.1.0-1.i386.deb

I then tried:
   sudo dpkg -P dcp7065dnlpr-2.1.0-1.i386

and got:
   dpkg: warning: there's no installed package matching dcp7065dnlpr-2.1.0-1.i386

If I try:
    sudo apt-get install -f
I get:
    Preparing to replace dcp7065dnlpr 2.1.0-1 (using
    .../dcp7065dnlpr-2.1.0-1.i386.deb) ...
    Unpacking replacement dcp7065dnlpr ...
    start: Unknown job: lpd
    dpkg: warning: subprocess old post-removal script returned error exit status 1
    dpkg - trying script from the new package instead ...
    start: Unknown job: lpd
    dpkg: error processing
    /home/rocky/MyDebs/./OLD/dcp7065dnlpr-2.1.0-1.i386.deb (--unpack):
    subprocess new post-removal script returned error exit status 1
    start: Unknown job: lpd
    dpkg: error while cleaning up:
    subprocess new post-removal script returned error exit status 1
    Errors were encountered while processing:
    /home/rocky/MyDebs/./OLD/dcp7065dnlpr-2.1.0-1.i386.deb
    E: Sub-process /usr/bin/dpkg returned an error code (1)

If I start up  Synaptic Package Manager and select Brother and then package:
     dcp7065dnlpr
      (installed version: 2.1.0-1)
      (latest version 2.1.0-1)
     (Description Brother DCP-7065DN LPR driver)

and then try installs, reinstalls, removes, or complete removals I run into 
similar problems.

On advice from someone in my local LUG I eventually I was able to get the command:
   sudo dpkg -P dcp7065dnlpr-2.1.0-1.i386

to work by editing the files postinst and postrm in  /var/lib/dpkg/info/ 
and commenting out commands like:
       /etc/init.d/lpd restart

I then tried:
    sudo  /etc/init.d/lpd restart
and got:
    Since the script you are attempting to invoke has been converted  to an
    Upstart job, you may also use the stop(8) and then start(8) utilities,
    e.g. stop lpd ; start lpd. The restart(8) utility is also available.
    start: Unknown job: lpd

If I try:
     sudo start lpd
I get:
    start: Unknown job: lpd

If while in /etc/inid.d  I do:
   ls -l lpd
I get:
   lrwxrwxrwx 1 root root 16 2011-09-26 13:33 lpd -> /etc/init.d/cups
If I do:
    ls -l cups
I get:
    lrwxrwxrwx 1 root root 21 2011-09-18 02:39 cups ->/lib/init/upstart-job

If while in /lib/init   I do:
    ls -l upstart-job
I get:
   -rwxr-xr-x 1 root root 2182 2011-04-20 16:45 upstart-job
So this file exists.  It is a shell script.
I am no expert with shell scripts but my interpretation of the
shell script is that it runs:
>>    start lpd.
which explains its output.

I don't know how to fix this problem so I went back to the Brother 
web site and downloaded the cups version of the driver for the printer.
This installed without problems.
I don't know if I am then supposed to start cups somehow or if it is started
with the install.

In any case I then tried to add the printer (system/administration/printing).
I tried many times and ways both through by router and through a direct connection
to my printer but nothing worked.  I can't give a clear explanation as to what
I did because am no longer sure.  I currently have 5 printer Icons in the printer
GUI but none of them work and I don't know how to get rid of them.
Note that if I did a database search from the Printer GUI/page my printer driver is
not one of the drivers listed and trying the dcp7045lprdn printer driver
also didn't work.

So here are some questions:

   1)  What is the problem with lpd, should I fix it and if so how?
   2)  Do I need to start cups now that I have it installed?
   3)  Should I uninstall cups and go back to the lpr driver?
   4)  How do I get rid of the icons on the printer GUI page that don't work.
   5)  Are my problems likely to be simplified if I upgrade to Ubuntu 11.10?
   6)  A reinstall seems like overkill but will it help?

Any advice most welcome.

Ralph Boland

---

### Post by kurt18947 on 2011-11-27
I think if it were me I'd open Synaptic, find the installed Brother entries and remove everything including configuration packages.  Are you using the 32 bit or 64 bit version?  If you're using 32 bit you can just double-click the .deb file, you don't need to use the command line.  64 bit requires the "--force-all".  I'm not sure what the difference is but "dpkg -i -force-all dcp7065dnlpr-2.1.0-1.i386.deb" should have been "dpkg -i **--**force-all dcp7065dnlpr-2.1.0-1.i386.deb", two dashes before force-all.  I believe Brother requires the .lpd driver to be installed before the CUPS driver is installed.

Did you look through this before installing?
[http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/before.html#004](http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/before.html#004)
There are references to creating directories/folders before installing.  I have a Brother MFC-6490CW running on 11.04 with no issues.  Many of the entries are not applicable but I run the debian related ones anyway.  If they return something to the effect that "it's already there" then I go onto the next item.  I'm mostly a GUI user but installing Brother printers on 64 bit systems requires command line install.

---

### Post by Ralph Boland on 2011-11-27
> I think if it were me I'd open Synaptic, find the installed Brother
> entries and remove everything including configuration packages. Are you > using the 32 bit or 64 bit version? 

32 bit version as far as I know.

> If you're using 32 bit you can just double-click the .deb file, you
> don't need to use the command line. 64 bit requires the "--force-all".
> I'm not sure what the difference is but "dpkg -i -force-all dcp7065dnlpr-2.1.0-1.i386.deb"
> should have been "dpkg -i --force-all dcp7065dnlpr-2.1.0-1.i386.deb", two dashes before force-all.

I in fact used "--";  my posting had a typo.

> II believe Brother requires the .lpd driver to be installed before the
> CUPS driver is installed.

You are right (but it is .lpr driver) which I discovered on rereading the Brother instructions.
But this doesn't help because I cannot install the lpr driver before the
cups driver do because of the "start lpd" command failure.


> Did you look through this before installing?
> [http://welcome.solutions.brother.com...efore.html#004](http://welcome.solutions.brother.com...efore.html#004)
> There are references to creating directories/folders before installing. 

I went through this again and spotted a directory I needed to create:
      mkdir /var/spool/lpd

However creating this directory did not help with getting "start lpd"
or "restart lpd" to work.

Note that a friend of mine had no trouble getting the printer to work
but he is using kubuntu  11.04 and not  ubuntu 11.04.

Regards and thanks for your help

Ralph Boland

---

### Post by kurt18947 on 2011-11-28
I'm sorry to hear it didn't work out.  I don't think it should matter whether Ubuntu or Kubuntu is being used;  as I understand it Brother recommends command line installs to so one set of instructions works for most or all Linux flavors.  You could try emailing Brother support.  Linux support is email only AFAIK.  I've used it and got a reply after a few days.  I hope you're able to resolve your problem.  

Fair warning.  If you install a Brother printer on 11.10 there are a couple gotchas.  One has to do with USB printing and one has to do with scanning.  I don't recall details without access to my notes but one or both problems are 64 bit issues.

---

