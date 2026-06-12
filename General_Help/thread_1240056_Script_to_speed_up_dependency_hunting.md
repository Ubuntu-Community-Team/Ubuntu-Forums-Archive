---
title: "Script to speed up dependency hunting"
date: 2009-08-14
forum: General Help
---

### Post by smani on 2009-08-14
A little script I wrote to install a package that provides a specified file:

```

#!/bin/bash
# Installs package that provides the specified file, using apt-file
# Written by Sandro Mani (smani@student.ethz.ch)
# Licence: GPL
# Version: 14.08.2009


if [ "$1" == "" ]; then
	echo -e "\nInstalls the package providing the specified file.\n  Usage: $0 filename\n  filename: name or complete path of the file to search,\n            can contain RegExp patterns.\n\n";
	exit 0;
fi;

file=/$1;
file=${file//\/\//\/};

if [ "$(aptitude search '~i ^apt-file$')" == "" ]; then
	echo -n "You need to install apt-file to use this script. Proceed? [Y/n] ";
	read confirm;
	if [ "$confirm" != "" ] && [ "$confirm" != "Y" ] && [ "$confirm" != "y" ]; then
		echo "Aborting...";
		exit 0;
	fi;
	sudo apt-get install apt-file;
	echo "Updating apt-file cache...";
	apt-file update;
fi;

list=$(apt-file search -x $file'$')

packages=$(echo -e "$list" | awk -F: '{print $1}');

packages=$(echo -e "$packages" | uniq);

count=$(echo -e "$packages" | wc -l);

if [[ "$packages" == "" ]]; then
	echo "No pachage found providing $1.";
	exit 0;
elif [[ $count -gt 1 ]]; then
	count=$(echo -e "$list" | wc -l);
	echo "$count packages provide $1:"
	echo -e "$list" | nl -w2 -s":  ";
	while [ "$choice" == "" ]; do
		echo -n "Please specify which package you want to install [1-$count]: "
		read choice;
		if [ $choice -gt $count ] || [ $choice -lt 1 ]; then
			choice="";
		fi;
	done;
	packages=$(echo -e "$packages" |  awk 'NR=="'"$choice"'"');
else
	echo "Found match for $1:";
	echo "$list"
fi;

if [ "$(aptitude search '~i ^'$packages'$')" != "" ]; then
	echo "The package $packages is already installed. Aborting...";
	exit 0;
fi;

echo -n "Install package $packages? [Y/n] ";
read confirm;
if [ "$confirm" != "" ] && [ "$confirm" != "Y" ] && [ "$confirm" != "y" ]; then
	echo "Aborting...";
	exit 0;
fi;
sudo apt-get install $packages;

exit 0;

```

Usage examples (I called the script install-providing):

install-providing stdlib.h

or

install-providing /usr/include/stdlib.h

Happy dependency hunting:D

smani

---

