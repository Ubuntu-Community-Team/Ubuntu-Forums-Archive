---
title: "How do I ask question in script?"
date: 2009-12-16
forum: General Help
---

### Post by DTHCND on 2009-12-16
I am setting up and shell script designed to install and configure a program and was wondering is there a way I can get it to ask the user something like "Do you want to continue (Yes/No)" and then if they type yes to continue or if the type no to exit... How do I do this???

---

### Post by kaibob on 2009-12-16
Have a look at the following thread. To exit in response to a no answer, you would use the exit command. 

[http://ubuntuforums.org/showthread.php?t=1352663](http://ubuntuforums.org/showthread.php?t=1352663)

Depending on the actual shell script, you could use a zenity dialog to ask the user whether to continue:

[http://linux.byexamples.com/archives/259/a-complete-zenity-dialog-examples-1/](http://linux.byexamples.com/archives/259/a-complete-zenity-dialog-examples-1/)

---

### Post by GregBrannon on 2009-12-16
There are many good resources to learn bash scripting.  A Google search for "LSST 1.05 Tutorial" and "cooper advanced bash" will lead you to two pdf resources that you can download and have at your fingertips.  Someone could answer your "How to do thing 1" question, but you'll soon be back with things 2 through x.

After you've done some scripting, ask for help when you get stuck and then show the code snippet that isn't doing what you think it should be doing.  Many people love to help fix broken code.

Good luck!

---

### Post by MaxIBoy on 2009-12-16
To get a single character, you can do this:
```
read -n 1 answer
```You can then see if the answer was "y" or "n":
```
if [ "$answer" = "y" ] ; then
   #the answer is yes, put code here
elif [ "$answer" = "n" ]; then
   #the answer is no, put code here
else 
   #invalid answer
fi
```You can improve this process by putting it in a loop:
```
read -n 1 answer #first try
while [ ! "$answer"  = "y" ]  && [ ! "$answer" = "n"  ] ; do #while the answer is neither y nor n
     echo "invalid answer, please pick y or n"
     read -n 1 answer #try again
done

if [ "$answer" = "y" ] ; then
     #the answer is yes, put code here
elif [ "$answer" = "n" ]; then
     #the answer is no, put code here
fi
```The "!" modifier means "not," so ```
[ ! "$answer" = "y" ]
``` means "answer is not y." The && means "and also."


Be sure to surround everything with spaces. This:
```
[!"$answer"="y"]
``` does NOT work.





If you want you can also just use
```
read answer
```So they can type as many characters as they would like and then hit enter.

---

