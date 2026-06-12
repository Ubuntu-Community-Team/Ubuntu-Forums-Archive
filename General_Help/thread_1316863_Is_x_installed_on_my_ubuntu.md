---
title: "Is x installed on my ubuntu?"
date: 2009-11-06
forum: General Help
---

### Post by fifoKamb3 on 2009-11-06
Hello,
How I know if a certain program (service, package, application, protocol, .. ) is installed or not?

Is there any command I can use?
Thank you.
Br

---

### Post by gwpritch on 2009-11-06
Use the synaptic package manager. To get a list of all installed packages click on 'by status' (or something to that effect) on the left panel then select installed. Or you can search for a specific package using the search tool.

---

### Post by Giblet5 on 2009-11-06
```
sudo dpkg-l | awk '{ print $2 }' | sed -e '1,5d' | grep -i [COLOR="Blue"]XXX[/COLOR]
```

Replace XXX with a packagename or part of one.

If you have anything like it, it will be listed.

---

### Post by HiImTye on 2009-11-06
```
aptitude search <package name>
```anything installed will start with an i and anything not installed will start with a p

for instance, this is my search of Yakuake:
```
tye@T:~$ aptitude search yakuake
i   yakuake                                                                           - a Quake-style terminal emulator based on KDE Konsole technology
p   yakuake-kde4                                                                      - Transitional package
```as you can see, yakuake is installed (i) while the yakuake-kde4 package is not (p)

this is the information from the aptitude man page (man aptitude)
```
       search
           Searches for packages matching one of the patterns supplied on the command line. All packages which match any of the given patterns will be displayed; for
           instance, &#8220;aptitude search ´~N´ edit&#8221; will list all &#8220;new&#8221; packages and all packages whose name contains &#8220;edit&#8221;. For more information on search patterns, see the
           section &#8220;Search Patterns&#8221; in the aptitude reference manual.

           Unless you pass the -F option, the output of aptitude search will look something like this:

               i   apt                             - Advanced front-end for dpkg
               pi  apt-build                       - frontend to apt to build, optimize and in
               cp  apt-file                        - APT package searching utility -- command-
               ihA raptor-utils                    - Raptor RDF Parser utilities

           Each search result is listed on a separate line. The first character of each line indicates the current state of the package: the most common states are p, meaning
           that no trace of the package exists on the system, c, meaning that the package was deleted but its configuration files remain on the system, i, meaning that the
           package is installed, and v, meaning that the package is virtual. The second character indicates the stored action (if any; otherwise a blank space is displayed)
           to be performed on the package, with the most common actions being i, meaning that the package will be installed, d, meaning that the package will be deleted, and
           p, meaning that the package and its configuration files will be removed. If the third character is A, the package was automatically installed.

           For a complete list of the possible state and action flags, see the section &#8220;Accessing Package Information&#8221; in the aptitude reference guide. To customize the
           output of search, see the command-line options -F and --sort.

```

---

### Post by fifoKamb3 on 2009-11-06
Thank you.
I am using the server edition (bash shell) not the desktop. Yes, with desktop I just use the synaptic package manager.

I am going to try the codes above.

Thanks again!

---

