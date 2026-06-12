---
title: "Scripting  recursing subdir"
date: 2011-05-30
forum: General Help
---

### Post by glene77is on 2011-05-30
Need to recurse a subdir tree, to apply chmod and chown and ls -al . 

chmod -R xxx yyy       does not function properly;  -R is nonfunctional.
chown -R xxx yyy       functions OK.  

Is there a script which will follow a subdir tree and open each subdir ? 

glene77is

---

### Post by AlphaLexman on 2011-05-30
Post what you have tried and any errors you are getting.

---

### Post by glene77is on 2011-05-30
> **AlphaLexman said:**
> Post what you have tried and any errors you are getting.

Alpha,
Thanks.

 Object: Importing files from Linux Puppy and TinyCore,  labled "My_" which is a tree 4 levels deep. 
Imported files are root, permissions 633.
Need to work the files on this computer, as glene77is, permissions 666. 

Was thinking that there might be a scripting file used in the system somwhere, 
which would be an example of how to loop through a set of subdir in a tree.  
That would be a clue for me to research the method. 
Learned lots by reading    boot-info-script055.sh   , then researching the commands.  

So, 
Have this subdir tree for testing: 
My_
(1) test
(a)    t1
(b)    t2
(c)    t3

Terminal opened in "test" subdir. 
Have placed script file   g-fix.sh in  test  . 

$ ls *.sh    
g-fix.sh

Have placed     test.txt in each  subdir:  t1, t2, t3.

Script file contains: 
#! /bin/bash
# Script code in g-fix.sh: 
    chown -R glene77is *.*
   chmod -R 666 *.*
###
   



###
Also, checking another method,  
Have placed g-fix.sh in /bin   (which is visible to the entire system), 
and it can be called via    terminal   local and will execute locally, 
but only affects the current subdir. 
Want  to  apply chmod and chown to all subdir in tree.    

###

---

### Post by AlphaLexman on 2011-05-30
Try it like this:
```
chmod -R 666 ./My_/test/t*/*.*
```

---

### Post by glene77is on 2011-05-30
> **AlphaLexman said:**
> Try it like this:
```
chmod -R 666 ./My_/test/t*/*.*
```

Alpha,
Thanks.
I see what you are doing. 
I'll stack them, for as many levels as I might have, 
because an attempted read too many levels deep will error. .

I think I'll have to insert some error checks, as the scripts tend to terminate on an error, sometimes. 

I will be reviewing the various script sampels I've collected.   

Great fun, when you are not under the gun.  :P

---

### Post by glene77is on 2011-05-30
> **AlphaLexman said:**
> Try it like this:
```
chmod -R 666 ./My_/test/t*/*.*
```

Alpha,
Thanks for the help.

Here is the code that works, running from a base subdir, and traversing the branches of the tree outwards.
This has some hard code written, but should be able to replace the subdir references with char like "*" and "?" for the subdir names.
The depth of the tree must be covered by repeated calls which extend the subdir address / subdir / subdir / subdir     outwardward.   
Error trapping (if I call out too far) must be written in; perhaps as an " if $fn exist then run " .


#! /root/bash/bin
###   test.txt is created by    ls -al *.* > test.txt      and then copied into each place. 
###   required subdir for testing. 
###   test/t1  with ta, tb, tc, each containing test.txt.
###   test/t2  with ta, tb, tc, each containing test.txt.
###   test/t3  with ta, tb, tc, each containing test.txt.

echo g-fix.sh running in      /test 

