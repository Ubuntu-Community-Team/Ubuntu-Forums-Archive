---
title: "Help! Computer crashed during app installation."
date: 2009-11-30
forum: General Help
---

### Post by max_power on 2009-11-30
My computer crashed during the installation of Docky. Now I cannot complete the installation. 

I have tried sudo-apt get remove docky, sudo apt-get purge docky, etc..

Here is the error report:

```
root@lin910:~# sudo apt-get install docky
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  docky
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
4 not fully installed or removed.
Need to get 0B/874kB of archives.
After this operation, 2,298kB of additional disk space will be used.
Selecting previously deselected package docky.
(Reading database ... 160860 files and directories currently installed.)
Unpacking docky (from .../docky_2.0~bzr671-0karmic1~dockycore1_i386.deb) ...
Processing triggers for hicolor-icon-theme ...
Processing triggers for desktop-file-utils ...
Setting up libxml-sax-perl (0.96+dfsg-1) ...
dpkg (subprocess): unable to execute installed post-installation script: Exec format error
dpkg: error processing libxml-sax-perl (--configure):
 subprocess installed post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of libxml-libxml-perl:
 libxml-libxml-perl depends on libxml-sax-perl (>= 0.11); however:
  Package libxml-sax-perl is not configured yet.
dpkg: error processing libxml-libxml-perl (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gtk-sharp2-gapi:
 gtk-sharp2-gapi depends on libxml-libxml-perl; however:
  Package libxml-libxml-perl is not configured yet.
dpkg: error processing gtk-sharp2-gapi (--configure):
 dependency problems - leaving unconfigured
Setting up libgnomedesktop2.20-cil (2.26.0-1) ...
No apport report written because the error message indicates its a followup error from a previous failure.
                          No apport report written because the error message indicates its a followup error from a previous failure.
                                                    dpkg (subprocess): unable to execute installed post-installation script: Exec format error
dpkg: error processing libgnomedesktop2.20-cil (--configure):
 subprocess installed post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of docky:
 docky depends on libgnomedesktop2.20-cil; however:
  Package libgnomedesktop2.20-cil is not configured yet.
 docky depends on gtk-sharp2-gapi; however:
  Package gtk-sharp2-gapi is not configured yet.
dpkg: error processing docky (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              No apport report written because MaxReports is reached already
                                            Errors were encountered while processing:
 libxml-sax-perl
 libxml-libxml-perl
 gtk-sharp2-gapi
 libgnomedesktop2.20-cil
 docky
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

---

### Post by theozzlives on 2009-11-30
try
```
sudo dpkg --configure -a
```

---

### Post by max_power on 2009-11-30
> **theozzlives said:**
> try
```
sudo dpkg --configure -a
```

Thanks for the reply.. Unfortunately, that doesn't work

```
root@lin910:~# sudo dpkg --configure -a
dpkg: dependency problems prevent configuration of libxml-libxml-perl:
 libxml-libxml-perl depends on libxml-sax-perl (>= 0.11); however:
  Package libxml-sax-perl is not configured yet.
