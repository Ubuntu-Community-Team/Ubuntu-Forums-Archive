---
title: "Script to move files to new folders"
date: 2009-12-12
forum: General Help
---

### Post by zgerrz on 2009-12-12
Hello,

I have a large collection of movies dumped into a network folder and need a special script.

I want to move each .avi movie file in a new folder titled the same as the movie. I'm doing this so that I can add subtitle files and other data in each movie folder. For example, I would need the movie "Aliens" to be moved into a new folder called "Aliens." I need the same thing to happen with about 300 other movies in the same directory.

Thanks!

---

### Post by staf0048 on 2009-12-13
Not sure if this will help or not, but not too long ago I did some tinkering around with shell scripts and wrote a script that would install scripts to whatever directory I wanted.  

I abandoned my idea simply because I found I didn't use shell script all that much, but if it helps here's what I came up with.

You should be able to tweak it to fit your needs, if your not familiar with shell scripting I'd be happy to make some changes for you, I just don't know when I'd be able to get around to it.

Let me know if you have any questions.

I tried to upload this as a file, but it didn't work.  So just copy and paste the code into a text editor, save it as "installscript" or whatever you want and invoke it from the command line w/ ./installscript.  There is a GUI front end to help you through the rest of the process.

```

#!/bin/bash

#This script is used to install custom scripts to /usr/local/bin

########## constants  Work on saving defualts to home dir and reading upon startup.
version="InstallScript_v1.3"
tmpfile=".tempfile.txt"

########## Functions

##### Main Menu
menu () {

	gdialog --title $version --menu "Main Menu" 15 50 5 1 "Instructions" 2 "System Defaults" 3 "Install using prompts" 4 "Credits" 5 "Exit" 2>$tmpfile
	usrmain=$(cat $tmpfile)
		
		case "$usrmain" in
			1 ) instructions;;
			2 ) defaults;;
			3 ) install;;
			4 ) information;;
			5 ) rm $tmpfile
			    sleep 2
			    gdialog --clear
			    exit 0;;
			* ) echo "Error: Please try again" && menu;;
		esac

}

##### Instructions Menu

instructions () {
	
	gdialog --title $version --msgbox "Instructions:  It is easiest to just use the command line to install a script using this format: $ installscript [file] [path] [owner] [group] [permissions]

For example, to install this script one would type $ installscript installscript /usr/local/bin root root 755

Good luck and happy scripting!!!" 25 25
	
		menu
}

##### System Defaults Function

defaults () {

	gdialog --title $version --menu "System Defaults: Select to change" 15 50 4 1 "Current Path: $defaultpath" 2 "Current Owner: $defaultown" 3 "Current Group: $defaultgrp" 4 "Current Permissions: $defaultmod" 2>$tmpfile
	usrdef=$(cat $tmpfile)
		
			case "$usrdef" in
				1 ) gdialog --title $version --inputbox "Please set a new default path" 2>.path.txt
					defaultpath=$(cat .path.txt) 
					defaults;;

				2 ) gdialog --title $version --inputbox "Please set a new default owner" 2>.own.txt
					defaultown=$(cat .own.txt) 
					defaults;;

				3 ) gdialog --title $version --inputbox "Please set a new default group" 2>.grp.txt 
					defaultgrp=$(cat .grp.txt)
					defaults;;

				4 ) gdialog --title $version --inputbox "Please set new default permissions" 2>.mod.txt
					defaultmod=$(cat .mod.txt) 
					defaults;;

				* ) menu;;
			esac
}

##### Install a Script function

install () {
	gdialog --title $version --inputbox "Enter the name of the script you wish to install" 15 50 2>$tmpfile
	usrfile=$(cat $tmpfile)

	gdialog --title $version --yesno "Would you like to use system defaults for the rest of the process?" 15 50
		if [ $? != 0 ]; then
			
			gdialog --title $version --inputbox "Please specify a path to install.  For example '/usr/local/bin'" 15 50 2>$tmpfile
			usrpath=$(cat $tmpfile)
			
			gdialog --title $version --inputbox "Please specify a an owner.  For example 'root'" 2>$tmpfile
			usrown=$(cat $tmpfile)
						
			gdialog --title $version --inputbox "Please specify a group.  For exampe 'root'" 2>$tmpfile
			usrgrp=$(cat $tmpfile)
			
			gdialog --title $version --inputbox "Please specify permissions.  For example '755' or 'a+x'" 2>$tmpfile
			usrmod=$(cat $tmpfile)
			
			sudo cp $usrfile $usrpath
			echo "Installing script..."
			echo "Setting privlages..."
			sudo chown $usrown $usrpath/$usrfile
			sudo chgrp $usrgrp $usrpath/$usrfile
			sudo chmod $usrmod $usrpath/$usrfile
		else 
			sudo cp $usrfile $defaultpath
			echo "Installing script..."
			echo "Setting privlages..."
			sudo chown $defaultown $defaultpath/$usrfile
			sudo chgrp $defaultgrp $defaultpath/$usrfile
			sudo chmod $defaultmod $defaultpath/$usrfile
		fi
				
}

##### Information

information () {

	gdialog --title $version --msgbox "This Script was developed by Brian Stafford.
	
Please send questions, comments, criticisms, or praise to estafford19@cox.net.

Be sure to put 'InstallScript' in the subject line so I may respond to your email more quickly.

Thank you for using InstallScript."

	menu
	
}


##### Check2 function

check2 () {
 # Check if user specified a path
	if [ "$usrpath" != "" ]; then
		check3
	else
		echo "Would you like to use system defaults for the rest of the installation process? (y/n):"
		read chk2
			case "$chk2" in
				[yY]|[Yy][Ee][Ss] )			
					sudo cp $usrfile $defaultpath
					echo "Installing script..."
					echo "Setting privlages..."
					sudo chown $defaultown $defaultpath/$usrfile
					sudo chgrp $defaultgrp $defaultpath/$usrfile
					sudo chmod $defaultmod $defaultpath/$usrfile
					;;
				
				[nN]|[Nn][Oo] )
					echo "Please specify a path to install.  For example '/usr/local/bin'"
					read usrpath
					echo " "
					echo "Please specify a an owner.  For example 'root'"
					read usrown
					echo " "			
					echo "Please specify a group.  For exampe 'root'"
					read usrgrp
					echo " "
					echo "Please specify permissions.  For example '755' or 'a+x'"
					read usrmod
					echo " "
					sudo cp $usrfile $usrpath
					echo "Installing script..."
					echo "Setting privlages..."
					sudo chown $usrown $usrpath/$usrfile
					sudo chgrp $usrgrp $usrpath/$usrfile
					sudo chmod $usrmod $usrpath/$usrfile
					;;

				* ) echo "Error: Please try again" && install;;
			esac
	fi
}

##### Check3 function

check3 () {
 # Check if user specified an owner
	if [ "$usrown" != "" ]; then
		check4
	else
		echo "Would you like to use system defaults for the rest of the installation process? (y/n):"
		read chk3
			case "$chk3" in
				[yY]|[Yy][Ee][Ss] )			
					sudo cp $usrfile $usrpath
					echo "Installing script..."
					echo "Setting privlages..."
					sudo chown $defaultown $usrpath/$usrfile
					sudo chgrp $defaultgrp $usrpath/$usrfile
					sudo chmod $defaultmod $usrpath/$usrfile
					;;
				
				[nN]|[Nn][Oo] )
					echo "Please specify a an owner.  For example 'root'"
					read usrown
					echo " "			
					echo "Please specify a group.  For exampe 'root'"
					read usrgrp
					echo " "
					echo "Please specify permissions.  For example '755' or 'a+x'"
					read usrmod
					echo " "
					sudo cp $usrfile $usrpath
					echo "Installing script..."
					echo "Setting privlages..."
					sudo chown $usrown $usrpath/$usrfile
					sudo chgrp $usrgrp $usrpath/$usrfile
					sudo chmod $usrmod $usrpath/$usrfile
					;;

				* ) echo "Error: Please try again" && install;;
			esac
	fi
}

##### Check4 function

check4 () {
  # Check if user specified a group
	if [ "$usrgrp" != "" ]; then
		check5
	else
		echo "Would you like to use system defaults for the rest of the installation process? (y/n):"
		read chk4
			case "$chk4" in
				[yY]|[Yy][Ee][Ss] )			
					sudo cp $usrfile $usrpath
					echo "Installing script..."
					echo "Setting privlages..."
					sudo chown $usrown $usrpath/$usrfile
					sudo chgrp $defaultgrp $usrpath/$usrfile
					sudo chmod $defaultmod $usrpath/$usrfile
					;;
				
				[nN]|[Nn][Oo] )
					echo "Please specify a group.  For exampe 'root'"
					read usrgrp
					echo " "
					echo "Please specify permissions.  For example '755' or 'a+x'"
					read usrmod
					echo " "
					sudo cp $usrfile $usrpath
					echo "Installing script..."
					echo "Setting privlages..."
					sudo chown $usrown $usrpath/$usrfile
					sudo chgrp $usrgrp $usrpath/$usrfile
					sudo chmod $usrmod $usrpath/$usrfile
					;;

				* ) echo "Error: Please try again" && install;;
			esac
	fi
}

##### Check5 function

check5 () {
  # Check if user specified a permissions
	if [ "$usrmod" != "" ]; then
		sudo cp $usrfile $usrpath
		echo "Installing script..."
		echo "Setting privlages..."
		sudo chown $usrown $usrpath/$usrfile
		sudo chgrp $usrgrp $usrpath/$usrfile
		sudo chmod $usrmod $usrpath/$usrfile
	else
		echo "Would you like to use system defaults for the rest of the installation process? (y/n):"
		read chk5
			case "$chk5" in
				[yY]|[Yy][Ee][Ss] )			
					sudo cp $usrfile $usrpath
					echo "Installing script..."
					echo "Setting privlages..."
					sudo chown $usrown $usrpath/$usrfile
					sudo chgrp $usrgrp $usrpath/$usrfile
					sudo chmod $defaultmod $usrpath/$usrfile
					;;
				
				[nN]|[Nn][Oo] )
					echo "Please specify permissions.  For example '755' or 'a+x'"
					read usrmod
					echo " "
					sudo cp $usrfile $usrpath
					echo "Installing script..."
					echo "Setting privlages..."
					sudo chown $usrown $usrpath/$usrfile
					sudo chgrp $usrgrp $usrpath/$usrfile
					sudo chmod $usrmod $usrpath/$usrfile
					;;

				* ) echo "Error: Please try again" && install;;
			esac
	fi
}

##### Check if pathfile exists

pathfile () {
	if [ -s .path.txt ]; then
		ownfile
	else
		touch .path.txt
		echo "/usr/local/bin">>.path.txt
		ownfile
	fi
}

##### Check if Ownfile exists

ownfile () {
	if [ -s .own.txt ]; then
		grpfile
	else
		touch .own.txt
		echo "root">>.own.txt
		grpfile
	fi
}

##### Check if grpfile exists

grpfile () {
	if [ -s .grp.txt ]; then
		modfile
	else
		touch .grp.txt
		echo "root">>.grp.txt
		modfile
	fi
}

##### Check if modfile exists

modfile () {
	if [ -s .mod.txt ]; then
		echo ""
	else
		touch .mod.txt
		echo "755">>.mod.txt
	fi
}


########### Main

# Check if user specified a file to install


if [ "$1" != "" ]; then
	usrfile=$1
	usrpath=$2
	usrown=$3
	usrgrp=$4
	usrmod=$5
	pathfile
	defaultpath=$(cat .path.txt)
	defaultown=$(cat .own.txt)
	defaultgrp=$(cat .grp.txt)
	defaultmod=$(cat .mod.txt)
	check2
else
	pathfile
	defaultpath=$(cat .path.txt)
	defaultown=$(cat .own.txt)
	defaultgrp=$(cat .grp.txt)
	defaultmod=$(cat .mod.txt)
	menu
fi

##### Cleanup and exit

rm $tmpfile
sleep 2
gdialog --clear	
exit 0

```

