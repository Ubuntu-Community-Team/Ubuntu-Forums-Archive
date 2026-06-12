---
title: "Error updating to dapper 6.06?"
date: 2006-06-15
forum: General Help
---

### Post by getzy on 2006-06-15
The first error i get is:
[I]
W: Couldn't stat source package list [http://koti.mbnet.fi](http://koti.mbnet.fi) breezy/ Packages (/var/lib/apt/lists/koti.mbnet.fi_%7eots_ubuntu_breezy_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://theli.free.fr](http://theli.free.fr) ./ Packages (/var/lib/apt/lists/theli.free.fr_packages_breezy_._Packages) - stat (2 No such file or directory)[/I]

The second error i get is: 
[I]Failed to fetch [http://koti.mbnet.fi/~ots/ubuntu/breezy/Packages.gz](http://koti.mbnet.fi/~ots/ubuntu/breezy/Packages.gz) 404 Not Found
Failed to fetch [http://koti.mbnet.fi/~ots/ubuntu/breezy/Sources.gz](http://koti.mbnet.fi/~ots/ubuntu/breezy/Sources.gz) 404 Not Found
Failed to fetch [http://theli.free.fr/packages/breezy/./Packages.gz](http://theli.free.fr/packages/breezy/./Packages.gz) 404 Not Found[/I]

Hopefully somebody can help me out :eek: 

Best regards
Daniel Paul Getz

---

### Post by Sutekh on 2006-06-15
A couple of things here.  

Firstly this repository has gone down.  This is the reason for the error.

I'm not sure there is a replacement one, that you can use for the packages that were there. Have you used an application such as Automatix, which may have altered your reposes list and added this?

Secondly, and trivially given the circumstances, if this *were* still a functioning repository and you were *dist-upgrading*, you would need to change the source to contain dapper instead of breezy.


All you need to do is remove the dead repository, by editing your sources. First open a Terminal window, from the Applications -> Accessories menu to use these following commands. 

These commands backup and edit the sources file
```
sudo cp /etc/apt/sources.list /etc/apt/sources.list_backup
sudo gedit /etc/apt/sources.list
``` 
When the editor opens, simply 'comment out' the offending sources, by placing a # at the beginning of the line.

Save the file and use
```
sudo apt-get update
``` To refresh the list.  If this error was stopping you from *dist-upgrading* then feel free to try again, now you've removed the lines.

---