dpkg: error processing libxml-libxml-perl (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gtk-sharp2-gapi:
 gtk-sharp2-gapi depends on libxml-libxml-perl; however:
  Package libxml-libxml-perl is not configured yet.
dpkg: error processing gtk-sharp2-gapi (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of docky:
 docky depends on gtk-sharp2-gapi; however:
  Package gtk-sharp2-gapi is not configured yet.
dpkg: error processing docky (--configure):
 dependency problems - leaving unconfigured
Setting up libgnomedesktop2.20-cil (2.26.0-1) ...
dpkg (subprocess): unable to execute installed post-installation script: Exec format error
dpkg: error processing libgnomedesktop2.20-cil (--configure):
 subprocess installed post-installation script returned error exit status 2
Errors were encountered while processing:
 libxml-libxml-perl
 gtk-sharp2-gapi
 docky
 libgnomedesktop2.20-cil

```

---

### Post by max_power on 2009-11-30
ive also tried removing the broken packages one by one, but that throws more errors..

hmmm

---

### Post by nerdopolis on 2009-11-30
Save the following text into ```
/var/lib/dpkg/info/libxml-sax-perl.postinst
```
The text editor you run will need to be run as root.

```
#!/bin/sh                                                                             
## ----------------------------------------------------------------------             
## debian/postinst : postinstallation script for libxml-sax-perl                      
## ----------------------------------------------------------------------             

## ----------------------------------------------------------------------
set -e                                                                   

## ----------------------------------------------------------------------
if [ "$1" = configure ]                                                  
then                                                                     
    [ -d /etc/perl/XML/SAX ] || mkdir --parents /etc/perl/XML/SAX        
    if which ucfr >/dev/null 2>&1                                        
    then                                                                 
        ucfr libxml-sax-perl /etc/perl/XML/SAX/ParserDetails.ini         
    fi                                                                   

    if [ -n "$2" ] && dpkg --compare-versions "$2" le 0.16-0.1
    then                                                      
        echo "Migrating the Perl SAX parser information directory."
        # first, move /etc/perl/XML/SAX/ParserDetails.d/ under     
        #             /var/lib/libxml-sax-perl                     
        for i in /etc/perl/XML/SAX/ParserDetails.d/*               
        do                                                         
            # the directory should never be missing or empty, but the [ ! -e ]
            # construct handles an unexpanded glob just in case
            [ ! -e "$i" ] || \
            mv "$i" "/var/lib/libxml-sax-perl/ParserDetails.d/50-$(basename $i)"
        done
        [ ! -d /etc/perl/XML/SAX/ParserDetails.d ] || \
            rmdir --ignore-fail-on-non-empty /etc/perl/XML/SAX/ParserDetails.d

        # now downgrade XML::SAX::PurePerl priority by removing it first
        update-perl-sax-parsers --remove XML::SAX::PurePerl
    fi

    update-perl-sax-parsers --add XML::SAX::PurePerl --priority 10
    update-perl-sax-parsers --update
fi

## ----------------------------------------------------------------------
## automatically generated debhelper commands


exit 0

## ----------------------------------------------------------------------

```After you save that in /var/lib/dpkg/info/libxml-sax-perl.postinst run
```
sudo chmod +x /var/lib/dpkg/info/libxml-sax-perl.postinst
``` to be sure, then try 
```
sudo dpkg --configure -a
``` again

---

### Post by max_power on 2009-11-30
I tried that as well and i get the same error message

```
chris@lin910:~$ sudo dpkg --configure -a
dpkg: dependency problems prevent configuration of libxml-libxml-perl:
 libxml-libxml-perl depends on libxml-sax-perl (>= 0.11); however:
  Package libxml-sax-perl is not configured yet.
dpkg: error processing libxml-libxml-perl (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gtk-sharp2-gapi:
 gtk-sharp2-gapi depends on libxml-libxml-perl; however:
  Package libxml-libxml-perl is not configured yet.
dpkg: error processing gtk-sharp2-gapi (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of docky:
 docky depends on gtk-sharp2-gapi; however:
  Package gtk-sharp2-gapi is not configured yet.
dpkg: error processing docky (--configure):
 dependency problems - leaving unconfigured
Setting up libgnomedesktop2.20-cil (2.26.0-1) ...
dpkg (subprocess): unable to execute installed post-installation script: Exec format error
dpkg: error processing libgnomedesktop2.20-cil (--configure):
 subprocess installed post-installation script returned error exit status 2
Errors were encountered while processing:
 libxml-libxml-perl
 gtk-sharp2-gapi
 docky
 libgnomedesktop2.20-cil

```

Is it possible to force removal of packages?

---

### Post by nerdopolis on 2009-11-30
OK. replace the contents of /var/lib/dpkg/info/libgnomedesktop2.20-cil.postinst with the following (as root):

```

#!/bin/sh
set -e
# Automatically added by dh_installcligac
if [ "$1" = "configure" ] && [ -x /usr/share/cli-common/gac-package-install ]; then
        /usr/share/cli-common/gac-package-install libgnomedesktop2.20-cil
fi
# End automatically added section

```
run ```
sudo chmod +x /var/lib/dpkg/info/libgnomedesktop2.20-cil.postinst
```
then run 
```
sudo dpkg --configure
```

---

### Post by max_power on 2009-11-30
Thanks for the help!!

Hmmm.. another error report.

```
chris@lin910:~$ sudo dpkg --configure -a
dpkg: dependency problems prevent configuration of libxml-libxml-perl:
 libxml-libxml-perl depends on libxml-sax-perl (>= 0.11); however:
  Package libxml-sax-perl is not configured yet.
dpkg: error processing libxml-libxml-perl (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gtk-sharp2-gapi:
 gtk-sharp2-gapi depends on libxml-libxml-perl; however:
  Package libxml-libxml-perl is not configured yet.
dpkg: error processing gtk-sharp2-gapi (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of docky:
 docky depends on gtk-sharp2-gapi; however:
  Package gtk-sharp2-gapi is not configured yet.
dpkg: error processing docky (--configure):
 dependency problems - leaving unconfigured
Setting up libgnomedesktop2.20-cil (2.26.0-1) ...
* Installing 0 assemblies from libgnomedesktop2.20-cil into Mono

Errors were encountered while processing:
 libxml-libxml-perl
 gtk-sharp2-gapi
 docky

```

---

### Post by nerdopolis on 2009-11-30
[COLOR=Black]try ```
[/COLOR][COLOR=Black]sudo apt-get -f install
``` 
[/COLOR]

---

### Post by max_power on 2009-12-01
yup that worked!

Thanks for sticking with me here.

---

### Post by max_power on 2009-12-07
I was able to force the Installation but now there are error when trying to run the program. Here is the error message:

```
$ docky

** (/usr/lib/docky/Docky.exe:2218): WARNING **: The following assembly referenced from /usr/lib/docky/Docky.exe could not be loaded:
     Assembly:   Mono.GetOptions    (assemblyref_index=17)
     Version:    2.0.0.0
     Public Key: 0738eb9f132ed756
The assembly was not found in the Global Assembly Cache, a path listed in the MONO_PATH environment variable, or in the location of the executing assembly (/usr/lib/docky/).


** (/usr/lib/docky/Docky.exe:2218): WARNING **: Could not load file or assembly 'Mono.GetOptions, Version=2.0.0.0, Culture=neutral, PublicKeyToken=0738eb9f132ed756' or one of its dependencies.

Unhandled Exception: System.TypeLoadException: Could not load type 'Docky.Docky' from assembly 'Docky, Version=0.1.0.0, Culture=neutral, PublicKeyToken=null'.

```

---