---

### Post by zgerrz on 2009-12-13
Wow this looks pretty complicated. I was hoping for a much simpler and smaller script since in this one it's hard for me to figure out what's going on. I'm no expert at shell scripts.

I was wondering if you could tweak it or simplify it so I could just run it as a bash script by invoking the sh command.

Thanks for all your help thus far!

---

### Post by LuisGMarine on 2009-12-13
> **zgerrz said:**
> Wow this looks pretty complicated. I was hoping for a much simpler and smaller script since in this one it's hard for me to figure out what's going on. I'm no expert at shell scripts.

I was wondering if you could tweak it or simplify it so I could just run it as a bash script by invoking the sh command.

Thanks for all your help thus far!

Don't know if someone is going to sit here and write YOU a script ... best way is to learn it yourself and if you run into problems then post.

---

### Post by zgerrz on 2009-12-13
No need to be a total prick about it...

I had hoped someone already had a similar script they had written. If you can't provide any decent help then kindly piss off.

> **LuisGMarine said:**
> Don't know if someone is going to sit here and write YOU a script ... best way is to learn it yourself and if you run into problems then post.

---

### Post by Primefalcon on 2009-12-13
> **zgerrz said:**
> No need to be a total prick about it...

I had hoped someone already had a similar script they had written. If you can't provide any decent help then kindly piss off.

