---
title: "unable to download programs from software center"
date: 2011-12-28
forum: General Help
---

### Post by Lar87 on 2011-12-28
I am unable to install any programs using the software center or by using the terminal.

If i try install a program using software center it begins to download it and then after a few mins it stops with no error msg.

when i try using the terminal it tells me it could not find the package.

 I am also unable to download any updates for the last 19 days this is what i get when i try update

 laurence@laurence-VPCF12M0E:~$ sudo apt-get update
[sudo] password for laurence: 
Ign [http://archive.canonical.com](http://archive.canonical.com) oneiric InRelease                  
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric InRelease                     
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric InRelease
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-updates InRelease                        
Get:1 [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric Release.gpg [72 B]                      
Get:2 [http://archive.canonical.com](http://archive.canonical.com) oneiric Release.gpg [198 B]                 
Get:3 [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric Release [9,759 B]                       
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-security InRelease                       
  
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric Release.gpg                              
  Unable to connect to 204.188.2
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-updates Release.gpg                      
  Unable to connect to 204.188.2
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-security Release.gpg                     
  Unable to connect to 204.188.21
Err [http://archive.canonical.com](http://archive.canonical.com) oneiric Release                               
  
Ign [http://archive.canonical.com](http://archive.canonical.com) oneiric/partner TranslationIndex              
Err [http://archive.canonical.com](http://archive.canonical.com) oneiric/partner i386 Packages
  Unable to connect to 204.188.21
Err [http://archive.canonical.com](http://archive.canonical.com) oneiric/partner Translation-en_IE
  Unable to connect to 204.188.21
Err [http://archive.canonical.com](http://archive.canonical.com) oneiric/partner Translation-en
  Unable to connect to 204.188.21
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric/main TranslationIndex
Err [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric/main Sources  
  Unable to connect to 204.188.21
Err [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric/main i386 Packages
  Unable to connect to 204.188.21
Err [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric/main Translation-en_IE
  Unable to connect to 204.188.21
Err [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric/main Translation-en
  Unable to connect to 204.188.21
Fetched 10.0 kB in 3min 36s (46 B/s)
Reading package lists... Done
W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/oneiric-security/InRelease](http://archive.ubuntu.com/ubuntu/dists/oneiric-security/InRelease)  

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/oneiric/Release.gpg](http://archive.ubuntu.com/ubuntu/dists/oneiric/Release.gpg)  Unable to connect to 204.188.21

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/oneiric-updates/Release.gpg](http://archive.ubuntu.com/ubuntu/dists/oneiric-updates/Release.gpg)  Unable to connect to 204.188.

W: Failed to fetch [http://archive.canonical.com/ubuntu/dists/oneiric/Release](http://archive.canonical.com/ubuntu/dists/oneiric/Release)  

W: Failed to fetch [http://extras.ubuntu.com/ubuntu/dists/oneiric/main/source/Sources](http://extras.ubuntu.com/ubuntu/dists/oneiric/main/source/Sources)  Unable to connect to 204.188.21

W: Failed to fetch [http://extras.ubuntu.com/ubuntu/dists/oneiric/main/binary-i386/Packages](http://extras.ubuntu.com/ubuntu/dists/oneiric/main/binary-i386/Packages)  Unable to connect to 204.188.21

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/oneiric-security/Release.gpg](http://archive.ubuntu.com/ubuntu/dists/oneiric-security/Release.gpg)  Unable to connect to 204.188.21

W: Failed to fetch [http://archive.canonical.com/ubuntu/dists/oneiric/partner/binary-i386/Packages](http://archive.canonical.com/ubuntu/dists/oneiric/partner/binary-i386/Packages)  Unable to connect to 204.188.21

W: Failed to fetch [http://archive.canonical.com/ubuntu/dists/oneiric/partner/i18n/Translation-en_IE](http://archive.canonical.com/ubuntu/dists/oneiric/partner/i18n/Translation-en_IE)  Unable to connect to 204.188.21

W: Failed to fetch [http://archive.canonical.com/ubuntu/dists/oneiric/partner/i18n/Translation-en](http://archive.canonical.com/ubuntu/dists/oneiric/partner/i18n/Translation-en)  Unable to connect to 204.188.21

W: Failed to fetch [http://extras.ubuntu.com/ubuntu/dists/oneiric/main/i18n/Translation-en_IE](http://extras.ubuntu.com/ubuntu/dists/oneiric/main/i18n/Translation-en_IE)  Unable to connect to 204.188.21

W: Failed to fetch [http://extras.ubuntu.com/ubuntu/dists/oneiric/main/i18n/Translation-en](http://extras.ubuntu.com/ubuntu/dists/oneiric/main/i18n/Translation-en)  Unable to connect to 204.188.21

W: Some index files failed to download. They have been ignored, or old ones used instead.




i have searched for solutions for this i keep seeing people say remove ppa from the software center- other software which i tried but there is no mention of ppa software.

i am using ubuntu 11.10 which i upgraded from 11.04 on a sony vaio vpcf12

ps please keep the answers simple because i am not an expert with computers.

Thanks.

---

### Post by sohmc on 2011-12-28
> **Lar87 said:**
> 
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric Release.gpg                              
  Unable to connect to 204.188.2
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-updates Release.gpg                                     
  Unable to connect to 204.188.21
Err [http://archive.canonical.com](http://archive.canonical.com) oneiric Release                               


It looks like an octet is missing.  Did you remove these from your post?  Or perhaps your DNS settings are correct.  Can you go to [http://archive.ubuntu.com](http://archive.ubuntu.com) on your ubuntu box?

---

### Post by Lar87 on 2011-12-28
> **sohmc said:**
> It looks like an octet is missing.  Did you remove these from your post?  Or perhaps your DNS settings are correct.  Can you go to [http://archive.ubuntu.com](http://archive.ubuntu.com) on your ubuntu box?

Yes i can connect to that link and i removed some of the digits of my ip address in that post if that's what you mean?.

---

### Post by sohmc on 2011-12-29
Well, the IP addresses you moved belong to ubuntu, so you didn't need to do that.  And in the future, if you want to blank out an IP address, replace the octet with xxx so that people know that there was a value there, but has been removed.

If you can connect to the link, you should be able to download the archives.  Are you using a wired connection or a wireless connection?  I've never had any luck using a wireless connection when doing updates.  Not sure why and wasn't in a position to really figure out the problem.

If you are using a wired connection, perhaps you have a problem somewhere on your network.

Out of curiosity, what are you trying to install?  Perhaps it can be obtained a different way.  But it wouldn't solve your problem of not being able to download the packages from apt-get.

---

### Post by Lar87 on 2011-12-29
> **sohmc said:**
> Well, the IP addresses you moved belong to ubuntu, so you didn't need to do that.  And in the future, if you want to blank out an IP address, replace the octet with xxx so that people know that there was a value there, but has been removed.

If you can connect to the link, you should be able to download the archives.  Are you using a wired connection or a wireless connection?  I've never had any luck using a wireless connection when doing updates.  Not sure why and wasn't in a position to really figure out the problem.

If you are using a wired connection, perhaps you have a problem somewhere on your network.

Out of curiosity, what are you trying to install?  Perhaps it can be obtained a different way.  But it wouldn't solve your problem of not being able to download the packages from apt-get.

I'm after connecting my modem directly to my laptop and i am still unable to download packages from the software center or update my system. i have also noticed that the update manager still reads '' the package information was last update 19 days ago'' instead of 21 days. 

i was trying to download a program to capture and record video and also a file converter.

Thanks for the help so far by the way. hopefully i wont have to reinstall ubuntu again.

---

### Post by Henkdroid on 2011-12-29
In the system settings go to 'Software Sources' and there is a 'Download from:' option choose the nearest server.

---

### Post by spacecheck on 2011-12-30
I was having similar problems after I tried to install a 'partner' program (Skype). The amd64 version was unavailable, so I downloaded directly from the website & set update mgr as the opening program. That worked fine to install Skype. Unfortunately, neither Update Mgr nor Synaptic would update correctly afterwards, instead issuing errors quite similar to yours, no matter which mirror I selected.  I've seen several other recent complaints showing similar errors.

If you will close all open package managers, open a terminal and sudo an editor and then open /etc/apt/sources.list so you can review and edit the allowed sources. Open a second terminal and run "man sources.list" to be able read the general parameters for listing sources in another window.

Look at the errors you've received (they appear to relate mostly to "partner" sources). If errors are received, the package programs complain & give up w/o installing anything, or changing the cache (date & list of available program updates) even if they could have reached some of the locations.

I solved this for my system (after five days of fruitless waiting for another's success story to show up here) simply by commenting out the lines related exclusively to "partner" AND by removing the word "partner" from the lines related to more than just "partner" sources.  Thus, each instance of source containing "partner" was treated as follows:

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) oneiric-updates partner main universe restricted multiverse

was changed to

# deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) oneiric-updates partner main universe restricted multiverse

and replaced with:

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) oneiric-updates main universe restricted multiverse

AND Each exclusive entry containing "partner" was commented out, i.e.:

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) oneiric partner

became

# deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) oneiric partner


So, although I will not get "partner" updates, I was able to get all the other available updates. I imagine this may work for you, too.

Good luck,  spacecheck

( just don't let it bounce! )

---

### Post by Lar87 on 2011-12-30
> **Henkdroid said:**
> In the system settings go to 'Software Sources' and there is a 'Download from:' option choose the nearest server.

just tried this but couldn't connect to any server while using a direct connection.

thanks anyway.

---

### Post by spacecheck on 2011-12-30
> **Lar87 said:**
> just tried this but couldn't connect to any server while using a direct connection.

thanks anyway.

Can you reach the same source address with your browser? If so, try my previous suggestion.

---

### Post by Lar87 on 2011-12-30
> **spacecheck said:**
> I was having similar problems after I tried to install a 'partner' program (Skype). The amd64 version was unavailable, so I downloaded directly from the website & set update mgr as the opening program. That worked fine to install Skype. Unfortunately, neither Update Mgr nor Synaptic would update correctly afterwards, instead issuing errors quite similar to yours, no matter which mirror I selected.  I've seen several other recent complaints showing similar errors. If you will close all open package managers, open a terminal and sudo an editor and then open /etc/apt/sources.list so you can review and edit the allowed sources. Open a second terminal and run man sources.list to be able read the general parameters for listing sources in another window. Look at the errors you've received (they appear to relate mostly to "partner" sources). If errors are received, the package progams complain & give up w/o installing anything, or changing the cache (date & list of available program updates) even if they could have reached some of the locations.  I solved this for my system (after five days of fruitless waiting for another's success story to show up here) simply by commenting out the lines related exclusively to "partner" AND by removing the word "partner" from the lines related to more than just "partner".  Thus, each instance of source containing "partner" was treated as follows: deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) oneiric-updates partner main universe restricted multiverse was changed to # deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) oneiric-updates partner main universe restricted multiverse and replaced with deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) oneiric-updates main universe restricted multiverse AND Each exclusive entry containing "partner" was commented out, i.e.: deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) oneiric partner became # deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) oneiric partner  So, although I will not get "partner" updates, I was able to get all the other available updates. I imagine this may work for you, too.  Good luck,  spacecheck ( just don't let it bounce! )

Thank for your help spacecheck but i'm having trouble following your instructions and understanding what you are telling me
as i never use or know anything about the terminal.

first i opened up the editor in the terminal and open the sources with /etc/apt/sources.list (i think) and this is what




 i got N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://ie.archive.ubuntu.com/ubuntu/](http://ie.archive.ubuntu.com/ubuntu/) oneiric multiverse
deb-src [http://ie.archive.ubuntu.com/ubuntu/](http://ie.archive.ubuntu.com/ubuntu/) oneiric multiverse
deb [http://ie.archive.ubuntu.com/ubuntu/](http://ie.archive.ubuntu.com/ubuntu/) oneiric-updates multiverse
deb-src [http://ie.archive.ubuntu.com/ubuntu/](http://ie.archive.ubuntu.com/ubuntu/) oneiric-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://ie.archive.ubuntu.com/ubuntu/](http://ie.archive.ubuntu.com/ubuntu/) natty-backports main restricted univ$
# deb-src [http://ie.archive.ubuntu.com/ubuntu/](http://ie.archive.ubuntu.com/ubuntu/) natty-backports main restricted 





then when i opened the second terminal and entered man sources.list to check for errors i got this.






NAME
       sources.list - Package resource list for APT

DESCRIPTION
       The package resource list is used to locate archives of the package
       distribution system in use on the system. At this time, this manual
       page documents only the packaging system used by the Debian GNU/Linux
       system. This control file is /etc/apt/sources.list.

       The source list is designed to support any number of active sources and
       a variety of source media. The file lists one source per line, with the
       most preferred source listed first. The format of each line is: type
       uri args The first item, type determines the format for args.  uri is a
       Universal Resource Identifier (URI), which is a superset of the more
       specific and well-known Universal Resource Locator, or URL. The rest of
       the line can be marked as a comment by using a #.

SOURCES.LIST.D
       The /etc/apt/sources.list.d directory provides a way to add
       sources.list entries in separate files. The format is the same as for
       the regular sources.list file. File names need to end with .list and
       may only contain letters (a-z and A-Z), digits (0-9), underscore (_),
       hyphen (-) and period (.) characters. Otherwise APT will print a notice
       that it has ignored a file if the file doesn't match a pattern in the
       Dir::Ignore-Files-Silently configuration list - in this case it will be
       silently ignored.

THE DEB AND DEB-SRC TYPES
       The deb type describes a typical two-level Debian archive,
       distribution/component. Typically, distribution is generally an
       archivename like stable or testing or a codename like squeeze or wheezy
       while component is one of main contrib or non-free. The deb-src type
       describes a debian distribution's source code in the same form as the
       deb type. A deb-src line is required to fetch source indexes.

       The format for a sources.list entry using the deb and deb-src types is:

           deb [ options ] uri distribution [component1] [component2] [...]

       The URI for the deb type must specify the base of the Debian
       distribution, from which APT will find the information it needs.
       distribution can specify an exact path, in which case the components
       must be omitted and distribution must end with a slash (/). This is
       useful for when the case only a particular sub-section of the archive
       denoted by the URI is of interest. If distribution does not specify an
       exact path, at least one component must be present.

       distribution may also contain a variable, $(ARCH) which expands to the
       Debian architecture (i386, m68k, powerpc, ...) used on the system. This
       permits architecture-independent sources.list files to be used. In
       general this is only of interest when specifying an exact path, APT
       will automatically generate a URI with the current architecture
       otherwise.

       Since only one distribution can be specified per line it may be necessary to have multiple lines for the same URI, if a subset of all
       available distributions or components at that location is desired. APT
       will sort the URI list after it has generated a complete set
       internally, and will collapse multiple references to the same Internet
       host, for instance, into a single connection, so that it does not
       inefficiently establish an FTP connection, close it, do something else,
       and then re-establish a connection to that same host. This feature is
       useful for accessing busy FTP sites with limits on the number of
       simultaneous anonymous users. APT also parallelizes connections to
       different hosts to more effectively deal with sites with low bandwidth.

       options is always optional and needs to be surounded by square
       brackets. It can consist of multiple settings in the form
       setting=value. Multiple settings are separated by spaces. The following
       settings are supported by APT, note through that unsupported settings
       will be ignored silently:

       ·   arch=arch1,arch2,...  can be used to specify for which
           architectures packages information should be downloaded. If this
           option is not set all architectures defined by the
           APT::Architectures option will be downloaded.

       ·   trusted=yes can be set to indicate that packages from this source
           are always authenificated even if the Release file is not signed or
           the signature can't be checked. This disables parts of apt-
           secure(8) and should therefore only be used in a local and trusted
           context.  trusted=no is the opposite which handles even correctly
           authenificated sources as not authenificated.

       It is important to list sources in order of preference, with the most
       preferred source listed first. Typically this will result in sorting by
       speed from fastest to slowest (CD-ROM followed by hosts on a local
       network, followed by distant Internet hosts, for example).

       Some examples:

           deb [http://ftp.debian.org/debian](http://ftp.debian.org/debian) squeeze main contrib non-free
           deb [http://security.debian.org/](http://security.debian.org/) squeeze/updates main contrib non-free

URI SPECIFICATION
       The currently recognized URI types are cdrom, file, http, ftp, copy,
       ssh, rsh.

       file
           The file scheme allows an arbitrary directory in the file system to
           be considered an archive. This is useful for NFS mounts and local
           mirrors or archives.

       cdrom
           The cdrom scheme allows APT to use a local CDROM drive with media
           swapping. Use the apt-cdrom(8) program to create cdrom entries in
           the source list.

       http
           The http scheme specifies an HTTP server for the archive. If an
           environment variable http_proxy is set with the format

 [http://server:port/](http://server:port/), the proxy server specified in http_proxy will
           be used. Users of authenticated HTTP/1.1 proxies may use a string
           of the format [http://user:pass@server:port/](http://user:pass@server:port/). Note that this is an
           insecure method of authentication.

       ftp
           The ftp scheme specifies an FTP server for the archive. APT's FTP
           behavior is highly configurable; for more information see the
           apt.conf(5) manual page. Please note that a ftp proxy can be
           specified by using the ftp_proxy environment variable. It is
           possible to specify a http proxy (http proxy servers often
           understand ftp urls) using this method and ONLY this method. ftp
           proxies using http specified in the configuration file will be
           ignored.

       copy
           The copy scheme is identical to the file scheme except that
           packages are copied into the cache directory instead of used
           directly at their location. This is useful for people using a zip
           disk to copy files around with APT.

       rsh, ssh
           The rsh/ssh method invokes rsh/ssh to connect to a remote host as a
           given user and access the files. It is a good idea to do prior
           arrangements with RSA keys or rhosts. Access to files on the remote
           uses standard find and dd commands to perform the file transfers
           from the remote.

       more recognizable URI types
           APT can be extended with more methods shipped in other optional
           packages which should follow the nameing scheme
           apt-transport-method. The APT team e.g. maintains also the
           apt-transport-https package which provides access methods for
           https-URIs with features similar to the http method, but other
           methods for using e.g. debtorrent are also available, see apt-
           transport-debtorrent(1).

EXAMPLES
       Uses the archive stored locally (or NFS mounted) at /home/jason/debian
       for stable/main, stable/contrib, and stable/non-free.

           deb file:/home/jason/debian stable main contrib non-free

       As above, except this uses the unstable (development) distribution.

           deb file:/home/jason/debian unstable main contrib non-free

       Source line for the above

           deb-src file:/home/jason/debian unstable main contrib non-free

       The first line gets package information for the architectures in
       APT::Architectures while the second always retrieves amd64 and armel.

           deb [http://ftp.debian.org/debian](http://ftp.debian.org/debian) squeeze main
           deb [ arch=amd64,armel ] [http://ftp.debian.org/debian](http://ftp.debian.org/debian) squeeze main  Uses HTTP to access the archive at archive.debian.org, and uses only
       the hamm/main area.

           deb [http://archive.debian.org/debian-archive](http://archive.debian.org/debian-archive) hamm main

       Uses FTP to access the archive at ftp.debian.org, under the debian
       directory, and uses only the squeeze/contrib area.

           deb [ftp://ftp.debian.org/debian](ftp://ftp.debian.org/debian) squeeze contrib

       Uses FTP to access the archive at ftp.debian.org, under the debian
       directory, and uses only the unstable/contrib area. If this line
       appears as well as the one in the previous example in sources.list a
       single FTP session will be used for both resource lines.

           deb [ftp://ftp.debian.org/debian](ftp://ftp.debian.org/debian) unstable contrib

       Uses HTTP to access the archive at ftp.tlh.debian.org, under the
       universe directory, and uses only files found under
       unstable/binary-i386 on i386 machines, unstable/binary-amd64 on amd64,
       and so forth for other supported architectures. [Note this example only
       illustrates how to use the substitution variable; official debian
       archives are not structured like this]

           deb [http://ftp.tlh.debian.org/universe](http://ftp.tlh.debian.org/universe) unstable/binary-$(ARCH)/

SEE ALSO
       apt-cache(8) apt.conf(5)

BUGS
       APT bug page[1]. If you wish to report a bug in APT, please see
       /usr/share/doc/debian/bug-reporting.txt or the reportbug(1) command.

AUTHORS
       Jason Gunthorpe

       APT team

NOTES
        1. APT bug page
           [http://bugs.debian.org/src:apt](http://bugs.debian.org/src:apt)

Linux                          29 February 2004                SOURCES.LIST(5)

the rest of what you i said couldn't do or understand.

---

### Post by spacecheck on 2011-12-30
In the text from &quot;man sources.list&quot; are the explicit instructions/explanations (examples) on how to create a sources.list file to suit your machine and your distribution.

 I told you to sudo to start the editor in the other terminal, so you would have the rights needed to modify the file and save your changes.

 You initial post showed more error results than indicated possible by your last post, which only showed &quot;...multiverse&quot; (everything else commented out or missing).

 I don't use an intel processor, nor am I sure your cpu is an x86-64, so I am not sure what your architecture selection should be (&quot;arch=&quot;).  Try the following suggestion:

 Open the &quot;Software Sources&quot; program and select the first four items of the first tab unless you use no restricted/proprietary drivers or software. If not, deselect the ones you don't use.

 I have deselected &quot;other software&quot;, so skip to the third tab &quot;Updates&quot;. I would suggest the first two.

 This will leave you with &quot;main&quot; and &quot;universe&quot; unless you added for proprietary drivers & restricted software, which will add &quot;restricted&quot; and &quot;multiverse&quot; (the last was already there). Then close the &quot;Software sources&quot; (don't run an update check yet).

 If you close and reopen the sources.file in your editor, you should see the changes. Before you edit directly, I suggest you make a back up copy of the file or its contents.

 An amd64 system could get by with the following:

 # /etc/apt/sources.list

 # deb cdrom:[Xubuntu 11.10 _Oneiric Ocelot_ - Release amd64 (20111012)]/ dists/oneiric/main/binary-i386/
# deb cdrom:[Xubuntu 11.10 _Oneiric Ocelot_ - Release amd64 (20111012)]/ oneiric main restricted
deb [arch=amd64] [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) oneiric main universe restricted multiverse
# deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) oneiric-security partner main universe restricted multiverse
# deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) oneiric-updates partner main universe restricted multiverse
deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) oneiric-security main universe restricted multiverse
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) oneiric-updates main universe restricted multiverse
        # deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) oneiric partner
# deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) oneiric partner
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) oneiric-proposed main universe restricted multiverse

 You can see that I turned off &quot;partner&quot; sources by adding a hash mark before those entries (they were blocking my updates). If you modify your file to look like the above, correcting the &quot;[arch=amd64]&quot; to suit your CPU, then saving the file. You could then run &quot;Update Manager&quot; and click &quot;check&quot;.  It should then give you some satisfaction.
  Good luck!

---

### Post by spacecheck on 2011-12-30
Just guessing but, on an intel system, you may be able to get away with just the following:

 # /etc/apt/sources.list

 # deb cdrom:[Xubuntu 11.10 _Oneiric Ocelot_ - Release i386 (20111012)]/ dists/oneiric/main/binary-i386/
# deb cdrom:[Xubuntu 11.10 _Oneiric Ocelot_ - Release i386 (20111012)]/ oneiric main restricted
deb [arch=i386] [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) oneiric main universe restricted multiverse
deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) oneiric-security main universe restricted multiverse
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) oneiric-updates main universe restricted multiverse

The specific source server section could be changed to suit your desires (for example: http://ie.archive.ubuntu.com/ubuntu/ )

 Good luck!

---

### Post by cortman on 2011-12-30
Lar87: Do you use a proxy to connect to the internet? If so that might be giving apt-get issues...

---

### Post by spacecheck on 2011-12-30
> **cortman said:**
> Lar87: Do you use a proxy to connect to the internet? If so that might be giving apt-get issues...

 His initial post indicated he was getting &quot;hits&quot; on some of the source locations, so he's either not got a proxy, or it is not causing problems.

When the Update Mgr or apt-get gets a retrieval error it gives up and makes no changes, but tells you which source caused the error. In some instances, it tells you which line in sources.list it didn't like.

 I hope my explanation & suggestion help solve the problem.

 spacecheck
(just don't let it bounce!)

---

### Post by cortman on 2011-12-30
> **spacecheck said:**
> His initial post indicated he was getting &quot;hits&quot; on some of the source locations, so he's either not got a proxy, or it is not causing problems.

When the Update Mgr or apt-get gets a retrieval error it gives up and makes no changes, but tells you which source caused the error. In some instances, it tells you which line in sources.list it didn't like.

 I hope my explanation & suggestion help solve the problem.

 spacecheck
(just don't let it bounce!)

Going by the initial post that could very well have been the issue-

> Unable to connect to 204.188.2

Doesn't appear to be getting server hits there...
Just a hint too, whatever coding you're trying to do with &quot; isn't working, it's cluttering up your posts pretty badly...

---

### Post by spacecheck on 2011-12-30
> **cortman said:**
> Going by the initial post that could very well have been the issue-



Doesn't appear to be getting server hits there...
Just a hint too, whatever coding you're trying to do with &quot; isn't working, it's cluttering up your posts pretty badly...

No, it certainly could NOT very well have been the issue. His first post shows he  obviously retrieves about 10 KB of data over about 3.5 minutes: >  Get:1 http://extras.ubuntu.com oneiric Release.gpg [72 B]
Get:2 http://archive.canonical.com oneiric Release.gpg [198 B]
Get:3 http://extras.ubuntu.com oneiric Release [9,759 B]
...
Fetched 10.0 kB in 3min 36s (46 B/s)
Reading package lists... Done
 As he also replied in post#3, he can connect to http://archive.ubuntu.com and he explained intentionally cut off the last octet from his list, thinking it was his own IP address he was hiding. Response #4 corrected him for that.

 Response#5 says he is using a -modem- but response #8 says -direct connection-, so I will assume he meant -cable modem- which doesn't explain -10 KB over 3.5 min.- as well as a dialup might. No matter, he can reach the archive site in his browser.

 I did not use coding for the miserably represented quotation marks, they are simply not transposed correctly.  Sorry they didn't meet with your aesthetic approval. Perhaps I should have written -hits- instead. But, thanks for the feedback.

 Cheers

---

### Post by cortman on 2011-12-30
> **spacecheck said:**
> No, it certainly could NOT very well have been the issue. His first post shows he  obviously retrieves about 10 KB of data over about 3.5 minutes:  As he also replied in post#3, he can connect to [http://archive.ubuntu.com](http://archive.ubuntu.com) and he explained intentionally cut off the last octet from his list, thinking it was his own IP address he was hiding. Response #4 corrected him for that.

 Response#5 says he is using a -modem- but response #8 says -direct connection-, so I will assume he meant -cable modem- which doesn't explain -10 KB over 3.5 min.- as well as a dialup might. No matter, he can reach the archive site in his browser.

 I did not use coding for the miserably represented quotation marks, they are simply not transposed correctly.  Sorry they didn't meet with your aesthetic approval. Perhaps I should have written -hits- instead. But, thanks for the feedback.

 Cheers

I stand corrected- I missed the IP address thing. I'll leave it to you guys, then.

No offense meant by the &quot; comment- weird things can happen with trying to use HTML code in posting, etc., just thought I'd let you know!

---

### Post by spacecheck on 2011-12-30
> **cortman said:**
> I stand corrected- I missed the IP address thing. I'll leave it to you guys, then.

No offense meant by the &quot; comment- weird things can happen with trying to use HTML code in posting, etc., just thought I'd let you know!

Hey, you don't have to stand! Seriously! Take a seat, get comfortable! And by no means take my earlier response to heart, as I was not &#34;offended&#34;.

 Thanks for letting me know (or, confirming) how ugly the &#34;quotation marks&#34; were appearing. I've since had the time to check for the correct code for &#34;quotation marks&#34;, as you can see, and have resolved that ugly little problem.

Don't be put off, a la &#34;I'll leave it to you guys&#34; because many eyes more quickly see and resolve simple but oft overlooked problems, than do fewer experienced eyes looking less often, if you know what I mean. Like I wrote (and meant) earlier, &#34;thanks for the feedback!&#34;

Perhaps Lawrence will let us know if the problem has since been solved.

Best wishes and regards,

spacecheck

(just don't let it bounce)

---

### Post by Lar87 on 2011-12-31
ok so i have selected/deselected the boxes in softare sources.
but now i cant open  /etc/apt/sources.list. i dont how to open it in the editor and when i enter it into terminal its i don't have permision what am i doing wrong?


ps i connected to a proxy server about 2 or 3 weeks through firefox. i don't no if i'm still connected to it.  

and yes i did use a cable modem to make sure it wasn't a problem with my router which i initially did the tests on.

---

### Post by spacecheck on 2011-12-31
> **Lar87 said:**
> ok so i have selected/deselected the boxes in softare sources.
but now i cant open  /etc/apt/sources.list. i dont how to open it in the editor and when i enter it into terminal its i don't have permision what am i doing wrong?


ps i connected to a proxy server about 2 or 3 weeks through firefox. i don't no if i'm still connected to it.  

and yes i did use a cable modem to make sure it wasn't a problem with my router which i initially did the tests on.

Some service providers keep the MAC address of the network card (or router) attached to the cable modem for an extended period, before releasing it for use by another MAC device. Sometimes takes a while (who knows, 10-20 min.?) before a new device gets access. Sometimes a cable modem or router will screw up and lose the connection until rebooted. Sometimes a router attached to a cable modem will have a problem getting connected, if not rebooted several minutes after a cable modem is rebooted.

To discover if you are using a proxy setting to connect in the browser, go to (Firefox) &#34;Edit, Preferences, Advanced, Network, Connection, Settings, Configure&#34; and select proxy settings required for your location, if any

If you call up the editor in the terminal with &#34;sudo&#34; you will have editing rights, but you won't want to do that while any package manager is using the file, so you will want to close &#34;Software Sources&#34;, &#34;Update Manager&#34; &#34;Synaptic&#34; etc., before opening and editing /etc/apt/sources.list 
&#34;sudo gedit&#34; (or whatever editor you enjoy) will allow you to enter your password, open up the editor for you, and you could then click &#34;File, Open&#34; and click your way to /etc/apt/ where you should see the file sources.list 

Then, you could save a backup copy make any required changes to the original and save the changes. Close and reopen the file, to see if the changes were retained (if an update manager was using it while you made changes, the changes probably won't be saved)
Afterwards, you could call up the Update manager and click on the &#34;Check&#34; button, to see if it finds and shows updates, or gives you some further error message in &#34;Details&#34; which we could examine.
Perhaps it'll work this time. 

Good luck!

---

### Post by Lar87 on 2011-12-31
Alright i'm looking at the sources list finally and have made a copy of it. here is what it looks like. Could you tell me exactly which lines i am replacing please.

## deb cdrom:[Ubuntu 11.04 _Natty Narwhal_ - Release i386 (20110427.1)]/ natty main restricted

## See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
## newer versions of the distribution.
deb [http://ie.archive.ubuntu.com/ubuntu/](http://ie.archive.ubuntu.com/ubuntu/) oneiric main restricted
deb-src [http://ie.archive.ubuntu.com/ubuntu/](http://ie.archive.ubuntu.com/ubuntu/) oneiric main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://ie.archive.ubuntu.com/ubuntu/](http://ie.archive.ubuntu.com/ubuntu/) oneiric-updates main restricted
deb-src [http://ie.archive.ubuntu.com/ubuntu/](http://ie.archive.ubuntu.com/ubuntu/) oneiric-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://ie.archive.ubuntu.com/ubuntu/](http://ie.archive.ubuntu.com/ubuntu/) oneiric universe
deb-src [http://ie.archive.ubuntu.com/ubuntu/](http://ie.archive.ubuntu.com/ubuntu/) oneiric universe
deb [http://ie.archive.ubuntu.com/ubuntu/](http://ie.archive.ubuntu.com/ubuntu/) oneiric-updates universe
deb-src [http://ie.archive.ubuntu.com/ubuntu/](http://ie.archive.ubuntu.com/ubuntu/) oneiric-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://ie.archive.ubuntu.com/ubuntu/](http://ie.archive.ubuntu.com/ubuntu/) oneiric multiverse
deb-src [http://ie.archive.ubuntu.com/ubuntu/](http://ie.archive.ubuntu.com/ubuntu/) oneiric multiverse
deb [http://ie.archive.ubuntu.com/ubuntu/](http://ie.archive.ubuntu.com/ubuntu/) oneiric-updates multiverse
deb-src [http://ie.archive.ubuntu.com/ubuntu/](http://ie.archive.ubuntu.com/ubuntu/) oneiric-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://ie.archive.ubuntu.com/ubuntu/](http://ie.archive.ubuntu.com/ubuntu/) natty-backports main restricted universe multiverse
# deb-src [http://ie.archive.ubuntu.com/ubuntu/](http://ie.archive.ubuntu.com/ubuntu/) natty-backports main restricted universe multiverse

deb [http://ie.archive.ubuntu.com/ubuntu/](http://ie.archive.ubuntu.com/ubuntu/) oneiric-security main restricted
deb-src [http://ie.archive.ubuntu.com/ubuntu/](http://ie.archive.ubuntu.com/ubuntu/) oneiric-security main restricted
deb [http://ie.archive.ubuntu.com/ubuntu/](http://ie.archive.ubuntu.com/ubuntu/) oneiric-security universe
deb-src [http://ie.archive.ubuntu.com/ubuntu/](http://ie.archive.ubuntu.com/ubuntu/) oneiric-security universe
deb [http://ie.archive.ubuntu.com/ubuntu/](http://ie.archive.ubuntu.com/ubuntu/) oneiric-security multiverse
deb-src [http://ie.archive.ubuntu.com/ubuntu/](http://ie.archive.ubuntu.com/ubuntu/) oneiric-security multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) oneiric partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) natty partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
# deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) oneiric main
# deb-src [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) oneiric main




by the way i added a second # to the very first few lines a few days ago.
I seen someone saying to this in another thread but i'm not sure if they meant to add the # if there was no # in the first place

Thanks again for the help really appreciate it.

---

### Post by spacecheck on 2011-12-31
A double hash mark ## indicates a comment or explanation. A single hash mark # means the line is to be ignored by the system.

I do not know if you need to load packages from source (deb-src) try it without them first.

If I was using intel system with oneiric, on your selected source server archive, mine would look like this (perhaps it will work this way for you?). Try it and let me know if you are successful:

# /etc/apt/sources.list

deb [arch=i386] [http://ie.archive.ubuntu.com/ubuntu](http://ie.archive.ubuntu.com/ubuntu) oneiric main universe restricted multiverse

## if you use partner packages and need updates
## and security updates for them, remove the hash
## marks for the next two lines

# deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) oneiric-security partner main universe restricted multiverse
# deb [http://ie.archive.ubuntu.com/ubuntu](http://ie.archive.ubuntu.com/ubuntu) oneiric-updates partner main universe restricted multiverse
deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) oneiric-security main universe restricted multiverse
deb [http://ie.archive.ubuntu.com/ubuntu](http://ie.archive.ubuntu.com/ubuntu) oneiric-updates main universe restricted multiverse




## If you need partner packages installed, use
## the software center to find and select them,
## then the next line will lose its hash mark

# deb [http://ie.archive.ubuntu.com/ubuntu](http://ie.archive.ubuntu.com/ubuntu) oneiric partner

---

### Post by Lar87 on 2012-01-01
that did not work unfortunately.

here is what my source list looks like now.


## deb cdrom:[Ubuntu 11.04 _Natty Narwhal_ - Release i386 (20110427.1)]/ natty main restricted

## See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
## newer versions of the distribution.
deb [http://ie.archive.ubuntu.com/ubuntu/](http://ie.archive.ubuntu.com/ubuntu/) oneiric main restricted
deb-src [http://ie.archive.ubuntu.com/ubuntu/](http://ie.archive.ubuntu.com/ubuntu/) oneiric main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://ie.archive.ubuntu.com/ubuntu/](http://ie.archive.ubuntu.com/ubuntu/) oneiric-updates main restricted
deb-src [http://ie.archive.ubuntu.com/ubuntu/](http://ie.archive.ubuntu.com/ubuntu/) oneiric-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://ie.archive.ubuntu.com/ubuntu/](http://ie.archive.ubuntu.com/ubuntu/) oneiric universe
deb-src [http://ie.archive.ubuntu.com/ubuntu/](http://ie.archive.ubuntu.com/ubuntu/) oneiric universe
deb [http://ie.archive.ubuntu.com/ubuntu/](http://ie.archive.ubuntu.com/ubuntu/) oneiric-updates universe
deb-src [http://ie.archive.ubuntu.com/ubuntu/](http://ie.archive.ubuntu.com/ubuntu/) oneiric-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://ie.archive.ubuntu.com/ubuntu/](http://ie.archive.ubuntu.com/ubuntu/) oneiric multiverse
deb-src [http://ie.archive.ubuntu.com/ubuntu/](http://ie.archive.ubuntu.com/ubuntu/) oneiric multiverse
deb [http://ie.archive.ubuntu.com/ubuntu/](http://ie.archive.ubuntu.com/ubuntu/) oneiric-updates multiverse
deb-src [http://ie.archive.ubuntu.com/ubuntu/](http://ie.archive.ubuntu.com/ubuntu/) oneiric-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://ie.archive.ubuntu.com/ubuntu/](http://ie.archive.ubuntu.com/ubuntu/) natty-backports main restricted universe multiverse
# deb-src [http://ie.archive.ubuntu.com/ubuntu/](http://ie.archive.ubuntu.com/ubuntu/) natty-backports main restricted universe multiverse

# deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) oneiric-security partner main universe restricted multiverse
# deb [http://ie.archive.ubuntu.com/ubuntu](http://ie.archive.ubuntu.com/ubuntu) oneiric-updates partner main universe restricted multiverse
deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) oneiric-security main universe restricted multiverse
deb [http://ie.archive.ubuntu.com/ubuntu](http://ie.archive.ubuntu.com/ubuntu) oneiric-updates main universe restricted multiverse


## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) oneiric partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) natty partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
# deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) oneiric main
# deb-src [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) oneiric main

---

### Post by spacecheck on 2012-01-01
> **Lar87 said:**
> that did not work unfortunately.



That is an extremely cryptic response. What error message did you get, which might explain where the problem is? If you replaced everything in the file with the few lines I posted (after making a backup copy), why does anything else appear in list?
Happy New Year!

---

### Post by Lar87 on 2012-01-01
Happy new year to you aswell.

I deleted the 6th group of lines and copy and pasted the lines
you gave me.

i'm not getting an error msg.

---

### Post by spacecheck on 2012-01-01
Did you try just using the lines I sent you?

---

### Post by Lar87 on 2012-01-01
> **spacecheck said:**
> Did you try just using the lines I sent you?

yes

---

### Post by spacecheck on 2012-01-01
> **Lar87 said:**
> yes

Sorry, but I cannot extract many details from your one word response. Please clarify.

---

### Post by Lar87 on 2012-01-01
you asked me if i just used the lines you sent me. the answer to this question is yes. what more can i say??. have you still not realized i am noob.

---

### Post by spacecheck on 2012-01-01
Perhaps you should try again.
First ensure all update/package managers are closed.
Second edit the sources.list as previously instructed.
Third save the edited file.
Fourth reopen the edited file, just to verify the changes truly were saved.
Fifth open another terminal and enter the words:    sudo apt-get update
Sixth enter password and hit return
Seventh look to see what the results are
Eighth report if there are any "hits" listed, or errors, like you did in your first posting
Good luck! Fingers are crossed for you!

---

### Post by Lar87 on 2012-01-01
after sudo apt-get update i got and error saying read only file sysytem so i restarted done it again and got this


Ign [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) oneiric InRelease                             
Err [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security InRelease                      
  
Err [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security Release.gpg                    
  Unable to connect to 204.188.215.54:3128:
Err [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) oneiric-updates InRelease
  
Err [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) oneiric Release.gpg
  Unable to connect to 204.188.215.54:3128:
Err [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) oneiric-updates Release.gpg
  Unable to connect to 204.188.215.54:3128:
Reading package lists... Done
W: Failed to fetch [http://ie.archive.ubuntu.com/ubuntu/dists/oneiric-updates/InRelease](http://ie.archive.ubuntu.com/ubuntu/dists/oneiric-updates/InRelease)  

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/oneiric-security/InRelease](http://security.ubuntu.com/ubuntu/dists/oneiric-security/InRelease)  

W: Failed to fetch [http://ie.archive.ubuntu.com/ubuntu/dists/oneiric/Release.gpg](http://ie.archive.ubuntu.com/ubuntu/dists/oneiric/Release.gpg)  Unable to connect to 204.188.215.54:3128:

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/oneiric-security/Release.gpg](http://security.ubuntu.com/ubuntu/dists/oneiric-security/Release.gpg)  Unable to connect to 204.188.215.54:3128:

W: Failed to fetch [http://ie.archive.ubuntu.com/ubuntu/dists/oneiric-updates/Release.gpg](http://ie.archive.ubuntu.com/ubuntu/dists/oneiric-updates/Release.gpg)  Unable to connect to 204.188.215.54:3128:

W: Some index files failed to download. They have been ignored, or old ones used instead.
laurence@laurence-VPCF12M0E:~$

---

### Post by spacecheck on 2012-01-01
The unreachable IP address (with added port number) is not related to Canonical/Ubuntu, but to "Sharktech Internet Services". Is that your service provider? 

This may mean you have made some recent change in your router or network settings (about the time you stopped getting updates; I read "19 days" in your first posting). Have you made such changes? 

You wrote (post # 18 ) "ps i connected to a proxy server about 2 or 3 weeks through firefox. i don't no if i'm still connected to it." That would be about the same time frame as you stopped getting updates. Why did you set that proxy? Have you gone back and removed it? If so, were there other settings you may have forgotten to return to normal? Have you changed DHCP or DNS settings?

---

### Post by Lar87 on 2012-01-01
no that's not my isp. im just after changing the settings in firefox to no proxy but i still get the same error msg after sudo apt-get update. I also have not changed any dns setting.

i installed linux mint yesterday to see if i got the same problem but i didn't. I was able to do the upadtes and install packages on it

---

### Post by spacecheck on 2012-01-01
To check your proxy settings in Ubuntu 11.10, select "System Settings, Network, Network Proxy". If you were using the system at a different location which required a proxy, but are no longer at that location, you probably no longer need the proxy and may wish to remove/deactivate it. If you select "No Proxy"  and select "System-wide" you may resolve the problem. Then try again to update

---

### Post by Lar87 on 2012-01-01
the network settings where already set to "no proxy" and "system wide"

---

### Post by spacecheck on 2012-01-01
What about the other settings for DHCP and DNS? Is the proxy setting still set in Firefox? Are you connected directly to the cable modem, or per cable or wireless to a router? Is the cable or wireless setting used specifically set up to use a proxy, or other DNS servers? Is the wired/wireless connection used set up for automatic DHCP connection or have you changed it to some other setting? Have you manually added any specific routing data?

---

### Post by Lar87 on 2012-01-01
yes i have disabled the firefox proxy. i haven't changed any settings on my wireless router. i am normally connected to a wirelles router. 

i have just now connected my cable modem to my laptop. re started it and done sudo update and here are the results. i dont no the answers to the other questions 

laurence@laurence-VPCF12M0E:~$ sudo apt-get update
[sudo] password for laurence: 
Ign [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security InRelease
Ign [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) oneiric InRelease                       
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security Release.gpg                    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security Release                  
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/main i386 Packages
Ign [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) oneiric-updates InRelease               
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/universe i386 Packages
Hit [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) oneiric Release.gpg
Get:1 [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/restricted i386 Packages [14 B]
Hit [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) oneiric-updates Release.gpg                   
Hit [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) oneiric Release                               
Hit [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) oneiric-updates Release                  
Ign [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/main TranslationIndex          
Ign [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/multiverse TranslationIndex
Ign [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/restricted TranslationIndex
Ign [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/universe TranslationIndex
Err [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/multiverse i386 Packages
  Unable to connect to 204.188.215.54:3128:
Err [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/main Translation-en_IE
  Unable to connect to 204.188.215.54:3128:
Err [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/main Translation-en
  Unable to connect to 204.188.215.54:3128:
Err [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/multiverse Translation-en_IE
  Unable to connect to 204.188.215.54:3128:
Err [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/multiverse Translation-en
  Unable to connect to 204.188.215.54:3128:
Err [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/restricted Translation-en_IE
  Unable to connect to 204.188.215.54:3128:
Err [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/restricted Translation-en
  Unable to connect to 204.188.215.54:3128:
Err [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/universe Translation-en_IE
  Unable to connect to 204.188.215.54:3128:
Err [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/universe Translation-en
  Unable to connect to 204.188.215.54:3128:
Get:2 [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) oneiric/main Sources [877 kB]
99% [Connecting to 204.188.215.54 (204.188.215.54)]                 103 kB/s 0s^99% [Connecting to 204.188.215.54 (204.188.215.54)]                 103 kB/s 0s^99% [Connecting to 204.188.215.54 (204.188.215.54)]                35.7 kB/s 0s^99% [Connecting to 204.188.215.54 (204.188.215.54)]                35.7 kB/s 0s^99% [Connecting to 204.188.215.54 (204.188.215.54)]

---

### Post by spacecheck on 2012-01-01
Something is changing/redirecting your domain name resolution (DNS) to __[]("http://ie.archive.ubuntu.com/")the wrong IP address. This is causing your apt-get errors.

Use terminal to ping security.ubuntu.com and ping ie.archive.ubuntu.com and post the results here.

---

### Post by Lar87 on 2012-01-01
i have pinged security.ubuntu.com but its been going on for an hour and not giving results
 

64 bytes from atemoya.canonical.com (91.189.92.166): icmp_req=4694 ttl=52 time=3

7.5 ms

64 bytes from atemoya.canonical.com (91.189.92.166): icmp_req=4694 ttl=52 time=2

[COLOR="RoyalBlue"][/COLOR]3.0 ms[COLOR="RoyalBlue"][/COLOR]

64 bytes from atemoya.canonical.com (91.189.92.166): icmp_req=4694 ttl=52 time=4

the numbers in 7.5ms and 3.0 are constantly changing beetween 3.0ms to 4.6ms(etc)

---

### Post by spacecheck on 2012-01-01
There are various locations (for example, /etc/hosts , network settings, manual routes, manually set DNS servers, etc.) where a redirection could occur. I can ping the main Ubuntu archive and security servers for you, tell you the addresses (or you could do it yourself on your Mint system), and you could simply find/replace the respective names in the sources.list with those IP-addresses. Then you could again test apt-get update.

Since that method would bypass name resolution, the name could not be redirected to a wrong IP-address.

I just ran a ping for archive.ubuntu.com, and it resolved to 91.189.92.176
I just ran a ping for security.ubuntu.com and it resolved to 91.189.92.166

sudo your editor and open /etc/apt/sources.list

Use menu items "Search, Replace" to find:  /ie.archive.ubuntu.com/ and replace all with /91.189.92.176/ (that is the main server not the ie.archive.ubuntu.com mirror)
Use menu items "Search, Replace" to find:  /isecurity.ubuntu.com/ and replace all with /91.189.92.166/

Save the file (close and reopen to ensure changes were kept)
sudo apt-get update
See if there any errors. If not, you could follow up with sudo apt-get upgrade

Unfortunately, that method neither locates nor corrects the name redirection, nor its origin or cause.

You could look in /etc/hosts to see if 204.188.215.54 is listed, or you could use grep to locate any/all files having lines containing the pattern 204.188.215.54 (man grep for details on how to do this).

Let us know how it goes.

Good Luck!

---

### Post by Zill on 2012-01-01
> **Lar87 said:**
> i have pinged security.ubuntu.com but its been going on for an hour and not giving results...
Just hit ctrl-c to stop the test after it has run for a few cycles and a summary of the tests should be shown.

The numbers you have posted for this test look fine to me (although others may disagree!).

---

### Post by Lar87 on 2012-01-01
ok i was about try this and got another error msg. i dont know if this is related but this is the error i got when trying to open the sources list

 laurence@laurence-VPCF12M0E:~$ sudo gedit
[sudo] password for laurence: 
sudo: Can't open /var/lib/sudo/laurence/0: Read-only file system

** (gedit:5645): WARNING **: Could not connect to session bus
laurence@laurence-VPCF12M0E:~$ 



no other program is running. i have to reboot to not get this error

---

### Post by Zill on 2012-01-02
> **Lar87 said:**
> ok i was about try this and got another error msg. i dont know if this is related but this is the error i got when trying to open the sources list

 laurence@laurence-VPCF12M0E:~$ [COLOR="Red"]sudo gedit[/COLOR]
[sudo] password for laurence: 
sudo: Can't open /var/lib/sudo/laurence/0: Read-only file system

** (gedit:5645): WARNING **: Could not connect to session bus
laurence@laurence-VPCF12M0E:~$ 
sudo should *only* be used to open CLI (command line interface) applications as root.  CLI applications normally run in the "Terminal".  For example, the text editor "nano" is a cli application and can be started with the sudo prefix if required.  eg.
```
sudo nano
```

However, the text editor "Gedit" is a ***graphical*** application, intended to be used directly within the Gnome desktop environment.

Graphical applications are generally started directly from a menu item or desktop launcher.  However, they *can* also be started from a terminal command if required.  If the application needs to be started as root in these circumstances the prefix "gksudo" should be used rather than "sudo".  eg.
```
gksudo gedit
```

You can read up on the reasons for this if you wish but it is mainly related to setting environment variables correctly.  Sometimes you *can* get away with starting a graphical application with sudo, rather than gksudo, but it *can* cause strange problems such as you have just experienced. ;-)

I suggest you reboot to ensure everything is clean, then decide if you wish to use a terminal-based editor (such as nano) or a graphical editor (such as gedit).  Then start your chosen application using the appropriate prefix for root access.

See [Running Sudo Graphically]("http://www.psychocats.net/ubuntu/graphicalsudo") for more info.

---

### Post by spacecheck on 2012-01-02
Other things can also lock a file system and make it read-only. If a cron job is running an update manager task, for example, sources.list would already be in use and probably unavailable for editing. I may err here, but I imagine a disk-indexing task could also lock files/directories and leave them in read-only state for the duration of the indexing (which could take a long time, depending upon amount of indexing required and number of parallel tasks).

Although I agree that gksudo is the better command to sudo a graphical application, I've been lucky enough not to have had any problems using sudo with gedit, leafpad, or other graphic editor.

spacecheck

---

### Post by spacecheck on 2012-01-02
Well Laurence, I did a simple query for 204.188.215.54 per google. Among a few other things, it came up with a long list of proxy/free proxy entries, most listing the port number 3128 cited in your error message.

Go figure...

---

### Post by Lar87 on 2012-01-04
> **spacecheck said:**
> Well Laurence, I did a simple query for 204.188.215.54 per google. Among a few other things, it came up with a long list of proxy/free proxy entries, most listing the port number 3128 cited in your error message.

Go figure...

well that explains the problem but i do not know why it's sill trying to connect to that that ip address so i am going to reinstall the os.

---

### Post by spacecheck on 2012-01-04
Do you have a file called /etc/apt/apt.conf ?

---

