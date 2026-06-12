---
title: "Rar encoded file in windows"
date: 2011-04-22
forum: General Help
---

### Post by &#1581;&#1587;&#1575;&#1606; on 2011-04-22
Here my problem

i have a rar file within I've many Arabic titled files "look picture below" this file is created under windows

now I'm using Ubuntu 10.10 and file roller 2.32.0 for Gnome

and my files' titles look like this

[IMG]http://img38.imageshack.us/img38/9226/encoding.png[/IMG]

it is too difficult to rename files one by one 

so what could i do

---

### Post by An Sanct on 2011-04-22
This rar file was created with a system, that has a certain codepage setting (Arabic).

I have seen a lot of such behavior with Chinese ans Japanese compressed files (rar, zip, ...)  and found out, that if you unpack them in a virtual machine _with_ that codepage installed and then move them through a shared folder, the file names stay intact.

This is mainly a windows problem ... windows became UTF8 in windows 7, Linux is UTF8 for ages now ...

---

### Post by dino99 on 2011-04-22
with synaptic, install: xfonts-intl-arabic, ttf-sil-scheherazade

---

### Post by An Sanct on 2011-04-22
dino99: Does that run natively in Ubuntu? Because I hate to use *my* solution and run a VM for such small codepage issue every time?

(PS. In my case: Correspondence with Russians, Chinese, Japanese, ... etc ...)

---

### Post by Vaphell on 2011-04-22
codepage issues may be small but they are royal pain in the ***.
What encoding are these windows names using?
You can use convmv - it allows to convert from 1 encoding to another.

```
convmv -f <encoding> -t <encoding> <files>
```
this would perform a dry run, to actually change names add --notest

---

### Post by &#1581;&#1587;&#1575;&#1606; on 2011-04-22
> **dino99 said:**
> with synaptic, install: xfonts-intl-arabic, ttf-sil-scheherazade

thank you Mr. dino99 but this really doesn't work

and thank you Mr. An Sanct for you participation in fact this is really a bad idea to use vmware every time

---

### Post by &#1581;&#1587;&#1575;&#1606; on 2011-04-22
> **Vaphell said:**
> codepage issues may be small but they are royal pain in the ***.
What encoding are these windows names using?
You can use convmv - it allows to convert from 1 encoding to another.

```
convmv -f <encoding> -t <encoding> <files>
```this would perform a dry run, to actually change names add --notest

thank you very much Mr. Vaphell for you reply

as i told you before i've rar file ... then to do this command it should be already extracted from the rar file "i tried then extract here" because entering using file roller to extract couldnt extract any files 

look what i have so
[IMG]http://img198.imageshack.us/img198/9343/screenshot1fv.png[/IMG]

on right rar file content -> on left files after extraction

so in terminal file names looked like this

[IMG]http://img541.imageshack.us/img541/1870/screenshot2uu.png[/IMG]

so i've tried to delete the last file in this appeared list using this command for exemple

```
rm ??? ?&#39210;??? ?? ????? ????? ???&#63458; ??&#31321;???.pdf
```it's gave me 

```
rm: cannot remove `???': No such file or directory
rm: cannot remove `?&#39210;???': No such file or directory
rm: cannot remove `??': No such file or directory
rm: cannot remove `?????': No such file or directory
rm: cannot remove `?????': No such file or directory
rm: cannot remove `???&#63458;': No such file or directory
rm: cannot remove `??&#31321;???.pdf': No such file or directory
```anyways i continued with the command that you told

```
convmv -f windows-1256 -t utf-8 -r --exec "/home/hael/arabic/" "/home/hael/arabic/"
```

its gave me this
```

Your Perl version has fleas #37757 #49830 
Starting a dry run without changes...
/home/hael/arabic
/home/hael/arabic
/home/hael/arabic
/home/hael/arabic
/home/hael/arabic
/home/hael/arabic
/home/hael/arabic
/home/hael/arabic
/home/hael/arabic
/home/hael/arabic
/home/hael/arabic
No changes to your files done. Use --notest to finally rename the files.
```

---

### Post by Vaphell on 2011-04-22
what is that --exec supposed to do? because i think it tries to use /home/hael/arabic as a command to perform instead of default 'rename'

rm failed because of unescaped spaces
your ```
rm some name full of junk
```
was not understood as
```
rm "some name full of junk"
```
but as
```
 rm "some" "name" "full" "of" "junk"
