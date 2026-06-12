---
title: "Zip file &quot;can not open file as archive&quot;"
date: 2011-06-20
forum: General Help
---

### Post by Suff0c8r on 2011-06-20
Hey Guys!

I'm not 100% sure if this is the right spot for it, but I'm having trouble unzipping files. I've downloaded a good few fonts from dafont.com, from different authors and with different browsers and I still get errors.

First I opened the .zip with Archive Manager


```
7-Zip 9.04 beta  Copyright (c) 1999-2009 Igor Pavlov  2009-05-30
p7zip Version 9.04 (locale=en_ZA.utf8,Utf16=on,HugeFiles=on,2 CPUs)

Error: /media/42E6F8E2366C0906/Fonts/panhead.zip: Can not open file as archive

Errors: 1
```

I then tried 
```
ross@Ross-PC:~$ unzip /media/42E6F8E2366C0906/Fonts/panhead.zip
```

and got this output

```
Archive:  /media/42E6F8E2366C0906/Fonts/panhead.zip
  End-of-central-directory signature not found.  Either this file is not
  a zipfile, or it constitutes one disk of a multi-part archive.  In the
  latter case the central directory and zipfile comment will be found on
  the last disk(s) of this archive.
unzip:  cannot find zipfile directory in one of /media/42E6F8E2366C0906/Fonts/panhead.zip or
        /media/42E6F8E2366C0906/Fonts/panhead.zip.zip, and cannot find /media/42E6F8E2366C0906/Fonts/panhead.zip.ZIP, period.
```

Any suggestions? I do have p7zip-full installed, but it isn't a .7zip file?

---

### Post by r-senior on 2011-06-20
I just picked one at random from that site, downloaded it, clicked on it in Nautilus (file manager) and it opened with File Roller (archive manager). Clicked on the .ttf file and it offered to install. Nothing unusual.

The above also works with the "Panhead" font. 

I was also able to unzip both zip files from the command line using unzip.

So I think the conclusion we'd have to draw is that the file is not being downloaded correctly.

---

### Post by Suff0c8r on 2011-06-20
> **r-senior said:**
> I just picked one at random from that site, downloaded it, clicked on it in Nautilus (file manager) and it opened with File Roller (archive manager). Clicked on the .ttf file and it offered to install. Nothing unusual.

The above also works with the "Panhead" font. 

I was also able to unzip both zip files from the command line using unzip.

So I think the conclusion we'd have to draw is that the file is not being downloaded correctly.

I have yet to use File Roller, but I can assure you it has been downloaded correctly. I have used both Namaroka and Chromium, as well as UGet.

