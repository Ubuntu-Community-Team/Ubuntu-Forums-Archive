---
title: "How to; rapidshare on ubuntu"
date: 2010-03-11
forum: General Help
---

### Post by ninuhadida on 2010-03-11
Hi,

I'm a regular user of rapidshare and I've seen some questions before on the internet in general on how to download multiple files automatically.

I have devised my own way, using mainly wget. It's pretty simple, uses the command line exclusively. GUI users please don't run away. With some determination you can easily get going with this.

Basically there are a couple of steps;

[LIST=1]
[*]get rapidshare cookie (to authenticate)
[*]create a text file with a list of urls you'd like to download
[*]run wget to download files
[/LIST]

Open up a terminal.

create a directory in /home/user/ to store our stuff
```

cd ~
mkdir rapidshare
cd rapidshare

```

open up your favourite text editor.. gedit/kate/vi/whatever. copy and paste the code below and save it to ~/rapidshare/cookie.sh (advanced users, feel free to point out improvements)
```

#!/bin/bash
#script to retrieve cookie from rapidshare

#config
COOKIE="cookie.txt"
URL="https://ssl.rapidshare.com/cgi-bin/premiumzone.cgi"

#ask for login details
echo -n "Login: " 
read LOGIN
echo -n "Password: "

#protect for interrupts
#if script terminated
#set bash to turn off silent read
trap "stty echo ; exit" 1 2 15 
stty -echo #set silent read
read PASSWORD #read password
stty echo #turn off silent read
#reset trap to do nothing if terminated
trap "" 1 2 15

#newline
echo ""

#call rapidshare login page and save cookie
#-q sets wget to quiet mode (no output)
#--post-data sends login details to page
wget -q --save-cookies $COOKIE --post-data "login=$LOGIN&password=$PASSWORD" -- $URL

#delete downloaded html file
rm premiumzone.cgi

#if login was successful
#cookie file will contain 5 lines
#else only 4 lines since no data saved

#read number of lines
nl=$(($(wc -l<$COOKIE)))

#if cookie successful
if [ $nl = 5 ]; then
	echo "Cookie created successfully!"
	exit 0
else
	rm $COOKIE
	echo "Failed!"
	exit 1
fi

```

using the terminal, run
```

sh cookie.sh

```

that should ask you for your rapidshare login and password. a new file called cookie.txt will be created.

time to open up you favourite editor again. paste the rapidshare urls you'd like to download, line by line and save it to ~/rapidshare/urls.txt

now it's time to actually use wget and start downloading!

```

wget -v -i urls.txt --load-cookies cookie.txt

```

-v is to show what's going on.. resolving, download process, etc
-i tells wget from where to get the urls
--load-cookies load our previously downloaded cookie.. authenticating us to download the files we want.

the files you pointed out in urls.txt will now be downloaded to ~/rapidshare

if you find this useful, have improvements or questions, let me know. :)

---

### Post by Intrepid Ibex on 2010-03-11
Shouldn't this be in the 'Tutorials & Tips' section, where it will also not be buried with other non-related topics :)?

---

### Post by ninuhadida on 2010-03-11
> **Intrepid Ibex said:**
> Shouldn't this be in the 'Tutorials & Tips' section, where it will also not be buried with other non-related topics :)?

makes sense, though I'm a newbie here. any mods that will kindly move it? :)

---

