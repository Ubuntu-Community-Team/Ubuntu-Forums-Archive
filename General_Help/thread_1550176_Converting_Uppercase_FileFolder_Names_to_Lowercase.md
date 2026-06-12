---
title: "Converting Uppercase File/Folder Names to Lowercase Bash Script."
date: 2010-08-10
forum: General Help
---

### Post by grumpy.medic on 2010-08-10
Hello all!

Hopefully you will be able to help me out a little. I have done a lot of searching but not found the right solution yet.

Issue: 
I have several thousand files and folders some of which have Uppercase letters which I would like to convert to lower case. In addition to that, there are duplicate folders (i.e. FolderName & foldername) which I would like to merger during this process as well.

I have been looking for the past 3 days and not found anything that does what I described above... and since I am new to Bash Scripting I was hoping you guys might be able to help.

If you need any clarifications, please just drop me a line... I really would like to figure this out.


Cheers!

---

### Post by grumpy.medic on 2010-08-11
I really do not like bumping threads... but I really gotta figure this out...

---

### Post by AlphaLexman on 2010-08-11
To translate uppercase names to lower, you'd use

```
rename 'y/A-Z/a-z/' *
```

---

### Post by grumpy.medic on 2010-08-11
> **AlphaLexman said:**
> To translate uppercase names to lower, you'd use

```
rename 'y/A-Z/a-z/' *
```

Thanks for the reply AlphaLexman. Problem with this is, it does not have a -recursive option, thus not changing file/folder names in subdirectories.

Also, even when using the -f option, it will not merge the directories (i.e. DirName + dirname) after changing to lowercase.

Do you have a suggestion on that?

---

### Post by AlphaLexman on 2010-08-11
Unless your ~/DirName and ~/dirname have a consistent pattern naming convention... DirName01, dirname01, DirName02, dirname02, etc., you may have to merge them one by one manually.

For example, if you had /music/RollingStones, and /music/rollingstones, and /music/RedHotChiliPeppers, and /music/redhotchilipeppers, the capitals are in different locations with different word lengths, they're not consistent. 

It may be possible, but you might spend 3 days trying to find some elaborate script, or get enough help to write it and debug it, it might be quickier, easier, but more laborious to manually merge the dirs.

As for the recursive file renaming, I think we can fix that. I have a nautilus script on my machine called 'renamer' it has a 'case' mode and a recursive switch that will do what you want (it might even do directories, I haven't tested that part.)

I did a quick google search, but can up empty. I've got the script on my box, but haven't found it yet. Nautilus has moved it's default script location a couple of times... and I don't remember where I put it. When I find it I will post it and let you know where to save it.

Regards.

---

### Post by AlphaLexman on 2010-08-11
It is 'pyrenamer' an updated version of the old python script I have.

It is in the repo's. If you need help with that let me know.

---

### Post by grumpy.medic on 2010-08-11
> **AlphaLexman said:**
> Unless your ~/DirName and ~/dirname have a consistent pattern naming convention... DirName01, dirname01, DirName02, dirname02, etc., you may have to merge them one by one manually.

For example, if you had /music/RollingStones, and /music/rollingstones, and /music/RedHotChiliPeppers, and /music/redhotchilipeppers, the capitals are in different locations with different word lengths, they're not consistent. 

It may be possible, but you might spend 3 days trying to find some elaborate script, or get enough help to write it and debug it, it might be quickier, easier, but more laborious to manually merge the dirs.

As for the recursive file renaming, I think we can fix that. I have a nautilus script on my machine called 'renamer' it has a 'case' mode and a recursive switch that will do what you want (it might even do directories, I haven't tested that part.)

I did a quick google search, but can up empty. I've got the script on my box, but haven't found it yet. Nautilus has moved it's default script location a couple of times... and I don't remember where I put it. When I find it I will post it and let you know where to save it.

Regards.

AlphaLexman, thank you very much for taking the time and helping me out. The naming convention is the same as you outlined in your example above.

I would be grateful if you could find the script and shared it with me :-)

In any case, if that does not work, I think I will spend some time (with support from knowledgeable community members like yourself, hopefully) piecing a script together that will do the job. There is a total of 900k files and 80k folders that need to be worked on. Aside from being labor intensive, there is also human error (though the argument can be made that scripts are not without error either as they were created by humans... but still).

In any case, if you get around to sharing the mentioned script, I will try to alter the workflow to make it work :-)

