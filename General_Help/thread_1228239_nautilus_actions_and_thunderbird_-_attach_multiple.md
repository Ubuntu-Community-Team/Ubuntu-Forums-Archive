---
title: "nautilus actions and thunderbird - attach multiple files"
date: 2009-07-31
forum: General Help
---

### Post by Post Monkeh on 2009-07-31
hi.

i've been trying to fiddle about to get a way to right click on a selection of multiple files, and send them using thunderbird.

when i was using vista, i liked the way it would add a list of the attached files to the subject line of the new email, however simply getting a way to send multiple files would be a start


i installed nautilus-actions, and tried to import the script from [here]("http://www.grumz.net/?q=node/232"), but it wouldn't work , presumably because it was written for an older version of nautilus-actions.

so i tried going through the script and stealing the parameter setting of "-compose "attachment=%u""  however i found that even when i selected "appears if selection has multiple files or folders" it would only add the first file (alphabetically) of any amount selected.

i tried to steal the parameters %d%M  after reading [this]("http://www.techthrob.com/2009/03/02/howto-add-items-to-the-right-click-menu-in-nautilus/")  page, but i didn't have any success.

i have found a couple of threads on here ([this one, ]("http://ubuntuforums.org/showthread.php?t=417978&highlight=nautilus-action+thunderbird") [and this]("http://ubuntuforums.org/showthread.php?t=373303&highlight=nautilus-action+thunderbird") )  but neither are for the more recent versions of ubuntu/thunderbird/nautilus actions, and none deal with the problem of sending multiple files.

i apologise in advance for by stupidness, but my wits are being dulled by age/years of alcohol abuse.

---

### Post by Post Monkeh on 2009-08-01
or if i can't do what i want with nautilus-actions is there any other way round it?

---

### Post by Johnny B on 2009-08-17
can thunderbird handle multiple attachments?
i cant get it to work, try it in the terminal first to refine your command

edit: i cant even get the attachment flag to work, its not in the help file either.

---

### Post by Post Monkeh on 2009-08-17
> **Johnny B said:**
> can thunderbird handle multiple attachments
i cant get it to work, try it in the terminal first to refine your command
i can drag multiple attatchments onto a composing message and it works.

and if i right click on multiple selected files in xp or vista it works (and in vista it actually adds the names of the files to the subject line)

the problem is obviously with my parameters.

---

### Post by Johnny B on 2009-08-17
still working on it:
thunderbird -compose "attachment=file://~/you_have_mail.wav"

---

### Post by Post Monkeh on 2009-08-17
the problem seems to be that the %u tag gives an output of file:///path/to/myfile.txt

but the %M tag, which should add the multiple files, gives an output of /path/to/myfile1.txt /path/to/myfile2.txt etc. which thunderbird doesn't seem to understand.

what is needed is a way to add the "file://" prefix to each file when the %M command gives its output.

---

### Post by Johnny B on 2009-08-17
well, i already tried that in the terminal, separated by commas or with another 'attachment=' flag
there's no info about it in --help or the man page.  i'm sure its possible, but i cant seem to figure it out or find the answer anywhere.

---

### Post by Post Monkeh on 2009-08-19
well, i've managed to attach multiple files from the command line like this

thunderbird -compose "attachment='file:////home/will/newfile,file:////home/will/newfile2'"

now i just need to figure out how to make nautilus actions add a "file:///" prefix before each selected file, and make it use a comma to seperate the list, instead of the default space.

needless to say i'm clueless, i consider it a massive achievement to have figured out how to even get it working from a command line. :D

also, slightly off topic, but shouldn't i be able to use ~/newfile instead of /home/will/newfile?

isn't ~ a shortcut to my home directory?


i tried using "thunderbird -compose "attachment='file:///~/newfile,file:///~/newfile2'" " but while it added files to the attached list, they weren't actually there, presumably because my path was wrong.  am i missing something?

---