Some of the .zip files do open, but many do not. the Panhead file is available at [http://www.dafont.com/search.php?psize=m&q=panhead](http://www.dafont.com/search.php?psize=m&q=panhead)

Could you check it on your side?

Thanks for the assistance :D

---

### Post by r-senior on 2011-06-20
Yes, Panhead is OK ...

I'm sure you know how to download a file but a problem with the download or downloaded file is the only logical explanation I can offer, given that unzip works here, but not there.

EDIT: screenshots are Firefox, File Roller, the font viewer/installer and terminal

---

### Post by Suff0c8r on 2011-06-20
Muchos Gracias :D I shall try other download methods and blame my lame Internet connection :P

Thank You so much for all the assistance! I see you have a duk load of beans, so thank you.  I suppose the benefit is that you now have an AMAZING font hey? I recently discovered Billy Argel and like his stiff a LOT. Could I ask for you to email/upload the ttf?

EDIT:
By using another website ([www.fontspace.com](www.fontspace.com)) I was able to get a working download and use the font.

---

### Post by r-senior on 2011-06-20
Could you try this method first (don't type the '$' signs, that's just to indicate your command prompt and what you should type):

```

[COLOR="Red"]$ wget http://img.dafont.com/dl/?f=panhead -O panhead.zip[/COLOR]
--2011-06-20 11:45:16--  http://img.dafont.com/dl/?f=panhead
Resolving img.dafont.com... 188.165.13.72, 2001:41d0:2:8848::1
Connecting to img.dafont.com|188.165.13.72|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: unspecified [application/zip]
Saving to: `panhead.zip'

    [      <=>                              ] 622,479      561K/s   in 1.1s    

2011-06-20 11:45:17 (561 KB/s) - `panhead.zip' saved [622479]
[COLOR="Red"]$ unzip panhead.zip[/COLOR]
Archive:  panhead.zip
  inflating: PANHEAD_.TTF            
  inflating: BILLY_ARGEL_PANHEAD_FONT_UP.jpg  
  inflating: LICENSE.txt             
  inflating: PANHEAD BILLY.abr

```

If that doesn't work, please compare your output of 'file' and 'md5sum':

```

[COLOR="Red"]$ file panhead.zip [/COLOR]
panhead.zip: Zip archive data, at least v2.0 to extract
[COLOR="Red"]$ md5sum panhead.zip [/COLOR]
cde7fa21f2e982085ea3ca64ec0679b0  panhead.zip

```

EDIT: OK, if you got it working that's fine. But if you are curious, do try the above.

---

### Post by Suff0c8r on 2011-06-20
Always amped to learn more :D

Here is my output. It did indeed fail, and it has a different md5sum. If I grasp it correctly, the md5 is like a signature to tell you if the file is "right"?

EDIT: I see my filesize is different to yours :/ And that your internet is nice :D

```
ross@Ross-PC:~$ wget http://img.dafont.com/dl/?f=panhead -O panhead.zip
--2011-06-20 12:52:51--  http://img.dafont.com/dl/?f=panhead
Resolving img.dafont.com... 188.165.13.72, 2001:41d0:2:8848::1
Connecting to img.dafont.com|188.165.13.72|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: unspecified [application/zip]
Saving to: `panhead.zip'

    [                          <=>          ] 466,348     37.7K/s   in 12s     

2011-06-20 12:53:03 (37.9 KB/s) - `panhead.zip' saved [466348]

ross@Ross-PC:~$ unzip panhead.zip
Archive:  panhead.zip
  End-of-central-directory signature not found.  Either this file is not
  a zipfile, or it constitutes one disk of a multi-part archive.  In the
  latter case the central directory and zipfile comment will be found on
  the last disk(s) of this archive.
unzip:  cannot find zipfile directory in one of panhead.zip or
        panhead.zip.zip, and cannot find panhead.zip.ZIP, period.
ross@Ross-PC:~$ file panhead.zip
panhead.zip: Zip archive data, at least v2.0 to extract
ross@Ross-PC:~$ md5sum panhead.zip
448fd54a49c256bc65ccc2511f847b17  panhead.zip

```

---

### Post by r-senior on 2011-06-20
> **Suff0c8r said:**
> It did indeed fail, and it has a different md5sum. If I grasp it correctly, the md5 is like a signature to tell you if the file is "right"?
That's correct. It looks like the file is being truncated. Presumably the connection is dropping or timing out.

Perhaps you could try a download manager with automatic resume?

[http://projects.gnome.org/gwget/](http://projects.gnome.org/gwget/)

You can install this on Ubuntu with:

```

sudo apt-get install gwget

```

---

### Post by Suff0c8r on 2011-06-20
Yes! Having seen my error with UGet, I can now see that it was indeed the download. Thanks a ton man!  Our beautiful South African internet (where 10mbps is UNGODLY fast and 512kbps is decent) is to blame :P

---

### Post by mus1cian on 2011-12-30
> **Suff0c8r said:**
> Yes! Having seen my error with UGet, I can now see that it was indeed the download. Thanks a ton man!  Our beautiful South African internet (where 10mbps is UNGODLY fast and 512kbps is decent) is to blame :P

Oh yes; I really miss that SA internet. Almost as much as Eskom.

---