Easy people, nothing wrong with hoping someone else had a similar script already written, a lot of us do keep out own library of scripts to make things easy..., though zgerrz getting aggressive in return doesn't help your case either, peace out 

you might have to do this manually though by using grep for example

create a  folder called aliens then just run 


```
find /path/to/folder -name aliens -exec mv /aliens/folder
```

I know thats prob not exactly what you were hoping for, but short of having a script for you that might shorten your task a little, hopefully

---

### Post by mo.reina on 2009-12-13
```
#!/bin/bash

#**creates temp file with a list of all the .avi files**
find */base_directory_here/* -name \*.avi -exec echo '{}' \; >> find.temp

**#strips the pathname from the temp list, leaving only the filename, creates a dir matching that file name, moves the file from original location to new directory**
while read line; do
	new=$(echo $line | sed -e 's/.*\(\/.*avi\)/\1/' -e 's/\///')
	mkdir "$new"
	mv "$line" $new/
done < find.temp

**#removes temp file**
rm find.temp

```

note that this will create the new directory in the same directory you run the script in.. so if you have a specific place you want to put the new directory in, script it in..

---

### Post by Primefalcon on 2009-12-13
> **mo.reina said:**
> ```
#!/bin/bash

#**creates temp file with a list of all the .avi files**
find */base_directory_here/* -name \*.avi -exec echo '{}' \; >> find.temp

**#strips the pathname from the temp list, leaving only the filename, creates a dir matching that file name, moves the file from original location to new directory**
while read line; do
	new=$(echo $line | sed -e 's/.*\(\/.*avi\)/\1/' -e 's/\///')
	mkdir "$new"
	mv "$line" $new/
done < find.temp

**#removes temp file**
rm find.temp

```

