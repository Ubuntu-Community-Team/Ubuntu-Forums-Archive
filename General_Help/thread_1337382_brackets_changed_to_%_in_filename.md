---
title: "brackets changed to % in filename"
date: 2009-11-25
forum: General Help
---

### Post by sticke4 on 2009-11-25
I am having a problem when downloading files through pidgin. The files that I download have brackets in their filenames, but when pidgin saves them to disk, they are changed. The left bracket [ turns into %5b and the right bracket ] turns into %5d. I was unsure whether this was a problem with Ubuntu/gnome/nautilus or with pidgin. Is there a way so that the filename is saved correctly. 

If not, how should I go about making a bash script to rename and change all %5b and %5d into brackets.

---

### Post by JKyleOKC on 2009-11-25
Take a look with the command line (the "ls" command) to verify that the name actually changed. The %5b and %5d that you see are the normal substitution for the brackets, when inside a web browser, and they should be automatically replaced with the correct bracket when the file is written to a directory.

---

### Post by sticke4 on 2009-11-25
I verified that the filenames were indeed changed, and saved to disk with the %5b and %5d in their names. I also checked in terminal and the ln command to make sure, and the results were the same. I also checked on Pidgin's IRC channel and they said that the program purposefully saves it that way as a safety feature.

I guess I will need to make a script to change the filename. Any ideas of how I should start off making this script; any command manuals I should look up that would be useful?

---

### Post by JKyleOKC on 2009-11-25
To rename files using a script, you use the "mv" command. A safer way would be to use "cp" which would make a new copy of each file without damage to the originals. "man bash" will tell you more than you probably want to know about things you can do in a script.

For starters, I would create a subdirectory called "test" while in the directory where the files are now and, from the command line in that directory, issue the command "cp ./*%5b*%5d* ./test/*\[*\]*', then look in the test directory to see if it worked correctly and to verify that the files were still good. If so, you could then delete the original misnamed files, use "mv" or the file manager to move the new ones up from test, and get rid of test...

The backslashes in that suggested command line are bash escapes to keep the shell from interpreting the brackets as bash modifiers. It might be necessary to add them in front of the percent signs also.

If it works, just copy the command into a text file, removing the "test/" string and changing the "cp" to "mv" and make that text file executable, and you have your script.

---

### Post by sticke4 on 2009-11-25
The command you gave me didn't seem to work, saying that there was no such directory, even though I tried it from the test directory and the directory that contained test. 

After some searching and learning a little regular expressions and lots of trial and error, I finally got a working script.

```
for file in *%5b*%5d*%5b*%5d* ; 
do mv $file `echo $file | sed 's/\(.*\)%5b\(.*\)%5d\(.*\)%5b\(.*\)%5d\(.*\)/\1\[\2\]\3\[\4\]\5/'` ;
done
```Because most of the files had two instance of %5b and %5d I had to make it this way. Thank you for taking your time to help me solve this problem.

---

### Post by kaibob on 2009-11-26
Glad to see that you have solved this issue. Just for future reference, you may want to look at the rename command, which can handle situations such as this with ease. 

For example, the following will change all the files as you wish:

```
rename -n 's/%5b/[/g ; s/%5d/]/g' *
```

The -n option directs rename to do a dry run and report proposed changes. Change -n to -v to actually rename the files.

More examples of the rename command can be found at:

[http://ubuntuforums.org/showthread.php?p=5210531](http://ubuntuforums.org/showthread.php?p=5210531)

---

### Post by sticke4 on 2009-12-06
Wow kaibob, that was amazing. I tested out the code you posted and it worked wonderfully, and it wasn't as complicated and long as my other script. Thank you very much

Could you also explain to me what the "g" part of the expression causes it to do. I have only recently seen that in examples.

Also, if I have normally put scripts like these in Nautilus Actions, so that i can use it as a shell extension. But for the script to work, i have to add a cd command and tell Nautilus Actions to pass the file's base path as a parameter. Is there another way of making scripts like these more shell extension friendly, or is this the only way.

---

