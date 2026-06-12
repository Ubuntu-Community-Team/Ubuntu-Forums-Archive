---
title: "Defragmenting USB external hard drives?"
date: 2010-05-09
forum: General Help
---

### Post by inameiname on 2010-05-09
I currently use Ubuntu Lucid, and I'm curious if there is a program that I can install and run through it which will defragment an external USB hard drive. 

My 500GB hard drive is used a lot, and I often add/remove stuff on and off of it, and I'm sure it's slowly starting to get a little fragmented with the amount of deletion and addition I do on it.

Does anybody know of a way to check and potentially defragment just it through linux? Or am I gonna have to just find a windows computer and do it there? 

FYI, I don't care to nor know I really don't need to defragment my Ext4 drive to which Ubuntu's installed, its' just the external I am curious about.

---

### Post by howefield on 2010-05-09
> **inameiname said:**
> I'm curious if there is a program that I can install and run through it which will defragment an external USB hard drive.

You are really looking at defragmenting from a Windows PC. There is no linux tool for defragmenting windows drives that I'm aware of, why would there be ?

In any event, you are probably better using windows tools to deal with windows file systems and linux tools to deal with linux file systems.

A workaround would be to copy the files to another drive and then copy them back to your external. The files would be copied back sequentially.

---

### Post by Ad@m on 2010-05-09
You will need to use a windows PC.

Alternatively change the filesystem.

---

### Post by inameiname on 2010-05-09
I was just curious as most people tend to format their usb external drives in ntfs or fat32 even if they have linux, especially portable ones, so they can plug and play it into any computer, windows or linux, and have it be recognized and used. 

Okie dokie. I just installed windows real quick and am currently defragging, and when it's done I'll just reinstall my Ubuntu Custom DVD. Simple enough. (Would you believe the Windows defragmenter said my 500GB drive was 47% fragmented? Glad I decided to do this.)

Thanks for the input.

---

### Post by inameiname on 2010-09-08
I did find a defragmenting script and fragcheck script a while back. So I'll mark this as solved. Works well enough. I use the FragCheck.sh script a lot, mainly for usb drives, to see the fragmentation.

FragCheck.pl

```

#!/usr/bin/perl -w

#this script search for frag on a fs
use strict;

#number of files
my $files = 0;
#number of fragment
my $fragments = 0;
#number of fragmented files
my $fragfiles = 0;

my $verbose;

if ($ARGV[0] eq '-v') { shift @ARGV; $verbose++; }

open (REPORT, "find " . $ARGV[0] . " -xdev -type f -print0 | xargs -0 filefrag |");

while (defined (my $res = <REPORT>)) {
        if ($res =~ m/.*:\s+(\d+) extents? found$/) {
                my $fragment = $1;
                $fragments += $fragment;
                if ($fragment > 1) {
                        $fragfiles++;
                }
                $files++;
        } else {
                print ("Failed to parse: $res\n");
        }
}
close (REPORT);

if ($verbose) {
   print "Total files:      $files\n";
   print "Fragmented files: $fragfiles\n";
   print "Fragments:        $fragments\n";
}

sub round($$) {
   my $v = shift; # value
   my $p = shift; # rouding divisor (1 for '123', 10 for '123.4', 100 for '123.45')
   return int($v * $p) / $p;
}
print ( $fragfiles / $files * 100 . "% non contiguous files, " . $fragments / $files . " average fragments.\n");

```Defrag.sh

```

#!/bin/bash
# defrag v0.08 by Con Kolivas <kernel@kolivas.org
# Braindead fs-agnostic defrag to rewrite files in order largest to smallest
# Run this in the directory you want all the files and subdirectories to be
# reordered. It will only affect one partition. It works best when run twice.
# Are you really crazy enough to be using this? It might blow your data
# into tiny little useless chunks.


trap 'abort' 1 2 15

renice 19 $$ > /dev/null

abort()
{
    echo -e "\nAborting"
    rm -f tmpfile dirlist
    exit 1
}

fail()
{
    echo -e "\nFailed"
    abort
}

declare -i filesize=0
declare -i numfiles=0

#The maximum size of a file we can easily cache in ram
declare -i maxsize=$((`awk '/MemTotal/ {print $2}' /proc/meminfo`*1024))
(( maxsize-= `awk '/Mapped/ {print $2}' /proc/meminfo` ))
(( maxsize/= 2))

if [[ -a tmpfile || -a dirlist  ]] ; then
    echo dirlist or tmpfile exists
    exit 1
fi

# Sort in the following order:
# 1) Depth of directory
# 2) Size of directory descending
# 3) Filesize descending
# I made this crap up. It's completely unvalidated.

echo "Creating list of files..."

#stupid script to find max directory depth
find -xdev -type d -printf "%d\n" | sort -n | uniq > dirlist

#sort directories in descending size order
cat dirlist | while read d;
do
    find -xdev -type d -mindepth $d -maxdepth $d -printf "\"%p\"\n" | \
        xargs du -bS --max-depth=0 | \
        sort -k 1,1nr -k 2 |\
        cut -f2 >> tmpfile
    if (( $? )) ; then
        fail
    fi

done

rm -f dirlist

#sort files in descending size order
cat tmpfile | while read d;
do
    find "$d" -xdev -type f -maxdepth 1 -printf "%s\t%p\n" | \
        sort -k 1,1nr | \
        cut -f2 >> dirlist
    if (( $? )) ; then
        fail
    fi
done

rm -f tmpfile

numfiles=`wc -l dirlist | awk '{print $1}'`

echo -e "$numfiles files will be reordered\n"

#copy to temp file, check the file hasn't changed and then overwrite original
cat dirlist | while read i;
do
    (( --numfiles ))
    if [[ ! -f $i ]]; then
        continue
    fi

    #We could be this paranoid but it would slow it down 1000 times
    #if [[ `lsof -f -- "$i"` ]]; then
    #    echo -e "\n File $i open! Skipping"
    #    continue
    #fi

    filesize=`find "$i" -printf "%s"`
    # read the file first to cache it in ram if possible
    if (( filesize < maxsize ))
    then
        echo -e "\r $numfiles files left                                                            \c"
        cat "$i" > /dev/null
    else
        echo -e "\r $numfiles files left - Reordering large file sized $filesize ...                \c"
    fi

    datestamp=`find "$i" -printf "%s"`
    cp -a -f "$i" tmpfile
    if (( $? )) ; then
        fail
    fi
    # check the file hasn't been altered since we copied it
    if [[ `find "$i" -printf "%s"` != $datestamp ]] ; then
        continue
    fi

    mv -f tmpfile "$i"
    if (( $? )) ; then
        fail
    fi
done

echo -e "\nSucceeded"

rm -f dirlist

```

---