note that this will create the new directory in the same directory you run the script in.. so if you have a specific place you want to put the new directory in, script it in..
Nice script

---

### Post by mo.reina on 2009-12-13
thanks.  i'm sure it can be shortened further but that's the current limit of my scripting skills

---

### Post by DaithiF on 2009-12-13
similar to mo.reina, but eliminating the temporary file, and, just for variety, showing a bash alternative to the sed command for manipulating the filenames
```
find /path/to/dir -name '*.avi' | while read avifile
do
        filename=${avifile##*/}
        dirname=${filename%.avi}
        mkdir "$dirname" && mv "$avifile" "$dirname"
done

```

---

### Post by ghostdog74 on 2009-12-13
bash 4.0+
```

dest="/dest"
shopt -s globstar
for file in /path/**/*.avi; 
do 
  file=${file##*/}
  file=${file%.*}
  if [ ! -d "$dest/$file" ];then
     mkdir "$dest/$file"  
  fi
  mv "$file" "$dest/${file}.avi"  
done

```

---

### Post by mo.reina on 2009-12-13
> **ghostdog74 said:**
> bash 4.0+
```

dest="/dest"
for file in /path/**/*.avi; 
do 
  file=${file##*/}
  file=${file%.*}
  if [ ! -d "$dest/$file" ];then
     mkdir "$dest/$file"  
  fi
  mv "$file" "$dest/${file}.avi"  
done

```

i considered this:
```
for file in /path/**/*.avi; 
```

but in my version of bash it's not recursive, it only shows avi files that are in the '**' directory, if there's another sub directory it doesn't show.  is it any different in version 4.0?

> similar to mo.reina, but eliminating the temporary file, and, just for variety, showing a bash alternative to the sed command for manipulating the filenames

```
find /path/to/dir -name '*.avi' | while read avifile
do
        filename=${avifile##*/}
        dirname=${filename%.avi}
        mkdir "$dirname" && mv "$avifile" "$dirname"
done
```

this is the missing link! i thought there was a way to correctly pipe find but i didn't know how to do it.

---

### Post by StuartN on 2009-12-13
```
for file in /home/me/downloads/*.avi
{
  filebasename=$(basename "$file" .avi)
  mkdir "/home/me/downloads/$filebasename"
  cp "$file" "/home/me/downloads/$filebasename"
}
```

---

### Post by ghostdog74 on 2009-12-13
> **mo.reina said:**
> i considered this:
```
for file in /path/**/*.avi; 
```

but in my version of bash it's not recursive, it only shows avi files that are in the '**' directory, if there's another sub directory it doesn't show.  is it any different in version 4.0?


you will need to do shopt -s globstar, which i forgot to add.

---

### Post by ghostdog74 on 2009-12-13
> **StuartN said:**
> ```
for file in /home/me/downloads/*.avi
{
  filebasename=$(basename "$file" .avi)
  mkdir "/home/me/downloads/$filebasename"
  cp "$file" "/home/me/downloads/$filebasename"
}
```

basename is not necessary since you can use shell internals to get file name without extension. using less external commands makes your script run faster.

---

### Post by zgerrz on 2009-12-20
Thanks a lot for your help guys.

Using a couple of the scripts here I managed to shorten a task that would normally take hours into a task that took only a few minutes.

Thanks!

---

