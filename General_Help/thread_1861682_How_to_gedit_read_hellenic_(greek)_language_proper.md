---
title: "How to: gedit read hellenic (greek) language properly"
date: 2011-10-15
forum: General Help
---

### Post by Claus7 on 2011-10-15
Hello,

I'm trying to make gedit open a file written in ISO-8859-7 and display properly the Hellenic letters. 

[EDIT: take a look on 3rd post about locale]

In order to do so I had to add to the file named local:
 ```
sudo gedit /var/lib/locales/supported.d/local
```

the line:
> el_GR ISO-8859-7

and then refresh locale:
```
sudo dpkg-reconfigure locales
```

In order to open a file I had to type:
```
LANG="el_GR.ISO-8859-7" ; export LANG ; gedit name_of_file.txt
```

mind the dot between the GR and the ISO!!

Finally I modified my .bashrc file by adding the line:
> alias gedit='LANG="el_GR.ISO-8859-7" ; export LANG ; gedit'

and now, via terminal, I can open a file with hellenic content and english one, with no problems.

Still, I want to add a shortcut to gedit, so as to use it graphically as well...

Regards!

---

### Post by Claus7 on 2011-10-16
Hello,

by doing the above procedure, gedit opens the file we want and the options that we have (e.g. file, view, e.t.c.) are in the hellenic language. Of course the same process can be done for other languages as well.

Now, what we want to do: automate the process by being able to click on the file and open it accordingly, instead of using the terminal.

In order to do so we have to do the following steps:

1) create a script (named for example gedit_el.sh):
```
vim gedit_el.sh

```
which will look like this:
> #         [email]patrick.largey@nazeman.org[/email]
#         [www.nazeman.org](www.nazeman.org)
#
# Licence : GNU GPL
#
# Copyright (C) Nazeman
#
# Encoding UTF-8
#
# Ver. 0.9-1 Date: 04.04.2003
# Add compatibilty with Nautilus 2.x
#
# Ver. 0.9-1 Date: 16.02.2002
# Add multiple file open in the same windows
#
# Ver: 0.9  Date: 27.10.2001
# Initial release
#
# Dependence : Nautilus (of course)
#              Gnome-utils (gdialog)
#
#curpath=`echo $NAUTILUS_SCRIPT_CURRENT_URI | sed 's/file:////'`
#cd $curpath
filesall=""
while [ $# -gt 0 ]
        do
                files=`echo "$1" | sed 's/ /\?/g'`
                filesall="$files $filesall"
                shift
        done
LANG="el_GR.ISO-8859-7" ; export LANG ; gedit $filesall&
#gedit $filesall&

[credit given to the one who created that script, I just made some minor modifications]

2) make it executable:
chmod 755 gedit_el.sh

3) place it in such a place, so as nautilus to recognize it: 
/home/*user_name*/.gnome2/nautilus-scripts

where in *user_name*, place your ubuntu username and

4) go and try to open a file by right clicking on it -> go to Scripts -> and choose the one you (just) created (gedit_el.sh). And voila! Your job is done!

Regards!

---

### Post by Claus7 on 2011-10-16
Hello,

with the command:
```
locale -a
```

someone can see all the available locales.

Before doing the procedure described in post 1, the output of the command was:
> C
el_CY.utf8
el_GR
el_GR.utf8
en_AG
en_AG.utf8
en_AU.utf8
en_BW.utf8
en_CA.utf8
en_DK.utf8
en_GB.utf8
en_HK.utf8
en_IE.utf8
en_IN
en_IN.utf8
en_NG
en_NG.utf8
en_NZ.utf8
en_PH.utf8
en_SG.utf8
en_US.utf8
en_ZA.utf8
en_ZW.utf8
POSIX  

and aftewards:
> C
el_CY.utf8
el_GR
**el_GR.iso88597**
el_GR.utf8
en_AG
en_AG.utf8
en_AU.utf8
en_BW.utf8
en_CA.utf8
en_DK.utf8
en_GB.utf8
en_HK.utf8
en_IE.utf8
en_IN
en_IN.utf8
en_NG
en_NG.utf8
en_NZ.utf8
en_PH.utf8
en_SG.utf8
en_US.utf8
en_ZA.utf8
en_ZW.utf8
POSIX  

Regards!

---