### Post by Post Monkeh on 2009-08-19
and i've also managed to automatically add all attached files to the subject line by using "-compose "subject=Emailing %m,attachment='%u'" in the parameters line, but i can't find a multiple version of "%u", (which adds the required file:// prefix before the path)
plus, the list options at the minute use a space to seperate the selected items, rather than the required comma.  
i don't think this is going to be possible at the minute, not without some programming anyway which is beyond my talents.

---

### Post by Johnny B on 2009-08-19
ok then, save this script, give it executable permissions, and in nautilus actions do;
path=path to script
parameters: %M

```
#!/bin/bash

if [ $* = "" ] ;then echo "no files given" ; exit 1 ;fi
X=`echo file://$* | sed 's/ /,file:\/\//g'`      
thunderbird -compose "attachment='$X'",subject="Emailing $*",

```

sorry, the subject shows the full path of the files, instead of the base names, i can fix that later, no time now.

---

### Post by Johnny B on 2009-08-19
updated:
```
#!/bin/bash

if [ $* = "" ] ;then echo "no files given" ; exit 1 ;fi &>/dev/null
X=`echo file://$* | sed 's/ /,file:\/\//g'`
SUBJECT=$(for file in $* ;do C=`basename $file` ; echo -n " $C" ; done)
thunderbird -compose "attachment='$X'",subject="Emailing $SUBJECT"

```

---

### Post by Post Monkeh on 2009-08-19
> **Johnny B said:**
> ok then, save this script, give it executable permissions, and in nautilus actions do;
path=path to script
parameters: %M

```
#!/bin/bash

if [ $* = "" ] ;then echo "no files given" ; exit 1 ;fi
X=`echo file://$* | sed 's/ /,file:\/\//g'`      
thunderbird -compose "attachment='$X'",subject="Emailing $*",

```

sorry, the subject shows the full path of the files, instead of the base names, i can fix that later, no time now.
good man, thanks a lot.

don't post the fix for the subject showing the full path.

i'm gonna investigate what the hell all that means tomorrow and see if i can figure it out myself. i reckon that should give me a good start.

---

### Post by Post Monkeh on 2009-08-19
doesn't seem to like spaces in filenames very much lol.

oh well, it's a start, i can have a look tomorrow and see if i can fix it.

---

### Post by Johnny B on 2009-08-20
this may help you with sed:

[[IMG]http://img20.imageshack.us/img20/1517/regularexpressionscheat.th.png[/IMG]](http://img20.imageshack.us/i/regularexpressionscheat.png/)

[Sed by example, Part 1]("http://www.ibm.com/developerworks/linux/library/l-sed1.html")

---

### Post by Post Monkeh on 2009-08-22
thanks for all your help.

i haven't forgotten about this - i've been on call this weekend and was out loads so don't want to get into anything too in depth because 1, i'm too tired, and 2, i'll end up getting called away, but i'll try to work on this next week. i'll let you know how i get on. thanks for your help.

---

### Post by christopheccc on 2010-05-05
Hi all,


Have you solved the problem with the spaces in the full path ?

I have for example problem with this:
/home/christophe/Pictures/2010_and_older_NOT_SAVED_YET/Beach_BBQ_(May_2010)/Best Of/P1070582.resized.JPG

where so far the designed action doesn't like the spaces (" "), but also the parenthesis ("(")

That would be great if someone had come up with a solution...


Cheers,
Christophe.

---

### Post by Johnny B on 2010-05-05
I think i had a solution, but he told me not to post it.

let me see what i can do.

---

### Post by Johnny B on 2010-05-05
yes, thankfully i solved that and saved it to my scripts folder.

 try this:
```
#!/bin/bash
# attach multiple files thunderbird.sh
#thunderbird -compose "attachment='file:////home/will/newfile,file:////home/will/newfile2'"
#-compose subject=Emailing %m,attachment=%u


if [ $* = "" ] ;then echo "no files given" ; exit 1 ;fi &>/dev/null
X=`echo file://$* | sed 's/ \//,file:\/\/\//g'`
SUBJECT=$(for file in $* ;do C=`basename $file` ; echo -n " $C" ; done)
thunderbird -compose "attachment='$X'",subject="Emailing $SUBJECT"
```

---

### Post by christopheccc on 2010-05-06
Hi,


thanks for the script, it works perfectly fine for the attachment.
However I still have a problem with the body.

My files are :
/home/christophe/Pictures/Beach_(May)/Best Of/P1070555.resized.JPG
/home/christophe/Pictures/Beach_(May)/Best Of/P1070557.resized.PDF

The script is :

```
#!/bin/bash
# attach multiple files thunderbird.sh
#thunderbird -compose  "attachment='file:////home/will/newfile,file:////home/will/newfile2'"
#-compose subject=Emailing %m,attachment=%u

if [ $* = "" ] ;then echo "no files given" ; exit 1 ;fi  &>/dev/null
X=`echo file://$* | sed 's/ \//,file:\/\/\//g'`
ii=1
BODY=$(for file in $* ;do C=`basename $file` ; echo ; echo -n "$ii) $C" ;  ii=$(($ii+1)) ; done)
thunderbird -compose "attachment='$X'",body="P.S. - Attached Files:  $BODY",subject="attached files"
```

And the result is a good attachement (the 2 files) but the body is :

P.S. - Attached Files: 
1) Best
2) P1070555.resized.JPG
3) Best
4) P1070559.resized.JPG

I tried many stuff, but the only trick that could have worked that I found on the web is here :
[http://www.macgeekery.com/tips/cli/handling_filenames_with_spaces_in_bash](http://www.macgeekery.com/tips/cli/handling_filenames_with_spaces_in_bash)

And I couldn't make it work...

If anyone feel the need to solve this tricky question...


Thanks again anyway.
Christophe.

---

### Post by Johnny B on 2010-05-06
i can't reproduce the problem, are you running a older version of ubuntu/gnome?
when I execute the script on my machine, nautilus acts as if it is working in that directory, and my script never see's the path to the file. anyway, this will work if i guessed correctly:



```
if [ $* = "" ] ;then echo "no files given" ; exit 1 ;fi  &>/dev/null
Y=`echo file://$* | sed 's/ \//,file:\/\/\//g' | sed 's/ /^^/g'`   #this sed replaces all spaces with a ^^. 
X=`echo $Y | sed 's/\^^/ /g'`			#this sed replaces all ^^'s with a space
Z=`echo $Y | sed 's/,file:\/\// /g'`
ii=1						#that sed (below)replaces all ^^'s with a space
BODY=$(for file in $Z ;do C=`basename $(echo $file | sed 's/\^^/ /g')` ; echo ; echo -n "$ii) $C" ;  ii=$(($ii+1)) ; done)
thunderbird -compose "attachment='$X'",body="P.S. - Attached Files:  $BODY",subject="attached files"
```

---

### Post by christopheccc on 2010-05-06
Hi,


I'm running the latest ubuntu (10.04).

I tried your script, and the attachment was still fine (2 files)
but the body was :

P.S. - Attached Files:  
 1) Best
 2) Best

I think that the problem is that when you do "for file in $...",

instead of seeing this (what it should):
/home/christophe/Pictures/Beach_(May)/Best Of/P1070555.resized.JPG
 /home/christophe/Pictures/Beach_(May)/Best Of/P1070557.resized.PDF

it sees this:
/home/christophe/Pictures/Beach_(May)/Best
Of/P1070555.resized.JPG
 /home/christophe/Pictures/Beach_(May)/Best
Of/P1070557.resized.PDF

But i still can't figure it out...


Cheers
Christophe.

---

### Post by Johnny B on 2010-05-06
there was supposed to be quotes around this:
C=`basename **"**$(echo $file | sed 's/\^^/ /g')**"**`

Full line (so you can cut and paste)
```
BODY=$(for file in $Z ;do C=`basename "$(echo $file | sed 's/\^^/ /g')"` ; echo ; echo -n "$ii) $C" ;  ii=$(($ii+1)) ; done)

```

---

### Post by christopheccc on 2010-05-06
Thank you so much, it works perfectly.

I've been looking for this so much, I'd like to submit it, but I have no idea where this kind of stuff can be proposed.

I wrote it the most explicit way possible.

First: what do you think ?
Second: where should I send this to make it the most available ?

---

1)
install the Nautilus Actions Configuration utility
(through synaptic OR ubuntu software centre OR in command line: )
```
sudo apt-get install nautilus-actions
```

2)
create a script with this code:
(that means open a new text file then copy/paste the code in it and save the file somewhere, for example in /home/mySession with the name multiple_attachment_thunderbird)

```
#!/bin/bash
# attach multiple files thunderbird.sh
#thunderbird -compose "attachment='file:////home/will/newfile,file:////home/will/newfile2'"
#-compose subject=Emailing %m,attachment=%u

if [ $* = "" ] ;then echo "no files given" ; exit 1 ;fi  &>/dev/null
Y=`echo file://$* | sed 's/ \//,file:\/\/\//g' | sed 's/ /^^/g'`   #this sed replaces all spaces with a ^^.
X=`echo $Y | sed 's/\^^/ /g'`            #this sed replaces all ^^'s with a space
Z=`echo $Y | sed 's/,file:\/\// /g'`
ii=1                        #that sed (below)replaces all ^^'s with a space
BODY=$(for file in $Z ;do C=`basename "$(echo $file | sed 's/\^^/ /g')"` ; echo ; echo -n "$ii) $C" ;  ii=$(($ii+1)) ; done)
thunderbird -compose "attachment='$X'",body="P.S. - Attached Files:  $BODY",subject="attached files"
```

4)
give it executable permissions
(right click on the file, properties, permissions, tick the box in front of "allow executing file as program, OR in command line (which is a better solution here): )
```
sudo chmod u+x /home/mySession/multiple_attachment_thunderbird
```

5)
open the Nautilus Actions Configuration utility
(in system -> preference -> nautilus actions configuration OR in command line: )
```
nautilus-actions-config-tool
```

6)
in the Nautilus Actions Configuration utility
define a new action with
Context label: Attach and send to mail
Command path: /home/mySession/multiple_attachment_thunderbird
Command parameters parameters: %M
Save the action

7)
Close the Nautilus Actions Configuration utility
Close all your nautilus windows (close all your open folders...)
(Just in case, save all current work that hasn't been yet!)
Restart nautilus (restart your computer OR log out / log in OR in command line: )
> nautilus -q

8 )
finish, you're ready !

---

### Post by Johnny B on 2010-05-06
thats excelent, you are much better at writing a tutorial than i am.
i really don't know where to send it, but just being in the forums it will be indexed by google, so hopefully it will help the people that need it.

---

### Post by crazy ivan on 2010-06-06
Thanks christopheccc,

tried it and was surprised how well it worked!

Only two things:

1) you should add "check Conditions > appears if selection has multiple files" to point 6

2) bug in nautilus: the path to the script itself should not contain any white spaces, your script handles white spaces well

Immediately started to think about integrating compression of folders ;) Only quick way I found was to compress everything, but that's already what the send to action does..

---

### Post by hezuo on 2010-06-09
> **christopheccc said:**
> Thank you so much, it works perfectly.

I've been looking for this so much, I'd like to submit it, but I have no idea where this kind of stuff can be proposed.

I wrote it the most explicit way possible.

First: what do you think ?
Second: where should I send this to make it the most available ?

---

1)
install the Nautilus Actions Configuration utility
(through synaptic OR ubuntu software centre OR in command line: )
```
sudo apt-get install nautilus-actions
```


2)
create a script with this code:
(that means open a new text file then copy/paste the code in it and save the file somewhere, for example in /home/mySession with the name multiple_attachment_thunderbird)

```
#!/bin/bash
# attach multiple files thunderbird.sh
#thunderbird -compose "attachment='file:////home/will/newfile,file:////home/will/newfile2'"
#-compose subject=Emailing %m,attachment=%u

if [ $* = "" ] ;then echo "no files given" ; exit 1 ;fi  &>/dev/null
Y=`echo file://$* | sed 's/ \//,file:\/\/\//g' | sed 's/ /^^/g'`   #this sed replaces all spaces with a ^^.
X=`echo $Y | sed 's/\^^/ /g'`            #this sed replaces all ^^'s with a space
Z=`echo $Y | sed 's/,file:\/\// /g'`
ii=1                        #that sed (below)replaces all ^^'s with a space
BODY=$(for file in $Z ;do C=`basename "$(echo $file | sed 's/\^^/ /g')"` ; echo ; echo -n "$ii) $C" ;  ii=$(($ii+1)) ; done)
thunderbird -compose "attachment='$X'",body="P.S. - Attached Files:  $BODY",subject="attached files"
```

4)
give it executable permissions
(right click on the file, properties, permissions, tick the box in front of "allow executing file as program, OR in command line (which is a better solution here): )
```
sudo chmod u+x /home/mySession/multiple_attachment_thunderbird
```

5)
open the Nautilus Actions Configuration utility
(in system -> preference -> nautilus actions configuration OR in command line: )
```
nautilus-actions-config-tool
```

6)
in the Nautilus Actions Configuration utility
define a new action with
Context label: Attach and send to mail
Command path: /home/mySession/multiple_attachment_thunderbird
Command parameters parameters: %M
Save the action

7)
Close the Nautilus Actions Configuration utility
Close all your nautilus windows (close all your open folders...)
(Just in case, save all current work that hasn't been yet!)
Restart nautilus (restart your computer OR log out / log in OR in command line: )


8 )
finish, you're ready !

It works perfectly. Thanks a lot!

---

### Post by adrigmail on 2010-06-26
Many thanks for this script,
wonderful, beautiful, it works!):P

---

### Post by mc_scRAT on 2011-05-10
> **christopheccc said:**
> Thank you so much, it works perfectly.

I've been looking for this so much, I'd like to submit it, but I have no idea where this kind of stuff can be proposed.

I wrote it the most explicit way possible.

First: what do you think ?
Second: where should I send this to make it the most available ?
...
...
...

**Command parameters parameters: %M**
...
...
...



8 )
finish, you're ready !

Btw  %M has to be replaced with %F for me, due to %M refers to mimetypes of selected objects, and %F refers to full filepath of selected objects. i'm at debian sid, but guess that's no real difference. Hope it helps.

BTW it doesn't work if there's non-english letters in the path (even a space makes this script to fail)

---

### Post by dwitkin on 2012-06-21
+1 for the last post about this. 

Everything worked well for me, but I also needed to replace the "Command parameters parameters: %M" with "Command parameters parameters: %F".

---

