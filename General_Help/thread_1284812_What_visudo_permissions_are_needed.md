---
title: "What visudo permissions are needed?"
date: 2009-10-07
forum: General Help
---

### Post by whizzle on 2009-10-07
I have a shell script that runs on a webserver. In the visudo file what commands should I allow for this file to run correctly. I don't want to allow ALL to the user. php is the user and calls this file via exec(). Whatever I seem to set besides ALL fails. 

file_mover.sh
```

#!/bin/sh

#
#get the flags set
#
rename=0
owner=""
group=""
while getopts "no:g:" optionName; 
do
    case "$optionName" in
    n) rename=1;;
    o) owner=$OPTARG;;
    g) group=$OPTARG;;
    ?) printf "Usage: %s: [-n] [-o] [-g] args\n file_mover.sh file_to_copy new_file_path"
            exit 2
            ;;

    esac
done

shift $(($OPTIND - 1))


#
#get the arguments passed in
#
movePath=$(readlink -f $2)
origFile=$1


#class variables
origFileName=$(basename $origFile)
newFileName=$(basename $origFile)


# if flag param rename was set to true
# loop through and rename the file to a unique name
i=1
while [ -f "$movePath/$newFileName" -a $rename -eq 1 ]
do
    #echo "$movePath/$newFileName already exists"
    i=$(($i+1))
    newFileName=${i}_${origFileName}
done

# move the file and set permissions
mv "$origFile" "$movePath/$newFileName"
chown -R "$owner:$group" "$movePath/$newFileName"
echo $(readlink -f "$movePath/$newFileName")

exit 0


```

---

### Post by minigeek on 2009-10-07
> **whizzle said:**
> I have a shell script that runs on a webserver. In the visudo file what commands should I allow for this file to run correctly. I don't want to allow ALL to the user. php is the user and calls this file via exec(). Whatever I seem to set besides ALL fails. 

file_mover.sh
```

#!/bin/sh

#
#get the flags set
#
rename=0
owner=""
group=""
while getopts "no:g:" optionName; 
do
    case "$optionName" in
    n) rename=1;;
    o) owner=$OPTARG;;
    g) group=$OPTARG;;
    ?) printf "Usage: %s: [-n] [-o] [-g] args\n file_mover.sh file_to_copy new_file_path"
            exit 2
            ;;

    esac
done

shift $(($OPTIND - 1))


#
#get the arguments passed in
#
movePath=$(readlink -f $2)
origFile=$1


#class variables
origFileName=$(basename $origFile)
newFileName=$(basename $origFile)


# if flag param rename was set to true
# loop through and rename the file to a unique name
i=1
while [ -f "$movePath/$newFileName" -a $rename -eq 1 ]
do
    #echo "$movePath/$newFileName already exists"
    i=$(($i+1))
    newFileName=${i}_${origFileName}
done

# move the file and set permissions
mv "$origFile" "$movePath/$newFileName"
chown -R "$owner:$group" "$movePath/$newFileName"
echo $(readlink -f "$movePath/$newFileName")

exit 0


```

Hi 
This might help
[http://ubuntuforums.org/archive/index.php/t-1132821.html](http://ubuntuforums.org/archive/index.php/t-1132821.html)

:popcorn:

---

### Post by whizzle on 2009-10-07
Hmmm....I'm talking more about based upon the script presented I should have something like this:
```

%scripters    ALL=(ALL) /scripts/file_mover.sh, /bin/readlink, /bin/basename, /bin/mv, /bin/chown

```

however, I think it fails at this line:
*while [ -f ...... ]*
because -f is not set to be allowed.

---

### Post by whizzle on 2009-10-08
bump.

---