Thanks again!

---

### Post by AlphaLexman on 2010-08-11
The nautilus script is attached. The newer version (pyrenamer) is a stand-alone python application.

---

### Post by grumpy.medic on 2010-08-12
> **AlphaLexman said:**
> The nautilus script is attached. The newer version (pyrenamer) is a stand-alone python application.

So I did some messing around with it and it just would not play nice.

However, I found something nice and simple that took care of it; **convertmv**.

Really simple and easy to use, lives in the apt repositories and does exactly what I needed it to do.

Thank you so much for your help! Once I got this project off my table, I will try to make that script work though... can't stop the learning curve :-)

Cheers!

---

### Post by DaithiF on 2010-08-12
gah, i had just put this script together as a rough proof of concept, using a recursive function (recursion is kind of messy to do in bash because variables are global by default, but it is just about doable).  The script doesn't actually do anything as-is, it just reports what it would do (the commands to do those things are commented out.)

btw, i couldn't find convertmv in the repos ... is that the package name, and what repo is it in? 

```

#!/bin/bash
function process_dir()
{
  # need to use local variables because this'll be a recursive function
  local dir=$1
  local item
  for item in "$dir"/*
  do
    # an empty directory/* will expand to a literal '*', e.g.: /some/dir/*
    #    this of course doesn't exist, so check for it & return
    [[ ! -e $item ]] && return    

    # if a directory, process it recursively  
    [[ -d $item ]] && process_dir $item  

    # now dissect the current item into path & filename, and create
    # lower case equivalent of that filename
    local path=${item%/*}
    local name=${item##*/}
    local lcase_name=$(tr 'A-Z' 'a-z' <<< $name)

    # we only have work to do if name differs from lowercase name
    if [[ $name != $lcase_name ]]; then          
      # if the lower case dir/file already exists at this level
      # then we have to be careful...
      if [[ -e $path/$lcase_name ]]; then        
        # if this is a directory, and the existing thing is also a directory, 
        # then attempt a merge
        if [[ -d $path/$lcase_name && -d $path/$name ]]; then
          # if we successfully move everything within this dir then 
          # we can also delete this dir afterward
          local can_delete_dir=1    
          local subdir_item
          for subdir_item in "$path/$name"/*
          do
            # if this is an empty directory, we can skip ahead 
            #  to the deleting it stage
            [[ ! -e $subdir_item ]] && break   
            local subdir_name=${subdir_item##*/}
            # check if the thing in this directory also 
            #  exists in the other directory
            if [[ -e $path/$lcase_name/$subdir_name ]]; then
              echo "CONFLICT: Cannot move item $subdir_item to $path/$lcase_name as that destination already exists"
              # we're leaving stuff behind here, so we can't delete the dir
              can_delete_dir=0    
            else
              # we're ok to move this item
              echo "MERGE: $subdir_item to $path/$lcase_name/$subdir_name"
              #mv "$subdir_item" "$path/$lcase_name/"
            fi
          done
          # if we moved everything from under this directory successfully then
          #  we can now delete the directory 
          if [[ $can_delete_dir -eq 1 ]]; then
            echo "DELETE: $path/$name having merged all its contents elsewhere"
            #rm $path/$name
          fi
        else
          # otherwise its a file, so don't overwrite the existing file
          #  just report the issue and move on
          echo "CONFLICT: Cannot rename file $path/$name to $path/$lcase_name as that file already exists"
        fi
      else  
        # the lowercase version doesn't exist in this directory, so rename
        echo "RENAME: $path/$name to $path/$lcase_name"
        #mv "$path/$name" "$path/$lcase_name"
      fi
    fi
  done
}

start_dir="$1"
[[ -n $start_dir && -e $start_dir ]] || { echo "Please supply the starting directory as a parameter to the script"; exit 1; }

# strip off any trailing '/'
start_dir=${start_dir%/}

process_dir "$start_dir"
```

---

### Post by luigi_mb on 2010-08-12
It's "convmv", not "convertmv".

/luigi

---

### Post by pasu11 on 2011-07-08
> **AlphaLexman said:**
> To translate uppercase names to lower, you'd use

```
rename 'y/A-Z/a-z/' *
```

Thanks, it's easy and it works.:popcorn:

---