### chown is recursive and provides 'me' with access rights. 
sudo  chown  -R  glene77is  t*/*/*.*


### running  chmod  to check recursive ability

sudo  chmod   777  t*/*/*.*  
ls  -al   t*/*/*.*  > test777.txt

sudo   chmod   666  t*/*/*.*  
ls  -al   t*/*/*.*  > test666.txt

sudo  chmod   655  t*/*/*.*  
ls  -al   t*/*/*.*  > test655.txt

sudo  chmod   644  t*/*/*.*  
ls  -al   t*/*/*.*  > test644.txt

### shows results of recursive ability
geany   test777.txt   test666.txt   test655.txt   test644.txt

###

Thanks again for the encouraging word.   :)

---

### Post by glene77is on 2011-05-30
Alex,

#! /root/bash/bin

echo g-fix.sh running in MY_/test 

### chown is recursive
sudo chown  -R  glene77is  */*/*.*

sudo chmod  777  */*/*.*  
ls  -al  */*/*.*  > test777.txt

sudo chmod  666  */*/*.*  
ls  -al  */*/*.*  > test666.txt

sudo chmod  655  */*/*.*  
ls  -al  */*/*.*  > test655.txt

sudo chmod  644  */*/*.*  
ls  -al  */*/*.*  > test644.txt

geany  test777.txt  test666.txt  test655.txt  test644.txt
###

---

### Post by AlphaLexman on 2011-05-30
You should learn more about [regular-expressions]("http://www.regular-expressions.info/")

---

### Post by AlphaLexman on 2011-05-30
Also, why does your '**shebang**' have:
> **glene77is said:**
> #! /root/bash/bin
instead of:
```
#!/bin/bash
```

---

### Post by glene77is on 2011-05-30
> **AlphaLexman said:**
> Also, why does your '**shebang**' have:
instead of: ```
#!/bin/bash
```

Alex,
[COLOR=Red]Thanks again for the helpful attitude and tips.  :)   [/COLOR]

[B]My shebang was an overstatement .  :confused:
[/B] 
It has been a very long time since I tried to do anything serious.
These are the preliminary steps in testing the waters of a new language. 
I was doing software design and programming in 1979, from assember on. 
Been a dozen years since I tried salvaging data or writing anything commercial. 

**So, I appreciate the reference to the " Regular-Expressions "  website.  Good, timely tip **:P

Here is the code that worked OK.  Ready to be refined, and included in a looping structure.
I really don't intend to just spell it out for every new application.   I need to read the code for boot-info-script again, and see what else is available to become more familiar with BASH  do-while and   case-esac structures.   I've also been checking in the TLDP tutorials, and will continue reading therein. 

This is the current code, and I see it as very much too concrete. 
Straight line coding like this is for amatuers, but for today it works.
 

#! /bash/bin

clear
echo "----------------------------" 
echo g-fix.sh running in /test 

### chown is recursive
### sudo chown  -R  glene77is  */*/*.*  ### not quite right. 

fnsrc="g-fix.sh"
fntrg="g-fix.txt"
fnstr1="=== "$fnsrc" running in  /test "
fnstr2=" ==================  > "
fnstr3="--------------------------"
# fndate=$date -s

echo $fnstr1" 999 "$fnstr2$fntrg
# echo $fndate
ext1="*.*"
ext2="*/*.*"
ext3="*/*/*.*"
ext4="*/*/*/*.*"
ext5="*/*/*/*/*.*"
ext6="*/*/*/*/*/*.*"
ext7="*/*/*/*/*/*/*.*"

echo "$ext1"
echo "$ext2"
echo "$ext3"
echo "$ext4"
echo "$ext5"
echo "$ext6"
echo "$ext7"


fnline="echo $fnstr1$fy$fnstr2  >> $fntrg"

### to display
echo "$fnline"

### header into file output
echo $fnstr3$fnstr3               > $fntrg
echo  $fnstr1$fy$fnstr2    >> $fntrg
# echo $fndate >> $fntrg


### begin (g-fix.sh) ###################################

fx=" 666 "
fy="$fx$fx$fx"
echo $fnstr3$fx$ext1$fnstr3               >> $fntrg
sudo chmod   $fx  $ext1
ls  -al           $ext1      >> $fntrg

echo $fnstr3$fx$ext2$fnstr3               >> $fntrg
sudo chmod   $fx  $ext2
ls  -al           $ext2    >> $fntrg

echo $fnstr3$fx$ext3$fnstr3               >> $fntrg
sudo chmod   $fx  $ext3
ls  -al           $ext3  >> $fntrg

echo $fnstr3$fx$ext4$fnstr3               >> $fntrg
sudo chmod   $fx  $ext4
ls  -al           $ext4  >> $fntrg

echo $fnstr3$fx$ext5$fnstr3               >> $fntrg
sudo chmod   $fx  $ext5
ls  -al           $ext5  >> $fntrg

echo $fnstr3$fx$ext6$fnstr3               >> $fntrg
sudo chmod   $fx  $ext6
ls  -al           $ext6  >> $fntrg

echo $fnstr3$fx$ext7$fnstr3               >> $fntrg
sudo chmod   $fx  $ext7
ls  -al           $ext7  >> $fntrg

echo $fnstr3" DONE "$fnstr3               >> $fntrg

### end (g-fix.sh) ##############################

geany  $fntrg

# funcx_()
# {
# echo $fnstr3$fx$ext1$fnstr3               >> $fntrg
# chown  -R  $fnowner  $ext0
# chmod   $fx  $ext1
# ls  -al           $ext1      >> $fntrg
# }
###


Would love to have FoxPro (like I used in Unix) available, 
with SQL, and numerous object-like constructs, 
but all I have is VisualFoxPro running on my XP machine.  
Anyway, I don't have to make a living at that anymore, 
and have time (in my old age) to learn what can be done with Linux. 

Thanks again.   :)

---

