---
title: "how to edit war file ?"
date: 2012-04-17
forum: General Help
---

### Post by winzip on 2012-04-17
I have a .war file.
I want to edit web.xml file under web-inf folder.

how do i do it. ?
System ubuntu 10.04 server os - no gui

---

### Post by albandy on 2012-04-17
Download the file, open it with file-roller and modify the web.xml then upload the file.
Do not extract it, only modify the file double-clicking it in file-roller. Then file-roller will ask you to update the file.

---

### Post by winzip on 2012-04-17
> **albandy said:**
> Download the file, open it with file-roller and modify the web.xml then upload the file.
Do not extract it, only modify the file double-clicking it in file-roller. Then file-roller will ask you to update the file.

Download to where ? Did you mean to windows ? I dont like that.
File-roller ? Please note my server os does not support gui.

---

### Post by lisati on 2012-04-17
If you've already managed to extract the file, then a command line editor such as nano should do the trick.

> **albandy said:**
> Download the file, open it with file-roller and modify the web.xml then upload the file.
Do not extract it, only modify the file double-clicking it in file-roller. Then file-roller will ask you to update the file.

Um, the OP doesn't have a gui.....

---

### Post by winzip on 2012-04-17
> **lisati said:**
> If you've already managed to extract the file, then a command line editor such as nano should do the trick.



Um, the OP doesn't have a gui.....

Steps are not clear.
Also.its a war file .

---

### Post by albandy on 2012-04-17
I thought you were using a Linux workstation. When I need to edit a war file I download it to my workstation through sftp and I open it with file-roller.

It's possible to do this in console by using the zip command, let me make some tests...

---

### Post by albandy on 2012-04-17
copy your war file to /tmp
now extract the contents:

cp warfile.war /tmp
cd /tmp
unzip warfile.war
cd WEB-INF
nano web.xml (or vim or any editor you want to use)
cd ..
zip -r -u warfile.war WEB-INF

now you have in /tmp/warfile.war your file updated.

---

### Post by winzip on 2012-04-17
> **albandy said:**
> copy your war file to /tmp
now extract the contents:

cp warfile.war /tmp
cd /tmp
unzip warfile.war
cd WEB-INF
nano web.xml (or vim or any editor you want to use)
cd ..
zip -r -u warfile.war WEB-INF

now you have in /tmp/warfile.war your file updated.

CP : omitting directory.  - i get this error when trying to copy.
Please check your cp command again. Why error copying a war file ?

---

### Post by albandy on 2012-04-17
use the full path:

cp /path/to/file/warfile.war /tmp

---

### Post by winzip on 2012-04-17
> **albandy said:**
> use the full path:

cp /path/to/file/warfile.war /tmp

Wrong. You need to use. -r flag.
Also unzip does not work on .war file.
Did you check your commands ? Its not working.

---

### Post by albandy on 2012-04-17
You don't need to use -r to copy a single file. -r means recursive and a war file is a zipped file.

and unzip works perfect with war files, I tested it on my server before posting the instructions.

---

### Post by winzip on 2012-04-17
> **albandy said:**
> You don't need to use -r to copy a single file. -r means recursive and a war file is a zipped file.

and unzip works perfect with war files, I tested it on my server before posting the instructions.

For me -r works fine.
But unzip on war still does not work. It says it cant find war file.
My system ubuntu 10.04 server os

---

### Post by albandy on 2012-04-17
see this:
[http://www.youtube.com/watch?v=IGozryxqKs8](http://www.youtube.com/watch?v=IGozryxqKs8)

also ensure you've installed zip and unzip on your server.

---

### Post by winzip on 2012-04-17
> **albandy said:**
> see this:
[http://www.youtube.com/watch?v=IGozryxqKs8](http://www.youtube.com/watch?v=IGozryxqKs8)



Thanks. I understand . I wish if that worked in my system.
> 
also ensure you've installed zip and unzip on your server.yes. its there . I can check that when I type * man zip*  ...it prints options.

cp  -r  worked  for me .

but still  unzip  on war not working.  

I think you have a gui system .  I  have server os 10.04 .  I searched forum . ..... some people are using  JAR command to extract   war  file ....unzip  did not  work for them too. I too  want to try with jar ...but jar command does not work in my system though openJDK installed.

---

### Post by albandy on 2012-04-17
type this:
file /path/to/file/warfile.war

and post the answer.

---

### Post by winzip on 2012-04-17
> **albandy said:**
> type this:
file /path/to/file/warfile.war

and post the answer.

$file /home/user/test/jmx-console.war

/home/user/test/jmx-console.war: directory

---

### Post by albandy on 2012-04-17
OK this is not a war file, this is a directory (also known as a folder in windows environment).

So I assume you're using jboss.

you can edit web.xml this way:

cd /path/to/jboss/server/default/deploy/jmx-console.war/WEB-INF
#use sudo if you're not the owner of the file
sudo nano web.xml

---