```
n different parameters not 1. Just look how you get 'rm: cannot remove...' for each name part
Put the whole name in "" or use \ before each space.

do you mind attaching a text file with few example names?
```
ls > list.txt
``` should do

---

### Post by &#1581;&#1587;&#1575;&#1606; on 2011-04-22
> **Vaphell said:**
> what is that --exec supposed to do? because i think it tries to use /home/hael/arabic as a command to perform instead of default 'rename'

i read this in the conmv manual using "man conmv" in terminal and that what i got about --exec 
```
       --exec command
           execute the given command. You have to quote the command and #1
           will be substituted by the old, #2 by the new filename. Using this
           option link targets will stay untouched.

           Example:

           convmv -f latin1 -t utf-8 -r --exec "echo #1 should be renamed to
           #2" path/to/files
```> 
rm failed because of unescaped spaces
your ```
rm some name full of junk
```was not understood as
```
rm "some name full of junk"
```but as
```
 rm "some" "name" "full" "of" "junk"
```n different parameters not 1. Just look how you get 'rm: cannot remove...' for each name part
Put the whole name in "" or use \ before each space.
i tried this

```
rm "?? ????? ??????? ????? ??&#31321;? ???????.pdf"

```then i got this
```

rm: cannot remove `?? ????? ??????? ????? ??&#31321;? ???????.pdf': No such file or directory

```after that i tried the backslash as you told me
```

rm ??\ ?????\ ???????\ ?????\ ??&#31321;?\ ???????.pdf
```and that worked thank you very much

> 
do you mind attaching a text file with few example names?
```
ls > list.txt
``` should dothe file is in attachment

thank you very much for this quick response

---

### Post by Vaphell on 2011-04-22
could you create a file with few names in windows? because these strings from your example look like garbage (assuming win1256 codepage), both convmv and my handcrafted python script show the same result

&#1609;§&#1722;ï&#1548; &#1722;éê©¢&#1722;*.pdf
&#1609;§&#1722;ï&#1548; &#1722;éê©¢&#1722;* (2).pdf
ê*©&#1726; &#1722;éê&#1605;&#1722;ëï &#1607;ï ¬©¥ ç*ï§&#1548; ¥©&#1726; &#1722;é&#1681;ê&#1722;ëï (êë &#1681;&#1610;é &#1722;é&#1681;&#1605;©&#1722;&#1607; *éî ë&#1609;&#1722;ï&#1548; &#1722;éê&#8250;êë&#1610;ë).pdf
doesn't look too arabic :/ Maybe rar mangled the names so i'd like to try if the original names from windows can be translated properly

---

### Post by &#1581;&#1587;&#1575;&#1606; on 2011-04-22
> **Vaphell said:**
> could you create a file with few names in windows? because these strings from your example look like garbage (assuming win1256 codepage), both convmv and my handcrafted python script show the same result

&#1609;§&#1722;ï&#1548; &#1722;éê©¢&#1722;*.pdf
&#1609;§&#1722;ï&#1548; &#1722;éê©¢&#1722;* (2).pdf
ê*©&#1726; &#1722;éê&#1605;&#1722;ëï &#1607;ï ¬©¥ ç*ï§&#1548; ¥©&#1726; &#1722;é&#1681;ê&#1722;ëï (êë &#1681;&#1610;é &#1722;é&#1681;&#1605;©&#1722;&#1607; *éî ë&#1609;&#1722;ï&#1548; &#1722;éê&#8250;êë&#1610;ë).pdf
doesn't look too arabic :/ Maybe rar mangled the names so i'd like to try if the original names from windows can be translated properly

sorry for this late

in fact as i told i was installing windows on virtualbox then copying it using folder sharing so i am late


here i joined in the attachment two files the arabic file which you could find it in in the zip file using utf-8 encoding

[IMG]http://img571.imageshack.us/img571/2310/screenshot3xo.png[/IMG]
and the arabic titled file you should find the same file in alan.rar 

thank you

---

### Post by Vaphell on 2011-04-23
these 2 work here, at least i think so :)
 &#1606;&#1592;&#1605; &#1571;&#1581;&#1603;&#1575;&#1605; &#1602;&#1608;&#1604;&#1607; &#1578;&#1593;&#1575;&#1604;&#1610; &#1570;&#1604;&#1570;&#1606;.doc 
 &#1606;&#1592;&#1605; &#1571;&#1581;&#1603;&#1575;&#1605; &#1602;&#1608;&#1604;&#1607; &#1578;&#1593;&#1575;&#1604;&#1610; &#1570;&#1604;&#1570;&#1606;.doc (2)
looks kind of arabic but your screenshot has characters in a different order


btw, really nice font you got there, mine is butt-ugly :/

