---
title: "Issues extracting from tar.gz"
date: 2011-01-04
forum: General Help
---

### Post by J2X on 2011-01-04
I've got a large .tar.gz file that I am trying to extract, I have had a look around at the problem and seems other people have had it, but I've tried their solutions and they haven't worked.

The command I am using is:

```
tar zxvf file.tar.gz
```

and the error is: 
```
gzip: stdin: not in gzip format
tar: Child returned status 1
tar: Exiting with failure status due to previous errors
```


I really need this to be extracted, any help you can give would be great!!

---

### Post by coffeecat on 2011-01-04
> **J2X said:**
> I've got a large .tar.gz file that I am trying to extract,

....

and the error is: 
```
gzip: stdin: not in gzip format
```

It's probably not a true tar.gz file. Open a terminal in the directory with the file, and:

```
file filename.tar.gz
```

---

### Post by J2X on 2011-01-04
This is odd, this is what it says:
```
UTF-8 Unicode English text, with very long lines
```

What do I do now?!

---

### Post by realzippy on 2011-01-04
..yes.
And if so (no *real* tar.gz),rename file to *file.tar* or maybe
*file.tar.bz2*
Unpack with
```
tar xvf file.tar
```
or
```
tar xvjf file.tar.bz2
```

Edit:
Ignore this,was too late.

---

### Post by J2X on 2011-01-04
It said it wasn't a .bz2 file so tried with tar:
```

tar: This does not look like a tar archive
tar: Skipping to next header
tar: Archive contains `\240r\3644w\376\373\216\234n\004\273' where numeric off_t value expected
tar: Archive contains `\263L\257R\303U\347\207' where numeric mode_t value expected
tar: Archive contains `\276\233<k\016\020\026\364\020\020\221B' where numeric time_t value expected
```

Along with that random files and folders were created that look like complete gibberish and end in (invalid encoding).

---

### Post by coffeecat on 2011-01-04
Where did you download it from, if you downloaded it? How large is it?

---

### Post by KJ KJ KJ on 2011-01-04
> **J2X said:**
> This is odd, this is what it says:
```
UTF-8 Unicode English text, with very long lines
```What do I do now?!

The chances are you right clicked on a link called filename.tar.gz, thinking it was a direct link to the archive you wanted. 

Sometimes websites expect you to do an ordinary left click onto a page which then runs some code to fetch the archive, or asks you to choose a mirror. So you end up downloading the webpage code instead of what you expected.

The reason I suspect this is because 'file' says:
UTF-8 Unicode English text, with very long lines
I'd try downloading again, and see what happens if you don't do a right-click on the link, and don't do Save-As.

---

### Post by J2X on 2011-01-04
> **KJ KJ KJ said:**
> The chances are you right clicked on a link called filename.tar.gz, thinking it was a direct link to the archive you wanted. 

Sometimes websites expect you to do an ordinary left click onto a page which then runs some code to fetch the archive, or asks you to choose a mirror. So you end up downloading the webpage code instead of what you expected.

The reason I suspect this is because 'file' says:
UTF-8 Unicode English text, with very long lines
I'd try downloading again, and see what happens if you don't do a right-click on the link, and don't do Save-As.

It was downloaded through FTP, and is about 15GB.

---

### Post by KJ KJ KJ on 2011-01-04
> **J2X said:**
> It was downloaded through FTP, and is about 15GB.

OK, I couldn't have known that so had to assume. It helps us all if you give as much information as you can in your first post. How about providing the link?

Is it an ascii file or a binary file? Did you use the appropriate ftp mode? What FTP client did you use?

Is there an MD5SUM you can download to check the archive integrity?

---

### Post by J2X on 2011-01-04
My FTP Client is FileZilla, its set to auto assign the transfer mode, I just went in and tried again at it says "Response:	200 TYPE is now 8-bit binary" so is auto assigning binary transfer, which I think is correct.

---

### Post by KJ KJ KJ on 2011-01-04
> **J2X said:**
> My FTP Client is FileZilla, its set to auto assign the transfer mode, I just went in and tried again at it says "Response:    200 TYPE is now 8-bit binary" so is auto assigning binary transfer, which I think is correct.

OK. Since it takes a while to download 15 Gbytes, copy the partial file and see if you can unpack the copy, and use 'file' to see if its a proper archive. If we don't see the 'long lines' message, that's good news.

---

### Post by J2X on 2011-01-04
> **KJ KJ KJ said:**
> OK. Since it takes a while to download 15 Gbytes, copy the partial file and see if you can unpack the copy, and use 'file' to see if its a proper archive. If we don't see the 'long lines' message, that's good news.

Ok, I just started transferring the file again, left it transferring and used the file command, this is what it said:
gzip compressed data, from Unix, last modified: Wed Dec  8 03:24:21 2010

---

### Post by KJ KJ KJ on 2011-01-04
> **J2X said:**
> Ok, I just started transferring the file again, left it transferring and used the file command, this is what it said:
gzip compressed data, from Unix, last modified: Wed Dec  8 03:24:21 2010

That's encouraging. While you're waiting, see if there is an MD5 or SHA checksum file associated with your download. It will be a tiny file.

---

### Post by J2X on 2011-01-04
> **KJ KJ KJ said:**
> That's encouraging. While you're waiting, see if there is an MD5 or SHA checksum file associated with your download. It will be a tiny file.

Only other file in the directory is .ftpquota, no md5's or anything.

---

### Post by KJ KJ KJ on 2011-01-04
> **J2X said:**
> Only other file in the directory is .ftpquota, no md5's or anything.

OK, that's not a problem. If there had been such a file, you could have used to confirm that your large file wasn't corrupted.

If you do have success, please tell the thread.

---

