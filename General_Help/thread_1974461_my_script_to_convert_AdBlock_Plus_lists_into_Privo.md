---
title: "my script to convert AdBlock Plus lists into Privoxy compatible filters"
date: 2012-05-06
forum: General Help
---

### Post by HiImTye on 2012-05-06
note: this script is based on [this]("http://andrwe.org/scripting/bash/privoxy-blocklist"). all the actual conversion was done by him (all of the sed work between "# convert to privoxy compatible list" and the following "done" were ccp'd directly from the original script) , I just cleaned it up a bit and made it more friendly to edit and create filter lists

first, we need to create a list of AdBlock compatible filters and place them in the file we are going to parse later on. if you don't want to edit the script too much then make sure the description is separated from the URI by tabs (yes, we need both as we add them both to the filter lists later on). here is my list:

.privoxy-AdBlockList
```
[SIZE="1"]EasyList		https://easylist-downloads.adblockplus.org/easylist.txt
EasyPrivacy		https://easylist-downloads.adblockplus.org/easyprivacy.txt
EasyList Germany	https://easylist-downloads.adblockplus.org/easylistgermany.txt
EasyList Italy		https://easylist-downloads.adblockplus.org/easylistitaly.txt
DutchAdBlockList	https://dutchadblockfilters.googlecode.com/svn/trunk/AdBlock_Dutch_hide.txt
Liste FR (French)	http://lian.info.tm/liste_fr.txt
ChinaList		https://adblock-chinalist.googlecode.com/svn/trunk/adblock.txt
Bulgarian List		http://stanev.org/abp/adblock_bg.txt
AB Pindo (Indonesian)	https://indonesianadblockrules.googlecode.com/hg/subscriptions/abpindo.txt[/SIZE]
```

now, we need to specify where both our script and list will be. place that location in 'basefolder'; mine are located in /storage/Launchers as shown in the script below:

.privoxy-AdBlock.sh
```
[SIZE="1"]#!/bin/bash

# declare variables
# ensure that our subsciptions list is delimited with tab characters, or else we will
 # need to change the 'sed' section of our script; tabs are much easier because visually
 # we can line them up for easier viewing and we can have anything before them to help us
 # look at the list itself

# change these to suit
configfolder="/etc/privoxy"
basefolder="/storage/Launchers"

# don't change these
workingfolder="$basefolder/.Privoxy-AdBlockLists.tmp"
downloadfolder="$workingfolder/download"
listfolder="$workingfolder/list"
filterfolder="$workingfolder/filter"
subscriptionlist="$basefolder/.privoxy-AdBlockList"

# make our folders and then move into it
cd $basefolder
mkdir $workingfolder
mkdir $downloadfolder
mkdir $listfolder
mkdir $filterfolder
cd $downloadfolder

# get our subscriptions from our list
cat $subscriptionlist | sed 's|.*\	*\(http.*\)|\1|' | wget -i -

# filter them out
for file in $downloadfolder/* ; do 
 if [ ! "grep -E '^\[Adblock.*\]$' $file" = "" ] ; then
  eval listname='$(echo $file | grep -o -E "[0-9A-Za-z _.]*$" | sed "s/\(.*\).txt/\1/")'
  actionfile=$listfolder/$listname.action
  filterfile=$listfolder/$listname.filter

 # convert to privoxy compatible list
  # URI blacklist
  echo -e "{ +block{$listname} }" > $actionfile
  sed '/^!.*/d;1,1 d;/^@@.*/d;/\$.*/d;/#/d;s/\./\\./g;s/\?/\\?/g;s/\*/.*/g;s/(/\\(/g;s/)/\\)/g;s/\[/\\[/g;s/\]/\\]/g;s/\^/[\/\&:\?=_]/g;s/^||/\./g;s/^|/^/g;s/|$/\$/g;/|/d' $file >> $actionfile
  echo "FILTER: $listname AdBlock Plus filters converted from $listname" > $filterfile

  # html element filter
  sed '/^#/!d;s/^##//g;s/^#\(.*\)\[.*\]\[.*\]*/s|<([a-zA-Z0-9]+)\\s+.*id=.?\1.*>.*<\/\\1>||g/g;s/^#\(.*\)/s|<([a-zA-Z0-9]+)\\s+.*id=.?\1.*>.*<\/\\1>||g/g;s/^\.\(.*\)/s|<([a-zA-Z0-9]+)\\s+.*class=.?\1.*>.*<\/\\1>||g/g;s/^a\[\(.*\)\]/s|<a.*\1.*>.*<\/a>||g/g;s/^\([a-zA-Z0-9]*\)\.\(.*\)\[.*\]\[.*\]*/s|<\1.*class=.?\2.*>.*<\/\1>||g/g;s/^\([a-zA-Z0-9]*\)#\(.*\):.*[:[^:]]*[^:]*/s|<\1.*id=.?\2.*>.*<\/\1>||g/g;s/^\([a-zA-Z0-9]*\)#\(.*\)/s|<\1.*id=.?\2.*>.*<\/\1>||g/g;s/^\[\([a-zA-Z]*\).=\(.*\)\]/s|\1^=\2>||g/g;s/\^/[\/\&:\?=_]/g;s/\.\([a-zA-Z0-9]\)/\\.\1/g' $file >> $filterfile
  echo "{ +filter{$listname} }" >> $actionfile
  echo "*" >> $actionfile

  # URI whitelist
  echo "{ -block }" >> $actionfile
  sed '/^@@.*/!d;s/^@@//g;/\$.*/d;/#/d;s/\./\\./g;s/\?/\\?/g;s/\*/.*/g;s/(/\\(/g;s/)/\\)/g;s/\[/\\[/g;s/\]/\\]/g;s/\^/[\/\&:\?=_]/g;s/^||/\./g;s/^|/^/g;s/|$/\$/g;/|/d' $file >> $actionfile

  # image whitelist
  echo "{ -block +handle-as-image }" >> $actionfile
  sed '/^@@.*/!d;s/^@@//g;/\$.*image.*/!d;s/\$.*image.*//g;/#/d;s/\./\\./g;s/\?/\\?/g;s/\*/.*/g;s/(/\\(/g;s/)/\\)/g;s/\[/\\[/g;s/\]/\\]/g;s/\^/[\/\&:\?=_]/g;s/^||/\./g;s/^|/^/g;s/|$/\$/g;/|/d' $file >> $actionfile

 fi
done

# consolidate into two filter files
for file in $listfolder/* ; do
 if echo $file | grep '.action' ; then
  eval filtername='$(echo $file | grep -o -E "[0-9A-Za-z _.]*$" | sed "s/\(.*\).action/\1/")'
  filterfile=$filterfolder/adblock.action
 elif echo $file | grep '.filter' ; then
  eval filtername='$(echo $file | grep -o -E "[0-9A-Za-z _.]*$" | sed "s/\(.*\).filter/\1/")'
  filterfile=$filterfolder/adblock.filter
 else filtername=""
 fi
 if echo $filtername ; then
  eval filtertitle='$(cat $subscriptionlist | grep $filtername.txt | sed "s|\(.*\)\	*http.*|\1|")'
  eval filterurl='$(cat $subscriptionlist | grep $filtername.txt | sed "s|.*\	*\(http.*\)|\1|")'
  echo "###################################" >> $filterfile
  echo "# $filtertitle" >> $filterfile
  echo "# $filterurl" >> $filterfile
  echo "###################################" >> $filterfile
  cat $file >> $filterfile  
 fi
done

# copy files to privoxy's folder and insert them into privoxy's config
if ! grep "adblock.action" "$configfolder/config" ; then
 cat "$configfolder/config" | sed "s|^\(actionsfile user.*\)|\1\nactionsfile adblock.action   # AdBlockPlus compatible actions file|" >> $filterfolder/config
fi
if ! grep "adblock.filter" "$configfolder/config" ; then
 if ls $filterfolder | grep config ; then
  cat $filterfolder/config | sed "s|^\(filterfile user.*\)|filterfile adblock.filter   # AdBlockPlus compatible filter file\n\1|" >> $filterfolder/config1
  mv -f $filterfolder/config1 $filterfolder/config
 else
   cat "$configfolder/config" | sed "s|^\(filterfile user.*\)|filterfile adblock.filter   # AdBlockPlus compatible filter file\n\1|" >> $filterfolder/config
 fi
fi
sudo cp -f $filterfolder/* $configfolder
sudo chown privoxy /etc/privoxy/adblock.action
sudo /etc/init.d/privoxy restart

# delete our working files
cd $basefolder
rm -R $workingfolder

# exit
exit[/SIZE]
```

now if you want it to update periodically then add it to your cron jobs and viola! privoxy + AdBlock Plus compatible filters!

Updates
-cleaned up a little bit
-I'll be going through the documentation to see how to get it working better in the next while, but I just moved from one city to another so that has been my top priority for the last while. for now this should do, it already blocks some stuff, just needs some love
-changed user.action and user.filter to be loaded after ours, not before, otherwise their changes would not be applied if they happen to conflict with ours
-pass ownership of the action file to privoxy so that if 'enable-edit-actions' is enabled, the user can edit the config from the interface

---

### Post by Jewfro_Macabbi on 2013-02-15
Getting a syntax error: 2013-02-15 17:36:50.263 7f31be233700 Fatal error: can't load actions file '/etc/privoxy/adblock.action': line 5 should begin with a '{': -e { +block{AdBlock_Dutch_hide} }

---

### Post by HiImTye on 2013-06-18
> **Jewfro_Macabbi said:**
> Getting a syntax error: 2013-02-15 17:36:50.263 7f31be233700 Fatal error: can't load actions file '/etc/privoxy/adblock.action': line 5 should begin with a '{': -e { +block{AdBlock_Dutch_hide} }

your echo is broken. change
```
# convert to privoxy compatible list
 # URI blacklist
 echo -e "{ +block{$listname} }" > $actionfile
 sed '/^!.*/d;1,1 d;/^@@.*/d;/\$.*/d;/#/d;s/\./\\./g;s/\?/\\?/g;s/\*/.*/g;s/(/\\(/g;s/)/\\)/g;s/\[/\\[/g;s/\]/\\]/g;s/\^/[\/\&:\?=_]/g;s/^||/\./g;s/^|/^/g;s/|$/\$/g;/|/d' $file >> $actionfile
 echo "FILTER: $listname AdBlock Plus filters converted from $listname" > $filterfile
```to
```
# convert to privoxy compatible list
 # URI blacklist
 echo "{ +block{$listname} }" > $actionfile
 sed '/^!.*/d;1,1 d;/^@@.*/d;/\$.*/d;/#/d;s/\./\\./g;s/\?/\\?/g;s/\*/.*/g;s/(/\\(/g;s/)/\\)/g;s/\[/\\[/g;s/\]/\\]/g;s/\^/[\/\&:\?=_]/g;s/^||/\./g;s/^|/^/g;s/|$/\$/g;/|/d' $file >> $actionfile
 echo "FILTER: $listname AdBlock Plus filters converted from $listname" > $filterfile
``` [CENTER][COLOR=#333333][FONT=Roboto][/FONT][/COLOR][/CENTER]

---

### Post by 4nt01n3 on 2014-02-20
Hello,

(Sorry for my english :/)

Nice job ! Perfect for my computer because Adblock uses to many memory.
I've changed Adblock list and run the script. Worked perfectly.
But I have a problem, when I use adblock.action & adblock.filter in my privoxy config file, privoxy doesn't work. When I restart it, I can see it in my system monitor just for 2 or 3 seconds and then it stops. If I don't use this files, privoxy works.
Any idea about this problem ?
Thanks.

---