---

### Post by &#1581;&#1587;&#1575;&#1606; on 2011-04-23
> **Vaphell said:**
> these 2 work here, at least i think so :)
 &#1606;&#1592;&#1605; &#1571;&#1581;&#1603;&#1575;&#1605; &#1602;&#1608;&#1604;&#1607; &#1578;&#1593;&#1575;&#1604;&#1610; &#1570;&#1604;&#1570;&#1606;.doc 
 &#1606;&#1592;&#1605; &#1571;&#1581;&#1603;&#1575;&#1605; &#1602;&#1608;&#1604;&#1607; &#1578;&#1593;&#1575;&#1604;&#1610; &#1570;&#1604;&#1570;&#1606;.doc (2)
looks kind of arabic but your screenshot has characters in a different order


btw, really nice font you got there, mine is butt-ugly :/

sorry amigo about that but i really dont know how that worked with you ...

i extracted the rar file
then i got "??? ????? ???? ????? ????.doc" when i used ls in terminal

then i did 
```
convmv -f windows-1256 -t utf-8 ???\ ?????\ ????\ ?????\ ????.doc

```and i got this```

Your Perl version has fleas #37757 #49830 
Starting a dry run without changes...
mv "./&#65533;&#65533;&#65533; &#65533;&#65533;&#65533;&#65533;&#65533; &#65533;&#65533;&#65533;&#65533; &#65533;&#65533;&#65533;&#65533;&#65533; &#65533;&#65533;&#65533;&#65533;.doc"    "./ëâê &#1681;¥è&#1722;ê ç&#1610;é&#1609; ¢&#1605;&#1722;éï ™é™ë.doc"
No changes to your files done. Use --notest to finally rename the files.

```when i list again i have the same last name "??? ????? ???? ????? ????.doc"

how does that worked with you.... what i should do to make it work !!
and how may i use the convmv on rar or zip files ?

thanks

