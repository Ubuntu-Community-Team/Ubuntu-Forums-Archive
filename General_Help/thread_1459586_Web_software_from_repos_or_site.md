---
title: "Web software from repos or site?"
date: 2010-04-21
forum: General Help
---

### Post by gvernold on 2010-04-21
I produce a lot of work under Drupal, Wordpress and Moin. Previously I have always downloaded the software packages for these from the developers website and installed it manually. When I install it manually it is fairly easy to see where files and directories have been created and I just get on with the projects.

I've just noticed that the above three packages are available in the repositories. Is it better to install from the repositories or manually with this kind of software?

The reason I ask is because a software package like Gimp just appears in my start menu so I naturally would download it from the repo. But if I download something like Wordpress I can see it is installed through synaptic but does it actually produce any new directories or files in somewhere like /var/www? I'm not sure how I would access the software once it is installed. The W3 Validator for instance, I downloaded in 8.10 but although it was showing installed there was no obvious way to access it.

---

### Post by no2498 on 2010-04-21
if you do not see it under applications
open a terminal and type its name
you may need to use sudo on some

hope this helps
repositories you can uninstall the same way

---

### Post by agnes on 2010-04-21
I have no experience with any of that software.
But just saying some general things that may help you.

_Downside repos: _
- a program in the repositories is often of an earlier version, than the most recent version. Because the .deb's of the programs are included in the repo's when the distro came out. But the developers may have made available a new (source) version in the meantime on their website.
- you can' t control install directory.  Usually this should be /usr/bin. But sometimes you will have to run a script first to fully install the program, even though you got the .deb. For Wordpress [this article]("https://help.ubuntu.com/community/WordPress") shows a script is involved for full installation when WordPress is installed via the repos.

_Downside manual install:_
- dependencies you must install yourself, if you build from source.
- if you build from source, you can't uninstall the program via Synaptic.

> The W3 Validator for instance, I downloaded in 8.10 but although it was showing installed there was no obvious way to access it. 
If you can't find the executable for a program for example W3 validator
type
*sudo find / -iname "*w3*"*
will find any files with "w3" in them, of which some obviously will point to the W3 validator install directory and executable.

---

### Post by wojox on 2010-04-21
I download Wordpress from their site but set it up like ubuntu [uhelp]https://help.ubuntu.com/community/WordPress[/uhelp]

---

### Post by Jive Turkey on 2010-04-21
If you are comfortable with the source installation of those webapps I would go that way. installing those particular things you mentioned from the repositories puts stuff in places that might not be obvious and there is a risk that the documentation won't have answers that you need (both ubuntu's or the web app developer) You can still use synaptic to find and install the dependencies of those packages.

Furthermore, wordpress and drupal etc are designed to be installed on a webserver's document root so its not really as tedious as compiling a source package or anything like that.  You will ultimately have more control of the software since you won't be trying to figure out what apt did with your files.  Also you will be able to create multiple instantiations of the software, while AFAIK you will only be able run one wordpress or drupal from a given server if you install via package manager.  I'm sure there are ways around that but you aren't likely to find good instructions for doing it.

With web facing applications it is also a good idea to use the latest versions and keep them up to date, which will probably be faster than waiting for them to be repackaged.

---

