---
title: "apt-get Git installation failed"
date: 2011-05-10
forum: General Help
---

### Post by simpangke on 2011-05-10
Hi,

I just reformatted my PC and installed Natty 11.04; my work files are all backed up in a separate /home directory that resides on another partition separately. That partition is not formated nor erased. I tried installing git through apt-get:

```
wanghao@wangwang-desktop:~$ sudo apt-get install git-core
Reading package lists... Done
Building dependency tree       
Reading state information... Done
git-core is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Do you want to continue [Y/n]? Y
Setting up man-db (2.5.9-4) ...
dpkg: error processing man-db (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 man-db
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

Then I tried:

```
wanghao@wangwang-desktop:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Setting up man-db (2.5.9-4) ...
dpkg: error processing man-db (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 man-db
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

I even followed the troubleshooting procedures for PackageManager  [here]("https://help.ubuntu.com/community/PackageManagerTroubleshootingProcedure") but to the same man-db postprocessing error. Any other logs I should look at? 

Please help. Thanks!

---

### Post by tgm4883 on 2011-05-10
That actually says that git-core is already installed. Installation is failing for man-db

---

### Post by simpangke on 2011-05-11
Yes, it was installed. I also noticed that later. However, this message keeps popping up when I do something with the package manager. What is wrong with man-db? please advise thanks

---

### Post by Horseboy on 2011-05-11
> **simpangke said:**
> Yes, it was installed. I also noticed that later. However, this message keeps popping up when I do something with the package manager. What is wrong with man-db? please advise thanks

try
```
sudo apt-get -f install
```

Regards,
HB.

---

### Post by sikander3786 on 2011-05-11
It might not be that easy to get rid of the man-db error messages. Lets start with commands.

```
sudo apt-get remove --purge git-core
```

```
sudo apt-get install -f
```

```
sudo dpkg --configure -a
```

If no errors, again

```
sudo apt-get install git-core
```

Please post the outputs.

---

### Post by simpangke on 2011-05-11
> **sikander3786 said:**
> It might not be that easy to get rid of the man-db error messages. Lets start with commands.

```
sudo apt-get remove --purge git-core
```

```
sudo apt-get install -f
```

```
sudo dpkg --configure -a
```

If no errors, again

```
sudo apt-get install git-core
```

Please post the outputs.

Hi sikander,

I seem to have git installed and working but i tried anyway to remove the man-db message:

```
wanghao@wangwang-desktop:~$ sudo apt-get remove --purge git-core
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  git-core*
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 28.7 kB disk space will be freed.
Do you want to continue [Y/n]? Y
(Reading database ... 136776 files and directories currently installed.)
Removing git-core ...
Setting up man-db (2.5.9-4) ...
dpkg: error processing man-db (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 man-db
E: Sub-process /usr/bin/dpkg returned an error code (1)

wanghao@wangwang-desktop:~$ sudo apt-get install -f 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Setting up man-db (2.5.9-4) ...
dpkg: error processing man-db (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 man-db
E: Sub-process /usr/bin/dpkg returned an error code (1)


wanghao@wangwang-desktop:~$ sudo dpkg --configure -a
Setting up man-db (2.5.9-4) ...
dpkg: error processing man-db (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 man-db

wanghao@wangwang-desktop:~$ sudo apt-get install git-core
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  git-core
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0 B/1380 B of archives.
After this operation, 28.7 kB of additional disk space will be used.
Selecting previously deselected package git-core.
(Reading database ... 136776 files and directories currently installed.)
Unpacking git-core (from .../git-core_1%3a1.7.4.1-3_all.deb) ...
Setting up man-db (2.5.9-4) ...
dpkg: error processing man-db (--configure):
 subprocess installed post-installation script returned error exit status 1
Setting up git-core (1:1.7.4.1-3) ...
Errors were encountered while processing:
 man-db
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

Essentially no effect, but git is working..

---

### Post by sikander3786 on 2011-05-11
What if you try,

```
sudo apt-get install --reinstall man-db
```

Or,

```
sudo apt-get remove --purge man-db
```

And then,

```
sudo apt-get install man-db
```

---

### Post by simpangke on 2011-05-11
```
wanghao@wangwang-desktop:~$ sudo apt-get install --reinstall man-db
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 1 reinstalled, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Setting up man-db (2.5.9-4) ...
dpkg: error processing man-db (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 man-db
E: Sub-process /usr/bin/dpkg returned an error code (1)

wanghao@wangwang-desktop:~$ sudo apt-get remove --purge man-db
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  man-db*
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 1802 kB disk space will be freed.
Do you want to continue [Y/n]? Y
(Reading database ... 125400 files and directories currently installed.)
Removing man-db ...
Purging configuration files for man-db ...
dpkg: error processing man-db (--purge):
 subprocess installed post-removal script returned error exit status 1
Processing triggers for doc-base ...
Processing 1 removed doc-base file(s)...
Registering documents with scrollkeeper...
/usr/bin/scrollkeeper-update:216: parse error near `&&'
Errors were encountered while processing:
 man-db
E: Sub-process /usr/bin/dpkg returned an error code (1)

wanghao@wangwang-desktop:~$ sudo apt-get install  man-db
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Suggested packages:
  groff
The following NEW packages will be installed:
  man-db
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 0 B/741 kB of archives.
After this operation, 1802 kB of additional disk space will be used.
Preconfiguring packages ...
man-db failed to preconfigure, with exit status 1
Selecting previously deselected package man-db.
(Reading database ... 125254 files and directories currently installed.)
Unpacking man-db (from .../man-db_2.5.9-4_amd64.deb) ...
Processing triggers for doc-base ...
Processing 1 added doc-base file(s)...
Registering documents with scrollkeeper...
/usr/bin/scrollkeeper-update:216: parse error near `&&'
Setting up man-db (2.5.9-4) ...
dpkg: error processing man-db (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 man-db
E: Sub-process /usr/bin/dpkg returned an error code (1)


```

is there an err log file for dpkg i can be pointed to?

---

### Post by sikander3786 on 2011-05-11
I think we have spotted the error and that can be corrected.

```
Registering documents with scrollkeeper...
/usr/bin/scrollkeeper-update:216: [COLOR="Red"]parse error near `&&'[/COLOR]

```

So, can we please see the output of this command.

```
cat /usr/bin/scrollkeeper-update
```

---

### Post by simpangke on 2011-05-11
As requested, here is the source of scrollkeeper-update

```
#!/bin/bash

# This script is designed to replace scrollkeeper-update
# It iterates through all the directories specified using -o <dir_list>
# If these aren't specified, the default convert_dir is used
# (typically /usr/share/omf) and checks whether the last-modified time for
# the directory has changed from the previous run.
# The previous timings are stored in output_dir/.rarian-update-mtimes
# in the file format:
# <mtime>:@:<dir_name>:@:<converted filenames>
# For top-level directories, the mtime is '0'
# When multiple scrolls are generated from a single omf subdir,
# the scroll names are seperated by a semi-colon.

# I'll annotate the rest of the scirpt
# If you want more info, please ping me and I'll try and help.


prefix=/usr
exec_prefix=/usr
bindir=/usr/bin
statedir=/var/lib/rarian
convert_dir=/usr/share/omf
datarootdir=/usr/share
datadir=/usr/share
output_dir=${datadir}/help
package_version=0.8.1
real_convert[0]=$convert_dir
skip_omf_translate=1

# Print the version info for this file
print_version()
{
    echo "`basename $0` version 0.9"
    echo "This script is distributed as part of Rarian v$package_version"
    echo "Use '`basename $0` --help' for options and instructions for running"
    echo ""
    echo "Have a nice day!"

    exit 0
}

# Standard help message
print_usage()
{
    echo "Usage: `basename $0` [OPTIONS]"
    echo "Update Rarian scrolls archive from scrollkeeper omf files."
    echo "Note: This script is a replacement for scrollkeeper-update, but"
    echo "does not update the scrollkeeper internal database."
    echo ""
    echo "Options:"
    echo -e "-o DIR\t\t\t\tUse the specified omf directories for"
    echo -e "\t\t\t\tconversion. Multiple directories can be "
    echo -e "\t\t\t\tspecified using colon (:) separator."
    echo -e "-r DIR\t\t\t\tUse the specified directory for the"\
            "resulting"
    echo -e "\t\t\t\tscrolls.  If the directory doesn't exist, it"
    echo -e "\t\t\t\twill be created at run time."
    echo -e "\t\t\t\t Note: Multiple output paths are not supported"
    echo -e "--c\t\t\t\tRebuild the index entirely.  This will rebuild"
    echo -e "\t\t\t\tall scroll files and may take a long time."
    echo -e "-v\t\t\t\tTurn Verbosity on."
    echo -e "-p\t\t\t\tSpecify a different place to store the mtimes file."
    echo -e "-q\t\t\t\tRun silently (default)."
    echo -e "-h, -?\t\t\t\tPrint this help message and exit."
    echo ""
    echo "Using this script without option will use the default omf directory"
    echo "'$convert_dir' and the default output directory '$output_dir'"

    echo ""
    if [ $skip_omf_translate != 0 ]
         then
        echo "NOTE (2): This script doesn't do anything and is "
        echo "only provided for scrollkeeper compatibility"
    fi
    exit 0
}

# Nice print function to call when we're in verbose mode.
# In normal mode, it's a no-op.
print_verbose()
{
    if [ $verbose ]
    then
        echo "$1"
    fi
}


# Process_dir handles the calling of the migration program
# It calls the program with the correct parameters
# and moves the results to the correct place.
process_dir()
{
    fname_list=""
    old_basename=""
    for f in $1/*.omf; do
        bname=$(basename $f)
        bname=${bname%-*.omf}
        if [[ $bname != $old_basename ]]
        then
            old_basename=$bname
            filename=$bname.document
            fname_list=$fname_list$filename";"
            if $bindir/rarian-sk-migrate $(dirname $f) ${bname%-*.omf} > $tmpdir/tmp.rarian
            then
                cp $tmpdir/tmp.rarian $output_dir/$filename
                rm $tmpdir/tmp.rarian
            else
                echo "Error: Cannot process file "$f".  See "$tmpdir"/tmp.rarian for the reason."
                exit 5
            fi
        fi
    done
    echo -e `stat -c %Y $1`':@:'$1':@:'$fname_list >> $tmpdir/rarian-updates
}

# Split up the omf dirs specified on the command line
# I've never seen this used in practice, but
# better safe than sorry
split_omf_dirs ()
{
    let counter=0
    while [ $convert_dir ]
    do
        entry=`echo $convert_dir | cut -d ':' -f 1`
        convert_dir=${convert_dir#$entry}
        convert_dir=${convert_dir#:}
        real_convert[$counter]=$entry
        let counter+=1
    done

}

# Determine whether the directory defined within the index file
# was specified in the convert_dirs
am_adding_dir ()
{
    let counter=0
    am_processing="0"
    for i in ${real_convert[@]}
    do
        if [[ $fname == $i ]]
        then
            real_convert[$counter]="0"
            am_processing="1"
            return
        fi
        let counter+=1
    done
}

# The directory wasn't specified.  This does nothing except cat the
# relevant lines from the old file to the new one
skip_directory ()
{
    read line
    time=`echo $line | awk -F ":@:" '{print $1}'`
    while [[ $time -ne 0 ]]
    do
        echo $line
        echo $line >> $tmpdir/rarian-updates
        read line
        time=`echo $line | awk -F ":@:" '{print $1}'`
    done
}

# Go through the given directory and add all subdirs (containing omfs)
# to the index file (and convert the omf's to scrolls)
add_all_files ()
{
    for i in $(ls $fname);
    do
        if [ -d $fname/$i ]
        then
            print_verbose "$fname/$i is new and will be added"
            process_dir $fname/$i
        fi
    done
    read line
}

# If the given directory actually exists within the omf dir
dirs_contains ()
{
    let counter=0
    am_processing="0"
    for i in ${entries[@]}
    do
        if [[ $1 == $i ]]
        then
            entries[$counter]="0"
            am_processing="1"
            return
        fi
        let counter+=1
    done
}

# The meat.  Goes through and checks each directory mtime against the
# cached version.  If they're different, regenerate the scroll.
# If the dir has been removed, delete.
process_directory ()
{
    let counter=0
    for i in  $(ls $fname)
    do
        entries[$counter]="$fname/$i"
        let counter+=1
    done

    read line

    old_time=`echo $line | awk -F ":@:" '{print $1}'`

    while [[ $old_time && $old_time != "0" ]]
    do
        name=`echo $line | awk -F ":@:" '{print $2}'`

        dirs_contains $name

        if [[ $am_processing != "0" ]]
        then
            new_time=`stat -c %Y $name`
            if [[ $new_time -ne $old_time ]]
            then
                print_verbose "Directory $name has changed.  Updating."
                process_dir $name
            else
                echo $line >> $tmpdir/rarian-updates
            fi
        else
            filenames=`echo $line | awk -F ":@:" '{print $3}'`
            while [[ $filenames ]]
            do
                entry=`echo $filenames | cut -d ';' -f 1`
                print_verbose "Directory resonsible for $entry has been removed.  Deleting"
                filenames=${filenames#$entry}
                filenames=${filenames#;}
                mv $entry $tmpdir
            done

        fi

        read line
        old_time=`echo $line | awk -F ":@:" '{print $1}'`
    done

    for i in ${entries[@]}
    do
        if [[ $i != "0" ]]
        then
            print_verbose "Directory $i is new and will be added."
            process_dir $i
        fi
    done
}



# Beginning of the main chunk of the script

# Sorry for the stupid naming of options.
# They are inherited from scrollkeeper :(

# We use TEMP as set -- seems to nuke the return value of getopt
TEMP=`getopt -u -n$(basename $0) -o "o:r:p:vqnhV" \
             -- "$@"` \
    || print_usage

if [ $? != 0 ] ; then
    print_usage
    exit 0
fi

eval set -- "$TEMP"

while true; do
    case "$1" in
        -o )
            convert_dir=$2
            update_output_dir=1
            shift 2
            ;;
        -r )
            output_dir=$2
            overload_update=1
            shift 2
            ;;
        -v )
            verbose=1
            shift
            ;;
        -q )
            shift
            ;;
        -c )
            clean_index=1
            shift
            ;;          
        -h | -\? )
            print_usage
            ;;
        -n )
            # Scrollkeeper compat.  Actually do nothing
            shift
            ;;
            -p )
                    statedir=$2
                    shift 2
            ;;
        -V | --version )
            print_version
            ;;
         * )
             break
             ;;
    esac
done

if [ $verbose ]
then
    echo "Verbosity turned on"
fi

if [ $skip_omf_translate = 0 ]
then

split_omf_dirs

if [ $update_output_dir ] && [ ! $overload_update ]
then
    # We assume here that people are sensible and put the 
    # omf files in <prefix>/share/omf
    # Also assumes only a single omf path
    print_verbose "Using non-installed location"
    output_dir=`dirname $real_convert[0]`/help
fi

print_verbose "Outputting to $output_dir"

if [ $clean_index ]
then
    print_verbose "Removing index file $statedir/rarian-update-mtimes"
    rm $statedir/rarian-update-mtimes > /dev/null 2>&1
fi


tmpdir=/tmp/rarian-$RANDOM
mkdir $tmpdir

if [ ! -d $output_dir ]
then
    mkdir -p $output_dir
fi

if [ ! -d $statedir ]
then
    mkdir -p $statedir
fi


res=$(touch $statedir/rarian-update-mtimes > /dev/null 2>&1)

if [ $? -ne 0  ]
then
    echo "Error: Unable to write to the output directory $output_dir."
    echo "write permission is needed in order to run"
    echo "this script.  If you don't have it, things"
    echo "break.  Please run this script with the correct"
    echo "permissions (normally root).  Exiting."
    exit 3
fi

exec < $statedir/rarian-update-mtimes

read line
fname=`echo $line | awk -F ":@:" '{print $2}'`


while [[ $fname != "" ]]
do
    print_verbose "Processing directory $fname"
    echo "0:@:$fname" >> $tmpdir/rarian-updates
    am_adding_dir $fname
    if [[ ! $(ls $fname 2>&1) ]]
    then
        print_verbose "Previous directory $fname no longer exists"
    else
        if [[ $am_processing != "0" ]]
        then
        process_directory
        else
        skip_directory
        fi
        fname=`echo $line | awk -F ":@:" '{print $2}'`
    fi
done

for i in ${real_convert[@]}
do
    if [[ $i != "0" ]]
    then
    res=$(ls $i 2>/dev/null)
    if [[ ! $res ]]
    then
        print_verbose "Path $i does not exist.  Ignoring"
    else
        
        print_verbose "Adding contents of directory $i"
        fname=$i
        echo "0:@:$fname" >> $tmpdir/rarian-updates
        add_all_files
    fi
    fi
done

rm -f $statedir/rarian-update-mtimes
if [ -e $tmpdir/rarian-updates ]
then
    mv $tmpdir/rarian-updates $statedir/rarian-update-mtimes
fi
rm -rf $tmpdir

fi # ENABLE_OMF_READ
```

---