for the arabic font that i used is KacstOne 
ref.
[http://www.khaledhosny.org/node/172](http://www.khaledhosny.org/node/172)

---

### Post by Vaphell on 2011-04-23
these 2 files i got from your zip file directly, 1st one was directly inside, 2nd in the zip inside the zip. I simply extracted stuff and that's how it looked o_O

look at my screenshot, this is what i get when i double click on tar (left) and rar inside the tar (right)

what is your locale?
```
locale
```

---

### Post by &#1581;&#1587;&#1575;&#1606; on 2011-04-23
> **Vaphell said:**
> these 2 files i got from your zip file directly, 1st one was directly inside, 2nd in the zip inside the zip. I simply extracted stuff and that's how it looked o_O

look at my screenshot, this is what i get when i double click on zip (left) and zip inside the zip (right)


i am ok with you about the 1st because its encoded using utf-8.. but the second within the 2nd rar file it is encoded with windows-1256 and i assure you when i extract it it gave me until now titled like this "&#65533;&#65533;&#65533; &#65533;&#65533;&#65533;&#65533;&#65533; &#65533;&#65533;&#65533;&#65533; &#65533;&#65533;&#65533;&#65533;&#65533; &#65533;&#65533;&#65533;&#65533;.doc (invalid encoding)"

> 
what is your locale?
```
locale
```

```
LANG=en_US.utf8
LANGUAGE=en_US:en
LC_CTYPE="en_US.utf8"
LC_NUMERIC="en_US.utf8"
LC_TIME="en_US.utf8"
LC_COLLATE="en_US.utf8"
LC_MONETARY="en_US.utf8"
LC_MESSAGES="en_US.utf8"
LC_PAPER="en_US.utf8"
LC_NAME="en_US.utf8"
LC_ADDRESS="en_US.utf8"
LC_TELEPHONE="en_US.utf8"
LC_MEASUREMENT="en_US.utf8"
LC_IDENTIFICATION="en_US.utf8"
LC_ALL=

```

---

### Post by Vaphell on 2011-04-23
you leave me scratching my head - i have no idea why i get proper names in both cases, i just did 'extract' twice.
which version of ubuntu you have?

---

### Post by &#1581;&#1587;&#1575;&#1606; on 2011-04-23
> **Vaphell said:**
> you leave me scratching my head - i have no idea why i get proper names in both cases, i just did 'extract' twice.
which version of ubuntu you have?

[B]lsb_release -a
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 10.10
Release:    10.10
Codename:    maverick

uname -a
Linux pc 2.6.35-28-generic #50-Ubuntu SMP Fri Mar 18 18:42:20 UTC 2011 x86_64 GNU/Linux

[/B]

---

### Post by Vaphell on 2011-04-23
something must be messed up on your end, because i tested your .tar successfully in 10.04, 10.10 (vbox) and 11.04 (vbox). Each time 'extract here' on tar, 'extract here' on rar produced nicely named copies of the file.
which unrar do you have installed? unrar (with proprietary stuff included) or unrar-free (not patent encumbered)? i use unrar

---

### Post by &#1581;&#1587;&#1575;&#1606; on 2011-04-23
> **Vaphell said:**
> something must be messed up on your end, because i tested your .tar successfully in 10.04, 10.10 (vbox) and 11.04 (vbox). Each time 'extract here' on tar, 'extract here' on rar produced nicely named copies of the file.
which unrar do you have installed? unrar (with proprietary stuff included) or unrar-free (not patent encumbered)? i use unrar

ok i see now

i used 
```
unrar e alan.rar
``` and that worked very well thank you very very much


so the problem is from : File Roller 2.32.0 (arhive manager for Gnome) .. 

thank you very much .. but not how could i have a gui remplacement or alternative for the file roller which support autocmatic arabic encoding

---

### Post by Vaphell on 2011-04-23
Fileroller is just a gui that uses command line tools under the hood to perform actual operations. If unrar in terminal works, it should also work with fileroller.

I extracted your archive files from rightclick menu, 'extract here' (which i assume uses fileroller) and from fileroller itself after doubleclicking.

If you really can't convince your fileroller/'extract here in context menu to cooperate, you may try nautilus-actions and add your own context menu item that would use unrar command which you say works. It's pretty straightforward to configure.

---

### Post by An Sanct on 2011-04-24
File roller has some limitations, try using Ark.

I don't know if this will help you, but it is wort a try...

---

### Post by &#1581;&#1587;&#1575;&#1606; on 2011-04-25
here i am back

thank you i tried Ark and PeaZip and they do fine with many files about rar encoded files.... 

but now i have the same problem but with zip files .... even with ark and peazip the problem still existing ....

really i dont understand why this is tooo complicated ... 

i've now
file roller 2.24.3
ark 2.15
peazip 3.7 and look what i've got with this zip file

[IMG]http://img69.imageshack.us/img69/5512/captureib.png[/IMG]

this should be displayed like this
  	 	 	 	 	 	  [COLOR=#000000][FONT=Arabic Transparent]**&#1575;&#1604;&#1571;&#1581;&#1585;&#1601; &#1575;&#1604;&#1587;&#1576;&#1593;&#1577; &#1604;&#1571;&#1576;&#1610; &#1593;&#1605;&#1585;&#1608; &#1575;&#1604;&#1583;&#1575;&#1606;&#1610;**[/FONT][/COLOR]
 
look attached

---

### Post by Vaphell on 2011-04-25
zip rapes the filename here too.
Internet says that zip shouldn't really be used for 'exotic' filenames, because it doesn't offer any encoding flexibility - it uses only 1 codepage that is hardcoded right into its standard (IBM Code Page 437). In times of unicode it's terribly ancient approach.

programming oriented thread, but explains the source of problem with zip
[http://stackoverflow.com/questions/106367/add-non-ascii-file-names-to-zip-in-java](http://stackoverflow.com/questions/106367/add-non-ascii-file-names-to-zip-in-java)

skip zip, stay with any format that works for you.

---

### Post by &#1581;&#1587;&#1575;&#1606; on 2011-04-25
> **Vaphell said:**
> zip rapes the filename here too.
Internet says that zip shouldn't really be used for 'exotic' filenames, because it doesn't offer any encoding flexibility - it uses only 1 codepage that is hardcoded right into its standard (IBM Code Page 437). In times of unicode it's terribly ancient approach.

programming oriented thread, but explains the source of problem with zip
[http://stackoverflow.com/questions/106367/add-non-ascii-file-names-to-zip-in-java](http://stackoverflow.com/questions/106367/add-non-ascii-file-names-to-zip-in-java)

skip zip, stay with any format that works for you.

Damn primitive zip... 

in fact i abandoned windows and i wont back but i've many many  zip and rar files that i download every time form arabic sites which support windows arabic encoding system ...

this problem should be resolved integrily for new linux users... because language support is a real problem that face new ubuntu and linux comers...

thank you Mr. Vaphell for your explanation

---

### Post by &#1581;&#1587;&#1575;&#1606; on 2011-04-26
last question please

what is the best extension format for  'exotic' filenames for linux and the best application to compile with 

thank you

---

