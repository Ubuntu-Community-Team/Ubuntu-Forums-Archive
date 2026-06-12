---
title: "Lux Delux"
date: 2010-08-05
forum: General Help
---

### Post by grant4353 on 2010-08-05
Hey,

I'm still a beginner when it comes to using Ubuntu, I recently bough Lux Delux and I'm having some difficult installing it, it's a tar.gz file. Anyone here ever install that game or have any advice on how to install it? 

Thanks!!

---

### Post by oldos2er on 2010-08-05
After you extract the tar.gz, read README.txt.

---

### Post by elliotn on 2010-08-05
If ur new, stay away from source codes coz u will have a headache. Use synaptic its the easiest

---

### Post by grant4353 on 2010-08-05
When you say extract, what do you mean? 

I did read the Readme, it doesn't really make any sense to me:


#!/bin/sh

# Edit this line to list where you have installed Lux Delux:
installFolder="/home/change_this_part/LuxDelux"

# That way you can create shortcuts from wherever and they will work.


## First thing we do is check for the location of the install folder

if [ -f LuxCore.jar ]
then
    pathtofolder="."
else 
    if [ -f "LuxDelux/LuxCore.jar" ]
    then
        pathtofolder="./LuxDelux"
    else
        if [ -f "$installFolder/LuxCore.jar" ]
        then
            pathtofolder="$installFolder"
        else
            echo "The start up script could not find the location"
            echo "of the install folder. Edit the Lux.sh script"
            echo "to specify the proper install location."
            echo "Specify a path now and the script will try it:"
            read pathtofolder
        fi
    fi
fi


## Now the $pathtofolder var should contain the location of the install dir
## If it doesn't, we won't be able to launch Lux


echo "Lux Delux: Starting up..."


# By default Lux will print output to both
# stdout AND to ./Support/log.txt.

# This line redirects the stdout output to /dev/null
# and launches Lux in the background.

$pathtofolder/linux-private-jre/bin/java -jar "$pathtofolder/LuxCore.jar" >> /dev/null &

---

### Post by grant4353 on 2010-08-05
So I clicked on the .jar file thing and opened with java and it works, now I'm wondering if I'll have to do that everytime, and if I'll have to re download updates each time/register too.

---

