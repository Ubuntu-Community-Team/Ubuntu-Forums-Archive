---
title: "Shell script to create files??"
date: 2011-04-21
forum: General Help
---

### Post by tealeaf- on 2011-04-21
Hey everyone,

Currently am studying UNIX at university and am enjoying my experience with Ubuntu! So far iv got to grips with basic terminal commands, turning my laptop into a web server etc etc

And now (bare with me) I need to create a shell script for my class next week, that when run will create a set of files to the directory.


This is the question/task:

:using the cat technique create a simple script to create files and directories for the user;
:document the files produced in item 1 above, using a recursive listing and find command; add this to the script using an editor programme
:change permissions on the script to make it executable by everyone
:use grep command on the password and shadow files to just display the records relevant to your users
:use head and history commands together in pipeline to restrict the number of recent commands displayed
:convert the listing of these files in item 2: so that the output is redirected to a single file.
:ensure that both of these listings are in the file.

(then use rm to clean up)

Can someone please help me as im stumped 0_o :confused:

I am new so could someone please explain how's and why's so that i can learn rather than just type in the code. 

I do understand basic terminal so will manage to follow with you and am a quick learner however, we always learn from someone who knows better (i.e. you guys knowing more) so please don't take the p*** out of me as we all need to start somewhere! :) 


Many thanks!!

---

### Post by hwttdz on 2011-04-21
The man command is your friend.  i.e. if you want to learn how to use grep, type "man grep" at the terminal, and you'll get to read all about it.  Man pages will tell you what the program can do, what all the flags do and often even give examples.  

You mention ls, find, rm, grep and a few others.  All of these are very well documented.  Oh and permissions are generally modified with the chmod and chown commands.  And redirecting output is usually called piping.  I assume that'd be covered in the bash manual, but that one's epic so you're probably better off just reading here: [http://www.itk.ntnu.no/ansatte/Hendseth_Sverre/bash/pipes.html](http://www.itk.ntnu.no/ansatte/Hendseth_Sverre/bash/pipes.html) or something similar.

---

### Post by tealeaf- on 2011-04-22
Many thanks for that, 

So I should use the man command to discover more about what a particular command does. 

I 'man grep' and others.

Yeah I figured I'd need to use chmod but not chown.

how would I create a shell script and then?

Examplescript.sh
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

touch /'directory/newfile.txt
touch /'directory'/newfile1.txt
touch /'directory'/newfile2.text


would this work? or one of my fellow students suggested this:


"cd /home/manager
sudo mkdir publicity
cd home/manager/publicity
sudo mkdir photos
sudo mkdir banners
sudo mkdir letters
sudo mkdir accounts
sudo mkdir score_sheets
then
cd /home/webmaster/web/updates
sudo touch Saturday"
continue....

Their doing it slightly different files to me, I think our lecturer only wants example files to be created. but I still cant work out how you would make a shell script containing this :S

Thanks for your quick reply though (Y) iv read up on piping and understand it better now and am about to use the man command on some of them!!

---

### Post by Elfy on 2011-04-22
> While we are happy to serve as a resource for _hints_ and for asking questions when you get stuck and need a little help, the Ubuntu Forums is not a homework service. Please do not post your homework assignments expecting someone else to do it for you. Any such threads will be taken offline and warnings or infractions may be issued.

When you've actually written something and then need help with some of _that_ then start a new thread. In the meantime this one is closed.

---

