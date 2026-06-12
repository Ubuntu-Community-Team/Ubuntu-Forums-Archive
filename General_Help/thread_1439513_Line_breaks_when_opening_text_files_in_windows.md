---
title: "Line breaks when opening text files in windows"
date: 2010-03-26
forum: General Help
---

### Post by SavageWolf on 2010-03-26
I have some text files (Just plain text files, not OpenOffice files or anything) and when I try to open them in Windows they are all one line. I think I read somewhere that Linux uses \n for new lines whereas Windows uses \t\n or something... I am using Kate to edit them, and I have a LOT of files to fix so...

---

### Post by HermanAB on 2010-03-26
Wordpad.exe handles text files correctly.  Notepad.exe is best avoided.

---

### Post by akakingess on 2010-03-26
Just a quick question, but is notepad++ any better at handling the formatting/line breaks, obviously I prefer it over notepad and actually wordpad, but haven't experimented/know about it's abilities at cross platform formatting?

---

### Post by NovaWasp on 2010-03-26
Yes Notepad++ handles both EOL characters.  
 
It will display the text just fine, but if you need to convert:
 
Edit : EOL Conversion : [windows/unix/mac]
 
later,

---

### Post by kaibob on 2010-03-26
> **SavageWolf said:**
> I have some text files (Just plain text files, not OpenOffice files or anything) and when I try to open them in Windows they are all one line. I think I read somewhere that Linux uses \n for new lines whereas Windows uses \t\n or something... I am using Kate to edit them, and I have a LOT of files to fix so...

For command-line solutions that will allow the quick conversion of a lot of files see:

[http://ubuntuforums.org/showthread.php?t=1436135](http://ubuntuforums.org/showthread.php?t=1436135)

---

### Post by SavageWolf on 2010-03-26
Tried the link in the post above, it seems to work! But I need to use it on a lot of files, and I see no -r option. Is there a program which will loop through all the subfolders and run a command on every file?

---

### Post by prodigy_ on 2010-03-26
> **SavageWolf said:**
> Tried the link in the post above, it seems to work! But I need to use it on a lot of files, and I see no -r option. Is there a program which will loop through all the subfolders and run a command on every file?
The correct solution is in [this post](http://ubuntuforums.org/showpost.php?p=9009209&postcount=4).

---

### Post by SavageWolf on 2010-03-26
> **prodigy_ said:**
> The correct solution is in [this post](http://ubuntuforums.org/showpost.php?p=9009209&postcount=4).

That doesn't really help much...

---

### Post by prodigy_ on 2010-03-26
> **SavageWolf said:**
> That doesn't really help much...
How come? If you want to process multiple files, you can easily make a script like this:

```
# !/bin/sh

case "$1" in
  --w2l)
        CONV_TYPE="l"
        ;;
  --l2w)
        CONV_TYPE="w"
        ;;
  *)
        printf "\n%b\n" "Wrong first argument: expected \"--l2w\" or \"--w2l\"! "
        exit 1
        ;;
esac

shift

for I in $@
do
  [ x"$CONV_TYPE" = x"l" ] && sed -i 's/.$//g' $I
  [ x"$CONV_TYPE" = x"w" ] && sed -i "s/$/`printf "%b\n" "\\\r"`/g" $I
done
```

A command to use this script for Linux--->Windows conversion: ```
sh ./<name_of_the_file_where_the_script_is> --l2w <filename1> <filename2> <filename3> ... 
```

---

### Post by SavageWolf on 2010-03-26
Your script takes in a list of all the names of the files, that would be impracticable for what I am doing. I am looking for something like "cp -r".

EDIT: On closer inspection, it destroyed images which were living in the folder... That's why you keep backups!

---

### Post by prodigy_ on 2010-03-26
Sure it's practical, because wildcards ("*" and ".") also work. For example, copy/move all files you want to process to some directory and use a command like this: ```
sh /<path_to_the_script>/<script_filename> --l2w /<path_to_processing_directory/*
```
Also you can make use of aliases to shorten the command line. For example, assuming  you can add this to your **~/.bashrc**: ```
alias l2w='sh /<path_to_the_script>/<script_filename> --l2w'
```

---

### Post by SavageWolf on 2010-03-26
Fixed it, forgot about those wildcards... I used the "unix2dos" method using the wildcards.

---

