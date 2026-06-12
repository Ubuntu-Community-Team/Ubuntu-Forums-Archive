---
title: "Command Line for Search &amp; Replace"
date: 2006-05-27
forum: General Help
---

### Post by Ted_Smith on 2006-05-27
I quickly tried to work out the command line way of doing this but failed finding only eferences to 'sed' and 'awk' which I did not understand. 

If I wanted to find a text string located in a single file somewhere within a folder what command would I use and how? 

For example, a string 'this is my text' exists in a file called 'index.php' in a folder called 'web_site'. If all I knew was the string I wanted to search for and the fact that it was in a file in a folder called 'web_site', how would I do it (so I don't know that it is in index.php)?

Thanks

Ted

---

### Post by gborzi on 2006-05-27
You can try this line after moving to the folder:
> for i in `grep -rl 'string to search for' *`; do
sed --in-place -e 's/string to search for/replacement string/g' "$i"
done
in case you want to save a backup copy of the modified files
> for i in `grep -rl 'string to search for' *`; do
sed --in-place=bak -e 's/string to search for/replacement string/g' "$i"
done
I suggest you to make a backup copy of your folder before using the above command.

EDIT: I forgot a backquote before.

---

### Post by xenmax on 2006-05-27
To just find the string, you can use grep,
```
grep <your searchstring> *
``` assuming you are in folder you want.
or
```
grep <your search string> <path to your folder>/*
``` 
Pass the -r option if you want to do a recursive search i.e. traverse subdirectories of your folder too.
Pass option -i if you need case insensitive search.

You should see the your string with filename prepending it.

And sed and awk are indeed best commands for non-interactive search-and-replace. You can always bring up a GUI text editor and use its search and replace if you dont mind interactive method.

EDIT: gborzi beat me to it :)

---

### Post by Ted_Smith on 2006-05-27
Thanks guys - that is very helpful.

---

