---
title: "Unrared files not showing up"
date: 2010-04-03
forum: General Help
---

### Post by bmetmike on 2010-04-03
Hello and thanks in advanced to anyone who can post any advice on this. I've only been using Ubuntu for a few months so im still rather new to it

I already have unrar-free installed. I should be able to use archive manager and all seems fine when I go to extract it. I dont receive any error messages but when I click show files or navigate to the folder myself the extracted file doesnt show up.
 
I want to try it in terminal and ive tried multiple times to get it right but it keeps saying it cant locate the file or something along those line. I have had this problem with plenty of other files.
 
If you have any idea what the problem could be please let me know, any response is greatly appreciated. I've also tried xarchiver with no success. The file in question this time(other files have done the same thing) is aaf-ss.s03e07.rar so if you could tell me what I should be typing in terminal that would also help. Ive tried unrar x- aaf-ss.s03e07.rar
*also tried using unrar-free in terminal and that didnt work either
again thanks to anyone who tries to help

---

### Post by lidex on 2010-04-03
What is the output of this command:
```
uname -a
```
In a terminal="Applications>Accessories>Terminal"
Also try installing this:
```
sudo apt-get install p7zip-full
```
Put the rar file on your desktop, right-click it and select "extract here" and see if it shows up there.

---

### Post by bmetmike on 2010-04-03
the output I get is 

Linux peach-desktop 2.6.31-20-generic #58-Ubuntu SMP Fri Mar 12 05:23:09 UTC 2010 i686 GNU/Linux

I just tried 7zip with strange results. I get a folder with the same name as the rar pop up on my desktop but no files inside. I know its not a problem with the .rar as its been used on a windows machine. It always seems like it extracted the files never show up. I havent gotten in error messages. 

Thanks for the help.  I really don't know what it could be but I am a newcomer and it may be something I missed early on which is causing this. Its got to be something simple that im missing

---

### Post by lidex on 2010-04-03
I'm thinking that file is bad. What filesizes are reported before/after? Try re-downloading.

---

### Post by bmetmike on 2010-04-03
I'm 100% sure the files arent bad. Ive check them on a windows machine. I can use my windows machine to extract but I just want to get my linux one to do it. It's all rar files. Every single one I have does this. I've tried around 6 of them and they all do this. They all worked on windows. Its something strange Ive never seen this before. Could you tell me exactly what I need to type in terminal to extract in unrar or is what im trying in the first post correct. Ive done so much research and this seems to be a very uncommon problem as I cant find anyone whos had this problem

---

### Post by lidex on 2010-04-03
I've not seen it. Where are these files located - are they on the windows partition? Are they single files or multi-part? Password protected?

---

### Post by bmetmike on 2010-04-04
they are located in my downloads folder in home. They are not password protected and are multipart files. Like I said I find this sort of bizarre as well. Never seen in thing like this. Got my friend to test the same file and it worked on his computer in ubuntu. Its something up with mine. He couldn't figure it out either. It really seems like the extraction was a success. I dont know what else to do. Thanks for the help. Hope I figure this out soon. Bringing files back in fourth over a usb is a little time consuming just to extract a file.

---

### Post by lidex on 2010-04-04
Too weird. Try uninstalling/purging archive manager and all the 7zip and rar/unrar packages. Then re-install archive manager and only p7zip-full. If that doesn't work, you probably need non-free versions, at least for those files - maybe because they were created with proprietary software.

---

### Post by halj32 on 2010-04-04
have you tried pressing F5 to refresh folder
sometimes the folder doesnt auto refresh..

---

### Post by shikhar_sharma on 2010-04-04
ok.this is very simple.see u cant view these files as the version in which these files were zipped was 3.5.now the free unrar version cant handle that neither can 7zip.if u want u can read the documentation as well.wat u need to do is go to synapltics and install unrar non free version.the best thing is all though its non free it doesnt ask u for any key or anything.i had the same problem and the unrar non free works perfectly and now its over 2 months its not asking for any license.enjoyyyy

---

### Post by _khAttAm_ on 2010-04-04
^The unrar-nonfree is now known as unrar.. and it is nonfree not because it costs money.. it is free as in "Software Freedom"..

@OP
can you confirm this with this rar file using the latest unrar (I'm using 3.9.3-1) : [http://www.khattam.info/junk/test.rar](http://www.khattam.info/junk/test.rar)

Does opening it with archive manager show the files?

---

