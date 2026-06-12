---
title: "get error message when trying to compress a file into a .zip"
date: 2010-05-19
forum: General Help
---

### Post by izquierdista on 2010-05-19
I wanted to compress a folder into a .zip file and I get the following error message:
An error occurred while adding files to the archive

the original folder is 1.2GB

I have made .zip files before without any issues before, could it be the size of the original folder?

I am trying to compress this folder in order to send it via email. I managed to compress the folder into a tar.gz file but Gmail didnt let me send it because I got a message stating that Gmail does not allow executable files to be sent. I have sent .zip files through Gmail with no issues before.

[B]Current version of Ubuntu: Release 9.10
                           Kernel: 2.6.31-21 generic
[/B]

thanks for the help in advance

---

### Post by themusicalduck on 2010-05-19
I'm not sure why it won't convert it to zip, but I don't think you're gonna have any luck emailing a file that is 1.2gb, even if you compress it first. Most emails have a limit of around 10mb or so for attachments.

Also gmail doesn't let you send executable files even if they are hidden in a zip or tar file. I think it's an extreme way to prevent viruses spreading. Hotmail is the same.

The only other way I can think of is by using a file sharing service like mediafire or dropbox, but I doubt mediafire would allow a file that large either.

---

### Post by rnerwein on 2010-05-19
> **izquierdista said:**
> I wanted to compress a folder into a .zip file and I get the following error message:
An error occurred while adding files to the archive

the original folder is 1.2GB

I have made .zip files before without any issues before, could it be the size of the original folder?

I am trying to compress this folder in order to send it via email. I managed to compress the folder into a tar.gz file but Gmail didnt let me send it because I got a message stating that Gmail does not allow executable files to be sent. I have sent .zip files through Gmail with no issues before.

[B]Current version of Ubuntu: Release 9.10
                           Kernel: 2.6.31-21 generic
[/B]

thanks for the help in advance

hi
--> Gmail does not allow executable files to be sent.
got that problem a couple of time ( not only gmail ). the reason is that the scanner for executables/virus
works with pattern scanning. randomly you can get some pattern in your compressed file wich match
the pattern for "executable". have a look at man pages for "magic". that's the way in unix/linux how the
file command identify the type of a file ( see file command ). 
if you can't send the file using gzip - try bczip2 it's another algorithmen and there for you get other
pattern in your ziped file.
and by the side - if the file is to big --> see: man split
ciao  :-)

---

