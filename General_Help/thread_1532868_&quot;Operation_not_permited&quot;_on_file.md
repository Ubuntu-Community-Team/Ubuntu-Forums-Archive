---
title: "&quot;Operation not permited&quot; on file"
date: 2010-07-17
forum: General Help
---

### Post by E-man96 on 2010-07-17
I got a zip file from utorrent, and when I try to unzip it with the archive manager it gives me these errors. 

(Stil in gui but output appears in dialogue box) error:  cannot open zipfile [ /home/emmanuel/wordlists-20031009-content.zip ]
        Operation not permitted
zipinfo:  cannot find or open /home/emmanuel/wordlists-20031009-content.zip, /home/emmanuel/wordlists-20031009-content.zip.zip or /home/emmanuel/wordlists-20031009-content.zip.ZIP.

I tried to copy it and this happened:
emmanuel@emmanuel-laptop:~$ cp wordlists-20031009-content.zip /home/emmanuel/Downloads/wordlists-20031009-content.zip
cp: cannot open `wordlists-20031009-content.zip' for reading: Operation not permitted

I then tried sudo but it gave out the exact same error

If I md5 it:
emmanuel@emmanuel-laptop:~$ md5sum wordlists-20031009-content.zip 
md5sum: wordlists-20031009-content.zip: Operation not permitted

And I get the same error if I sudo this one too.

Can anyone explain/help/pointer this out for me?

---

### Post by Penguin Guy on 2010-07-17
Lets get some information about this file:
```
ls -l wordlists-20031009-content.zip
```

I'd appreciate it if you could post the result back in a code box - it just helps with the readability, thanks.

---

### Post by bumanie on 2010-07-17
Try right clicking the .zip and choosing 'exract here', If that doesn't work, try installing 7zip - it can extract most compression formats. > sudo apt-get install p7zip-fullYou can get a gui for 7zip from [here]("http://linux.softpedia.com/progDownload/K7Z-Download-17178.html") (.deb) - it's a kde app, but apparently works well on gnome too.

---

### Post by E-man96 on 2010-07-17
```

emmanuel@emmanuel-laptop:~$ ls -l wordlists-20031009-content.zip
-rwxrwxrwx 1 emmanuel emmanuel 224045590 2010-07-16 18:23 wordlists-20031009-content.zip

```
BTW I moved the file to Downloads

---

