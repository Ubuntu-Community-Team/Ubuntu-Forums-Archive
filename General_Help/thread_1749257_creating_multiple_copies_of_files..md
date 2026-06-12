---
title: "creating multiple copies of files."
date: 2011-05-04
forum: General Help
---

### Post by atomiser on 2011-05-04
hi there,
 
i have a source file, which is the configuration file for a wyse terminal. i also have another file which is just a list of mac addresses, of wyse terminals.
 
i would like to be able to create multiple copies of the source file, having them renamed to the mac addresses in the list in the above file.
 
i.e. if there are a list of 100 mac addresses in one file, and a source configuration file - i would like 100 copies of the source configuration file renamed as the mac addresses from the list.
 
is there a way to do this using the ubuntu command line?
 
thanks in advance, andy.

---

### Post by atomiser on 2011-05-05
managed to write a shell script to do this, i'm not sure if it's the most elegant way of doing it, but it works!
 
for sma in $( cat mac ); do
cp config $sma
done
 
my interpretation of that is create a variable for each line of a file called mac, and then pass that variable to the target_file portion of the cp command to replicate a file called config.
 
from a bit of reading that might be a 'useless use of cat', since i get the impression cat is primarily used with multiple files...but i'm a newbie, and this does what i need - i now have the 400 files i was after in a matter of seconds!  if anyone cares to point out a more elegant way of doing things such as this, please feel free! :)

---

### Post by erind on 2011-05-05
Yes, '*for'* loop and '*cat*' are problematic - there's an extra-process (*cat*) and it'll also suffer from file names with whitespaces in them. Use a '*while*' loop instead:

```
while read sma
  do
    cp config "$sma"
  done < mac_list
```Don't forget to quote the variables,* $sma* in this case.

__
PS. Check this link on UUOC:  [http://partmaps.org/era/unix/award.html](http://partmaps.org/era/unix/award.html)

---

### Post by atomiser on 2011-05-05
hi erind, thanks for the response.  i'm sorry but i dont really understand what your quoted script does.  mine appears to work ok - however, i have noticed that within finder all the created files appear as i expect them to, however at cli if i list out the directory all the file names have a trailing ?, and if i copy the files to a usb stick and then read them from a windows machine they all have a trailing special character.  would like to try and avoid this if possible.  any ideas?  thanks in advance.
p.s. i know my script is ok, because if i dummy the input files (mac address lists) then it doesn't happen...yet if i use the proper input lists i get trailing ? on the filename.  i've checked the input lists and there are no special characters or whitespace, it is just a list of mac addresses, one per line.  the only other difference is that my dummy files are lower case and the proper lists are all uppercase.

---

### Post by erind on 2011-05-05
> **atomiser said:**
> hi erind, thanks for the response.  i'm sorry but i dont really understand what your quoted script does.  mine appears to work ok - ...

Yes your code works fine, but has issues in certain cases. Just use whatever code yuo're happy with.


> however, i have noticed that within finder all the created files appear as i expect them to, however at cli if i list out the directory all the file names have a trailing ?, and if i copy the files to a usb stick and then read them from a windows machine they all have a trailing special character.  would like to try and avoid this if possible.  any ideas?  thanks in advance.
I think that your file names have extra non-printable characters at their ends. You can see them in VI, but I don't recall now what exact option does that  (you can google it), or use *cat -vte list_file*, etc .... Usually this happens when the file is created in Windows, then used in Linux ( they use different end-of-line characters ). Create your list file in Ubuntu and use it inside Ubuntu, or do some clean-up of your current list file inside Ubuntu ( vi, sed, perl ...).

---

