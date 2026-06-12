---
title: "How to install firefox extensions for all users"
date: 2010-05-17
forum: General Help
---

### Post by narnie on 2010-05-17
Hello,

I am wondering the "new way" to install firefox extensions for all users.

From [https://developer.mozilla.org/En/Command_Line_Options]("https://developer.mozilla.org/En/Command_Line_Options") we can see that the "old way" is no longer available.

> -install-global-extension and -install-global-theme have been removed from Gecko 1.9.2 and upwards.

I'm using the Lucid UNE to write this and note that it has these extensions installed for every user:

> Ubuntu Firefox Modifications
webfav

I have several users on many computers and would like to have certain extensions installed for them, such as xmarks, add bookmark here, coolpreview, etc.

I searched the entire root filesystem and didn't find any .xpi files.

Can someone give me an idea on how to do this? How does Ubuntu do it?

With thanks,
Narnie

---

### Post by lovinglinux on 2010-05-17
You won't find any xpi file on the system, because those are not installed as xpi, but as deb. 

To locate where the extensions are installed, use this:

```
locate install.rdf
```

Every extension has an **install.rdf** file, so you can find all installed extensions with that.

Ubuntu Firefox Modifications is located at /usr/share/xul-ext/ubufox

I tried to extract an extension there to see if it would be installed on a new profile, but it didn't.

So I guess you need to package the extension as deb and install it via package manager. See [https://wiki.ubuntu.com/MozillaTeam/Extensions/Packaging](https://wiki.ubuntu.com/MozillaTeam/Extensions/Packaging)

---

### Post by narnie on 2010-05-17
A user at unix.com helped me on this one.

Take a look at 

> 
[https://developer.mozilla.org/en/Installing_extensions](https://developer.mozilla.org/en/Installing_extensions)


This says to unzip xpi to /usr/lib/firefox-addons/extentions.

Make sure permissions are 755 to 775 for dirs and 644 to 664 for files (recommend just setting umask to 0022 while installing).

The trick is to name the directory as the extention ID is called, which is usually something like {2JBUJUB2J4BJ262B42J2} "jibberish"

This can be found in the install.js file if there is one.

Otherwise, you have to look in the install.rdf (which is harder to parse using the shell as it is in xml).

I have a shell script that automates this process for those with install.js written, but am working on a quick learning of python xml parsing for those that don't have install.js to return the extension ID from install.rdf.

I'll post the finish product back here.

---

### Post by lovinglinux on 2010-05-18
> **narnie said:**
> A user at unix.com helped me on this one.

Take a look at 



This says to unzip xpi to /usr/lib/firefox-addons/extentions.

Make sure permissions are 755 to 775 for dirs and 644 to 664 for files (recommend just setting umask to 0022 while installing).

The trick is to name the directory as the extention ID is called, which is usually something like {2JBUJUB2J4BJ262B42J2} "jibberish"

This can be found in the install.js file if there is one.

Otherwise, you have to look in the install.rdf (which is harder to parse using the shell as it is in xml).

I have a shell script that automates this process for those with install.js written, but am working on a quick learning of python xml parsing for those that don't have install.js to return the extension ID from install.rdf.

I'll post the finish product back here.

Thanks for the heads up.

BTW, I don't have any **install.js** file on any of the extensions I develop. There is no such file in the required extension structure. Nevertheless, the extension might include js files with the extension ID inside them. But there is no standard declaration of the extension ID in js files. 

The only files that are certainly to be found are **chrome.manifest** and install.rdf. The last one is where the extension ID is declared. The ID can be a gibberish string like you mentioned or can be an e-mail address. Old extensions usually use the gibberish string. My extensions all have e-mail addresses (fake) as ID.

---

### Post by narnie on 2010-05-18
> **lovinglinux said:**
> Thanks for the heads up.

BTW, I don't have any **install.js** file on any of the extensions I develop. There is no such file in the required extension structure. Nevertheless, the extension might include js files with the extension ID inside them. But there is no standard declaration of the extension ID in js files. 

The only files that are certainly to be found are **chrome.manifest** and install.rdf. The last one is where the extension ID is declared. The ID can be a gibberish string like you mentioned or can be an e-mail address. Old extensions usually use the gibberish string. My extensions all have e-mail addresses (fake) as ID.

Wow, then you are someone I would really wish I had your knowledge. I am very facile with the command line, but have no real programming knowledge/experience and have been trying to learn python as my first entry.

I have been very confused with trying to parse the XML/RDF file of install.rdf.

There can be more than one em:id field and I've given up trying to isolate it using the shell.

I figured out how to on one that uses em:id as a tag as in <em:id>{SDBS565513651Sbs}</em:id> using python and minidom.

However, I stumbled across a install.rdf that uses has this code [COLOR="Red"]**_(DON'T USE THIS CODE, USE THE CODE I WROTE LATER IN THE THREAD)_**[/COLOR]:

```
<?xml version="1.0"?>

<RDF:RDF xmlns:em="http://www.mozilla.org/2004/em-rdf#"

         xmlns:NC="http://home.netscape.com/NC-rdf#"

         xmlns:RDF="http://www.w3.org/1999/02/22-rdf-syntax-ns#">

  <RDF:Description RDF:about="rdf:#$VB9S51"

                   em:id="{ec8030f7-c20a-464f-9b0e-13a3a9e97384}"

                   em:minVersion="3.0"

                   em:maxVersion="3.6.*" />

  <Description RDF:about="rdf:#$wfnx83"

                   em:id="{a463f10c-3994-11da-9945-000d60ca027b}"

                   em:minVersion="0.4"

                   em:maxVersion="1.0" />

  <RDF:Description RDF:about="urn:mozilla:extension:file:cooliris.jar"

                   em:package="content/cooliris/"

                   em:skin="skin/classic/cooliris/"

                   em:locale="locale/cooliris/en-US/" />

  <RDF:Description RDF:about="rdf:#$.B9S51"

                   em:id="{86c18b42-e466-45a9-ae7a-9b95ba6f5640}"

                   em:minVersion="1.7"

                   em:maxVersion="1.8" />

  <RDF:Description RDF:about="urn:mozilla:install-manifest"

                   em:id="{CE6E6E3B-84DD-4cac-9F63-8D2AE4F30A4B}"

                   em:name="CoolPreviews"                   

                   em:version="3.0.1"

                   em:description="Browse Faster. Preview and share links and media without leaving your current page."

                   em:creator="Cooliris Inc, www.cooliris.com"

                   em:optionsURL="chrome://cooliris/content/options3.xul"

                   em:iconURL="chrome://cooliris/skin/new/previews-installer-icon.png">

    <em:file RDF:resource="urn:mozilla:extension:file:cooliris.jar"/>

    <em:targetApplication RDF:resource="rdf:#$VB9S51"/>

    <em:targetApplication RDF:resource="rdf:#$.B9S51"/>

    <em:targetApplication RDF:resource="rdf:#$wfnx83"/>

  </RDF:Description>

</RDF:RDF>


```

The em:id is not in the form of a tag that I can use a simple 

```

doc = minidom.parse('install.rdf')
doc.getElementsByTagName("em:id")[0].childNodes[0].data
```

I don't know how to parse out the em:id when in this format. ERR !

Yours,
Nathan

---

### Post by lovinglinux on 2010-05-18
> **narnie said:**
> Wow, then you are someone I would really wish I had your knowledge. I am very facile with the command line, but have no real programming knowledge/experience and have been trying to learn python as my first entry.

I have been very confused with trying to parse the XML/RDF file of install.rdf.

There can be more than one em:id field and I've given up trying to isolate it using the shell.

I figured out how to on one that uses em:id as a tag as in <em:id>{SDBS565513651Sbs}</em:id> using python and minidom.

However, I stumbled across a install.rdf that uses has this code:

```
<?xml version="1.0"?>

<RDF:RDF xmlns:em="http://www.mozilla.org/2004/em-rdf#"

         xmlns:NC="http://home.netscape.com/NC-rdf#"

         xmlns:RDF="http://www.w3.org/1999/02/22-rdf-syntax-ns#">

  <RDF:Description RDF:about="rdf:#$VB9S51"

                   em:id="{ec8030f7-c20a-464f-9b0e-13a3a9e97384}"

                   em:minVersion="3.0"

                   em:maxVersion="3.6.*" />

  <Description RDF:about="rdf:#$wfnx83"

                   em:id="{a463f10c-3994-11da-9945-000d60ca027b}"

                   em:minVersion="0.4"

                   em:maxVersion="1.0" />

  <RDF:Description RDF:about="urn:mozilla:extension:file:cooliris.jar"

                   em:package="content/cooliris/"

                   em:skin="skin/classic/cooliris/"

                   em:locale="locale/cooliris/en-US/" />

  <RDF:Description RDF:about="rdf:#$.B9S51"

                   em:id="{86c18b42-e466-45a9-ae7a-9b95ba6f5640}"

                   em:minVersion="1.7"

                   em:maxVersion="1.8" />

  <RDF:Description RDF:about="urn:mozilla:install-manifest"

                   em:id="{CE6E6E3B-84DD-4cac-9F63-8D2AE4F30A4B}"

                   em:name="CoolPreviews"                   

                   em:version="3.0.1"

                   em:description="Browse Faster. Preview and share links and media without leaving your current page."

                   em:creator="Cooliris Inc, www.cooliris.com"

                   em:optionsURL="chrome://cooliris/content/options3.xul"

                   em:iconURL="chrome://cooliris/skin/new/previews-installer-icon.png">

    <em:file RDF:resource="urn:mozilla:extension:file:cooliris.jar"/>

    <em:targetApplication RDF:resource="rdf:#$VB9S51"/>

    <em:targetApplication RDF:resource="rdf:#$.B9S51"/>

    <em:targetApplication RDF:resource="rdf:#$wfnx83"/>

  </RDF:Description>

</RDF:RDF>


```

The em:id is not in the form of a tag that I can use a simple 

```

doc = minidom.parse('install.rdf')
doc.getElementsByTagName("em:id")[0].childNodes[0].data
```

I don't know how to parse out the em:id when in this format. ERR !

Yours,
Nathan

Those are target applications ID's. The install.rdf also include the ID of the application that is compatible with the extension. In this case:

Firefox
{ec8030f7-c20a-464f-9b0e-13a3a9e97384}

Flock Browser
{a463f10c-3994-11da-9945-000d60ca027b} 

Mozilla Suite
{86c18b42-e466-45a9-ae7a-9b95ba6f5640}

So the extension ID is CE6E6E3B-84DD-4cac-9F63-8D2AE4F30A4B.

Usually, the install.rdf is simpler than that and include the target application ID element under a distinct xml element - <em:targetApplication>.

Here is a script to install your extensions semi-automatically:


```
#!/bin/bash

#select the extension xpi to be installed globally
FILE=$(zenity --file-selection)

#create a clean temporary Firefox profile
firefox -no-remote -CreateProfile TestProfile

#open the extension with the new profile
firefox -no-remote -P "TestProfile" file:///${FILE}

#fetch the extension ID from the installation folder name
EXTENSIONID=$(ls $HOME/.mozilla/firefox/*.TestProfile/extensions)

#create a new global folder using the extension ID
sudo mkdir /usr/lib/firefox-addons/extensions/${EXTENSIONID}

#unzip the extension to the new global folder
sudo unzip ${FILE} -d /usr/lib/firefox-addons/extensions/${EXTENSIONID}

#shut down firefox
killall firefox-bin

#delete the test profile folder
rm -r $HOME/.mozilla/firefox/*.TestProfile

#remove the test profile from profile.ini
sed -i -e 's/.*TestProfile.*//g' $HOME/.mozilla/firefox/profiles.ini

```

When you start the script it will prompt for the xpi file. After that it will launch a separate instance of Firefox with a new temporary profile (won't affect your current installation) and prompt for the extension installation. Install it, then restart Firefox so the extension can be installed, then close Firefox to let the script continue. It will install the extension in the /usr/lib/firefox-addons/extensions/ and remove the test profile from your system.

This is a very basic script that doesn't check if the file exists or if the user interrupted the installation. So you can add this to the code or make sure you don't interrupt the process, otherwise you might end with an empty extension folder in  /usr/lib/firefox-addons/extensions/

---

### Post by narnie on 2010-05-18
> **lovinglinux said:**
> Those are target applications ID's. The install.rdf also include the ID of the application that is compatible with the extension. In this case:

Firefox
{ec8030f7-c20a-464f-9b0e-13a3a9e97384}

Flock Browser
{a463f10c-3994-11da-9945-000d60ca027b} 

Mozilla Suite
{86c18b42-e466-45a9-ae7a-9b95ba6f5640}

So the extension ID is CE6E6E3B-84DD-4cac-9F63-8D2AE4F30A4B.

Usually, the install.rdf is simpler than that and include the target application ID element under a distinct xml element - <em:targetApplication>.

Here is a script to install your extensions semi-automatically:


```
#!/bin/bash

#select the extension xpi to be installed globally
FILE=$(zenity --file-selection)

#create a clean temporary Firefox profile
firefox -no-remote -CreateProfile TestProfile

#open the extension with the new profile
firefox -no-remote -P "TestProfile" file:///${FILE}

#fetch the extension ID from the installation folder name
EXTENSIONID=$(ls $HOME/.mozilla/firefox/*.TestProfile/extensions)

#create a new global folder using the extension ID
sudo mkdir /usr/lib/firefox-addons/extensions/${EXTENSIONID}

#unzip the extension to the new global folder
sudo unzip ${FILE} -d /usr/lib/firefox-addons/extensions/${EXTENSIONID}

#shut down firefox
killall firefox-bin

#delete the test profile folder
rm -r $HOME/.mozilla/firefox/*.TestProfile

#remove the test profile from profile.ini
sed -i -e 's/.*TestProfile.*//g' $HOME/.mozilla/firefox/profiles.ini

```

When you start the script it will prompt for the xpi file. After that it will launch a separate instance of Firefox with a new temporary profile (won't affect your current installation) and prompt for the extension installation. Install it, then restart Firefox so the extension can be installed, then close Firefox to let the script continue. It will install the extension in the /usr/lib/firefox-addons/extensions/ and remove the test profile from your system.

This is a very basic script that doesn't check if the file exists or if the user interrupted the installation. So you can add this to the code or make sure you don't interrupt the process, otherwise you might end with an empty extension folder in  /usr/lib/firefox-addons/extensions/

Wow, that is really neat. Thanks for teaching me about making the test profiles. My ultimate goal is to make it a little more automated where I can teach users to run it (on multiple extensions, too, in one instance).

For extensions with install.js, this script works great (but you have taught me that install.js is not a necessary spec, so I'm back to the install.rdf):

```
setUp () {
	umask 0022
	if [ -d $TMPDIR ] ; then
		(cd $TMPDIR ; rm -rf *)
	else
		sudo mkdir -p "$TMPDIR"
	fi
	sudo unzip "$EXT" -d "$TMPDIR"
}

getID () {
	if [ ! -f "$TMPDIR/install.js" ] ; then echo "No install.js" ; exit 1 ; fi
	ID=`grep "var _2" "$TMPDIR/install.js" |sed 's/.*{\(.*\)\}.*/\1/'`
}

installExtention () {
	sudo mkdir -p "$EXTDIR/$ID"
	sudo mv -vv "$TMPDIR" "$EXTDIR/{$ID}"
}

getPath () {
	(
	cd ${1%%/*}
	pwd
	)
}

EXT="$1"
EXTPATH="`getPath $EXT`"
EXTDIR="/usr/lib/firefox-addons/extensions"
TMPDIR="/tmp/ext"

setUp

getID

installExtention
```

As with yours, I need to set up some traps and a check to make sure the xpi file exists and checking for failures to clean up the /tmp/ext dir if not moved.

I greatly appreciate your time for the above as it adds to my "toolkit."

With thanks,
Narnie

---

### Post by lovinglinux on 2010-06-04
I was searching for an extension I want to develop, to check if it hasn't been developed yet and found this:

[Extension Manager Extended](https://addons.mozilla.org/en-US/firefox/addon/2195/)

It might be useful for you.

---

### Post by narnie on 2010-06-04
> **lovinglinux said:**
> I was searching for an extension I want to develop, to check if it hasn't been developed yet and found this:

[Extension Manager Extended](https://addons.mozilla.org/en-US/firefox/addon/2195/)

It might be useful for you.

Thanks, I'll check it out. In the meantime, I had a "bright idea" and figured out how parse out what I needed from the install.rdr file and then the rest was easy.

Here's the code:

```
#! /bin/bash
#


USAGE () {
	USG=\
"
___________________________________________________________________

${0##*/} [-h] XPI_FILE_TO_INSTALL

installs the xpi file to /usr/lib/firefox-addons/extensions which
will inable installation the next time the user runs firefox

-h	print help
___________________________________________________________________
"
	echo "$USG"
	exit
}

if [ $# -lt 1 -o "$1" = -h ] ; then USAGE ; fi 

setUp () {
	if [ ! -f $EXT ] ; then
		echo "File doesn't exist"
		exit 1
	fi
	umask 0022
	if [ -d $TMPDIR ] ; then
		(cd $TMPDIR ; sudo rm -rf *)
	else
		sudo mkdir -p "$TMPDIR"
	fi
	echo -e "\n\nworking . . .\n\n"
	sudo unzip "$EXT" -d "$TMPDIR" &> /dev/null
}

getID () {
	local IFS="
"
	FILE="`cat $TMPDIR/install.rdf`"
	for i in $FILE ; do
		if echo "$i"|grep "urn:mozilla:install-manifest" &> /dev/null ; then
			GET=true
			continue
		fi
		if [ "$GET" = true ] ; then
			if echo "$i"|grep "<em:id>" ; then
				ID=`echo "$i" | sed 's#.*<em:id>\(.*\)</em:id>.*#\1#'`
			elif echo "$i"|grep "em:id=\"" ; then
				ID=`echo "$i" | sed 's/.*em:id="\(.*\)".*/\1/'`
			fi
			if [ -n "$ID" ] ; then
				return
			fi
		fi
	done
	echo "Sorry, could not correctly parse file"
	cleanUp 1
}

installExtention () {
	if [ -d "$EXTDIR/$ID" ] ; then
		sudo rm -rvf "$EXTDIR/$ID"
	fi
	sudo mv -vv "$TMPDIR" "$EXTDIR/$ID"
	if [ $? = 0 ] ; then
		echo -e "\n\nExtension was installed\n\n"
	else
		cleanUp 1
	fi
}

getPath () {
	(
	cd ${1%%/*}
	pwd
	)
}

cleanUp () {
	if [ -d $TMPDIR ] ; then
		sudo rm -rf $TMPDIR
	fi
	if [ "$1" = 1 ] ; then
		echo -e "\n\nFailed to install extension\n\n"
	fi
	exit $1
}

EXT="$1"

EXTDIR="/usr/lib/firefox-addons/extensions"
TMPDIR="/tmp/ext"

trap "cleanUp 1" 1 2 3 15

setUp

getID

installExtention

cleanUp

```

For those not knowing who might be reading this thread, paste the above into a text editor and save it (I called it add_firefox_extensions)

run
```
chmod +x add_firefox_extension
```

to run it, put it in a folder found by
```
echo $PATH
```

or just run it in any folder by prefixing it with "./" as in
```
./add_firefox_extension XPI_EXTENSION_TO_INSTALL
```

Cheerio,
Narnie

---

### Post by lovinglinux on 2010-06-04
> **narnie said:**
> Thanks, I'll check it out. In the meantime, I had a "bright idea" and figured out how parse it and then the rest was easy.

Here's the code:

Thanks for sharing.

---

### Post by kitrule on 2011-01-18
Thanks for the code. I altered it a bit to suit my coding style and added the ability to process multiple XPIs at once, code attached.

e.g. sudo script.sh *.xpi
or sudo script.sh first.xpi second.xpi etc.xpi
or sudo script.sh a_folder_of_xpis/*

Edit: altered first script to prevent installing extensions when firefox is running

the second script can download extensions keeping a record so it update it all for you in conjunction with the first script.

add.firefox.extensions.sh
```
#!/bin/bash

EXTDIR="/usr/lib/firefox-addons/extensions"
TMPDIR="/tmp/ext"
clobber=false

USG="	${0##*/} [-f] XPI_FILE_TO_INSTALL

	# Source: http://ubuntuforums.org/showthread.php?t=1485995
	Installs the xpi file to /usr/lib/firefox-addons/extensions which
	will enable the installation next time the firefox starts.

	-f Overwrite existing extensions - may be useful for upgrading."

setUp(){
	umask 0022
	mkdir -p "$TMPDIR"
	echo 'Working...'
	unzip "$1" -d "$TMPDIR" &> /dev/null
}

getID(){
	local IFS="
"
	FILE="`cat "$TMPDIR/install.rdf"`"; GET=; ID=
	for i in $FILE; do
		if echo "$i" | grep "urn:mozilla:install-manifest" > /dev/null; then
			GET=true
			continue
		fi
		if [ "$GET" = true ]; then
			if echo "$i" | grep "<em:id>" > /dev/null; then ID=`echo "$i" | sed 's#.*<em:id>\(.*\)</em:id>.*#\1#'`
			elif echo "$i" | grep "em:id=\"" > /dev/null; then ID=`echo "$i" | sed 's/.*em:id="\(.*\)".*/\1/'`; fi

			[ -n "$ID" ] && return
		fi
	done
	echo "ERROR: Error parsing file: \"$FILE\"" && return 1
}

installExtention(){
	[ "$clobber" = true ] && [ -d "$EXTDIR/$ID" ] && rm -rf "$EXTDIR/$ID"
	[ -d "$EXTDIR/$ID" ] && echo "SKIP: Extension already installed: \"$EXTDIR/$ID\"" && return 1
	mv "$TMPDIR" "$EXTDIR/$ID"
}

cleanUp(){
	[ $? = 0 ] && echo "Extension installed: \"$1\"" || echo "ERROR: Failed to install extension: \"$1\""
	[ -d "$TMPDIR" ] && rm -rf "$TMPDIR"
}

[ $# -lt 1 ] && echo "$USG" && exit
[ ! -w /etc/passwd ] && echo "Need root. Exiting!" && exit
[ -d "$TMPDIR" ] && echo "ERROR: Temporary folder already exists: \"$TMPDIR\"" && exit
[ "$1" = -f ] && clobber='true' && shift

warning='Please exit Firefox before continuing: (k=kill)'
while [ 1 ]; do
	psff=`ps --no-headers -o user,pid,cmd -C firefox-bin`
	[ ! "$psff" ] && break
	[ "$warning" ] && echo "$warning"; warning=
	echo -n "$psff: "
	read killff
	[ "$killff" = k ] && killall -i firefox-bin
	sleep 2
done

for each in $@; do
	trap "cleanUp 1 \"$each\"" 1 2 3 15
	[ ! -f "$each" ] && echo "ERROR: File doesn't exist: \"$each\"" && continue
	setUp "$each"
	[ $? = 0 ] && getID
	[ $? = 0 ] && installExtention
	cleanUp "$each"
done
```

download.firefox.extensions.sh
```
#!/bin/bash

tmpdir=/tmp/dl-ff-x
storefile="${0%.*}.store"
install=true
installer="${0%/*}/add.firefox.extensions.sh"
force=false

usage="	${0##*/} [-d] [-f] URL_OF_XPI_FILE_TO_INSTALL

	# Source: http://ubuntuforums.org/showthread.php?t=1485995
	Downloads the xpi file and invokes add.firefox.extension.sh
	to install it correctly.

	-d Download only, don't try to install.
	-f Force downloads, don't skip previously downloaded extensions."

# https://addons.mozilla.org/en-US/firefox/downloads/latest/433/addon-433-latest.xpi?src=addondetail
# https://addons.mozilla.org/firefox/downloads/latest/flashblock/addon-flashblock-latest.xpi?src=addondetail
# http://releases.mozilla.org/pub/mozilla.org/addons/433/flashblock-1.5.14.2-fx.xpi
# https://addons.mozilla.org/en-US/firefox/downloads/latest/1530/addon-1530-latest.xpi?src=addondetail
# https://addons.mozilla.org/firefox/downloads/file/94327/autohidestatusbar-0.4.7-fx.xpi?src=addondetail
# https://addons.mozilla.org/_files/1530/autohidestatusbar-0.4.7-fx.xpi

[ $# -lt 1 ] && echo "$usage" && exit
#[ ! -w /etc/passwd ] && echo "Need root. Exiting!" && exit
[ -d "$tmpdir" ] && echo "WARNING: Temporary folder already exists: \"$tmpdir\"" || mkdir -p "$tmpdir/.partial"
[ "$1" = -d ] && install=false && shift
[ "$1" = -f ] && force=true && shift

#load store
[ -f" $storefile" -a -r "$storefile" ] && mapfile -t store < "$storefile"
i=0; for each in "${store[@]}"; do
	each=($each)
	ext[$i]=$i
	ext_id[$i]="${each[0]}"
	old_file[$i]="${each[1]}"
	ext_url[$i]="${each[2]}"
	((i++))
done

#check latest
for i in "${ext[@]}"; do
	route="$tmpdir/${ext_file[$i]}.route"
	spider="https://addons.mozilla.org/en-US/firefox/downloads/latest/${ext_id[$i]}/addon-${ext_id[$i]}-latest.xpi?src=addondetail"

	! wget --spider "${ext_url[$i]}" -o "$route" && echo "ERROR: Remote file doesn't exist: \"${ext_url[$i]}\"" && [ "${ext_url[$i]}" = "$spider" ] \
		&& ! wget --spider "$spider" 2>&1>"$route" && echo "ERROR: Remote file doesn't exist: \"$spider\"" && continue

	dsturl[$i]="`grep "\.xpi" "$route" | tail -n 1`"; dsturl[$i]="${dsturl[$i]##* }"
	ext_id[$i]="${dsturl[$i]%/*}"; ext_id[$i]="${ext_id[$i]##*/}"
	ext_file[$i]="${dsturl[$i]##*/}"
	ext_url[$i]="`grep 'latest.xpi' "$route" | tail -n 1`"; ext_url[$i]="${ext_url[$i]##* }"
done

#read commandline
for each in $@; do
	route="$tmpdir/temp.route" && rm -f "$route"

	! wget --spider "$each" -o "$route" && echo "ERROR: Remote file doesn't exist: \"$each\"" && continue

	i="${#ext[@]}"
	dsturl[$i]="`grep "\.xpi" "$route" | tail -n 1`"; dsturl[$i]="${dsturl[$i]##* }"
	ext[$i]=$i
	ext_id[$i]="${dsturl[$i]%/*}"; ext_id[$i]="${ext_id[$i]##*/}"
	ext_file[$i]="${dsturl[$i]##*/}"
	ext_url[$i]="`grep 'latest.xpi' "$route" | tail -n 1`"; ext_url[$i]="${ext_url[$i]##* }"
done

#remove duplicates
for i in "${ext[@]}"; do
	skip=0
	for j in "${duplicates[@]}"; do
		[ "$i" = "$j" ] && skip=1
	done
	[ "$skip" = 1 ] && continue
	for j in "${ext[@]}"; do
		[ "${ext_id[$i]}" = "${ext_id[$j]}" ] && duplicates[${#duplicates[@]}]=$j
	done
	ext_unique[${#ext_unique[@]}]="$i"
done

#remove existing
for i in "${ext_unique[@]}"; do
	skip=0
	for j in "$tmpdir/*.xpi"; do
		[ "${ext_file[$i]}" = "$j" ] && skip=1
	done
	[ "$skip" = 1 ] && echo "Bypassing: Download found: ${ext_file[$i]}" && ext_got[${#ext_got[@]}]="$i" && continue
	skip=0
	for j in "${old_file[@]}"; do
		[ "${ext_file[$i]}" = "$j" ] && skip=1
	done
	[ "$skip" = 1 ] && [ "$force" = false ] && echo "Bypassing: Previously downloaded: ${ext_file[$i]}" && continue
	ext_get[${#ext_get[@]}]="$i"
done

#get extension
olddir=`pwd`
cd "$tmpdir/.partial"
for i in "${ext_get[@]}"; do
	wget "${dsturl[$i]}" && mv "${ext_file[$i]}" "../" && ext_got[${#ext_got[@]}]="$i" || rm -f "${ext_file[$i]}" "../${ext_file[$i]}" || echo "ERROR: wget/mv: \"${dsturl[$i]}\""
done
cd $olddir

#save store
for i in "${ext_unique[@]}"; do
	echo "${ext_id[$i]} ${ext_file[$i]} ${ext_url[$i]}" >> "$storefile.new"
done
mv -f "$storefile.new" "$storefile"

for i in "${ext_got[@]}"; do
	ext_inst[${#ext_inst[@]}]="$tmpdir/${ext_file[$i]}"
done

#install
if [ "${#ext_inst[@]}" != 0 ]; then
	if [ "$install" != true ]; then
		echo "The next step should be:"
		echo "	sudo $installer ${ext_inst[@]}; rm -rf $tmpdir"
	else
		#install_latest
		sudo "$installer" -f ${ext_inst[@]}
		#cleanup
		rm -rf "$tmpdir"
	fi
fi
```

---

### Post by narnie on 2011-01-19
> **kitrule said:**
> Thanks for the code. I altered it a bit to suit my coding style and added the ability to process multiple XPIs at once, code attached.

Cool, thanks for the updated code. Hadn't thought about this in a while.

Regards,
Narnie

---

### Post by kitrule on 2011-01-19
No probs, I just updated my previous post and put a freeze in the installer so it doesn't try to install when firefox is running. Also put together a second script that can download extensions from addons.mozilla.org if there are updates and use the first script to install them. =)

---

### Post by stlouisubntu on 2011-08-18
Hey friends, great script!  I have been utilizing them in conjunction with an Ubuntu Remix I maintain.  The remix is Ubuntu Lucid with updated Firefox among other things and three addons automatically installed for all users.  Namely, the addons are Status4Evar, https-everywhere, and adblock plus.

What has been giving me the most fits is adblock plus.  Anytime there are significant updates (which add up to more than 100 MGS or so or a new Firefox version), I respin the .isos.  The adblock plus has not been automatically installing via your great script on Firefox 6 (although it does appear in /usr/lib/firefox-addons along with the other two addons that do install correctly using this method.)  The adblock plus version is confirmed to be one that is compatible with Firefox 6 (and installs properly using the traditional method.)

Any advice would be much appreciated.  Can this script be modified to work with Firefox 6 and adblock plus?  Is this a firefox bug or an adblock plus bug?  (Should I try to file a bug with the adblock plus developer?)

Thanks and thanks so much for sharing this script.

stlouisubntu

[http://sourceforge.net/projects/ubuntu-sdr/files/](http://sourceforge.net/projects/ubuntu-sdr/files/)

 :)

---

### Post by Cobalto on 2011-09-22
This could be extremely useful for reinstalling Ubuntu & Firefox.

I like to reinstall the whole thing every six months instead of relying on the distribution upgrade. That way I can poke around and learn about the system without worrying about long-term stability, but Firefox extensions take ages.

I'm currently using the 'Extension List Dumper' extension to help me with that,  and I've asked the author to provide the actual link in each case. If he's willing, we could pipe use that to populate the download.firefox.extensions.sh script and automate the whole thing.

Do you think this is a good idea?

---

